#experience-replay #RL #PER #n-step-return #ALE #C51

![[Pasted image 20250325235046.png]]
- motivation
	- experience replay is crucial to any off-policy method
	- DQN uses replay buffer with capacity of 1M transitions and this number has not been adjusted by most follow-up works
- concepts
	- experience replay
		- typically implemented as a circular buffer, where the oldest transition in the buffer is removed to make room for a transition that was just collected
		- replay capacity: number of transitions that can be stored
		- age of a transition: number of gradient steps taken by the learner since the transition was generated
		- age of the oldest policy in a replay buffer: age of the oldest transition in buffer
		- replay ratio: ratio of learning updates to experience collected
	- Rainbow algorithm
		- combines many good ideas on top of the DQN algorithm
			- PER
			- n-step returns
			- Adam optimizer
			- C51
- experimental setup
	- replay capacity from 0.1M to 10M considered
	- trying to uncover why Rainbow benefits from increased replay buffer
		- adding one single components (of the above mentioned four) to DQN
		- taking away one single components of Rainbow
- results
	- hyperparameters buffer capacity and rate of data throughput are interlinked, modifying both amount of data available and typical age of the data
	- performance improves
		- with increased replay capacity
			- this is e.g. visible in Rainbow
			- Zhang & Sutton (2017) however find a detrimental effect with larger replay capacity
			- => it depends on the algorithm too... the authors find n-step returns to be a crucial component that allows benefits from replay buffer scaling
		- with reduced age of the oldest policy
			- however, this is not the case in the PrivateEye env which has sparse reward
	- n-step returns are critical when using increased replay capacity
		- one reason: increasing replay capacity can help mitigate the variance of n-step targets (*not* the variance of the gradients)
	- more work needs to be done, not everything has been answered - but the distinct relationship between n-step returns and increased replay capacity is a novel insight

🗓️ 2019

✍️
- [[William Fedus]]
- [[Prajit Ramachandran]]
- [[Rishabh Agarwal]]
- [[Yoshua Bengio]]
- [[Hugo Larochelle]]
- [[Mark Rowland]]
- [[Will Dabney]]
