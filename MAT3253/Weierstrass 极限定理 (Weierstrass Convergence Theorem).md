- **定理陈述 (Formal Statement)**
    - 设 $\{f_k(z)\}$ 是区域 $D$ 内的一列全纯函数。
    - 若 $\{f_k(z)\}$ 在 $D$ 上内闭一致收敛 (Locally Uniformly Convergent) 于 $f(z)$。
    - 则：
        1. 极限函数 $f(z)$ 在 $D$ 内也是全纯的。
        2. 导数序列 $\{f_k'(z)\}$ 在 $D$ 上也内闭一致收敛于 $f'(z)$。
        3. 即：$f'(z) = \lim_{k \to \infty} f_k'(z)$。


**Claim**: 若 $\{f_k\}$ 为区域 $D$ 上的全纯函数序列，且在 $D$ 上内闭一致收敛于 $f$，则：
1.  **全纯性保持**: 极限函数 $f$ 在 $D$ 上亦为全纯函数。
2.  **导数收敛性**: 导数序列 $\{f_k'\}$ 在 $D$ 上内闭一致收敛于 $f'$。

#### 3. 证明逻辑：Cauchy 积分公式的刚性
该定理的核心在于复分析的“刚性”。其证明逻辑如下：

*   **Step 1: 局部积分表示**
    对于任意点 $z_0 \in D$，选取以 $z_0$ 为圆心的闭圆盘 $\overline{B}(z_0, r) \subset D$。由 Cauchy 积分公式，对任意 $z \in B(z_0, r)$，有：
    $$f_k(z) = \frac{1}{2\pi i} \oint_{\partial B} \frac{f_k(\zeta)}{\zeta - z} d\zeta$$
*   **Step 2: 取极限**
    由于 $\{f_k\}$ 在 $\partial B$ 上一致收敛于 $f$，根据积分与极限交换定理（Uniform Convergence Theorem for Integrals），可得：
    $$f(z) = \lim_{k \to \infty} f_k(z) = \frac{1}{2\pi i} \oint_{\partial B} \frac{f(\zeta)}{\zeta - z} d\zeta$$
    此式表明 $f$ 在 $B(z_0, r)$ 内由 Cauchy 积分表示，故 $f$ 在 $z_0$ 处解析（全纯）。
*   **Step 3: 导数收敛**
    利用 Cauchy 导数公式：
    $$f_k'(z) = \frac{1}{2\pi i} \oint_{\partial B} \frac{f_k(\zeta)}{(\zeta - z)^2} d\zeta$$
    同理，由于 $f_k \to f$ 一致收敛，积分项趋于 $f'(z)$，从而保证了 $\{f_k'\}$ 的一致收敛性。

- **为什么实分析中不成立？(Remark: The Real Analysis Counterexample)**
    - 老师提到的“Remark”非常关键。在实分析中，考虑 $f_n(x) = \frac{\sin(nx)}{\sqrt{n}}$。
    - 当 $n \to \infty$ 时，$f_n(x) \to 0$（一致收敛）。
    - 但是，其导数 $f_n'(x) = \sqrt{n} \cos(nx)$ 在 $n \to \infty$ 时会剧烈震荡，根本不收敛。
    - **结论**：实分析中，一致收敛无法控制导数的行为。

- **为什么复分析中成立？(The "Rigidity" of Holomorphic Functions)**
    - **Cauchy 积分公式的威力**：
        - 复分析中，函数值 $f(z)$ 和导数 $f'(z)$ 是通过积分公式紧密耦合的：
            $$f'(z) = \frac{1}{2\pi i} \oint_{\gamma} \frac{f(\zeta)}{(\zeta - z)^2} d\zeta$$
        - 因为积分号下的一致收敛允许我们交换极限与积分的顺序，所以导数序列的收敛性是“免费”得到的。
