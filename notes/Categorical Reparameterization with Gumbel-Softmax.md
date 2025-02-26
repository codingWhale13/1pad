#Gumbel-distribution #classification #softmax #one-hot-encoding #REINFORCE #SF #semi-supervised-learning

![[Pasted image 20250226201342.png]]
- great explanation [here](https://sassafras13.github.io/GumbelSoftmax/)
- motivation
	- standard neural networks are deterministic: we have a fixed bunch of weights and the same input $x$ will always produce the same output $y$ (assuming we don't train)
	- then there are stochastic neural networks, which are useful for things such as:
		- modeling uncertainty
		- anything that samples during training (e.g. in some RL methods)
	- the famous reparameterization trick got us covered
	- but what if some parts of our model are not just stochastic but also defined by a *discrete* distribution? Now there's a problem: picking a category in the forward pass prevents us from flowing the gradient through this stochastic node during backprop
- introduced method: *reparameterizable Gumbel-Softmax distribution* (Gumbel-Softmax)
	- why is it cool? sampling mechanism for categorical variables that can be integrated into neural networks and trained using standard backpropagation
	- how? the Gumbel-Softmax estimator uses a reparameterizable continuous distribution over the simplex that can approximate samples from a categorical distribution
		- this is quite similar to the reparameterization trick for stochasticity, except
			- now we sample from the Gumbel distribution instead of the normal distribution
			- we take the argmax (well, actually the softmax to allow gradient flow) operator instead of the plus operator
	- properties of the Gumbel Softmax distribution
		- both expectation and samples of the distribution interpolate between categorical and uniform distribution:
			- temperature $\tau\to 0$ leads to categorical (= "one hot") distribution
			- temperature $\tau\to\infty$ leads to uniform distribution
- results: better performance and speed for semi-supervised generative models etc.
- related work: there are some existing stochastic gradient estimation techniques for discrete variables
	- score function-based gradient estimators (SF, a.k.a. REINFORCE)
		- a bunch of methods use this approach: NVIL, DARN, MuProp, VIMCO
		- side note: in section 3.2, they talk about the identity $\nabla_{\theta} p_\theta(z)=p_\theta(z)\nabla_\theta \log p_\theta(z)$. This "score function identity" apparently comes from using the chain rule and rearranging: $\nabla_\theta \log p_\theta(z)=\frac{\nabla_\theta p_\theta(z)}{p_\theta(z)}$

🗓️ 2017

✍️
- [[Shixiang Gu]]
- [[Eric Jang]]
- [[Ben Poole]]
