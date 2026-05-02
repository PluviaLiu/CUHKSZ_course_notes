- [ ] 完成STA2001H期末模拟卷

# Q1

#### 1. 题目翻译

**第(i)题：**
设 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间，$A$ 和 $B$ 为 $\mathcal{F}$-可测集。在此背景下，陈述并证明贝叶斯定理。[7分]

**第(ii)题：**
三名囚犯 $A, B, C$ 被单独关押，均被判处死刑，但其中一人将被随机赦免（概率相等）。囚犯 $A$ 请求狱长告诉他自己是否会被赦免。狱长拒绝直接回答，但透露了"$B$ 将被处决"。狱长认为自己没有泄露有用信息，因为 $A$ 本来就知道 $B$ 或 $C$ 中至少有一人会被处决。

**(a)** $A$ 突然感到非常高兴，因为他认为自己被赦免的概率从 $1/3$ 上升到了 $1/2$。而狱长（如果 $A$ 真的要被赦免，他同等概率说出 $C$ 或 $B$ 的名字）对 $A$ 的高兴感到困惑。**谁是对的？**[7分]

提示：令 $A, B, C$ 为事件"$A, B, C$ 分别被赦免"，它们构成样本空间 $\Omega$ 的划分。令 $G_{AB}$ 为"狱长告诉 $A$ 说 $B$ 将被处决"这一事件。你需要计算 $\mathbb{P}(A \mid G_{AB})$，方法是分别计算在 $A, B, C$ 各自成立时 $G_{AB}$ 的条件概率，再用贝叶斯定理。

**(b)** 如果 $C$ 偷听到了狱长的回答，但以为这个问题是狱警问的（即考虑事件 $G_{PB}$：狱长告诉**狱警**说 $B$ 将被处决），$C$ 应该作何感想？[6分]

---

#### 2. 背景概念

[[可测集(Measurable Set]]


[[贝叶斯定理 (Bayes' Theorem)]]

$$\mathbb{P}(A_i \mid B) = \frac{\mathbb{P}(B \mid A_i)\,\mathbb{P}(A_i)}{\sum_{j=1}^{n} \mathbb{P}(B \mid A_j)\,\mathbb{P}(A_j)}$$

直觉：已知结果 $B$ 发生了，反推"原因 $A_i$"的概率。

[[划分 (Partition)]]

事件 $A, B, C$（"$A$ 被赦免"、"$B$ 被赦免"、"$C$ 被赦免"）满足：
- 互斥（Mutually Exclusive）：不能同时两人都被赦免
- 穷举（Exhaustive）：必有一人被赦免
- 因此 $\mathbb{P}(A) = \mathbb{P}(B) = \mathbb{P}(C) = 1/3$

---

#### 3. 第(i)题解答：陈述与证明贝叶斯定理

**陈述 (Statement)：**

设 $A, B \in \mathcal{F}$，且 $\mathbb{P}(B) > 0$，则：

$$\mathbb{P}(A \mid B) = \frac{\mathbb{P}(B \mid A)\,\mathbb{P}(A)}{\mathbb{P}(B)}$$

**证明 (Proof)：**

- 由条件概率定义 (definition of conditional probability)：

$$\mathbb{P}(A \mid B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)} \quad \cdots (1)$$

$$\mathbb{P}(B \mid A) = \frac{\mathbb{P}(B \cap A)}{\mathbb{P}(A)} \quad \cdots (2)$$

- 因为 $A \cap B = B \cap A$（交集的对称性 symmetry of intersection），由 $(2)$ 得：

$$\mathbb{P}(A \cap B) = \mathbb{P}(B \mid A)\,\mathbb{P}(A)$$

- 代入 $(1)$：

$$\mathbb{P}(A \mid B) = \frac{\mathbb{P}(B \mid A)\,\mathbb{P}(A)}{\mathbb{P}(B)}$$


> 若需要更一般的版本（分母用全概率公式展开），将 $\mathbb{P}(B) = \mathbb{P}(B|A)\mathbb{P}(A) + \mathbb{P}(B|A^c)\mathbb{P}(A^c)$ 代入即可。

---

#### 4. 第(ii)(a)题解答：谁是对的？

**逻辑链条：**

**第一步：建立先验概率 (Prior Probability)**

- 初始条件：三人等概率被赦免
- $\mathbb{P}(\text{event } A) = \mathbb{P}(\text{event } B) = \mathbb{P}(\text{event } C) = \dfrac{1}{3}$

**第二步：分析狱长说出 $G_{AB}$（"$B$ 被处决"）的条件概率 (Likelihood)**

关键：狱长**知道**谁被赦免，且只会说出一个**将被处决**的人的名字（不会说被赦免者的名字）。

| 真实被赦免者 | 狱长的选择 | $\mathbb{P}(G_{AB} \mid \cdot)$ |
| --- | --- | --- |
| $A$ 被赦免 | $B$ 或 $C$ 等概率（各$1/2$）| $\mathbb{P}(G_{AB} \mid A) = \dfrac{1}{2}$ |
| $B$ 被赦免 | 只能说 $C$（不能说被赦免的$B$）| $\mathbb{P}(G_{AB} \mid B) = 0$ |
| $C$ 被赦免 | 只能说 $B$（不能说被赦免的$C$）| $\mathbb{P}(G_{AB} \mid C) = 1$ |

**第三步：用全概率公式计算 $\mathbb{P}(G_{AB})$**

$$\mathbb{P}(G_{AB}) = \mathbb{P}(G_{AB} \mid A)\,\mathbb{P}(A) + \mathbb{P}(G_{AB} \mid B)\,\mathbb{P}(B) + \mathbb{P}(G_{AB} \mid C)\,\mathbb{P}(C)$$

$$= \frac{1}{2} \cdot \frac{1}{3} + 0 \cdot \frac{1}{3} + 1 \cdot \frac{1}{3} = \frac{1}{6} + 0 + \frac{1}{3} = \frac{1}{2}$$

**第四步：用贝叶斯定理 (Bayes' Theorem) 计算后验概率 (Posterior Probability)**

$$\mathbb{P}(A \mid G_{AB}) = \frac{\mathbb{P}(G_{AB} \mid A)\,\mathbb{P}(A)}{\mathbb{P}(G_{AB})} = \frac{\frac{1}{2} \cdot \frac{1}{3}}{\frac{1}{2}} = \frac{1}{3}$$

$$\mathbb{P}(C \mid G_{AB}) = \frac{\mathbb{P}(G_{AB} \mid C)\,\mathbb{P}(C)}{\mathbb{P}(G_{AB})} = \frac{1 \cdot \frac{1}{3}}{\frac{1}{2}} = \frac{2}{3}$$

**结论：狱长是对的。**
- $A$ 被赦免的概率**仍然是 $1/3$**，没有变化。
- 但 $C$ 被赦免的概率从 $1/3$ 上升到了 $2/3$。
- $A$ 的"高兴"是错误的直觉——这与著名的**蒙提霍尔问题 (Monty Hall Problem)** 完全同构。

---

#### 5. 第(ii)(b)题解答：$C$ 偷听到后应该怎么想？

**关键区别：** 这次考虑的是 $G_{PB}$——狱长告诉**狱警**说"$B$ 将被处决"。

狱警的问题与囚犯 $A$ 的处境**无关**，狱长回答时**没有任何关于谁被赦免的策略性选择**。也就是说，狱长只是随机说出一个将被处决的人。

**重新计算条件概率 (Likelihood)：**

狱长在狱警问的情况下，从两个将被处决的人中**随机**说一个名字：

| 真实被赦免者 | 将被处决的人 | $\mathbb{P}(G_{PB} \mid \cdot)$ |
| --- | --- | --- |
| $A$ 被赦免 | $B$ 和 $C$ 均将处决，随机选一个 | $\dfrac{1}{2}$ |
| $B$ 被赦免 | $A$ 和 $C$ 均将处决，随机选一个 | $\dfrac{1}{2}$ |
| $C$ 被赦免 | $A$ 和 $B$ 均将处决，随机选一个 | $\dfrac{1}{2}$ |

**计算 $\mathbb{P}(G_{PB})$：**

$$\mathbb{P}(G_{PB}) = \frac{1}{2} \cdot \frac{1}{3} + \frac{1}{2} \cdot \frac{1}{3} + \frac{1}{2} \cdot \frac{1}{3} = \frac{1}{2}$$

**用贝叶斯定理计算 $C$ 被赦免的后验概率：**

$$\mathbb{P}(C \mid G_{PB}) = \frac{\mathbb{P}(G_{PB} \mid C)\,\mathbb{P}(C)}{\mathbb{P}(G_{PB})} = \frac{\frac{1}{2} \cdot \frac{1}{3}}{\frac{1}{2}} = \frac{1}{3}$$

**结论：$C$ 的概率仍然是 $\dfrac{1}{3}$，没有任何变化。**

- 因为在这个情境下，狱长的回答对三人**完全对称**，没有包含任何关于谁被赦免的额外信息。
- 信息量 (information) 的关键在于**狱长的策略（如何选择说哪个名字）**。当策略完全随机时，听到任何名字都不会更新概率。


# Q2
#### 1. 题目翻译

**第(i)题：**
设 $X$ 为一个离散随机变量 (discrete random variable)，其支撑集 (support) $X \subseteq \mathbb{Z}$（即取值为整数）。给出 $X$ 的期望 (expectation) 和方差 (variance) 的定义。[5分]

**第(ii)题：**
设 $X \sim Ge(p)$，即 $X$ 服从几何分布 (geometrically distributed)，$p \in (0,1)$，$X \in \{1, 2, \dots\}$。证明 $\mathbb{E}[X] = 1/p$，$\text{Var}[X] = (1-p)/p^2$。**不允许**使用矩母函数 (moment generating function) 或概率母函数 (probability generating function)。[10分]

**第(iii)题：**
某人反复参加驾驶考试。设每次通过的概率为 $p \in (0,1)$，且每次考试结果相互独立 (independent)。设 $X$ 为直到该人通过考试所需的考试次数。证明"在两次或更少的考试内通过"的概率为 $p(2-p)$。另外，求 $X$ 的期望值 $\mathbb{E}[X]$。[5分]

---

#### 2. 背景概念

[[期望 (Expectation)]]

离散随机变量 $X$ 的期望定义为：

$$\mathbb{E}[X] = \sum_{x \in X} x \cdot f_X(x)$$

其中 $f_X(x) = P(X = x)$ 是概率质量函数 (PMF, Probability Mass Function)。直觉：对所有可能取值，用概率加权求平均。

[[方差 (Variance)]]

$$\text{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$

等价定义：$\text{Var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2]$。计算时通常用前者更方便。

[[几何分布 (Geometric Distribution)]]

$X \sim Ge(p)$，$X \in \{1, 2, 3, \dots\}$，PMF 为：

$$P(X = k) = (1-p)^{k-1} \cdot p, \quad k = 1, 2, 3, \dots$$

直觉：前 $k-1$ 次都失败（概率各为 $1-p$），第 $k$ 次成功（概率 $p$）。

[[等比数列求和公式 (Geometric Series)]]

$$\sum_{k=0}^{\infty} r^k = \frac{1}{1-r}, \quad |r| < 1$$

对其求导可得：

$$\sum_{k=1}^{\infty} k \cdot r^{k-1} = \frac{1}{(1-r)^2}$$

再乘以 $r$ 后再求导，可得二阶矩需要的公式：

$$\sum_{k=1}^{\infty} k^2 \cdot r^{k-1} = \frac{1+r}{(1-r)^3}$$

这是整道第(ii)题的核心计算工具。

---

#### 3. 第(i)题解答：定义期望与方差

**期望的定义 (Definition of Expectation)：**

$$\mathbb{E}[X] = \sum_{x \in X} x \cdot P(X = x)$$

要求：该级数绝对收敛 (absolutely convergent)，即 $\sum_{x} |x| \cdot P(X=x) < \infty$。

**方差的定义 (Definition of Variance)：**

$$\text{Var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2] = \sum_{x \in X} (x - \mathbb{E}[X])^2 \cdot P(X=x)$$

等价计算公式（考试更常用）：

$$\text{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$

---

#### 4. 第(ii)题解答：证明几何分布的期望和方差

**目标：** 证明 $\mathbb{E}[X] = \dfrac{1}{p}$，$\text{Var}[X] = \dfrac{1-p}{p^2}$

令 $q = 1 - p$（失败概率），则 $P(X = k) = q^{k-1} p$。

---

**第一步：求 $\mathbb{E}[X]$**

- 由期望定义：

$$\mathbb{E}[X] = \sum_{k=1}^{\infty} k \cdot P(X=k) = \sum_{k=1}^{\infty} k \cdot q^{k-1} \cdot p$$

- 提出常数 $p$：

$$= p \sum_{k=1}^{\infty} k \cdot q^{k-1}$$

- 由等比数列求导公式 (Geometric Series derivative)，$|q| < 1$：

$$\sum_{k=1}^{\infty} k \cdot q^{k-1} = \frac{1}{(1-q)^2} = \frac{1}{p^2}$$

- 代入得：

$$\mathbb{E}[X] = p \cdot \frac{1}{p^2} = \frac{1}{p} \quad \checkmark$$

---

**第二步：求 $\mathbb{E}[X^2]$（为方差做准备）**

先用一个技巧：把 $k^2$ 拆成 $k(k-1) + k$，这样更容易和等比级数配合：

$$\mathbb{E}[X^2] = \sum_{k=1}^{\infty} k^2 q^{k-1} p = p\sum_{k=1}^{\infty} [k(k-1) + k] q^{k-1}$$

$$= p\sum_{k=1}^{\infty} k(k-1) q^{k-1} + p\sum_{k=1}^{\infty} k q^{k-1}$$

第二项已经算过了，等于 $p \cdot \dfrac{1}{p^2} = \dfrac{1}{p}$。

对第一项，注意 $k=1$ 时 $k(k-1)=0$，从 $k=2$ 开始求和。提出一个 $q$：

$$\sum_{k=2}^{\infty} k(k-1) q^{k-1} = q \sum_{k=2}^{\infty} k(k-1) q^{k-2}$$

由等比级数二阶导 (second derivative of geometric series)：

$$\sum_{k=2}^{\infty} k(k-1) q^{k-2} = \frac{2}{(1-q)^3} = \frac{2}{p^3}$$

所以：

$$p \sum_{k=1}^{\infty} k(k-1) q^{k-1} = p \cdot q \cdot \frac{2}{p^3} = \frac{2q}{p^2}$$

因此：

$$\mathbb{E}[X^2] = \frac{2q}{p^2} + \frac{1}{p} = \frac{2q}{p^2} + \frac{p}{p^2} = \frac{2q + p}{p^2}$$

由于 $q = 1-p$，所以 $2q + p = 2(1-p) + p = 2 - p$：

$$\mathbb{E}[X^2] = \frac{2-p}{p^2}$$

---

**第三步：求 $\text{Var}(X)$**

$$\text{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2 = \frac{2-p}{p^2} - \frac{1}{p^2} = \frac{2-p-1}{p^2} = \frac{1-p}{p^2} = \frac{q}{p^2} \quad \checkmark$$

---

#### 5. 第(iii)题解答：驾驶考试问题

**目标①：** 证明 $P(X \leq 2) = p(2-p)$

**目标②：** 求 $\mathbb{E}[X]$

---

**第一步：识别分布**

- 每次考试独立，通过概率为 $p$ → $X \sim Ge(p)$，$X \in \{1, 2, 3, \dots\}$
- 由几何分布 PMF：$P(X = k) = (1-p)^{k-1} p$

**第二步：计算 $P(X \leq 2)$**

$$P(X \leq 2) = P(X=1) + P(X=2)$$

- $P(X=1)$：第1次就通过 → $p$
- $P(X=2)$：第1次失败，第2次通过 → $(1-p) \cdot p$

$$P(X \leq 2) = p + (1-p)p = p[1 + (1-p)] = p(2-p) \quad \checkmark$$

**第三步：求 $\mathbb{E}[X]$**

由第(ii)题已证结论，$X \sim Ge(p)$ 的期望为：

$$\mathbb{E}[X] = \frac{1}{p}$$
# Q3

# Q4


