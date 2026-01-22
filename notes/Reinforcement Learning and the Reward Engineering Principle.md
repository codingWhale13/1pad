#reward-design #RL #AI

- definition of AI
	- Russell (1997): "one can define AI as the problem of designing systems that do the right thing"
	- McCarthy (2007:) "the computational part of the ability to achieve goals in the world"
	- Legg and Hutter (2007): "intelligence measures an agent’s ability to achieve goals in a wide range of environments"
- key take-away
	- when operators are not always able to determine an agent's rewards, dominance relationships can arise between action policies for that agent
	- reward engineering principle: as RL-based AI systems become more general and autonomous, the design of reward mechanisms that elicit desired behaviours becomes both more important and more difficult
- some unconventional definitions
	- reward from two sources: this work differentiates between
		- reward from the operator
		- reward from the env
	- policy domination
		- policy A dominates policy B if - no matter what rewards are scheduled - A receives more rewards than B
		- implication: with more autonomy, agents will be more likely to receive rewards from the env (not the operator), increasing the chance of learning a policy that dominates the one with operator-based reward

🗓️ 2014

✍️
- [[Daniel Dewey]]
