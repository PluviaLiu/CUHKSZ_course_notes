针对你提到的这几种形式，展开成 [[劳伦级数 (Laurent Series)]] 的核心逻辑其实就是“套公式”加上“变量代换”。作为工科思维者，你不需要去推导这些公式，你只需要把它们当成“标准零件”，然后学会如何把复杂的题目拆解成这些零件。

以下是详细的展开指南：

#### 1. 任务拆解：三大标准零件 (Task Breakdown: Three Standard Components)

在复分析中，你只需要死记硬背住以下三个“母公式”，所有的展开题都是由它们变形而来的：

- **零件 A：[[等比级数 (Geometric Series)]]**（最常用，处理分式）
    - $\frac{1}{1-w} = 1 + w + w^2 + w^3 + \dots = \sum_{n=0}^{\infty} w^n$ （条件：$|w| < 1$）
- **零件 B：[[指数函数 (Exponential Function)]]**（处理 $e$ 的次方）
    - $e^w = 1 + w + \frac{w^2}{2!} + \frac{w^3}{3!} + \dots = \sum_{n=0}^{\infty} \frac{w^n}{n!}$
- **零件 C：[[三角函数 (Trigonometric Functions)]]**（处理 $\sin$ 和 $\cos$）
    - $\sin w = w - \frac{w^3}{3!} + \frac{w^5}{5!} - \dots$
    - $\cos w = 1 - \frac{w^2}{2!} + \frac{w^4}{4!} - \dots$

---

#### 2. 背景条件与基本概念 (Background & Concepts)

- [[泰勒展开 (Taylor Expansion)]]
    - **解释**：这是在“好点”（解析点）附近的展开，只有正幂次。上述三个母公式在 $w=0$ 处都是泰勒展开。
- [[收敛半径 (Radius of Convergence)]]
    - **解释**：公式有效的范围。对于 $e^w, \sin w, \cos w$，它们在全平面都有效；但对于等比级数 $\frac{1}{1-w}$，必须满足 $|w| < 1$。

---

#### 3. 逻辑链条：如何具体操作 (Logic Chains for Expansion)

#### 等比级数形式 (Geometric Form) —— “强行凑 1 法”
**场景**：看到分式，如 $\frac{1}{z-2}$，且要在 $z=0$ 以外的点展开。这是最难的，也是考试最常考的。

- **逻辑链条（以 $f(z) = \frac{1}{z}$ 在 $z=1$ 处展开为例）：**
    - ● 目标：中心是 $z=1$，所以我们要凑出 $(z-1)$ 这个整体。
    - ● 令 $w = z-1$ $\rightarrow$ 则 $z = w+1$。
    - ● 代入原式 $\rightarrow$ $f(z) = \frac{1}{1+w}$。
    - ● 匹配母公式 $\rightarrow$ 母公式是 $\frac{1}{1-w}$，我们现在是 $\frac{1}{1-(-w)}$。
    - ● 变量代换 $\rightarrow$ 把母公式里的 $w$ 换成 $-w$。
    - ● 展开 $\rightarrow$ $1 + (-w) + (-w)^2 + (-w)^3 + \dots = 1 - w + w^2 - w^3 + \dots$
    - ● 换回 $z$ $\rightarrow$ $1 - (z-1) + (z-1)^2 - (z-1)^3 + \dots$
    - ● **结论**：因为没有负幂次项，所以 $z=1$ 是该函数的解析点（泰勒展开）。

#### 3.4 强行提取法 (Forced Factoring) —— 处理 $|z| > R$ 的情况
**场景**：如果题目要求在区域 $|z| > 2$ 展开 $\frac{1}{z-2}$。

- **逻辑链条：**
    - ● 已知条件 $|z| > 2$ $\rightarrow$ 意味着 $|\frac{2}{z}| < 1$。
    - ● 核心规则 $\rightarrow$ 等比级数公式 $\frac{1}{1-w}$ 里的 $w$ 绝对值必须小于 1。
    - ● 变形技巧 $\rightarrow$ 我们必须在分母凑出 $\frac{2}{z}$。
    - ● **强行提取 (Forced Factoring)** $\rightarrow$ 从 $z-2$ 中强行提走 $z$。
    - ● 变形过程 $\rightarrow$ $\frac{1}{z-2} = \frac{1}{z(1 - \frac{2}{z})} = \frac{1}{z} \cdot \frac{1}{1 - \frac{2}{z}}$。
    - ● 套用公式 $\rightarrow$ 令 $w = \frac{2}{z}$，因为 $|w| < 1$，公式成立。
    - ● 展开 $\rightarrow$ $\frac{1}{z} \cdot (1 + \frac{2}{z} + (\frac{2}{z})^2 + \dots) = \frac{1}{z} + \frac{2}{z^2} + \frac{4}{z^3} + \dots$
    - ● **结论**：这就是在无穷远区域的劳伦展开。


- **看到分式 $\frac{1}{A-B}$**：
    - 1. 确定展开中心 $z_0$。
    - 2. 如果 $z_0 \neq 0$，先做代换 $w = z-z_0$。
    - 3. 观察区域：
        - 如果是“小区域”（靠近中心），把常数提出来，凑出 $\frac{1}{1 - (\text{变量}/\text{常数})}$。
        - 如果是“大区域”（远离中心），把变量提出来，凑出 $\frac{1}{1 - (\text{常数}/\text{变量})}$。
