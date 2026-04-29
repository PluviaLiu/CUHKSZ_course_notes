'- [ ] 完成MAT3253的HW13

# Q1
我来仔细拆解这道题目。

---

#### 1. 题目翻译与信息拆解

**原题翻译：**

> 第1题（Brown & Churchill 习题81.2）
> 在(a)、(b)、(c)三个小题中，使用**主支 (principal branch)** $0 < \text{Arg}(z) < 2\pi$ 来计算 $z$ 的分数次幂函数与对数函数。证明：
>
> (a) $\text{Res}\left(\dfrac{z^{1/4}}{z+1}; -1\right) = \dfrac{1+i}{\sqrt{2}}$
>
> (b) $\text{Res}\left(\dfrac{\text{Log}(z)}{(z^2+1)^2}; i\right) = \dfrac{\pi + 2i}{8}$
>
> (c) $\text{Res}\left(\dfrac{z^{1/2}}{(z^2+1)^2}; i\right) = \dfrac{1-i}{8\sqrt{2}}$

**题目给了我们什么：**

- **已知条件：** 使用主支 $0 < \text{Arg}(z) < 2\pi$（这决定了 $z^{1/4}$、$z^{1/2}$、$\text{Log}(z)$ 的取值方式）
- **要求做什么：** 分别计算三个函数在指定点处的**留数 (Residue)**，并验证等号成立

---

#### 2. 背景概念

**[[留数 (Residue)]]**

留数是劳伦展开 (Laurent expansion) 中 $\dfrac{1}{z - z_0}$ 项的系数，记作 $\text{Res}(f; z_0)$。

对于**极点 (pole)** 的留数计算，最常用两个公式：

- **简单极点 (simple pole)**，即一阶极点：

$$\text{Res}(f; z_0) = \lim_{z \to z_0} (z - z_0) f(z)$$

- **$m$ 阶极点 (pole of order $m$)**：

$$\text{Res}(f; z_0) = \frac{1}{(m-1)!} \lim_{z \to z_0} \frac{d^{m-1}}{dz^{m-1}} \left[(z-z_0)^m f(z)\right]$$

**[[主支 (Principal Branch)]]**

对于多值函数 (multi-valued function)，也就是给一个输入可以有多个输出的，比如 $z^{1/4}$ 或 $\text{Log}(z)$，我们需要**切支 (branch cut)** 来让它变成单值的。

题目规定 $0 < \text{Arg}(z) < 2\pi$，这意味着：

- 切支线 (branch cut) 是**正实轴 (positive real axis)**
- 任意 $z = re^{i\theta}$，其中 $\theta \in (0, 2\pi)$，则：
  - $z^{1/n} = r^{1/n} e^{i\theta/n}$
  - $\text{Log}(z) = \ln r + i\theta$

**[[分数次幂 (Fractional Power)]]**

在主支 $0 < \text{Arg}(z) < 2\pi$ 下：

$$z^{1/4} = r^{1/4} e^{i\theta/4}, \quad z^{1/2} = r^{1/2} e^{i\theta/2}$$

其中 $z = re^{i\theta}$，$\theta \in (0, 2\pi)$。

特别注意：**$(-1)$ 和 $i$ 用极坐标表示时，$\theta$ 的取值由主支决定。**

- $z = -1$：$r = 1$，在主支下 $\theta = \pi$，所以 $-1 = e^{i\pi}$
- $z = i$：$r = 1$，在主支下 $\theta = \pi/2$，所以 $i = e^{i\pi/2}$

---

#### 3. 解题思路（逐步逻辑链条）

---

**(a) $\text{Res}\left(\dfrac{z^{1/4}}{z+1}; -1\right)$**

● **判断极点阶数 (order of pole)**：

- 分母 $z+1$ 在 $z = -1$ 处有一个一阶零点 (simple zero)
- 分子 $z^{1/4}$ 在 $z = -1$ 处非零（因为 $(-1)^{1/4} \neq 0$）
- → 所以 $z = -1$ 是**简单极点 (simple pole)**，阶数为 1

● **用简单极点公式 (simple pole formula)**：

$$\text{Res}(f; -1) = \lim_{z \to -1}(z+1) \cdot \frac{z^{1/4}}{z+1} = \lim_{z \to -1} z^{1/4} = (-1)^{1/4}$$

● **计算 $(-1)^{1/4}$（关键步骤，用主支）**：

- $z = -1$，极坐标 (polar form)：$r = 1$，主支下 $\theta = \pi$
- 代入分数次幂公式：$(-1)^{1/4} = 1^{1/4} \cdot e^{i\pi/4} = e^{i\pi/4}$

● **化简 $e^{i\pi/4}$（用欧拉公式 Euler's formula）**：

$$e^{i\pi/4} = \cos\frac{\pi}{4} + i\sin\frac{\pi}{4} = \frac{\sqrt{2}}{2} + i\frac{\sqrt{2}}{2} = \frac{1+i}{\sqrt{2}}$$

● **结论：**

$$\text{Res}\left(\frac{z^{1/4}}{z+1}; -1\right) = \frac{1+i}{\sqrt{2}} \quad \checkmark$$

---

**(b) $\text{Res}\left(\dfrac{\text{Log}(z)}{(z^2+1)^2}; i\right)$**

● **判断极点阶数**：

- 分母 $(z^2+1)^2 = [(z-i)(z+i)]^2$，在 $z = i$ 处有**二阶零点 (zero of order 2)**
- 分子 $\text{Log}(i)$ 在 $z = i$ 处非零
- → $z = i$ 是**二阶极点 (pole of order 2)**

● **用二阶极点公式 (pole of order 2 formula)**：

$$\text{Res}(f; i) = \lim_{z \to i} \frac{d}{dz}\left[(z-i)^2 \cdot \frac{\text{Log}(z)}{(z^2+1)^2}\right]$$

- 注意到 $(z^2+1)^2 = (z-i)^2(z+i)^2$，所以：

$$(z-i)^2 \cdot \frac{\text{Log}(z)}{(z-i)^2(z+i)^2} = \frac{\text{Log}(z)}{(z+i)^2}$$

● **对 $g(z) = \dfrac{\text{Log}(z)}{(z+i)^2}$ 求导（用商法则 quotient rule）**：

$$g'(z) = \frac{\frac{1}{z}(z+i)^2 - \text{Log}(z) \cdot 2(z+i)}{(z+i)^4} = \frac{\frac{1}{z}(z+i) - 2\text{Log}(z)}{(z+i)^3}$$

● **代入 $z = i$（先算 $\text{Log}(i)$）**：
[[对数函数复数情况求导]]

- $z = i$，极坐标：$r = 1$，主支下 $\theta = \pi/2$
- $\text{Log}(i) = \ln 1 + i \cdot \frac{\pi}{2} = \frac{i\pi}{2}$

代入 $g'(i)$：

$$g'(i) = \frac{\frac{1}{i}(i+i) - 2 \cdot \frac{i\pi}{2}}{(i+i)^3} = \frac{\frac{1}{i} \cdot 2i - i\pi}{(2i)^3}$$

- 分子：$\dfrac{1}{i} \cdot 2i = 2$，所以分子 $= 2 - i\pi$
- 分母：$(2i)^3 = 8i^3 = 8(-i) = -8i$

$$g'(i) = \frac{2 - i\pi}{-8i}$$

● **化简（分子分母乘以 $i$ 来消去 $-8i$）**：

$$\frac{2 - i\pi}{-8i} \cdot \frac{i}{i} = \frac{2i - i^2\pi}{-8i^2} = \frac{2i + \pi}{8} = \frac{\pi + 2i}{8}$$

● **结论：**

$$\text{Res}\left(\frac{\text{Log}(z)}{(z^2+1)^2}; i\right) = \frac{\pi + 2i}{8} \quad \checkmark$$

---

**(c) $\text{Res}\left(\dfrac{z^{1/2}}{(z^2+1)^2}; i\right)$**

● **判断极点阶数**：

- 与 (b) 完全一样的分母结构，$z = i$ 是**二阶极点 (pole of order 2)**

● **用二阶极点公式**，化简得需要对 $h(z) = \dfrac{z^{1/2}}{(z+i)^2}$ 求导：

$$h'(z) = \frac{\frac{1}{2}z^{-1/2}(z+i)^2 - z^{1/2} \cdot 2(z+i)}{(z+i)^4} = \frac{\frac{1}{2}z^{-1/2}(z+i) - 2z^{1/2}}{(z+i)^3}$$

● **代入 $z = i$（先算 $i^{1/2}$）**：

- $z = i$，极坐标：$r = 1$，主支下 $\theta = \pi/2$
- $i^{1/2} = e^{i\pi/4} = \dfrac{1+i}{\sqrt{2}}$（与 (a) 中 $(-1)^{1/4}$ 同理）

- $i^{-1/2} = e^{-i\pi/4} = \cos\frac{\pi}{4} - i\sin\frac{\pi}{4} = \dfrac{1-i}{\sqrt{2}}$

代入 $h'(i)$（分母 $(i+i)^3 = (2i)^3 = -8i$）：

分子：

$$\frac{1}{2} \cdot \frac{1-i}{\sqrt{2}} \cdot (2i) - 2 \cdot \frac{1+i}{\sqrt{2}}$$

$$= \frac{(1-i)i}{\sqrt{2}} - \frac{2(1+i)}{\sqrt{2}}$$

$$= \frac{i - i^2}{\sqrt{2}} - \frac{2+2i}{\sqrt{2}}$$

$$= \frac{i+1}{\sqrt{2}} - \frac{2+2i}{\sqrt{2}}$$

$$= \frac{1+i - 2 - 2i}{\sqrt{2}} = \frac{-1-i}{\sqrt{2}}$$

● **整合，计算留数**：

$$h'(i) = \frac{\frac{-1-i}{\sqrt{2}}}{-8i} = \frac{-1-i}{-8i\sqrt{2}} = \frac{1+i}{8i\sqrt{2}}$$

● **化简（乘以 $\dfrac{i}{i}$ 消去分母中的 $i$）**：

$$\frac{1+i}{8i\sqrt{2}} \cdot \frac{i}{i} = \frac{(1+i)i}{8i^2\sqrt{2}} = \frac{i+i^2}{-8\sqrt{2}} = \frac{i-1}{-8\sqrt{2}} = \frac{1-i}{8\sqrt{2}}$$

● **结论：**

$$\text{Res}\left(\frac{z^{1/2}}{(z^2+1)^2}; i\right) = \frac{1-i}{8\sqrt{2}} \quad \checkmark$$

---

#### 4. 核心逻辑总结（可复用规则）

- **遇到留数 (Residue) 问题 →** 先判断极点阶数 (order of pole)
  - 一阶极点 → 直接用极限公式
  - $m$ 阶极点 → 先消掉 $(z-z_0)^m$，再求 $m-1$ 阶导数，最后取极限
- **遇到分数次幂或 Log 的取值 →** 必须用主支 (principal branch) 转换成极坐标 $re^{i\theta}$，$\theta \in (0, 2\pi)$
- **化简复数分式 →** 分子分母同乘 $i$ 或共轭，消去虚数单位
# Q2
我来仔细拆解这道题目。

---

#### 1. 题目翻译与信息拆解

**原题翻译：**

> 第2题（Brown & Churchill 习题81.4）
> 求积分的值：
> $$\oint_C \frac{3z^3 + 2}{(z-1)(z^2+9)} \, dz$$
> 沿以下圆周**逆时针 (counterclockwise)** 方向积分：
> (a) $|z - 2| = 2$；(b) $|z| = 4$

**题目给了我们什么：**

- 被积函数 (integrand)：$\dfrac{3z^3+2}{(z-1)(z^2+9)}$
- 两条不同的围道 (contour)，形状都是圆，但大小位置不同
- 要求我们分别计算两种情况下的积分值

---

#### 2. 背景概念

**[[留数定理 (Residue Theorem)]]**

$$\oint_C f(z)\,dz = 2\pi i \sum \text{Res}(f; z_k)$$

意思是：沿围道 $C$ 的积分 $=$ $2\pi i$ 乘以**所有在 $C$ 内部的奇点 (singularity) 的留数之和**。

条件：$C$ 是简单闭合曲线 (simple closed curve)，逆时针方向。

**[[奇点 (Singularity) 的位置判断]]**

先找出被积函数所有的极点 (pole)，即让分母为零的点：

- $(z-1) = 0 \Rightarrow z = 1$
- $(z^2 + 9) = 0 \Rightarrow z = \pm 3i$

所以一共有**三个极点 (pole)**：

$$z_1 = 1, \quad z_2 = 3i, \quad z_3 = -3i$$

每个都是**简单极点 (simple pole)**（分母每个因子都是一次方）。

**[[围道 (Contour) 的判断]]**

- $|z - 2| = 2$：以 $z = 2$ 为圆心，半径为 $2$ 的圆
- $|z| = 4$：以原点为圆心，半径为 $4$ 的圆

判断哪些极点在圆的**内部**，就看极点到圆心的距离是否**小于**半径。

**[[简单极点的留数公式 (Residue Formula for Simple Pole)]]**

当分母可以写成 $g(z) = (z - z_0) \cdot h(z)$，且 $h(z_0) \neq 0$ 时：

$$\text{Res}(f; z_0) = \lim_{z \to z_0} (z - z_0) f(z) = \frac{\text{分子在} z_0 \text{的值}}{\text{其余分母在} z_0 \text{的值}}$$

即：

$$\text{Res}(f; z_0) = \frac{p(z_0)}{q'(z_0)} \quad \text{或直接消去}(z-z_0)\text{后代入}$$

---

#### 3. 解题思路

---

**先算三个极点各自的留数 (Residue)**

被积函数：

$$f(z) = \frac{3z^3+2}{(z-1)(z^2+9)}$$

**(i) $\text{Res}(f; 1)$**

- ● $(z-1)$ 是简单极点 → 消去 $(z-1)$，代入 $z=1$：

$$\text{Res}(f;1) = \lim_{z\to 1}(z-1)\cdot\frac{3z^3+2}{(z-1)(z^2+9)} = \frac{3(1)^3+2}{1^2+9} = \frac{5}{10} = \frac{1}{2}$$

**(ii) $\text{Res}(f; 3i)$**

- ● $(z^2+9) = (z-3i)(z+3i)$，所以 $z=3i$ 是简单极点 → 消去 $(z-3i)$，代入 $z=3i$：

$$\text{Res}(f;3i) = \lim_{z\to 3i}(z-3i)\cdot\frac{3z^3+2}{(z-1)(z-3i)(z+3i)} = \frac{3(3i)^3+2}{(3i-1)(6i)}$$

- 计算分子：$3(3i)^3 = 3 \cdot 27i^3 = 81 \cdot (-i) = -81i$，所以分子 $= -81i + 2$
- 计算分母：$(3i-1)(6i) = 18i^2 - 6i = -18 - 6i$

$$\text{Res}(f;3i) = \frac{2-81i}{-18-6i}$$

- 分子分母同乘共轭 $(-18+6i)$：

$$= \frac{(2-81i)(-18+6i)}{(-18)^2+(6)^2} = \frac{-36+12i+1458i-486i^2}{324+36}$$

$$= \frac{-36 + 1470i + 486}{360} = \frac{450 + 1470i}{360} = \frac{5+\frac{49i}{3}}{4}$$

整理：

$$= \frac{450}{360} + \frac{1470}{360}i = \frac{5}{4} + \frac{49}{12}i$$

**(iii) $\text{Res}(f; -3i)$**

- ● 同理，消去 $(z+3i)$，代入 $z = -3i$：

$$\text{Res}(f;-3i) = \frac{3(-3i)^3+2}{(-3i-1)(-6i)}$$

- 分子：$3(-3i)^3 = 3\cdot(-27i^3) = 3\cdot 27i = 81i$，所以分子 $= 81i+2$
- 分母：$(-3i-1)(-6i) = 18i^2+6i = -18+6i$

$$\text{Res}(f;-3i) = \frac{2+81i}{-18+6i}$$

- 同乘共轭 $(-18-6i)$：

$$= \frac{(2+81i)(-18-6i)}{324+36} = \frac{-36-12i-1458i-486i^2}{360}$$

$$= \frac{-36 - 1470i + 486}{360} = \frac{450 - 1470i}{360} = \frac{5}{4} - \frac{49}{12}i$$

---

**注意：$\text{Res}(f;3i)$ 和 $\text{Res}(f;-3i)$ 互为共轭，这是正常现象。**

---

**(a) 围道 $|z-2|=2$（圆心 $z=2$，半径 $2$）**

判断哪些极点在圆内（距圆心距离 $< 2$）：

- ● $z=1$：$|1-2| = 1 < 2$ → **在圆内 ✓**
- ● $z=3i$：$|3i-2| = \sqrt{4+9} = \sqrt{13} \approx 3.6 > 2$ → **在圆外 ✗**
- ● $z=-3i$：$|-3i-2| = \sqrt{4+9} = \sqrt{13} > 2$ → **在圆外 ✗**

→ 只有 $z=1$ 在圆内，用留数定理：

$$\oint_C f(z)\,dz = 2\pi i \cdot \text{Res}(f;1) = 2\pi i \cdot \frac{1}{2} = \pi i$$

---

**(b) 围道 $|z|=4$（圆心原点，半径 $4$）**

判断哪些极点在圆内（距原点距离 $< 4$）：

- ● $z=1$：$|1| = 1 < 4$ → **在圆内 ✓**
- ● $z=3i$：$|3i| = 3 < 4$ → **在圆内 ✓**
- ● $z=-3i$：$|-3i| = 3 < 4$ → **在圆内 ✓**

→ 三个极点全部在圆内，用留数定理：

$$\oint_C f(z)\,dz = 2\pi i \left(\text{Res}(f;1) + \text{Res}(f;3i) + \text{Res}(f;-3i)\right)$$

$$= 2\pi i \left(\frac{1}{2} + \frac{5}{4} + \frac{49}{12}i + \frac{5}{4} - \frac{49}{12}i\right)$$

- 虚部 $\pm\frac{49}{12}i$ 相消
- 实部：$\frac{1}{2} + \frac{5}{4} + \frac{5}{4} = \frac{2}{4} + \frac{5}{4} + \frac{5}{4} = \frac{12}{4} = 3$

$$= 2\pi i \cdot 3 = 6\pi i$$

---

#### 4. 最终答案

- **(a)** $\displaystyle\oint_C f(z)\,dz = \pi i$
- **(b)** $\displaystyle\oint_C f(z)\,dz = 6\pi i$

---

#### 5. 核心逻辑总结（可复用规则）

- ● 遇到围道积分 → 找分母所有零点（极点）
- ● 判断哪些极点在围道**内部**（比较距离与半径）
- ● 对圆内每个极点算留数（简单极点直接消去因子代入）
- ● 留数定理：积分 $= 2\pi i \times$（圆内所有留数之和）
- ● 多个留数相加时，共轭对的虚部会自动消去
# Q3
#### 1. 题目翻译与信息拆解

**原题翻译：**

> 第3题（Brown & Churchill 习题86.4,6）
> 用留数 (residues) 推导以下积分公式：
>
> (a) $\displaystyle\int_0^{\infty} \dfrac{x^2}{x^6+1}\,dx = \dfrac{\pi}{6}$
>
> (b) $\displaystyle\int_0^{\infty} \dfrac{x^2}{(x^2+9)(x^2+4)^2}\,dx = \dfrac{\pi}{200}$

**题目给了我们什么：**

- 两个**实数轴上的[[反常积分 (improper integral)]]**，积分范围从 $0$ 到 $\infty$
- 要求用留数方法**推导**出等号右边的值

---

#### 2. 背景概念


当被积函数 $f(x)$ 满足：
- 是偶函数 (even function)，即 $f(-x) = f(x)$
- 分母次数比分子高至少 2 次
- 在实轴上没有极点 (pole)

则可以用以下步骤转化：

$$\int_0^{\infty} f(x)\,dx = \frac{1}{2}\int_{-\infty}^{\infty} f(x)\,dx = \frac{1}{2} \cdot 2\pi i \sum_{\text{上半平面}} \text{Res}(f;z_k) = \pi i \sum_{\text{上半平面}} \text{Res}(f;z_k)$$

**为什么可以折半？** 因为 $f(x)$ 是偶函数：

$$\int_{-\infty}^{\infty} f(x)\,dx = 2\int_0^{\infty} f(x)\,dx$$

**[[半圆围道 (Semicircular Contour)]]**

==实轴积分转化为围道积分，也就是把从负无穷到正无穷的积分。由于它不封闭，我们可以把上半平面补一个围道让它封闭==

此方法使用的条件是，分母至少比分子大了两个次数

标准做法是取上半平面 (upper half-plane) 的半圆围道 $C_R$：

- 沿实轴从 $-R$ 到 $R$
- 再沿半径为 $R$ 的上半圆弧 $\Gamma_R$ 从 $R$ 到 $-R$

当 $R \to \infty$ 时，半圆弧上的积分趋近于 $0$（由 Jordan 引理或估计法保证），剩下的就是实轴积分。

**[[约当引理 / 大圆弧引理 (Jordan's Lemma / Big Arc Lemma)]]**

若分母次数比分子次数高 $\geq 2$，则当 $R \to \infty$：

$$\int_{\Gamma_R} f(z)\,dz \to 0$$

这保证了半圆弧的贡献消失，围道积分 $=$ 实轴积分。

---

#### 3. 解题思路

---

**(a) $\displaystyle\int_0^{\infty} \dfrac{x^2}{x^6+1}\,dx$**

**Step 1：确认可以用半圆围道法**

- ● 被积函数 $f(x) = \dfrac{x^2}{x^6+1}$ 是偶函数（分子分母都只有偶次幂）→ 可以折半
- ● 分母次数 $6$ − 分子次数 $2$ $= 4 \geq 2$ → 大圆弧积分趋于 $0$（Jordan 引理适用）
- ● 实轴上 $x^6+1 \neq 0$（实数范围内无极点）→ 围道合法

**Step 2：找上半平面的极点**

令 $z^6 + 1 = 0$，即 $z^6 = -1 = e^{i\pi}$，解为：

$$z_k = e^{i(\pi + 2k\pi)/6} = e^{i\pi(2k+1)/6}, \quad k = 0,1,2,3,4,5$$

六个根均匀分布在单位圆上，角度分别为：

$$\frac{\pi}{6},\quad \frac{3\pi}{6}=\frac{\pi}{2},\quad \frac{5\pi}{6},\quad \frac{7\pi}{6},\quad \frac{9\pi}{6},\quad \frac{11\pi}{6}$$

- ● 上半平面 (upper half-plane) = $\text{Im}(z) > 0$，即角度在 $(0, \pi)$ 之间
- ● 满足条件的三个极点：

$$z_0 = e^{i\pi/6}, \quad z_1 = e^{i\pi/2} = i, \quad z_2 = e^{i5\pi/6}$$

**Step 3：算每个极点的留数（用 $P/Q'$ 法）**

$f(z) = \dfrac{z^2}{z^6+1}$，分母 $Q(z) = z^6+1$，$Q'(z) = 6z^5$，分子 $P(z) = z^2$：

$$\text{Res}(f; z_k) = \frac{z_k^2}{6z_k^5} = \frac{1}{6z_k^3}$$

分别计算：

- $z_0 = e^{i\pi/6}$：$z_0^3 = e^{i\pi/2} = i$，所以 $\text{Res} = \dfrac{1}{6i}$

- $z_1 = e^{i\pi/2} = i$：$z_1^3 = i^3 = -i$，所以 $\text{Res} = \dfrac{1}{6(-i)} = \dfrac{1}{-6i}$

- $z_2 = e^{i5\pi/6}$：$z_2^3 = e^{i5\pi/2} = e^{i\pi/2} = i$，所以 $\text{Res} = \dfrac{1}{6i}$

**Step 4：求留数之和**

$$\sum \text{Res} = \frac{1}{6i} + \frac{1}{-6i} + \frac{1}{6i} = \frac{1}{6i} = \frac{-i}{6}$$

（注意：$\dfrac{1}{6i} = \dfrac{-i}{6}$，因为 $\dfrac{1}{i} = -i$）

**Step 5：代入公式**

$$\int_{-\infty}^{\infty} f(x)\,dx = 2\pi i \cdot \frac{-i}{6} = \frac{2\pi i \cdot (-i)}{6} = \frac{2\pi}{6} = \frac{\pi}{3}$$

（因为 $i \cdot (-i) = -i^2 = 1$）

$$\int_0^{\infty} f(x)\,dx = \frac{1}{2} \cdot \frac{\pi}{3} = \boxed{\frac{\pi}{6}} \quad \checkmark$$

---

**(b) $\displaystyle\int_0^{\infty} \dfrac{x^2}{(x^2+9)(x^2+4)^2}\,dx$**

**Step 1：确认可以用半圆围道法**

- ● $f(x) = \dfrac{x^2}{(x^2+9)(x^2+4)^2}$ 是偶函数 → 可以折半
- ● 分母次数 $2+4=6$，分子次数 $2$，差 $\geq 2$ → 大圆弧趋于 $0$
- ● 实轴上分母不为零 → 合法

**Step 2：找上半平面的极点**

令分母为零：

- $(z^2+9) = 0 \Rightarrow z = \pm 3i$，上半平面取 $z = 3i$（简单极点 simple pole）
- $(z^2+4)^2 = 0 \Rightarrow z = \pm 2i$，上半平面取 $z = 2i$（**二阶极点 pole of order 2**）

**Step 3：算 $\text{Res}(f; 3i)$（简单极点，用 $P/Q'$ 或直接消去）**

直接消去 $(z-3i)$，代入 $z = 3i$：

$$\text{Res}(f; 3i) = \frac{(3i)^2}{(3i+3i)(z^2+4)^2}\bigg|_{z=3i} = \frac{-9}{6i \cdot (−9+4)^2} = \frac{-9}{6i \cdot 25} = \frac{-9}{150i} = \frac{-3}{50i} = \frac{3i}{50}$$

（化简：$\dfrac{-3}{50i} = \dfrac{-3 \cdot i}{50 \cdot i^2} = \dfrac{-3i}{-50} = \dfrac{3i}{50}$）

**Step 4：算 $\text{Res}(f; 2i)$（二阶极点，用求导公式）**

$$\text{Res}(f; 2i) = \lim_{z \to 2i} \frac{d}{dz}\left[(z-2i)^2 \cdot f(z)\right] = \lim_{z \to 2i} \frac{d}{dz}\left[\frac{z^2}{(z^2+9)(z+2i)^2}\right]$$

设 $g(z) = \dfrac{z^2}{(z^2+9)(z+2i)^2}$，用商法则 (quotient rule) 求导：

分子：$u = z^2$，$u' = 2z$

分母：$v = (z^2+9)(z+2i)^2$

$$v' = 2z(z+2i)^2 + (z^2+9)\cdot 2(z+2i)$$

所以：

$$g'(z) = \frac{2z(z^2+9)(z+2i)^2 - z^2\left[2z(z+2i)^2 + 2(z^2+9)(z+2i)\right]}{[(z^2+9)(z+2i)^2]^2}$$

代入 $z = 2i$，逐项计算：

- $z = 2i$，$z^2 = -4$，$z+2i = 4i$，$(z+2i)^2 = -16$，$z^2+9 = 5$

分子各项：
- $2z(z^2+9)(z+2i)^2 = 2(2i)(5)(-16) = -320i$
- $2z(z+2i)^2 = 2(2i)(-16) = -64i$
- $2(z^2+9)(z+2i) = 2(5)(4i) = 40i$
- $z^2[...] = (-4)[(-64i)+(40i)] = (-4)(-24i) = 96i$

分子 $= -320i - 96i = -416i$

分母 $= [(5)(-16)]^2 = (-80)^2 = 6400$

$$g'(2i) = \frac{-416i}{6400} = \frac{-13i}{200}$$

**Step 5：求留数之和**

$$\sum \text{Res} = \frac{3i}{50} + \frac{-13i}{200} = \frac{12i}{200} + \frac{-13i}{200} = \frac{-i}{200}$$

**Step 6：代入公式**

$$\int_{-\infty}^{\infty} f(x)\,dx = 2\pi i \cdot \frac{-i}{200} = \frac{2\pi}{200} = \frac{\pi}{100}$$

$$\int_0^{\infty} f(x)\,dx = \frac{1}{2} \cdot \frac{\pi}{100} = \boxed{\frac{\pi}{200}} \quad \checkmark$$

---

#### 4. 核心逻辑总结（可复用规则）

- ● 被积函数是偶函数，积分从 $0$ 到 $\infty$ → 折半，转化为 $-\infty$ 到 $\infty$
- ● 取上半平面半圆围道，$R \to \infty$ 时弧上积分消失（分母次数比分子高 $\geq 2$）
- ● 只需找**上半平面**的极点（$\text{Im}(z) > 0$）
- ● 简单极点用 $P/Q'$，二阶极点用求导公式
- ● 最终：$\displaystyle\int_0^\infty f(x)\,dx = \pi i \sum_{\text{上半平面}}\text{Res}(f;z_k)$
# Q4
好的，我来帮你完整拆解这道复分析 (Complex Analysis) 的积分题目。这道题要求你通过留数定理 (Residue Theorem) 推导一个实积分公式。

#### 1. 题目翻译与信息点拆解

**原题翻译：**

问题 4（Brown & Churchill 练习 86.10）：设 $m$ 和 $n$ 是整数 (integers)，其中 $0 < m < n$。按照以下步骤推导积分公式 (integration formula)：

$$\int_0^\infty \frac{x^{2m}}{x^{2n}+1} dx = \frac{\pi}{2n} \csc\left(\frac{2m+1}{2n}\pi\right)$$

**(a) 证明多项式 (polynomial) $z^{2n}+1$ 位于实轴上方 (above the real axis) 的零点 (zeros) 为：**

$$c_k = \exp\left(i\frac{(2k+1)\pi}{2n}\right) \quad (k=0,1,\ldots,n-1)$$

**并且在实轴上没有零点 (none on that axis)。**

**(b) 借助讲义中的定理 13.6.4，证明：**

$$\text{Res}\left(\frac{z^{2m}}{z^{2n}+1}; c_k\right) = -\frac{1}{2n} e^{i(2k+1)\alpha} \quad (k=0,1,\ldots,n-1)$$

**其中 $c_k$ 是 (a) 中找到的零点，且：**

$$\alpha = \frac{2m+1}{2n}\pi$$

**然后使用求和公式 (summation formula)：**

$$\sum_{k=0}^{n-1} z^k = \frac{1-z^n}{1-z} \quad (z \neq 1)$$

**来得到表达式：**

$$2\pi i \sum_{k=0}^{n-1} \text{Res}\left(\frac{z^{2m}}{z^{2n}+1}; c_k\right) = \frac{\pi}{n\sin\alpha}$$

**(c) 使用 (b) 中的最终结果来完成积分公式的推导。**

---

**题目给了我们什么信息：**

- 给定条件：$0 < m < n$，$m, n$ 都是整数
- 目标：证明一个实积分等于一个三角函数表达式
- 方法：分三步走
  - 第一步：找出复函数 $z^{2n}+1$ 在上半平面 (upper half-plane) 的所有零点
  - 第二步：计算这些零点处的留数 (residues)，然后求和
  - 第三步：利用留数定理把复积分转化为实积分

---

#### 2. 背景知识与核心概念

**[[零点 (Zeros / Roots)]]**

函数 $f(z)$ 的零点是指满足 $f(z) = 0$ 的复数 $z$。对于多项式 $z^{2n}+1$，我们要找所有满足 $z^{2n} = -1$ 的复数。

**[[欧拉公式 (Euler's Formula)]]**

$$e^{i\theta} = \cos\theta + i\sin\theta$$

这是复数的极坐标表示 (polar form)。任何复数 $z$ 都可以写成 $z = re^{i\theta}$，其中 $r = |z|$ 是模 (modulus)，$\theta$ 是辐角 (argument)。

**[[留数 (Residue)]]**

如果函数 $f(z)$ 在点 $z_0$ 有一个简单极点 (simple pole)，那么它在该点的留数定义为：

$$\text{Res}(f; z_0) = \lim_{z \to z_0} (z - z_0) f(z)$$

对于形如 $f(z) = \frac{g(z)}{h(z)}$ 的函数，如果 $h(z_0) = 0$ 但 $h'(z_0) \neq 0$（即 $z_0$ 是 $h$ 的简单零点），那么：

$$\text{Res}(f; z_0) = \frac{g(z_0)}{h'(z_0)}$$

这就是题目中提到的"定理 13.6.4"的内容。

**[[留数定理 (Residue Theorem)]]**

如果 $f(z)$ 在闭合曲线 (closed contour) $C$ 内部除了有限个孤立奇点 (isolated singularities) 外处处解析 (analytic)，那么：

$$\oint_C f(z) dz = 2\pi i \sum \text{Res}(f; z_k)$$

其中求和是对 $C$ 内部所有奇点进行的。

**[[上半平面积分技巧 (Upper Half-Plane Integration)]]**

当我们要计算形如 $\int_{-\infty}^{\infty} f(x) dx$ 的实积分时，常用方法是：

- 构造一个包含实轴的闭合曲线（通常是实轴加上上半平面的大半圆）
- 利用留数定理计算闭合曲线上的积分
- 证明半圆弧上的积分在半径趋于无穷时趋于零
- 最后得到实积分等于 $2\pi i$ 乘以上半平面所有留数之和

---

#### 3. 逐步解答思路

**Part (a)：找出上半平面的零点**
这 $2n$ 个根中，==哪些在**实轴上方 (Upper Half-Plane)**？（别忘了这个条件！==
**逻辑链条：**

- ● 要找 $z^{2n} + 1 = 0$ 的解 → 即找满足 $z^{2n} = -1$ 的所有 $z$
- ● 将 $-1$ 写成极坐标形式 (polar form) → $-1 = e^{i\pi}$
- ● 但 $e^{i\theta}$ 有周期性 (periodicity)：$e^{i\theta} = e^{i(\theta + 2\pi k)}$ 对任意整数 $k$ 成立
- ● 所以 $-1 = e^{i\pi} = e^{i(\pi + 2\pi k)}$ 对任意整数 $k$
- ● 因此 $z^{2n} = e^{i(2k+1)\pi}$（这里我把 $\pi + 2\pi k$ 写成了 $(2k+1)\pi$）
- ● 两边开 $2n$ 次方根 (take the $2n$-th root) → $z = e^{i(2k+1)\pi/(2n)}$
- ● 由于 $e^{i\theta}$ 的周期是 $2\pi$，所以 $k$ 取 $0, 1, 2, \ldots, 2n-1$ 会给出 $2n$ 个不同的根
- ● 但题目只要上半平面 (upper half-plane) 的根，即 $\text{Im}(z) > 0$
- ● 对于 $z = e^{i\theta}$，有 $\text{Im}(z) = \sin\theta$
- ● 要 $\sin\theta > 0$ → 需要 $0 < \theta < \pi$
- ● 即 $0 < \frac{(2k+1)\pi}{2n} < \pi$ → $0 < 2k+1 < 2n$ → $k = 0, 1, \ldots, n-1$
- ● 结论：上半平面恰好有 $n$ 个零点，它们是 $c_k = \exp\left(i\frac{(2k+1)\pi}{2n}\right)$，$k = 0, 1, \ldots, n-1$

**为什么实轴上没有零点？**

- ● 实轴上的点满足 $\text{Im}(z) = 0$，即 $z$ 是实数
- ● 如果 $z$ 是实数且 $z^{2n} = -1$，那么 $z^{2n}$ 也必须是实数
- ● 但对于实数 $z$，$z^{2n} \geq 0$（因为 $2n$ 是偶数）
- ● 而 $-1 < 0$，矛盾
- ● 所以实轴上没有零点

---

**Part (b)：计算留数并求和**

**步骤 1：计算单个留数**

**逻辑链条：**

- 使用公式：

$$\text{Res}(f; c_k) = \frac{P(c_k)}{Q'(c_k)} = \frac{c_k^{2m}}{-2n/c_k} = -\frac{c_k^{2m+1}}{2n}$$

- ● 将 $c_k = e^{i(2k+1)\pi/(2n)}$ 代入：
$$\text{Res}(f; c_k) = -\frac{1}{2n} e^{i(2k+1)\alpha}$$

**步骤 2：对所有留数求和**

**逻辑链条：**

- 用公式：$$\sum_{k=0}^{n-1} z^k = \frac{1-z^n}{1-z}$$
得到留数的和为：

	$$\sum_{k=0}^{n-1} Res= -\frac{e^{i\alpha}}{2n}  \frac{2}{1-e^{i(2\alpha)}} = - \frac{1}{n} \frac{1}{e^{-i\alpha}-e^{i\alpha}}$$
分母部分用三角形式化简，得：
$$ 
\sum_{k=0}^{n-1} Res  = \frac{1}{2nisin(\alpha)}
$$
代入留数公式，得：

$$2\pi i \sum_{k=0}^{n-1} \text{Res}(f; c_k) = \frac{\pi}{n\sin(\alpha)}$$

**Part (c)：完成实积分的推导**

**逻辑链条：**

- ● 考虑沿着实轴从 $-R$ 到 $R$，再沿上半平面的大半圆 $C_R$ 回到 $-R$ 的闭合曲线
- ● 当 $R \to \infty$ 时，半圆弧上的积分趋于零（这需要用 Jordan 引理或直接估计，因为分母的次数比分子高）
- ● 所以：

$$\int_{-\infty}^{\infty} \frac{x^{2m}}{x^{2n}+1} dx = 2\pi i \sum_{k=0}^{n-1} \text{Res}(f; c_k) = \frac{\pi}{n\sin(\alpha)}$$

- ● 但被积函数 $\frac{x^{2m}}{x^{2n}+1}$ 是偶函数 (even function)（因为 $2m$ 和 $2n$ 都是偶数）
- ● 对于偶函数，有性质：$\int_{-\infty}^{\infty} f(x) dx = 2\int_0^{\infty} f(x) dx$
- ● 所以：

$$2\int_0^{\infty} \frac{x^{2m}}{x^{2n}+1} dx = \frac{\pi}{n\sin(\alpha)}$$

- ● 两边除以 2：

$$\int_0^{\infty} \frac{x^{2m}}{x^{2n}+1} dx = \frac{\pi}{2n\sin(\alpha)}$$

- ● 代入 $\alpha = \frac{2m+1}{2n}\pi$：

$$\int_0^{\infty} \frac{x^{2m}}{x^{2n}+1} dx = \frac{\pi}{2n\sin\left(\frac{2m+1}{2n}\pi\right)}$$

- ● 利用三角恒等式：$\frac{1}{\sin(\theta)} = \csc(\theta)$（余割函数 (cosecant function)）
- ● 最终得到：

$$\int_0^{\infty} \frac{x^{2m}}{x^{2n}+1} dx = \frac{\pi}{2n} \csc\left(\frac{2m+1}{2n}\pi\right)$$

证毕。

---

#### 4. 关键定理与技巧总结

**使用的核心定理：**

- 复数的极坐标表示 (Polar form of complex numbers)
- 单位根的性质 (Properties of roots of unity)
- 简单极点的留数公式 (Residue formula for simple poles)
- 留数定理 (Residue Theorem)
- 等比数列求和 (Geometric series summation)
- 偶函数的对称性 (Symmetry of even functions)

**考试时的关键步骤：**

1. 找零点时，记得用 $-1 = e^{i(2k+1)\pi}$ 而不是 $e^{i\pi}$，这样才能找到所有根
2. 判断简单极点时，一定要验证 $h'(z_0) \neq 0$
3. 求和时，识别出等比数列的形式，利用公式简化
4. 最后别忘了偶函数的对称性，从 $(-\infty, \infty)$ 转换到 $(0, \infty)$ 要除以 2
# Q5

# Q6

# Q7
