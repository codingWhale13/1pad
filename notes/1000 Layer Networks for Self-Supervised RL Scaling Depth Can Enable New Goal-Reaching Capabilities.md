#self-supervised-learning #RL #goal-conditioned-RL #scaling-up #deep-learning

- motivation
	- making self-supervised architectures deeper (say, 100 layers) boosts performance
	- can it also help in RL, where architectures are often shallow (2-5 layers)?
- background
	- one reason why today's popular RL architectures only use a few layers, is the sparse reward signal
	- instead of doing pure RL, the authors do self-supervised RL, extending the contrastive RL (CRL) method
- setting
	- goal-conditioned RL
- method
	- optimization goal: classify if current states and actions belong to the same or different trajectory that leads to a goal state
	- algorithm
		- based on contrastive RL (CRL)
		- actor-critic method
			- actor: $\pi_\theta(a\mid s,g)$
			- critic $f$ consists of two neural networks
				- state-action pair embedding $\phi (s,a)$
				- goal embedding $\psi(g)$
				- => critic's output is the L2-norm between these: $f_{\phi,\psi}(s,a,g)=\lVert\phi (s,a)-\psi (g) \rVert_2$
				- trained with the InfoNCE objective
		- architecture: ResNet-style
- clever eval: separating exploration and expressivity
	- train three networks in parallel
		- collector
		- shallow  learner
		- deep learner
		- => both learners are trained concurrently with data from the collector
	- setup 1: deep collector
		- deep learner substantially outperforms the shallow one -> it is more expressive than the shallow one
	- setup 2: shallow collector
		- buffer gets populated with low-coverage experience
		- both shallow and deep learners struggle
		- deep network's additional capacity does not overcome the limitations of insufficient data coverage
	- => "scaling depth enhances exploration and expressivity in a synergized way: stronger learning capacity drives more extensive exploration, and strong data coverage is essential to fully realize the power of stronger learning capacity"
- take-aways
	- scaling depth gives more immediate results than scaling width, so when operating under fixed compute or memory budgets, depth scaling is generally more computationally efficient
	- the benefits of depth scaling arise from a combination of improved exploration and increased expressivity working jointly (see clever eval above)
	- deeper networks unlock batch size scaling
	- the choice of algorithm is critical: CRL is self-supervised and thus allows for scaling, other algos (SAC, SAC+HER, TD3+HER) don't show the same benefits when scaled

🗓️ 2025

✍️
- [[Kevin Wang]]
- [[Ishaan Javali]]
- [[Michał Bortkiewicz]]
- [[Tomasz Trzciński]]
