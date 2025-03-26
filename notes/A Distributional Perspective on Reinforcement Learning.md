#RL #ALE #C51 #multi-modal

- motivation
	- authors argue, we can do better than modeling the expected cumulative return value
	- let's model instead the value distribution to implement risk-aware behavior
- introduced method: *C51* (Categorical 51-atom algorithm)
	- uses distributional Bellman equation ("value distribution")
		- $Z(s,a)=r+\gamma Z(s',a')$ is the distribution over future rewards
		- this is in contrast to the $Q$ function which just outputs a scalar
		- we got three random variables here
			- reward $R$
			- next state-action $(S',A')$
			- return $Z(S',A')$
	- discrete value distribution
		- support is the set of atoms $\{z_i=V_\text{min}+i\Delta z:0\leq i<N\}$
			- $V_\text{min},V_\text{max}\in\mathbb R$  -> I guess that's the range of possible values
			- $\Delta z\coloneqq \frac{V_\text{max}-V_\text{min}}{N-1}$ -> equal bin size
		- atomic probabilities are given by a parametric model $\theta:\mathcal X\times \mathcal A\to\mathbb R^N$
			- $Z_0(s,a)=z_i$ with probability $p_i(s,a)\coloneqq \frac{e^{\theta_i(s,a)}}{\sum_j e^{\theta_j(s,a)}}$
			- so basically: softmax
		- tested with 5, 11, 21, and 51 returns
		- using 51 atoms performs especially well
- math concepts used in derivation
	- Bellman optimality operator
	- Wasserstein metric
	- Banach's fixed point theorem
- results
	- when using a policy aiming to maximize expected return
	- outperforms other methods by a great deal in SeaQuest
	- learning distributions matters in the presence of approximation
	- the authors mention the following reasons why a value distribution is better than modeling a scalar return
		- reduced chattering, more likely to converge because of distribution averaging
		- state aliasing can make deterministic envs stochastic -> modeling the resulting distribution is beneficial
		- richer set of predictions
		- framework for inductive bias
		- well-behaved optimization

🗓️ 2017

✍️
- [[Marc G. Bellemare]]
- [[Will Dabney]]
- [[Rémi Munos]]
