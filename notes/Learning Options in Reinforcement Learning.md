#RL #option-learning #SMDP #Q-learning

- background and motivation
	- options framework is a natural way to incorporate temporally extended actions (e.g., macro actions) into RL systems
	- option is defined as triple (set of states in which the option can be initiated, internal policy, termination condition)
		- or more concise: $(I\subseteq S,\pi:\mathcal A\times\mathcal S\mapsto [0,1],\beta:\mathcal S\mapsto [0,1])$
		- if initiation set $I$ and termination condition $\beta$ are specified, RL methods can learn the internal policy of the option
		- an option can only be taken in states that are contained in $I$
		- if option is taken, actions are selected using the option policy $\pi$ until stochastic termination defined by $\beta$
		- primitive options can be viewed as a special case of options
			- -> generalize action-value function to option-value function $Q^\mu(s,o)$ with policy $\mu$ and option $o$
	- MDP augmented by options is an SMDP (Semi-Markov Decision Process)
	- motivation: how can we automatically find initiation sets and termination conditions for options?
- introduced method: an unnamed option finding algorithm
	1. select at random a number of start states $S$ and target states $T$ that will be used to generate random tasks for the agent
	2. for each pair $\langle S,T\rangle$:
	   (a) perform $N_{train}$ episodes of Q-learning, to learn a policy for going from $S$ to $T$
	   (b) perform $N_{test}$ episodes using the greedy policy learned. For all states $s$, count the total number of times $n(s)$ that each state is visited during these trajectories
	3. repeat until the desired number of options is reached:
	   (a) pick the state with the most visitations, $T_{max}=\arg\max_sn(s)$, as the target state for the option
	   (b) compute $n(s,T_{max})$, the number of times each state $s$ occurs on paths that go through $T_{max}$
	   (c) compute $\bar n(T_{max})=avg_s n(s,T_{max})$
	   (d) select all the states $s$ for which $n(s,T_{max})>\bar n(T_{max})$ to be part of the initiation set $I$ for the option
	   (e) complete the initiation set by interpolating between the selected states; the interpolation process is domain-specific
	4. for each option, learn its internal policy; this is achieved by giving a high reward for entering $T_{max}$, and no rewards otherwise. The agent performs Q-learning, by performing episodes which start at random states in $I$ and end when $T_{max}$ is reached, or when the agent exits $I$
- experiments
	- 2 simple gridworld navigation tasks
		- finite state and action space
		- env 1 contains bottleneck states, by dividing the space into "rooms" with connecting "doors"
		- env 2 doesn't contain bottlenecks, just a plain grid
	- after option finding algorithm, SMDP Q-learning learns a policy over options
	- in both environments, useful options are found
		- in particular, the bottlenecks in env 1 were found as target states for options

🗓️ 2002

✍️
- [[Martin Stolle]]
- [[Doina Precup]]
