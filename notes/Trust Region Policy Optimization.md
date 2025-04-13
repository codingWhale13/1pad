#RL #TRPO #PI #policy-gradient #MC

![[Pasted image 20250413235116.png]]
- motivation
	- policy optimization algorithms come in three flavors
		- policy iteration
		- policy gradient
		- derivative-free optimization methods
			- e.g. cross-entropy
	- gradient-based methods have much better sample complexity guarantees than gradient-free methods, but can't consistently beat gradient-free random search
		- -> this work finds a principled way to work on continuous gradient-based optimization in the RL setting
	- work gives a new perspective to unify policy gradient and policy iteration methods
- theory
	- policy iteration algorithm guaranteeing non-decreasing expected return $\eta$
		- start with $\pi_0$
		- loop
			- compute all advantage values $A_{\pi_i}(s,a)$
			- solve $\pi_{i+1}={\arg\max}_\pi [L_{\pi_i}(\pi)-C\cdot D_\text{KL}^\max (\pi_i,\pi)]$
				- $C=\frac{4\epsilon\gamma}{(1-\lambda^2)}$
				- $L_{\pi_i}(\pi)=\eta(\pi_i)+\sum_s \rho_{\pi_i}(s)\sum_a \pi(a\mid s)A_{\pi_i}(s,a)$
				- $\eta(\pi)$ is the expected discounted reward of stochastic policy $\pi$
		- => monotonic improvement
	- sampling schemes
		- single path sampling scheme
			- model-free
			- see left side of picture above
		- vine sampling scheme
			- only possible in simulation
			- see right side of picture above
- introduced family of methods: *TRPO* (Trust Region Policy Optimization)
	- TRPO is an approximation of the algorithm above
	- basically three steps:
		1. collect a set of state-action paris with MC estimates of their Q-values
			- using either single path or vine sampling scheme
		2. construct estimated objective and constraint based on average over samples
		3. approximately solve constrained optimization problem to update $\theta$ of $\pi_\theta$

🗓️ 2017

✍️
- [[John Schulman]]
- [[Sergey Levine]]
- [[Philipp Moritz]]
- [[Michael Jordan]]
- [[Pieter Abbeel]]
