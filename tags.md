# Glossary
- #BC-MDP Block Contextual Markov Decision Process
- #DDPG Deep Deterministic Policy Gradient (algorithm)
- #DL Deep Learning
- #LLM Large-Language Model
- #LSTM Long Short-Term Memory
- #MBRL Model-Based Reinforcement Learning
- #MTRL Multi-Task Reinforcement Learning
- #MoE Mixture of Experts
- #RL Reinforcement Learning
- #SAC Soft Actor-Critic
- #SC-MDP Stiefel Contextual Markov Decision Process
- #SF Score Function (estimator)
- #SPR Self-Predictive Representations (algorithm)
- #SR-SAC Scaled-by-Resetting Soft Actor Critic (algorithm)
- #SR-SPR Scaled-by-Resetting Self-Predictive Representation (algorithm)
- #STS-unit Stochastic Times Smooth unit
- #TCRL Temporal Consistency Reinforcement Learning (algorithm)
- #TD3 Twin Delayed Deep Deterministic policy gradient (algorithm)
- #VQ-VAE Vector Quantized-Variational AutoEncoder

# Tag Counts

```dataview
TABLE WITHOUT ID length(rows) + " - " + tag AS "Tag Occurences"
FROM "notes"
FLATTEN file.tags AS tag
GROUP BY tag
SORT length(rows) DESC
```
