#backpropagation #straight-through-estimator

🗓️ 2013

- problem: can't directly take gradient of stochastic neurons or hard non-linearities
	- but they're useful, e.g. for creating large sparse networks through conditional computation
- solution: there are different ways to go about this
	- noisy rectifier
	- STS units: stochastic times smooth
	- unbiased estimator of gradient for stochastic binary neurons
	- straight-through estimator
		- heuristically copying the gradient with respect to the stochastic output directly as an estimator of the gradient with respect to the argument
- results
	- injecting noise can be useful not just as a regularizer but also to help explore good parameters and fit the training objective
	- straight-through units provide perform really well and are simple to implement

✍️
- [[Yoshua Bengio]]
- [[Nicholas Léonard]]
-  [[Aaron Courville]]
