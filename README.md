# 🧠 Assignment 2 — Q-Learning Parameter Sensitivity Study
**Course:** CSCN8020 – Reinforcement Learning Programming  
**Student:** Krishna Reddy Bovilla  **ID:** 9050861  
**Date:** October 2025  
**Repository:** [Reinforcement-Learning-A2](https://github.com/bkrishnareddy-ai/Reinforcement-Learning-A2)

---

## 1. Project Overview
This project investigates the **sensitivity of Q-Learning** to key hyperparameters — the **learning rate (α)** and **exploration factor (ε)** — using the **Taxi-v3 environment** from OpenAI Gymnasium.  
Through extensive experimentation, training logs, and visual analysis, the study identifies how these parameters influence **learning stability**, **convergence rate**, and **policy efficiency**.

The goal is to produce a *quantitative and qualitative assessment* supported by **empirical metrics**, **comparative plots**, and **reasoned commentary**, fulfilling all assignment criteria.

---

## 2. Methodology Summary

### 2.1 Algorithm
Q-Learning is an *off-policy Temporal Difference (TD)* method that learns the optimal state–action value function by iteratively updating a Q-table:

Q(s,a) ← Q(s,a) + α [r + γ max Q(s′,a′) − Q(s,a)]

The balance between exploration (ε-greedy policy) and exploitation is tuned using ε, while the update aggressiveness is controlled by α.

### 2.2 Environment Configuration

| Parameter | Symbol | Value / Range | Purpose |
|------------|---------|---------------|----------|
| Learning Rate | α | 0.001 → 0.2 | Magnitude of Q-updates |
| Exploration Factor | ε | 0.1 → 0.3 | Controls stochastic action choice |
| Discount Factor | γ | 0.9 | Balances short-term vs. long-term reward |
| Episodes | — | 5,000 per model | Training horizon |
| Reward Structure | — | +20 (success), –10 (illegal), –1 (step) | Defines task incentives |

### 2.3 Evaluation Metrics
- **Average Reward:** Mean return per episode  
- **Average Steps:** Mean number of steps to complete an episode  
- **Reward Variance:** Indicator of policy stability  
- **Smoothed Reward Curves:** 50-episode rolling averages  

---

## 3. Repository Structure

```
Reinforcement-Learning-A2/
│
├── Assignment2.ipynb
├── README.md
├── requirements.txt
├── .gitignore
├── QLearning_Report.pdf
```

---

## 4. Environment Setup

### Step 1: Clone the Repository
```bash
git clone https://github.com/bkrishnareddy-ai/Reinforcement-Learning-A2.git
cd Reinforcement-Learning-A2
```

### Step 2: Create Conda or Virtual Environment
```bash
conda create -n rl_env python=3.10 -y
conda activate rl_env
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Launch Jupyter Notebook
```bash
jupyter notebook Assignment2.ipynb
```

---

## 5. Experimentation Workflow

| Step | Title | Objective |
|------|--------|------------|
| 1 | Implement Q-Learning Algorithm | Define agent class, Q-table initialization, update loop |
| 2 | Base Model (α=0.1, ε=0.1) | Establish baseline metrics |
| 3 | Learning Rate Sweep | Evaluate α ∈ [0.001, 0.01, 0.2] |
| 4 | Exploration Factor Sweep | Evaluate ε ∈ [0.1, 0.2, 0.3] |
| 5 | Metrics Summary Table | Compare models quantitatively |
| 6 | Pygame Visualization | Qualitative task demonstration |
| 7 | Enhanced Metrics | Rolling averages and reward statistics |
| 8 | Multi-Panel Comparison | Consolidated 2×2 visual analysis |
| 9 | Retraining with Best Parameters | Validate optimal configuration (α=0.2, ε=0.1) |

---

## 6. Results Summary

### 6.1 Base Configuration (α=0.1, ε=0.1)

| Metric | Value |
|--------|--------|
| Average Return | –37.24 |
| Average Steps | 40.67 |
| Best Reward | +15.00 |

**Observations:**  
The base agent exhibited consistent improvement, converging by ≈ episode 2000. The learning trajectory stabilized, showing an optimal baseline for comparison.

---

### 6.2 Learning Rate Variation (ε=0.1)

| α | Avg. Return | Avg. Steps | Qualitative Comment |
|--|--|--|--|
| 0.001 | –264.19 | 187.36 | Stagnation; negligible updates |
| 0.01 | –205.26 | 154.46 | Partial convergence, low responsiveness |
| 0.2 | –21.04 | 29.41 | Rapid and stable learning |

*(Refer to Figure 2: Effect of Learning Rate on Convergence.)*

---

### 6.3 Exploration Factor Variation (α=0.1)

| ε | Avg. Return | Avg. Steps | Observation |
|--|--|--|--|
| 0.1 | –37.24 | 40.67 | Balanced exploration |
| 0.2 | –51.35 | 43.55 | Prolonged exploration, slower learning |
| 0.3 | –69.29 | 46.92 | Over-exploration, oscillating performance |

*(Refer to Figure 3: Impact of Exploration Rate on Learning Stability.)*

---

### 6.4 Optimized Retraining (α=0.2, ε=0.1)

| Metric | Base | Optimized | % Improvement |
|--|--|--|--|
| Avg. Reward | –37.24 | –11.77 | +68 % |
| Avg. Steps | 40.67 | 23.60 | –42 % |
| Reward Variance | 378.1 | 104.5 | –72 % |

*(Refer to Figure 4: Retraining Comparison of Base vs. Optimized Model.)*

---

## 9. Key Takeaways
- Higher learning rates accelerate convergence significantly without instability.  
- Optimal exploration (ε=0.1) maintains stable and efficient policy learning.  
- Retraining with α=0.2, ε=0.1 improved average reward by 68% and reduced episode length by 42%.  
- Reinforces the exploration–exploitation trade-off principle.

---

## 10. References
1. Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction* (2nd ed.). MIT Press.  
2. Kaelbling, L. P., Littman, M. L., & Moore, A. W. (1996). *Reinforcement Learning: A Survey*. *JAIR*, 4, 237–285.  
3. OpenAI Gymnasium (2024). *Taxi-v3 Environment Documentation*.

---

## 11. Compliance
✅ Implementation of Q-Learning algorithm.  
✅ Metrics, observations, and comments per parameter change.  
✅ Multiple plots supporting analytical discussion.  
✅ Retrained model comparison with quantifiable performance improvement.  
✅ Ready for submission and professional evaluation.
