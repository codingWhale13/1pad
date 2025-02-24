#backpropagation #straight-through-estimator #STS-unit #sparse-network #REINFORCE

- backstory
	- computational graph relates inputs and parameters to outputs and training criterion
	- most researchers thought that the graph has to be smooth for gradient-based training to work well
	- however, when nonlinearities (e.g. ReLU) were introduced, things actually improved and this assumption had to be re-evaluated
- motivation: exploit sparse stochastic gating units for conditional computation, allowing for large models with only partially used parameters for each example
	- sparsity of a representation <-> prior that, for a given input, most of the explanatory factors are irrelevant, thus leading to many zeros
- problem: can't directly take gradient of stochastic neurons or hard non-linearities
	- but they're useful, e.g. for creating large sparse networks through conditional computation
- solution: there are 4 different ways to go about this
	- noisy rectifier
		- works by injecting additive or multiplicative noise in a computational graph that is otherwise differentiable
		- injecting noise can be useful not just as a regularizer but also to help explore good parameters and fit the training objective
	- STS (stochastic times smooth) unit, proposed in this work
		- STS decomposes the operation of a binary stochastic neuron into a stochastic binary part and a smooth differentiable part, which approximates the expected effect of the pure stochastic binary neuron to first order
			- for any differentiable function $f$ of $h_i$, we have $E[f(h_i)]=f(p_i)+o(\sqrt{p_i})$
				- not sure what $o$ is...
		- going from activation $a_i$ to STS output $h_i$:
			- $p_i=\text{sigmoid}(a_i)$
			- $b_i\sim\text{Binomial}(\sqrt{p_i})$
			- $h_i=b_i\sqrt{p_i}$
		- benefit: gradient is obtained by standard backprop in a computational graph
	- minimum variance unbiased estimator of gradient for stochastic binary neurons
		- a special case of the REINFORCE algorithm
		- this allows for training with indicator functions
	- straight-through estimator
		- heuristically copying the gradient with respect to the stochastic output directly as a (biased) estimator of the gradient with respect to the argument
			- although biased, this estimator has the right sign when considering a single layer of neurons (this is not guaranteed anymore when back-propagating through more hidden layers
		- idea is to back-propagate through the hard threshold function (1 if the argument is positive, 0 otherwise) as if it had been the identity function
		- straight-through units provide perform really well and are simple to implement

🗓️ 2013

✍️
- [[Yoshua Bengio]]
- [[Nicholas Léonard]]
- [[Aaron Courville]]
