#RL #curriculum-learning #reverse-learning #VI #PI #TRPO #Brownian-motion

- motivation
	- RL often faces needle-in-haystack problem, e.g. learning to turn a key in a lock
	- one way to help learning is shaping the reward function in a clever way
		- this often requires considerable human expert effort -> expensive
	- instead of struggling endlessly in such sparse reward environments, let's provide the agent with a single state in which the task is achieved and work back from there
- setting
	- goal-oriented tasks -> naturally, sparse reward
	- start state $\rho^0\in S^0\subset\mathcal S$
	- goal state $\rho^g\in S^g\subset\mathcal S$
	- we want to get from $S^0$ to $S^g$, by using a binary reward function $r(s_t)=\mathbb 1\{s_t\in S^g\}$
- introduced setting: reverse curriculum learning
	- based on policy optimization algo TRPO (but any on-policy method could be used)
	- here's the twist: in every iteration $i$, use a different start-state distribution $\rho_i$
		- evaluation happens still on the original distribution $\rho_0$, of course
		- this reverse expansion is inspired by RL classics like VI or PI
		- no reward engineering
	- how are those start-states chosen?
		- new states are sampled by applying noise in the action space, using short "Brownian motion" rollouts, taking actions $a_{t+1}=\epsilon_t$ with $\epsilon_t\sim\mathcal N(0,\Sigma)$
			- such states are guaranteed to be feasible; env takes care of that
		- "good" start states for next iteration are those with $R_\text{min}\leq R(\pi_{i-1,s_0})\leq R_\text{max}$
			- hyperparameters $R_\text{min},R_\text{max}$ can be tuned in accordance with the interpretation as bounds on the probability of success
		- once some start states are mastered ($R(\pi_{i+1},s_0)>R_\text{max})$, $s_0$ is no longer in $S_{i+1}^0$
	- assumptions
		1. agent can be arbitrarily reset to any start state at beginning of all trajectories
		2. at least one goal state state is provided
		3. Markov Chain induced by taking uniformly sampled random actions has a communicating class including all start states and the given goal state
			- communication class = maximal set such that every pair of states in that set communicates with each other (i.e. there is a non-zero probability of reaching one from the other)
		- => all three are often satisfied in simulated goal-oriented tasks

🗓️ 2017

✍️
- [[Carlos Florensa]]
- [[David Held]]
- [[Markus Wulfmeier]]
- [[Michael Zhang]]
- [[Pieter Abbeel]]
