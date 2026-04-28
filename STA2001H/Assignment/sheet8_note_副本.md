# Q1

#### 问题翻译
随机变量X的概率密度函数为：
$$f_X(x) = \begin{cases} 
3x^2, & 0 < x < 1 \\
0, & \text{其他}
\end{cases}$$
求：期望 $E[X]$ 和方差 $Var(X)$。

#### 背景条件解释
**基本概念**：
- **期望 Expectation** 随机变量的平均值（均值）
- **方差 Variance** 随机变量偏离期望的程度
- **概率密度函数 PDF** 连续随机变量的密度函数
- **积分计算 Integration** 连续变量的期望和方差计算

**具体条件**：
- PDF：$f_X(x) = 3x^2$, 当 $0 < x < 1$
- 定义域：开区间 (0,1)
- 求解：
  - 期望：$E[X] = \int_{-\infty}^{\infty} x f_X(x) dx$
  - 方差：$Var(X) = E[X^2] - (E[X])^2$

#### 解答思路

**步骤1：计算期望 $E[X]$**
- 期望公式：
  $$E[X] = \int_{-\infty}^{\infty} x f_X(x) dx$$
- 代入PDF：
  $$E[X] = \int_{0}^{1} x \cdot 3x^2 dx = 3 \int_{0}^{1} x^3 dx$$
- 计算积分：
  $$3 \int_{0}^{1} x^3 dx = 3 \left[ \frac{x^4}{4} \right]_{0}^{1} = 3 \times \frac{1}{4} = \frac{3}{4}$$

**步骤2：计算 $E[X^2]$**
- 为了计算方差，需要先计算 $E[X^2]$：
  $$E[X^2] = \int_{-\infty}^{\infty} x^2 f_X(x) dx$$
- 代入PDF：
  $$E[X^2] = \int_{0}^{1} x^2 \cdot 3x^2 dx = 3 \int_{0}^{1} x^4 dx$$
- 计算积分：
  $$3 \int_{0}^{1} x^4 dx = 3 \left[ \frac{x^5}{5} \right]_{0}^{1} = 3 \times \frac{1}{5} = \frac{3}{5}$$

**步骤3：计算方差 $Var(X)$**
- 方差公式：
  $$Var(X) = E[X^2] - (E[X])^2$$
- 代入已知值：
  $$Var(X) = \frac{3}{5} - \left(\frac{3}{4}\right)^2 = \frac{3}{5} - \frac{9}{16}$$
- 通分计算：
  $$\frac{3}{5} = \frac{48}{80}, \quad \frac{9}{16} = \frac{45}{80}$$
  $$Var(X) = \frac{48}{80} - \frac{45}{80} = \frac{3}{80}$$

#### 关键概念总结
- **期望 Expectation** $E[X] = \int x f_X(x) dx$ 随机变量的平均值
- **方差 Variance** $Var(X) = E[X^2] - (E[X])^2$ 偏离期望的程度
- **概率密度函数 PDF** $f_X(x)$ 连续随机变量的密度
- **积分 Integration** 连续变量的期望和方差计算方式
- **线性性质** $E[aX + b] = aE[X] + b$ 期望的线性性

---

# Q2

#### 问题翻译
随机变量X的概率密度函数为：
$$f_X(x) = \begin{cases} 
2(1 - x), & 0 < x < 1 \\
0, & \text{其他}
\end{cases}$$
求：
1. 期望 $E[X]$
2. 方差 $Var(X)$
3. 标准差 $\sigma_X$

#### 背景条件解释
**基本概念**：
- **期望 Expectation** 随机变量的中心位置（均值）
- **方差 Variance** 数据的离散程度
- **标准差 Standard Deviation** 方差的平方根，与原始变量同单位
- **概率密度函数 PDF** 连续随机变量的密度函数

**具体条件**：
- PDF：$f_X(x) = 2(1 - x)$, 当 $0 < x < 1$
- 定义域：开区间 (0,1)
- 这是一个三角形分布，在x=0处达到最大值2，在x=1处为0
- 求解：期望、方差和标准差

#### 解答思路

**步骤1：验证PDF的合法性**
- 首先验证PDF积分是否为1：
  $$\int_{-\infty}^{\infty} f_X(x) dx = \int_{0}^{1} 2(1 - x) dx$$
- 计算积分：
  $$2 \int_{0}^{1} (1 - x) dx = 2 \left[ x - \frac{x^2}{2} \right]_{0}^{1} = 2 \left(1 - \frac{1}{2}\right) = 2 \times \frac{1}{2} = 1$$
- 验证通过，PDF是合法的

**步骤2：计算期望 $E[X]$**
- 期望公式：
  $$E[X] = \int_{-\infty}^{\infty} x f_X(x) dx = \int_{0}^{1} x \cdot 2(1 - x) dx$$
- 展开积分：
  $$E[X] = 2 \int_{0}^{1} (x - x^2) dx = 2 \left[ \frac{x^2}{2} - \frac{x^3}{3} \right]_{0}^{1}$$
- 计算边界值：
  $$E[X] = 2 \left( \frac{1}{2} - \frac{1}{3} \right) = 2 \times \frac{1}{6} = \frac{1}{3}$$

**步骤3：计算 $E[X^2]$**
- 为了计算方差，先计算二阶矩：
  $$E[X^2] = \int_{0}^{1} x^2 \cdot 2(1 - x) dx = 2 \int_{0}^{1} (x^2 - x^3) dx$$
- 计算积分：
  $$E[X^2] = 2 \left[ \frac{x^3}{3} - \frac{x^4}{4} \right]_{0}^{1} = 2 \left( \frac{1}{3} - \frac{1}{4} \right) = 2 \times \frac{1}{12} = \frac{1}{6}$$

**步骤4：计算方差 $Var(X)$**
- 方差公式：
  $$Var(X) = E[X^2] - (E[X])^2 = \frac{1}{6} - \left(\frac{1}{3}\right)^2$$
- 计算得：
  $$Var(X) = \frac{1}{6} - \frac{1}{9} = \frac{3}{18} - \frac{2}{18} = \frac{1}{18}$$

**步骤5：计算标准差 $\sigma_X$**
- 标准差是方差的平方根：
  $$\sigma_X = \sqrt{Var(X)} = \sqrt{\frac{1}{18}} = \frac{1}{3\sqrt{2}} = \frac{\sqrt{2}}{6}$$

#### 关键概念总结
- **期望 Expectation** $E[X] = \int x f_X(x) dx$ 随机变量的平均值
- **方差 Variance** $Var(X) = E[X^2] - (E[X])^2$ 数据的离散程度
- **标准差 Standard Deviation** $\sigma_X = \sqrt{Var(X)}$ 与原始变量同单位
- **矩 Moment** $E[X^k]$ 随机变量的k阶矩
- **概率密度函数 PDF** $f_X(x)$ 连续随机变量的密度函数