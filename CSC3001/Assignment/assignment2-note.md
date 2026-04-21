- [x] 完成CSC3001_Ass2的内容 📅 2026-04-14 ✅ 2026-04-13
- [x] 完成CSC3001_Ass2的提交 📅 2026-04-13 ✅ 2026-04-14

# Q8
#### ① 题目翻译 (Problem Translation)

考虑斐波那契数列 (Fibonacci sequence) $\{F_n\}$，其中初始条件 (Initial Conditions) 为 $F_0 = 0$，$F_1 = 1$，且对于其他 $n \ge 2$ 的项，满足递推关系 (Recurrence Relation)：$F_n = F_{n-1} + F_{n-2}$。请计算该斐波那契数列 $F_n$ 的生成函数 (Generating Function) $f(x)$ 的闭式解 (Closed Form)。

---

#### ② 背景条件与基本概念解释 (Background & Concepts)

作为数学系新生，理解这道题需要掌握以下几个核心“工具”：

- **1. 数列 (Sequence) $\{F_n\}$**
    - 就像一排排好队的数字。斐波那契数列的特点是：从第三项开始，每一项都等于前两项之和。
    - 例子：$0, 1, 1, 2, 3, 5, 8, \dots$

- **2. 生成函数 (Generating Function, 简称 GF)**
    - **工科思维理解：** 把它想象成一个“信息存储器”或“衣架”。我们把数列里的每一个数字 $F_n$ 挂在 $x^n$ 这个“钩子”上。
    - **数学定义：** $f(x) = \sum_{n=0}^{\infty} F_n x^n = F_0 x^0 + F_1 x^1 + F_2 x^2 + \dots$
    - **为什么要这么做？** 因为处理一串无穷无尽的数字（数列）很难，但如果我们把它变成一个函数 $f(x)$，就可以用代数（Algebra）的方法去“解”它。

- **3. 闭式解 (Closed Form)**
    - **通俗解释：** 就是把那个没完没了的无穷级数（$\sum \dots$）压缩成一个简单的分数或公式。
    - 比如：$1 + x + x^2 + \dots$ 的闭式解是 $\frac{1}{1-x}$。

- **4. 位移性质 (Shifting Property)**
    - 如果 $f(x)$ 代表序列 $F_0, F_1, F_2, \dots$
    - 那么 $x \cdot f(x)$ 就代表序列 $0, F_0, F_1, F_2, \dots$（整体向右挪了一位，前面补个0）。
    - 那么 $x^2 \cdot f(x)$ 就代表序列 $0, 0, F_0, F_1, \dots$（向右挪了两位）。
    - **这个性质是解题的关键**，因为它能让我们把递推公式里的 $F_{n-1}$ 和 $F_{n-2}$ 转换回 $f(x)$。

---

#### ③ 问题解答思路与逻辑链条 (Logic Chain)

我们要把“递推公式”变成“代数方程”。

- **Step 1: 写出生成函数的定义 (Definition)**
    - 逻辑：我们要找 $f(x)$，首先得把它写出来。
    - $f(x) = F_0 + F_1 x + F_2 x^2 + F_3 x^3 + \dots + F_n x^n + \dots$

- **Step 2: 写出递推关系 (Recurrence Relation)**
    - 逻辑：题目给出的核心规则。
    - $F_n = F_{n-1} + F_{n-2}$ （适用于 $n \ge 2$）

- **Step 3: 构造等式 (Constructing the Equation)**
    - 逻辑：为了利用 $F_n = F_{n-1} + F_{n-2}$，我们需要在 $f(x)$ 的展开式中找到对应的项。
    - 我们观察：
        - $f(x) = F_0 + F_1 x + F_2 x^2 + F_3 x^3 + \dots$
        - $x f(x) = 0 + F_0 x + F_1 x^2 + F_2 x^3 + \dots$ （利用位移性质 Shifting Property）
        - $x^2 f(x) = 0 + 0 + F_0 x^2 + F_1 x^3 + \dots$ （再次利用位移性质）

- **Step 4: 执行减法 (Subtraction / Elimination)**
    - 逻辑：因为 $F_n - F_{n-1} - F_{n-2} = 0$，所以如果我们用 $f(x)$ 减去后面两项，大部分项都会抵消掉。
    - 计算 $f(x) - x f(x) - x^2 f(x)$：
        - $x^0$ 项：$F_0 = 0$
        - $x^1$ 项：$(F_1 - F_0)x = (1 - 0)x = x$
        - $x^2$ 项：$(F_2 - F_1 - F_0)x^2 = 0 \cdot x^2 = 0$ （因为递推关系）
        - $x^n$ 项：$(F_n - F_{n-1} - F_{n-2})x^n = 0$ （全部抵消）

- **Step 5: 整理得到闭式解 (Solve for $f(x)$)**
    - 逻辑：现在只剩下一个简单的代数方程了。
    - $f(x)(1 - x - x^2) = x$
    - $\rightarrow f(x) = \frac{x}{1 - x - x^2}$

---

#### ④ 考试答题卡风格解答 (Exam-Style Solution)

**Solution:**

- **1. Define the Ordinary Generating Function (OGF):**
    - Let $f(x) = \sum_{n=0}^{\infty} F_n x^n = F_0 + F_1 x + \sum_{n=2}^{\infty} F_n x^n$.
    - Given initial conditions (初始条件): $F_0 = 0, F_1 = 1$.
    - So, $f(x) = x + \sum_{n=2}^{\infty} F_n x^n$.

- **2. Apply the Recurrence Relation (应用递推关系):**
    - For $n \ge 2$, we have $F_n = F_{n-1} + F_{n-2}$.
    - Substitute this into the summation:
    - $f(x) - x = \sum_{n=2}^{\infty} (F_{n-1} + F_{n-2}) x^n$

- **3. Use Linearity and Shifting Properties (利用线性与位移性质):**
    - $f(x) - x = \sum_{n=2}^{\infty} F_{n-1} x^n + \sum_{n=2}^{\infty} F_{n-2} x^n$
    - $f(x) - x = x \sum_{n=2}^{\infty} F_{n-1} x^{n-1} + x^2 \sum_{n=2}^{\infty} F_{n-2} x^{n-2}$
    - $f(x) - x = x (f(x) - F_0) + x^2 f(x)$

- **4. Substitute $F_0 = 0$ and solve (代入并求解):**
    - $f(x) - x = x f(x) + x^2 f(x)$
    - $f(x) - x f(x) - x^2 f(x) = x$
    - $f(x)(1 - x - x^2) = x$

- **Conclusion (结论):**
    - The closed form of the generating function is:
    - $f(x) = \frac{x}{1 - x - x^2}$

---

#### ⑤ 逻辑链条拆解 (Logic Chain Summary)

- $F_n = F_{n-1} + F_{n-2}$ (递推关系 Recurrence Relation)
- $\rightarrow$ 每一项都对应一个 $x^n$ (生成函数定义 OGF Definition)
- $\rightarrow$ $F_{n-1}$ 对应 $x \cdot f(x)$，$F_{n-2}$ 对应 $x^2 \cdot f(x)$ (位移性质 Shifting Property)
- $\rightarrow$ 建立方程 $f(x) - x = x f(x) + x^2 f(x)$ (代数化 Algebraic Transformation)
- $\rightarrow$ 提取公因式并相除 (解方程 Solving Equation)
- $\rightarrow$ 得到 $f(x) = \frac{x}{1-x-x^2}$ (目标结果 Closed Form)

**以后什么时候能用这个方法？**
只要你看到题目给了一个**递推公式**（比如 $a_n = 3a_{n-1} + 2$ 之类的）并且让你求**生成函数**，统一套路就是：
- 1. 写出 $f(x)$ 定义。
- 2. 根据递推式，给 $f(x)$ 乘以 $x$ 或 $x^2$ 来对齐下标。
- 3. 加加减减把中间的项抵消掉。
- 4. 解出 $f(x)$。

# Q9
#### ① 题目翻译 (Problem Translation)

同样考虑斐波那契数列 (Fibonacci sequence) $\{F_n\}$，确定下方数列的和。你可以使用 $n$ 阶斐波那契数 (n-Fibonacci number) $F_n$ 来表示这些值。

- 1. $S_n^1 = F_0 + F_1 + F_2 + \dots + F_n$ （求前 $n$ 项的和）
- 2. $S_n^2 = F_0 + F_2 + F_4 + \dots + F_{2n}$ （求前 $n$ 个偶数下标项的和）

---

#### ② 背景条件与基本概念解释 (Background & Concepts)

作为数学系新生，处理这类“求和”问题的核心工科思维是：**寻找抵消项**。

- **1. 递推关系 (Recurrence Relation)**
    - 斐波那契数列的定义是：$F_n = F_{n-1} + F_{n-2}$。
    - **变形 (Rearrangement)：** 为了求和，我们经常把这个公式写成减法的形式，用来抵消中间项。
    - 变形一：$F_{n-2} = F_n - F_{n-1}$
    - 变形二：$F_{n-1} = F_n - F_{n-2}$

- **2. 逐项抵消法 / 裂项相消法 (Telescoping Sum)**
    - 这是大学数学处理级数 (Series) 求和最常用的技巧。
    - **原理：** 如果你能把每一项 $a_i$ 写成两个连续项的差（例如 $a_i = b_{i+1} - b_i$），那么当你把它们加起来时：
    - $(b_1 - b_0) + (b_2 - b_1) + (b_3 - b_2) + \dots$
    - 你会发现中间的项全部“自杀”了，只剩下开头和结尾。

- **3. 初始条件 (Initial Conditions)**
    - 必须牢记：$F_0 = 0, F_1 = 1, F_2 = 1, F_3 = 2, \dots$

---

#### ③ 问题 1 的解答思路与逻辑链条 (Logic Chain for $S_n^1$)

我们要计算 $S_n^1 = \sum_{i=0}^n F_i$。

- **逻辑链条：**
    - 目标：求 $F_0 + F_1 + \dots + F_n$
    - 利用递推公式变形：$F_i = F_{i+2} - F_{i+1}$ (这是由 $F_{i+2} = F_{i+1} + F_i$ 移项得到的)
    - 将每一项都替换掉：
        - $F_0 = F_2 - F_1$
        - $F_1 = F_3 - F_2$
        - $F_2 = F_4 - F_3$
        - ...
        - $F_n = F_{n+2} - F_{n+1}$
    - 全部相加：中间的 $F_2, F_3, \dots, F_{n+1}$ 全部抵消 (Telescoping)
    - 结果：只剩下 $F_{n+2} - F_1$
    - 代入已知值：$F_1 = 1$
    - 最终结论：$S_n^1 = F_{n+2} - 1$

---

#### ④ 问题 1 的考试答题卡风格解答 (Exam-Style Solution for $S_n^1$)

**Solution:**

- **Step 1: Use the recurrence relation (利用递推关系):**
    - From $F_{k+2} = F_{k+1} + F_k$, we can rewrite each term as:
    - $F_k = F_{k+2} - F_{k+1}$

- **Step 2: Expand the sum (展开求和式):**
    - $S_n^1 = \sum_{k=0}^n F_k = F_0 + F_1 + F_2 + \dots + F_n$
    - $S_n^1 = (F_2 - F_1) + (F_3 - F_2) + (F_4 - F_3) + \dots + (F_{n+2} - F_{n+1})$

- **Step 3: Apply Telescoping Sum property (应用逐项抵消性质):**
    - Notice that $F_2$ cancels with $-F_2$, $F_3$ cancels with $-F_3$, and so on.
    - The sum simplifies to:
    - $S_n^1 = F_{n+2} - F_1$

- **Step 4: Substitute initial conditions (代入初始条件):**
    - Since $F_1 = 1$, we have:
    - $S_n^1 = F_{n+2} - 1$

---

#### ⑤ 问题 2 的解答思路与逻辑链条 (Logic Chain for $S_n^2$)

我们要计算偶数项的和 $S_n^2 = F_0 + F_2 + F_4 + \dots + F_{2n}$。

- **逻辑链条：**
    - 目标：求偶数下标项的和。
    - 寻找关联：偶数项 $F_{2i}$ 出现在哪些递推式里？
    - 利用递推公式变形：$F_{2i} = F_{2i+1} - F_{2i-1}$ (这是由 $F_{2i+1} = F_{2i} + F_{2i-1}$ 移项得到的)
    - 注意：$F_0$ 比较特殊，我们先把它拎出来。
    - 将其他项替换：
        - $F_2 = F_3 - F_1$
        - $F_4 = F_5 - F_3$
        - $F_6 = F_7 - F_5$
        - ...
        - $F_{2n} = F_{2n+1} - F_{2n-1}$
    - 全部相加：中间的奇数项 $F_3, F_5, \dots, F_{2n-1}$ 全部抵消 (Telescoping)
    - 结果：$F_0 + (F_{2n+1} - F_1)$
    - 代入已知值：$F_0 = 0, F_1 = 1$
    - 最终结论：$S_n^2 = F_{2n+1} - 1$

---

#### ⑥ 问题 2 的考试答题卡风格解答 (Exam-Style Solution for $S_n^2$)

**Solution:**

- **Step 1: Use the recurrence relation for odd indices (利用奇数下标的递推关系):**
    - We know $F_{2k+1} = F_{2k} + F_{2k-1}$, which implies:
    - $F_{2k} = F_{2k+1} - F_{2k-1}$

- **Step 2: Expand the sum for $k \ge 1$ (展开 $k \ge 1$ 的求和项):**
    - $S_n^2 = F_0 + \sum_{k=1}^n F_{2k}$
    - $S_n^2 = F_0 + (F_3 - F_1) + (F_5 - F_3) + (F_7 - F_5) + \dots + (F_{2n+1} - F_{2n-1})$

- **Step 3: Apply Telescoping Sum property (应用逐项抵消性质):**
    - The intermediate odd-indexed terms $F_3, F_5, \dots, F_{2n-1}$ cancel out.
    - The sum simplifies to:
    - $S_n^2 = F_0 + F_{2n+1} - F_1$

- **Step 4: Substitute initial conditions (代入初始条件):**
    - Given $F_0 = 0$ and $F_1 = 1$:
    - $S_n^2 = 0 + F_{2n+1} - 1 = F_{2n+1} - 1$

---

#### ⑦ 总结与规则 (Rules for Future Use)

**以后什么时候能用这个方法？**
- 1. **看到求和符号 ($\sum$) 或一长串加法：** 优先考虑能不能把每一项拆成两个连续项的差 (Difference of two consecutive terms)。
- 2. **看到斐波那契数求和：** 永远记住 $F_n = F_{n+2} - F_{n+1}$ 这个变形。
- 3. **边界检查 (Boundary Check)：** 抵消完之后，一定要检查剩下的是 $F_1$ 还是 $F_0$，这取决于你的求和是从 $0$ 开始还是从 $1$ 开始。在考试中，代入 $n=1$ 或 $n=2$ 验算一下结果是否符合常识是非常稳妥的工科做法。

# Q10
#### ① 题目翻译 (Problem Translation)

证明递推公式 (Recursion Formula) $r_n = \sum_{k=1}^n r_{k-1}r_{n-k}$ 可以推导出显式表达 (Explicit Form) $r_n = \frac{1}{n+1} \binom{2n}{n}$，其中初始条件为 $r_0 = 1$。这个数列被称为第 $n$ 个卡特兰数 (n-th Catalan number)。

提示：使用生成函数 (Generating Function) 进行证明，并学习如何展开分数次幂的二项式 (Fractional Binomials) 以及分数二项式系数 (Fractional Binomial Coefficients)。

---

#### ② 背景条件与基本概念解释 (Background & Concepts)

这道题是组合数学中的经典问题。对于工科思维来说，最重要的是理解“卷积”如何变成“平方”。

- **1. 卷积 (Convolution)**
    - 题目中的求和式 $\sum_{k=1}^n r_{k-1}r_{n-k}$ 在数学上被称为**卷积**。
    - **直观理解：** 想象你有两个完全一样的序列 $R$。当你把这两个序列对应的函数相乘时，乘积的系数正好就是这种“头尾相碰”的求和形式。
    - **规则：** 如果 $R(x) = \sum r_n x^n$，那么 $R(x) \cdot R(x)$ 的第 $n-1$ 项系数就是 $\sum_{k=0}^{n-1} r_k r_{n-1-k}$。

- **2. [[广义二项式定理 (Generalized Binomial Theorem)]]
    - 高中我们学过 $(a+b)^n$ 当 $n$ 是正整数的情况。
    - 在大学数学中，当幂次是分数（比如 $1/2$）时，公式变为：
        - $(1+z)^\alpha = \sum_{n=0}^{\infty} \binom{\alpha}{n} z^n$
    - 这里的 $\binom{\alpha}{n}$ 叫做**广义二项式系数**，计算公式是：
        - $\binom{\alpha}{n} = \frac{\alpha(\alpha-1)(\alpha-2)\dots(\alpha-n+1)}{n!}$
        - 高中时，我们要求幂次$n$必须是 **正整数 (Positive Integer)**。

- **3. 生成函数 (Generating Function)**
    - 我们把整个数列 $\{r_n\}$ 打包成一个函数 $R(x) = r_0 + r_1 x + r_2 x^2 + \dots$。

---

#### ③ 解题思路与逻辑链条 (Logic Chain)

我们要通过“打包 -> 解方程 -> 拆包”的过程来解题。

- **逻辑链条：**
    - **Step 1: 定义生成函数** $\rightarrow$ 建立数列与函数 $R(x)$ 的联系。
    - **Step 2: 观察递推式的结构** $\rightarrow$ 发现右边的求和式其实是 $R(x)$ 自己乘自己（卷积性质 Convolution Property）。
    - **Step 3: 建立函数方程** $\rightarrow$ 将递推式 $r_n = \dots$ 转换成关于 $R(x)$ 的二次方程。
    - **Step 4: 解二次方程** $\rightarrow$ 得到 $R(x)$ 的闭式解 (Closed Form)。
    - **Step 5: 筛选合理的根** $\rightarrow$ 根据初始条件 $r_0=1$ 排除掉不符合物理意义的解。
    - **Step 6: 泰勒展开 (Taylor Expansion)** $\rightarrow$ 利用广义二项式定理把函数重新拆解成级数。
    - **Step 7: 提取系数 (Extract Coefficient)** $\rightarrow$ 比较 $x^n$ 前面的系数，得出 $r_n$ 的通项公式。

---

#### ④ 考试答题卡风格解答 (Exam-Style Solution)

**Solution:**

- **1. Define the Generating Function (定义生成函数):**
    - Let $R(x) = \sum_{n=0}^{\infty} r_n x^n = r_0 + r_1 x + r_2 x^2 + \dots$
    - Given $r_0 = 1$.

- **2. Transform the Recurrence into an Equation (转化递推式):**
    - The given recurrence is $r_n = \sum_{k=1}^n r_{k-1}r_{n-k}$ for $n \ge 1$.
    - Consider the square of the generating function:
        - $R(x)^2 = (\sum_{i=0}^{\infty} r_i x^i)(\sum_{j=0}^{\infty} r_j x^j) = \sum_{n=0}^{\infty} (\sum_{k=0}^n r_k r_{n-k}) x^n$
    - Notice that the sum in the recurrence $\sum_{k=1}^n r_{k-1}r_{n-k}$ is exactly the coefficient of $x^{n-1}$ in $R(x)^2$.
    - Therefore, we can write:
        - $R(x) = r_0 + \sum_{n=1}^{\infty} r_n x^n = 1 + x \cdot R(x)^2$

- **3. Solve the Quadratic Equation (解二次方程):**
    - We have $x R(x)^2 - R(x) + 1 = 0$.
    - Using the quadratic formula (求根公式):
        - $R(x) = \frac{-(-1) \pm \sqrt{(-1)^2 - 4(x)(1)}}{2x} = \frac{1 \pm \sqrt{1-4x}}{2x}$

- **4. Choose the Correct Root (选择合适的根):**
    - As $x \to 0$, $R(x)$ should approach $r_0 = 1$.
    - If we take the positive root ($+$), $R(x) \to \infty$ as $x \to 0$.
    - If we take the negative root ($-$), using L'Hôpital's rule or expansion:
        - $\lim_{x \to 0} \frac{1 - \sqrt{1-4x}}{2x} = \lim_{x \to 0} \frac{1 - (1 - 2x + \dots)}{2x} = 1$.
    - Thus, $R(x) = \frac{1 - \sqrt{1-4x}}{2x}$.

- **5. Expand using Generalized Binomial Theorem (展开函数):**
    - We need the coefficient of $x^n$ in $R(x)$, which is the coefficient of $x^{n+1}$ in $\frac{1}{2}(1 - (1-4x)^{1/2})$.
    - Using $(1+z)^\alpha = \sum \binom{\alpha}{k} z^k$ with $\alpha = 1/2$ and $z = -4x$:
        - $(1-4x)^{1/2} = \sum_{k=0}^{\infty} \binom{1/2}{k} (-4x)^k$
    - The coefficient of $x^{n+1}$ in $\sqrt{1-4x}$ is $\binom{1/2}{n+1} (-4)^{n+1}$.

- **6. Final Calculation (最终推导):**
    - $r_n = -\frac{1}{2} \binom{1/2}{n+1} (-4)^{n+1}$
    - After simplifying the combination formula (see details below):
    - $r_n = \frac{1}{n+1} \binom{2n}{n}$

---

#### ⑤ 关键推导步骤详解 (Detailed Derivation of the "Why")

你可能会困惑：**那个复杂的组合数是怎么变出来的？** 这是最基础的代数化简技巧：

- **1. 展开广义组合数 $\binom{1/2}{n+1}$:**
    - $\binom{1/2}{n+1} = \frac{(1/2)(1/2-1)(1/2-2)\dots(1/2-n)}{(n+1)!}$
    - 分子有 $n+1$ 项。提取出所有的 $1/2$：
    - $= \frac{1}{2^{n+1}} \cdot \frac{1 \cdot (-1) \cdot (-3) \cdot \dots \cdot (1-2n)}{(n+1)!}$
    - 提取出负号：$= \frac{(-1)^n}{2^{n+1}} \cdot \frac{1 \cdot 3 \cdot 5 \cdot \dots \cdot (2n-1)}{(n+1)!}$

- **2. 处理双阶乘 (Double Factorial):**
    - $1 \cdot 3 \cdot 5 \cdot \dots \cdot (2n-1)$ 可以写成 $\frac{(2n)!}{2^n \cdot n!}$。
    - **原理：** 把 $(2n)!$ 中偶数项 $2, 4, 6 \dots 2n$ 提出来（即 $2^n \cdot n!$），剩下的就是奇数项。

- **3. 代回 $r_n$ 公式:**
    - $r_n = -\frac{1}{2} \cdot \left[ \frac{(-1)^n}{2^{n+1}} \cdot \frac{(2n)!}{2^n \cdot n! (n+1)!} \right] \cdot (-1)^{n+1} 4^{n+1}$
    - 注意符号：$(-1) \cdot (-1)^n \cdot (-1)^{n+1} = (-1)^{2n+2} = 1$（负号全部抵消了）。
    - 注意常数：$\frac{1}{2} \cdot \frac{1}{2^{n+1}} \cdot \frac{1}{2^n} \cdot 4^{n+1} = \frac{4^{n+1}}{2^{2n+2}} = \frac{4^{n+1}}{4^{n+1}} = 1$（常数全部抵消了）。
    - 剩下的项：$r_n = \frac{(2n)!}{n! (n+1)!} = \frac{1}{n+1} \cdot \frac{(2n)!}{n! n!} = \frac{1}{n+1} \binom{2n}{n}$。

**以后什么时候能用这个方法？**
- 1. **看到卷积形式的递推：** 只要看到 $a_n = \sum a_k a_{n-k}$ 这种形式，立刻想到生成函数的平方 $A(x)^2$。
- 2. **看到根号形式的生成函数：** 立刻准备使用广义二项式定理进行展开。
- 3. **处理组合数化简：** 记住把奇数相乘（双阶乘）转化为全阶乘除以偶数项的技巧。



