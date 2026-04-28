# Q1

#### 问题翻译
某批灯泡的平均寿命为1000小时，标准差为100小时。随机抽取100个灯泡，求它们的平均寿命大于1050小时的概率。

#### 背景条件解释
**基本概念**：
- **中心极限定理 Central Limit Theorem (CLT)** 大样本均值的分布趋于正态
- **样本均值 Sample Mean** $\bar{X} = \frac{1}{n}\sum_{i=1}^{n} X_i$
- **标准化 Standardization** 转换为标准正态分布的过程
- **大数定律 Law of Large Numbers** 样本均值收敛到总体均值

**具体条件**：
- 总体分布：$X_i \sim (\mu, \sigma^2)$
- 均值：$\mu = 1000$ 小时
- 标准差：$\sigma = 100$ 小时
- 样本量：$n = 100$ 个灯泡
- 求解：$P(\bar{X} > 1050)$

#### 解答思路

**步骤1：理解中心极限定理**
- 中心极限定理：
  - 如果 $X_1, X_2, \ldots, X_n$ 是独立同分布的随机变量
  - $E[X_i] = \mu$, $Var(X_i) = \sigma^2$
  - 当 $n$ 足够大时，样本均值 $\bar{X}$ 近似服从正态分布
  - $\bar{X} \sim N(\mu, \frac{\sigma^2}{n})$

**步骤2：确定样本均值的分布**
- 根据CLT：
  $$\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(1000, \frac{100^2}{100}\right) = N(1000, 100)$$
- 所以：
  - $E[\bar{X}] = \mu = 1000$
  - $Var(\bar{X}) = \frac{\sigma^2}{n} = \frac{10000}{100} = 100$
  - 标准差：$\sigma_{\bar{X}} = \sqrt{100} = 10$

**步骤3：进行标准化**
- 标准化公式：
  $$Z = \frac{\bar{X} - \mu}{\sigma/\sqrt{n}} = \frac{\bar{X} - 1000}{10}$$
- 所以：
  $$P(\bar{X} > 1050) = P\left(Z > \frac{1050 - 1000}{10}\right) = P(Z > 5)$$

**步骤4：计算概率**
- 标准正态分布：
  $$P(Z > 5) = 1 - \Phi(5)$$
- 查标准正态分布表：
  - $\Phi(5) \approx 0.9999997$
  - 所以 $P(Z > 5) \approx 1 - 0.9999997 = 0.0000003$

#### 关键概念总结
- **中心极限定理 Central Limit Theorem** 大样本均值趋于正态分布
- **样本均值 Sample Mean** $\bar{X} = \frac{1}{n}\sum X_i$ 样本的平均值
- **标准化 Standardization** $Z = \frac{\bar{X} - \mu}{\sigma/\sqrt{n}}$ 转换为标准正态
- **标准误差 Standard Error** $\sigma_{\bar{X}} = \frac{\sigma}{\sqrt{n}}$ 样本均值的标准差
- **大数定律 Law of Large Numbers** 样本均值收敛到总体均值

---

# Q2

#### 问题翻译
假设某大学学生的平均身高为170cm，标准差为5cm。随机抽取25名学生，求：
1. 样本平均身高在168cm到172cm之间的概率
2. 样本平均身高大于175cm的概率
3. 样本平均身高小于165cm的概率

#### 背景条件解释
**基本概念**：
- **中心极限定理 Central Limit Theorem** 大样本均值的正态近似
- **样本均值分布 Sample Mean Distribution** $\bar{X} \sim N(\mu, \frac{\sigma^2}{n})$
- **标准化 Z-score** 样本均值相对于总体均值的标准差数
- **概率区间 Probability Interval** 事件发生的概率范围

**具体条件**：
- 总体分布：学生身高 $X_i \sim (\mu, \sigma^2)$
- 总体均值：$\mu = 170$ cm
- 总体标准差：$\sigma = 5$ cm
- 样本量：$n = 25$ 名学生
- 求解：不同身高区间的概率

#### 解答思路

**步骤1：确定样本均值的分布**
- 根据中心极限定理：
  $$\bar{X} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(170, \frac{25}{25}\right) = N(170, 1)$$
- 所以：
  - $E[\bar{X}] = 170$ cm
  - $Var(\bar{X}) = \frac{5^2}{25} = \frac{25}{25} = 1$ cm²
  - 标准差：$\sigma_{\bar{X}} = \sqrt{1} = 1$ cm

**步骤2：计算168cm到172cm之间的概率**
- $P(168 < \bar{X} < 172) = P\left(\frac{168-170}{1} < Z < \frac{172-170}{1}\right)$
- 计算Z值：
  - $Z_1 = \frac{168-170}{1} = -2$
  - $Z_2 = \frac{172-170}{1} = 2$
- 所以 $P(-2 < Z < 2) = \Phi(2) - \Phi(-2)$
- 利用对称性：$\Phi(-2) = 1 - \Phi(2)$
- 查表：$\Phi(2) \approx 0.9772$
- $\Phi(-2) = 1 - 0.9772 = 0.0228$
- $P(-2 < Z < 2) = 0.9772 - 0.0228 = 0.9544$

**步骤3：计算大于175cm的概率**
- $P(\bar{X} > 175) = P\left(Z > \frac{175-170}{1}\right) = P(Z > 5)$
- $Z = \frac{175-170}{1} = 5$
- $P(Z > 5) = 1 - \Phi(5) \approx 1 - 0.9999997 = 0.0000003$
- 这是一个极小的概率，几乎不可能发生

**步骤4：计算小于165cm的概率**
- $P(\bar{X} < 165) = P\left(Z < \frac{165-170}{1}\right) = P(Z < -5)$
- $Z = \frac{165-170}{1} = -5$
- $P(Z < -5) = \Phi(-5) \approx 0.0000003$
- 这也是一个极小的概率

#### 关键概念总结
- **中心极限定理 Central Limit Theorem** $\bar{X} \approx N(\mu, \frac{\sigma^2}{n})$
- **样本均值分布 Sample Mean Distribution** 样本均值的正态分布
- **标准化 Standardization** $Z = \frac{\bar{X} - \mu}{\sigma/\sqrt{n}}$
- **标准误差 Standard Error** $\sigma_{\bar{X}} = \frac{\sigma}{\sqrt{n}}$
- **概率区间 Probability Interval** 事件发生的概率范围