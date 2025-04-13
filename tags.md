# Glossary
- #AEVB Auto-Encoding Variational Bayes (algorithm)
- #ALE Arcade Learning Environment (benchmark)
- #AGC Adaptive Gradient Clipping (optimizer)
- #API Approximate Policy-Iteration
- #AVI Approximate Value-Iteration
- #BBF Bigger, Better, Faster (algorithm)
- #BC-MDP Block Contextual Markov Decision Process
- #BRO Bigger, Regularized, Optimistic (algorithm)
- #C51 Categorical 51-atom (algorithm)
- #CReLU Concatenated Rectified Linear Unit
- #CNN Convolutional Neural Network
- #CTPG Cross-Task Policy Guidance (MTRL framework)
- #DBN Deep Belief Network
- #DPG Deterministic Policy Gradient (algorithm)
- #DDPG Deep Deterministic Policy Gradient (algorithm)
- #DL Deep Learning
- #DMC-suite DeepMind Control Suite (benchmark)
- #DQN Deep Q-Network (algorithm)
- #EI Expected Improvement (optimization criterion)
- #EMA Exponential Moving Average (filter, can be used as target)
- #FQI Fitted Q-Iteration (algorithm)
- #GAE Generalized Advantage Estimator
- #GP Gaussian Process
- #HL Histogram Loss
- #HO2 Hindsight Off-policy Options
- #IS Importance Sampling
- #KL-divergence Kullback–Leibler divergence
- #LASSO Least Absolute Shrinkage and Selection Operator (l1 norm)
- #LLM Large-Language Model
- #LSTM Long Short-Term Memory
- #MAP Maximum A Posteriori (estimator)
- #MNIST Modified National Institute of Standards and Technology (dataset)
- #MBRL Model-Based Reinforcement Learning
- #MC Monte Carlo
- #MLE Maximum Likelihood Estimator
- #MTAN Multi-Task Attention Network
- #MTL Multi-Task Learning
- #MTRL Multi-Task Reinforcement Learning
- #MoE Mixture of Experts
- #PER Prioritized Experience Replay (type of replay buffer)
- #PI Policy Iteration
- #POMDP Partially Observable Markov Decision Process
- #ReLU Rectified Linear Unit
- #RL Reinforcement Learning
- #RSSM Recurrent State Space Model
- #S-ALE Switching Arcade Learning Environment (experiment setup)
- #SAC Soft Actor-Critic
- #SAL Shared domain-Agnostic Latent space (algorithm)
- #SC-MDP Stiefel Contextual Markov Decision Process
- #SF Score Function (estimator)
- #SMBO Sequential Model-Based global Optimization (algorithm)
- #SMDP Semi-Markov Decision Process
- #SGD Stochastic Gradient Descent (algorithm)
- #SGVB Stochastic Gradient Variational Bayes
- #SPR Self-Predictive Representations (algorithm)
- #SR-SAC Scaled-by-Resetting Soft Actor Critic (algorithm)
- #SR-SPR Scaled-by-Resetting Self-Predictive Representation (algorithm)
- #STARS Share-unique features and task-aware Prioritized Sampling (algorithm)
- #STS-unit Stochastic Times Smooth unit
- #TCRL Temporal Consistency Reinforcement Learning (algorithm)
- #TD Temporal Difference (learning method)
- #TD-MPC Temporal Difference Learning for Model Predictive Control (algorithm)
- #TD3 Twin Delayed Deep Deterministic policy gradient (algorithm)
- #TRPO Trust Region Policy Optimization
- #TTD Truncated Temporal Differences (algorithm)
- #TPE Tree-structured Parzen Estimator
- #VB Variational Bayes
- #VI Value Iteration
- #VQ-VAE Vector Quantized-Variational AutoEncoder

# Tag Counts

```dataview
TABLE WITHOUT ID length(rows) + " - " + tag AS "Tag Occurences"
FROM "notes"
FLATTEN file.tags AS tag
GROUP BY tag
SORT length(rows) DESC
```
