
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

Update rule:  
\[
Q(s,a) \leftarrow Q(s,a) + \alpha \Big[ r + \gamma Q(s',a') - Q(s,a) \Big]
\]

### Step 1 — Update \(Q(S,R)\)
- Current: \(Q(S,R)=0\)  
- Reward: \(r = -1\)  
- Next state: \(A\), next action taken: \(D\), so \(Q(A,D)=0\)  
- Target: \(-1 + 1\cdot 0 = -1\)  
- TD error: \(-1 - 0 = -1\)  
- Update: \(Q(S,R) = 0 + 0.5 \times (-1) = -0.5\)  

### Step 2 — Update \(Q(A,D)\)
- Current: \(Q(A,D)=0\)  
- Reward: \(r=0\), next state is **G** (terminal), so \(Q(G,\cdot)=0\)  
- Target: \(0 + 1 \cdot 0 = 0\)  
- TD error: \(0 - 0 = 0\)  
- Update: \(Q(A,D)=0\)  

**Final SARSA values:**  
- \(Q(S,R) = -0.5\)  
- \(Q(A,D) = 0\)  

---

## Task 2: Q-learning (Off-Policy)

Update rule:  
\[
Q(s,a) \leftarrow Q(s,a) + \alpha \Big[ r + \gamma \max_{a'} Q(s',a') - Q(s,a) \Big]
\]

### Step 1 — Update \(Q(S,R)\)
- Current: \(Q(S,R)=0\)  
- Reward: \(r = -1\)  
- Next state: \(A\), \(\max_{a'} Q(A,a')=0\)  
- Target: \(-1 + 1\cdot 0 = -1\)  
- TD error: \(-1 - 0 = -1\)  
- Update: \(Q(S,R) = 0 + 0.5 \times (-1) = -0.5\)  

### Step 2 — Update \(Q(A,D)\)
- Current: \(Q(A,D)=0\)  
- Reward: \(r = 0\), next is terminal, \(\max Q(G,\cdot)=0\)  
- Target: \(0\)  
- TD error: \(0\)  
- Update: \(Q(A,D)=0\)  

**Final Q-learning values:**  
- \(Q(S,R) = -0.5\)  
- \(Q(A,D) = 0\)  

---

## Comparison
- For this simple case, **SARSA and Q-learning give identical numeric results** because all Q-values start at 0.  
- **Key difference:**  
  - SARSA uses the *actual next action taken* (\(a'\)) → **on-policy**  
  - Q-learning uses the *greedy max over actions* → **off-policy**  

---

## Optional Extension
To make the difference visible, try:  
- Set \(Q(A,D)=0.5\) and \(Q(A,R)=2.0\) before updates.  
- Then compare SARSA vs Q-learning updates for \(Q(S,R)\).  
- You’ll see Q-learning’s update uses the maximum (2.0), while SARSA uses the actual taken action value (0.5).  

---
