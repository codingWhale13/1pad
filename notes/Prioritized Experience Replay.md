#PER #experience-replay #RL #IS

- motivation
	- experience replay is crucial for off-policy learning
	- but surely, we can do better than uniformly sampling experience, right?
- introduced replay sampling method: *PER* (Prioritized Experience Replay)
	- use case: model-free, off-policy RL
	- this work only addresses how to replay stored experiences
		- in other words: what goes into the replay buffer is not affected
	- idea: more frequently sample transitions that have high expected learning progress
		- this is measured by the magnitude of the TD error
		- TD error can be a poor choice, e.g. with noise rewards
	- implementation
		- priority queue is built with a binary heap
		- -> sampling max priority transition in O(1)
		- -> updating priorities (with new TD-error after learning step) is O(log N)
	- greedy TD-error prioritization comes with problems that are addressed accordingly
		- loss of diversity due to only updating TD errors of those sampled transitions
			- solution: stochastic prioritization, interpolating between greedy prioritization and uniform random sampling using $P(i)=\frac{p_i^\alpha}{\sum_k p_k^\alpha}$
				- $p_i>0$ is the probability of transition $i$
				- exponent $\alpha$ determines how much to prioritize, $\alpha=0$ is uniform
		- introduces bias, due to changing sampling distribution
			- solution: importance sampling with $w_i=(\frac{1}{N}\cdot\frac{1}{P(i)})^\beta$
				- fully compensates for the non-uniform probabilities $P(i)$ if $\beta=1$
				- in practice, $\beta$ gets annealed from some $\beta_0$ to $1$

🗓️ 2016

✍️
- [[Tom Schaul]]
- [[John Quan]]
- [[Ioannis Antonoglou]]
- [[David Silver]]
