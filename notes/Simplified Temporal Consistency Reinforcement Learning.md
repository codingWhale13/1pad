#RL #TCRL #self-consistency-loss

- what
	- investigates the role of latent temporal consistency in state-based reinforcement learning
	- to learn a state encoder and a latent dynamics model jointly, a
- introduced method: *TCRL* (Temporal Consistency Reinforcement Learning)
	- minimalist version of learning latent state representation
	- high-level idea: encode observation space to latent space and learn there using TD3-like RL method
	- beside value network and policy network (both MLPs), TLRC only contains
		- state encoder
			- pixel-based input -> CNN
			- state-based input -> MLP
			- note that there are actually 2 encoders: online $e_\theta$ and EMA target $e_{\theta^-}$
		- transition model (MLP)
	- training dynamics model together with encoder
		- predicting H-step rewards and latent states (rollout horizon H = 5)
		- target rewards are trajectory rewards
		- target latent states are calculated using target encoder
- results
	- two settings analzyed
		- model-based "TCRL-dynamics", using the dynamics model directly for online planning
			- mixed results, but strongly better in dog-walk env, compared to other methods (EnsDet and PETS)
		- model-free, learning a policy (this is the TCRL algorithm)
			- on-par with TD-MPC2 and better in dog-run env
		- in both settings, TCRL is faster than compared methods (factor 2+)
	- focus is on state-based inputs, but the authors also provide pixel-based results
	- training objective: cosine similarity is better than MSE (in TCRL)
		- natural idea: replace MSE loss in TD-MPC with cosine similarity
		  -> however, that leads to worse performance
	- other take-aways:
		- jointly training value function and dynamics model leads to bad performance, no matter if MSE or cosine similarity is used

🗓️ 2023

✍️
- [[Yi Zhao]]
- [[Wenshuai Zhao]]
- [[Rinu Boney]]
- [[Juho Kannala]]
- [[Joni Pajarinen]]
