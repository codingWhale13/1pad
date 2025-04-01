#RL #backgammon #TD #TD-lambda #self-play

- motivation
	- backgammon is a great testing ground for RL
	- tackle the temporal credit assignment problem, which prevents RL methods from being used much in practice
- background
	- backgammon
		- two-player game
		- based on dice rolls
		- goal: move checkers to win a "gammon" (or even triple-stake "backgammon")
	- TD method
		- heuristic error, based on difference between two successive predictions
		- influence of future predictions gets exponentially decayed using discount factor
- introduced method: *TD-Gammon*
	- neural-net based algorithm
	- goal: become an evaluation function for the game
	- learns through self-play
		- however, adding a set of handcrafted features to the raw states helps learning
		- starts with random play -> games can last thousands of time steps (compared to human games, with 50-60 time steps)
	- formula for TD(lambda) weight change (expressed for single output unit)
		- $w_{t+1}-w_t=\alpha (Y_{t+1}-Y_t)\sum_{k=1}^t\lambda^{t-k}\nabla_w Y_k$
		- $\alpha$ is the learning rate
		- $w$ are the neural net weights
		- $\nabla_w Y_k$ is the gradient of the network output w.r.t. weights
- results
	- the agent learns strategies and tactics, even without any handcrafted features
	- best performance was with 40 hidden units, trained for 200k games
	- best version of TD-Gammon (2.1, using handcrafted features) matches world-leading Bill Robertie
- other takeaways
	- the absolute accuracy of the learned value function is not great, but the errors are highly correlated, making the agent perform much better than what it might seem from just taking the absolute accuracy into account
	- the stochastic nature of the game (due to dice rolls) helps exploration and finding strategies quicker than if the game were deterministic
	- network first learns linearly separable concepts, giving already a strong strategy
		- only later on during training does it make more use of the nonlinearities

🗓️ 1995

✍️
- [[Gerald Tesauro]]
