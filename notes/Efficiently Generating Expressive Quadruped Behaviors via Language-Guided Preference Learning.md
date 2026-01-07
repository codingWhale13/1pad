#LGPL #RL #quadruped #robotics #LLM

- motivation
	- setting: social robots, see these [fun videos](https://lgpl-gaits.github.io/)
	- two inputs for shaping robot behaviors:
		- natural language: efficient but low-resolution
		- human preferences: high-resolution but sample-inefficient
	- let's combine the two using an LLM as prior, as well as preference learning
- method: Language-Guided Preference Learning (LGPL)
	- uses preferences for real-time behavior from a *fixed* multi-task policy
		- -> policy has already been trained, only different rollouts (based on weighted objectives) are presented to the user
		- uses Bradley-Terry model (which is the gold standard for preference ranking) 
	- assumption: reward function can be expressed as a sum of differentiable functions (this is the case for quadruped, e.g., velocity, orientation, energy usage)
- results
	- with as few as 4 queries (user ranking of trajectories), expressive behaviors can be generated
- take-aways
	- "although language is a coarse mechanism of feedback, it can provide high-quality candidate solutions which vastly speed up the preference learning process"

🗓️ 2025

✍️
- [[Jaden Clark]]
- [[Joey Hejna]]
- [[Dorsa Sadigh]]

