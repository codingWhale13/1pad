#RL #actor-critic #scaling-up #resnet #layer-norm

![[Pasted image 20250411235908.png]]
- motivation
	- algorithmic choices in RL are important
	- but also: RL performance can improve through scale
	- explore how these are related
	- key question: "Can significant performance improvements in continuous control be achieved by combining parameter and replay scaling with existing algorithmic improvements?" => answer: yes
- introduced method: *BRO* (Bigger, Regularized, Optimistic)
	- what's in a name?
		- bigger: critic has 5M parameters
		- regularized: LayerNorm, weight decay, and full-parameter resets
		- optimistic: dual policy optimistic exploration and non-pessimistic quantile Q-value approximation
	- how is BRO able to scale up the critic?
		- ResNet blocks are crucial
- take-aways
	- naive scaling can harm performance (says "Multi-Task Reinforcement Learning Enables Parameter Scaling" paper)
	- scaling actor was not useful; critic benefits much more from scale
	- n-step returns did not help

🗓️ 2024

✍️
- [[Michal Nauman]]
- [[Mateusz Ostaszewski]]
- [[Krzysztof Jankowski]]
- [[Piotr Miłoś]]
- [[Marek Cygan]]
