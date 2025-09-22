# HuggingFace-Course-Notes
Notes from the huggingface Deep Reinforcment Learning course


# Reinforcement Learning Framework

## The RL Process
- RL is a loop of:
  **State → Action → Reward → Next State**
- Source: *Reinforcement Learning: An Introduction* by Sutton & Barto
<img width="1400" height="787" alt="image" src="https://github.com/user-attachments/assets/587bd444-6ac3-490c-90b2-0dbba3d22cc6" />

### Example: Platform Game
1. Agent receives initial state `S0` (first game frame).
2. Agent takes action `A0` (e.g., move right).
3. Environment transitions to new state `S1` (new frame).
4. Environment gives reward `R1` (e.g., survived → +1).
5. Loop continues: `(State, Action, Reward, Next State)`.

**Goal of the Agent**: Maximize *cumulative reward* (expected return).
<img width="1305" height="576" alt="image" src="https://github.com/user-attachments/assets/d5c4d87c-12f2-47a8-bbe3-4e1fc16662a4" />

---

## Reward Hypothesis
- All goals can be described as maximizing expected return.
- Best behavior = actions that maximize expected cumulative reward.

---

## Markov Property
- RL process = **Markov Decision Process (MDP)**.
- **Markov Property**:  
  The current state contains all the information needed for the next action.  
  → Past history is not required.

---

## Observations vs States
- **State (s)**: Complete description of the environment.  
  - Example: Chess → full board visible → fully observed environment.
- **Observation (o)**: Partial description of the environment.  
  - Example: Super Mario Bros → only see part of the level → partially observed environment.

> In this course:  
> - "State" is often used to refer to both *states* and *observations*.  
> - Distinction matters in implementations.
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b49cc0c5-c5da-45bf-ab47-977b2d15fd42" />

---

## Action Space
- **Action space** = set of all possible actions in an environment.

### Types
- **Discrete Action Space**  
  - Finite number of actions.  
  - Example: *Super Mario Bros* → left, right, jump, crouch (4 actions).
- **Continuous Action Space**  
  - Infinite number of possible actions.  
  - Example: Self-driving car → can turn by any angle, accelerate, honk, etc.

**Why it matters**:  
The type of action space influences the choice of RL algorithm.

---

## Rewards and Discounting
- **Reward** = only feedback for the agent to know if an action was good or bad.  
- **Cumulative reward (return)** = sum of rewards over time.

### Problem
- Immediate rewards are more predictable.  
- Distant future rewards are uncertain and less reliable.  
- Example: A mouse collecting cheese while avoiding a cat:  
  - Nearby cheese = safer, more likely reward.  
  - Cheese near cat = riskier, more discounted.

### Solution: Discounting Future Rewards
- Define a **discount factor** γ (gamma), where `0 < γ < 1`.  
  - Typical range: `0.95–0.99`.  
  - Large γ → agent values long-term rewards more.  
  - Small γ → agent values short-term rewards more.

### Formula
Expected discounted cumulative reward at time step `t`:



---
<img width="1400" height="648" alt="image" src="https://github.com/user-attachments/assets/293dc8b8-ddf4-4518-b5ef-f5c9a08352bc" />
what the fuck
why did this math shit happen



## Recap
- RL loop: `State → Action → Reward → Next State`.
- Agent maximizes **expected discounted cumulative reward**.
- **Markov Property**: Current state is enough for decision-making.
- **State vs Observation**: Fully vs partially observed environments.
- **Action Space**: Discrete (finite) or Continuous (infinite).
- **Discounting**: Future rewards are weighted less with γ.

