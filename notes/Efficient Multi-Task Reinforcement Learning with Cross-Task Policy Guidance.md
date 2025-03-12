#CTPG #MTRL #RL #SAC #hindsight-correction

- motivation
	- in MTRL, most work focuses on parameter sharing ("implicit knowledge sharing")
	- but what about exploiting cross-task similarities more directly?
		- -> control policies of solved tasks can help in unsolved tasks
- introduced method: *CTPG* (Cross-Task Policy Guidance)
	- authors use SAC as underlying RL method
		- SAC for training control policies
		- discrete action space variant of SAC for training guide policies
			- hindsight off-policy correction is used
	- CTPG only manipulates the data collection process
		- for each task $i$, there's now also a guide policy $\Pi_i^g$ , outputting a task index $j_t$ which can serve as behavior policy for task $i$
		- for each task $i$, we have
			- control policy $\pi_i(a_t\mid s_t)$
			- control Q-value function $Q_i(s_t,a_t)$
			- guide policy $\Pi^g_i(j_t,s_t)$ outputs a task index $j_t\in\mathbb T$
			- guide Q-value function $Q_i^g(s_t,j_t)$ predicts expected n-step return when selecting different control policies
	- two gating mechanisms are used to improve CTPG's performance
		- extension 1: policy-filter gate
			- addresses the fact that not all policies are beneficial for guidance
			- adaptively assigns each task-policy $i$ an indicator if that task policy is assumed to be beneficial for guidance or not
			- $m_j(s_t)=\begin{cases}1,&Q_i^g(s_t,j)\geq V_i(s_t)\\0,&Q_i^g(s_t,j)< V_i(s_t)\end{cases}$
		- extension 2: guide-block filter
			- addresses the fact that not all tasks need guidance
			- this is decided based on SAC's temperature parameter $\alpha_i$
				- if task $i$ has below-average $\log \alpha_i$, it is considered to need guidance

🗓️ 2024

✍️
- [[Jinmin He]]
- [[Kai Li]]
- [[Yifan Zang]]
- [[Haobo Fu]]
- [[Qiang Fu]]
- [[Junliang Xing]]
- [[Jian Cheng]]
