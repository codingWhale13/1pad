#PathNet #scaling-up #A3C #dropout #stochastic-depth #swapout #atari-2600 #SVHN #CIFAR #MNIST

![[Pasted image 20250418221635.png]]
- motivation
	- to enable better generalization and continual learning, a giant neural network with multiple paths could be beneficial
	- this giant network should be able to
		- learn multiple "agents" learn in parallel
			- agent = unit of evolution
		- sharing parameters if possible
		- do transfer learning
		- do multitask learning
		- continuously learn
- introduced method: *PathNet*
	- modular deep neural net
		- $L$ layers, each having $M$ modules
		- each module is a simple neural net, can be CNN or MLP
		- for each layer, the outputs of the modules are summed before being handed over to the next layer
		- weights and biases are learned using gradient descent
	- evolution determines subset of parameters to be trained
		- evolution meaning tournament selection genetic algorithm
		- analogy
			- evolutionary dropout
			- evolutionary swapout (dropout + stochastic depth)
		- pathways (genotypes)
			- random init
			- serial implementation
				- pick random genotype
				- train its pathway for $T$ epochs
				- fitness = negative classification error
			- but with A3C, 64 genotypes are parallelized
	- transfer learning
		- once a task has been trained for the desired time, its best pathway is fixed
- evaluation
	- MNIST
	- Atari
	- CIFAR
	- SVHN
	- labyrinth games

🗓️ 2017

✍️
- [[Chrisantha Fernando]]
- [[Dylan Banarse]]
- [[Charles Blundell]]
- [[Yori Zwols]]
- [[David Ha]]
- [[Andrei A. Rusu]]
- [[Alexander Pritzel]]
- [[Daan Wierstra]]
