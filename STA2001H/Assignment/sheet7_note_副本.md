# Q1

#### 问题翻译
随机变量X和Y的联合概率密度函数为：
$$f_{X,Y}(x,y) = \begin{cases} 
2e^{-(x+2y)}, & x > 0, y > 0 \\
0, & \text{其他}
\end{cases}$$
求：X的边缘概率密度函数 $f_X(x)$。

#### 背景条件解释
**基本概念**：
- **联合分布 Joint Distribution** 两个随机变量同时的概率分布
- **边缘分布 Marginal Distribution** 单个随机变量的分布
- **概率密度函数 PDF** 连续随机变量的密度函数
- **积分 Integration** 连续随机变量概率的计算方式

**具体条件**：
- 联合PDF：$f_{X,Y}(x,y) = 2e^{-(x+2y)}$, 当 $x > 0, y > 0$
- 定义域：第一象限（x>0且y>0）
- 求解：X的边缘PDF $f_X(x)$
- 边缘分布通过积分另一个变量得到

#### 解答思路

**步骤1：理解边缘分布公式**
- 对于连续随机变量，边缘分布通过对另一个变量积分得到：
  $$f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x,y) dy$$
- 由于联合PDF在 $y \le 0$ 时为0，所以：
  $$f_X(x) = \int_{0}^{\infty} f_{X,Y}(x,y) dy$$

**步骤2：代入联合PDF**
- 将给定的联合PDF代入：
  $$f_X(x) = \int_{0}^{\infty} 2e^{-(x+2y)} dy$$
- 指数函数可以分解：
  $$e^{-(x+2y)} = e^{-x} \cdot e^{-2y}$$

**步骤3：进行积分计算**
- 将常数项提出积分号：
  $$f_X(x) = 2e^{-x} \int_{0}^{\infty} e^{-2y} dy$$
- 计算积分：
  $$\int_{0}^{\infty} e^{-2y} dy = \left[ -\frac{1}{2}e^{-2y} \right]_{0}^{\infty} = -\frac{1}{2}(0 - 1) = \frac{1}{2}$$

**步骤4：得出边缘分布**
- 代入积分结果：
  $$f_X(x) = 2e^{-x} \times \frac{1}{2} = e^{-x}$$
- 考虑定义域：
  - 当 $x > 0$ 时：$f_X(x) = e^{-x}$
  - 当 $x \le 0$ 时：$f_X(x) = 0$

#### 关键概念总结
- **联合分布 Joint Distribution** $f_{X,Y}(x,y)$ 两个变量的联合概率密度
- **边缘分布 Marginal Distribution** $f_X(x) = \int f_{X,Y}(x,y) dy$ 单个变量的分布
- **概率密度函数 PDF** 连续随机变量的密度函数
- **积分 Integration** 连续变量概率的计算方式
- **定义域 Domain** 函数有定义的变量范围

---

# Q2

#### 问题翻译
随机变量X和Y的联合概率密度函数为：
$$f_{X,Y}(x,y) = \begin{cases} 
8xy, & 0 < x < 1, 0 < y < x \\
0, & \text{其他}
\end{cases}$$
求：
1. X的边缘概率密度函数 $f_X(x)$
2. Y的边缘概率密度函数 $f_Y(y)$
3. 判断X和Y是否独立

#### 背景条件解释
**基本概念**：
- **联合分布 Joint Distribution** 两个随机变量的联合概率密度
- **边缘分布 Marginal Distribution** 单个随机变量的分布
- **独立性 Independence** 两个随机变量的概率关系
- **积分区域 Integration Region** 积分的范围限制

**具体条件**：
- 联合PDF：$f_{X,Y}(x,y) = 8xy$, 当 $0 < y < x < 1$
- 定义域：三角形区域（0 < y < x < 1）
- 求解：两个边缘分布和独立性判断

#### 解答思路

**步骤1：理解积分区域**
- 联合PDF的定义域是 $0 < y < x < 1$
- 这是在第一象限内，直线y=x下方的三角形区域
- 对于固定的x，y的范围是 $0 < y < x$
- 对于固定的y，x的范围是 $y < x < 1$

**步骤2：求X的边缘分布 $f_X(x)$**
- 对y积分：
  $$f_X(x) = \int_{-\infty}^{\infty} f_{X,Y}(x,y) dy = \int_{0}^{x} 8xy dy$$
- 提出常数：
  $$f_X(x) = 8x \int_{0}^{x} y dy = 8x \left[ \frac{y^2}{2} \right]_{0}^{x} = 8x \times \frac{x^2}{2} = 4x^3$$
- 考虑定义域：当 $0 < x < 1$ 时，$f_X(x) = 4x^3$，其他情况为0

**步骤3：求Y的边缘分布 $f_Y(y)$**
- 对x积分：
  $$f_Y(y) = \int_{-\infty}^{\infty} f_{X,Y}(x,y) dx = \int_{y}^{1} 8xy dx$$
- 提出常数：
  $$f_Y(y) = 8y \int_{y}^{1} x dx = 8y \left[ \frac{x^2}{2} \right]_{y}^{1} = 8y \left( \frac{1}{2} - \frac{y^2}{2} \right) = 4y(1 - y^2)$$
- 考虑定义域：当 $0 < y < 1$ 时，$f_Y(y) = 4y(1 - y^2)$，其他情况为0

**步骤4：判断独立性**
- 检查是否满足 $f_{X,Y}(x,y) = f_X(x) f_Y(y)$
- 计算乘积：
  $$f_X(x) f_Y(y) = 4x^3 \times 4y(1 - y^2) = 16x^3 y(1 - y^2)$$
- 与联合PDF比较：
  - $f_{X,Y}(x,y) = 8xy$
  - $f_X(x) f_Y(y) = 16x^3 y(1 - y^2)$
- 显然 $8xy \neq 16x^3 y(1 - y^2)$
- 所以X和Y不独立

#### 关键概念总结
- **联合分布 Joint Distribution** $f_{X,Y}(x,y)$ 两个变量的联合概率密度
- **边缘分布 Marginal Distribution** $f_X(x) = \int f_{X,Y}(x,y) dy$ 单个变量的分布
- **独立性 Independence** $f_{X,Y}(x,y) = f_X(x)f_Y(y)$ 当且仅当独立
- **积分区域 Integration Region** 积分范围由联合PDF的定义域决定
- **概率密度函数 PDF** 连续随机变量的密度函数