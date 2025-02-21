#RL #DL #action-shaping #multi-discrete-actions #video-games

- transformations of the action space = "action space shaping"
	- analogous to reward shaping
- types of action spaces considered
	- discrete
	- multi-discrete
		- each dim of the action vector can have different number of possibilities
	- continuous
- domain-specific action space modifications can be crucial for success, e.g. in learning video games
	- removal of actions
	- discretization of continuous action spaces
	- convert multi-discrete actions to discrete
- paper gives overview of recent methods and how they tackled different envs
- results of authors' experiments (in order of general usefulness):
	- not useful: converting multi-discrete to discrete action spaces
	- useful for learning at all, but might decrease performance: removing actions
	- useful: discretizing continuous action spaces

🗓️ 2020

✍️
- [[Anssi Kanervisto]]
- [[Christian Scheller]]
- [[Ville Hautamäki]]
