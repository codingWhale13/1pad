#MTRL #scaling-up #Meta-World #SAC

- motivation
	- recently, many fancy MTRL methods have emerged
	- but could their improvements mostly be due to scale (parameter count)?
	- maybe we don't need such sophisticated architectures
- experiments
	- considered methods
		- MTMHSAC (multi-task multi-head SAC)
		- Soft-Modularization
		- PaCo
		- MOORE
	- benchmark
		- Meta-World MT10
		- MT50
	- main result
		- simple method MTMHSAC outperforms other methods, when scaled up to similar parameter count
		- increasing parameter count even more also increases performance
			- (the same would likely be true for the other methods, though)
- other take-aways
	- value function benefits more from scaling than policy
		- assumed reason: Q-function has to fit multiple state-action functions
	- more tasks -> less plasticity loss
	- nice visualization of different methods (but too low-res to include here)

🗓️ 2025

✍️
- [[Reginald McLean]]
- [[Evangelos Chatzaroulas]]
- [[J.K. Terry]]
- [[Isaac Woungang]]
- [[Nariman Farsad]]
- [[Pablo Samuel Castro]]
