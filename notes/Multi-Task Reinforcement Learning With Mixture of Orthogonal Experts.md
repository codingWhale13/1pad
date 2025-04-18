#RL #MTRL #MoE #SC-MDP #BC-MDP #Gram-Schmidt #Stiefel-manifold

- motivation
	- open challenge of learning a shared set of diverse representations
- introduced method: *MOORE* (Mixture of Orthogonal Experts)
	- novel approach for representation learning in MTRL
	- idea: using policy $\pi(a\vert s,c)$, each task can interpolate its relevant representation from the sub-space spanned by the $k$-orthonormal representations $V_s$
		- $s$ is state and $c$ is context, e.g. task-id
	- how?
		- new MDP formulation: SC-MDP (Stiefel Contextual Markov Decision Process)
			- builds on BC-MDP (Block Contextual Markov Decision Process)
		- uses a Gram-Schmidt process to shape a shared subspace of representations generated by a mixture of experts
			- Gram-Schmidt process orthogonalizes a set of linearly independent vectors; in other words it makes the vectors perpendicular to each other
		- latent representations belong to the Stiefel manifold
- results
	- benchmarks: MiniGrid and MetaWorld
	- slightly beats other methods (MoE, PCGrad, MTPPO)
	- multi-head architecture performs much better than single-head architecture
	- transfer learning also possible

🗓️ 2024

✍️
- [[Ahmed Hendawy]]
- [[Jan Peters]]
- [[Carlo D'Eramo]]
