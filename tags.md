# Glossary
- #A3C Asynchronous Advantage Actor Critic
- #ADP Approximate Dynamics Programming
- #AEVB Auto-Encoding Variational Bayes (algorithm)
- #ALE Arcade Learning Environment (benchmark)
- #AGC Adaptive Gradient Clipping (optimizer)
- #ASPP Atrous Spatial Pyramid Pooling
- #API Approximate Policy-Iteration
- #AVI Approximate Value-Iteration
- #BBF Bigger, Better, Faster (algorithm)
- #BC-MDP Block Contextual Markov Decision Process
- #BRO Bigger, Regularized, Optimistic (algorithm)
- #C51 Categorical 51-atom (algorithm)
- #CIFAR Canadian Institute for Advanced Research (image dataset)
- #CPI Classification-based Policy Iteration
- #CReLU Concatenated Rectified Linear Unit
- #CNN Convolutional Neural Network
- #CTPG Cross-Task Policy Guidance (MTRL framework)
- #CQL Conservative Q-Learning
- #DBN Deep Belief Network
- #DP Dynamic Progamming
- #DPG Deterministic Policy Gradient (algorithm)
- #DDPG Deep Deterministic Policy Gradient (algorithm)
- #DL Deep Learning
- #DMC-suite DeepMind Control Suite (benchmark)
- #DQN Deep Q-Network (algorithm)
- #EI Expected Improvement (optimization criterion)
- #EMA Exponential Moving Average (filter, can be used as target)
- #EUREKA Evolution-driven Universal REward Kit for Agent
- #FQI Fitted Q-Iteration (algorithm)
- #GAE Generalized Advantage Estimator
- #GP Gaussian Process
- #HIRL Human Intervention Reinforcement Learning
- #HITL Human-In-The-Loop
- #HL Histogram Loss
- #HO2 Hindsight Off-policy Options
- #IS Importance Sampling
- #KL-divergence Kullback–Leibler divergence
- #KNN K-Nearest Neighbor
- #LASSO Least Absolute Shrinkage and Selection Operator (l1 norm)
- #LGPL Language-Guided Preference Learning
- #LLM Large-Language Model
- #LSTM Long Short-Term Memory
- #MAP Maximum A Posteriori (estimator)
- #MNIST Modified National Institute of Standards and Technology (dataset)
- #MBRL Model-Based Reinforcement Learning
- #MC Monte Carlo
- #MCP Model Context Protocol
- #MLE Maximum Likelihood Estimator
- #MNIST Modified National Institute of Standards and Technology (dataset)
- #MTAN Multi-Task Attention Network
- #MTL Multi-Task Learning
- #MTRL Multi-Task Reinforcement Learning
- #MoE Mixture of Experts
- #PER Prioritized Experience Replay (type of replay buffer)
- #PI Policy Iteration
- #PLPG Probabilistic Logic Policy Gradient
- #POMDP Partially Observable Markov Decision Process
- #PBRS Potential-Based Reward Shaping
- #ReLU Rectified Linear Unit
- #ResNet Residual Neural Network
- #RL Reinforcement Learning
- #RLVR Reinforcement Learning with Verifiable Rewards
- #RNN Recurrent Neural Network
- #RSSM Recurrent State Space Model
- #S-ALE Switching Arcade Learning Environment (experiment setup)
- #SAC Soft Actor-Critic
- #SAL Shared domain-Agnostic Latent space (algorithm)
- #SDPA Scaled Dot-Product Attention
- #SC-MDP Stiefel Contextual Markov Decision Process
- #SEM Simplicial Embedding
- #SF Score Function (estimator)
- #SMBO Sequential Model-Based global Optimization (algorithm)
- #SMDP Semi-Markov Decision Process
- #SGD Stochastic Gradient Descent (algorithm)
- #SGVB Stochastic Gradient Variational Bayes
- #SPR Self-Predictive Representations (algorithm)
- #SR-SAC Scaled-by-Resetting Soft Actor Critic (algorithm)
- #SR-SPR Scaled-by-Resetting Self-Predictive Representation (algorithm)
- #SSL Self-Supervised Learning
- #STARS Share-unique features and task-aware Prioritized Sampling (algorithm)
- #STS-unit Stochastic Times Smooth unit
- #SVHN Street View House Numbers (dataset)
- #TCRL Temporal Consistency Reinforcement Learning (algorithm)
- #TD Temporal Difference (learning method)
- #TD-MPC Temporal Difference Learning for Model Predictive Control (algorithm)
- #TD3 Twin Delayed Deep Deterministic policy gradient (algorithm)
- #TRPO Trust Region Policy Optimization
- #TTD Truncated Temporal Differences (algorithm)
- #TPE Tree-structured Parzen Estimator
- #VB Variational Bayes
- #VI Value Iteration
- #VLM Vision-Language Model
- #VQ-VAE Vector Quantized-Variational AutoEncoder
- #VQA Visual Question Answering

# Tag Counts

```dataview
TABLE WITHOUT ID length(rows) + " - " + tag AS "Tag Occurences"
FROM "notes"
FLATTEN file.tags AS tag
GROUP BY tag
SORT length(rows) DESC
```
