# Q1
#### 1. 题目翻译 (Translation of the Question)

- **原题内容：**
    - Let $f$ and $g$ be **holomorphic** (全纯的) on an **open disc** (开圆盘) $D(z_0, r)$ **centered at** (以...为中心) $z_0$ with **radius** (半径) $r > 0$.
    - Assume that $f^{(n)}(a) = g^{(n)}(a)$ for all $n = 0, 1, 2, \dots$ (假设对于所有阶数的导数，在点 $a$ 处都相等).
    - **Show that** (证明) $f = g$ on $D(z_0, r)$.

- **中文直译：**
    - 设 $f$ 和 $g$ 是定义在以 $z_0$ 为中心、半径为 $r > 0$ 的开圆盘 $D(z_0, r)$ 上的**全纯函数** (holomorphic functions)。
    - 假设在圆盘内的某一点 $a$，$f$ 和 $g$ 的各阶导数都相等，即对于 $n=0, 1, 2, \dots$，都有 $f^{(n)}(a) = g^{(n)}(a)$。（注意：$n=0$ 时即函数值本身 $f(a)=g(a)$）。
    - 证明：在整个圆盘 $D(z_0, r)$ 上，$f$ 恒等于 $g$。

#### 2. 背景条件与基本概念解释 (Background & Concepts)

- **全纯函数 (Holomorphic Function)：**
    - 这是复分析中最核心的概念。在复数域里，如果一个函数在某点“可微”，它的要求比实数（高中数学）严格得多。
    - **工科直觉：** 全纯函数具有极强的“刚性” (Rigidity)。如果你知道它在一个点附近的长相（导数信息），你就知道了它在很大一片区域的长相。这不像实函数，实函数可以一段是平的，下一段突然弯曲，但全纯函数做不到。

- **开圆盘 (Open Disc) $D(z_0, r)$：**
    - 在复平面上，到中心点 $z_0$ 的距离小于 $r$ 的所有点构成的集合。公式表示为 $\{z \in \mathbb{C} : |z - z_0| < r\}$。
    - **工科直觉：** 这就是一个“连通”的区域，中间没有断开，也没有孤立的点。

- **泰勒级数 (Taylor Series)：**
    - 如果一个函数 $f$ 在点 $a$ 附近是全纯的，那么它一定可以写成幂级数的形式：
        - $f(z) = \sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!} (z-a)^n$
    - **工科直觉：** 导数 $f^{(n)}(a)$ 决定了级数的**系数** (coefficients)。如果两个函数的导数在 $a$ 点一模一样，那么它们在 $a$ 点附近的“基因”就完全一样。

- **唯一性定理 (Identity Theorem)：**
    - 这是本题背后的终极定理。它告诉我们：如果两个全纯函数在某个区域内的一小块地方相等，那么它们在整个连通区域内都相等。

#### 3. 问题解答思路与逻辑链条 (Logical Chain)

我们要证明 $f = g$，最常用的工科思维是：证明它们的差 $h = f - g$ 恒等于 $0$。

- **第一步：构造辅助函数**
    - 令 $h(z) = f(z) - g(z)$。
    - **因为** $f$ 和 $g$ 在 $D(z_0, r)$ 上是 **holomorphic** (全纯的)，
    - **所以** 它们的差 $h$ 在 $D(z_0, r)$ 上也是 **holomorphic** (全纯的)。
    - *（性质：全纯函数的线性组合依然是全纯的）*

- **第二步：转化已知条件**
    - **因为** 题目给出 $f^{(n)}(a) = g^{(n)}(a)$ 对于所有 $n \ge 0$ 成立，
    - **所以** $h^{(n)}(a) = f^{(n)}(a) - g^{(n)}(a) = 0$ 对于所有 $n \ge 0$ 成立。
    - 这意味着函数 $h$ 在点 $a$ 处的所有阶导数（包括函数值本身）全部为 $0$。

- **第三步：利用泰勒展开 (Taylor Expansion)**
    - **因为** $h$ 是全纯函数，它在点 $a$ 附近可以展开为 **Taylor series** (泰勒级数)：
        - $h(z) = \sum_{n=0}^{\infty} c_n (z-a)^n$，其中系数 $c_n = \frac{h^{(n)}(a)}{n!}$。
    - **因为** 我们已经算出所有的 $h^{(n)}(a) = 0$，
    - **所以** 所有的系数 $c_n = 0$。
    - **由此推出** 在点 $a$ 的某个 **neighborhood** (邻域/小范围内)，$h(z) = 0 + 0 + 0 \dots = 0$。

- **第四步：从“局部”推向“整体” (Analytic Continuation)**
    - **因为** $h(z)$ 在点 $a$ 附近恒为 $0$，且 $h$ 在整个 **connected domain** (连通域) $D(z_0, r)$ 上是全纯的，
    - **根据** **Identity Theorem** (唯一性定理)，如果一个全纯函数在区域内的某个开子集上为 $0$，则它在整个区域上必为 $0$。
    - **所以** 对于所有的 $z \in D(z_0, r)$，都有 $h(z) = 0$。

- **第五步：得出结论**
    - **因为** $h(z) = 0$ 意味着 $f(z) - g(z) = 0$，
    - **所以** $f(z) = g(z)$ 对于所有 $z \in D(z_0, r)$ 成立。
    - **Q.E.D.** (证明完毕)

#### 4. 总结与规则应用 (Summary & Rules)

- **什么时候可以使用这个逻辑？**
    - 当你看到“两个全纯函数在某一点的导数全部相等”或者“在一段很小的线段上相等”时，立刻想到它们在整个连通的区域内必然完全相等。
    - **关键点：** 必须强调区域是 **connected** (连通的)。如果区域分成了不相连的两块，这个结论在另一块就不一定成立了。但在本题中，**open disc** (开圆盘) 天然是连通的。

- **答题卡风格总结：**
    - 1. Define $h(z) = f(z) - g(z)$, which is **holomorphic** on $D(z_0, r)$.
    - 2. Since $f^{(n)}(a) = g^{(n)}(a)$, we have $h^{(n)}(a) = 0$ for all $n$.
    - 3. The **Taylor coefficients** of $h$ at $a$ are $c_n = \frac{h^{(n)}(a)}{n!} = 0$, so $h(z) \equiv 0$ in a **neighborhood** of $a$.
    - 4. By the **Identity Theorem** and the fact that $D(z_0, r)$ is **connected**, $h(z) = 0$ for all $z \in D(z_0, r)$.
    - 5. Thus, $f = g$ on $D(z_0, r)$.

# Q2
#### 1. 题目翻译 (Translation of the Question)

- **问题 2：考虑以下函数**
    - $f(z) = \sin\left(\frac{1}{1-z}\right)$，$g(z) = 0$
    - 定义在 **unit disc** (单位圆盘) $D(0, 1)$ 上。

- **(a) 证明 $f$ 和 $g$ 在 $D(0, 1)$ 上是 holomorphic (全纯的)。**
- **(b) 证明在 $D(0, 1)$ 中存在一个由 distinct points (互不相同的点) 组成的 sequence (序列) $(z_n)$，使得 $z_n \to 1$ 且对于所有 $n$ 都有 $f(z_n) = g(z_n)$。**
- **(c) 解释为什么这并不 contradict (矛盾/违背) Identity Theorem (唯一性定理)。**

---

#### 2. 背景条件与基本概念解释 (Background & Concepts)

- **单位圆盘 (Unit Disc) $D(0, 1)$：**
    - 指的是复平面上所有满足 $|z| < 1$ 的点。
    - **注意：** 边界点 $|z| = 1$（比如 $z=1$）**不属于**这个开圆盘。它只是圆盘的边缘。

- **全纯函数的复合 (Composition of Holomorphic Functions)：**
    - **规则：** 如果函数 $A$ 是全纯的，函数 $B$ 也是全纯的，那么复合函数 $A(B(z))$ 在定义域内也是全纯的。
    - **工科理解：** 只要内层函数在某个区域没“爆炸”（没有分母为0的情况），外层函数又是处处可导的，那整体就是全纯的。

- **唯一性定理 (Identity Theorem) 的核心限制：**
    - 定理说：如果两个全纯函数 $f$ 和 $g$ 在一串点 $z_n$ 上相等，且这串点有一个 **accumulation point** (聚点) $a$，只要这个 $a$ 在定义域内，那么 $f$ 就必须**死死地**等于 $g$，全域相等。
    - **关键边界：** 这个 **accumulation point** (聚点) 必须落在函数的 **domain** (定义域) **之内**。如果聚点跑到了定义域的边缘（边界上），定理就失效了。

---

#### 3. 问题 (a) 的解答思路与逻辑链条 (Solution for Part a)

- **目标：** 证明 $f(z)$ 和 $g(z)$ 在 $|z| < 1$ 时是全纯的。

- **逻辑链条：**
    - **对于 $g(z) = 0$：**
        - **因为** $g(z)$ 是一个 **constant function** (常数函数)，
        - **所以** 它在整个复平面 $\mathbb{C}$ 上都是 **holomorphic** (全纯的)。
        - *（性质：常数函数处处可导）*
    - **对于 $f(z) = \sin\left(\frac{1}{1-z}\right)$：**
        - **第一步：** 观察内层函数 $h(z) = \frac{1}{1-z}$。
            - **因为** $h(z)$ 是一个 **rational function** (有理函数)，它只在分母为 $0$（即 $z=1$）时不可导，
            - **因为** 我们的定义域是 **unit disc** $D(0, 1)$，即 $|z| < 1$，点 $z=1$ **不在**这个范围内，
            - **所以** $h(z)$ 在 $D(0, 1)$ 上是 **holomorphic** (全纯的)。
        - **第二步：** 观察外层函数 $\sin(w)$。
            - **因为** $\sin(w)$ 是一个 **entire function** (整函数，指在全复平面全纯)，
            - **所以** 根据 **composition rule** (复合规则)，$f(z) = \sin(h(z))$ 在 $D(0, 1)$ 上是 **holomorphic** (全纯的)。

---

#### 4. 问题 (b) 的解答思路与逻辑链条 (Solution for Part b)

- **目标：** 找到一串点 $z_n$，让 $f(z_n) = 0$，且这些点最后都挤向 $1$。

- **逻辑链条：**
    - **第一步：设置方程**
        - 我们需要 $f(z_n) = \sin\left(\frac{1}{1-z_n}\right) = 0$。
    - **第二步：利用高中三角函数知识**
        - **因为** $\sin(\theta) = 0$ 的解是 $\theta = k\pi$（其中 $k$ 是整数），
        - **所以** 我们令 $\frac{1}{1-z_n} = n\pi$（这里取 $n = 1, 2, 3, \dots$）。
    - **第三步：解出 $z_n$**
        - 倒过来写：$1 - z_n = \frac{1}{n\pi}$。
        - 推出：$z_n = 1 - \frac{1}{n\pi}$。
    - **第四步：验证条件**
        - **条件1：在圆盘内吗？**
            - **因为** $n \ge 1$ 且 $\pi \approx 3.14$，所以 $\frac{1}{n\pi}$ 是一个很小的正数。
            - **所以** $z_n = 1 - (\text{正数}) < 1$，这意味着 $z_n$ 都在 **unit disc** $D(0, 1)$ 内部。
        - **条件2：趋向于 1 吗？**
            - **因为** 当 $n \to \infty$ 时，$\frac{1}{n\pi} \to 0$，
            - **所以** $z_n = 1 - \frac{1}{n\pi} \to 1$。
        - **条件3：点互不相同吗？**
            - **因为** 对于不同的 $n$，$\frac{1}{n\pi}$ 的值都不同，
            - **所以** $z_n$ 是 **distinct points** (互不相同的点)。
    - **结论：** 序列 $z_n = 1 - \frac{1}{n\pi}$ 满足所有要求。

---

#### 5. 问题 (c) 的解答思路与逻辑链条 (Solution for Part c)

- **目标：** 解释为什么明明有一堆相等的点，却不能说 $f = g$（即 $f$ 并不恒等于 $0$）。

- **逻辑链条：**
    - **第一步：回顾 Identity Theorem (唯一性定理) 的前提**
        - 定理要求：两个全纯函数相等的点必须在 **domain** (定义域) 内有一个 **accumulation point** (聚点)。
    - **第二步：分析本题的聚点在哪里**
        - **因为** 在 (b) 小题中，我们发现 $z_n \to 1$，
        - **所以** 这串零点的 **accumulation point** (聚点) 是 $1$。
    - **第三步：检查聚点是否在定义域内**
        - **因为** 函数 $f$ 和 $g$ 的定义域是 **open disc** $D(0, 1)$，即 $\{z : |z| < 1\}$，
        - **因为** 点 $1$ 满足 $|1| = 1$，它在圆盘的 **boundary** (边界) 上，而 **不在** 内部，
        - **所以** 这个聚点 $1 \notin D(0, 1)$。
    - **第四步：得出结论**
        - **因为** 聚点不在定义域内，**Identity Theorem** 的前提条件不满足，
        - **所以** 我们不能推导出 $f(z) = g(z)$ 在整个圆盘上成立。
        - 这就是为什么 $f(z) = \sin\left(\frac{1}{1-z}\right)$ 虽然在很多点上等于 $0$，但它本身不是零函数，这与定理并不矛盾。

---


# Q3
#### 1. 题目翻译 (Translation of the Question)

- **Question 3 (Locally uniform convergence / 局部一致收敛)**
    - 设 $f_n(z) = z^n$，其中 $n = 1, 2, 3, \dots$
    - **(a) 证明：** 在 **unit disk** (单位圆盘) $D(0, 1)$ 上，$f_n \to 0$ 是 **locally uniformly** (局部一致收敛) 的，但是对于所有的 $n$，都有 $f_n(1) = 1$。
    - **(b) 解释：** 为什么在 **boundary** (边界) $|z| = 1$ 上的行为与关于 **open unit disc** (开单位圆盘) 的 **Theorem 12.4.3** (定理 12.4.3) 无关。

---

#### 2. 背景条件与基本概念解释 (Background & Concepts)

- **单位圆盘 (Unit Disk) $D(0, 1)$：**
    - 指的是复平面上满足 $|z| < 1$ 的所有点。这是一个 **open set** (开集)，不包含边界线 $|z|=1$。

- **逐点收敛 (Pointwise Convergence)：**
    - **工科直觉：** 你固定一个点 $z$，看当 $n$ 变大时，$z^n$ 往哪跑。
    - 如果 $|z| < 1$，比如 $z=0.5$，那么 $0.5^n$ 显然趋向于 $0$。

- **一致收敛 (Uniform Convergence)：**
    - **工科直觉：** 所有的点 $z$ 必须以“同样的速度”一起趋向于极限。
    - 在整个 $D(0, 1)$ 上，$z^n$ 其实**不是**一致收敛的。因为越靠近边界（比如 $z=0.999$），$z^n$ 掉到 $0$ 的速度就越慢。

- **局部一致收敛 (Locally Uniform Convergence)：**
    - **核心定义：** 如果在定义域内的任何一个 **compact subset** (紧子集，通常指闭且有界的区域) 上都是一致收敛的，就叫局部一致收敛。
    - **工科直觉：** 虽然在靠近大边界 $|z|=1$ 时速度会变慢，但只要我只看圆盘内部的一个“小一圈”的闭圆盘（比如 $|z| \le 0.99$），在这个小圈子里，收敛速度就是可以统一的。

- **定理 12.4.3 (通常指的含义)：**
    - 这个定理通常说明：如果一列 **holomorphic** (全纯) 函数在开集上 **locally uniformly** (局部一致收敛) 到某个函数 $f$，那么这个极限函数 $f$ 在该开集上也是全纯的。

---

#### 3. 问题 (a) 的解答思路与逻辑链条 (Solution for Part a)

- **第一部分：证明 $f_n(1) = 1$**
    - **因为** $f_n(z) = z^n$，
    - **所以** 当 $z = 1$ 时，$f_n(1) = 1^n = 1$。
    - 这说明在边界点 $z=1$ 处，函数值永远是 $1$，根本不会趋向于 $0$。

- **第二部分：证明在 $D(0, 1)$ 上局部一致收敛到 $0$**
    - **第一步：选取任意紧集**
        - 设 $K$ 是 $D(0, 1)$ 内部的任意一个 **compact subset** (紧子集)。
    - **第二步：确定边界距离**
        - **因为** $K$ 是在开圆盘 $D(0, 1)$ 内部的紧集，
        - **所以** $K$ 与边界 $|z|=1$ 之间一定有一段距离。这意味着存在一个半径 $r < 1$，使得对于 $K$ 里的所有点 $z$，都有 $|z| \le r$。
        - *（工科直觉：紧集不能无限贴近边界而不包含边界，它一定被锁在一个稍小一点的圆 $|z| \le r$ 里面）*
    - **第三步：估计误差 (Uniform Bound)**
        - 对于 $K$ 中的任意 $z$：
        - $|f_n(z) - 0| = |z^n| = |z|^n$。
        - **因为** $|z| \le r$，
        - **所以** $|z|^n \le r^n$。
    - **第四步：利用极限得出一致性**
        - **因为** $r < 1$，所以当 $n \to \infty$ 时，$r^n \to 0$。
        - **注意：** 这个 $r^n$ 只取决于 $r$，与具体的 $z$ 无关。
        - **所以** 在 $K$ 上，误差是一致趋于 $0$ 的。
    - **结论：** $f_n \to 0$ 在 $D(0, 1)$ 上是 **locally uniformly** (局部一致收敛) 的。

---

#### 4. 问题 (b) 的解答思路与逻辑链条 (Solution for Part b)

- **目标：** 解释为什么边界上的“坏表现”（不收敛到 $0$）不影响定理在开集内部的使用。

- **逻辑链条：**
    - **第一步：明确定理的适用范围**
        - **因为** **Theorem 12.4.3** [[Weierstrass极限定理 (Weierstrass Convergence Theorem)]]讨论的是函数在 **open set** (开集) $D(0, 1)$ 上的性质，
        - **所以** 定理只关心开集内部的点，即满足 $|z| < 1$ 的点。
    - **第二步：分析局部一致收敛的定义**
        - **因为** **locally uniform convergence** 的定义只要求在区域内部的 **compact subsets** (紧子集) 上一致收敛，
        - **因为** 任何 $D(0, 1)$ 内部的紧集 $K$ 都**不包含**边界点（如 $z=1$），
        - **所以** 边界点 $z=1$ 处的函数值是多少、是否收敛，完全不会影响“内部紧集一致收敛”这个事实。
    - **第三步：得出结论**
        - **因为** 边界 $|z|=1$ 不在 **open disc** (开圆盘) 内部，
        - **所以** 边界上的行为对于定义在开集上的定理是 **irrelevant** (无关的)。
        - *（工科直觉：只要围墙里面的每一个小块都表现良好，围墙上发生什么火灾都不会影响围墙内函数的全纯性质）*

---

#### 5. 总结与规则应用 (Summary & Rules)

- **什么时候使用“局部一致收敛”？**
    - 当你发现一个函数序列在开集边缘表现很差（比如趋向于无穷，或者像本题一样不收敛），但在内部任何一个闭区域都表现很好时。
    - **关键点：** 紧集 $K \subset \text{Open Set } \Omega$ 意味着 $K$ 必须和 $\Omega$ 的边界保持一个正距离 $\delta > 0$。

- **答题卡风格总结：**
    - 1. For any **compact set** $K \subset D(0, 1)$, there exists $r < 1$ such that $|z| \le r$ for all $z \in K$.
    - 2. $\sup_{z \in K} |z^n - 0| = r^n \to 0$ as $n \to \infty$, which proves **uniform convergence** on $K$.
    - 3. Thus, $f_n \to 0$ **locally uniformly** on $D(0, 1)$.
    - 4. The **boundary** $|z|=1$ is not part of the **open set** $D(0, 1)$, and **locally uniform convergence** only depends on subsets **strictly inside** the domain. Therefore, the behavior at $z=1$ is **irrelevant**.

# Q4
#### 1. 题目翻译 (Translation of the Question)

- **Question 4 (Weierstrass $M$ test for locally uniformly convergence) / 问题 4（关于局部一致收敛的魏尔斯特拉斯 $M$ 判别法）**
    - Let $f_k(z)$ be a **series of function** (函数级数), for $k = 1, 2, \dots$, defined on a **domain** (区域) $D$.
    - Suppose that for each point $z_0$ in $D$, there is a **neighborhood** (邻域) $U$ of $z_0$ and a **sequence of number** (数列) $(M_k)_{k=1}^{\infty}$, such that $|f_k(z)| \le M_k$ for all $z \in U \cap D$, and $\sum_{k=1}^{\infty} M_k$ **converges** (收敛).
    - **Apply Weierstrass $M$-test to prove that $f_k(z)$ converge locally uniformly.**
    - **中文直译：** 设 $\sum f_k(z)$ 是定义在区域 $D$ 上的函数级数。假设对于 $D$ 中的每一个点 $z_0$，都存在 $z_0$ 的一个邻域 $U$ 以及一个数列 $M_k$，使得在 $U \cap D$ 里的所有点上都有 $|f_k(z)| \le M_k$，并且常数级数 $\sum M_k$ 是收敛的。请利用魏尔斯特拉斯 $M$ 判别法证明：该级数 $\sum f_k(z)$ 在 $D$ 上是**局部一致收敛** (locally uniformly convergent) 的。

---

#### 2. 背景条件与基本概念解释 (Background & Concepts)

- **函数级数 (Series of Functions)：**
    - **工科直觉：** 就是把一串函数加起来，看它们的总和 $S(z) = \sum_{k=1}^{\infty} f_k(z)$ 是否存在，以及收敛得“快不快”。

- **魏尔斯特拉斯 $M$ 判别法 (Weierstrass $M$-test)：**
    - **核心思想：** 找一个“天花板”。
    - 如果你能给每一个函数 $f_k(z)$ 都找一个常数“天花板” $M_k$（即 $|f_k(z)| \le M_k$），且这些天花板的总和 $\sum M_k$ 是有限的（收敛），那么原函数级数就一定收敛，而且是**一致收敛** (uniformly convergent) 的。
    - **工科直觉：** 如果误差的“最大可能值”加起来都是有限的，那么整体误差一定会消失。

- **邻域 (Neighborhood) $U$：**
    - 在复平面上，通常指以 $z_0$ 为中心的一个很小的开圆盘。

- **局部一致收敛 (Locally Uniform Convergence)：**
    - **定义：** 如果级数在定义域 $D$ 内的每一个 **compact subset** (紧子集，即闭且有界的集合) 上都一致收敛，就叫局部一致收敛。
    - **等价定义（本题使用）：** 如果对于 $D$ 中的每一个点，都存在一个邻域，使得级数在该邻域上一致收敛，那么它就是局部一致收敛的。

---

#### 3. 问题解答思路与逻辑链条 (Logical Chain)

我们要证明“局部一致收敛”，根据定义，只需要证明“在每一个点附近都一致收敛”。

- **第一步：利用已知条件锁定局部范围**
    - **因为** 题目给出：对于 $D$ 中的任意点 $z_0$，存在一个邻域 $U$。
    - **因为** 在这个邻域 $U$ 内，满足 $|f_k(z)| \le M_k$ 且 $\sum M_k$ 收敛。
    - **所以** 在这个局部区域 $U \cap D$ 上，满足了 **Weierstrass $M$-test** ([[魏尔斯特拉斯M判别法]]) 的所有前提条件。

- **第二步：应用 $M$ 判别法得出局部结论**
    - **因为** 满足了 $M$ 判别法，
    - **所以** 级数 $\sum f_k(z)$ 在该邻域 $U \cap D$ 上是 **uniformly convergent** (一致收敛) 的。
    - *（定理边界：$M$ 判别法直接推导出一致收敛）*

- **第三步：从“局部一致”推导到“局部一致收敛”的定义**
    - **因为** 我们证明了对于 $D$ 中的**每一个点** $z_0$，都存在一个邻域 $U$ 使得级数在该处一致收敛。
    - **根据** **Locally Uniform Convergence** (局部一致收敛) 的定义：如果在每一点附近都一致收敛，则该级数在整个区域 $D$ 上局部一致收敛。
    - **所以** $\sum f_k(z)$ 在 $D$ 上局部一致收敛。

- **第四步：连接到紧集（进阶逻辑，供理解）**
    - **如果** 我们想证明它在任意 **compact set** (紧集) $K \subset D$ 上一致收敛：
    - **因为** $K$ 是紧的，我们可以用无数个上述的邻域 $U$ 去覆盖 $K$。
    - **根据** **Heine-Borel Theorem** (有限覆盖定理)，我们只需要从中选出**有限个**邻域就能盖住 $K$。
    - **因为** 级数在有限个邻域的每一个上都一致收敛，
    - **所以** 它在它们的并集（即 $K$）上也必然是一致收敛的。

---

#### 4. 总结与规则应用 (Summary & Rules)

- **什么时候可以使用 Weierstrass $M$-test？**
    - 当你需要证明一个级数“一致收敛”时。
    - 只要你能找到一个不依赖于 $z$ 的常数数列 $M_k$ 把函数“压住”，且 $\sum M_k$ 算出来是有限的，就可以直接用。

- **答题卡风格总结：**
    - 1. For any $z_0 \in D$, there exists a **neighborhood** $U$ such that $|f_k(z)| \le M_k$ for all $z \in U \cap D$.
    - 2. Since $\sum M_k$ **converges**, by the **Weierstrass $M$-test**, the series $\sum f_k(z)$ **converges uniformly** on $U \cap D$.
    - 3. By definition, if a series converges uniformly in a neighborhood of each point, it **converges locally uniformly** on $D$.
    - 4. Therefore, $\sum f_k(z)$ converges locally uniformly on $D$.

- **关键单词识别：**
    - **Series of function**: 函数级数（一堆函数相加）
    - **Neighborhood**: 邻域（点周围的一小块地）
    - **Converges**: 收敛（有极限，不爆炸）
    - **Locally uniformly**: 局部一致地（在每一小块上都收敛得一样快）

# Q5
#### 1. 题目翻译 (Translation of the Question)

- **Question 5 (Morera theorem for triangles) / 问题 5（关于三角形的莫雷拉定理）**
    - 设 $\Omega \subset \mathbb{C}$ 是一个 **open set** (开集)，且 $f : \Omega \to \mathbb{C}$ 是 **continuous** (连续的)。
    - **(a) 假设：** 对于每一个满足其闭包 $\overline{T} \subset \Omega$ 的 **triangle** (三角形) $T$，都有：
        $$\int_{\partial T} f(z) dz = 0$$
        **证明：** $f$ 在 $\Omega$ 上是 **holomorphic** (全纯的)。
        *(提示：使用关于三角形的柯西-古萨定理。)*
    - **(b) (选做题)：** 如果我们将假设改为“对于 $\Omega$ 内的所有 **rectangle** (矩形) $R$，都有 $\int_{\partial R} f(z) dz = 0$”，**Morera theorem** (莫雷拉定理) 是否仍然成立？

---

#### 2. 背景条件与基本概念解释 (Background & Concepts)

- **全纯函数 (Holomorphic Function)：**
    - 指在区域内处处复可导的函数。
    - **工科直觉：** 全纯函数是复分析里的“贵族”，性质极好。一旦一个函数是全纯的，它就无限次可导，且可以展开成幂级数。

- **莫雷拉定理 (Morera's Theorem)：**
    - 这是 **Cauchy's Theorem** (柯西定理) 的**逆定理**。
    - **柯西定理说：** 如果函数全纯，那么它在闭合路径上的积分为 0。
    - **莫雷拉定理说：** 如果一个连续函数在闭合路径上的积分总是 0，那么它一定是全纯的。
    - **本题意义：** 莫雷拉定理告诉我们，不需要检查所有奇奇怪怪的闭合曲线，只要三角形（或矩形）这种简单图形的积分为 0，就足够判定全纯性了。

- **原函数 (Primitive / Antiderivative)：**
    - 如果存在一个函数 $F$，使得 $F'(z) = f(z)$，那么 $F$ 就是 $f$ 的原函数。
    - **关键性质：** 在复分析中，如果一个函数 $f$ 在某个小区域内有原函数 $F$，那么 $f$ 一定是全纯的。

---

#### 3. 问题 (a) 的解答思路与逻辑链条 (Solution for Part a)

证明 $f$ 是全纯的，最稳妥的办法是证明它在每一点附近都有一个“原函数”。

- **第一步：局部化处理**
    - **因为** 我们要证明 $f$ 在 $\Omega$ 上全纯，只需要证明它在 $\Omega$ 内任意一点 $z_0$ 的某个 **neighborhood** (邻域) 内全纯即可。
    - 我们取一个包含在 $\Omega$ 内的小圆盘 $D$。

- **第二步：构造候选原函数**
    - 在圆盘 $D$ 内固定一个基准点 $z_0$。
    - 对于圆盘内的任意一点 $z$，定义函数 $F(z) = \int_{z_0}^z f(\zeta) d\zeta$。
    - **注意：** 这里的积分路径是从 $z_0$ 到 $z$ 的一条直线段。

- **第三步：利用“三角形积分为 0”证明路径无关性**
    - **因为** 题目假设任何三角形 $T$ 的边界积分 $\int_{\partial T} f(z) dz = 0$，
    - **所以** 考虑由 $z_0, z, z+\Delta z$ 三点构成的三角形。从 $z_0$ 直接走到 $z+\Delta z$ 的积分，等于先从 $z_0$ 走到 $z$ 再从 $z$ 走到 $z+\Delta z$ 的积分。
    - 这意味着 $F(z)$ 的定义是 **path-independent** (路径无关) 的。

- **第四步：证明 $F$ 是可导的**
    - 计算导数定义式：$\frac{F(z+\Delta z) - F(z)}{\Delta z} = \frac{1}{\Delta z} \int_{z}^{z+\Delta z} f(\zeta) d\zeta$。
    - **因为** $f$ 是 **continuous** (连续的)，当 $\Delta z$ 很小时，$f(\zeta)$ 几乎等于 $f(z)$。
    - **所以** 上述积分趋近于 $f(z)$。
    - **结论：** $F'(z) = f(z)$。

- **第五步：利用全纯函数的性质得出结论**
    - **因为** $F$ 在圆盘内可导，
    - **所以** $F$ 在圆盘内是 **holomorphic** (全纯的)。
    - **根据定理：** 全纯函数的导数依然是全纯的。
    - **因为** $f$ 是 $F$ 的导数，
    - **所以** $f$ 在圆盘内是全纯的。
    - **最终结论：** 由于 $z_0$ 是任意取的，$f$ 在整个 $\Omega$ 上全纯。

---

#### 4. 问题 (b) 的解答思路与逻辑链条 (Solution for Part b)

- **结论：** 是的，结论仍然成立 (Yes, it still holds)。

- **逻辑链条：**
    - **第一步：核心逻辑复用**
        - 证明全纯性的核心在于能否构造出 **primitive** (原函数) $F$。
    - **第二步：矩形的作用**
        - **因为** 任何一个三角形都可以被分割成若干个小矩形（或者通过矩形路径来逼近），
        - **或者更简单地：** 我们可以定义 $F(z)$ 的积分路径为“先水平走，再垂直走”（阶梯状路径）。
    - **第三步：利用矩形积分为 0**
        - **因为** 矩形边界积分 $\int_{\partial R} f(z) dz = 0$，
        - **所以** 这种“阶梯状路径”的积分也是路径无关的。
    - **第四步：得出结论**
        - 只要路径无关，我们就能定义出 $F(z)$ 使得 $F'(z) = f(z)$。
        - 剩下的推导过程与 (a) 完全一致。
    - **工科理解：** 无论是三角形还是矩形，它们的作用都是为了保证你在一个小区域内绕一圈回来积分是 0，从而保证你能定义出一个稳定的“势函数”（即原函数）。

---

#### 5. 总结与规则应用 (Summary & Rules)

- **什么时候使用 Morera's Theorem？**
    - 当你不知道函数是否可导，但你知道它在某些闭合路径（三角形、矩形、圆）上的积分为 0 时。
    - 它是判定全纯性的“积分判别法”。

- **答题卡风格总结：**
    - 1. For any disk $D \subset \Omega$, define $F(z) = \int_{z_0}^z f(\zeta) d\zeta$.
    - 2. The assumption $\int_{\partial T} f = 0$ implies that the integral is **path-independent** in $D$.
    - 3. Since $f$ is **continuous**, we can show $F'(z) = f(z)$ using the **Fundamental Theorem of Calculus**.
    - 4. $F$ is **holomorphic** $\implies$ its derivative $f$ is also **holomorphic**.
    - 5. For part (b), the same logic applies as a **primitive** can be constructed using **rectangular paths**.

- **关键单词识别：**
    - **Triangle / Rectangle**: 三角形 / 矩形
    - **Continuous**: 连续
    - **Holomorphic**: 全纯
    - **Primitive**: 原函数
    - **Path-independent**: 路径无关

# Q6
#### 1. 题目翻译 (Translation of the Question)

- **原题内容：**
    - Let $f(z)$ be **holomorphic** (全纯的) in a **neighborhood** (邻域) of $z_0$, and suppose that the **power series expansion** (幂级数展开) of $f(z)$ at $z_0$ is
        $$f(z) = \sum_{k=n}^{\infty} a_k(z - z_0)^k$$
        with $a_n \neq 0$.
    - **Show that** (证明) there exists a **holomorphic function** (全纯函数) $h(z)$ in a neighborhood of $z_0$ such that
        $$f(z) = (h(z))^n$$

- **中文直译：**
    - 假设 $f(z)$ 在点 $z_0$ 的邻域内是全纯的，并且 $f(z)$ 在 $z_0$ 处的幂级数展开式是从第 $n$ 项开始的（即前 $n-1$ 阶导数在 $z_0$ 处都为 0），且第 $n$ 项系数 $a_n$ 不为 0。
    - 证明：在 $z_0$ 的某个邻域内，存在一个全纯函数 $h(z)$，使得 $f(z)$ 可以写成 $h(z)$ 的 $n$ 次方的形式。

---

#### 2. 背景条件与基本概念解释 (Background & Concepts)

- **$n$ 阶零点 (Zero of order $n$)：**
    - **定义：** 如果一个全纯函数在 $z_0$ 处的幂级数是从 $(z-z_0)^n$ 开始的，我们就说 $z_0$ 是 $f$ 的一个 $n$ 阶零点。
    - **工科直觉：** 这意味着 $f(z)$ 在 $z_0$ 附近的行为非常像 $a_n(z-z_0)^n$。它不仅在 $z_0$ 等于 0，而且它“消失”得很快。

- **全纯函数的 $n$ 次方根 (n-th root of a holomorphic function)：**
    - **核心定理：** 如果一个全纯函数 $g(z)$ 在某一点 $z_0$ 满足 $g(z_0) \neq 0$，那么在 $z_0$ 的一个小邻域内，我们可以定义它的 $n$ 次方根函数 $g(z)^{1/n}$，且这个根函数依然是全纯的。
    - **为什么？** 因为在复数域里，只要避开 0 点，开方运算（取对数的分支）就是平滑且可导的。

- **幂级数的提取 (Factoring Power Series)：**
    - 我们可以像提取公因式一样，从级数里提取出 $(z-z_0)^n$。

---

#### 3. 问题解答思路与逻辑链条 (Logical Chain)

我们要找到一个 $h(z)$ 使得 $h^n = f$。既然 $f$ 里面已经含有了 $(z-z_0)^n$，那么 $h$ 里面理应含有一个 $(z-z_0)$。

- **第一步：提取公因式，构造辅助函数 $g(z)$**
    - **因为** $f(z) = a_n(z-z_0)^n + a_{n+1}(z-z_0)^{n+1} + \dots$
    - **所以** 我们可以写成 $f(z) = (z-z_0)^n \cdot [a_n + a_{n+1}(z-z_0) + a_{n+2}(z-z_0)^2 + \dots]$
    - 令括号里的部分为 $g(z)$，即 $g(z) = \sum_{k=n}^{\infty} a_k(z-z_0)^{k-n}$。

- **第二步：分析 $g(z)$ 的性质**
    - **因为** $g(z)$ 本身也是一个 **power series** (幂级数)，
    - **所以** $g(z)$ 在 $z_0$ 的邻域内是 **holomorphic** (全纯的)。
    - **因为** 题目给出 $a_n \neq 0$，而 $g(z_0) = a_n + 0 + 0 \dots = a_n$，
    - **所以** $g(z_0) \neq 0$。

- **第三步：给 $g(z)$ 开 $n$ 次方**
    - **因为** $g(z)$ 是全纯的且 $g(z_0) \neq 0$，
    - **根据** **Existence of holomorphic n-th root** (全纯 $n$ 次根的存在性定理)，
    - **所以** 在 $z_0$ 的某个邻域内，存在一个全纯函数，我们记作 $\phi(z)$，使得 $(\phi(z))^n = g(z)$。
    - *（注：$\phi(z)$ 其实就是 $g(z)^{1/n}$ 的一个分支）*

- **第四步：构造目标函数 $h(z)$**
    - 令 $h(z) = (z-z_0) \cdot \phi(z)$。
    - **因为** $(z-z_0)$ 是全纯的，$\phi(z)$ 也是全纯的，
    - **所以** 它们的乘积 $h(z)$ 在 $z_0$ 的邻域内也是 **holomorphic** (全纯的)。

- **第五步：验证结果**
    - 计算 $(h(z))^n$：
        - $(h(z))^n = [(z-z_0) \cdot \phi(z)]^n$
        - $= (z-z_0)^n \cdot (\phi(z))^n$
        - $= (z-z_0)^n \cdot g(z)$
    - **因为** $(z-z_0)^n \cdot g(z)$ 正好就是我们第一步拆解出来的 $f(z)$，
    - **所以** $f(z) = (h(z))^n$ 成立。

---

#### 4. 总结与规则应用 (Summary & Rules)

- **什么时候可以使用这个逻辑？**
    - 当题目要求你把一个函数写成“某个东西的 $n$ 次方”时，通常是因为这个函数在某点有一个 $n$ 阶零点。
    - **核心套路：** 
        1. 强行提取出 $(z-z_0)^n$。
        2. 证明剩下的部分 $g(z)$ 在该点不为 0。
        3. 声明不为 0 的全纯函数可以开 $n$ 次方且保持全纯。

- **答题卡风格总结：**
    - 1. Write $f(z) = (z-z_0)^n g(z)$, where $g(z) = \sum_{k=n}^{\infty} a_k(z-z_0)^{k-n}$.
    - 2. $g(z)$ is **holomorphic** near $z_0$ and $g(z_0) = a_n \neq 0$.
    - 3. Since $g(z_0) \neq 0$, there exists a **holomorphic branch** of $g(z)^{1/n}$ in a neighborhood of $z_0$. Let $\phi(z) = g(z)^{1/n}$.
    - 4. Define $h(z) = (z-z_0)\phi(z)$, which is **holomorphic** as a product of holomorphic functions.
    - 5. Then $h(z)^n = (z-z_0)^n g(z) = f(z)$.

- **关键单词识别：**
    - **Power series expansion**: 幂级数展开
    - **Neighborhood**: 邻域
    - **Holomorphic branch**: 全纯分支（指在开方或取对数时选定的一支，保证连续可导）
    - **n-th root**: n 次方根