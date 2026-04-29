当被积函数含有 $\sin ax$ 或 $\cos ax$（即三角函数 (trigonometric function)）时，**不能**直接用"分母次数比分子高 $\geq 2$"的大圆弧引理，而要用约当引理 (Jordan's Lemma)。

约当引理说的是：若 $f(z) \to 0$ 当 $|z| \to \infty$（分母次数比分子至少高 1），且 $a > 0$，则：

$$\int_{\Gamma_R} f(z) e^{iaz} \, dz \to 0 \quad (R \to \infty)$$

其中 $\Gamma_R$ 是上半平面的半圆弧。

**关键技巧：** 对于含 $\sin ax$ 的积分，我们把它写成复指数 (complex exponential) 的虚部 (imaginary part)：

$$\sin ax = \text{Im}(e^{iax})$$

所以：

$$\int_{-\infty}^{\infty} \frac{x^3 \sin ax}{x^4+4} \, dx = \text{Im}\left(\int_{-\infty}^{\infty} \frac{x^3 e^{iax}}{x^4+4} \, dx\right)$$
