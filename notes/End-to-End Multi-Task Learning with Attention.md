#MTAN #CNN #MTL

![[Pasted image 20250330232724.png]]
- motivation
	- MTL holds two key challenges
		- network architecture (how to share)
		- loss function (how to balance tasks)
	- most works focus on one of these; this paper addresses both
- introduced method: *MTAN* (Multi-Task Attention Network)
	- two key components
		- global feature pool -> learns task-shared features
		- task-specific attention modules -> learns task-specific features
			- same architecture, but individually trained weights
			- each applies a soft attention mask to a particular layer of the shared network, to learn task-specific features -> attention masks are automatically learned feature selectors
	- architectures
		- MTAN can be built on any feed-forward neural net
		- authors tried
			- VGG-16 (see image)
			- wide residual network
			- SegNet
	- some details
		- $p^{(j)}$: shared features in $j$th layer/block of the shared network
		- $a_i^{(j)}$: learned attention mask for task $i$ in layer $j$
		- $\hat a_i^{(j)}=a_i^{(j)}\odot p^{(j)}$: task-specific features for task $i$ in layer $j$
		- for layers $j\geq 2$ and conv layers $f^{(j)},g^{(j)}_i,h^{(j)}_i$, we have
			- $a^{(j)}_i =  h^{(j)}_i (g_{i}^{j} ([u^{(j)} ; f^{(j)} ( \hat{a}^(j-1)]))$
		- loss function $\mathcal L_\text{tot}( X, Y_{1:K})=\sum_{i=1}^K \lambda_i\mathcal L_i (X, Y_i)$
			- where $\lambda_i$ are task weightings, manually picked based on scenario
			- semantic segmentation -> pixel-wise cross-entropy
			- depth estimation -> $L_1$ norm
			- surface models -> element-wise dot product at each normalized pixel
			- classification tasks -> cross-entropy loss

🗓️ 2019

✍️
- [[Shikun Liu]]
- [[Edward Johns]]
- [[Andrew J. Davison]]
