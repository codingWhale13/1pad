#CNN #ResNet #stochastic-depth #backpropagation #dropout

![[Pasted image 20250418215704.png]]
- motivation
	- deep CNNs (hundreds of layers) perform well but have challenges
		- gradients can vanish
		- forward flow diminishes
		- slow training
- introduced method: *stochastic depth*
	- key idea: train short networks, test deep networks
	- procedure
		- start with very deep networks
		- during training, randomly bypass a subset of layers with identity
			- -> very similar to resnet, but random
		- survival probabilities
			- $p_l$ are hyperparameters
			- set as smooth decay from 1 to $p_L>0$:
				- $p_\ell=1-\frac \ell L (1-p_L)$
			- layer $f_\ell$ is bypassed with probability $(1-p_\ell)$
			- so we're left with just one hyperparamter: $p_L$
				- if $p_L=0.5$, expected number of ResBlocks during training is $3L/4$
				  -> saves 25% of training cost
- results
	- can increase depth of ResNets beyond 1200 layers
	- faster training because less work
	- reduced test error because
		- shorter chain of forward and backward propagation -> stronger gradients, especially in the earlier layers during backprop
		- stochastic depth nets $\approx$ ensemble of networks of different depths
	- similar to dropout, stochastic depth provides regularization

🗓️ 2016

✍️
- [[Gao Huang]]
- [[Yu Sun]]
- [[Zhuang Liu]]
- [[Daniel Sedra]]
- [[Kilian Q. Weinberger]]
