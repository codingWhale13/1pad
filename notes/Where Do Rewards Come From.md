#RL #reward-design #Q-learning #RL-env-hungry-thirsty

- motivation
	- traditionally, we view reward as external to an RL agent, decided by the environment
		- this outsourcing makes the RL framework general and simple
	- but in animals, all rewards are generated internally, e.g. by the dopamine system
		- this paper adopts this mindset and asks: how to determine the optimal reward?
		- in other words: when we view all reward as agent-internal, we need a framework of reward itself!
- background
	- while all reward may be viewed as internal to the agent, psychologists differentiate:
		- extrinsic reward (environment-mandated) and
		- intrinsic reward, driving exploration and curiosity without explicit reward
		- (however, the lines can be blurry...)
	- in the RL framework, we have
		- primary reward
			- hard-wired in animals by evolutionary process
			- environment reward
		- secondary reward
			- predictors of primary rewards at as rewards themselves
			- learned value function
	- important differences
		- internal != intrinsic
		- intrinsic != secondary
- contribution: a general framework of reward, with minimal changes to the RL framework
	- key ingredients:
		- $A$: agent
		- $R_A$: reward function space, where $r_A\in R_A$ map states to primary reward for RL
		- $\mathcal E$: set of MDP envs in which we want our agents to perform well (in expectation)
		- $h$: history of agent $A$ adapting to env $E\in\mathcal E$ under reward function $r_A\in R_A$
		- $r_A^*\in R_A$: optimal reward function, maximizing expected fitness over all envs
		- $F$: fitness function, mapping $h$ to scalar fitness value
			- may take any form (including discounted sums of extrinsic rewards)
	- hypotheses:
		1. the $r_A^*$ derived from search will capture physical regularities across environments in $\mathcal E$ as well as complex interactions between $\mathcal E$ and specific structural properties of the agent $A$
			- note that the agent $A$ is part of its environment and is constant across all environments in $\mathcal E$
		2. the value functions learned by an agent during its lifetime will capture regularities present within its specific environment that are not necessarily shared across environments
- experiments
	- agent: $\epsilon$-greedy Q-learning, doing grid-search over learning rate $\alpha$ and exploration $\epsilon$
	-  6x6 gridworlds in two flavors
		- hungry-thirsty domain
			- intricate design, see paper for more details
			- shows emergent extrinsic reward for water
			- while I don't understand where they get these values from, the authors claim that the "best reward function in our search space" to be:
				- hungry and thirsty: -0.05
				- hungry and not-thirsty: -0.01
				- not-hungry and thirsty: 1.0
				- not-hungry and not-thirsty: 0.5
		- boxes domain
			- extension of the hungry-thirsty domain, where the agent has to "open a box" to earn food and water
			- shows emergent intrinsic reward for exploration and manipulation
- take-away
	- even in simple envs, the true objective (fitness) is a poor reward signal for learning
	- learning a reward can produce way better results than using the fitness directly
		- I suppose this happens via evolutionary methods, paper doesn't provide details

🗓️ 2009

✍️
- [[Satinder Singh]]
- [[Richard L. Lewis]]
- [[Andrew G. Barto]]
