- **S** = Start (top-left)
- **G** = Goal (bottom-right, terminal)
- **A, B** = intermediate states
- **Actions:** Right (R), Down (D)
- **Rewards:** Each move = −1, reaching Goal = 0

---

## Given Trajectory

The agent follows this path (with ε-greedy exploration):

1. From **S**, take action **R**, go to **A**, reward = −1.
2. From **A**, take action **D**, go to **G**, reward = 0.

Trajectory:  
\[
(S, R, -1, A), \quad (A, D, 0, G)
\]

---

## Initial Conditions

- Discount factor: \(\gamma = 1\)
- Learning rate: \(\alpha = 0.5\)
- All \(Q(s,a) = 0\) initially

---

## Task 1: SARSA (On-Policy)

SARSA update rule:  
\[
Q(s,a) \leftarrow Q(s,a) + \alpha \Big[ r + \gamma Q(s',a') - Q(s,a) \Big]
\]

1. Compute the update for \(Q(S,R)\) using the first transition.
2. Compute the update for \(Q(A,D)\) using the second transition.
3. Write down the final values of \(Q(S,R)\) and \(Q(A,D)\).

---

## Task 2: Q-learning (Off-Policy)

Q-learning update rule:  
\[
Q(s,a) \leftarrow Q(s,a) + \alpha \Big[ r + \gamma \max_{a'} Q(s',a') - Q(s,a) \Big]
\]

1. Compute the update for \(Q(S,R)\) using the first transition.
2. Compute the update for \(Q(A,D)\) using the second transition.
3. Write down the final values of \(Q(S,R)\) and \(Q(A,D)\).

---

## Discussion Questions

1. Did SARSA and Q-learning give the same numerical results in this case? Why or why not?
2. Conceptually, how does SARSA differ from Q-learning in terms of the update rule?
3. Which one is **on-policy** and which is **off-policy**?

---

## Optional Extension

Modify the problem:

- Assume before the updates that \(Q(A,D)=0.5\) and \(Q(A,R)=2.0\).
- Repeat the first update for both SARSA and Q-learning.
- Compare how the two algorithms differ in updating \(Q(S,R)\).
