#HIRL #model-free-RL #RL #safety #alignment #HITL

- motivation
	- how can an RL agent explore and learn without making a single mistake that causes serious damage? (think: self-driving cars)
	- in model-free RL, the only solution is: human supervision
	- but does this even work and is it scalable? (spoiler: it works okay in Atari, but doesn't scale)
- background
	- suboptimal actions are fine (e.g. driving slow), but we don't want a catastrophe (e.g. hitting a pedestrian)
	- training in simulation would be fine (errors there don't hurt anyone), but transfer to the real-world is unrealistic, because humans (e.g. pedestrians walking over the street) can't be modeled accurate enough in many cases)
- method: human intervention RL (HIRL)
	- goal: learn an RL task without a single catastrophe
	- there are three phases to HIRL
		1. human oversight phase
			- for the first 4.5h of training, a human watched every frame (game is slowed down) and intervenes by blocking the agent from taking unsafe actions
		2. blocker training
			- game is paused, and CNN is trained to imitate human blocking decisions
		3. blocker oversight phase
			- for the next 12-24h of training, the blocker takes over from human and game is run at usual speed
	- RL-algo agnostic, anything works
		- -> the blocker imitates the human overseer in a modular way: it can be trained on some data and act as a safeguard for a different agent (on the same env... makes sense, because we don't care about how the RL algo arrived at this decision, we just know it's probably dangerous)
- experiments
	- HIRL is applied to some Atari games: Pong, Space Invaders, Road Runner
	- the catastrophic scenarios are somewhat reasonable heuristics in space invaders (don't shoot defense) and road runner (don't die on level 1), but pretty arbitrary in Pong (don't let the paddle enter the bottom section of the screen)
		- bottom line: they focus on locally avoidable catastrophes, because the more long-term ones are not feasible for the human to block in time
- take-aways
	- there's a serious scalability problem for human intervention in RL
	- possible solutions are
		- fail faster, seek out catastrophes
		- make human blockers more data-efficient (how, they don't say)
		- make RL more data-efficient
		- model-based RL

🗓️ 2017

✍️
- [[William Saunders]]
- [[Girish Sastry]]
- [[Andreas Stuhlmüller]]
- [[Owain Evans]]
