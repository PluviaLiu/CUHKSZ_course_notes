当被积函数在**实轴上有极点 (pole on the real axis)**（这里是 $z=0$），普通半圆围道会直接穿过极点，不合法。

解决方法：在 $z=0$ 处绕一个**小半圆 $\gamma_\varepsilon$**（半径 $\varepsilon$，在实轴上方），绕过去。

整个围道 $C$ 由四段组成：

$$C = [-R, -\varepsilon] + (-\gamma_\varepsilon) + [\varepsilon, R] + \Gamma_R$$

其中：
- $[-R,-\varepsilon]$ 和 $[\varepsilon, R]$：实轴上避开原点的两段
- $\gamma_\varepsilon$：绕过 $z=0$ 的**小半圆弧**（逆时针方向的上半圆，但我们走的是顺时针，所以带负号）
- $\Gamma_R$：大半圆弧