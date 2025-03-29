#RL #MBRL #DreamerV2 #atari-100k #RSSM #SAC #stop-gradient
![[Pasted image 20250329214937.png]]
- motivation
	- learning compact state representations from images that can be used for planning
	- Atari performance so far dominated by model-free methods, e.g. Rainbow and IQN
		- -> making model-based RL work could give big improvements
- introduced method: *Dreamer v2*
	- components
		- world model (total of 20M parameters)
			- summarizes agent's experience into a predictive model that can be used in plane of the environment to learn behaviors
				- learning compact representations (much smaller than high-dim images) is crucial to make the dynamics predictable
			- experience dataset sees trajectories of 50 steps
				- to see enough terminal states, the start index of each training sequence is sampled uniformly within the episode
			- uses sequence of *deterministic* recurrent states $h_t$ from which it computes two distributions over *stochastic* states at each step
				- prior state $\hat z_t$, no access to current image
				- posterior state $z_t$, access to current image
			- world model components, first 3 are RSSM
				- (image) encoder: $z_t\sim q_\phi(z_t\mid h_t,x_t)$
				- sequence model: $h_t=f_\phi (h_{t-1},z_{t-1},a_{t-1})$
				- dynamics predictor: $\hat z_t\sim p_\phi(\hat z_t\mid h_t)$
				- reward predictor: $\hat r_t\sim p_\phi(\hat r_t\mid h_t,z_t)$, zero-initialized
				- discount predictor: $\hat \gamma_t\sim p_\phi(\hat \gamma_t\mid h_t,z_t)$
				- (image) decoder: $\hat x_t\sim p_\phi(\hat x_t\mid h_t,z_t)$
			- loss $\mathcal L(\phi)\coloneqq E_{q_\phi (z_{1:T}\mid a_{1:T},x_{1:T})} [\sum_{t=1}^T -\ln p_\phi (x_t\mid h_t,z_t)-\ln p_\phi (r_t\mid h_t,z_t)-\ln p_\phi (\gamma_t\mid h_t,z_t)+\beta\text{KL} [q_\phi (z_t\mid h_t,x_t)\mid\mid p_\phi (z_t\mid h_t)]]$
				- terms from left to right are
					- image log loss
					- reward log loss
					- discount log loss
					- KL loss
			- KL balancing
		- critic (1M parameters)
			- $v_\xi(\hat z_t)\approx E_{p_\phi,p_\psi}[\sum_{\tau\geq t}\hat\gamma^{\tau-t}\hat r_\tau]$
			- uses $\lambda$-target, using $\lambda=0.95$ to focus on long horizon targets
			- uses loss $\mathcal L(\xi)\coloneqq E_{p_\phi,p_\psi}[\sum_{t=1}^{H=1}\frac 1 2 (v_\xi (\hat z_t)-sg(V_t^\lambda))^2]$
				- $$\begin{align*}V_t^\lambda\coloneqq \hat r_t+\hat\gamma_t\begin{cases}(1-\lambda)v_\xi (\hat z_{t+1})+\lambda V^\lambda_{t+1}\text{ if }t<H\\v_\xi(\hat z_H)\text{ if } t=H \end{cases}\end{align*}$$
		- actor (1M parameters)
			- $\hat a_t\sim p_\psi (\hat a_t\mid \hat z_t)$
			- uses loss $\mathcal L(\psi)\coloneqq \mathbb E_{p_\phi,p_\psi}[\sum_{t=1}^{H-1}(-\rho \ln p_\psi (\hat a\mid \hat z_t)\text{sg}(V_t^\lambda-v_\xi(\hat z_t))-(1-\rho)V_t^\lambda-\eta H[a_t\mid \hat z_t])$
				- terms from left to right are
					- reinforce
					- dynamics backprop
					- entropy regularizer
	- differences to Dreamer v1
		- latent variables are now categorical instead of Gaussian
- result
	- outperforms both model-free and model-based RL methods on Atari benchmark

🗓️ 2022

✍️
- [[Danijar Hafner]]
- [[Timothy Lillicrap]]
- [[Mohammad Norouzi]]
- [[Jimmy Ba]]
