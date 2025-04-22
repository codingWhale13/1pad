#SEM #SSL #BYOL #CIFAR #ImageNet

![[Pasted image 20250422235018.png]]
- motivation
	- Self-Supervised Learning (SSL) is effective in learning representations
	- but it also matters what type of reprsentation is learned
	- Simplicial Embeddings (SEM) are especially powerful, this paper zooms in on them
	- SSL may be used to learn sparse and overcomplete representations
		- discretization during pre-training is not necessary to achieve a sparse representation
- background: SEM
	- representation (coming from e.g. an encoder) is projected into $L$ simplices $z_i$ of $V$ dims each, using softmax
		- see image
		- softmax temperature parameter $\tau$ scales the $z_i$ for $i=1,\dots,L$
			- the lower, the stronger the bias toward sparsity
			- controls the trade-off between training loss and generalization gap
		- in math
			- $\bar z_i\coloneqq \sigma_\tau (z_i)$
			- $\sigma_\tau(z_i)_j=\frac{e^{z_{ij}/\tau}}{\sum_{k=1}^V e^{z_{ik}}/\tau}$ (softmax)
			- $\hat z\coloneqq \text{Concat}(\bar z_1,\dots,\bar z_L)$, $\forall i\in 1,\dots,L,\forall j\in 1,\dots,V$
	- SEM is a re-normalization, leading to better generalization
		- see paper for proof
- results
	- SEM empirically improves test accuracy on CIFAR-100 and ImageNet

🗓️ 2022

✍️
- [[Samuel Lavoie]]
- [[Christos Tsirigotis]]
- [[Max Schwarzer]]
- [[Ankit Vani]]
- [[Michael Noukhovitch]]
- [[Kenji Kawaguchi]]
- [[Aaron Courville]]
