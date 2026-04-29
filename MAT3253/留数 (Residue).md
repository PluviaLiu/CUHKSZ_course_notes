留数是劳伦展开 (Laurent expansion) 中 $\dfrac{1}{z - z_0}$ 项的系数，记作 $\text{Res}(f; z_0)$。

对于**极点 (pole)** 的留数计算，最常用两个公式：

- **简单极点 (simple pole)**，即一阶极点：

$$\text{Res}(f; z_0) = \lim_{z \to z_0} (z - z_0) f(z)$$

- **$m$ 阶极点 (pole of order $m$)**：

$$\text{Res}(f; z_0) = \frac{1}{(m-1)!} \lim_{z \to z_0} \frac{d^{m-1}}{dz^{m-1}} \left[(z-z_0)^m f(z)\right]$$