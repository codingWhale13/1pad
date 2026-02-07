#RL #reward-design #GranTurismo

- motivation
	- learn reward function for Gran Turismo
- introduced method
	- steps
		1. reward generation
			- input: environment context & task description
			- output: reward code
		2. trajectory alignment filter
			- use trajectory alignment coefficient (TAC) to filter out potentially misaligned reward functions
		3. RL training
			- any RL algo works here
		4. agent selection
			- select best performing policy (based on VLM judgement) for human evaluation
		5. go to step 2
	- perks
		- no need for fitness function - hypothesis is that VLMs can differentiate good and bad behavior just as well as humans
		- uses a VLM for preference selection (in the role of a human-like reward designer)
		- can deal with environment code specified in multiple files, via dataclass API
- evaluation
	- reference point: GT Sophy, an RL agent trained with expert-designed reward function

🗓️ 2025

✍️
- [[Michel Ma]]
- [[Takuma Seno]]
- [[Kaushik Subramanian]]
- [[Peter R. Wurman]]
- [[Peter Stone]]
- [[Craig Sherstan]]
