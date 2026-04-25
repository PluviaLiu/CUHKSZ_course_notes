- [x] 完成MAT3253-HW12 ✅ 2026-04-25
# Q1

#### 1. 题目翻译 (Translation of the Problem)

- **原题：** Find a representation for the function $f(z) = \frac{1}{1+z} = \frac{1}{z} \cdot \frac{1}{1+(1/z)}$ in negative powers of $z$ that is valid when $1 < |z| < \infty$.
- **翻译：** 请找到函数 $f(z) = \frac{1}{1+z}$ 的一种表示形式（通常指级数展开），要求该形式包含 $z$ 的**负幂次 (negative powers)**，并且该表示在 **$1 < |z| < \infty$** 这个范围内是**有效的 (valid)**。
- **提示部分翻译：** 题目已经贴心地给出了一个变形提示：$f(z) = \frac{1}{z} \cdot \frac{1}{1+(1/z)}$。

#### 2. 背景知识与基本概念 (Background & Basic Concepts)

在做这道题之前，你必须死记硬背住一个“工具”，它是所有这类题目的亲爹：

- **等比级数公式 (Geometric Series Formula):**
    - 在数学中，如果你看到 $\frac{1}{1-w}$ 这种形式，你可以把它写成：
        - $\frac{1}{1-w} = 1 + w + w^2 + w^3 + \dots = \sum_{n=0}^{\infty} w^n$
    - **极其重要的边界条件 (Convergence Condition):** 这个公式**只有**在 $|w| < 1$ 的时候才成立。如果 $|w| \ge 1$，这个加法就会变成无穷大，公式失效。
    - **变体：** 如果分母是加号，即 $\frac{1}{1+w}$，我们可以看作 $\frac{1}{1-(-w)}$，代入公式得：
        - $\frac{1}{1+w} = 1 - w + w^2 - w^3 + \dots = \sum_{n=0}^{\infty} (-1)^n w^n$
        - 同样，要求 $|-w| < 1$，即 $|w| < 1$。
[[级数公式]]

- [[劳伦级数 (Laurent Series)]]
    - 当一个函数在某个点（比如 $z=0$）不解析（可以理解为分母为0，函数“爆了”）时，我们不能只用正幂次（像 $z, z^2$）来表示它，还需要用到负幂次（像 $z^{-1}, z^{-2}$）。这种既有正幂次又有负幂次的级数就叫**劳伦级数**。

- **收敛区域 (Region of Convergence, ROC):**
    - 题目给出的 $1 < |z| < \infty$ 就是收敛区域。它告诉我们，我们写出来的级数必须在这个范围内“听话”（不爆炸）。

#### 3. 解题思路与逻辑链条 (Logic Chain & Solution)

我们要解决的核心矛盾是：标准的等比级数公式要求变量的绝对值**小于1**，但题目给我们的条件是 $|z|$ **大于1**。

- **逻辑步骤 1：分析已知条件与公式的冲突**
    - 已知条件：$|z| > 1$。
    - 公式要求：变量必须 $< 1$。
    - 推导：既然 $|z| > 1$，那么它的倒数 $\frac{1}{|z|}$（即 $|\frac{1}{z}|$）就一定满足 $|\frac{1}{z}| < 1$。
    - **结论：** 我们不能直接对 $z$ 用公式，我们要想办法对 $\frac{1}{z}$ 用公式。

- **逻辑步骤 2：代数变形 (Algebraic Manipulation)**
    - 目标：把 $f(z) = \frac{1}{1+z}$ 强行变成含有 $\frac{1}{z}$ 的形式。
    - 操作：从分母中提取出 $z$。
    - 推导过程：
        - $f(z) = \frac{1}{z + 1}$
        - $f(z) = \frac{1}{z(1 + \frac{1}{z})}$ （这一步就是把 $z$ 提出来，括号里就出现了我们想要的 $\frac{1}{z}$）
        - $f(z) = \frac{1}{z} \cdot \frac{1}{1 + \frac{1}{z}}$

- **逻辑步骤 3：应用等比级数公式 (Apply Geometric Series)**
    - 条件：令 $w = \frac{1}{z}$。因为题目说 $|z| > 1$，所以 $|w| = |\frac{1}{z}| < 1$。
    - 定理：因为 $|w| < 1$，所以满足**等比级数 (Geometric Series)** 的收敛条件。
    - 代入：
        - $\frac{1}{1 + w} = \sum_{n=0}^{\infty} (-1)^n w^n$
        - 将 $w = \frac{1}{z}$ 代回：
        - $\frac{1}{1 + \frac{1}{z}} = \sum_{n=0}^{\infty} (-1)^n (\frac{1}{z})^n = \sum_{n=0}^{\infty} \frac{(-1)^n}{z^n}$

- **逻辑步骤 4：整合最终结果 (Final Assembly)**
    - 逻辑：不要忘了前面还有一个提出来的 $\frac{1}{z}$。
    - 推导：
        - $f(z) = \frac{1}{z} \cdot \left( \sum_{n=0}^{\infty} \frac{(-1)^n}{z^n} \right)$
        - 将 $\frac{1}{z}$ 乘进求和符号里面：
        - $f(z) = \sum_{n=0}^{\infty} \frac{(-1)^n}{z^{n+1}}$
    - 展开前几项看看：
        - 当 $n=0$ 时：$\frac{(-1)^0}{z^1} = \frac{1}{z}$
        - 当 $n=1$ 时：$\frac{(-1)^1}{z^2} = -\frac{1}{z^2}$
        - 当 $n=2$ 时：$\frac{(-1)^2}{z^3} = \frac{1}{z^3}$
        - 所以 $f(z) = \frac{1}{z} - \frac{1}{z^2} + \frac{1}{z^3} - \frac{1}{z^4} + \dots$

- **逻辑步骤 5：验证目标 (Verification)**
    - 目标 1：是否包含 **negative powers of $z$**？
        - 是的，$\frac{1}{z} = z^{-1}, \frac{1}{z^2} = z^{-2}$，全是负幂次。
    - 目标 2：是否在 **$1 < |z| < \infty$** 有效？
        - 是的，因为我们在推导过程中使用了 $|\frac{1}{z}| < 1$ 这个条件，它等价于 $|z| > 1$。

#### 4. 总结与考试套路 (Summary & Exam Tips)

以后遇到这种“在某个区域展开”的题目，你的工科思维逻辑应该是：

- **第一步：看区域。**
    - 如果区域是 $|z| < R$，说明你要凑出形如 $(\frac{z}{R})$ 的项，因为这样它才小于 1。
    - 如果区域是 $|z| > R$，说明你要凑出形如 $(\frac{R}{z})$ 的项，因为这样它才小于 1。
- **第二步：强行提取。**
    - 想要凑出 $\frac{R}{z}$，就从分母里强行把 $z$ 提出来。
- **第三步：套公式。**
    - 使用 $\frac{1}{1+w} = \sum (-1)^n w^n$ 或者 $\frac{1}{1-w} = \sum w^n$。
- **第四步：整理。**
    - 把括号外的项乘进去，写成标准的 $\sum$ 形式。

**关键单词回顾：**
- **Representation:** 表示/展开式
- **Negative powers:** 负幂次（即 $z$ 在分母上）
- **Valid:** 有效的/收敛的
- **Geometric Series:** 等比级数/几何级数
- **Convergence:** 收敛（级数不爆炸，能加出一个具体的数）


# Q2
你好！这道题目是复分析中关于级数展开的经典练习。它要求我们针对同一个函数，在不同的“领地”上写出它的级数表达式。

我会严格按照你的要求，用最基础的逻辑为你拆解。

#### 1. 题目翻译与任务拆解 (Translation & Task Breakdown)

- **题目翻译：**
    - **原题：** Give two [[劳伦级数展开 (Laurent series expansions)]] in [[z 的幂次 (powers of z)]] for the function $f(z) = \frac{1}{z^2(1-z)}$, and specify the [[区域 (regions)]] in which those expansions are [[有效的 (valid)]].
    - **中文直译：** 给出函数 $f(z) = \frac{1}{z^2(1-z)}$ 关于 $z$ 的幂次的两个劳伦级数展开式，并指明这些展开式在哪些区域内是有效的。

- **题目给出的信息点：**
    - **信息点 1：** 目标函数是 $f(z) = \frac{1}{z^2(1-z)}$。
    - **信息点 2：** 展开中心是 $z=0$（因为题目要求“in powers of $z$”，即 $z-0$ 的幂次）。
    - **信息点 3：** 函数有两个 [[奇点 (Singularities)]]：一个是 $z=0$（分母里的 $z^2$ 导致的），另一个是 $z=1$（分母里的 $1-z$ 导致的）。

- **我们要做的任务：**
    - ① 确定以 $z=0$ 为中心的两个不同的 [[收敛区域 (Regions of convergence)]]。
    - ② 在这两个区域内分别把函数写成 $\sum$（求和符号）的形式。

#### 2. 背景条件与基本概念 (Background & Concepts)

- **[[劳伦级数 (Laurent series)]]：**
    - 当一个函数在某个点（比如 $z=0$）“爆炸”了（不解析），我们就不能用普通的泰勒级数。劳伦级数允许出现 $z$ 的负数次方（比如 $1/z, 1/z^2$），用来描述这种“爆炸”行为。

- **[[奇点 (Singularities)]]：**
    - 简单来说就是让分母为 0 的点。本题中，分母 $z^2(1-z)=0$ 得到 $z=0$ 和 $z=1$。这两个点就是函数的“禁区”。

- **[[收敛区域 (Region of convergence)]]：**
    - 级数展开式只能在不包含奇点的“安全区”内有效。以 $z=0$ 为中心，奇点 $z=1$ 到中心的距离是 1。
    - 这就把平面分成了两块：
        - 区域 1：$0 < |z| < 1$（在禁区 $z=1$ 的内部）。
        - 区域 2：$|z| > 1$（在禁区 $z=1$ 的外部）。

- **[[等比级数公式 (Geometric series formula)]]：**
    - 这是做题的唯一核心工具：$\frac{1}{1-w} = 1 + w + w^2 + \dots = \sum_{n=0}^{\infty} w^n$。
    - **使用前提：** 必须满足 $|w| < 1$。如果 $|w| > 1$，这个公式就失效了。

#### 3. 解答思路与逻辑链条 (Logic Chain & Solution)

我们将函数拆解为 $f(z) = \frac{1}{z^2} \cdot \frac{1}{1-z}$。前面的 $\frac{1}{z^2}$ 已经是 $z$ 的幂次了，不需要动；我们只需要处理 $\frac{1}{1-z}$。

##### 3.1 第一种展开：针对区域 $0 < |z| < 1$

- **逻辑链条：**
    - ● 目标区域是 $0 < |z| < 1$ → 意味着我们手里的条件是 $|z| < 1$。
    - ● 观察函数中的项 $\frac{1}{1-z}$ → 这里的 $z$ 扮演了公式 $\frac{1}{1-w}$ 中 $w$ 的角色。
    - ● 因为条件 $|z| < 1$ 成立 → 符合 [[等比级数 (Geometric series)]] 的收敛要求。
    - ● 应用公式 → $\frac{1}{1-z} = \sum_{n=0}^{\infty} z^n = 1 + z + z^2 + z^3 + \dots$
    - ● 整合整体函数 → $f(z) = \frac{1}{z^2} \cdot (1 + z + z^2 + z^3 + \dots)$
    - ● 分配律展开 → $f(z) = \frac{1}{z^2} + \frac{1}{z} + 1 + z + z^2 + \dots$
    - ● 写成标准求和形式 → $f(z) = \sum_{n=0}^{\infty} z^{n-2}$。

- **考试答题风格：**
    - For the region $0 < |z| < 1$, the function can be written as $f(z) = \frac{1}{z^2} \cdot \frac{1}{1-z}$.
    - Since $|z| < 1$, we use the [[等比级数 (Geometric series)]] expansion:
        - $\frac{1}{1-z} = \sum_{n=0}^{\infty} z^n$
    - Thus, $f(z) = \frac{1}{z^2} \sum_{n=0}^{\infty} z^n = \sum_{n=0}^{\infty} z^{n-2}$.
    - This is the [[劳伦级数 (Laurent series)]] valid for $0 < |z| < 1$.

##### 3.2 第二种展开：针对区域 $1 < |z| < \infty$

- **逻辑链条：**
    - ● 目标区域是 $|z| > 1$ → 此时 $|z| < 1$ 不成立，不能直接对 $z$ 用公式。
    - ● 寻找小于 1 的项 → 因为 $|z| > 1$，所以它的倒数满足 $|\frac{1}{z}| < 1$。
    - ● 强行变形函数 → 我们要把 $\frac{1}{1-z}$ 变成含有 $\frac{1}{z}$ 的形式。
        - $\frac{1}{1-z} = \frac{1}{-z(1 - \frac{1}{z})} = -\frac{1}{z} \cdot \frac{1}{1 - \frac{1}{z}}$
    - ● 令 $w = \frac{1}{z}$ → 因为 $|w| < 1$，现在可以对 $w$ 使用 [[等比级数 (Geometric series)]] 公式了。
    - ● 应用公式 → $\frac{1}{1 - \frac{1}{z}} = \sum_{n=0}^{\infty} (\frac{1}{z})^n = 1 + \frac{1}{z} + \frac{1}{z^2} + \dots$
    - ● 整合整体函数 → $f(z) = \frac{1}{z^2} \cdot \left( -\frac{1}{z} \right) \cdot (1 + \frac{1}{z} + \frac{1}{z^2} + \dots)$
    - ● 整理系数与幂次 → $f(z) = -\frac{1}{z^3} - \frac{1}{z^4} - \frac{1}{z^5} - \dots$
    - ● 写成标准求和形式 → $f(z) = -\sum_{n=0}^{\infty} \frac{1}{z^{n+3}}$ 或 $-\sum_{n=0}^{\infty} z^{-n-3}$。

- **考试答题风格：**
    - For the region $|z| > 1$, we have $|\frac{1}{z}| < 1$.
    - Rewrite the function:
        - $f(z) = \frac{1}{z^2} \cdot \frac{1}{1-z} = \frac{1}{z^2} \cdot \frac{-1}{z(1 - 1/z)} = -\frac{1}{z^3} \cdot \frac{1}{1 - 1/z}$
    - Using the [[等比级数 (Geometric series)]] formula for $|1/z| < 1$:
        - $f(z) = -\frac{1}{z^3} \sum_{n=0}^{\infty} \left( \frac{1}{z} \right)^n = -\sum_{n=0}^{\infty} z^{-n-3}$
    - This expansion is [[有效的 (valid)]] for $1 < |z| < \infty$.

#### 4. 总结与规则 (Summary & Rules)

- **规则 1：** 看到“in powers of $z$”，中心就是 $0$。
- **规则 2：** 找到所有奇点到中心的距离。本题奇点是 $0$ 和 $1$，距离分别是 $0$ 和 $1$。这决定了边界。
- **规则 3：** 
    - 在边界**内**（$|z| < 1$），直接凑出 $\frac{1}{1-z}$。
    - 在边界**外**（$|z| > 1$），必须提一个 $z$ 出来，凑出 $\frac{1}{1 - (1/z)}$。
- **规则 4：** 永远记住公式 $\frac{1}{1-w}$ 要求 $|w| < 1$。这是所有变形的动力来源。

**关键单词回顾：**
- [[劳伦级数 (Laurent series)]]
- [[奇点 (Singularities)]]
- [[收敛区域 (Region of convergence)]]
- [[等比级数 (Geometric series)]]
- [[有效的 (valid)]]
- [[z 的幂次 (powers of z)]]


# Q3
这道题目非常经典，它把[[劳伦级数 (Laurent series)]]和[[欧拉公式 (Euler's formula)]]结合在了一起，用来推导三角函数的求和公式。

#### 1. 题目翻译与任务拆解 (Translation & Task Breakdown)

- **题目翻译：**
    - **(a) 部分：** 设 $a$ 为一个实数，满足 $-1 < a < 1$。请推导出函数 $\frac{a}{z-a}$ 在区域 $|a| < |z| < \infty$ 内的[[劳伦级数表示 (Laurent series representation)]]：
        $$\frac{a}{z-a} = \sum_{n=1}^{\infty} \frac{a^n}{z^n}$$
    - **(b) 部分：** 在 (a) 部分得到的等式中令 $z = e^{i\theta}$，然后通过[[令实部相等 (equate real parts)]]和[[令虚部相等 (equate imaginary parts)]]，推导出以下两个[[求和公式 (summation formulas)]]：
        $$\sum_{n=1}^{\infty} a^n \cos n\theta = \frac{a \cos \theta - a^2}{1 - 2a \cos \theta + a^2} \quad \text{和} \quad \sum_{n=1}^{\infty} a^n \sin n\theta = \frac{a \sin \theta}{1 - 2a \cos \theta + a^2}$$
        其中 $-1 < a < 1$。

- **任务拆解：**
    - **任务 1：** 做代数变形，把函数凑成[[等比级数 (Geometric series)]]的形式，证明 (a) 的等式。
    - **任务 2：** 把复数 $z = e^{i\theta}$ 代入等式两边。
    - **任务 3：** 左边利用[[欧拉公式 (Euler's formula)]]拆成实部和虚部。
    - **任务 4：** 右边利用[[共轭复数 (Complex conjugate)]]进行分母实数化，拆成实部和虚部。
    - **任务 5：** 左右对号入座，得出结论。

#### 2. 背景条件与基本概念 (Background & Concepts)

- **[[劳伦级数 (Laurent series)]]：**
    - 就像我们之前讨论的，当我们在奇点外面（这里是 $|z| > |a|$）展开时，会出现 $z$ 的负幂次。
- **[[等比级数公式 (Geometric series formula)]]：**
    - $\frac{1}{1-w} = \sum_{n=0}^{\infty} w^n$，前提是 $|w| < 1$。
- **[[欧拉公式 (Euler's formula)]]：**
    - $e^{i\phi} = \cos \phi + i \sin \phi$。
    - 它的变体：$e^{-in\theta} = \cos(n\theta) - i \sin(n\theta)$。
- **[[共轭复数 (Complex conjugate)]]：**
    - 如果分母有 $i$，比如 $A+Bi$，我们要乘以它的共轭 $A-Bi$ 来把分母变成实数 $(A^2+B^2)$。这叫[[分母实数化 (Rationalizing the denominator)]]。

#### 3. (a) 部分解答思路与逻辑链条 (Logic Chain for Part a)

- **逻辑链条：**
    - ● 目标区域是 $|z| > |a|$ → 意味着 $|\frac{a}{z}| < 1$。
    - ● 变形函数 → 为了使用公式，必须凑出 $\frac{a}{z}$。
        - $\frac{a}{z-a} = \frac{a}{z(1 - \frac{a}{z})} = \frac{a}{z} \cdot \frac{1}{1 - \frac{a}{z}}$
    - ● 应用[[等比级数 (Geometric series)]]公式 → 令 $w = \frac{a}{z}$，因为 $|w| < 1$，所以：
        - $\frac{1}{1 - \frac{a}{z}} = \sum_{n=0}^{\infty} (\frac{a}{z})^n = 1 + \frac{a}{z} + \frac{a^2}{z^2} + \dots$
    - ● 整合 → $\frac{a}{z} \cdot \sum_{n=0}^{\infty} (\frac{a}{z})^n = \sum_{n=0}^{\infty} \frac{a^{n+1}}{z^{n+1}}$。
    - ● 调整下标 → 令 $k = n+1$。当 $n=0$ 时 $k=1$。
    - ● 结论 → $\sum_{k=1}^{\infty} \frac{a^k}{z^k}$。这与题目给出的 $\sum_{n=1}^{\infty} \frac{a^n}{z^n}$ 是一回事。

#### 4. (b) 部分解答思路与逻辑链条 (Logic Chain for Part b)

这一步比较繁琐，我们分左右两边处理。

##### 4.1 处理左边 (Left Hand Side, LHS)

- **逻辑链条：**
    - ● 代入 $z = e^{i\theta}$ → 左边变为 $\sum_{n=1}^{\infty} \frac{a^n}{(e^{i\theta})^n} = \sum_{n=1}^{\infty} a^n e^{-in\theta}$。
    - ● 应用[[欧拉公式 (Euler's formula)]] → $e^{-in\theta} = \cos(n\theta) - i \sin(n\theta)$。
    - ● 展开 → $\sum_{n=1}^{\infty} a^n (\cos n\theta - i \sin n\theta) = \sum a^n \cos n\theta - i \sum a^n \sin n\theta$。
    - ● **结论：** 左边的[[实部 (Real part)]]是 $\sum a^n \cos n\theta$，[[虚部 (Imaginary part)]]是 $-\sum a^n \sin n\theta$。

##### 4.2 处理右边 (Right Hand Side, RHS)

- **逻辑链条：**
    - ● 代入 $z = e^{i\theta}$ → 右边变为 $\frac{a}{e^{i\theta} - a}$。
    - ● 展开分母 → $\frac{a}{(\cos \theta + i \sin \theta) - a} = \frac{a}{(\cos \theta - a) + i \sin \theta}$。
    - ● [[分母实数化 (Rationalizing)]] → 分子分母同乘以分母的[[共轭 (Conjugate)]]：$(\cos \theta - a) - i \sin \theta$。
    - ● 计算分母 → $((\cos \theta - a) + i \sin \theta)((\cos \theta - a) - i \sin \theta) = (\cos \theta - a)^2 + \sin^2 \theta$。
        - 展开：$\cos^2 \theta - 2a \cos \theta + a^2 + \sin^2 \theta$。
        - 利用 $\sin^2 \theta + \cos^2 \theta = 1$ → 分母变为 $1 - 2a \cos \theta + a^2$。
    - ● 计算分子 → $a [(\cos \theta - a) - i \sin \theta] = (a \cos \theta - a^2) - i(a \sin \theta)$。
    - ● 整理右边结果 → $\frac{a \cos \theta - a^2}{1 - 2a \cos \theta + a^2} - i \frac{a \sin \theta}{1 - 2a \cos \theta + a^2}$。

##### 4.3 左右对比 (Equating Parts)

- **逻辑链条：**
    - ● [[令实部相等 (Equate real parts)]]：
        - 左边实部 $\sum a^n \cos n\theta$ = 右边实部 $\frac{a \cos \theta - a^2}{1 - 2a \cos \theta + a^2}$。
    - ● [[令虚部相等 (Equate imaginary parts)]]：
        - 左边虚部 $-\sum a^n \sin n\theta$ = 右边虚部 $-\frac{a \sin \theta}{1 - 2a \cos \theta + a^2}$。
        - 两边去掉负号：$\sum a^n \sin n\theta = \frac{a \sin \theta}{1 - 2a \cos \theta + a^2}$。

#### 5. 总结与考试技巧 (Summary & Tips)

- **技巧 1：** 看到 $\sum a^n \cos n\theta$ 这种形式，第一反应应该是它某个复数级数的[[实部 (Real part)]]。
- **技巧 2：** 复数分母的处理永远是乘以[[共轭 (Conjugate)]]。
- **技巧 3：** 记住 $\sin^2 + \cos^2 = 1$ 是化简分母的常客。
- **边界条件：** 题目给出的 $-1 < a < 1$ 保证了当 $|z|=1$（即 $z=e^{i\theta}$）时，条件 $|z| > |a|$ 依然成立，所以级数是[[收敛的 (convergent)]]。

**关键单词回顾：**
- [[劳伦级数展开 (Laurent series expansion)]]
- [[欧拉公式 (Euler's formula)]]
- [[实部 (Real part)]] / [[虚部 (Imaginary part)]]
- [[共轭复数 (Complex conjugate)]]
- [[分母实数化 (Rationalizing the denominator)]]
- [[等比级数 (Geometric series)]]
# Q4
你好！这道题目是复分析中一个非常著名的应用，它展示了如何利用[[劳伦级数 (Laurent Series)]]来定义数学中极其重要的[[贝塞尔函数 (Bessel Functions)]]。

虽然题目看起来公式很长，但它的核心逻辑其实就是“套公式”和“做替换”。我会为你一步步拆解。

#### 1. 题目翻译与任务拆解 (Translation & Task Breakdown)

- **题目翻译：**
    - **(a) 部分：** 设 $z$ 为任意复数，令 $C$ 为 $w$ 平面上的[[单位圆 (Unit circle)]] $w = e^{i\phi}$ ($-\pi \le \phi \le \pi$)。请使用课本中的[[劳伦系数公式 (Laurent Coefficient Formula)]]（针对以原点为中心的级数），证明：

		$$\exp\left[\frac{z}{2}\left(w - \frac{1}{w}\right)\right] = \sum_{n=-\infty}^{\infty} J_n(z)w^n \quad (0 < |w| < \infty)$$
        其中系数 $J_n(z)$ 的表达式为：
        $$J_n(z) = \frac{1}{2\pi} \int_{-\pi}^{\pi} \exp[-i(n\phi - z \sin \phi)] d\phi \quad (n = 0, \pm 1, \pm 2, \dots)$$
    - **(b) 部分：** 利用关于实变量的复值函数的[[定积分 (Definite integrals)]]的[[奇偶性 (Even and odd properties)]]，证明 (a) 中的系数可以写成：
        $$J_n(z) = \frac{1}{\pi} \int_{0}^{\pi} \cos(n\phi - z \sin \phi) d\phi \quad (n = 0, \pm 1, \pm 2, \dots)$$

- **题目给出的信息点：**
    - **信息点 1：** ==我们研究的函数是 $f(w) = \exp[\frac{z}{2}(w - \frac{1}{w})]$。注意，这里的变量是 $w$，而 $z$ 只是一个常数参数。得到结论方式：in the w plane == w为自变量
    - **信息点 2：** 展开中心是 $w=0$。由于分母有 $w$，所以 $w=0$ 是一个[[奇点 (Singularity)]]。
    - **信息点 3：** 积分路径 $C$ 是一个圆，可以用 $w = e^{i\phi}$ 来参数化。

- **我们要做的任务：**
    - **任务 1：** 写出劳伦级数系数的通用积分公式。
    - **任务 2：** 把 $w = e^{i\phi}$ 代入积分公式，通过代数运算化简出 (a) 的结果。
    - **任务 3：** 利用三角函数的对称性（奇偶性），把 $[-\pi, \pi]$ 的积分变成 $[0, \pi]$ 的积分，并去掉虚数部分。

#### 2. 背景条件与基本概念 (Background & Concepts)

- **[[劳伦级数 (Laurent Series)]]：**
    - 当函数在某个点（如 $w=0$）不解析时，我们将其展开为包含正负幂次的级数 $\sum_{n=-\infty}^{\infty} c_n w^n$。

- **[[劳伦系数公式 (Laurent Coefficient Formula)]]：**
    - 这是本题的灵魂。对于函数 $f(w)$，其第 $n$ 项的系数 $c_n$（本题中叫 $J_n(z)$）计算公式为：
        $$c_n = \frac{1}{2\pi i} \int_C \frac{f(w)}{w^{n+1}} dw$$
    - **工科理解：** 这个公式告诉我们，只要把函数放进去积个分，就能算出每一项前面的系数。

- **[[欧拉公式 (Euler's Formula)]]：**
    - $e^{i\phi} = \cos \phi + i \sin \phi$。
    -   ==派生公式：$\sin \phi = \frac{e^{i\phi} - e^{-i\phi}}{2i}$。这个在化简指数项时非常有用。==

- **[[参数化 (Parameterization)]]：**
    - 在复平面上绕圆圈积分很难算，所以我们把 $w$ 换成角度 $\phi$。
    - 令 $w = e^{i\phi}$，则微分项 $dw = i e^{i\phi} d\phi$。

- [[定积分的奇偶性]]

#### 3. (a) 部分解答思路与逻辑链条 (Logic Chain for Part a)

我们要证明 $J_n(z)$ 的积分形式。

- **逻辑步骤 1：列出系数公式**
    - 根据[[劳伦系数公式 (Laurent Coefficient Formula)]]，系数 $J_n(z)$ 为：
        $$J_n(z) = \frac{1}{2\pi i} \int_C \frac{\exp[\frac{z}{2}(w - \frac{1}{w})]}{w^{n+1}} dw$$

- **逻辑步骤 2：进行变量替换（参数化）**
    - 我们沿着单位圆 $C$ 积分，令 $w = e^{i\phi}$，其中 $\phi$ 从 $-\pi$ 变到 $\pi$。
    - 那么 $dw = i e^{i\phi} d\phi$。
    - 同时也注意到 $\frac{1}{w} = e^{-i\phi}$。

- **逻辑步骤 3：化简被积函数中的指数部分**
    - 观察 $w - \frac{1}{w}$：
        - $w - \frac{1}{w} = e^{i\phi} - e^{-i\phi}$
        - 根据[[欧拉公式 (Euler's Formula)]]的变形，我们知道 $e^{i\phi} - e^{-i\phi} = 2i \sin \phi$。
    - 所以，$\frac{z}{2}(w - \frac{1}{w}) = \frac{z}{2}(2i \sin \phi) = iz \sin \phi$。

- **逻辑步骤 4：代入积分式并化简**
    - 把所有零件装回去：
        $$J_n(z) = \frac{1}{2\pi i} \int_{-\pi}^{\pi} \frac{\exp(iz \sin \phi)}{(e^{i\phi})^{n+1}} \cdot (i e^{i\phi} d\phi)$$
    - 注意到分子分母的 $i$ 可以约掉。
    - 处理 $w$ 的幂次部分：$\frac{e^{i\phi}}{(e^{i\phi})^{n+1}} = \frac{1}{(e^{i\phi})^n} = e^{-in\phi}$。
    - 整合指数：$\exp(iz \sin \phi) \cdot e^{-in\phi} = \exp(iz \sin \phi - in\phi) = \exp[-i(n\phi - z \sin \phi)]$。

- **逻辑步骤 5：得出结论**
    - 整理后得到：$J_n(z) = \frac{1}{2\pi} \int_{-\pi}^{\pi} \exp[-i(n\phi - z \sin \phi)] d\phi$。
    - **结论：** 成功推导出 (a) 的表达式。

#### 4. (b) 部分解答思路与逻辑链条 (Logic Chain for Part b)

我们要把上面的复数指数积分变成实数的余弦积分。
==奇偶性 (Even and Odd Properties)的积分规则通常是针对“实值函数”定义的，为了利用这些规则，我们必须把复数拆开。==

- **逻辑步骤 1：展开复数指数**
    - 令 $X = n\phi - z \sin \phi$。
    - 根据[[欧拉公式 (Euler's Formula)]]：$\exp(-iX) = \cos X - i \sin X$。
    - 所以积分变为：
        $$J_n(z) = \frac{1}{2\pi} \left[ \int_{-\pi}^{\pi} \cos(n\phi - z \sin \phi) d\phi - i \int_{-\pi}^{\pi} \sin(n\phi - z \sin \phi) d\phi \right]$$

- **逻辑步骤 2：分析奇偶性 (Even/Odd Properties)**
    - 考虑函数 $g(\phi) = \sin(n\phi - z \sin \phi)$：
        - $g(-\phi) = \sin(n(-\phi) - z \sin(-\phi)) = \sin(-n\phi + z \sin \phi) = -\sin(n\phi - z \sin \phi)$。
        - 这是一个[[奇函数 (Odd function)]]。
        - **定理：** 奇函数在对称区间 $[-\pi, \pi]$ 上的积分为 0。
        - 所以，虚部积分消失了。
    - 考虑函数 $h(\phi) = \cos(n\phi - z \sin \phi)$：
        - $h(-\phi) = \cos(n(-\phi) - z \sin(-\phi)) = \cos(-(n\phi - z \sin \phi)) = \cos(n\phi - z \sin \phi)$。
        - 这是一个[[偶函数 (Even function)]]。
        - **定理：** 偶函数在对称区间 $[-\pi, \pi]$ 上的积分等于 $[0, \pi]$ 区间积分的两倍。

- **逻辑步骤 3：最终整合**
    - $J_n(z) = \frac{1}{2\pi} \cdot \left[ 2 \int_{0}^{\pi} \cos(n\phi - z \sin \phi) d\phi - 0 \right]$
    - 约掉系数 2：
        $$J_n(z) = \frac{1}{\pi} \int_{0}^{\pi} \cos(n\phi - z \sin \phi) d\phi$$

- **逻辑步骤 4：得出结论**
    - **结论：** 成功证明了 $J_n(z)$ 可以表示为实数形式的定积分。

#### 5. 总结与工科思维 (Summary & Engineering Logic)

这道题的逻辑链条非常清晰，是典型的“定义 -> 替换 -> 化简”过程：

- ● **第一阶段（定义）：** 只要是求级数系数，永远先祭出 [[劳伦系数公式 (Laurent Coefficient Formula)]]。
- ● **第二阶段（坐标转换）：** 复平面上的圆周积分不直观，通过 $w = e^{i\phi}$ 转换到角度坐标系（实数轴）。
- ● **第三阶段（三角化简）：** 看到 $e^{i\phi} - e^{-i\phi}$ 就要条件反射想到 $2i \sin \phi$。
- ● **第四阶段（对称性利用）：** 在对称区间积分时，利用[[奇偶性 (Even and odd properties)]]可以极大地简化计算，把复数积分变成实数积分。

**关键单词回顾：**
- [[劳伦级数 (Laurent Series)]]
- [[单位圆 (Unit circle)]]
- [[劳伦系数公式 (Laurent Coefficient Formula)]]
- [[欧拉公式 (Euler's Formula)]]
- [[参数化 (Parameterization)]]
- [[奇偶性 (Even and odd properties)]]
- [[贝塞尔函数 (Bessel Functions)]]
# Q5
你好！这道题目是复分析中非常核心的计算题，它要求我们使用[[柯西留数定理 (Cauchy's Residue Theorem)]]来计算四个不同函数的[[围道积分 (Contour Integral)]]。

这道题是典型的“流程化”题目，只要掌握了寻找[[奇点 (Singularities)]]和计算[[留数 (Residue)]]的套路，就能像工厂流水线一样解出来。

#### 1. 题目翻译与任务拆解 (Translation & Task Breakdown)

- **题目翻译：**
    - **原题：** Use Cauchy’s residue theorem to evaluate the integral of each of these functions around the circle $|z| = 3$ in the positive sense.
    - **中文直译：** 使用[[柯西留数定理 (Cauchy's Residue Theorem)]]计算下列每个函数沿圆周 $|z|=3$（按[[正向 (Positive sense)]]，即逆时针方向）的积分。
- **题目给出的信息点：**
    - **信息点 1：** 积分路径 $C$ 是 $|z|=3$。这是一个以原点为中心，半径为 3 的圆。
    - **信息点 2：** 方向是 [[正向 (Positive sense)]]，这意味着我们直接套用定理公式，不需要额外加负号。
    - **信息点 3：** 工具必须是 [[柯西留数定理 (Cauchy's Residue Theorem)]]。
- **我们要做的任务：**
    - **第一步：** 找出函数所有的[[奇点 (Singularities)]]（让函数“爆炸”或者分母为 0 的点）。
    - **第二步：** 判断哪些奇点落在圆圈 $|z|=3$ 的**内部**。落在外面的我们不管。
    - **第三步：** 计算圆圈内部每个奇点的[[留数 (Residue)]]。
    - **第四步：** 把所有留数加起来，乘以 $2\pi i$。

#### 2. 背景条件与基本概念 (Background & Concepts)

- #### [[柯西留数定理 (Cauchy's Residue Theorem)]]
    - 这是复分析的“终极武器”。它告诉我们：一个函数在闭合曲线上的积分，只取决于曲线内部那些“坏点”（奇点）的[[留数 (Residue)]]之和。
    - 公式：$\int_C f(z) dz = 2\pi i \sum_{k=1}^n \text{Res}(f, z_k)$。
    - **工科理解**：就像算一个水管的流量，你不需要管水管壁怎么走，你只需要管水管里面有几个“出水口”（奇点）以及每个出水口排了多少水（留数）。

- #### [[奇点 (Singularities)]]
    - 函数不解析的点。最常见的就是分母等于 0 的点。
    - 比如 $\frac{1}{z-1}$，在 $z=1$ 处就是奇点。

- #### [[留数 (Residue)]]
    - 它是函数在奇点处的[[劳伦级数 (Laurent Series)]]展开式中，$(z-z_0)^{-1}$ 这一项前面的系数，通常记作 $c_{-1}$。
    - **计算方法 A（公式法）**：如果 $z_0$ 是 $m$ 阶[[极点 (Pole)]]，则 $\text{Res}(f, z_0) = \frac{1}{(m-1)!} \lim_{z \to z_0} \frac{d^{m-1}}{dz^{m-1}} [(z-z_0)^m f(z)]$。
    - **计算方法 B（级数法）**：直接写出函数的展开式，找 $\frac{1}{z-z_0}$ 前面的系数。

- #### [[极点 (Poles)]]
    - 奇点的一种。如果分母是 $(z-z_0)^m$，我们就说 $z_0$ 是 $m$ 阶极点。

- #### [[本性奇点 (Essential Singularity)]]
    - 另一种奇点。比如 $e^{1/z}$ 在 $z=0$ 处。这种点不能用公式法，必须用[[级数展开 (Series expansion)]]找系数。

#### 3. (a) 部分解答思路与逻辑链条 (Logic Chain for a)

函数：$f(z) = \frac{\exp(-z)}{z^2}$

- **逻辑步骤：**
    - ● 观察分母 $z^2 = 0$ → 找到[[奇点 (Singularity)]] $z=0$。
    - ● 检查位置：$|0| = 0 < 3$ → 该奇点在圆圈**内部**。
    - ● 判定类型：分母是 $z^2$ → $z=0$ 是一个 **2 阶[[极点 (Pole of order 2)]]**。
    - ● 计算[[留数 (Residue)]]（使用级数法最快）：
        - 我们知道 $\exp(-z) = 1 - z + \frac{z^2}{2!} - \frac{z^3}{3!} + \dots$
        - 那么 $f(z) = \frac{1}{z^2}(1 - z + \frac{z^2}{2!} - \dots) = \frac{1}{z^2} - \frac{1}{z} + \frac{1}{2} - \dots$
        - 找到 $\frac{1}{z}$ 前面的系数 → $c_{-1} = -1$。
    - ● 应用[[柯西留数定理 (Cauchy's Residue Theorem)]]：
        - 积分 = $2\pi i \times (-1) = -2\pi i$。

#### 4. (b) 部分解答思路与逻辑链条 (Logic Chain for b)

函数：$f(z) = \frac{\exp(-z)}{(z-1)^2}$

- **逻辑步骤：**
    - ● 观察分母 $(z-1)^2 = 0$ → 找到[[奇点 (Singularity)]] $z=1$。
    - ● 检查位置：$|1| = 1 < 3$ → 该奇点在圆圈**内部**。
    - ● 判定类型：分母是 $(z-1)^2$ → $z=1$ 是一个 **2 阶[[极点 (Pole of order 2)]]**。
    - ● 计算[[留数 (Residue)]]（使用公式法）：
        - 公式：$\text{Res}(f, 1) = \frac{d}{dz} [(z-1)^2 \cdot \frac{e^{-z}}{(z-1)^2}] \Big|_{z=1}$
        - 简化：$\frac{d}{dz} [e^{-z}] \Big|_{z=1} = -e^{-z} \Big|_{z=1} = -e^{-1}$。
    - ● 应用[[柯西留数定理 (Cauchy's Residue Theorem)]]：
        - 积分 = $2\pi i \times (-e^{-1}) = -\frac{2\pi i}{e}$。

#### 5. (c) 部分解答思路与逻辑链条 (Logic Chain for c)

函数：$f(z) = z^2 \exp(1/z)$

- **逻辑步骤：**
    - ● 观察指数部分 $1/z$ → 找到[[奇点 (Singularity)]] $z=0$。
    - ● 检查位置：$|0| < 3$ → 在**内部**。
    - ● 判定类型：指数里有 $1/z$ → $z=0$ 是[[本性奇点 (Essential Singularity)]]。
    - ● 计算[[留数 (Residue)]]（必须用级数展开）：
        - $\exp(w) = 1 + w + \frac{w^2}{2!} + \frac{w^3}{3!} + \dots$
        - 令 $w = 1/z$：$\exp(1/z) = 1 + \frac{1}{z} + \frac{1}{2!z^2} + \frac{1}{3!z^3} + \dots$
        - 乘以 $z^2$：$f(z) = z^2(1 + \frac{1}{z} + \frac{1}{2z^2} + \frac{1}{6z^3} + \dots) = z^2 + z + \frac{1}{2} + \frac{1}{6z} + \dots$
        - 找到 $\frac{1}{z}$ 前面的系数 → $c_{-1} = 1/6$。
    - ● 应用[[柯西留数定理 (Cauchy's Residue Theorem)]]：
        - 积分 = $2\pi i \times \frac{1}{6} = \frac{\pi i}{3}$。

#### 6. (d) 部分解答思路与逻辑链条 (Logic Chain for d)

函数：$f(z) = \frac{z+1}{z^2-2z}$

- **逻辑步骤：**
    - ● 分解分母：$z^2 - 2z = z(z-2)$。
    - ● 找到[[奇点 (Singularities)]]：$z=0$ 和 $z=2$。
    - ● 检查位置：
        - $|0| = 0 < 3$ → 在**内部**。
        - $|2| = 2 < 3$ → 在**内部**。
        - **结论**：两个点都要算！
    - ● 计算 $z=0$ 的留数（1 阶极点）：
        - $\text{Res}(f, 0) = \lim_{z \to 0} [z \cdot \frac{z+1}{z(z-2)}] = \frac{0+1}{0-2} = -1/2$。
    - ● 计算 $z=2$ 的留数（1 阶极点）：
        - $\text{Res}(f, 2) = \lim_{z \to 2} [(z-2) \cdot \frac{z+1}{z(z-2)}] = \frac{2+1}{2} = 3/2$。
    - ● 应用[[柯西留数定理 (Cauchy's Residue Theorem)]]：
        - 积分 = $2\pi i \times (\text{Res}(f, 0) + \text{Res}(f, 2))$
        - 积分 = $2\pi i \times (-1/2 + 3/2) = 2\pi i \times 1 = 2\pi i$。

#### 7. 总结与考试套路 (Summary & Exam Tips)

以后遇到这种题，你的工科思维逻辑应该是：

- **第一步：找分母的根。** 那些就是你的[[奇点 (Singularities)]]。
- **第二步：画圆圈。** 看看哪些根在圆里面。不在圆里面的根，哪怕它再复杂也跟你没关系，直接无视。
- **第三步：选工具。**
    - 如果是简单的分母，用[[公式法 (Formula method)]]。
    - 如果有 $e^{1/z}$ 或者 $\sin(1/z)$，必须用[[级数展开 (Series expansion)]]。
- **第四步：求和。** 别忘了最后要乘以 $2\pi i$。

**关键单词回顾：**
- [[柯西留数定理 (Cauchy's Residue Theorem)]]
- [[奇点 (Singularities)]]
- [[留数 (Residue)]]
- [[极点 (Poles)]]
- [[本性奇点 (Essential Singularity)]]
- [[正向 (Positive sense)]]
- [[围道积分 (Contour Integral)]]
# Q6
你好！这道题目是复分析中一个非常漂亮的综合题。它要求我们证明一个看起来很复杂的积分等式。这道题的精妙之处在于它把[[麦克劳林级数 (Maclaurin Series)]]、[[逐项积分 (Term-by-term Integration)]]和[[留数定理 (Residue Theorem)]]完美地结合在了一起。

我会按照你的要求，为你拆解每一个逻辑环节。

#### 1. 题目翻译与任务拆解 (Translation & Task Breakdown)

- **题目翻译：**
    - **原题：** 设 $C$ 表示圆周 $|z|=1$，取[[逆时针方向 (Counterclockwise)]]，利用以下步骤证明：
        $$\int_C \exp\left(z + \frac{1}{z}\right) dz = 2\pi i \sum_{n=0}^{\infty} \frac{1}{n!(n+1)!}$$
    - **(a) 部分：** 通过使用 $e^z$ 的[[麦克劳林级数 (Maclaurin series)]]并参考讲义中的定理 12.3.2（该定理证明了可以进行[[逐项积分 (Term-by-term integration)]]），将上述积分写成：
        $$\sum_{n=0}^{\infty} \frac{1}{n!} \int_C z^n \exp(1/z) dz$$
    - **(b) 部分：** 计算 (a) 部分中出现的积分，从而得出最终结果。

- **题目给出的信息点：**
    - **信息点 1：** 积分路径 $C$ 是单位圆 $|z|=1$。
    - **信息点 2：** 函数是 $\exp(z + 1/z)$。根据指数函数的性质，它可以拆成 $\exp(z) \cdot \exp(1/z)$。
    - **信息点 3：** 提示我们要先对其中一部分做级数展开，然后交换积分和求和的顺序。

- **我们要做的任务：**
    - **任务 1：** 把 $\exp(z)$ 展开成无穷级数。
    - **任务 2：** 证明（或根据提示直接使用）积分号可以放到求和号里面去。
    - **任务 3：** 针对每一项 $z^n \exp(1/z)$ 计算它的[[留数 (Residue)]]。
    - **任务 4：** 把所有结果汇总，凑出最终的求和公式。

#### 2. 背景条件与基本概念 (Background & Concepts)

- #### [[麦克劳林级数 (Maclaurin Series)]]
    - 这是泰勒级数在 $z=0$ 处的特殊形式。对于指数函数，你必须死记硬背住这个公式：
    - $e^z = 1 + z + \frac{z^2}{2!} + \frac{z^3}{3!} + \dots = \sum_{n=0}^{\infty} \frac{z^n}{n!}$
    - 这个级数在整个复平面上都是[[收敛的 (Convergent)]]。

- #### [[逐项积分 (Term-by-term Integration)]]
    - 通常情况下，积分和无穷求和是不能随便交换顺序的。
    - 但如果级数在积分路径上是[[一致收敛的 (Uniformly convergent)]]，我们就可以先积分每一项，再把结果加起来。定理 12.3.2 就是在为这一步提供法律依据。

- #### [[留数定理 (Residue Theorem)]]
    - 计算闭合路径积分的终极工具：$\int_C f(z) dz = 2\pi i \times (\text{所有内部奇点的留数之和})$。
    - 在本题中，唯一的[[奇点 (Singularity)]]是 $z=0$。

- #### [[本性奇点 (Essential Singularity)]]
    - 函数 $\exp(1/z)$ 在 $z=0$ 处表现得非常疯狂，它不是简单的几阶极点，而是[[本性奇点 (Essential Singularity)]]。
    - 对付这种点，唯一的办法就是写出它的[[劳伦级数 (Laurent Series)]]，然后肉眼寻找 $1/z$ 项前面的系数。

#### 3. (a) 部分解答思路与逻辑链条 (Logic Chain for Part a)

这一步的目标是把一个复杂的积分拆成无穷多个简单的积分。

- **逻辑步骤：**
    - ● 函数为 $f(z) = \exp(z + 1/z) = \exp(z) \cdot \exp(1/z)$
        - → 利用指数函数的[[指数法则 (Exponential law)]]：$e^{a+b} = e^a \cdot e^b$。
    - ● 对 $\exp(z)$ 使用[[麦克劳林级数 (Maclaurin Series)]]展开
        - → $\exp(z) = \sum_{n=0}^{\infty} \frac{z^n}{n!}$。
    - ● 将展开式代入积分式
        - → $\int_C \left( \sum_{n=0}^{\infty} \frac{z^n}{n!} \right) \exp(1/z) dz$。
    - ● 将 $\exp(1/z)$ 乘进求和号内部
        - → $\int_C \sum_{n=0}^{\infty} \left( \frac{1}{n!} z^n \exp(1/z) \right) dz$。
    - ● 应用[[逐项积分 (Term-by-term Integration)]]定理
        - → 交换 $\int$ 和 $\sum$ 的位置。
    - ● **结论：** 得到 $\sum_{n=0}^{\infty} \frac{1}{n!} \int_C z^n \exp(1/z) dz$。
        - → 这一步完成了从“一个大积分”到“无穷多个小积分之和”的转变。

#### 4. (b) 部分解答思路与逻辑链条 (Logic Chain for Part b)

这一步的目标是算出每一个小积分的值。

- **逻辑步骤 1：分析单个积分 $I_n = \int_C z^n \exp(1/z) dz$**
    - ● 观察函数 $g(z) = z^n \exp(1/z)$
        - → 唯一的[[奇点 (Singularity)]]在 $z=0$。
    - ● 展开 $\exp(1/z)$ 的[[劳伦级数 (Laurent Series)]]
        - → 我们知道 $e^w = \sum_{k=0}^{\infty} \frac{w^k}{k!}$。
        - → 令 $w = 1/z$，得到 $\exp(1/z) = \sum_{k=0}^{\infty} \frac{1}{k! z^k} = 1 + \frac{1}{z} + \frac{1}{2!z^2} + \frac{1}{3!z^3} + \dots$。
    - ● 将 $z^n$ 乘进去
        - → $z^n \exp(1/z) = z^n \left( 1 + \frac{1}{z} + \frac{1}{2!z^2} + \dots + \frac{1}{k!z^k} + \dots \right)$
        - → 展开后为：$z^n + z^{n-1} + \frac{z^{n-2}}{2!} + \dots + \frac{z^{n-k}}{k!} + \dots$。

- **逻辑步骤 2：寻找[[留数 (Residue)]]**
    - ● 根据定义，留数是 $1/z$（即 $z^{-1}$）那一项前面的系数。
    - ● 在展开式 $\frac{z^{n-k}}{k!}$ 中，我们需要幂次 $n-k = -1$。
    - ● 解方程：$k = n + 1$。
    - ● 对应的系数就是当 $k = n+1$ 时的项
        - → 系数为 $\frac{1}{(n+1)!}$。
    - ● **结论：** $\text{Res}(z^n \exp(1/z), 0) = \frac{1}{(n+1)!}$。

- **逻辑步骤 3：计算积分值**
    - ● 根据[[留数定理 (Residue Theorem)]]
        - → $\int_C z^n \exp(1/z) dz = 2\pi i \cdot \text{Res} = 2\pi i \frac{1}{(n+1)!}$。

- **逻辑步骤 4：代回总和式**
    - ● 将 $I_n$ 的结果代入 (a) 部分的求和式
        - → $\sum_{n=0}^{\infty} \frac{1}{n!} \left( 2\pi i \frac{1}{(n+1)!} \right)$。
    - ● 提取常数 $2\pi i$
        - → $2\pi i \sum_{n=0}^{\infty} \frac{1}{n!(n+1)!}$。
    - ● **结论：** 证明完毕。

#### 5. 总结与工科思维 (Summary & Engineering Logic)

这道题展示了一个非常经典的“化繁为简”的工程处理流程：

- ● **第一阶段（拆解）：** 面对复杂的复合函数 $\exp(z+1/z)$，直接积分是不可能的。我们利用级数展开，把它拆成了一系列 $z^n \exp(1/z)$ 的叠加。
- ● **第二阶段（单元测试）：** 我们不再看整体，而是只看其中某一项 $z^n \exp(1/z)$。通过[[劳伦级数 (Laurent Series)]]展开，我们发现每一项都贡献了一个非常整齐的[[留数 (Residue)]] $\frac{1}{(n+1)!}$。
- ● **第三阶段（封装）：** 利用[[留数定理 (Residue Theorem)]]把每一项的积分算出来，最后再把它们全部加回去。

**关键单词回顾：**
- [[麦克劳林级数 (Maclaurin Series)]]
- [[逐项积分 (Term-by-term Integration)]]
- [[留数定理 (Residue Theorem)]]
- [[本性奇点 (Essential Singularity)]]
- [[劳伦级数 (Laurent Series)]]
- [[逆时针方向 (Counterclockwise)]]
- [[一致收敛 (Uniform Convergence)]]
# Q7
#### 1. 题目翻译与拆解 (Problem Translation & Breakdown)

**题目翻译：**
问题 7. (选自 Brown & Churchill 练习 79.1) 在下列每种情况下，写出函数在其**孤立奇点 (isolated singular point)** 处的**主要部分 (principal part)**，并判断该点是**可去奇点 (removable singular point)**、**本性奇点 (essential singular point)** 还是**极点 (pole)**。

**题目信息点拆解：**
- **目标 1：找到孤立奇点 (Find isolated singular points)**。即找到函数分母为 0 或函数定义“爆炸”的那个点。
- **目标 2：写出主要部分 (Write the principal part)**。你需要对函数进行**劳伦级数展开 (Laurent series expansion)**。展开式中所有“负幂次项”（即 $1/(z-z_0)^n$ 这种形式）的总和就是主要部分。
- **目标 3：==分类奇点 (Classify the singularity)**。
    - ==如果没有负幂次项 $\rightarrow$ **可去奇点 (Removable)**。==
    - ==如果负幂次项有有限个（最高到 $n$ 次） $\rightarrow$ **$n$ 阶极点 (Pole of order $n$)**。==
    - ==如果负幂次项有无限多个 $\rightarrow$ **本性奇点 (Essential)**。==

---

#### 2. 背景条件与基本概念 (Background & Concepts)

- [[孤立奇点 (Isolated Singular Point)]]
    - **解释**：如果函数 $f(z)$ 在点 $z_0$ 处不解析（比如分母为 0），但在 $z_0$ 周围的一个小圆圈内（不含 $z_0$ 本身）是解析的，那么 $z_0$ 就是孤立奇点。
    - **工科理解**：这就是机器上那个唯一的“故障点”，周围都是好的。

- [[劳伦级数 (Laurent Series)]]
    - **数学形式**：$f(z) = \sum_{n=0}^{\infty} a_n(z-z_0)^n + \sum_{n=1}^{\infty} \frac{b_n}{(z-z_0)^n}$
    - **解释**：在奇点附近，函数可以拆成两部分。左边是**解析部分 (Analytic Part)**，全是正幂次；右边是**主要部分 (Principal Part)**，全是负幂次。

- [[主要部分 (Principal Part)]]
    - **解释**：就是劳伦级数里那些分母含有 $(z-z_0)$ 的项。它们决定了函数在奇点处的“爆炸”程度。

- [[奇点的三种类型 (Three Types of Singularities)]]
    - **可去奇点 (Removable Singular Point)**：主要部分为 0。函数在这一点其实可以“修补”好。
    - **极点 (Pole)**：主要部分有有限多项。最高的那一项的次数 $m$ 称为**阶 (Order)**。
    - **本性奇点 (Essential Singular Point)**：主要部分有无穷多项。函数在这里的行为极其混乱。

---

#### 3. 问题解答思路与逻辑链条 (Solutions & Logic Chains)

我们将逐一拆解题目中的五个小题。

#### (a) $f(z) = z \exp(\frac{1}{z})$

- **逻辑链条：**
    - ● 观察函数 $\rightarrow$ 指数函数内部是 $1/z$ $\rightarrow$ 当 $z=0$ 时分母为 0 $\rightarrow$ **孤立奇点 (Isolated Singular Point)** 是 $z=0$。
    - ● 使用已知公式 $\exp(u) = 1 + u + \frac{u^2}{2!} + \frac{u^3}{3!} + \dots$（这是 **泰勒展开 Taylor Expansion**）。
    - ● 令 $u = \frac{1}{z}$ $\rightarrow$ $\exp(\frac{1}{z}) = 1 + \frac{1}{z} + \frac{1}{2!z^2} + \frac{1}{3!z^3} + \dots$
    - ● 整体乘以 $z$ $\rightarrow$ $f(z) = z(1 + \frac{1}{z} + \frac{1}{2!z^2} + \frac{1}{3!z^3} + \dots) = z + 1 + \frac{1}{2!z} + \frac{1}{3!z^2} + \dots$
    - ● 提取负幂次项 $\rightarrow$ **主要部分 (Principal Part)** 是 $\frac{1}{2!z} + \frac{1}{3!z^2} + \frac{1}{4!z^3} + \dots$
    - ● 观察项数 $\rightarrow$ 负幂次项有无限多个 $\rightarrow$ **本性奇点 (Essential Singular Point)**。

- **结论：**
    - 主要部分：$\sum_{n=1}^{\infty} \frac{1}{(n+1)! z^n}$
    - 类型：Essential singular point

#### (b) $f(z) = \frac{z^2}{1+z}$

- **逻辑链条：**
    - ● 观察分母 $\rightarrow$ $1+z=0$ 时失效 $\rightarrow$ **孤立奇点 (Isolated Singular Point)** 是 $z=-1$。
    - ● 目标是把函数写成 $(z+1)$ 的幂次 $\rightarrow$ 需要进行变量代换。
    - ● 令 $w = z+1$，则 $z = w-1$。
    - ● 代入函数 $\rightarrow$ $f(z) = \frac{(w-1)^2}{w} = \frac{w^2 - 2w + 1}{w}$。
    - ● 拆分每一项 $\rightarrow$ $f(z) = \frac{w^2}{w} - \frac{2w}{w} + \frac{1}{w} = w - 2 + \frac{1}{w}$。
    - ● 换回 $z$ $\rightarrow$ $f(z) = (z+1) - 2 + \frac{1}{z+1}$。
    - ● 提取负幂次项 $\rightarrow$ **主要部分 (Principal Part)** 是 $\frac{1}{z+1}$。
    - ● 观察最高负幂次 $\rightarrow$ 只有一项，次数是 1 $\rightarrow$ **1 阶极点 (Pole of order 1)**，也叫 **简单极点 (Simple pole)**。

- **结论：**
    - 主要部分：$\frac{1}{z+1}$
    - 类型：Pole of order 1 (Simple pole)

#### (c) $f(z) = \frac{\sin z}{z}$

- **逻辑链条：**
    - ● 观察分母 $\rightarrow$ $z=0$ 时失效 $\rightarrow$ **孤立奇点 (Isolated Singular Point)** 是 $z=0$。
    - ● 使用已知公式 $\sin z = z - \frac{z^3}{3!} + \frac{z^5}{5!} - \dots$。
    - ● 整体除以 $z$ $\rightarrow$ $f(z) = \frac{z - \frac{z^3}{3!} + \frac{z^5}{5!} - \dots}{z} = 1 - \frac{z^2}{3!} + \frac{z^4}{5!} - \dots$。
    - ● 提取负幂次项 $\rightarrow$ 展开式中没有任何分母含有 $z$ 的项 $\rightarrow$ **主要部分 (Principal Part)** 是 $0$。
    - ● 根据定义 $\rightarrow$ 主要部分为 0 $\rightarrow$ **可去奇点 (Removable Singular Point)**。

- **结论：**
    - 主要部分：$0$
    - 类型：Removable singular point

#### (d) $f(z) = \frac{\cos z}{z}$

- **逻辑链条：**
    - ● 观察分母 $\rightarrow$ $z=0$ 时失效 $\rightarrow$ **孤立奇点 (Isolated Singular Point)** 是 $z=0$。
    - ● 使用已知公式 $\cos z = 1 - \frac{z^2}{2!} + \frac{z^4}{4!} - \dots$。
    - ● 整体除以 $z$ $\rightarrow$ $f(z) = \frac{1 - \frac{z^2}{2!} + \frac{z^4}{4!} - \dots}{z} = \frac{1}{z} - \frac{z}{2!} + \frac{z^3}{4!} - \dots$。
    - ● 提取负幂次项 $\rightarrow$ **主要部分 (Principal Part)** 是 $\frac{1}{z}$。
    - ● 观察最高负幂次 $\rightarrow$ 只有一项，次数是 1 $\rightarrow$ **1 阶极点 (Pole of order 1)**。

- **结论：**
    - 主要部分：$\frac{1}{z}$
    - 类型：Pole of order 1 (Simple pole)

#### (e) $f(z) = \frac{1}{(2-z)^3}$

- **逻辑链条：**
    - ● 观察分母 $\rightarrow$ $2-z=0$ 时失效 $\rightarrow$ **孤立奇点 (Isolated Singular Point)** 是 $z=2$。
    - ● 目标是写成 $(z-2)$ 的形式 $\rightarrow$ 注意符号。
    - ● $2-z = -(z-2)$ $\rightarrow$ 所以 $(2-z)^3 = [-(z-2)]^3 = -(z-2)^3$。
    - ● 代入函数 $\rightarrow$ $f(z) = \frac{1}{-(z-2)^3} = -\frac{1}{(z-2)^3}$。
    - ● 观察展开式 $\rightarrow$ 这个函数本身就已经是一个只有一项的劳伦级数了，且这一项就是负幂次项。
    - ● 提取负幂次项 $\rightarrow$ **主要部分 (Principal Part)** 是 $-\frac{1}{(z-2)^3}$。
    - ● 观察最高负幂次 $\rightarrow$ 次数是 3 $\rightarrow$ **3 阶极点 (Pole of order 3)**。

- **结论：**
    - 主要部分：$-\frac{1}{(z-2)^3}$
    - 类型：Pole of order 3

---

#### 4. 总结与规则 (Summary & Rules)

- **如何找主要部分？**
    - 核心是做 **劳伦展开 (Laurent Expansion)**。
    - 如果奇点在 $z=0$，直接用已知的泰勒公式（如 $\sin, \cos, \exp$）。
    - 如果奇点在 $z=z_0$，先做代换 $w = z-z_0$，把问题转化到 $w=0$ 的情况。

- **如何判断类型？**
    - **没有** $1/(z-z_0)$ 这种项 $\rightarrow$ **Removable (可去)**。
    - 有**有限个** $1/(z-z_0)$ 这种项 $\rightarrow$ **Pole (极点)**。
    - 有**无限个** $1/(z-z_0)$ 这种项 $\rightarrow$ **Essential (本性)**。

[[Laurent展开的具体方法]]
