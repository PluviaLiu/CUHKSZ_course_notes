#### 可测集 (Measurable Set)

这是**测度论 (Measure Theory)** 里的核心概念，是概率论的数学基础。

---

#### 1. 为什么需要"可测集"这个概念？

直觉上你可能觉得：所有集合都应该能定义"大小"（长度、面积、概率）。

但数学上存在一些**病态集合**，你无法给它们定义一个自洽的"大小"。所以我们需要先划定一个范围——**哪些集合是"合法的"、可以被测量的**——这些集合就叫**可测集**。

---

#### 2. 先理解 $\sigma$-代数 ($\sigma$-algebra)

可测集的定义依赖于 $\sigma$-代数。

给定样本空间 $\Omega$，一个集合族 $\mathcal{F}$（即一堆子集的集合）叫做 $\sigma$-代数，如果满足：

- **① 包含全集**：$\Omega \in \mathcal{F}$
- **② 对补集封闭 (closed under complement)**：若 $A \in \mathcal{F}$，则 $A^c \in \mathcal{F}$
- **③ 对可数并封闭 (closed under countable union)**：若 $A_1, A_2, \ldots \in \mathcal{F}$，则 $\bigcup_{i=1}^{\infty} A_i \in \mathcal{F}$

---

#### 3. 可测集的定义

在概率空间 $(\Omega, \mathcal{F}, \mathbb{P})$ 中：

> **可测集 = $\mathcal{F}$ 中的元素**，即属于这个 $\sigma$-代数的子集。

换句话说，$A$ 是**可测集**当且仅当 $A \in \mathcal{F}$。

---

#### 4. 三元组 $(\Omega, \mathcal{F}, \mathbb{P})$ 的直觉理解

| 符号 | 名称 | 直觉 |
| --- | --- | --- |
| $\Omega$ | 样本空间 (Sample Space) | 所有可能结果的集合 |
| $\mathcal{F}$ | $\sigma$-代数 | 所有"合法事件"的集合，即所有可以被赋予概率的事件 |
| $\mathbb{P}$ | 概率测度 (Probability Measure) | 给每个可测集赋予一个 $[0,1]$ 的数 |

- $\mathcal{F}$ 里的每一个元素（集合）就是一个**可测集**，也就是一个**合法事件 (event)**。
- $\mathbb{P}$ 只对 $\mathcal{F}$ 里的集合有定义——不在 $\mathcal{F}$ 里的集合，你没办法问"它的概率是多少"。

---

#### 5. 具体例子

设 $\Omega = \{1, 2, 3\}$（掷一个三面骰子）。

一个合法的 $\sigma$-代数可以是：

$$\mathcal{F} = \{\emptyset,\ \{1\},\ \{2,3\},\ \Omega\}$$

- **可测集**：$\emptyset,\ \{1\},\ \{2,3\},\ \{1,2,3\}$
- **不可测集**（在这个 $\mathcal{F}$ 下）：$\{2\},\ \{3\},\ \{1,2\}$ 等——它们不在 $\mathcal{F}$ 里，**无法被赋予概率**。

最常用的 $\mathcal{F}$ 是**幂集 (power set)** $2^\Omega$，即 $\Omega$ 的所有子集——这时候每个子集都是可测集。

---

#### 6. 和你题目的联系

题目中说"$A$ 和 $B$ 为 $\mathcal{F}$-可测集"，就是在说：

> $A$ 和 $B$ 都是合法的事件，都在 $\sigma$-代数 $\mathcal{F}$ 里，因此可以对它们谈论概率 $\mathbb{P}(A)$、$\mathbb{P}(B)$、$\mathbb{P}(A \cap B)$ 等。

这只是在告诉你"这些集合是合法的"，以便后续推导贝叶斯定理时所有的条件概率都有意义。