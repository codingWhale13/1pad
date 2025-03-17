# Glossary
- #API Approximate Policy-Iteration
- #AVI Approximate Value-Iteration
- #BBF Bigger, Better, Faster (algorithm)
- #BC-MDP Block Contextual Markov Decision Process
- #CReLU Concatenated Rectified Linear Unit
- #CTPG Cross-Task Policy Guidance (MTRL framework)
- #DBN Deep Belief Network
- #DDPG Deep Deterministic Policy Gradient (algorithm)
- #DL Deep Learning
- #DQN Deep Q-Learning
- #EI Expected Improvement (optimization criterion)
- #FQI Fitted Q-Iteration (algorithm)
- #GP Gaussian Process
- #HL Histogram Loss
- #HO2 Hindsight Off-policy Options
- #KL-divergence Kullback–Leibler divergence
- #LLM Large-Language Model
- #LSTM Long Short-Term Memory
- #MNIST Modified National Institute of Standards and Technology (dataset)
- #MBRL Model-Based Reinforcement Learning
- #MTRL Multi-Task Reinforcement Learning
- #MoE Mixture of Experts
- #POMDP Partially Observable Markov Decision Process
- #ReLU Rectified Linear Unit
- #RL Reinforcement Learning
- #S-ALE Switching Arcade Learning Environment (experiment setup)
- #SAC Soft Actor-Critic
- #SAL Shared domain-Agnostic Latent space (algorithm)
- #SC-MDP Stiefel Contextual Markov Decision Process
- #SF Score Function (estimator)
- #SMBO Sequential Model-Based global Optimization (algorithm)
- #SMDP Semi-Markov Decision Process
- #SPR Self-Predictive Representations (algorithm)
- #SR-SAC Scaled-by-Resetting Soft Actor Critic (algorithm)
- #SR-SPR Scaled-by-Resetting Self-Predictive Representation (algorithm)
- #STS-unit Stochastic Times Smooth unit
- #TCRL Temporal Consistency Reinforcement Learning (algorithm)
- #TD-MPC Temporal Difference Learning for Model Predictive Control (algorithm)
- #TD3 Twin Delayed Deep Deterministic policy gradient (algorithm)
- #TPE Tree-structured Parzen Estimator
- #VQ-VAE Vector Quantized-Variational AutoEncoder

# Tag Counts

```dataview
TABLE WITHOUT ID length(rows) + " - " + tag AS "Tag Occurences"
FROM "notes"
FLATTEN file.tags AS tag
GROUP BY tag
SORT length(rows) DESC
```
