#MTRL #MTL #unitary-scalarization #Meta-World #SAC

- motivation
	- easiest way to train a neural net for multiple tasks: minimize sum of per-task losses
		- this is called "unitary scalarization"
	- some researchers attribute the difficulty of MTL to conflicting gradients or similar, and argue for elaborate techniques of gradient surgery
	- this work argues that unitary scalarization works just as well, when coupled with proper regularization and stabilization techniques from single-task learning
- preliminaries
	- SMTO: Specialized Multi-Task Optimizer
	- unitary scalarization: training multiple tasks jointly by minimizing the sum of losses
	- assumption in this work: each parameter update employs information from all tasks
	- SMTO objective: $\min_\theta[\mathcal L^\text{MT}(\theta)\coloneqq [\mathcal L_1 (f(\theta,X,1),Y),\dots,\mathcal L_m (f(\theta,X,m),Y)]]$
	- unitary scalarization objective: $\min_\theta[\mathcal L^\text{MT}(\theta)\coloneqq\sum_{i\in\mathcal T}\mathcal L_i (f(\theta,X,i),Y)]$
		- no per-task gradients required; can directly compute gradient of the sum $\mathcal L^\text{MT}$
		- compared to SMTOs
			- backward pass is performed once per iteration (rather than $m$ times)
			- memory cost is a factor of $m$ less than most SMTOs
- experiments
	- first time running multi-task supervised learning methods MGDA, IMTL, RLW, GradDrop in RL setting (Meta-World benchmark)
		- no SMTO consistently outperforms SAC with unitary scalarization
			- while being much faster (15h vs. a week)
		- not even PCGrad, which is developed for RL
	- to make SAC work well with unitary scalarization, the authors did these things
		- increased replay buffer size
		- actor $l_2$ regularization
		- modified reward normalization
	- hypothesis why we can achieve similar results: SMTOs act as regularizers
		- that being said, there may be environments, where unitary scalarization underperforms - it just wasn't the case in MT10 and MT50, compared to current SMTO methods

🗓️ 2023

✍️
- [[Vitaly Kurin]]
- [[Alessandro De Palma]]
- [[Ilya Kostrikov]]
- [[Shimon Whiteson]]
- [[M. Pawan Kuma]]
