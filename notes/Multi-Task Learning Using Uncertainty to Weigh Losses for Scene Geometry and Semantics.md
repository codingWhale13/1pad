#DL #MTL #classification #regression #ResNet #ASPP

- motivation
	- performance of multi-task learning methods is strongly dependent on relative weighting between the task losses
	- can we do better than manually tuning the loss weights?
- setting: computer vision
	- need to understand both
		- geometry
		- and semantics of the scene
		- -> various regression and classification tasks with different units and scales
	- specifically, these 3 tasks are learned
		- classify objects at a pixel level ("semantic segmentation")
		- instance segmentation
		- pixel-wise metric depth
- background: uncertainty in Bayesian modeling
	- epistemic uncertainty: uncertainty in the model, due to lack of model capacity or training data
	- aleatoric uncertainty: uncertainty w.r.t. information which the data cannot explain
		- data-dependent ("heteroscedastic") uncertainty: depends on input data
		- task-dependent ("homoscedastic") uncertainty: not dependent on input data, but rather a quantity which stays constant for all input data and varies between different tasks
			- captures relative confidence between tasks
			- authors' idea: use this as a basis for weighting losses in multi-task setting
- proposed loss for multi-output model
	- $$\begin{align*}\mathcal L(W,\sigma_1,\sigma_2)&=-\log p(y_1,y_2\mid f^W(x))\\&\propto \frac {1}{2\sigma^2_1}\lVert y_1-f^W(x)\rVert^2+\frac{1}{2\sigma_2^2}\lVert y_2-f^W(x)\rVert^2+\log\sigma_1\sigma_2\\&=\frac{1}{2\sigma^2_1}\mathcal L_1(W)+\frac{1}{2\sigma^2_2}\mathcal L_2(W)+\log \sigma_1\sigma_2\end{align*}$$
		- this weighs multiple loss functions by considering the homoscedastic uncertainty of each task
		- $\mathcal L_1$ is the loss for the first output variable and $\mathcal L_2$ for the second
		- as $\sigma_1$ - the noise parameter for variable $y_1$ - increases, weight of $\mathcal L_1$ decreases
		- can be trivially extended for multiple regression outputs
		- works also for classification likelihoods, but is a bit different
			- uses softmax
			- see paper
	- architecture used for experiments
		- ResNet101, followind by Atrous Spatial Pyramid Pooling (ASPP)
		- split network into separate decoders for each task (3x3 conv layer each)

🗓️ 2018

✍️
- [[Alex Kendall]]
- [[Yarin Gal]]
- [[Roberto Cipolla]]
