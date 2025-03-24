#SAC #RL #entropy-regularization #KL-divergence #EMA

- motivation: let's combine the best of two worlds:
	- off-policy RL -> sample-efficiency
	- maximum entropy -> stability
- soft policy iteration
	- relevant components
		- maximum entropy objective
			- $J(\pi)=\sum_{t=0}^T\mathbb E_{(s_t,a_t)\sim p_\pi}[r(s_t,a_t)+\alpha\mathcal H (\pi(\cdot\mid s_t))]$
		- soft state value function
			- $V(s_t)=\mathbb E_{a_t\sim\pi}[Q(s_t,a_t)-\log\pi (a_t\mid s_t)]$
		- modified Bellman back operator
			- $T^\pi Q(s_t,a_t)\hat = r(s_t,a_t)+\gamma\mathbb E_{s_{t+1}\sim p}[V(s_{t+1})]$
		- action value function
			- $Q^0:\mathcal S\times\mathcal A\to\mathbb R$ with $\lvert \mathcal A\rvert<\infty$
			- $Q^{k+1}=T^\pi Q^k$
		- set of policies is a parameterized family of distributions
			- $\Pi$
			- e.g. Gaussians
			- to account for $\pi\in\Pi$, policies are projected onto $\Pi$ using KL-divergence
		- partition function
			- $Z^{\pi_\text{old}}(s_t)$
			- normalizes the distribution
			- does not contribute to gradient w.r.t. new policy -> can be ignored
	- soft policy evaluation (lemma)
		- the sequence $Q^k$ will converge to the soft Q-value of $\pi$ as $k\to\infty$
	- soft policy improvement (lemma)
		- let $\pi_\text{old}\in\Pi$
		- let $\pi_\text{new}=\arg\min_{\pi'\in\Pi} D_{KL}(\pi'(\cdot\mid s_t)\mid\mid \frac{\exp(Q^{\pi_\text{old}}(s_t,\cdot))}{Z^{\pi_\text{old}}(s_t)})$
		- then $Q^{\pi_\text{new}}(s_t,a_t)\geq Q^{\pi_\text{old}}(s_t,a_t)$ for all $(s_t,a_t)\in\mathcal S\times \mathcal A$ with $\lvert\mathcal A\rvert < \infty$
	- soft policy iteration (theorem)
		- repeated application of soft policy evaluation and soft policy improvement from any $\pi\in\Pi$ converges to a policy $\pi^*$ s.t. $Q^{\pi^*}(s_t,a_t)\geq Q^\pi(s_t,a_t)$ for all $\pi\in\Pi$ and $(s_t,a_t)\in\mathcal S\times\mathcal A$, assuming $\lvert\mathcal A\rvert <\infty$
	- so far, only the tabular case is considered - approximation in continuous case works with the following components
		- approximate Q-function with neural net parameters $Q_\theta(s_t,a_t)$
		- approximate policy with neural net parameters $\pi_\phi(a_t\mid s_t)$
		- approximate state value function $V_\psi(s_t)$
			- not necessarily needed, since we could use $Q_\theta(s_t,\pi(s_t))$ without introducing a bias
			- still useful for stabilizing training in practice
- introduced method: *SAC* (Soft Actor-Critic)
	- implements the above soft policy iteration
	- maximum entropy objective
		- differs from the standard maximum expected reward objective used in conventional reinforcement learning
		- conventional objective can be recovered in the limit as $\alpha\to 0$
	- target value network weights are a exponential moving average (EMA) of the online value network

🗓️ 2018

✍️
- [[Tuomas Haarnoja]]
- [[Aurick Zhou]]
- [[Pieter Abbeel]]
- [[Sergey Levine]]
