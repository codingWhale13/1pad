#RL #safe-RL #logic-reasoning #probabilistic-logic-shields #PLPG

![[Pasted image 20250619104905.png]]
- motivation
	- in safe RL, shielding is a common technique, preventing the agent to take unsafe actions
		- the shields are rejection-based
		- the shields are usually deterministic (action is either safe or unsafe)
	- but this is difficult to integrate with end-to-end RL methods
- introduced method: *PLS* (Probabilistic Logic Shields)
	- uses probabilistic shielding
		- does not assume perfect sensors
		- does not require knowledge of the underlying MDP
	- provides convergence guarantees (unlike rejection-based shields)
- introduced method: *PLPG* (Probabilistic Logic Policy Gradient)
	- it is possible that no optimal policies exist in the safe policy space -> in this case, PLPG aims to find a policy that is as safe as possible

🗓️ 2023

✍️
- [[Wen-Chi Yang]]
- [[Giuseppe Marra]]
- [[Gavin Rens]]
- [[Luc De Raedt]]
