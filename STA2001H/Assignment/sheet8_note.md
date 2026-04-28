- [ ] 完成STA2001H Sheet8练习
# Q1
#### 1. 题目翻译

**原题：**
假设 X ∈ X = [0,1] 是一个连续随机变量（continuous random variable），其概率密度函数（PDF, Probability Density Function）为：

$f(x) = 4x^3, \quad x \in [0,1]$

求以下随机变量（random variables）的概率密度函数（PDFs）：
- (1) $Y = X^4$
- (2) $W = e^X$
- (3) $Z = \log(X)$

---

#### 2. 背景知识与基本概念

**什么是概率密度函数（PDF）？**
- 对于连续随机变量（continuous random variable）X，PDF f(x) 描述了 X 取某个值附近的"概率密度"
- 重要性质（properties）：
  - $f(x) \geq 0$（非负性，non-negativity）
  - $\int_{-\infty}^{\infty} f(x)dx = 1$（归一化条件，normalization condition）
  - $P(a \leq X \leq b) = \int_a^b f(x)dx$（概率等于面积）

**随机变量变换（Transformation of Random Variables）的核心方法：**

当我们有 $Y = g(X)$，其中 g 是 X 的某个函数变换时，求 Y 的 PDF 有两种主要方法：

**方法一：CDF 法（Cumulative Distribution Function Method）**
- 步骤1：先求 Y 的累积分布函数（CDF）$F_Y(y) = P(Y \leq y)$
- 步骤2：将 $Y \leq y$ 转换为关于 X 的不等式
- 步骤3：用 X 的 PDF 积分得到 $F_Y(y)$
- 步骤4：对 CDF 求导得到 PDF：$f_Y(y) = \frac{d}{dy}F_Y(y)$

**方法二：变换公式（Transformation Formula）**
- 如果 $Y = g(X)$，且 g 是单调函数（monotonic function），则：
  $$f_Y(y) = f_X(x) \cdot \left|\frac{dx}{dy}\right|$$
  其中 $x = g^{-1}(y)$（反函数，inverse function）
- 这个公式的直观理解：PDF 要乘以"雅可比行列式（Jacobian）"来调整"密度的拉伸或压缩"

---

#### 3. 逐步求解

**验证给定的 PDF 是否合法：**

检查归一化条件（normalization condition）：
$$\int_0^1 4x^3 dx = 4 \cdot \frac{x^4}{4}\Big|_0^1 = x^4\Big|_0^1 = 1 - 0 = 1 \quad \checkmark$$

所以 $f(x) = 4x^3$ 确实是合法的 PDF。

---

#### (1) 求 $Y = X^4$ 的 PDF

**逻辑链条：**

**步骤 1：确定 Y 的取值范围（range/support）**
- 因为（because）$X \in [0,1]$
- 所以（therefore）$Y = X^4 \in [0,1]$（因为 0 的 4 次方是 0，1 的 4 次方是 1）

**步骤 2：写出 Y 的 CDF**（P形式的）
- 定义（definition）：$F_Y(y) = P(Y \leq y)$
- 代入（substitute）$Y = X^4$：$F_Y(y) = P(X^4 \leq y)$

**步骤 3：将关于 Y 的不等式转换为关于 X 的不等式**，代入x的不等式，积分求出CDF
- 因为（because）$X^4 \leq y$
- 且（and）$X \geq 0$（X 非负）
- 所以（therefore）两边开 4 次方（take the 4th root）：$X \leq y^{1/4}$
- 运用的性质（property used）：对于非负数，单调递增函数保持不等号方向

$$F_Y(y) = P(X \leq y^{1/4}) = \int_0^{y^{1/4}} f_X(x)dx = \int_0^{y^{1/4}} 4x^3 dx$$
$$F_Y(y) = 4 \cdot \frac{x^4}{4}\Big|_0^{y^{1/4}} = x^4\Big|_0^{y^{1/4}} = (y^{1/4})^4 = y$$

**步骤 6：对 CDF 求导得到 PDF**
- 运用定理（theorem）：$f_Y(y) = \frac{d}{dy}F_Y(y)$
- 计算：$f_Y(y) = \frac{d}{dy}(y) = 1$

**最终答案：**
$$f_Y(y) = 1, \quad y \in [0,1]$$

这是均匀分布（uniform distribution）！

**为什么会得到均匀分布？**
- 原因（reason）：$f_X(x) = 4x^3$ 在 [0,1] 上是递增的，越靠近 1 密度越大
- 变换 $Y = X^4$ 把 X 的值"压缩"了（小的 X 变得更小）
- 这种压缩正好抵消了原来的不均匀性，结果变成均匀分布

---

#### (2) 求 $W = e^X$ 的 PDF

**逻辑链条：**

**步骤 1：确定 W 的取值范围**（确认最终答案的有效区域，超出范围的概率为0如骰子掷到7）
- 因为（because）$X \in [0,1]$
- 且（and）指数函数（exponential function）$e^x$ 是递增的
- 所以（therefore）$W = e^X \in [e^0, e^1] = [1, e]$

**步骤 2：写出 W 的 CDF**
$$F_W(w) = P(W \leq w) = P(e^X \leq w)$$

**步骤 3：转换不等式**
- 因为（because）$e^X \leq w$
- 两边取自然对数（take natural logarithm）：$X \leq \ln(w)$
- 运用的性质（property）：ln 是单调递增函数，保持不等号方向

**步骤 4：用 X 的 PDF 计算**（这里积分的下限是由x的范围决定的，如果支撑集是整个实数轴那就要从-无穷开始积分）
$$F_W(w) = P(X \leq \ln(w)) = \int_0^{\ln(w)} 4x^3 dx$$

**步骤 5：计算积分**
$$F_W(w) = 4 \cdot \frac{x^4}{4}\Big|_0^{\ln(w)} = (\ln(w))^4$$

**步骤 6：求导得到 PDF**
- 运用链式法则（chain rule）：
$$f_W(w) = \frac{d}{dw}[(\ln(w))^4]$$
- 外层导数（outer derivative）：$4(\ln(w))^3$
- 内层导数（inner derivative）：$\frac{d}{dw}\ln(w) = \frac{1}{w}$
- 相乘：$f_W(w) = 4(\ln(w))^3 \cdot \frac{1}{w}$

**最终答案：**
$$f_W(w) = \frac{4(\ln w)^3}{w}, \quad w \in [1, e]$$

---

#### (3) 求 $Z = \log(X)$ 的 PDF

**注意：** 这里的 log 通常指自然对数（natural logarithm）ln，即以 e 为底。

**逻辑链条：**

**步骤 1：确定 Z 的取值范围**
- 因为（because）$X \in (0,1]$（注意 X=0 时 log 无定义）
- 且（and）$\ln(x)$ 在 (0,1] 上的值域是 $(-\infty, 0]$
- 所以（therefore）$Z = \ln(X) \in (-\infty, 0]$

**步骤 2：写出 Z 的 CDF**
$$F_Z(z) = P(Z \leq z) = P(\ln(X) \leq z)$$

**步骤 3：转换不等式**
- 因为（because）$\ln(X) \leq z$
- 两边取指数（exponentiate）：$X \leq e^z$
- 运用的性质（property）：指数函数是单调递增的

**步骤 4：注意定义域限制**
- 因为（because）$X \in [0,1]$
- 且（and）当 $z \leq 0$ 时，$e^z \leq 1$
- 所以（therefore）：
  - 如果 $z < 0$：$F_Z(z) = P(X \leq e^z) = \int_0^{e^z} 4x^3 dx$
  - 如果 $z \geq 0$：$F_Z(z) = P(X \leq 1) = 1$（因为 X 最大就是 1）

**步骤 5：计算积分（对于 z ≤ 0）**
$$F_Z(z) = \int_0^{e^z} 4x^3 dx = x^4\Big|_0^{e^z} = (e^z)^4 = e^{4z}$$

**步骤 6：求导得到 PDF**
$$f_Z(z) = \frac{d}{dz}(e^{4z}) = 4e^{4z}$$

**最终答案：**
$$f_Z(z) = 4e^{4z}, \quad z \in (-\infty, 0]$$

这是指数分布（exponential distribution）的一种形式！

---

#### 4. 总结与规律

**三个问题的共同方法论（methodology）：**

1. 已知X范围，求Y范围
2. **写出 CDF**（也就是P形式） → $F_Y(y) = P(Y \leq y)$
3. **转换为X主元不等式** → 将 $g(X) \leq y$ 转换为 $X \leq$ 某个表达式，**用原 PDF 积分** → 计算 $\int f_X(x)dx$
4. **对 CDF 求导** → 得到新的 PDF

**关键定理（key theorem）：**
- CDF 与 PDF 的关系：$f(x) = \frac{d}{dx}F(x)$
- 这是微积分基本定理（Fundamental Theorem of Calculus）的应用

**什么时候能用这个方法？**
- 当变换函数 g 是单调的（monotonic）时最方便
- 如果不单调，需要分段讨论或用其他方法


# Q2
#### 1. 题目翻译

**原题：**

假设 $(X,Y) \in Z = \{(x,y) \in [0,1]^2 : 0 < x+y < 1\}$ 有联合概率密度函数（joint pdf, joint probability density function）为：

$$f(x,y) = cxy(1-x-y), \quad (x,y) \in Z$$

其中 c 是某个常数（constant）。求 c 的值，以及 X 和 Y 的协方差（covariance）。

**题目要求：**
1. 找出常数 c
2. 计算 X 和 Y 的协方差

---

#### 2. 背景知识与基本概念

##### 2.1 [[联合概率密度函数（Joint PDF）]]

**定义（Definition）：**
- 对于两个连续随机变量（continuous random variables）X 和 Y
- 联合PDF $f(x,y)$ 描述了 (X,Y) 这个点在平面上的"概率密度"
- 类比：如果单变量PDF是"线上的密度"，联合PDF就是"面上的密度"

**性质（Properties）：**
1. **非负性（Non-negativity）：** $f(x,y) \geq 0$ 对所有 (x,y)
2. **归一化条件（Normalization）：** 
   $$\iint_{\text{全平面}} f(x,y) \, dx \, dy = 1$$
   - 意思：在整个可能的区域上积分，总概率等于1
   - 这是用来求常数 c 的关键条件

##### 2.2 支撑集（Support）

**这道题的支撑集 Z：**
$$Z = \{(x,y) \in [0,1]^2 : 0 < x+y < 1\}$$

**拆解这个集合：**
- $x \in [0,1]$（x 在 0 到 1 之间）
- $y \in [0,1]$（y 在 0 到 1 之间）
- $x + y < 1$（x 和 y 的和小于 1）
- $x + y > 0$（x 和 y 的和大于 0，但因为 x,y ≥ 0，这个自动满足）

**几何意义：**
- 这是单位正方形 [0,1]×[0,1] 中
- 在直线 x+y=1 下方的三角形区域
- 三个顶点是：(0,0), (1,0), (0,1)

##### 2.3 [[协方差（Covariance）]]

**定义（Definition）：**
$$\text{Cov}(X,Y) = E[XY] - E[X]E[Y]$$

**含义：**
- 协方差衡量两个随机变量的"线性相关程度"
- Cov(X,Y) > 0：正相关（X 大时 Y 倾向于大）
- Cov(X,Y) < 0：负相关（X 大时 Y 倾向于小）
- Cov(X,Y) = 0：不相关（uncorrelated）

**计算协方差需要三个期望值（Expected Values）：**
1. $E[X]$：X 的期望
2. $E[Y]$：Y 的期望
3. $E[XY]$：XY 的期望

##### 2.4 期望的计算公式

**对于联合PDF：**

**X 的期望：**
$$E[X] = \iint_Z x \cdot f(x,y) \, dx \, dy$$

**Y 的期望：**
$$E[Y] = \iint_Z y \cdot f(x,y) \, dx \, dy$$

**XY 的期望：**
$$E[XY] = \iint_Z xy \cdot f(x,y) \, dx \, dy$$

---

#### 3. 逐步求解

##### 步骤1：求常数 c（利用归一化条件）

**逻辑链条：**

**因为：** f(x,y) 是合法的PDF
**所以：** 必须满足归一化条件（normalization condition）
$$\iint_Z f(x,y) \, dx \, dy = 1$$

**代入：** $f(x,y) = cxy(1-x-y)$
$$\iint_Z cxy(1-x-y) \, dx \, dy = 1$$

**提取常数：** c 是常数，可以提到积分外面
$$c \iint_Z xy(1-x-y) \, dx \, dy = 1$$

**所以：**
$$c = \frac{1}{\iint_Z xy(1-x-y) \, dx \, dy}$$

**现在需要计算：** $I = \iint_Z xy(1-x-y) \, dx \, dy$

---

**设置积分区域（Integration Region）：**

**方法：** 先对 y 积分，再对 x 积分（或反过来）

**确定积分限（Integration Limits）：**
- x 的范围：$x \in [0, 1]$
- 对于固定的 x，y 的范围：
  - 下限：$y = 0$
  - 上限：由 $x + y < 1$ 得到 $y < 1 - x$
  - 所以 $y \in [0, 1-x]$

**写出二重积分：**
$$I = \int_0^1 \int_0^{1-x} xy(1-x-y) \, dy \, dx$$

---

**先计算内层积分（对 y）：**

$$I_{\text{inner}} = \int_0^{1-x} xy(1-x-y) \, dy$$

**展开：** $(1-x-y) = 1-x-y$
$$= \int_0^{1-x} xy(1-x) - xy^2 \, dy$$

**提取关于 y 的常数：** x 和 (1-x) 对 y 来说是常数
$$= x(1-x) \int_0^{1-x} y \, dy - x \int_0^{1-x} y^2 \, dy$$

**计算积分：**
- $\int_0^{1-x} y \, dy = \frac{y^2}{2}\Big|_0^{1-x} = \frac{(1-x)^2}{2}$
- $\int_0^{1-x} y^2 \, dy = \frac{y^3}{3}\Big|_0^{1-x} = \frac{(1-x)^3}{3}$

**代入：**
$$I_{\text{inner}} = x(1-x) \cdot \frac{(1-x)^2}{2} - x \cdot \frac{(1-x)^3}{3}$$

**化简：**
$$= \frac{x(1-x)^3}{2} - \frac{x(1-x)^3}{3}$$

**通分：**
$$= x(1-x)^3 \left(\frac{1}{2} - \frac{1}{3}\right) = x(1-x)^3 \cdot \frac{1}{6}$$

---

**现在计算外层积分（对 x）：**

$$I = \int_0^1 \frac{x(1-x)^3}{6} \, dx = \frac{1}{6} \int_0^1 x(1-x)^3 \, dx$$

**展开 $(1-x)^3$：**
$$(1-x)^3 = 1 - 3x + 3x^2 - x^3$$

**所以：**
$$x(1-x)^3 = x - 3x^2 + 3x^3 - x^4$$

**积分：**
$$\int_0^1 (x - 3x^2 + 3x^3 - x^4) \, dx$$

**逐项积分：**
$$= \left[\frac{x^2}{2} - 3 \cdot \frac{x^3}{3} + 3 \cdot \frac{x^4}{4} - \frac{x^5}{5}\right]_0^1$$

$$= \frac{1}{2} - 1 + \frac{3}{4} - \frac{1}{5}$$

**通分（公分母是20）：**
$$= \frac{10}{20} - \frac{20}{20} + \frac{15}{20} - \frac{4}{20} = \frac{10-20+15-4}{20} = \frac{1}{20}$$

**所以：**
$$I = \frac{1}{6} \cdot \frac{1}{20} = \frac{1}{120}$$

---

**求 c：**

**因为：** $c \cdot I = 1$
**所以：** $c = \frac{1}{I} = \frac{1}{1/120} = 120$

**答案：** $c = 120$

---

##### 步骤2：计算 E[X]

**公式：**
$$E[X] = \iint_Z x \cdot f(x,y) \, dx \, dy$$

**代入：** $f(x,y) = 120xy(1-x-y)$
$$E[X] = \int_0^1 \int_0^{1-x} x \cdot 120xy(1-x-y) \, dy \, dx$$

$$= 120 \int_0^1 \int_0^{1-x} x^2y(1-x-y) \, dy \, dx$$

**先计算内层积分：**
$$\int_0^{1-x} x^2y(1-x-y) \, dy$$

==**提取常数 $x^2$：（这一步特别好，因为把x这种提出来分开来只看y会更好算）**
$$= x^2 \int_0^{1-x} y(1-x-y) \, dy$$

**展开：**
$$= x^2 \int_0^{1-x} [y(1-x) - y^2] \, dy$$

$$= x^2 \left[(1-x) \int_0^{1-x} y \, dy - \int_0^{1-x} y^2 \, dy\right]$$

**计算：**
$$= x^2 \left[(1-x) \cdot \frac{(1-x)^2}{2} - \frac{(1-x)^3}{3}\right]$$

$$= x^2 \left[\frac{(1-x)^3}{2} - \frac{(1-x)^3}{3}\right]$$

$$= x^2(1-x)^3 \cdot \frac{1}{6}$$

**外层积分：**==实际计算的时候，直接把前面的这个系数漏掉了！！！千万不要漏抄，多可惜。可以在草稿纸上算出答案，减少过细的分支带来的篇幅===
$$E[X] = 120 \int_0^1 \frac{x^2(1-x)^3}{6} \, dx = 20 \int_0^1 x^2(1-x)^3 \, dx$$

**展开 $(1-x)^3 = 1 - 3x + 3x^2 - x^3$：**
$$x^2(1-x)^3 = x^2 - 3x^3 + 3x^4 - x^5$$

**积分：**
$$\int_0^1 (x^2 - 3x^3 + 3x^4 - x^5) \, dx$$

$$= \left[\frac{x^3}{3} - \frac{3x^4}{4} + \frac{3x^5}{5} - \frac{x^6}{6}\right]_0^1$$

$$= \frac{1}{3} - \frac{3}{4} + \frac{3}{5} - \frac{1}{6}$$

**通分（公分母是60）：**
$$= \frac{20}{60} - \frac{45}{60} + \frac{36}{60} - \frac{10}{60} = \frac{20-45+36-10}{60} = \frac{1}{60}$$

**所以：**
$$E[X] = 20 \cdot \frac{1}{60} = \frac{20}{60} = \frac{1}{3}$$

---

##### ==步骤3：计算 E[Y]（利用对称性）==

**观察：**
- 支撑集 Z 关于直线 y=x 对称
- ==PDF $f(x,y) = 120xy(1-x-y)$ 关于 x 和 y 对称（交换 x 和 y，函数不变）——这个性质很好用，能减少很多计算量1==

**因为：** 对称性（symmetry）
**所以：** $E[Y] = E[X] = \frac{1}{3}$

**如果不用对称性：** 可以用同样的方法计算，结果相同

---

##### 步骤4：计算 E[XY]

**公式：**
$$E[XY] = \iint_Z xy \cdot f(x,y) \, dx \, dy$$

**代入：**
$$E[XY] = \int_0^1 \int_0^{1-x} xy \cdot 120xy(1-x-y) \, dy \, dx$$

$$= 120 \int_0^1 \int_0^{1-x} x^2y^2(1-x-y) \, dy \, dx$$

**先计算内层积分：**
$$\int_0^{1-x} x^2y^2(1-x-y) \, dy$$

**提取 $x^2$：**
$$= x^2 \int_0^{1-x} y^2(1-x-y) \, dy$$

**展开：**
$$= x^2 \int_0^{1-x} [y^2(1-x) - y^3] \, dy$$

$$= x^2 \left[(1-x) \int_0^{1-x} y^2 \, dy - \int_0^{1-x} y^3 \, dy\right]$$

**计算：**
$$= x^2 \left[(1-x) \cdot \frac{(1-x)^3}{3} - \frac{(1-x)^4}{4}\right]$$

$$= x^2 \left[\frac{(1-x)^4}{3} - \frac{(1-x)^4}{4}\right]$$

$$= x^2(1-x)^4 \left(\frac{1}{3} - \frac{1}{4}\right) = x^2(1-x)^4 \cdot \frac{1}{12}$$

**外层积分：**
$$E[XY] = 120 \int_0^1 \frac{x^2(1-x)^4}{12} \, dx = 10 \int_0^1 x^2(1-x)^4 \, dx$$

**展开 $(1-x)^4$：**

使用二项式定理（binomial theorem）：
$$(1-x)^4 = 1 - 4x + 6x^2 - 4x^3 + x^4$$

**所以：**
$$x^2(1-x)^4 = x^2 - 4x^3 + 6x^4 - 4x^5 + x^6$$

**积分：**
$$\int_0^1 (x^2 - 4x^3 + 6x^4 - 4x^5 + x^6) \, dx$$

$$= \left[\frac{x^3}{3} - \frac{4x^4}{4} + \frac{6x^5}{5} - \frac{4x^6}{6} + \frac{x^7}{7}\right]_0^1$$

$$= \frac{1}{3} - 1 + \frac{6}{5} - \frac{2}{3} + \frac{1}{7}$$

**通分（公分母是105）：**
$$= \frac{35}{105} - \frac{105}{105} + \frac{126}{105} - \frac{70}{105} + \frac{15}{105}$$

$$= \frac{35 - 105 + 126 - 70 + 15}{105} = \frac{1}{105}$$

**所以：**
$$E[XY] = 10 \cdot \frac{1}{105} = \frac{10}{105} = \frac{2}{21}$$

---

##### 步骤5：计算协方差

**公式：**
$$\text{Cov}(X,Y) = E[XY] - E[X]E[Y]$$

**代入：**
$$\text{Cov}(X,Y) = \frac{2}{21} - \frac{1}{3} \cdot \frac{1}{3}$$

$$= \frac{2}{21} - \frac{1}{9}$$

**通分（公分母是63）：**
$$= \frac{6}{63} - \frac{7}{63} = -\frac{1}{63}$$

---

#### 4. 最终答案

**常数 c：**
$$c = 120$$

**协方差：**
$$\text{Cov}(X,Y) = -\frac{1}{63}$$

**协方差为负的含义：**
- X 和 Y 是负相关的（negatively correlated）
- 当 X 增大时，Y 倾向于减小
- 这符合直觉：因为 $x + y < 1$，如果 x 大了，y 就必须小一些

---

#### 5. 解题逻辑链条总结

**求常数 c：**
1. PDF 必须满足归一化条件 → $\iint f(x,y) \, dx \, dy = 1$
2. 代入 f(x,y) → 得到关于 c 的方程
3. 计算二重积分 → 得到 $c = 120$

**求协方差：**
1. 协方差公式 → $\text{Cov}(X,Y) = E[XY] - E[X]E[Y]$
2. 需要计算三个期望值 → $E[X], E[Y], E[XY]$
3. 用联合PDF计算期望 → $E[g(X,Y)] = \iint g(x,y)f(x,y) \, dx \, dy$
4. 利用对称性 → $E[Y] = E[X]$（节省计算）
5. 代入公式 → 得到 $\text{Cov}(X,Y) = -\frac{1}{63}$

**关键技巧：**
- 正确设置积分限（根据支撑集）
- 先内层后外层积分
- 利用对称性简化计算
- 仔细计算多项式积分


# Q3
#### 1. 题目翻译

假设 $U_1 \sim \mathcal{U}_{[0,1]}$ 并且独立地（independently）$U_2 \sim \mathcal{U}_{[0,1]}$。定义（Define）：

$$Z_1 = \sqrt{-2\log(U_1)}\cos(2\pi U_2)$$
$$Z_2 = \sqrt{-2\log(U_1)}\sin(2\pi U_2)$$

求 $(Z_1, Z_2)$ 的联合概率密度函数（joint PDF, joint probability density function）。

**符号说明：**
- $\mathcal{U}_{[0,1]}$：在区间 [0,1] 上的均匀分布（uniform distribution）
- $U_1, U_2$：两个独立的均匀分布随机变量
- $Z_1, Z_2$：通过变换得到的新随机变量

---

#### 2. 背景知识与基本概念

##### 2.1 Box-Muller变换

1.  **均匀分布的性质**：如果 $U \sim \text{Uniform}(0, 1)$，那么它的 PDF 是 $f(u) = 1$（因为高度 $\times$ 宽度 $1$ 必须等于总概率 $1$）。
2.  **独立性的性质**：如果两个变量相互独立，它们的联合 PDF 等于各自边缘 PDF 的乘积：
    $$f_{U_1, U_2}(u_1, u_2) = f_{U_1}(u_1) \cdot f_{U_2}(u_2) = 1 \cdot 1 = 1$$
当你使用雅可比变换法去求 $Z_1, Z_2$ 的联合分布时，公式是这样的：
$$f_{Z_1, Z_2}(z_1, z_2) = f_{U_1, U_2}(u_1, u_2) \cdot |J|$$

因为 $f_{U_1, U_2}(u_1, u_2) = 1$，所以你**实际上只需要计算雅可比行列式 $|J|$**，算出来的结果直接就是 $Z_1, Z_2$ 的联合密度函数。

##### 2.2 随机变量变换（Transformation of Random Variables）
你给出的这两个公式其实是把“均匀分布”通过两步包装成了“正态分布”：
*   **$U_2$ 负责“角度”**：$2\pi U_2$ 把 $(0, 1)$ 映射到了 $(0, 2\pi)$，这就是极坐标里的 $\theta$。
*   **$U_1$ 负责“半径”**：$\sqrt{-2\log(U_1)}$ 是通过 **逆变换采样法（Inverse Transform Sampling）** 把均匀分布转成了一个特定的分布（瑞利分布），对应极坐标里的 $R$。

**总结：**
你现在的起点是 $f(u_1, u_2) = 1$。你的目标是通过雅可比变换证明，经过这一串复杂的 $\sqrt{\log}$ 和 $\sin/\cos$ 变换后，终点会变成：
$$f_{Z_1, Z_2}(z_1, z_2) = \frac{1}{2\pi} e^{-\frac{z_1^2 + z_2^2}{2}}$$
这就是两个**独立标准正态分布**的联合 PDF。

##### 2.2
[[trick：雅可比变换法+极坐标变化（Jacobian Transformation Method）]]**

**定理（Theorem）：**
如果 $(Z_1, Z_2) = g(U_1, U_2)$ 是一个可逆变换（invertible transformation），即可以写成 $(U_1, U_2) = g^{-1}(Z_1, Z_2)$，那么：

$$f_{Z_1,Z_2}(z_1, z_2) = f_{U_1,U_2}(u_1, u_2) \cdot |J|$$

其中 $|J|$ 是雅可比行列式（Jacobian determinant）的绝对值：

$$J = \det\begin{pmatrix} \frac{\partial u_1}{\partial z_1} & \frac{\partial u_1}{\partial z_2} \\ \frac{\partial u_2}{\partial z_1} & \frac{\partial u_2}{\partial z_2} \end{pmatrix}$$

**直观理解：**
- 变换会"拉伸"或"压缩"概率密度
- 雅可比行列式 $|J|$ 衡量这种拉伸/压缩的程度
- 类比：如果你把一块橡皮泥拉长2倍，它的密度就变成原来的1/2

##### 2.3 极坐标变换（Polar Coordinates）

**观察题目中的变换：**
$$Z_1 = \sqrt{-2\log(U_1)}\cos(2\pi U_2)$$
$$Z_2 = \sqrt{-2\log(U_1)}\sin(2\pi U_2)$$

**这看起来像极坐标形式：**
- 如果设 $R = \sqrt{-2\log(U_1)}$（半径，radius）
- 设 $\Theta = 2\pi U_2$（角度，angle）
- 那么：$Z_1 = R\cos(\Theta)$，$Z_2 = R\sin(\Theta)$

**极坐标与直角坐标的关系：**
- 直角坐标（Cartesian coordinates）：$(Z_1, Z_2)$
- 极坐标（Polar coordinates）：$(R, \Theta)$
- 转换公式：$Z_1 = R\cos\Theta$，$Z_2 = R\sin\Theta$
- 反向：$R = \sqrt{Z_1^2 + Z_2^2}$，$\Theta = \arctan(Z_2/Z_1)$

---

#### 3. 逐步求解

##### 步骤1：引入中间变量（极坐标）

**为什么要引入中间变量？**
- 因为（because）：直接从 $(U_1, U_2)$ 到 $(Z_1, Z_2)$ 的反函数很复杂
- 所以（therefore）：我们先转换到极坐标 $(R, \Theta)$，再转到 $(Z_1, Z_2)$
- 策略（strategy）：分两步走，每步都简单

**定义中间变量：**
$$R = \sqrt{-2\log(U_1)}$$
$$\Theta = 2\pi U_2$$

**那么：**
$$Z_1 = R\cos\Theta$$
$$Z_2 = R\sin\Theta$$

---

##### 步骤2：从 $(U_1, U_2)$ 到 $(R, \Theta)$ 的变换

**第一步：求反函数（找 $U_1, U_2$ 用 $R, \Theta$ 表示）**

**从 $R = \sqrt{-2\log(U_1)}$ 求 $U_1$：**
- 两边平方：$R^2 = -2\log(U_1)$
- 除以 -2：$\log(U_1) = -\frac{R^2}{2}$
- 取指数：$U_1 = e^{-R^2/2}$

**从 $\Theta = 2\pi U_2$ 求 $U_2$：**
- 除以 $2\pi$：$U_2 = \frac{\Theta}{2\pi}$

**所以反函数是：**
$$U_1 = e^{-R^2/2}, \quad U_2 = \frac{\Theta}{2\pi}$$

---

**第二步：确定 $(R, \Theta)$ 的取值范围**

**因为（because）：** $U_1 \in (0, 1]$（注意0不能取，因为log(0)无定义）
**所以（therefore）：**
- $-2\log(U_1) \in [0, \infty)$（当 $U_1 \to 1$ 时，$\log(U_1) \to 0$；当 $U_1 \to 0^+$ 时，$\log(U_1) \to -\infty$）
- $R = \sqrt{-2\log(U_1)} \in [0, \infty)$

**因为（because）：** $U_2 \in [0, 1]$
**所以（therefore）：** $\Theta = 2\pi U_2 \in [0, 2\pi]$

---

**第三步：计算雅可比行列式**

**需要计算：**
$$J_1 = \det\begin{pmatrix} \frac{\partial u_1}{\partial r} & \frac{\partial u_1}{\partial \theta} \\ \frac{\partial u_2}{\partial r} & \frac{\partial u_2}{\partial \theta} \end{pmatrix}$$

**计算偏导数（partial derivatives）：**

1. $\frac{\partial u_1}{\partial r}$：
   - $u_1 = e^{-r^2/2}$
   - 链式法则（chain rule）：$\frac{\partial}{\partial r}e^{-r^2/2} = e^{-r^2/2} \cdot (-r) = -re^{-r^2/2}$

2. $\frac{\partial u_1}{\partial \theta}$：
   - $u_1$ 不含 $\theta$
   - 所以：$\frac{\partial u_1}{\partial \theta} = 0$

3. $\frac{\partial u_2}{\partial r}$：
   - $u_2 = \frac{\theta}{2\pi}$ 不含 $r$
   - 所以：$\frac{\partial u_2}{\partial r} = 0$

4. $\frac{\partial u_2}{\partial \theta}$：
   - $\frac{\partial}{\partial \theta}\left(\frac{\theta}{2\pi}\right) = \frac{1}{2\pi}$

**雅可比矩阵（Jacobian matrix）：**
$$J_1 = \begin{pmatrix} -re^{-r^2/2} & 0 \\ 0 & \frac{1}{2\pi} \end{pmatrix}$$

**行列式（determinant）：**
- 对角矩阵的行列式等于对角元素的乘积
$$|J_1| = \left|-re^{-r^2/2}\right| \cdot \frac{1}{2\pi} = \frac{r}{2\pi}e^{-r^2/2}$$

（因为 $r \geq 0$，所以 $|{-r}| = r$）

---

**第四步：写出 $(R, \Theta)$ 的联合PDF**

**运用变换公式（transformation formula）：**
$$f_{R,\Theta}(r, \theta) = f_{U_1,U_2}(u_1, u_2) \cdot |J_1|$$

**因为（because）：** $U_1, U_2$ 独立且都是 $\mathcal{U}_{[0,1]}$
**所以（therefore）：** $f_{U_1,U_2}(u_1, u_2) = 1$（当 $u_1, u_2 \in [0,1]$）

**代入：**
$$f_{R,\Theta}(r, \theta) = 1 \cdot \frac{r}{2\pi}e^{-r^2/2} = \frac{r}{2\pi}e^{-r^2/2}$$

**定义域（support）：** $r \in [0, \infty)$，$\theta \in [0, 2\pi]$

---

##### 步骤3：从 $(R, \Theta)$ 到 $(Z_1, Z_2)$ 的变换

**第一步：写出变换关系**

**正向变换：**
$$Z_1 = R\cos\Theta, \quad Z_2 = R\sin\Theta$$

**反向变换：**
$$R = \sqrt{Z_1^2 + Z_2^2}, \quad \Theta = \arctan\left(\frac{Z_2}{Z_1}\right)$$

（更准确地说，$\Theta = \text{atan2}(Z_2, Z_1)$，考虑象限）

---

**第二步：计算雅可比行列式**

**需要计算：**
$$J_2 = \det\begin{pmatrix} \frac{\partial r}{\partial z_1} & \frac{\partial r}{\partial z_2} \\ \frac{\partial \theta}{\partial z_1} & \frac{\partial \theta}{\partial z_2} \end{pmatrix}$$

**计算偏导数：**

1. $\frac{\partial r}{\partial z_1}$：
   - $r = \sqrt{z_1^2 + z_2^2}$
   - $\frac{\partial r}{\partial z_1} = \frac{1}{2\sqrt{z_1^2 + z_2^2}} \cdot 2z_1 = \frac{z_1}{r}$

2. $\frac{\partial r}{\partial z_2}$：
   - 同理：$\frac{\partial r}{\partial z_2} = \frac{z_2}{r}$

3. $\frac{\partial \theta}{\partial z_1}$：
   - 从 $\tan\theta = \frac{z_2}{z_1}$ 两边对 $z_1$ 求导
   - 隐函数求导（implicit differentiation）：$\sec^2\theta \cdot \frac{\partial\theta}{\partial z_1} = -\frac{z_2}{z_1^2}$
   - 因为 $\sec^2\theta = 1 + \tan^2\theta = 1 + \frac{z_2^2}{z_1^2} = \frac{z_1^2 + z_2^2}{z_1^2} = \frac{r^2}{z_1^2}$
   - 所以：$\frac{\partial\theta}{\partial z_1} = -\frac{z_2}{z_1^2} \cdot \frac{z_1^2}{r^2} = -\frac{z_2}{r^2}$

4. $\frac{\partial \theta}{\partial z_2}$：
   - 同理：$\frac{\partial\theta}{\partial z_2} = \frac{z_1}{r^2}$

**雅可比矩阵：**
$$J_2 = \begin{pmatrix} \frac{z_1}{r} & \frac{z_2}{r} \\ -\frac{z_2}{r^2} & \frac{z_1}{r^2} \end{pmatrix}$$

**行列式：**
$$|J_2| = \frac{z_1}{r} \cdot \frac{z_1}{r^2} - \frac{z_2}{r} \cdot \left(-\frac{z_2}{r^2}\right)$$

$$= \frac{z_1^2}{r^3} + \frac{z_2^2}{r^3} = \frac{z_1^2 + z_2^2}{r^3} = \frac{r^2}{r^3} = \frac{1}{r}$$

---

**第三步：写出 $(Z_1, Z_2)$ 的联合PDF**

**运用变换公式：**
$$f_{Z_1,Z_2}(z_1, z_2) = f_{R,\Theta}(r, \theta) \cdot |J_2|$$

**代入：**
$$f_{Z_1,Z_2}(z_1, z_2) = \frac{r}{2\pi}e^{-r^2/2} \cdot \frac{1}{r}$$

**化简：**
$$= \frac{1}{2\pi}e^{-r^2/2}$$

**用 $z_1, z_2$ 表示：**
- 因为 $r^2 = z_1^2 + z_2^2$
$$f_{Z_1,Z_2}(z_1, z_2) = \frac{1}{2\pi}e^{-(z_1^2 + z_2^2)/2}$$

**定义域：** $(z_1, z_2) \in \mathbb{R}^2$（整个平面）

---

##### 步骤4：识别分布类型

**观察PDF的形式：**
$$f_{Z_1,Z_2}(z_1, z_2) = \frac{1}{2\pi}e^{-(z_1^2 + z_2^2)/2}$$

**可以分解为：**
$$= \frac{1}{\sqrt{2\pi}}e^{-z_1^2/2} \cdot \frac{1}{\sqrt{2\pi}}e^{-z_2^2/2}$$

**识别（recognize）：**
- $\frac{1}{\sqrt{2\pi}}e^{-z_1^2/2}$ 是标准正态分布（standard normal distribution）$\mathcal{N}(0,1)$ 的PDF
- $\frac{1}{\sqrt{2\pi}}e^{-z_2^2/2}$ 也是 $\mathcal{N}(0,1)$ 的PDF

**结论（conclusion）：**
- $Z_1$ 和 $Z_2$ 都服从标准正态分布
- 且它们是独立的（因为联合PDF可以分解为两个边缘PDF的乘积）

---

#### 4. 最终答案

**$(Z_1, Z_2)$ 的联合概率密度函数（joint PDF）：**

$$f_{Z_1,Z_2}(z_1, z_2) = \frac{1}{2\pi}\exp\left(-\frac{z_1^2 + z_2^2}{2}\right), \quad (z_1, z_2) \in \mathbb{R}^2$$

**或者写成：**
$$f_{Z_1,Z_2}(z_1, z_2) = \frac{1}{\sqrt{2\pi}}e^{-z_1^2/2} \cdot \frac{1}{\sqrt{2\pi}}e^{-z_2^2/2}$$

**分布类型：**
- $Z_1 \sim \mathcal{N}(0, 1)$（标准正态分布）
- $Z_2 \sim \mathcal{N}(0, 1)$（标准正态分布）
- $Z_1$ 和 $Z_2$ 独立（independent）

---

#### 5. 解题逻辑链条总结

**整体策略：分步变换**

1. **因为：** 直接从 $(U_1, U_2)$ 到 $(Z_1, Z_2)$ 太复杂
   **所以：** 引入中间变量 $(R, \Theta)$（极坐标）

2. **第一步变换：** $(U_1, U_2) \to (R, \Theta)$
   - 求反函数 → $U_1 = e^{-R^2/2}$，$U_2 = \Theta/(2\pi)$
   - 计算雅可比行列式 → $|J_1| = \frac{r}{2\pi}e^{-r^2/2}$
   - 运用变换公式 → $f_{R,\Theta}(r,\theta) = \frac{r}{2\pi}e^{-r^2/2}$

3. **第二步变换：** $(R, \Theta) \to (Z_1, Z_2)$
   - 这是标准的极坐标到直角坐标变换
   - 计算雅可比行列式 → $|J_2| = \frac{1}{r}$
   - 运用变换公式 → $f_{Z_1,Z_2}(z_1,z_2) = \frac{1}{2\pi}e^{-(z_1^2+z_2^2)/2}$

4. **识别分布：**
   - 联合PDF可分解为两个独立的标准正态分布的乘积
   - 这就是著名的Box-Muller变换（Box-Muller transform）

**关键定理和性质：**
- 雅可比变换定理（Jacobian transformation theorem）
- 独立随机变量的联合PDF等于边缘PDF的乘积
- 极坐标变换的雅可比行列式是 $r$

**这个方法的应用场景：**
- 当你需要从一个分布生成另一个分布的随机数时
- 特别是从均匀分布生成正态分布（计算机随机数生成的常用方法）
- 任何涉及多个随机变量复杂变换的问题