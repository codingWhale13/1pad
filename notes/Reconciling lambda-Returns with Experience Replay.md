#RL #TD-lambda #experience-replay #PER #n-step-return #DQN #directly-prioritized-replay

![[Pasted image 20250405100231.png]]
- motivation
	- $\lambda$-return usually improves empirical sample efficiency
	- on the other hand, experience replay is a crucial component of the most sample-efficient RL methods out there
	- this work finds some middle ground between policy methods based on experience replay and $\lambda$-return
- considerations
	- challenge: $\lambda$-return theoretically depends on all future Q-values
	- even truncating the $\lambda$-return calculation after 10 time steps, would require 10x the computation of 1-step method -> expensive with large Q networks
- background: truncated $\lambda$-return  $G_t^\lambda$
	- $G_t^\lambda$ is equivalent to an exponential average of all $n$-step returns for $n=\{1,2,\dots,N\}$
		- with $n$-step return $G_t^{(n)}\coloneqq R_t+\gamma R_{t+1}+\dots+\gamma^{n-1}R_{t+n-1}+\gamma^n \max_{a\in\mathcal A}Q(s_{t+n},a)$
			- note: no matter the real action, we're taking the maximizing action in the final term, as done in Peng's $Q(\lambda)$
	- forward view: $G_t^\lambda=(1-\lambda)\sum_{n=1}^{N-1}\lambda^{n-1}G_t^{(n)}+\lambda^{N-1}G_t^{(N)}$
		- note that it's essentially $G_t^{(1)}+\lambda G_t^{(2)}+\dots+\lambda^{N-1}G_t^{(N)}$
		- the other terms are just for weight conservation
			- first term weights: $(1-\lambda)(1 + \lambda + \lambda^2 + \cdots + \lambda^{N-2}) = 1 - \lambda^{N-1}$
			- value approximation gets the remaining weight: $\lambda^{N-1}$
			- total weight: $(1 - \lambda^{N-1}) + \lambda^{N-1} = 1$
	- recursive view: $G_t^\lambda=G_t^{(1)}+\gamma\lambda(G_{t+1}^\lambda-\max_{a\in\mathcal A}Q(s_{t+1},a))$
- introduced method: *directly prioritized replay*
	- the authors use DQN, but with the following modifications
	- the replay buffer stores
		- short sequences of past memory
		- a cache of precomputed $\lambda$-returns (using the recursive formula above)
	- $\lambda$-returns have to be refreshed periodically to keep up with the changing $Q$
		- nice side effect: we don't need $Q$-target network anymore
		- but still, this is expensive...
	- solution to make things faster: randomly select fixed-size blocks of the replay buffer and only implement the cache there
	- it's the first experience replay method to compute returns before they are sampled
		- opportunity to select samples based on this precalculated return
		- thus, the name: "directly prioritized replay"
		- disadvantage: only samples in the cache can be prioritized, not the full cache...
	- proposed prioritization: mixture of
		- uniform distribution over the cache
		- uniform distribution over the samples in the cache whose absolute TD errors exceed some quantile (the authors use the median, for symmetry)
	- final trick is dynamically select $\lambda$
		- redefine $G_t^\lambda=\text{median}(G_t^{\lambda=\frac{0}{k}},G_t^{\lambda=\frac{1}{k}},\dots,G_t^{\lambda=\frac{k}{k}})$
		- authors use $k=20$

🗓️ 2020

✍️
- [[Brett Daley]]
- [[Christopher Amato]]
