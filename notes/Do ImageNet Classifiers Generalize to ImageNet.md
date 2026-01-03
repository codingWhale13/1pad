#ImageNet #classification #generalization

![[Pasted image 20260103005901.png]]

- motivation
	- for ML to be useful, we need methods to generalize well; focus of this study is the robustness of classification models to small variations in the data
	- how well are different image classification methods doing and what kind of errors can lead to drops in performance?
- experiment setup
	1. build new test sets for CIFAR-10 and ImageNet datasets, similar to how the original datasets were created
	2. evaluate models that trained on the canonical datasets on the new test sets to see how well they truly generalize
- findings
	- accuracy drop of 3% - 15%
	- accuracy gains of method A vs. B on canonical test sets -> accuracy gains also on new test sets (i.e., ordering of A's and B's final performance remains the same)
		- in fact, the performance gap widens!
		- this is unlike "conventional wisdom" which suggests that after extensive hyperparameter tuning, the model design overfits on the test sets of these famous datasets (unintentionally, or because some researchers misuse the test set to tweak their method)
- analysis of the results
	- given
		- original test set: $S\in D$
		- new test set: $S'\in D'$
	- the authors divide the difference in accuracy into three factors
		- $L_S-L_{S'}=\underbrace{(L_S-L_D)}_\text{Adaptivity gap}+\underbrace{(L_D-L_{D'})}_\text{Distribution gap}+\underbrace{(L_{D'}-L_{S'})}_\text{Generalization gap}$
	- generalization gap
		- attributed solely to random sampling error
		- doesn't explain the results (see image above), it is unlikely that $S'$ has by chance sampled significantly harder modes of $D'$
	- adaptivity gap
		- quantifies how much adapting a model to $S$ causes the test error $L_S$ to underestimate the population loss $L_D$
		- natural assumption: this is large, i.e., "models have experienced more adaptive overfitting since they are the result of more successive hyperparameter tuning on the same test set"
			- this is however not the case, see image above
	- distribution gap
		- quantifies how different the original distribution $D$ is to the new $D'$
		- the authors tried their best to keep $D'$ close to $D$
		- however, this gap seems to be the main cause of the difference in performance seen in the image above
- other take-aways
	- while most current classification methods are only evaluated on a single test set per benchmark, the authors argue that this is not enough -> instead, we need test data from various sources to gauge generalization
	- it is surprisingly difficult to create a new test set that matches the distribution of an existing dataset

🗓️ 2019

✍️
- [[Benjamin Recht]]
- [[Rebecca Roelofs]]
- [[Ludwig Schmidt]]
- [[Vaishaal Shankar]]
