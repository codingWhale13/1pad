
- motivation
	- what does interpretability mean in ML, is there a wholistic definition? (spoiler: no)
	- author questions the oft-made assertions that linear models are interpretable and that deep neural networks are not
- desiderata of interpretability research
	- trust (which itself can mean a lot of things)
	- causality (however, causal inference methods tend to have too strong assumptions)
	- transferability (generalizing from training to test set is nowhere near real-world human generalization abilities)
	- informativeness (being helpful to the human, even if not necessarily transparent)
	- fair and ethical decision making
	- transparency
		- at the level of the entire model (simulatability)
		- at the level of individual components such as parameters (decomposability)
		- at the level of the training algorithm (algorithmic transparency)
- take-aways
	- in the academic literature, few authors articulate precisely what interpretability means or precisely how their proposed solution is useful
	- while the machine-learning objective might be to reduce error, the real-world purpose is to provide useful information
	- the weights of a linear model might seem intuitive, but they can be fragile with respect to feature selection and preprocessing
	- linear models lose simulatability or decomposability, respectively
		- -> when choosing between linear and deep models, you must often make a tradeoff between algorithmic transparency and decomposability


🗓️ 2018

✍️
- [[Zachary C. Lipton]]
