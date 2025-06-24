# Deep Reinforcement Learning for Portfolio Optimization

---

## Project Overview

This project explores the classical **Merton Portfolio Optimization Problem** through the lens of **Deep Reinforcement Learning (DRL)**. We implement the **Advantage Actor-Critic (A2C)** algorithm to learn optimal lifetime strategies for consumption and investment, and compare these with Merton’s elegant but idealized analytical solution.

Our goal is to investigate whether DRL can approximate or outperform classical approaches in dynamic, real-world financial environments where traditional assumptions no longer hold.

---

## Motivation

Merton’s original model assumes:
- Constant market parameters (μ, σ, r)
- Perfect market conditions with no transaction costs
- Continuous trading and rebalancing

Such ideal assumptions limit the model’s real-world applicability.

> We aim to determine whether a DRL agent can learn robust policies in more realistic settings — capturing complex behaviors without relying on closed-form solutions.

---

## The Classical Merton Model

Merton (1971) proposed a continuous-time model for optimizing consumption and investment decisions over an investor’s lifetime.

Key results:
- **Optimal portfolio allocation** (π*): Constant fraction in risky assets  
- **Optimal consumption plan**: Proportional to wealth with time-dependent consumption rate

While analytically elegant, it fails to accommodate market frictions or changing dynamics.

---

## DRL Reformulation

We reformulate the investment-consumption task as a **reinforcement learning problem**, using a custom **OpenAI Gym** environment:

- **State**: Wealth, time step remaining  
- **Action**: % allocation to risky asset, consumption amount  
- **Reward**: Utility of consumption (CRRA utility function)

### Why A2C?

- Handles **continuous action spaces**
- Combines **policy and value estimation**
- Suitable for **long-horizon planning** problems like lifetime investment

---

## 🛠Environment & Training

- Each episode simulates a full investor lifetime (e.g., 0 to T years)
- Wealth evolves based on investment returns and consumption decisions
- A2C agent is trained over thousands of episodes
- Learning curve shows convergence to a near-optimal policy over time

---

## Evaluation & Comparison

| Method            | Allocation Strategy       | Consumption Strategy        | Flexibility |
|------------------|---------------------------|-----------------------------|-------------|
| Merton (Closed-form) | Constant π*, c(t) from formula | Time-varying κ(t) | Limited by assumptions |
| A2C Agent         | Learned via policy gradient | Learned via reward optimization | Highly adaptable |

The A2C agent successfully replicates and in some cases improves upon Merton’s strategy, particularly under conditions that deviate from classical assumptions.

---

## Insights & Future Work

### Key Takeaways:
- Deep RL agents can **internalize optimal policies** without needing explicit formulas
- DRL provides a promising tool for **financial decision-making under uncertainty**

### Future Enhancements:
- Introduce **transaction costs**, **stochastic interest rates**, and **multiple asset classes**
- Test DRL performance in **non-stationary or regime-switching markets**
- Explore **alternative architectures** (e.g., PPO, SAC)

---

## References

- Merton, R.C. (1971). *Optimum Consumption and Portfolio Rules in a Continuous-Time Model*
- Sutton & Barto (2018). *Reinforcement Learning: An Introduction*
- OpenAI Gym: [https://www.gymlibrary.dev](https://www.gymlibrary.dev)

---

> 💡 *"In modern finance, optimization isn’t just about solving equations — it’s about empowering intelligent agents to make decisions that adapt, learn, and evolve with the market."*

---
