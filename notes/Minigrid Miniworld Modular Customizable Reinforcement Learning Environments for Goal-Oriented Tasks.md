#RL #benchmark #minigrid #miniworld #POMDP

- motivation
	- create modular benchmark for RL, in particular transfer learning
- introduced libraries: *Minigrid* and *Miniworld*
	- properties of these RL environments
		- goal-oriented
		- navigation-based
		- instruction-based
		- modular
		- customizable
		- implemented in Python (not as fast as they could be)
		- minimalistic design paradigm
		- implement POMDPs
		- deterministic
		- sparse reward by default
	- Minigrid
		- discrete action space with 7 options
		- agent observation has 3 items
			- image
			- direction
			- mission
	- Miniworld
		- discrete action space with 8 options
		- agent observation is an RGB image of sizei 80x60
	- use cases
		- curriciulum learning
		- exploration
		- meta learning & transfer learning
			- minigrid -> miniworld
			- directly miniworld
	- implementation details
		- Miniworld uses Pyglet, env is 2.5D (easier than 3D) due to flat floorplan
		- wrappers available, e.g. for stochastic actions
	- install with pip
		- `pip install minigrid`
		- `pip install miniworld`


🗓️ 2023

✍️
- [[Maxime Chevalier-Boisvert]]
- [[Bolun Dai]]
- [[Mark Towers]]
- [[Rodrigo de Lazcano]]
- [[Lucas Willems]]
- [[Salem Lahlou]]
- [[Suman Pal]]
- [[Pablo Samuel Castro]]
- [[Jordan Terry]]
