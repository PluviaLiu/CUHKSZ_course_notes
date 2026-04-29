这是在讲**用留数定理计算实积分**（Evaluation of real integrals），这是留数定理最重要的应用场景之一！

## 核心内容

$$\int_{-\infty}^{\infty} \frac{1}{1+x^2} dx = \lim_{a \to \infty} \int_{-a}^{a} \frac{1}{1+x^2} dx$$

下面标注：**Cauchy's principal value**（柯西主值）

---

## 知识点：用留数定理计算实积分

### 基本思路

**目标**：计算实轴上的无穷积分 $\int_{-\infty}^{\infty} f(x) dx$

**方法**：
1. 把实函数 $f(x)$ 延拓到复平面，变成 $f(z)$
2. 构造一个**闭合围道**（通常是半圆）
3. 用留数定理计算围道积分
4. 让半圆半径 $R \to \infty$，半圆上的积分趋于0
5. 剩下的就是实轴上的积分

---

## 这个例子的完整解法

**例**：计算 $\int_{-\infty}^{\infty} \frac{1}{1+x^2} dx$

**步骤1**：延拓到复平面
$$f(z) = \frac{1}{1+z^2} = \frac{1}{(z-i)(z+i)}$$

奇点：$z = i$ 和 $z = -i$

**步骤2**：构造围道
- 实轴：$[-R, R]$
- 上半圆：$C_R = \{z : |z|=R, \text{Im}(z) \geq 0\}$
- 围道包含上半平面的奇点 $z=i$

**步骤3**：计算留数
$$\text{Res}(f, i) = \lim_{z \to i} (z-i) \frac{1}{(z-i)(z+i)} = \frac{1}{2i}$$

**步骤4**：应用留数定理
$$\oint_{\text{围道}} f(z) dz = 2\pi i \cdot \frac{1}{2i} = \pi$$

**步骤5**：分解积分
$$\int_{-R}^{R} \frac{1}{1+x^2} dx + \int_{C_R} \frac{1}{1+z^2} dz = \pi$$

当 $R \to \infty$ 时，半圆上的积分 $\to 0$，所以：
$$\int_{-\infty}^{\infty} \frac{1}{1+x^2} dx = \pi$$

---

## 柯西主值（Cauchy Principal Value）

当积分在实轴上有奇点时，需要用柯西主值定义：
$$\text{P.V.} \int_{-\infty}^{\infty} f(x) dx = \lim_{a \to \infty} \int_{-a}^{a} f(x) dx$$

这确保了积分的对称性。


## 图中内容逐步解析

### 第一张图：设置等式和估计

**1. 计算留数**（顶部）
$$\lim_{z \to i} \frac{1}{z+i} = \frac{1}{2i}$$
$$2\pi i \cdot \text{Res} = 2\pi i \cdot \frac{1}{2i} = \pi$$

**2. 分解积分**
$$\left|\int_{-a}^{a} \frac{1}{1+x^2} dx - \pi\right| = \left|\int_{C_R} \frac{1}{1+z^2} dz\right|$$

这是说：实轴积分与 $\pi$ 的差 = 半圆上的积分

**3. 用ML不等式估计半圆积分**（红圈部分）
$$\left|\int_{C_R} \frac{1}{1+z^2} dz\right| \leq \frac{1}{a^2-1} \cdot 2\pi a$$

其中：
- $M = \frac{1}{a^2-1}$（函数在半圆上的最大值）
- $L = 2\pi a$（半圆的弧长）

**4. 估计分母**（底部红色）
在半圆上 $|z| = a$：
$$|z^2+1| \geq |z|^2 - 1 = a^2 - 1$$

所以：
$$\left|\frac{1}{1+z^2}\right| \leq \frac{1}{a^2-1}$$

---

### 第二张图：取极限

**5. 半圆积分趋于0**
$$\frac{1}{a^2-1} \cdot 2\pi a \to 0 \quad \text{as } a \to \infty$$

因为分子是 $O(a)$，分母是 $O(a^2)$

**6. 最终结论**
$$\lim_{a \to \infty} \int_{-a}^{a} \frac{1}{1+x^2} dx = \pi$$

---

## 核心技巧总结

这个证明用到了**三个关键步骤**：

1. **留数定理**：围道积分 = $2\pi i \times$ 留数
2. **ML不等式**：估计半圆上的积分 $\leq M \cdot L$
3. **极限论证**：证明半圆积分 $\to 0$ 当 $a \to \infty$

这是用留数定理计算实积分的**标准流程**！

---

**ML不等式**（Estimation Lemma）：
$$\left|\int_C f(z) dz\right| \leq M \cdot L$$
其中 $M = \max_{z \in C} |f(z)|$，$L$ 是路径长度。