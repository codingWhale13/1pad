#auto-encoder #VB #SGVB #AEVB #MLE #MAP

![[Pasted image 20250331225619.png]]
- setting and motivation(see also image)
	- components
		- $\{\mathbf z^{(i)}\}_{i=1}^N$: i.i.d. samples from latent variable $\mathbf z$ with prior $p_{\mathbf\theta^*}(\mathbf z)$
			- both the true parameters $\mathbf\theta^*$ and $\mathbf z^{(i)}$ are unknown
		- $\mathbf x^{(i)}$: value of continuous or discrete variable $\mathbf x$, generated from $p_{\mathbf \theta^*}(\mathbf x\mid\mathbf z)$
		- solid lines: generative model $p_{\mathbf \theta}(\mathbf z)p_{\mathbf \theta} (\mathbf x\mid \mathbf z)$
		- dashed lines: variational approximation $q_{\mathbf \phi}(\mathbf z\mid \mathbf x)$ to intractable posterior $p_{\mathbf \theta}(\mathbf z\mid \mathbf x)$
		- variational parameters $\mathbf \phi$ and generative model parameters $\mathbf\theta$ are learned jointly
			- both types of parameters are global parameters -> drawn outside of box
	- assumptions
		- prior $p_{\mathbf\theta^*}(\mathbf z)$ comes from parametric family $p_{\mathbf\theta}(\mathbf z)$
		- likelihood $p_{\mathbf \theta^*}(\mathbf x\mid\mathbf z)$ comes from parametric family $p_{\mathbf \theta}(\mathbf x\mid\mathbf z)$
		- their PDFs are differentiable almost everywhere w.r.t. to both $\mathbf\theta$ and $\mathbf z$
	- goals
		- perform ML or MAP inference on the parameters $\mathbf\theta$
			- allows analyzing the underlying process or generating artificial data with it
		- perform variational inference on the latent variables $\mathbf z$, given an observed $\mathbf x$ for a choice of parameters $\mathbf\theta$
			- useful for data representation tasks
		- approximate marginal inference on $\mathbf x$
			- useful for inference tasks, where a prior over $\mathbf x$ is required
			- e.g. in computer vision: image denoising, inpainting, super-resolution
- two contributions
	- show that a reparameterization of the variational lower bound yields an easy-to optimize lower bound estimator
	- for i.i.d. datasets with continuous latent variables per data point, posterior inference can be made especially efficient
- introduce method: *VAE* (variational auto-encoder)
	- central tool
		- recognition model $q_\phi(\mathbf z\mid\mathbf x)$ approximates intractable true posterior $p_{\mathbf\theta}(\mathbf z\mid\mathbf x)$
	- abstraction of concepts
		- AEVB (Auto-Encoding VB): makes inference and learning efficient by using the SGVB (Stochastic Gradient Variational Bayes) estimator to optimize a recognition model
			- no need for expensive iterative inference schemes, such as MCMC
		- when using a neural network as recognition model -> variational auto-encoder
	- now
	- goal is to differentiate and optimize the lower bound $\mathcal L(\mathbf\theta,\mathbf\phi;\mathbf x^{(i)})=-D_\text{KL}(q_\phi(\mathbf z\mid\mathbf x^{(i)})\mid\mid p_{\mathbf\theta}(\mathbf z))+\mathbb E_{q_\phi(\mathbf z\mid\mathbf x^{(i)})}[\log p_\mathbf\theta (\mathbf x^{(i)}\mid\mathbf z)]$ w.r.t. both the variational parameters $\phi$ and generative parameters $\theta$
	- main part of the paper omitted here, I might come back to this
- fun fact about naming
	- latent variables $\mathbf z$ are also called "code"
	- -> recognition model is a probabilistic "encoder"
	- -> $p_{\mathbf\theta}(\mathbf x\mid\mathbf z)$ is a probabilistic "decoder"

🗓️ 2013

✍️
- [[Diederik P. Kingma]]
- [[Max Welling]]
