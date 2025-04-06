#RL #policy-gradient #credit-assignment-problem #n-step-return #TRPO #GAE

- motivation
	- one difficulty inherent to RL is the long delay between actions and their effects on rewards -> credit assignment problem
	- value functions tackle this issue by estimating the value of a state before the delayed reward arrives
	- PPO is great but has 2 challenges
		- 1: large number of samples typically required
			- proposed solution: use value functions to substantially reduce the variance of policy gradient estimates at the cost of some bias, with an exponentially-weighted estimator of the advantage function that is analogous to TD(λ)
		- 2: difficulty of obtaining stable and steady improvement despite the nonstationarity of the incoming data
			- proposed solution: TRPO
- background: types of RL
	- policy-gradient
		- parameterized stochastic policy
		- gives unbiased estimate of the gradient, but has high variance over long horizons
	- actor-critic
		- uses value function instead of empirical returns -> lower variance but biased
		- note that variance can be "fixed" by just sampling more, while bias can't be corrected as straightforward
	- => this work combines both of them
- introduced method: *GAE* (Generalized Advantage Estimator)
	- family of model-free policy gradient estimators, with good variance-bias tradeoff
	- crucial idea
		- consider undiscounted formulation
		- make discount factor $\gamma\in[0,1]$ an algo parameter; setting it $<1$
			- reduces variance
			- but introduces bias
	- consider state-value function $V$ and action-value function $Q$
		- $V^{\pi,\gamma}(s_t)\coloneqq \mathbb E_{s_{t+1:\infty},a_{t:\infty}}[\sum_{l=0}^\infty\gamma^lr_{t+l}]$
		- $Q^{\pi,\gamma}(s_t,a_t)\coloneqq \mathbb E_{s_{t+1:\infty},a_{t+1:\infty}}[\sum_{l=0}^\infty\gamma^lr_{t+l}]$
	- goal: estimate advantage $A^{\pi,\lambda}(s,a)=Q^{\pi,\lambda}(s_t,a_t)-V^{\pi,\lambda}(s_t)$
		- policy gradient is then $g^\gamma\coloneqq\mathbb E_{s_{0:\infty},a_{0:\infty}}[\sum_{t=0}^\infty A^{\pi,\gamma}(s_t,a_t)\nabla_\theta\log \pi_0(a_t\mid s_t)]$
	- besides $\gamma$, we have another parameter $\lambda\in[0,1]$
		- this corresponds to the recency factor in TD($\lambda$)
	- $\hat A_t^{\text{GAE}(\gamma,\lambda)}\coloneqq (1-\lambda)(\hat A_t^{(1)}+\lambda\hat A_t^{(2)}+\lambda^2\hat A_t^{(3)}+\dots)=\sum_{l=0}^\infty (\gamma\lambda)^l\delta_{t+l}^V$
		- $\delta_t^V=-V(s_t)+r_t+\gamma V(s_{t+1})$
		- $\hat A_t^{(k)}=\sum_{l=0}^{k-1}\gamma^l\delta_{t+l}^V$
		- exponentially-weighted average of $k$-step estimators
	- now, we can construct a biased estimator of $g^\gamma$:
		- $g^\gamma\approx \mathbb E[\sum_{t=0}^\infty\nabla_\theta\log\pi_\theta (a_t\mid s_t)\hat A_t^{GAE(\gamma,\lambda)}]$

🗓️ 2015

✍️
- [[John Schulman]]
- [[Philipp Moritz]]
- [[Sergey Levine]]
- [[Michael I. Jordan]]
- [[Pieter Abbeel]]
