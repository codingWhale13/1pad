#representation-learning #VQ-VAE #auto-encoder

- background: Variational Auto-Encoder (VAE)
	- encoder, parameterizing a posterior distribution $q(z\vert x)$ of discrete latent random variables $z$ given the input data $x$
	- prior distribution $p(z)$
	- decoder with distribution $p(x\vert z)$ over input data
- introduced method: *VQ-VAE*
	- posterior and prior are categorical
	- samples drawn using an embedding table
	- forward steps
		- input $x$ gets encoded to $z_e(x)$
		- $z_e(x)$ is passed through discretization bottleneck to get discrete latent variable $z$
			- nearest-neighbor lookup in embedding space $e$
	- training
		- using straight-through gradient estimation, mapping from $z_e(x)$ to $z_q(x)$
		- Vector Quantization (VQ) - one of the simplest dictionary learning algorithms - learns the embedding space
- results show versatility of VQ-VAE
	- generating 128×128 color image
	- sampling action conditional video sequences
		- VQ-VAE can be used to predict sequences (in experiment: 10 frames) in latent space without resorting to pixel space
	- doing audio speaker conversion
		- the learned discrete latent codes are closely related to phonemes - impressive because obtained fully unsupervised

🗓️ 2018

✍️
- [[Aaron van den Oord]]
- [[Oriol Vinyals]]
- [[Koray Kavukcuoglu]]
