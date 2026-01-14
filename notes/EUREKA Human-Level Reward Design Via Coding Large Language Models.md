#LLM #reward-design #RL #EUREKA

- motivation
	- reward design for RL
- background
	- setting is defined by the reward design problem, see [[Where Do Rewards Come From]]
- introduced method: Evolution-driven Universal REward Kit for Agent (EUREKA)
	- input
		- unmodified environment source code
		- language task description
	- output
		- executable reward function (generated in a zero-shot fashion)
	- evolutionary search
		- for all envs considered, sampling just 16x is enough to contain at least one executable reward code in the first iteration
	- reward reflection
		- LLM-generated feedback summarizing the policy training dynamics in text
- baselines
	- human rewards (original reward formulation designed by humans)
	- sparse rewards (usually binary success indicators)
	- L2R, a 2023 method

🗓️ 2024

✍️
- [[Yecheng Jason Ma]]
- [[William Liang]]
- [[Guanzhi Wang]]
- [[De-An Huang]]
- [[Osbert Bastani]]
- [[Dinesh Jayaraman]]
- [[Yuke Zhu]]
- [[Linxi "Jim" Fan]]
- [[Anima Anandkumar]]
