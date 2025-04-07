#RL #DDPG #DPG #DL #actor-critic #Q-learning

- motivation
	- adapt Deep Q-learning to the continuous action domain
	- simply using DQN on discretized action space is not good enough
		- curse of dimensionality
		- throwing away structural information
- introduced method: *DDPG* (Deep Deterministic Policy Gradient)
	- uses ideas from DQN, namely
		- training model-free and off-policy, using a replay buffer
		- using a Q target network
		- however, we can't apply Q-learning straight-forwardly to continuous actions, because optimizing $a_t$ at every time step is too expensive with deep learning
			- => see next point: DPG
	- extends DPG (Deterministic Policy Gradient), an actor-critic method
		- policy gradient helps generalizing in larger state and action spaces
		- to make thing work, the authors
			- the target network for actor-critic case and
			- use soft target updates
		- both targets $\pi'$ (called $\mu'$ in the paper) and $Q'$ are crucial for stable targets $y_t$
			- $y_t=r(s_t,a_t)+\gamma Q(s_{t+1},\pi(s_{t+1})\mid \theta^Q)$
	- to aid exploration (tricky in continuous domain), Gaussian noise is added to policy
- results: interestingly
	- DDPG sometimes finds policies that exceed the performance of the planner
	- DDPG can learn some tasks end-to-end from pixel-based input

🗓️ 2019

✍️
- [[Timothy P. Lillicrap]]
- [[Jonathan J. Hunt]]
- [[Alexander Pritzel]]
- [[Nicolas Heess]]
- [[Tom Erez]]
- [[Yuval Tassa]]
- [[David Silver]]
- [[Daan Wierstra]]
