<style>
  table {
    border-collapse: collapse;
    width: 100%;
    margin-top: 10px;
  }
  th, td {
    border: 1px solid black;
    padding: 6px;
    text-align: center;
  }
  th {
    background-color: #f2f2f2;
  }
  h1, h2, h3 {
    text-align: center;
  }
</style>

# 🎰 Exercise 2

---

## 🎯 Objective

Find out which slot machine gives the most reward using three different strategies.

---

## 🕹 Setup

- **Credits:** 300 pulls
- **Machines:** A, B, C
- **Cost per pull:** 1 credit
- **Your task:** Record the machine you play, the reward, and keep track of total reward.

---

## 📊 Strategies

**1. Explore Only**  
Play each machine an equal number of times (100 pulls each).

**2. Exploit Only**  
Try each machine once at the start. Pick the highest reward and play only that machine for the rest.

**3. UCB (Upper Confidence Bound)**  
Play each machine once, then pick based on:
\[
\text{UCB} = \bar{X}\_j + \sqrt{\frac{2 \ln n}{n_j}}
\]
Where:

- \(\bar{X}\_j\) = Average reward for machine \(j\)
- \(n\) = Total pulls so far
- \(n_j\) = Pulls of machine \(j\)

---

## 📝 Recording Table – Explore / Exploit

| Pull # | Strategy | Machine | Reward | Total Reward | Regret |
| ------ | -------- | ------- | ------ | ------------ | ------ |
| 1      | Explore  | A       |        |              |        |
| 2      | Explore  | B       |        |              |        |
| 3      | Explore  | C       |        |              |        |
| ...    | ...      | ...     |        |              |        |
| 300    |          |         |        |              |        |

---

## 📝 Recording Table – UCB

| Pull # | Machine | Reward | Avg Reward | Exploration Bonus | UCB Score | Total Reward | Regret |
| ------ | ------- | ------ | ---------- | ----------------- | --------- | ------------ | ------ |
| 1      | A       |        |            |                   |           |              |        |
| 2      | B       |        |            |                   |           |              |        |
| 3      | C       |        |            |                   |           |              |        |
| ...    | ...     |        |            |                   |           |              |        |
| 300    |         |        |            |                   |           |              |        |

---

## 📌 Notes

- **Regret** = Best possible reward – Your reward
- **Exploration Bonus** comes from \(\sqrt{\frac{2 \ln n}{n_j}}\)
- Be honest when recording rewards.
- At the end, compare results for all strategies.

---

**Name:** ****\*\*****\_\_****\*\*****  
**Date:** ****\*\*****\_\_****\*\*****
