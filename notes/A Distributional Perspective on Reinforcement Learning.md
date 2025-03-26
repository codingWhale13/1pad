#RL #ALE #C51

- motivation
	- the authors argue that modeling the expected cumulative return value is not enough
		- instead, model value distribution, to implement risk-aware behavior
- introduced method: *C51* (Categorical 51-atom algorithm)
	- uses distributional Bellman equation
	- Categorical algorithm
		- tested with 5, 11, 21, and 51 returns
		- using 51 atoms performs especially well
- results
	- when using a policy aiming to maximize expected return
	- learning distributions matters in the presence of approximation
		- reduced chattering
		- state aliasing
		- richer set of predictions
		- framework for inductive bias
		- well-behaved optimization

🗓️ 2017

✍️
- [[Marc G. Bellemare]]
- [[Will Dabney]]
- [[Rémi Munos]]
