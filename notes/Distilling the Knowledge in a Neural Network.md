#knowledge-distillation #MoE #cross-entropy-loss #classification #MNIST

- motivation
	- most ML methods can be enhanced through an ensemble but that also makes inference expensive
	- let's distill the knowledge of an ensemble into a single model
- reasoning
	- at the end of the day, we want models to be general
	- if a big model, seeing many training examples, generalizes well, it is generally useful to distill that knowledge into a smaller model that is able to generalize in the same way (because it isn't tied so closely to the training example, having a good teacher instead)
		- note that the transfer set that is used to train the small model could consist purely of unlabeled data
- introduced method: *knowledge distillation*
	- most natural use case: classification
	- use softmax as output layer
	- simplest form of distillation
		- use soft target distribution to let small model match the output layer distribution of the larger model
	- when we have labels, we can use them as well
		- one way: modify soft targets
		- better way: weighted average of two objective functions
			- cross entropy with soft targets
			- cross entropy with correct labels
	- special case of distillation: matching logits
- how is this different to mixture of experts?
	- both MoE and knowledge distillation use specialists trained on subsets of data
	- however:
		- MoE: experts and gating network learn together, making it hard to parallelize 
		- knowledge distillation: specialists are separate, easy to parallelize
		- => parallelization is important with huge datasets!

🗓️ 2015

✍️
- [[Geoffrey Hinton]]
- [[Oriol Vinyals]]
- [[Jeff Dean]]
