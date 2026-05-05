
### 1. 概率导论 (Introduction to Probability)

#### ① 定义与概念 (Definitions & Concepts)
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
    - 用PDF表达：$f(x,y) = f_X(x) \cdot f_Y(y)$，对所有 $(x,y)$ 成立
4.  **划分 (Partition):** 集合族 $\{B_i\}$ 是 $\Omega$ 的划分, 若 $B_i$ 互斥 ($B_i \cap B_j = \emptyset, \forall i \neq j$) 且 $\bigcup_i B_i = \Omega$.
5. 考试公式先写：$Consider probability space (Ω, F , P) and let A, B ∈ F with P(A), P(B) > 0.$
#### ② 公式与定理 (Formulas & Theorems)
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

#### ③ ⚠️ 常见错误与混淆 (Common Mistakes & Confusions)
1.  **排列 vs. 组合 (Permutation vs. Combination):** 排列关心顺序 (order matters), 组合不关心 (order doesn't matter).
2.  **独立 vs. 互斥 (Independent vs. Disjoint):** 若 $P(A), P(B) > 0$, 则 $A, B$ 互斥 $\implies$ $P(A \cap B) = 0 \neq P(A)P(B) \implies$ $A, B$ 不独立 (相关).互斥意味着“有你没我”。如果我知道 $A$ 发生了，那 $B$ 肯定没发生。这意味着 $A$ 的信息极大地影响了对 $B$ 的判断，所以它们**极度相关**。
3.  **零概率 vs. 不可能事件 (Null vs. Impossible):** $P(A)=0$ (零概率) $\not\implies A=\emptyset$ (不可能). 连续 RV 取单点概率为0但可能发生.
4.  **辛普森悖论 (Simpson's Paradox):** 分组数据中的趋势在合并后可能逆转.

---
### 2. 离散型随机变量 (Discrete Random Variables)

#### ① 定义与性质 (Definitions & Properties)
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
7.  **概率生成函数 (PGF):** $G_X(s) = E[s^X] = \sum_{k=0}^\infty p_k s^k$ （仅适用于离散型非负整数随机变量）。$G_K(\text{某个东西}) = E[(\text{某个东西})^K]$
    *   **性质**: 
        *   $G_X(1) = 1$
        *   $E[X] = G_X'(1)$
        *   $Var(X) = G_X''(1) + G_X'(1) - [G_X'(1)]^2$
    *   **常见 PGF**:
        *   **Poisson($\lambda$)**: $G(s) = e^{\lambda(s-1)}$
        *   **Geometric($p$)**: $G(s) = \frac{ps}{1-(1-p)s}$ (从1开始) 或 $\frac{p}{1-(1-p)s}$ (从0开始)
        *   **Binomial($n,p$)**: $G(s) = (q+ps)^n$




#### ② ⚠️ 常见分布比较 (Common Distribution Comparisons)
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
### 3. 连续型随机变量 (Continuous Random Variables)

#### ① 定义与性质 (Definitions & Properties)
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

 
- 如果题目出现 **"at least (至少) / at most (至多)"** $\rightarrow$ 把对应的**求概率公式**进行累加 (离散型用 $\sum$) 或积分 (连续型用 $\int$)。例如至少3次就是 $1 - P(X=0) - P(X=1) - P(X=2)$。


---

### 4. 联合与多维分布 (Joint & Multivariate Distributions)

#### ① 定义与概念 (Definitions & Concepts)
1.  **联合分布 (Joint Distribution):**
    *   **联合 CDF:** $F(x,y) = P(X \le x, Y \le y)$
    *   **联合 PDF/PMF:** $f(x,y)$（离散用求和，连续用积分）
        *   性质: $f(x,y) \ge 0$，全概率归一（$\sum\sum = 1$ 或 $\int\int = 1$）
        *   ⚠️ 连续型：$f(x,y)$ 不是概率，$P(X=x, Y=y)=0$
2.  **边缘分布 (Marginal):** $f_X(x) = \sum_y f(x,y)$ 或 $\int f(x,y)dy$
    *   💡 **口诀：求谁就不积谁**
3.  **条件分布 (Conditional):** $f(y|x) = \frac{f(x,y)}{f_X(x)}$（要求 $f_X(x)>0$）
    *   💡 **口诀：条件在下，联合在上**
4.  **独立性 (Independence):** $f(x,y) = f_X(x) \cdot f_Y(y)$ 对所有 $(x,y)$ 成立
    *   ⚠️ **支持集检验**: 若 $x$ 和 $y$ 的取值范围相互依赖（如 $0 < x < y < 1$），则**直接判定不独立**
5.  **协方差:** $Cov(X,Y) = E[XY] - E[X]E[Y]$
6.  **相关系数:** $\rho(X,Y) = \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$，$|\rho| \le 1$

#### ② 核心公式 (Key Formulas)
1.  **联合期望:** $E[g(X,Y)] = \sum\sum g(x,y)f(x,y)$ 或 $\iint g(x,y)f(x,y)dxdy$
    *   特例：$E[XY] = \iint xy \cdot f(x,y)dxdy$（用于算协方差）
2.  **条件期望:** $E[Y|X=x] = \sum y \cdot f(y|x)$ 或 $\int y \cdot f(y|x)dy$
    *   ⚠️ 用的是**条件PDF** $f(y|x)$，不是联合PDF
3.  **全期望公式:** $E[Y] = E[E[Y|X]]$
    *   **Taking out known**: $E[g(X)Y|X] = g(X)E[Y|X]$
4.  **全方差公式:** $Var(Y) = E[Var(Y|X)] + Var(E[Y|X])$
5.  **区域概率 (连续):** $P(X>Y) = \int_{-\infty}^{\infty}\int_y^{\infty} f(x,y)dxdy$
    *   💡 画图确定积分上下限；若$X,Y$独立同分布，$P(X>Y)=\frac{1}{2}$
6.  **随机项数之和:** 设 $Z = X_1 + \cdots + X_N$（$N$随机，$X_i$ i.i.d.且独立于$N$）
    *   **PGF复合**: $G_Z(s) = G_N(G_X(s))$（$N$在外面）
    *   **期望**: $E[Z] = E[N] \cdot E[X]$
    *   **方差**: $Var(Z) = E[N]Var(X) + (E[X])^2Var(N)$

#### ③ 常见错误 (Common Mistakes)
1.  **不相关 ≠ 独立:** 独立$\implies$不相关($Cov=0$)，反之不成立
    *   反例: $X \sim N(0,1), Y=X^2$不相关但不独立

---


### 5. 不等式与收敛模式 (Inequalities & Convergence)

#### ① 核心定义 (Definitions)
1.  **依概率收敛:** $X_n \xrightarrow{\mathbb{P}} c \iff \forall \epsilon > 0, \lim_{n\to\infty} P(|X_n - c| > \epsilon) = 0$
2.  **依分布收敛:** $X_n \xrightarrow{d} X \iff \lim_{n\to\infty} F_n(x) = F(x)$（在$F$的连续点）
3.  **收敛强弱:** 几乎必然 $\implies$ 依概率 $\implies$ 依分布

#### ② 核心不等式 (Inequalities)
1.  **马尔可夫不等式**（$X \ge 0$）: $P(X \ge a) \le \frac{E[X]}{a}$
2.  **切比雪夫不等式**: $P(|X - \mu| \ge \epsilon) \le \frac{Var(X)}{\epsilon^2}$

#### ③ 核心定理 (Key Theorems)
1.  **弱大数定律 (WLLN):** $\bar{X}_n = \frac{1}{n}\sum X_i \xrightarrow{\mathbb{P}} E[X_1]$（$X_i$ i.i.d.）
    *   **证明套路**: 算$E[\bar{X}_n]=\mu$，$Var(\bar{X}_n)=\frac{\sigma^2}{n}$ → 切比雪夫 → 取极限
2.  **中心极限定理 (CLT):** $\frac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} \xrightarrow{d} N(0,1)$
    *   **应用**: $n$大时，$\bar{X}_n \approx N(\mu, \sigma^2/n)$
3.  **连续映射定理:** 若$X_n \xrightarrow{\mathbb{P}} c$且$g$连续，则$g(X_n) \xrightarrow{\mathbb{P}} g(c)$
    *   **常用**: $\ln X_n \to c \implies X_n \to e^c$

#### ④ 证明技巧 (Proof Techniques)
1.  **证明依概率收敛** → 用切比雪夫不等式
2.  **处理乘积** → 取对数变求和 → WLLN → 连续映射定理
3.  **最大值极限** → CDF: $[F(x)]^n$ → 变换 → 极限公式: $\lim[1-a/n]^n = e^{-a}$

---

