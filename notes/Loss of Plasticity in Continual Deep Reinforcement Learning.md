#RL #DL #continual-learning #ReLU #CReLU #S-ALE

![[Pasted image 20250309223839.png]]
- motivation
	- long-lived RL agents need to deal with non-stationarities over timescales much longer than what is feasible for a replay buffer to store
	- so, the authors ask: how does value-based deep RL do under varying degrees of non-stationarity? -> goal is to surface the issue of loss of plasticity, also known as
		- implicit under-parameterization
		- primacy bias
		- capacity loss
- 3 contributions
	- demonstration of catastrophic loss of plasticity in Rainbow
		- cycle through a fixed sequence of games
		- experimental setup named "Switching ALE", or S-ALE
		- using Alien-Atlantis-Boxing-Breakout-Centipede, performance in all game visits drops over time (Breakout learns surprisingly stable though)
	- analysis of weights, gradients, and activations sampled over the lifetime of the experiment
		- weights stop changing while loss remains high - due to gradient collapse
			- l2 norm of gradients over consecutive visits doesn't seem that drastic, due to emphasis on outliers - however, l0 and l1 norm fall rapidly, showing gradient collapse
		- over time, the number of active neurons shrinks
			- this is due to ReLU: if not active, the zero output value does not contribute to the change of its incoming weights
		- poor performance
	- CReLU mitigates loss of plasticity
		-  $\text{CReLU}(x)\coloneq [\text{ReLU}(x), \text{ReLU}(−x)]$
		- this modification allows Rainbow to maintain or improve its performance on successive visits in all five games
		- side effect output size is twice the input size -> more parameters in following layer
- unresolved: catastrophic forgetting
	- CReLU allows for same performance gains in each game visit, but it doesn't solve the problem of catastrophic forgetting: when the agent is confronted again with the same task after learning the other tasks, it starts learning from scratch
- my open question: in figure 17, I don't understand how the output dimension is now always 1. Does this mean, every layer has a single output neuron? How do we reduce the number of parameters when CReLU has at least two outputs?

🗓️ 2023

✍️
- [[Zaheer Abbas]]
- [[Rosie Zhao]]
- [[Joseph Modayil]]
- [[Adam White]]
- [[Marlos C. Machado]]
