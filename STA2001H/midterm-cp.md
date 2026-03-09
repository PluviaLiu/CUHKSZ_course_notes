## 知识概要
### **1. 概率导论 (Introduction to Probability)**

#### **① 定义与概念 (Definitions & Concepts)**
1.  **概率三元组 (Probability Triple):** $(\Omega, \mathcal{F}, \mathbb{P})$
    *   **样本空间 (Sample Space) $\Omega$**: 所有可能结果的集合.
    *   **事件集合 ($\sigma$-algebra) $\mathcal{F}$**: $\Omega$ 的子集构成的集合, 满足: (i) $\emptyset \in \mathcal{F}$, (ii) 若 $A \in \mathcal{F}$ 则 $A^c \in \mathcal{F}$, (iii) 若 $A_1, A_2, \dots \in \mathcal{F}$ 则 $\bigcup_i A_i \in \mathcal{F}$.
    *   **概率测度 (Prob. Measure) $\mathbb{P}$**: 函数 $\mathbb{P}: \mathcal{F} \to [0, 1]$, 满足: (i) $\mathbb{P}(\Omega) = 1$, (ii) 对互斥事件 $A_1, A_2, \dots$, 有 $\mathbb{P}(\bigcup_{i=1}^\infty A_i) = \sum_{i=1}^\infty \mathbb{P}(A_i)$ (可数可加性).
2.  **条件概率 (Conditional Probability):** $P(A|B) = \frac{P(A \cap B)}{P(B)}$, (要求 $P(B)>0$).
3.  **独立性 (Independence):**
    *   **两事件**: $A, B$ 独立 $\iff P(A \cap B) = P(A)P(B)$.
    *   **多事件**: $A_1, \dots, A_n$ 相互独立 $\iff P(\bigcap_{i=1}^n A_i) = \prod_{i=1}^n P(A_i)$.
    *   **成对独立 (Pairwise Indep.)**: $\forall i \neq j, P(A_i \cap A_j) = P(A_i)P(A_j)$. ⚠️ 相互独立比成对独立更强.
    *   **条件独立 (Conditional Indep.)**: $A, B$ 在 $C$ 下条件独立 $\iff P(A \cap B|C) = P(A|C)P(B|C)$.
4.  **划分 (Partition):** 集合族 $\{B_i\}$ 是 $\Omega$ 的划分, 若 $B_i$ 互斥 ($B_i \cap B_j = \emptyset, \forall i \neq j$) 且 $\bigcup_i B_i = \Omega$.

#### **② 公式与定理 (Formulas & Theorems)**
1.  **计数 (Counting):** 排列 (Permutation) $P(n,k) = \frac{n!}{(n-k)!}$, 组合 (Combinatic lion) $C(n,k) = \binom{n}{k} = \frac{n!}{k!(n-k)!}$.
2.  **基本性质 (Properties):**
    *   $P(A^c) = 1 - P(A)$.
    *   $A \subseteq B \implies P(A) \le P(B)$.
    *   $P(A \cup B) = P(A) + P(B) - P(A \cap B)$.
    *   **De Morgan's Laws:** $(\bigcup_i A_i)^c = \bigcap_i A_i^c$; $(\bigcap_i A_i)^c = \bigcup_i A_i^c$.
    *   **容斥原理 (Inclusion-Exclusion):** $P(\bigcup_{i=1}^n A_i) = \sum_i P(A_i) - \sum_{i<j} P(A_i \cap A_j) + \dots + (-1)^{n+1} P(\bigcap_{i=1}^n A_i)$.
3.  **核心定理 (Core Theorems):**
    *   **全概率公式 (Total Probability):** 若 $\{B_i\}$ 是划分, $P(A) = \sum_{i} P(A|B_i)P(B_i)$.
    *   **贝叶斯定理 (Bayes' Theorem):** $P(B_i|A) = \frac{P(A|B_i)P(B_i)}{P(A)} = \frac{P(A|B_i)P(B_i)}{\sum_{j} P(A|B_j)P(B_j)}$.
4.  **赌徒破产问题 (Gambler's Ruin):** 初始资金 $i$, 目标 $N$, 赢率 $p$. 最终获胜概率 $P_i$:
    $P_i = \begin{cases} \frac{i}{N} & \text{if } p = 1/2 \\ \frac{1 - ((1-p)/p)^i}{1 - ((1-p)/p)^N} & \text{if } p \neq 1/2 \end{cases}$

#### **③ ⚠️ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **排列 vs. 组合 (Permutation vs. Combination):** 排列关心顺序 (order matters), 组合不关心 (order doesn't matter).
2.  **独立 vs. 互斥 (Independent vs. Disjoint):** 若 $P(A), P(B) > 0$, 则 $A, B$ 互斥 $\implies$ $P(A \cap B) = 0 \neq P(A)P(B) \implies$ $A, B$ 不独立 (相关).
3.  **零概率 vs. 不可能事件 (Null vs. Impossible):** $P(A)=0$ (零概率) $\not\implies A=\emptyset$ (不可能). 连续 RV 取单点概率为0但可能发生.
4.  **辛普森悖论 (Simpson's Paradox):** 分组数据中的趋势在合并后可能逆转.

---
### **2. 离散型随机变量 (Discrete Random Variables)**

#### **① 定义与性质 (Definitions & Properties)**
1.  **随机变量 (Random Variable, RV):** 函数 $X: \Omega \to \mathbb{R}$.
2.  **分布函数 (CDF):** $F_X(x) = P(X \le x)$.
    *   性质: (i) 非降, (ii) 右连续, (iii) $\lim_{x\to-\infty} F(x) = 0$, (iv) $\lim_{x\to\infty} F(x) = 1$.
3.  **概率质量函数 (PMF):** $f_X(x) = P(X=x)$.
    *   性质: (i) $f(x) \ge 0$, (ii) $\sum_x f(x) = 1$.
    *   关系: $F(x) = \sum_{y \le x} f(y)$.
4.  **期望 (Expectation):** $E[X] = \sum_x x f(x)$.
    *   **线性性:** $E[aX + bY] = aE[X] + bE[Y]$.
    *   **函数期望:** $E[g(X)] = \sum_x g(x)f(x)$.
    *   **独立性:** $X, Y$ 独立 $\implies E[XY] = E[X]E[Y]$.
    *   **指示函数 (Indicator):** $E[I_A] = P(A)$.
5.  **方差 (Variance):** $Var(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2$.
    *   $Var(aX + b) = a^2 Var(X)$.
    *   $X, Y$ 不相关 $\implies Var(X+Y) = Var(X) + Var(Y)$.
6.  **矩生成函数 (MGF):** $M_X(t) = E[e^{tX}]$.
    *   $E[X^k] = M_X^{(k)}(0)$ (在0点的k阶导数).
    *   ⚠️ MGF 唯一确定分布 (若存在).

#### **② ⚠️ 常见分布比较 (Common Distribution Comparisons)**
1.  **二项 vs. 超几何 (Binomial vs. Hypergeometric):**
    *   $B(n,p)$: 有放回抽样, 独立重复试验, $p$ 不变.
    *   $Hy(N,K,n)$: 无放回抽样, 非独立试验, 成功概率改变.
2.  **几何 vs. 负二项 (Geometric vs. Negative Binomial):**
    *   $Ge(p)$: 首次成功所需的试验次数.
    *   $Ne(r,p)$: 第 $r$ 次成功所需的试验次数. $Ge(p)$ 是 $Ne(1,p)$ 的特例.
3.  **泊松近似二项 (Poisson Approx. to Binomial):**
    *   当 $n \to \infty, p \to 0$ 且 $np=\lambda$ (常数) 时, $B(n, p) \approx P(\lambda)$.

---
### **3. 连续型随机变量 (Continuous Random Variables)**

#### **① 定义与性质 (Definitions & Properties)**
1.  **概率密度函数 (PDF):** $f_X(x)$ 满足 $F_X(x) = \int_{-\infty}^x f(u)du$.
    *   性质: (i) $f(x) \ge 0$, (ii) $\int_{-\infty}^\infty f(x)dx = 1$.
    *   关系: $f(x) = F'(x)$.
    *   ⚠️ $f(x)$ 不是概率, $P(X=x)=0$.
2.  **概率计算:** $P(a \le X \le b) = \int_a^b f(x)dx$.
    *   ⚠️ 对于连续 RV, $P(a \le X \le b) = P(a < X < b)$.
3.  **期望 (Expectation):** $E[X] = \int_{-\infty}^\infty x f(x)dx$.
4.  **方差 (Variance):** $Var(X) = \int_{-\infty}^\infty (x-E[X])^2 f(x)dx = E[X^2] - (E[X])^2$.
5.  **矩生成函数 (MGF):** $M_X(t) = E[e^{tX}] = \int_{-\infty}^\infty e^{tx} f(x)dx$.
6.  **正态分布标准化 (Standardization of Normal):** 若 $X \sim \mathcal{N}(\mu, \sigma^2)$, 则 $Z = \frac{X-\mu}{\sigma} \sim \mathcal{N}(0, 1)$.
    *   $P(X \le x) = P(Z \le \frac{x-\mu}{\sigma}) = \Phi(\frac{x-\mu}{\sigma})$, 其中 $\Phi$ 是标准正态 CDF.


## 解题思路: 解析题目条件，快速判断分布，求解
### 1. 离散型分布大全 (Discrete Distributions - 查数/抽卡类)

| 具体例子                 | **情景描述与触发词 (Scenarios & Keywords)**                                                                         | **锁定模型 (Distribution)**                    | **标准解题动作 (四大公式闭眼套)**                                                                                                                                                                                                                    |
| -------------------- | ----------------------------------------------------------------------------------------------------------- | ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 只抛一次硬币               | **单次试验**，只有“成功”和“失败”。<br>触发词: "coin flip", "success/failure"                                                | **伯努利分布**<br>Bernoulli $B(1, p)$           | 求概率: $P(X=1)=p, P(X=0)=1-p$<br>求期望: $\mathbb{E}[X] = p$<br>求方差: $Var(X) = p(1-p)$<br>求MGF: $M(t) = 1-p+pe^t$ $M'(t) = pe^t$                                                                                                             |
| 有放回连抽10次             | **$n$次独立重复试验**，问成功几次。<br>触发词: "with replacement" (有放回),<br>"repeat $n$ times" (重复n次),<br>"independent" (独立) | **二项分布**<br>Binomial $B(n, p)$             | 求恰好$x$次: $P(X=x) = \binom{n}{x}p^x(1-p)^{n-x}$<br>求期望: $\mathbb{E}[X] = np$<br>求方差: $Var(X) = np(1-p)$<br>求MGF: $M(t) = (1-p+pe^t)^n$$M'(t) = n(1-p+pe^t)^{n-1}pe^t$                                                                    |
| 无放回地直接抓一把，数一数抓到了几个   | 从$N$个里**无放回抽$n$个**，问抽中目标$x$个概率。<br>触发词: "without replacement" (无放回),<br>"draw $k$ items" (一次性抽出)            | **超几何分布**<br>Hypergeometric<br>X∼HG(N,M,n) | 求概率: $P(X=x) = \frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}$<br>求期望: $\mathbb{E}[X] = n\frac{K}{N}$<br>求方差: $Var(X) = n\frac{K}{N}(1-\frac{K}{N})\frac{N-n}{N-1}$<br>求MGF: (考试一般不考超几何的MGF)                                         |
| 一直单抽，直到抽出第1个金光才停手。   | 一直做试验，**直到出现第1次成功**。<br>触发词: "the first time" (直到第一次出现...),<br>"until the first..."                         | **几何分布**<br>Geometric $Ge(p)$              | 求恰好第$x$次: $P(X=x) = (1-p)^{x-1}p$<br>求期望: $\mathbb{E}[X] = 1/p$<br>求方差: $Var(X) = (1-p)/p^2$<br>求MGF: $M(t) = \frac{pe^t}{1-(1-p)e^t}$ $M'(t) = \frac{pe^t}{(1-(1-p)e^t)^2}$                                                            |
| 一直单抽，直到抽出第 n 个金光才停手。 | 一直做试验，**直到出现第$n$次成功**才停。<br>触发词: "the first time... $n$ items"<br>(直到出现第 $n$ 个...才停止)                       | **负二项分布**<br>Negative Binomial             | 求恰好第$x$次: $P(X=x) = \binom{x-1}{n-1}p^n(1-p)^{x-n}$<br>求期望: $\mathbb{E}[X] = n/p$<br>求方差: $Var(X) = n(1-p)/p^2$<br>求MGF: $M(t) = \left(\frac{pe^t}{1-(1-p)e^t}\right)^n$$M'(t) = n M(t) \left( 1 + \frac{(1-p)e^t}{1-(1-p)e^t} \right)$ |
| 蹲在路口，数一个小时内过去了多少辆车。  | **固定时间/空间内**，随机事件发生的次数。<br>触发词: "rate of $\lambda$" (平均发生率),<br>"per hour/day/minute" (每段时间内)               | **泊松分布**<br>Poisson $P(\lambda)$           | 求恰好发生$x$次: $P(X=x) = \frac{\lambda^x e^{-\lambda}}{x!}$<br>求期望: $\mathbb{E}[X] = \lambda$<br>求方差: $Var(X) = \lambda$<br>求MGF: $M(t) = e^{\lambda(e^t-1)}$$M'(t) = e^{\lambda(e^t-1)} \cdot \lambda e^t$                                 |

### 2. 连续型分布大全 (Continuous Distributions - 寿命/时间/测量类)

|             | **情景描述与触发词 (Scenarios & Keywords)**                                                          | **锁定模型 (Distribution)**                | **标准解题动作 (四大公式闭眼套 + MGF求导)**                                                                                                                                                                                                                                    |
| ----------- | -------------------------------------------------------------------------------------------- | -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 等公交车等多久     | 在区间$[a,b]$内**等可能发生**。<br>触发词: "uniformly distributed",<br>"randomly chosen from interval"    | **均匀分布**<br>Uniform $U(a,b)$           | 密度函数(PDF): $f(x) = \frac{1}{b-a}$<br>求期望: $\mathbb{E}[X] = \frac{a+b}{2}$<br>求方差: $Var(X) = \frac{(b-a)^2}{12}$<br>求MGF: $M(t) = \frac{e^{tb}-e^{ta}}{t(b-a)}$<br>MGF一阶导: $M'(t) = \frac{t(be^{tb}-ae^{ta}) - (e^{tb}-e^{ta})}{t^2(b-a)}$                       |
| 下一个客人多久才进店。 | 两次泊松事件之间的**时间间隔/寿命等待时间**。<br>触发词: "time until next event",<br>"lifetime", "rate $\lambda$"   | **指数分布**<br>Exponential $Exp(\lambda)$ | 密度函数(PDF): $f(x) = \lambda e^{-\lambda x}$<br>求期望: $\mathbb{E}[X] = 1/\lambda$<br>求方差: $Var(X) = 1/\lambda^2$<br>求MGF: $M(t) = \frac{\lambda}{\lambda-t}$ (当 $t<\lambda$)<br>MGF一阶导: $M'(t) = \frac{\lambda}{(\lambda-t)^2}$                                    |
| 机器打包面粉的误差   | 典型**钟形曲线/中心极限定理/测量误差**。<br>触发词: "normally distributed",<br>"mean $\mu$, variance $\sigma^2$" | **正态分布**<br>Normal $N(\mu, \sigma^2)$  | 密度函数(PDF): $f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$<br>求期望: $\mathbb{E}[X] = \mu$<br>求方差: $Var(X) = \sigma^2$<br>求MGF: $M(t) = e^{\mu t + \sigma^2 t^2 / 2}$<br>MGF一阶导: $M'(t) = (\mu + \sigma^2 t) e^{\mu t + \sigma^2 t^2 / 2}$ |
 
- 如果题目出现 **"at least (至少) / at most (至多)"** $\rightarrow$ 把对应的**求概率公式**进行累加 (离散型用 $\sum$) 或积分 (连续型用 $\int$)。例如至少3次就是 $1 - P(X=0) - P(X=1) - P(X=2)$。

### 🛠️ 1. “求什么” (目标动作翻译)

| **题目里的原话 (English text)**                        | **翻译成的数学符号 (Math Symbol)** | **你的解题动作**                              |
| ------------------------------------------------ | -------------------------- | --------------------------------------- |
| **probability**/**chance**                       | 求 $P(...)$                 | 找对应分布的 **PMF/PDF 公式**                   |
| **expected** number/average** / **mean           | 求 $\mathbb{E}[X]$          | 找对应分布的 **期望 $\mathbb{E}[X]$ 公式**        |
| "What is the **variance**..."                    | 求 $Var(X)$                 | 找对应分布的 **方差 $Var(X)$ 公式**               |
| "Find the **standard deviation**..."             | 求 $\sigma$                 | 先算方差 $Var(X)$，然后**开根号** $\sqrt{Var(X)}$ |
| "By using the **moment generating function**..." | 找 $M(t)$ 并求导               | 抄我前面给你的 **MGF求导找t=0                     |


### 🧩 3. “参数提取” (找 $n, p, \lambda$ 填空)

| **寻找目标参数**            | **在题目里的伪装形态 (如何寻找)**                                                                             | **高频常识（直接当已知数字用）**                             |
| --------------------- | ------------------------------------------------------------------------------------------------ | ---------------------------------------------- |
| **找 $n$** (总次数)       | "repeat **$n$** times" (重复了多少次)<br>"draw **$5$** cards" (抽了几个)<br>sample size of **$10$**" (样本量) | 如果题目没给具体数字，就保留字母 $n$ 留在式子里（像你们练习卷第一题那样）。       |
| **找 $p$** (单次成功概率)    | "probability of success is **$0.2$**"<br>"proportion of defective is **$5\%$**"                  | **抛硬币 (fair coin)**: $p = 1/2$<br>             |
| **找 $\lambda$** (发生率) | "average rate is **$3$** per hour" (平均每小时...)<br>"mean arrivals is **$5$**"                      | 看到 per / average / rate 这种词，后面的数字就是 $\lambda$。 |


_"You are given a pack of well-shuffled cards. You take out a card and some **replaces it** at a random place and **repeat this $n \ge 1$ times**."_

- **翻译器运作**：看到 "replaces it" (有放回) + "repeat $n$ times"，立刻触发 **二项分布 (Binomial) $B(n, p)$**。
    
- **找参数**：$n$ 就是 $n$。题目问的是抽到 Aces (A)，一副牌 52 张有 4 张 A，所以高中常识 $p = 4/52$。
    

**小问 (a)：**

_"**What is the probability** that you draw **three** aces..."_

- **翻译器运作**：“What is the probability” $\rightarrow$ 求 $P(X=x)$；“three” $\rightarrow$ $x=3$。
    
- **套公式**：抄 A4 纸二项分布 PMF 公式，把 $n$ 留着，$p=4/52$，$x=3$ 代入。
    
- **得到答案**：$P(X=3) = \binom{n}{3} (4/52)^3 (1 - 4/52)^{n-3}$。搞定！
    

**小问 (b)：**

_"What are the **expected number** of aces..."_

- **翻译器运作**：“expected number” $\rightarrow$ 求期望 $\mathbb{E}[X]$。
    
- **套公式**：抄二项分布期望公式 $\mathbb{E}[X] = np$。
    
- **得到答案**：$\mathbb{E}[X] = n \times (4/52)$。搞定！
    

**小问 (d)：**

_"What is the **probability** that you have **at least $x$** aces..."_

- **翻译器运作**：“at least $x$” $\rightarrow$ 范围翻译为 $P(\text{次数} \ge x)$。
    
- **怎么写式子**：这时候你要么写 $1 - P(\text{次数} < x)$，要么直接用 $\Sigma$ 把 $x$ 到 $n$ 的全部加起来。
    
- **得到答案**：写成 $\sum_{u=x}^{n} \binom{n}{u} (4/52)^u (1 - 4/52)^{n-u}$ （这里的 $u$ 就是一个临时代替求和的指标符号）。
    

怎么样？有了这三个表格，你现在看全英文的概率题，是不是感觉那些长难句都已经自动高亮成数学符号了？直接复制进 Obsidian 吧！