#RL #TD3 #actor-critic #double-Q-learning #DL #DDPG

- motivation
	- overestimation bias is a common problem in RL: maximization of  a noisy value leads to consistent overestimation (values blowing up)
	- value-based methods in discrete action spaces are known to suffer from value overestimation -> well-studied
	- similar issues persist in actor-critic methods -> under-explored
- recap actor critic, leading up to clipped double Q-learning idea
	- policy ("actor") can be updated using the deterministic policy gradient algorithm
		- $\nabla_{\phi} J(\phi) = \mathbb{E}_{s \sim \rho_{\pi}} \left[ \nabla_a Q^{\pi}(s, a) \vert_{a=\pi(s)} \nabla_{\phi} \pi_{\phi}(s) \right]$
		- where $Q^\pi(s,a)=\mathbb E_{s_i\sim p_\pi,a_i\sim\pi}[R_t\vert s,a]$ is the expected return, provided by the critic
	- the value-estimate ("critic") can be updated by (variants of) Q-learning
		- Q-learning with discrete actions: greedy target $y=r+\gamma\max_{a'} Q(s',a')$
		- using a target network $Q_{\theta'}$ in actor-critic setting: $y=r+\gamma Q_{\theta'}(s',\pi_\phi(s'))$
		- double Q-learning: using a pair of actors and critics
			-  $y_1=r+\gamma Q_{\theta_2'}(s',\pi_{\phi_1}(s'))$
			-  $y_2=r+\gamma Q_{\theta_1'}(s',\pi_{\phi_2}(s'))$
			- $\pi_{\phi_1}$ is optimized wrt $Q_{\theta_1}$ and $\pi_{\phi_2}$ is optimized wrt $Q_{\theta_2}$
		- clipped double Q-learning finally solves overestimation (unlike all above)
			- $y_1=r+\gamma \min_{i=1,2}Q_{\theta_i'}(s',\pi_{\phi_1}(s'))$
			- proposed in this paper
- introduced method: *TD3* (Twin Delayed Deep Deterministic policy gradient algorithm)
	- TD3 is an extension of DDPG
	- key components of TD3
		- novel variant of Double Q-learning
			- taking the minimum value between a pair of critics to limit over-estimation (section 4.2)
		- target networks
			- delay policy updates to reduce per-update error (section 5.2)
		- SARSA-style regularization technique
			- introduce noise to smooth policy (section 5.3)

🗓️ 2018

✍️
- [[Scott Fujimoto]]
- [[Herke van Hoof]]
- [[David Meger]]
