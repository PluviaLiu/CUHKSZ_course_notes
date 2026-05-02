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
    * 离散型：$\forall x, y, P(X=x, Y=y) = P(X=x)P(Y=y)$
    - 连续型：$\forall x, y, f_{X,Y}(x,y) = f_X(x)f_Y(y)$
    - 通用CDF：$\forall x, y, F_{X,Y}(x,y) = F_X(x)F_Y(y)$
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
2.  **独立 vs. 互斥 (Independent vs. Disjoint):** 若 $P(A), P(B) > 0$, 则 $A, B$ 互斥 $\implies$ $P(A \cap B) = 0 \neq P(A)P(B) \implies$ $A, B$ 不独立 (相关).互斥意味着“有你没我”。如果我知道 $A$ 发生了，那 $B$ 肯定没发生。这意味着 $A$ 的信息极大地影响了对 $B$ 的判断，所以它们**极度相关**。
3.  **零概率 vs. 不可能事件 (Null vs. Impossible):** $P(A)=0$ (零概率) $\not\implies A=\emptyset$ (不可能). 连续 RV 取单点概率为0但可能发生.
4.  **辛普森悖论 (Simpson's Paradox):** 分组数据中的趋势在合并后可能逆转.

---
### **2. 离散型随机变量 (Discrete Random Variables)**

#### **① 定义与性质 (Definitions & Properties)**
1.  **随机变量 (Random Variable, RV):** 函数 $X: \Omega \to \mathbb{R}$.
2.  **分布函数 (CDF):** $F_X(x) = P(X \le x)$.
    *   性质: (i) 非降, (ii) 右连续, (iii) $\lim_{x\to-\infty} F(x) = 0$, (iv) $\lim_{x\to\infty} F(x) = 1$.
    * 通过CDF计算期望：$\mathbb{E}[X] = \int_{0}^{\infty} [1 - F(x)] \, dx$，其中上限看变量取值。当你发现概率密度函数 $f(x)$ 积分极其复杂，但累积分布函数 $F(x)$ 或生存函数 $S(x) = 1-F(x)$ 形式很简单时（如指数分布），直接用这个公式。
3.  **概率质量函数 (PMF):** $f_X(x) = P(X=x)$.
    *   性质: (i) $f(x) \ge 0$, (ii) $\sum_x f(x) = 1$.
    *   关系: $F(x) = \sum_{y \le x} f(y)$.
    *   多变量：$\sum_{x=0}^{\infty} \sum_{y=0}^{\infty} f(x, y) = 1$
    * （当x和y取值范围相互独立的时候，函数乘积形式可以拆）
    *   Marginal PMF:
	    * $f_X(x) = \sum_{y} f(x, y)$
	    * $f_Y(y) = \sum_{x} f(x, y)$
	    * 独立性判别：证明对所有xy都有$f(x, y) = f_X(x) \cdot f_Y(y)$，或者PMF可以完全分解$g(x) \cdot h(y)$
4.  **期望 (Expectation):** $E[X] = \sum_x x f(x)$.
    *   **线性性:** $E[aX + bY] = aE[X] + bE[Y]$.
    *   **函数期望:** $E[g(X)] = \sum_x g(x)f(x)$.
    *   **独立性:** $X, Y$ 独立 $\implies E[XY] = E[X]E[Y]$.
    *   **指示函数 (Indicator):** $E[I_A] = P(A)$.
5.  **方差 (Variance):** $Var(X) = E[(X - E[X])^2] = E[X^2] - (E[X])^2$.
    *   $Var(aX + b) = a^2 Var(X)$.
    *   $X, Y$ 不相关 $\implies Var(X+Y) = Var(X) + Var(Y)$.
    * 如果相关，$Var(aX + bY) = a^2 Var(X) + b^2 Var(Y) + 2ab \cdot Cov(X, Y)$
    * standard dericition  $\sigma$ **开根号** $\sqrt{Var(X)}$
6.  **矩生成函数 (MGF):** $M_X(t) = E[e^{tX}]$.
    *   $E[X^k] = M_X^{(k)}(0)$ (在0点的k阶导数).
    *   ⚠️ MGF 唯一确定分布 (若存在).

| 具体例子                 | **情景描述与触发词 (Scenarios & Keywords)**                                                                         | **锁定模型 (Distribution)**                                                                                                                                                  | **标准解题动作 (四大公式闭眼套$M_X(t) = \sum e^{tx} \cdot P(X=x)$                                                                                                                                                                                    |
| -------------------- | ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 只抛一次硬币               | **单次试验**，只有“成功”和“失败”。<br>触发词: "coin flip", "success/failure"                                                | **伯努利分布**Bernoulli <br>$B(1, p)$<br>直接加起来x=0和1<br>                                                                                                                       | 求概率: $P(X=1)=p, P(X=0)=1-p$<br>求期望: $\mathbb{E}[X] = p$<br>求方差: $Var(X) = p(1-p)$<br>求MGF: $M(t) = 1-p+pe^t$ $M'(t) = pe^t$                                                                                                             |
| 有放回连抽10次             | **$n$次独立重复试验**，问成功几次。<br>触发词: "with replacement" (有放回),<br>"repeat $n$ times" (重复n次),<br>"independent" (独立) | **二项分布**Binomial<br> $B(n, p)$  <br>n总共抽了几次， p单次中奖概率（有放回）， 最终一共抽中了几个。$\sum \binom{n}{k} a^k b^{n-k} = (a+b)^n$<br>把$pe^t$看成a，1-p看成b                                      | 求恰好$x$次: $P(X=x) = \binom{n}{x}p^x(1-p)^{n-x}$<br>求期望: $\mathbb{E}[X] = np$<br>求方差: $Var(X) = np(1-p)$<br>求MGF: $M(t) = (1-p+pe^t)^n$$M'(t) = n(1-p+pe^t)^{n-1}pe^t$                                                                    |
| 无放回地直接抓一把，数一数抓到了几个   | 从$N$个里**无放回抽$n$个**，问抽中目标$x$个概率。<br>触发词: "without replacement" (无放回),<br>"draw $k$ items" (一次性抽出)            | **超几何分布**Hypergeometric<br>X∼HG(N,K,n)<br>N总池子大小， K池子里目标总数，n一口气抽了几个（无放回）， x抽出的这批里含几个目标。<br>恒等式：$\sum \binom{M}{x}\binom{N-M}{n-x} = \binom{N}{n}$保证总概率1                  | 求概率: $P(X=x) = \frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}$<br>求期望: $\mathbb{E}[X] = n\frac{K}{N}$<br>求方差: $Var(X) = n\frac{K}{N}(1-\frac{K}{N})\frac{N-n}{N-1}$<br>求MGF: (考试一般不考超几何的MGF)                                         |
| 一直单抽，直到抽出第1个金光才停手。   | 一直做试验，**直到出现第1次成功**。<br>触发词: "the first time" (直到第一次出现...),<br>"until the first..."                         | **几何分布 Geometric $Ge(p)$**<br>$p$ 单次中奖概率，$x$ 一直单抽，直到第 $x$ 次才“第一次”出金。$\sum_{k=1}^{\infty} r^{k-1} = \frac{1}{1-r}$<br>$r = (1-p)e^t$                                      | 求恰好第$x$次: $P(X=x) = (1-p)^{x-1}p$(第一次成功在第x次实验)<br>求期望: $\mathbb{E}[X] = 1/p$<br>求方差: $Var(X) = (1-p)/p^2$<br>求MGF: $M(t) = \frac{pe^t}{1-(1-p)e^t}$ $M'(t) = \frac{pe^t}{(1-(1-p)e^t)^2}$                                               |
| 一直单抽，直到抽出第 n 个金光才停手。 | 一直做试验，**直到出现第$n$次成功**才停。<br>触发词: "the first time... $n$ items"<br>(直到出现第 $n$ 个...才停止)                       | **负二项分布**<br>Negative Binomial $Ne(r, p)$<br>$r$ 目标要凑齐几个，$p$ 单次中奖概率，$x$ 一直单抽，直到第 $x$ 次才刚好凑齐 $r$ 个。<br>$\sum \binom{k-1}{n-1} r^{k-n} = (1-r)^{-n}$                       | 求恰好第$x$次: $P(X=x) = \binom{x-1}{r-1}p^r(1-p)^{x-r}$<br>求期望: $\mathbb{E}[X] = n/p$<br>求方差: $Var(X) = n(1-p)/p^2$<br>求MGF: $M(t) = \left(\frac{pe^t}{1-(1-p)e^t}\right)^n$$M'(t) = n M(t) \left( 1 + \frac{(1-p)e^t}{1-(1-p)e^t} \right)$ |
| 蹲在路口，数一个小时内过去了多少辆车。  | **固定时间/空间内**，随机事件发生的次数。<br>触发词: "rate of $\lambda$" (平均发生率),<br>"per hour/day/minute" (每段时间内)               | **泊松分布**<br>Poisson $P(\lambda)$ $\lambda$ 固定的平均掉落率/发生频率，$x$ 实际到底掉落了/发生了几个。<br>$\sum_{k=0}^{\infty} \frac{a^k}{k!} = e^a$ 把$\sum_{k=0}^{\infty} \frac{a^k}{k!} = e^a$看成a | 求恰好发生$x$次: $P(X=x) = \frac{\lambda^x e^{-\lambda}}{x!}$<br>求期望: $\mathbb{E}[X] = \lambda$<br>求方差: $Var(X) = \lambda$<br>求MGF: $M(t) = e^{\lambda(e^t-1)}$$M'(t) = e^{\lambda(e^t-1)} \cdot \lambda e^t$                                 |



#### **② ⚠️ 常见分布比较 (Common Distribution Comparisons)**
1.  **二项 vs. 超几何 (Binomial vs. Hypergeometric):**
    *   $B(n,p)$: 有放回抽样, 独立重复试验, $p$ 不变.
    *   $Hy(N,K,n)$: 无放回抽样, 非独立试验, 成功概率改变.
2.  **几何 vs. 负二项 (Geometric vs. Negative Binomial):**
    *   $Ge(p)$: 首次成功所需的试验次数.
    *   $Ne(r,p)$: 第 $r$ 次成功所需的试验次数. $Ge(p)$ 是 $Ne(1,p)$ 的特例.
    * **联系**：负二项分布 $Ne(r, p)$ 其实就是 $r$ 个相互独立的几何分布 $Ge(p)$ 之和。所以 $\mathbb{E}[Ne] = r \cdot \mathbb{E}[Ge] = r/p$。这种拆分思想在算方差时也极快。
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
3.  **期望 (Expectation):** 对于定义在 [a,b] 上的连续随机变量 X，$\mathbb{E}[X] = \int_{a}^{b} x \cdot f(x) \, dx$，$\mathbb{E}[X] = \int_{0}^{\infty} [1 - F(x)] \, dx$I这个只适用于非负随机变量，如果负数则使用公式$\mathbb{E}[X] = \int_{0}^{\infty} [1 - F(x)] \, dx - \int_{-\infty}^{0} F(x) \, dx$）
	- $\mathbb{E}[aX] = a\mathbb{E}[X]$
	- $\mathbb{E}[b] = b$
	- $\mathbb{E}[aX + b] = a\mathbb{E}[X] + b$
4.  **方差 (Variance):** $Var(X) = \int_{-\infty}^\infty (x-E[X])^2 f(x)dx = E[X^2] - (E[X])^2$.
	- 已知$\mathbb{E}[X]$ ,可以通过PDF，然后求出x^2的情况$\mathbb{E}[X^2] = \int_{0}^{1} x^2 f(x) \, dx$
5.  **矩生成函数 (MGF):** $M_X(t) = E[e^{tX}] = \int_{-\infty}^\infty e^{tx} f(x)dx$.
	- **MGF 的线性性质**： 如果 $Z = aX + b$，那么 Z 的 MGF 与 X 的关系为：$M_Z(t) = e^{bt} M_X(at)$
	- 求期望：$\mathbb{E}[Z] = M_Z'(0)$ ，$\mathbb{E}[X^n] = M_X^{(n)}(0)$
	- 如果有两个**相互独立**的随机变量 $X, Y$，那么它们和 $S = X + Y$ 的 MGF 满足：$M_{X+Y}(t) = M_X(t) \cdot M_Y(t)$，题目如果给你一个奇怪的 MGF（比如两个指数函数相乘），让你求期望，你不需要求导，直接看它能拆成哪两个已知分布的乘积，然后直接加它们的期望就行。
6.  **正态分布标准化 (Standardization of Normal):** 若 $X \sim \mathcal{N}(\mu, \sigma^2)$, 则 $Z = \frac{X-\mu}{\sigma} \sim \mathcal{N}(0, 1)$.
    *   $P(X \le x) = P(Z \le \frac{x-\mu}{\sigma}) = \Phi(\frac{x-\mu}{\sigma})$, 其中 $\Phi$ 是标准正态 CDF.
7. **生存函数Survival function**; $S(x) = 1 - F(x)$，其中后面那个是CDF，$\mathbb{E}[X] = \int_{0}^{\infty} [1 - F(x)] \, dx$
8. 无记忆性Memoryloss property:$P(X > s+t \mid X > s) = P(X > t)$

| **特性**   | **PDF (f(x))**            | **CDF (F(x))**                           |
| -------- | ------------------------- | ---------------------------------------- |
| **定义**   | 概率密度（某一点附近的“密集程度”）        | 累积概率（变量小于等于 $x$ 的总概率）                    |
| **数学关系** | $f(x) = \frac{d}{dx}F(x)$ | $F(x) = \int_{-\infty}^{x} f(t) dt$ (积分) |
| **范围限制** | $f(x) \ge 0$ (可以大于 1)     | $0 \le F(x) \le 1$ (概率不能超标)              |
| **图形直观** | 曲线的高度                     | 曲线下方的**面积**                              |


|             | **情景描述与触发词 (Scenarios & Keywords)**                                                          | **锁定模型 (Distribution)**                                                                     | **标准解题动作 (四大公式闭眼套 + MGF求导)**                                                                                                                                                                                                                                    |
| ----------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 等公交车等多久     | 在区间$[a,b]$内**等可能发生**。<br>触发词: "uniformly distributed",<br>"randomly chosen from interval"    | **均匀分布**Uniform $U(a,b)$ $a$ 最早/下限，$b$ 最晚/上限，$x$ 介于两者之间的某个具体时间或数值。                          | 密度函数(PDF): $f(x) = \frac{1}{b-a}$<br>求期望: $\mathbb{E}[X] = \frac{a+b}{2}$<br>求方差: $Var(X) = \frac{(b-a)^2}{12}$<br>求MGF: $M(t) = \frac{e^{tb}-e^{ta}}{t(b-a)}$<br>MGF一阶导: $M'(t) = \frac{t(be^{tb}-ae^{ta}) - (e^{tb}-e^{ta})}{t^2(b-a)}$                       |
| 下一个客人多久才进店。 | 两次泊松事件之间的**时间间隔/寿命等待时间**。<br>触发词: "time until next event",<br>"lifetime", "rate $\lambda$"   | **指数分布**Exponential $Exp(\lambda)$ <br>$\lambda$ 平均发生频率，$x$ (或 $t$) 苦苦等了多久才“第一次”发生/来临。      | 密度函数(PDF): $f(x) = \lambda e^{-\lambda x}$<br>求期望: $\mathbb{E}[X] = 1/\lambda$<br>求方差: $Var(X) = 1/\lambda^2$<br>求MGF: $M(t) = \frac{\lambda}{\lambda-t}$ (当 $t<\lambda$)<br>MGF一阶导: $M'(t) = \frac{\lambda}{(\lambda-t)^2}$                                    |
| 机器打包面粉的误差   | 典型**钟形曲线/中心极限定理/测量误差**。<br>触发词: "normally distributed",<br>"mean $\mu$, variance $\sigma^2$" | **正态分布**Normal $N(\mu, \sigma^2)$ <br>$\mu$ 平均水平，$\sigma$ 波动大小/标准差，$x$ 你关心的具体数值（如考试分数）。<br> | 密度函数(PDF): $f(x) = \frac{1}{\sqrt{2\pi\sigma^2}}e^{-\frac{(x-\mu)^2}{2\sigma^2}}$<br>求期望: $\mathbb{E}[X] = \mu$<br>求方差: $Var(X) = \sigma^2$<br>求MGF: $M(t) = e^{\mu t + \sigma^2 t^2 / 2}$<br>MGF一阶导: $M'(t) = (\mu + \sigma^2 t) e^{\mu t + \sigma^2 t^2 / 2}$ |
|             |                                                                                              |                                                                                             |                                                                                                                                                                                                                                                                 |
 
- 如果题目出现 **"at least (至少) / at most (至多)"** $\rightarrow$ 把对应的**求概率公式**进行累加 (离散型用 $\sum$) 或积分 (连续型用 $\int$)。例如至少3次就是 $1 - P(X=0) - P(X=1) - P(X=2)$。

### 高频使用的计算结论
| **类型**   | **积分式**                                                   | **结果**               | **常见用途**       |
| -------- | --------------------------------------------------------- | -------------------- | -------------- |
| **基础指数** | $\int_{0}^{\infty} e^{-ax} dx$                            | $\frac{1}{a}$        | 指数分布全概率归一化     |
| **一阶期望** | $\int_{0}^{\infty} x e^{-ax} dx$                          | $\frac{1}{a^2}$      | 指数分布的期望 $E[X]$ |
| **二阶矩**  | $\int_{0}^{\infty} x^2 e^{-ax} dx$                        | $\frac{2}{a^3}$      | 计算方差 $Var(X)$  |
| **高斯积分** | $\int_{-\infty}^{\infty} e^{-x^2} dx$                     | $\sqrt{\pi}$         | 正态分布的基础        |
| 指数函数     | $\sum_{k=0}^{\infty} \frac{a^k}{k!}$                      | $e^a$                | 化简求和式子         |
| 伽马函数     | $\int_{0}^{\infty} x^n e^{-ax} dx$                        | $\frac{n!}{a^{n+1}}$ |                |
| 尾概率      | $P(X > n) = \sum_{x=n+1}^{\infty} (1-\theta)^{x-1}\theta$ | $(1-\theta)^n$       | 知道n+1次或更晚才发生   |
