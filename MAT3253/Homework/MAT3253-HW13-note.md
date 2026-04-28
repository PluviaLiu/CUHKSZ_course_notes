- [ ] 完成MAT3253的HW13

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

==这种充满1/2的数字的格式，一定要写大， 然后所有的z都要标一个杠）

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

# Q3

# Q4

# Q5

# Q6

# Q7
