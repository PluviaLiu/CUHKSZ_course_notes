
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
    - 用PDF表达：$f(x,y) = f_X(x) \cdot f_Y(y)$，对所有 $(x,y)$ 成立
4.  **划分 (Partition):** 集合族 $\{B_i\}$ 是 $\Omega$ 的划分, 若 $B_i$ 互斥 ($B_i \cap B_j = \emptyset, \forall i \neq j$) 且 $\bigcup_i B_i = \Omega$.
5. 考试公式先写：$Consider probability space (Ω, F , P) and let A, B ∈ F with P(A), P(B) > 0.$
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
7.  **概率生成函数 (PGF):** $G_X(s) = E[s^X] = \sum_{k=0}^\infty p_k s^k$ （仅适用于离散型非负整数随机变量）。$G_K(\text{某个东西}) = E[(\text{某个东西})^K]$
    *   **性质**: 
        *   $G_X(1) = 1$
        *   $E[X] = G_X'(1)$
        *   $Var(X) = G_X''(1) + G_X'(1) - [G_X'(1)]^2$
    *   **常见 PGF**:
        *   **Poisson($\lambda$)**: $G(s) = e^{\lambda(s-1)}$
        *   **Geometric($p$)**: $G(s) = \frac{ps}{1-(1-p)s}$ (从1开始) 或 $\frac{p}{1-(1-p)s}$ (从0开始)
        *   **Binomial($n,p$)**: $G(s) = (q+ps)^n$




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

 
- 如果题目出现 **"at least (至少) / at most (至多)"** $\rightarrow$ 把对应的**求概率公式**进行累加 (离散型用 $\sum$) 或积分 (连续型用 $\int$)。例如至少3次就是 $1 - P(X=0) - P(X=1) - P(X=2)$。


---

### **4. 联合与多维分布 (Joint & Multivariate Distributions)**

#### **① 定义与概念 (Definitions & Concepts)**
1.  **联合分布 (Joint Distribution):**
    *   **联合 CDF:** $F(x,y) = P(X \le x, Y \le y)$。
        *   性质: (i) 非降, (ii) 右连续, (iii) $\lim_{x,y\to-\infty} F(x,y) = 0$, (iv) $\lim_{x,y\to\infty} F(x,y) = 1$。
    *   **离散型 (Jointly Discrete):** 若 $(X,Y)$ 只取可数个值，则有联合 PMF $f(x,y) = P(X=x, Y=y)$。
        *   性质: (i) $f(x,y) \ge 0$, (ii) $\sum_x \sum_y f(x,y) = 1$。
    *   **连续型 (Jointly Continuous):** 若存在联合 PDF $f: \mathbb{R}^2 \to [0, \infty)$ 使得 $F(x,y) = \int_{-\infty}^y \int_{-\infty}^x f(u,v)dudv$。
        *   性质: (i) $f(x,y) \ge 0$, (ii) $\int_{-\infty}^\infty \int_{-\infty}^\infty f(x,y)dxdy = 1$。
        *   关系: $f(x,y) = \frac{\partial^2 F(x,y)}{\partial x \partial y}$ (在连续点处)。
        *   ⚠️ $f(x,y)$ 不是概率, $P(X=x, Y=y)=0$。
2.  **边缘分布 (Marginal Distribution):**
    *   **离散 PMF:** $f_X(x) = \sum_y f(x,y)$。
    *   **连续 PDF:** $f_X(x) = \int_{-\infty}^\infty f(x,y)dy$。
    *   💡 **口诀：求谁就不积谁** (求 $X$ 的边缘，就把 $y$ 积分积掉)。
3.  **条件分布 (Conditional Distribution):** 
    *   **离散:** $f(y|x) = \frac{f(x,y)}{f_X(x)}$ (要求 $f_X(x)>0$)。
    *   **连续:** $f(y|x) = \frac{f(x,y)}{f_X(x)}$ (要求 $f_X(x)>0$)。
    *   💡 **口诀：条件在下，联合在上**。
4.  **独立性 (Independence):**
    *   **离散:** $X, Y$ 独立 $\iff f(x,y) = f_X(x) \cdot f_Y(y)$ 对所有 $(x,y)$ 成立。
    *   **连续:** $X, Y$ 独立 $\iff f(x,y) = f_X(x) \cdot f_Y(y)$ 对所有 $(x,y)$ 成立。
    *   **通用 CDF:** $X, Y$ 独立 $\iff F(x,y) = F_X(x) \cdot F_Y(y)$ 对所有 $(x,y)$ 成立。
    *   ⚠️ **支持集检验**: 若 $x$ 和 $y$ 的取值范围相互依赖（如 $0 < x < y < 1$），则**直接判定不独立**，无需验证公式。
5.  **协方差 (Covariance):** $Cov(X,Y) = E[(X-E[X])(Y-E[Y])] = E[XY] - E[X]E[Y]$。
6.  **相关系数 (Correlation):** $\rho(X,Y) = \frac{Cov(X,Y)}{\sqrt{Var(X)Var(Y)}}$，其中 $|\rho| \le 1$。
7.  **顺序统计量 (Order Statistics):** 随机样本 $X_1, \dots, X_n$ 从小到大排序后的值 $X_{(1)} \le \dots \le X_{(n)}$。
8.  **泊松过程 (Poisson Process):** 速率为 $\lambda$ 的计数过程 $\{N_t\}$。
    *   $N_0=0$。
    *   增量独立且平稳。
    *   $N_t - N_s \sim P(\lambda(t-s))$。
9.  **多维正态分布 (Multivariate Normal):** 随机向量 $(X_1, \dots, X_d)$ 的任意线性组合 $\sum t_j X_j$ 均服从正态分布。

#### **② 公式与方程 (Formulas & Equations)**
1.  **联合期望 (Joint Expectation):**
    *   **离散:** $E[g(X,Y)] = \sum_x \sum_y g(x,y) f(x,y)$。
    *   **连续:** $E[g(X,Y)] = \int_{-\infty}^\infty \int_{-\infty}^\infty g(x,y) f(x,y) dxdy$。
    *   **特例:** $E[XY] = \int_{-\infty}^\infty \int_{-\infty}^\infty xy \cdot f(x,y) dxdy$ (用于计算协方差)。
2.  **条件期望 (Conditional Expectation):**
    *   **离散:** $E[Y|X=x] = \sum_y y \cdot f(y|x)$。
    *   **连续:** $E[Y|X=x] = \int_{-\infty}^\infty y \cdot f(y|x) dy$。
    *   ⚠️ **注意**: 积分里用的是**条件 PDF** $f(y|x)$，不是联合 PDF $f(x,y)$。
3.  **区域概率计算 (Probability over Regions):**
    *   对于连续型随机变量，计算 $P(X \in A, Y \in B)$ 需要在对应区域上积分：
        $$P((X,Y) \in D) = \iint_D f(x,y) \, dx \, dy$$
    *   **常见情况**：
        *   $P(X > Y) = \int_{-\infty}^{\infty} \int_{y}^{\infty} f(x,y) \, dx \, dy = \int_{-\infty}^{\infty} \int_{-\infty}^{x} f(x,y) \, dy \, dx$
        *   $P(X + Y \le c) = \iint_{x+y \le c} f(x,y) \, dx \, dy$
        *   $P(X < Y < X+a) = \int_{-\infty}^{\infty} \int_{x}^{x+a} f(x,y) \, dy \, dx$
    *   💡 **技巧**: 画出区域 $D$ 在 $(x,y)$ 平面上的图形，确定积分上下限的相互依赖关系。
    *   💡 **对称性**: 若 $X, Y$ 独立同分布且连续，则 $P(X > Y) = P(Y > X) = \frac{1}{2}$ (因为 $P(X=Y)=0$)。
4.  **全期望公式 (Law of Total Expectation):** $E[Y] = E[E[Y|X]]$。
    *   **Taking out what is known**: $E[g(X)Y | X] = g(X) E[Y|X]$。
    *   *直观理解*：在已知 $X$ 的条件下，$g(X)$ 就像一个常数，可以提到期望符号外面。
5.  **条件方差公式 (Law of Total Variance):** $Var(Y) = E[Var(Y|X)] + Var(E[Y|X])$。
6.  **随机变量函数转换 (Change of Variables):**
    *   **一维:** $Y=g(X)$, $f_Y(y) = f_X(g^{-1}(y)) |\frac{d}{dy}g^{-1}(y)|$。
    *   **多维:** $(Y_1, Y_2) = T(X_1, X_2)$, $g(y_1, y_2) = f(T^{-1}(y_1, y_2)) |J|$。其中 $J$ 是 $T^{-1}$ 变换的雅可比行列式 (Jacobian) 的绝对值。
7.  **顺序统计量 PDF:** $X_{(j)}$ 的 PDF 为 $f_{X_{(j)}}(x) = \frac{n!}{(j-1)!(n-j)!} f(x) [F(x)]^{j-1} [1-F(x)]^{n-j}$。
8.  **泊松过程与指数分布:** 泊松过程的事件间隔时间服从独立的指数分布，参数为 $\lambda$。
9.  **正态相关分布 (Distributions related to Normal):**
    *   若 $Z_i \stackrel{i.i.d.}{\sim} N(0,1)$, 则 $\sum_{i=1}^n Z_i^2 \sim \chi_n^2$ (卡方分布 Chi-squared)。
    *   若 $Z \sim N(0,1), Y \sim \chi_n^2$ 且独立, 则 $\frac{Z}{\sqrt{Y/n}} \sim t_n$ (t-分布)。
    *   若 $X \sim \chi_{d_1}^2, Y \sim \chi_{d_2}^2$ 且独立, 则 $\frac{X/d_1}{Y/d_2} \sim F_{d_1, d_2}$ (F-分布)。
10.  **随机项数之和 (Compound Distribution / Random Sums):**
    *   设 $Z = X_1 + X_2 + \dots + X_N$，其中 $N$ 是随机变量，$X_i$ 是 i.i.d. 且独立于 $N$。
    *   **PGF 复合公式**: $G_Z(s) = G_N(G_X(s))$ （记忆法：$N$ 在外面，因为 $N$ 决定了层数）
    *   **MGF 复合公式**: $M_Z(t) = G_N(M_X(t))$ 或 $M_N(\ln M_X(t))$
    *   **Wald's Identity (期望)**: $E[Z] = E[N] \cdot E[X]$
    *   **方差公式**: $Var(Z) = E[N]Var(X) + (E[X])^2 Var(N)$ （利用全方差公式推导）

#### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **不相关 vs. 独立:** 独立 (Independent) $\implies$ 不相关 (Uncorrelated, $Cov=0$)。反之不成立，除非是多维正态分布。
    *   反例: $X \sim N(0,1), Y=X^2$。$X, Y$ 不相关但相关。

#### **④ 关键点与补充 (Key Points & Additional Notes)**
1.  **i.i.d. 连续随机变量的对称性:** 对于 i.i.d. 连续 RV $X_1, \dots, X_n$，任何一种排序 $P(X_{p(1)} < \dots < X_{p(n)})$ 的概率都是 $1/n!$。

---

---

---

### **5. 不等式与收敛模式 (Inequalities & Modes of Convergence)**

#### **① 定义与概念 (Definitions & Concepts)**
1.  **依概率收敛 (Convergence in Probability):** $X_n \xrightarrow{P} c$ if $\forall \epsilon > 0, \lim_{n\to\infty} P(|X_n - c| > \epsilon) = 0$。
2.  **依分布收敛 (Convergence in Distribution):** $X_n \xrightarrow{d} X$ if $\lim_{n\to\infty} F_n(x) = F(x)$ 对所有 $F(x)$ 的连续点成立。
3.  **特征函数 (Characteristic Function):** $\phi_X(t) = E[e^{itX}]$。
4. 同分布：x1 x2等等下标可以统一写成x,因为服从相同的分布

#### **② 公式与方程 (Formulas & Equations)**
1.  **马尔可夫不等式 (Markov's Inequality):** 对非负 RV $X$ 和 $\epsilon>0$, $P(X \ge \epsilon) \le \frac{E[X]}{\epsilon}$。
2.  **切比雪夫不等式 (Chebyshev's Inequality):** $P(|X - \mu| \ge \epsilon) \le \frac{Var(X)}{\epsilon^2}$。
3.  **弱大数定律 (Weak Law of Large Numbers, WLLN):** 若 $X_i$ i.i.d. 且 $E[|X_1|] < \infty$，则 $\bar{X}_n = \frac{1}{n}\sum_{i=1}^n X_i \xrightarrow{P} E[X_1]$。
4.  **中心极限定理 (Central Limit Theorem, CLT):** 若 $X_i$ i.i.d. 且 $E[X_1^2] < \infty$ (即均值 $\mu$ 和方差 $\sigma^2$ 存在)，则 $\frac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} = \frac{\sum X_i - n\mu}{\sigma\sqrt{n}} \xrightarrow{d} N(0, 1)$。

#### **③ 常见错误与混淆 (Common Mistakes & Confusions)**
1.  **WLLN vs. CLT:**
    *   **WLLN** 描述了样本均值会收敛到一个**常数** (总体均值)。
    *   **CLT** 描述了标准化后的样本均值的**分布**会趋近于标准正态分布。
    * Gumbel 说的是"某些分布的最大值，做适当变换后都趋向 Gumbel

#### **④ 关键点与补充 (Key Points & Additional Notes)**
1.  **通过特征函数判断依分布收敛:** $X_n \xrightarrow{d} X \iff \lim_{n\to\infty} \phi_{X_n}(t) = \phi_X(t)$ 对所有 $t$ 成立。
2.  **CLT 应用:** 提供了用正态分布近似大量 i.i.d. 随机变量之和的分布的理论依据。


概率论证明题最后一句话：
Since the equality is true for every n it holds in the limit，（由于对每个n成立，极限成立）
the function 1 − e−v is the CDF of an E(1) random variable.（识别函数分布）

---

#### 4. 考试时可以干什么？
- 最大值的 CDF：$\mathbb{P}(Y_n \leq x) = [F(x)]^n$（独立→可以连乘，同分布→每个因子都是同一个 $F$）
- **大数定律 (Law of Large Numbers)**：样本均值趋近总体均值
- **中心极限定理 (Central Limit Theorem)**：样本均值标准化后趋近正态分布


不是通用的，**只对特定类型的分布成立**。

考试会**直接给你 $F(x)$**，让你自己算极限：

● 代入 $F_{Y_n}(x) = [F(x)]^n$

↓ 做变换（比如 $U_n = Y_n - \log n$）

↓ 算 $\lim_{n\to\infty}[F(x + \log n)]^n$

↓ 得到极限 CDF，验证合法性
验证左极限为0，右极限为1，验证cdf单调不减

↓ 认出它叫什么名字（加分，不认识也没关系）
