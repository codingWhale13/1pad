#DQN #RL #DL #ALE #CNN #Q-learning #experience-replay

- motivation
	- deep learning brought breakthroughs to computer vision and speech recognition
	- let's do he same for RL, by cracking end-to-end learning from images
		- images are high-dimensional, highly correlated states
- introduced method: *DQN* (Deep Q-Network)
	- experience replay
		- crucial component, for this off-policy approach to work
		- first introduced by Long-Ji Lin in 1993 but rediscovered through this work
		- at each time step, tuple $(s_t,a_t,r_t,s_{t+1})$ is added to a dataset which is the buffer
		- during training, samples are drawn at random from the pool of stored samples
		- using samples in (potentially) many updates gives data efficiency
		- another advantage: randomizing the samples is more efficient than learning from highly correlated consecutive samples
		- off-policy approach smoothes out learning and avoids oscillations and divergences in the parameters
	- uses CNN
	- raw pixel input, no information about actual emulator state
	- discrete action output
- results
	- as rewards are very noisy, the authors suggest to look at the Q values to evaluate the progress over training time
	- DQN strongly outperforms other methods
		- random
		- Sarsa
		- Contingency
	- even beats human performance in 3 games
- a bit of history: TD-Gammon achieved unprecedented performance on backgammon
	- in contrast to this work, it used a state value function $V(s)$ rather than an action value function $Q(s, a)$ and learnt on-policy rather than off-policy

🗓️ 2013

✍️
- [[Volodymyr Mnih]]
- [[Koray Kavukcuoglu]]
- [[David Silver]]
- [[Alex Graves]]
- [[Ioannis Antonoglou]]
- [[Daan Wierstra]]
- [[Martin Riedmiller]]
