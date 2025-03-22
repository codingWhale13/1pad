#RL #representation-learning #FSQ #quantization #EMA #n-step-return #DMC-suite

![[Pasted image 20250322182343.png]]
- background
	- mapping environment observation to latent states improves sample-efficiency
	- one way to do this is using a self-predictive loss (-> no decoder)
	- this is however prone to dimensional collapse (-> discretization helps)
- introduced method: *iQRL* (implicitly Quantized Reinforcement Learning)
	- high-level idea
		1. learn a representation (in latent space) of the observation space
		2. perform model-free RL on this representation
	   => compatible with any model-free RL algorithm (TD3 is used in the paper)
	- state-based RL (as opposed to image-based)
	- uses TD3 as RL algo, but other model-free RL methods could be used too
	- all components (encoder, dynamics, policy and Q-network) are simply MLPs
	- components
		- encoder
			- $e_\theta:\mathcal O\to\text{latent space}$
			- momentum encoder $\bar{\mathbf z}_{t+1}=f(e_{\bar\theta}(\mathbf o_{t+1}))$ uses an exponential moving average (EMA) of the encoder's weights
			- quantization scheme $f(\cdot)$ quantizes latent representation
		- latent-space dynamics model
			- $d_\phi$
			- predicts the next latent state $\hat{\mathbf z}_{t+1}$ given latent state $\mathbf z_t$ and action $\mathbf a_t$
			- purpose: making the latent states temporally consistent
			- note: we are *not* using $d_\phi$ for model-based RL
		- Q-network (= "critic")
			- critic loss uses $n$-step returns
			- updated by minimizing $$\mathcal L_q(\psi;\tau)=\mathbb E_{\tau\sim\mathcal D}\left[\sum_{k=1}^2(q_{\psi_k}(f(e_\theta(\mathbf o_t)),\mathbf a_t)-y)^2\right],$$ where $$y=\sum_{n=0}^{N-1}r_{t+n}+\gamma^n\min_{k\in\{1,2\}}q_{\bar\psi_k}(e_\theta(\mathbf o_{t+n+1}),\mathbf a_{t+n+1}),$$ with $\mathbf a_{t+n}=\pi_{\bar\eta}(\mathbf z_{t+n}+\eta_{t+n})$
		- policy (="actor")
			- updated by minimizing $$\mathcal L_\pi(\eta;\tau)=-\mathbb E_{\mathbf o_t\sim\mathcal D}\left[\min_{k\in\{1,2\}}q_{\psi_k}(f(e_\theta(\mathbf o_t)),\pi_\eta(f(e_\theta(\mathbf o_t))))\right]$$
				- that is: we maximize the Q-values the agent can achieve through its actions
				- note: clipped double Q-learning trick combats overestimation of Q-values
					- this is why we use two critics instead of just one
	- training encoder and dynamics model
		- encoder and dynamics model are used for representation learning
		- they are learned jointly by sharing the following loss function $$\mathcal L_\text{rep}(\theta,\phi;\tau)=\sum_{h=0}^{H-1}\gamma_\text{rep}^h\left(\frac{f(\hat{\mathbf z}_{t+h}+d_\phi(\hat{\mathbf z}_{t+h},\mathbf a_{t+h}))}{\lVert f(\hat{\mathbf z}_{t+h}+d_\phi(\hat{\mathbf z}_{t+h},\mathbf a_{t+h}))\rVert_2}\right)^\top\left(\frac{f(e_{\bar\theta}(\mathbf o_{t+h+1}))}{\lVert f(e_{\bar\theta}(\mathbf o_{t+h+1}))\rVert_2}\right)$$
			- $\tau=0.005$ is the target network update rate
				- used implicitly in the target $e_{\bar\theta}(\mathbf o_{t+1})$ where $\bar\theta=(1-\tau)\bar\theta+\tau\theta$
			- $H=5$ is the horizon for representation learning
			- $\gamma_{rep}=0.9$ is the discount factor for representation learning
			- intuition:
				- we have two different perspectives: dynamics model and encoder
					- the dynamics model has seen the previous latent state from $\mathcal Z$
					- the (EMA) encoder has seen the current observation from $\mathcal O$
					- => together, they want to determine the current latent state
				- we use cosine similarity of the two predictions
					- since we divide by the norms, the magnitude doesn't matter
					- cosine similarity is always in $[-1,1]$
					- $\mathcal L_\text{rep}$ is maximized when all $H$ cosine similarities are 1, i.e. the compared vectors have the same direction
- results
	- more sample-efficient than compared methods
		- TD3
		- TD7
		- TACO
		- TCRL
	- performs well in DMC Humanoid and Dog tasks
- other insights
	- iQRL is similar to TD7 (both extending TD3), but focuses specifically on preventing representation collapse
	- reconstruction loss has negative impact
	- projection head has negative impact
		- might perform better in image-based representations, but this work focuses on state-based representations
	- reward head doesn't really help -> turned off in iQRL

🗓️ 2024

✍️
- [[Aidan Scannell]]
- [[Kalle Kujanpää]]
- [[Yi Zhao]]
- [[Mohammadreza Nakhaei]]
- [[Arno Solin]]
- [[Joni Pajarinen]]
