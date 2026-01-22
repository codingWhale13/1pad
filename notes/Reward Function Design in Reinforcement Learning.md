#reward-design #RL #PBRS

- natural reward signals
	- evolutionary view: survival and fitness
		- survival is an extremely sparse reward signal, it alone does not explain why we do what we do
	- economics: money
		- more tightly connected to the RL framework
		- one exception: the discount factor in economics is the interest/inflation rate and is dictated by the environment (not a learning parameter of the agent)
- reward shaping
	- described for behavioral science by Skinner
		- sparse reward -> discontinuity in the operands (units of behavior)
		- fix: give successive approximation (shaping) for more dense learning
	- formalized for RL by Ng
		- potential-based reward shaping (PBRS)
		- Sutton & Barto warn that reward shaping goes against the "tabula rasa" ideal of RL: "the reward signal is not the place to impart to the agent prior knowledge about how to achieve what we want it to do"
- intrinsic motivation
	- psychology distinguishes primary reinforcers (basic needs) from secondary reinforcers (abstract desires correlated with later satisfaction of basic needs)
	- curiosity-based exploration in RL mimics this
- when to use what?
	- friendly env with useful dense rewards -> good to go, just train RL agent
	- sparse reward + prior knowledge -> reward shaping, leaves optimal policy unchanged
	- sparse reward and no prior knowledge -> intrinsic motivation

🗓️ 2022

✍️
- [[Jonas Eschmann]]
