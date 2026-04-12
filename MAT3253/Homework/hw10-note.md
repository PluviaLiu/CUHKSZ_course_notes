# Q1

#### 1. 题目翻译与核心概念
- **题目翻译**：
    - 证明一个类似于定理 11.1.2 的结论，即将路径 $C_1$ 替换为一个矩形（rectangle）。
    - 设 $C_1$ 是矩形区域 $[a, b] \times [c, d]$ 的边界（boundary），$C_2$ 是位于该矩形内部的一个圆周（circle）的边界。两者均取逆时针方向（counter-clockwise orientation）。对于一个在矩形区域内全纯（holomorphic）的函数 $f(z)$，证明 $\int_{C_1} f(z) dz = \int_{C_2} f(z) dz$。

- **核心概念解析**：
    - **全纯函数 (Holomorphic function)**：指在复平面（complex plane）的某个开集（open set）内处处可导（differentiable）的函数。这是复分析（Complex Analysis）的基石。
    - [[轮廓变形原理 (Deformation of contour)]]：这是复分析中处理积分的核心思想。如果函数在两条闭合路径（closed curve）之间的区域内是全纯的，那么在这两条路径上的积分值相等。
    - **柯西积分定理 (Cauchy's Integral Theorem)**：这是证明的核心。它指出，如果一个函数在简单闭合曲线（simple closed curve）及其内部是全纯的，那么该函数沿此闭合曲线的积分为 0。

#### 2. 逻辑链条拆解（证明过程）
为了证明 $\int_{C_1} f(z) dz = \int_{C_2} f(z) dz$，我们采用“切割法”（cut method）将复杂的区域转化为柯西积分定理适用的简单区域。

- **步骤 1：构造辅助路径 (Construct auxiliary paths)**
    - 在外边界 $C_1$ 和内边界 $C_2$ 之间添加两条线段（cross-cuts），记为 $L_1$ 和 $L_2$。
    - 逻辑：通过这两条线，我们将原本的“环形区域”（annular-like region）切割成了两个简单的子区域 $R_1$ 和 $R_2$。
    - 此时，我们得到了两个闭合回路（closed loops）：$\Gamma_1$ 和 $\Gamma_2$。

- **步骤 2：应用柯西积分定理 (Apply Cauchy's Integral Theorem)**
    - 因为 $f(z)$ 在 $R_1$ 和 $R_2$ 内部及边界上是全纯的（holomorphic）。
    - 根据柯西积分定理：$\oint_{\Gamma_1} f(z) dz = 0$ 且 $\oint_{\Gamma_2} f(z) dz = 0$。
    - 逻辑：因为函数在这些子区域内没有“坏点”（奇点 singularity），所以闭合路径积分为 0。

- **步骤 3：路径相加与抵消 (Summation and cancellation)**
    - 将两个积分相加：$\oint_{\Gamma_1} f(z) dz + \oint_{\Gamma_2} f(z) dz = 0$。
    - 观察路径构成：
        - 外边界 $C_1$（逆时针）。
        - 内边界 $C_2$（在回路中因为方向相反，实际上是顺时针，记为 $-C_2$）。
        - 连接线 $L_1$ 和 $L_2$（在 $\Gamma_1$ 中是 $L_1$，在 $\Gamma_2$ 中是 $-L_1$）。
    - 逻辑：根据积分的线性性质（linearity of integration），$\int_{L_1} f(z) dz + \int_{-L_1} f(z) dz = 0$。连接线上的积分相互抵消。

- **步骤 4：得出结论 (Conclusion)**
    - 剩下的部分就是外边界 $C_1$ 的积分和内边界 $C_2$ 的积分。
    - $\int_{C_1} f(z) dz + \int_{-C_2} f(z) dz = 0$。
    - 移项得：$\int_{C_1} f(z) dz = \int_{C_2} f(z) dz$。

#### 3. 总结与应用场景
- **何时使用**：当你需要计算一个复杂路径的积分，但该路径内部包含一个“坏点”（奇点）时，你可以将路径变形为一个简单的圆周（通常是单位圆），只要变形过程中不穿过“坏点”，积分值就不变。
- **核心逻辑总结**：
    - 区域内全纯（Holomorphic in region） $\rightarrow$ 柯西积分定理适用（Cauchy's Theorem applies）。
    - 闭合路径积分和为 0（Sum of closed loop integrals is 0） $\rightarrow$ 路径变形积分不变（Deformation of contour preserves integral value）。
    - 只要起点和终点相同（闭合路径），且中间不跨越奇点，积分结果就由柯西定理保证相等。

# Q2：如何利用[[柯西积分公式 (Cauchy's Integral Formula)]]计算路径积分

这道题的核心在于利用[[轮廓变形原理 (Deformation of Contour)]]，将复杂的方形路径 $C$ 变形为围绕奇点（singularity）的微小圆周，然后应用[[柯西积分定理 (Cauchy's Integral Theorem)]]进行计算。

#### 1. 题目翻译与核心概念
- **题目翻译**：利用上一题的变形定理和圆周的柯西积分公式，计算给定积分。$C$ 是正方形边界，由 $x = \pm 2$ 和 $y = \pm 2$ 围成，方向为逆时针（positively oriented）。
- **核心概念解析**：
    - [[柯西积分公式 (Cauchy's Integral Formula)]]：
        - 基础形式：$f(z_0) = \frac{1}{2\pi i} \oint_C \frac{f(z)}{z - z_0} dz$，即 $\oint_C \frac{f(z)}{z - z_0} dz = 2\pi i f(z_0)$。
        - 导数形式：$f^{(n)}(z_0) = \frac{n!}{2\pi i} \oint_C \frac{f(z)}{(z - z_0)^{n+1}} dz$。
    - **奇点 (Singularity)**：分母为 0 的点。积分值取决于函数在这些点处的取值或导数。
    - [[正向边界（positively oriented boundary）]]

#### 2. 逻辑链条拆解与解答

对于所有题目，逻辑步骤统一为：
1. 找出被积函数分母为 0 的点（奇点）。
2. 判断奇点是否在正方形 $C$ 内部（$|x|<2, |y|<2$）。
3. 若在内部，将路径 $C$ 变形为围绕该奇点的小圆周，套用公式。

#### (a) $\int_C \frac{e^{-z}}{z - (\pi i/2)} dz$
- 奇点：$z_0 = \pi i/2 \approx 1.57i$。因为 $|1.57i| < 2$，奇点在正方形内。
- 逻辑：令 $f(z) = e^{-z}$。
- 计算：根据柯西积分公式，结果为 $2\pi i \cdot f(\pi i/2) = 2\pi i \cdot e^{-\pi i/2}$。
- 因为 $e^{-\pi i/2} = \cos(-\pi/2) + i\sin(-\pi/2) = -i$。
- 结果：$2\pi i \cdot (-i) = 2\pi$。

#### (b) $\int_C \frac{\cos z}{z(z^2 + 8)} dz$
- 奇点：$z_0 = 0, z_1 = \sqrt{-8} = 2\sqrt{2}i, z_2 = -2\sqrt{2}i$。
- 判断：$|2\sqrt{2}i| \approx 2.82 > 2$，所以只有 $z_0 = 0$ 在正方形内。
- 逻辑：令 $f(z) = \frac{\cos z}{z^2 + 8}$。
- 计算：$\oint_C \frac{f(z)}{z - 0} dz = 2\pi i \cdot f(0) = 2\pi i \cdot \frac{\cos 0}{0^2 + 8} = 2\pi i \cdot \frac{1}{8} = \frac{\pi i}{4}$。

#### (c) $\int_C \frac{z}{2z + 1} dz$
- 变形：分母提取系数 $2$，变为 $\frac{1}{2} \int_C \frac{z}{z - (-1/2)} dz$。
- 奇点：$z_0 = -1/2$。在正方形内。
- 逻辑：令 $f(z) = z$。
- 计算：$\frac{1}{2} \cdot [2\pi i \cdot f(-1/2)] = \frac{1}{2} \cdot 2\pi i \cdot (-1/2) = -\frac{\pi i}{2}$。


#### (d) $\int_C \frac{\cosh z}{z^4} dz$
- 奇点：$z_0 = 0$（四阶极点）。
- 逻辑：使用导数形式的柯西积分公式：$\oint_C \frac{f(z)}{(z-z_0)^{n+1}} dz = \frac{2\pi i}{n!} f^{(n)}(z_0)$。
- 这里 $n=3, f(z) = \cosh z$。
- 计算：$f'(z) = \sinh z, f''(z) = \cosh z, f'''(z) = \sinh z$。
- 结果：$\frac{2\pi i}{3!} \cdot f'''(0) = \frac{2\pi i}{6} \cdot \sinh(0) = 0$。

#### (e) $\int_C \frac{\tan(z/2)}{(z - x_0)^2} dz$
- 奇点：$z_0 = x_0$。题目给定 $-2 < x_0 < 2$，说明奇点在正方形内。
- 逻辑：使用导数形式，这里 $n=1, f(z) = \tan(z/2)$。
- 公式：$\oint_C \frac{f(z)}{(z-x_0)^2} dz = \frac{2\pi i}{1!} f'(x_0)$。
- 计算：$f'(z) = \frac{1}{2} \sec^2(z/2)$。
- 结果：$2\pi i \cdot \frac{1}{2} \sec^2(x_0/2) = \pi i \sec^2(x_0/2)$。

#### 3. 总结与考试技巧
- **定理边界**：如果奇点在路径 $C$ 外部，根据柯西积分定理，积分为 0。
- **工科思维总结**：
    - 看到分母有 $(z-z_0)^n$，立刻想到柯西积分公式。
    - 看到复杂的路径，先找奇点，再用变形原理将其简化为围绕奇点的小圆。
    - 只要函数在路径内部全纯（除了奇点），积分值就只由奇点处的函数值或导数决定。



# Q3
这道题是复分析（Complex Analysis）中非常经典的一个结论，它展示了全纯函数（holomorphic function）的“刚性”（rigidity）。

#### 1. 题目翻译与核心概念
- **题目翻译**：
    - 假设 $f(z)$ 是整函数（entire function），且其实部（real part）$u(x, y) = \text{Re}(f(z))$ 有一个上界（upper bound）$u_0$；也就是说，对于平面上所有的点 $(x, y)$，都有 $u(x, y) \leq u_0$。证明 $u(x, y)$ 在整个平面上必须是常数（constant）。
    - 提示（Hint）：将刘维尔定理（Liouville's Theorem）应用于 $\exp(f(z))$。

- **核心概念解析**：
    - [[整函数 (Entire function)]]：指在整个复平面（complex plane）上处处全纯（holomorphic）的函数。例如多项式（polynomials）、指数函数（exponential function）$e^z$、正弦函数（sine）$\sin z$ 等。
    - [[刘维尔定理 (Liouville's Theorem)]]：这是复分析的核心定理之一。它指出：如果一个函数在整个复平面上是全纯的，且它是有界的（bounded），那么这个函数一定是一个常数。
    - [[指数函数 (Exponential function)]]：$\exp(f(z)) = e^{f(z)} = e^{u+iv} = e^u \cdot e^{iv}$。

#### 2. 逻辑链条拆解
我们要证明 $u$ 是常数，根据提示，我们构造一个新函数 $g(z) = \exp(f(z))$，并证明它满足刘维尔定理的条件。

- **步骤 1：构造辅助函数 (Construct auxiliary function)**
    - 令 $g(z) = \exp(f(z))$。
    - 因为 $f(z)$ 是整函数（entire），且指数函数（exponential function）也是整函数，根据复合函数性质（composition of holomorphic functions），$g(z)$ 也是整函数。

- **步骤 2：分析 $g(z)$ 的模长 (Analyze the modulus of $g(z)$)**
    - $g(z) = e^{f(z)} = e^{u+iv} = e^u \cdot e^{iv}$。
    - 取模长（modulus）：$|g(z)| = |e^u| \cdot |e^{iv}| = e^u \cdot 1 = e^u$。
    - 因为题目已知 $u \leq u_0$，所以 $e^u \leq e^{u_0}$。
    - 结论：$|g(z)|$ 是有界的（bounded）。

- **步骤 3：应用刘维尔定理 (Apply Liouville's Theorem)**
    - 条件：$g(z)$ 是整函数（entire）且是有界的（bounded）。
    - 定理：根据刘维尔定理，任何有界的整函数必须是常数。
    - 结论：$g(z) = \exp(f(z)) = C$（常数）。

- **步骤 4：反推 $u$ 的性质 (Deduce the property of $u$)**
    - 因为 $\exp(f(z)) = C$，两边取对数（logarithm）或直接分析：
    - $e^{u+iv} = C$。
    - 这意味着 $e^u$ 必须是常数（因为 $|C|$ 是常数）。
    - 如果 $e^u$ 是常数，那么 $u$ 必然是常数。
    - 结论：$u(x, y)$ 在整个平面上是常数。

#### 3. 考试答题卡风格的总结
在考试中，你可以按照以下逻辑书写：

- **Step 1 (Define)**：Define $g(z) = \exp(f(z))$. Since $f(z)$ is entire, $g(z)$ is also entire.
    - （定义 $g(z) = \exp(f(z))$。因为 $f(z)$ 是整函数，所以 $g(z)$ 也是整函数。）
- **Step 2 (Bound)**：The modulus is $|g(z)| = |e^{u+iv}| = e^u$. Given $u \leq u_0$, we have $|g(z)| \leq e^{u_0}$. Thus, $g(z)$ is bounded.
    - （模长为 $|g(z)| = e^u$。已知 $u \leq u_0$，所以 $|g(z)| \leq e^{u_0}$。因此，$g(z)$ 是有界的。）
- **Step 3 (Theorem)**：By Liouville's Theorem, an entire and bounded function must be constant. So $g(z) = C$.
    - （根据刘维尔定理，整且有界的函数必须是常数。所以 $g(z) = C$。）
- **Step 4 (Conclusion)**：Since $e^{u+iv} = C$, the real part $u$ must be constant.
    - （因为 $e^{u+iv} = C$，其实部 $u$ 必须是常数。）

#### 4. 为什么这个方法有效？
- **工科思维总结**：当你面对一个关于“实部有界”的证明题时，直接处理 $u$ 很难，因为 $u$ 只是函数的一部分。通过构造 $\exp(f(z))$，我们把“实部”转化为了“模长”，从而成功地把问题转化为了刘维尔定理的适用场景。
- **定理边界**：刘维尔定理只适用于“整函数”（entire function）。如果函数在某一点不全纯（例如 $1/z$），这个定理就不能用。所以题目中“$f(z)$ 是整函数”这个条件是整个逻辑链条的起点，缺一不可。

# Q4 


# Q5

# Q6
