---
time : "2025-11-02"
---

# Chapter1 - Preliminaries to Complex Analysis

/// quote | Quote
The sweeping  development of mathematics during the last two centuries is due in large part to the inductionn of complex numbers; paradoxically, this is based on the seemingly absurd notion that three are numbers whose squares are negative.

-- $E. Borel\, , 1952$
///

## Context

对应 `复变函数简明教程` Ch1, Ch2, Ch3 的内容.
主要有 `复数和复平面的基本性质` , `解析函数的 C-R 方程` , `幂级数展开` , `分式线性变换` , `简单曲线上的积分`

## Exercise

> **练习1** `(From Stein Ch1 ET4)` Show that it is impossible to define a total ordering on C. In other words, one cannot find a relation $\prec$ between complex numbers so that:
> 
> 1.  For any two complex numbers z, w, one and only one of the following is true : $z \prec w$, $w\prec z$ or $z = w$.
   
> 2.  For all $z_1, z_2, z_3 \in \mathbb{C}$ the relation $z_1 \prec z_2$ implies $z_1 + z_3 \prec z_2 + z_3$.
   
> 3.  Moreover, for all $z_1, z_2, z_3 \in \mathrm{C}$ with $0 \prec z_3$, then $z_1 \prec z_2$ implies $z_1z_3 \prec z_2z_3$.
>
>[Hint: First check if $0 \prec i$ is possible.]

**解答** :
不妨设 $0 \prec i$ , 那么 $0 \cdot i \prec i \cdot i$, 即 $0 \prec -i$, 两边加 $i$, 有 $i \prec 0$, 矛盾! <span style="float:right">$\square$</span>

---

> **练习2** `(From Stein Ch1 ET8)` Suppose $U$ and $V$ are open set in complex plane. Prove that if $f : U \to V$ and $g : V \to \mathbb{C}$ are two functions that are difficrentable (in the real sense, that is, as functions of the two real variables $x$ and $y$), and $h = g \circ f$, then
> 
$$ \frac{\partial h}{\partial z} = \frac {\partial g}{\partial z} \frac{\partial f}{\partial z} + \frac{\partial g}{\partial \bar z} \frac{\partial \bar f}{\partial z}$$
>
> and 
>
>$$ \frac{\partial h}{\partial \bar z} = \frac {\partial g}{\partial z} \frac{\partial f}{\partial \bar z} + \frac{\partial g}{\partial \bar z} \frac{\partial \bar f}{\partial \bar z}$$
>
>This is the complex version of the chain rule.

**证明** :
直接把 $f$ 写成 $w = f(z, \bar z)$ 的形式 , 再令 $g(f) = g(f, \bar f)$, 于是 $g \circ f$ 变为

$$h(z, \bar z) = g(w, \bar w) = g(f(z, \bar z), \bar f (z, \bar z)).$$

那么

$$\frac{\partial h}{\partial z} = g_ww_z + g_{\bar w}\bar w_z = g_zf_z + g_{\bar z}\bar f_z $$

$$\frac{\partial h}{\partial \bar z} = g_ww_{\bar z} + g_{\bar w}\bar w_{\bar z} = g_zf_{\bar z} + g_{\bar z}\bar f_\bar z $$ 

<span style="float:right">$\square$</span>

---

> **练习3** `(From Stein Ch1 ET9)` Show that in polar coordonates, the Cauchy-Riemann equations take the form
>
> $$\frac{\partial u}{\partial r} = \frac 1r \frac{\partial v}{\partial \theta} \qquad \text{and} \qquad  \frac 1r \frac{\partial u}{\partial \theta} = - \frac{\partial v}{\partial r}$$

**证明** :
设 $x = r\cos \theta, y = r \sin \theta$, 那么

$$\frac{\partial}{\partial r} = \frac{\partial}{\partial x}\cos \theta + \frac{\partial}{\partial y}\sin \theta ,  \quad \frac{\partial}{\partial \theta} = - r \frac{\partial}{\partial x}\sin \theta + r\frac{\partial}{\partial y}\cos \theta.$$

带入 C-R 方程化简即得. <span style="float:right">$\square$</span>

---
**Remark** : <font color = "rgba(2888, 100, 255)"> 若将 $f(x, y) $ 写成 $ R e^{i \Theta}$ 的形式 </font>
设 $f (z) = u(x, y) + i v(x, y) = R(x, y) \exp(i \Theta(x, y))$, 也即

$$u = R\cos \Theta, \qquad v = R\sin \Theta$$

从而,

$$\frac{\partial u}{\partial x} = \frac{\partial R}{\partial x}\cos \Theta - r\frac{\partial \Theta}{\partial x}\sin \Theta\quad, \qquad \frac{\partial u}{\partial y} = \frac{\partial R}{\partial y}\cos \Theta - R\frac{\partial \Theta}{\partial y}\sin \Theta $$

和

\[
 \frac{\partial v}{\partial x} = \frac{\partial R}{\partial x}\sin \Theta + R\frac{\partial \Theta}{\partial x}\cos \Theta \quad, \qquad \frac{\partial v}{\partial y} = \frac{\partial R}{\partial y}\sin \Theta + R\frac{\partial \Theta}{\partial y} \cos \Theta
\]

由 Cauchy-Riemann 方程, 得

$$\frac{\partial R}{\partial x}\cos \Theta - R\frac{\partial \Theta}{\partial x}\sin \Theta = \frac{\partial R}{\partial y}\sin \Theta + R\frac{\partial \Theta}{\partial y}\cos \Theta$$

$$\frac{\partial R}{\partial y}\cos \Theta - R\frac{\partial \Theta}{\partial y}\sin \Theta = -\left(\frac{\partial R}{\partial x}\sin \Theta + R\frac{\partial \Theta}{\partial x}\cos \Theta\right)$$

整理得方程组

$$\begin{pmatrix}
    R_x - R\Theta_y & -R_y - R\Theta_x\\
    R_y + R\Theta_x & R_x - R\Theta_y
\end{pmatrix} \begin{pmatrix}\cos \Theta \\ \sin \Theta\end{pmatrix} = 0$$

1. 若 $(\cos \Theta \quad \sin \Theta)^T = 0$, 那么 $\cos \Theta = \sin \Theta = 0$, 这与恒等式 $\cos ^ 2 \Theta + \sin ^ 2 \Theta = 1$ 矛盾!
2. 若 $(\cos \Theta \quad \sin \Theta)^T \ne 0$, 则左边的系数矩阵不可逆, 行列式为 0, 得到
   
$$(R_x - R\Theta_y)^2 + (R_y + R\Theta_x)^2 = 0.$$

因此 $R_x = R\Theta_y, \: R_y = -R\Theta_x$. <span style="float:right">$\square$</span>

---

> **练习4** `(From Stein Ch1 ET12)` Consider the function defined by
> 
> $$f(x + iy) = \sqrt{|x||y|}, \quad \text{whenever} \:\: x, y \in \mathbb{R}.$$
> 
> Show that $f$ is satisfies the Cauchy-Riemann equtions at the origin, yet $f$ is not holomorphic at 0.

**证明** :
计算得

$$\frac{\partial u}{\partial x} =
\begin{cases}
    \frac 12 \sqrt{\frac{|y|}{|x|}} &, x > 0\\
    -\frac 12 \sqrt{\frac{|y|}{|x|}} &,  x < 0\\
    0 &, x = 0, y= 0\\
    \text{不存在} &, x = 0, y \ne 0
\end{cases}
$$

$$\frac{\partial u}{\partial y} =
\begin{cases}
    \frac 12 \sqrt{\frac{|x|}{|y|}} &, y > 0\\
    -\frac 12 \sqrt{\frac{|x|}{|y|}} &,  y < 0\\
    0 &, x = 0, y= 0\\
    \text{不存在} &, x \ne 0, y = 0
\end{cases}
$$

$$\frac{\partial v}{\partial x} = \frac{\partial v}{y} = 0$$

从而 $f$ 在 $(0, 0)$ 处满足 C-R 方程, 但是显然不解析.<span style="float:right">$\square$</span>

> **练习5** `(From Stein Ch1 ET13)` Suppose that $f$ is holomorphic in an opan set $\Omega$. Prove that in any one of the following cases :
> 
> 1. $\mathrm{Re}f$ is constant;
> 
> 1. $\mathrm{Im}f$ is constant;
> 
> 1. $|f|$ is constant;
> 
> one can conclude that $f$ is contstant.

**证明** :
假设不为常数, 利用开映射定理导出矛盾.<span style="float:right">$\square$</span>

---

> **练习6** `(From Stein Ch1 ET14)` Suppose $\{a_n\}_{n = 1}^N$ and $\{b_n\}_{n = 1}^N$ are two finite sequences of complex numbers. Let $B_k = \sum_{n=1}^k b_n$ denote the partial sums of the series $\sum b_n$  with the convention $B_0 = 0$. Prove **the summation by parts** formula
> 
> $$\sum_{n =M}^N a_nb_n = a_NB_N - a_MB_{M-1} - \sum_{n=M}^{N-1}(a_{n+1}-a_n)B_n. $$

**证明** :

$$
\begin{align*}
    \sum_{n = M}^N a_nb_n &= \sum_{n = M}^N a_n(B_n - B_{n-1})\\
    &= \sum_{n = M}^N a_nB_n - \sum_{n = M}^N a_nB_{n-1}\\
    &=a_NB_N + \sum_{n = M}^{N-1} a_{n}B_n -\sum_{n = M - 1}^{N-1} a_{n+1}B_n\\
    &=a_NB_N - a_MB_{M-1} - \sum_{n=M}^{N-1}(a_{n+1}-a_n)B_n.
\end{align*}
$$

<span style="float:right">$\square$</span>

---

> **练习7** `(From Stein Ch1 ET15)`**Abel's theorem.** Suppose $\sum_{n=1}^\infty a_n$ converges. Prove that
> 
> $$\lim_{r \to 1, \: r < 1} \sum_{n=1}^\infty r^na_n = \sum_{n=1}^\infty a_n.$$
>
> [Hint: Sum by parts.] In other words, if a series converges, then it is Abel summable with the same limit. For the preeise definition of these terms, and more information on summability methods, we refer the reader to Book I, Chapter 2.

**证明** :
直接计算有

$$(1-r)\sum_{n=1}^NA_nr^n = \sum_{n=1}^NA_nr^n-\sum_{n=2}^{N+1}A_{n-1}r^n = \sum_{n=1}^N a_nr^n - A_Nr^{N+1}.$$

注意到有 $A_n \to A$, 可知 $A_n$ 有界. 而 $r \in [0, 1)$, 于是有 $A_Nr^{N+1} \to 0, N \to \infty$.
因此在上式中令 $N \to \infty$ 得

$$(1-r)\sum_{n=1}^{\infty}A_nr^n = \sum_{n=1}^{\infty}a_nr^n.$$

下证 : $\displaystyle\lim_{r \to 1^-} (1-r)\sum_{n=1}^\infty A_nr^n = A$

$\forall \varepsilon > 0$, 由$A_n \to A$知, $\exists N_0, \forall n > N_0, |A_n - A| < \varepsilon$; 又$A_n$ 有界, 存在$M > 0,$ 使得$|A_n| \le M, |A|\le M,$ 取 $\delta = \dfrac{\varepsilon}{2N_0M}$, 于是当 $1 - \delta < r < 1$ 时, 有

$$
\begin{align*}
    |(1 - r)\sum_{n = 1}^\infty A_nr^n - A| &= |(1 - r)\sum_{n = 1}^\infty (A_n - A)r^n - (r-1)A|\\
    &\le |(1-r)\sum_{n=1}^{N_0}(A_n - A)r^n| + |(1-r)\sum_{n = N_0 + 1}^\infty (A_n - A)r^n| + |(r-1)A|\\
    &\le (1-r)\sum_{n=1}^{N_0}|A_n - A|r^n + (1-r)\sum_{n=N_0+1}^\infty |A_n -A|r^n + \delta M\\
    &\le (1-r)2MN_0 + (1-r)\sum_{n=0}^\infty r^n\varepsilon + \delta M\\
    &\le 2\varepsilon + \dfrac{\varepsilon}{2N_0}
\end{align*}
$$

这说明

$$\lim_{r \to 1^-} \sum_{n=1}^\infty a_nr^n = \lim_{r \to 1^-} (1-r)\sum_{n=1}^\infty A_nr^n = A.$$

也即 $\sum a_n$ 可阿贝尔求和, 且 Abel 和为原级数$A$. <span style="float:right">$\square$</span>

---
**Remark** : <font color = "rgba(2888, 100, 255)"> 下文来自 Stein《 Fourier Analysis》Chapter2 ET13 </font>

> The purpose of this exercise is to prove that Abel summability is stronger than  the standard or Cesàro methods of summation.
> 
> 1. Show that if the series $\sum_{n=1}^\infty c_n$ of complex numbers converges to a finite limit $s$, then the series is Abel summable to $s$.
> 
> 2. However, show that there exists series which are Abel summable, but that do not converge.[Hint: Try $c_n = (-1)^n$. What is the Abel limit of $c_n$?]
> 
> 3. Argue similarly to prove that if a series $\sum_{n=1}^\infty c_n$ is Cesàro  summable to $\sigma$, then it is Abel summable to $\sigma$. [Hint: Note that \(
\sum_{n=1}^\infty c_nr^n = (1-r)\sum_{n=1}^\infty n\sigma_nr^n\)
>and assume $\sigma = 0$.]
> 
> 
> 4. Give an example of a series that is Abel summable but not Cesàro summable. [Hint: Try $c_n = (-1)^{n-1}n$. Note that if $\sum c_n$ is Cesàro summable, then $c_n / n$ tends to zero.]
>
> The results above can be summarized by the following implications about series: 
> 
> \[\text{convergent} \Rightarrow \text{Cesàro summable} \Rightarrow \text{Abel summable} \]
>
> and the fact that none of the arrows can be reversed.

证明来源[知乎链接](https://zhuanlan.zhihu.com/p/651968522), 下为知乎截图
<!-- ![xxx](./Pictures/Ch1/Zhihu1.jpeg)
![xxx](Pictures/Ch1/Zhihu2.jpeg) -->

/// details | 展开阅读截图1(图片较长)
    type : tip
![知乎图表](../img/Ch1/Zhihu1.jpeg)
///

/// details | 展开阅读截图2(图片较长)
    type : tip
![知乎图表](../img/Ch1/Zhihu2.jpeg)
///

*来源于知乎
作者: 元亨利贞*

---

> **练习8** `(From Stein Ch1 ET21)` Show that for $|z| < 1$, one has 
> 
> $$\frac{z}{1-z^2}+ \frac{z^2}{1-z^4}+\cdots + \frac{z^{2^n}}{1-z^{2^{n+1}}}+\cdots =\frac{z}{1-z}.$$
>
> and 
> 
> $$\frac{z}{1+z} + \frac{2z^2}{1+z^2}+\cdots +\frac{2^kz^{2^k}}{1+z^{2^k}}+\cdots =\frac{z}{1-z}.$$
>
> Justify any change in the order of summation.
> [Hint: Use the dyadic expansion of an integer and the fact that $2^{k+1} - 1 = 1 + 2 + 2^2 + \cdots + 2 ^ k$.]

**证明** :
对上面一式, 有

$$\text{LHS}= \sum_{k=0}^\infty z^{2k+1} + \sum_{k=0}^\infty z^{4k+2}+\cdots +\sum_{k=0}^\infty z^{2^{n+1}k+2^n}+\cdots=\sum_{n=0}^\infty\sum_{k=1}^\infty z^{2^{n+1}k+2^n}.$$

\[\text{RHS}=\sum_{k=0}^\infty z^l.\]

对于二元组$(n_1, k_1), (n_2, k_2)\in \mathbb{N}^2$, 不妨设$n_2 \ge n_1$, 若

\[(2k_1+1)2^{n_1}=(2k_2+1)2^{n_2} \Leftrightarrow 2k_1+1 =(2k_2+1)2^{n_2-n_1}, \]

则必有$n_1=n_2$, 否则$(2k_2+1)2^{n_2-n_1}$为偶数, 而$2k_1+1$为奇数, 上式不可能成立, 于是上式进一步变为

\[2k_1+1=(2k_2+1)2^{n_2-n_1}=2k_2+1,\]

即又有$k_1=k_2$. 因此对于不同的二元组$n, k$, 求和式中的$z^{2^{n+1}k+2^n}$的指数部分不同, 故而左式求和的每一项都对于右式求和中不同的某一项, 从而左式包含右式.

另一方面, 由二进制, $\forall l \in \mathbb{Z}_+$都有唯一的二进制分解

\[l=a_02^0+a_12^1+\cdots +a_m2^m+\cdots,\]

其中$a_m$等于 $0$ 或 $1$, 并且 $a_m$ 不全为 $0$. 设 $a_n$ 是第一个不为 $0$ 的数, 即

\[a_0=a_1= \cdots =a_{n-1} = 1, \]

因此$n\in \mathbb{N}$并且有

\[l=2^n(1+2k), k=a_{n+1}2^0+a_{n+2}2^1+\cdots \in \mathbb{N},  \]

因此 $\forall l \in \mathbb{Z}_+$, 右式求和中的 $z^l$ 都能在左式求和中找到某一项 $z^{2^{n+1}k+2^n}$ 与其对应, 即右式包含左式.

因此左右两式中的每一项都是一一对应的, 并且由于绝对收敛求和顺序可以打乱, 所以

\[\sum_{n=0}^\infty \sum_{k=0}^\infty z^{2^{n+1}k+2^n}=\sum_{l=1}^\infty z^l. \]

再看第二个式子

注意到 $\frac{1}{z-1}+\frac{1}{z+1}=\frac{2z}{z^2-1}.$
将 $z$ 替为 $z^{2^k}$ 并两边同乘之以$2^kz^{2^k}$得

\[ \frac{2^kz^{2^k}}{z^{2^k}+1} =  \frac{2^{k+1}z^{2^{k+1}}}{z^{2^{k+1}}-1}-\frac{2^kz^{2^k}}{z^{2^k}-1}.\]

因此 

$$\text{LHS} = \sum_{k=0}^\infty \frac{2^{k+1}z^{2^{k+1}}}{z^{2^{k+1}}-1}-\frac{2^kz^{2^k}}{z^{2^k}-1} = -\frac{z}{z-1} =\frac{z}{1-z}.$$ 

<span style="float:right">$\square$</span>

---

> **练习9** `(From Stein Ch1 ET23)` Consider the function $f$ defined on $\mathbb{R}$ by
> 
> \[f(x) = \begin{cases}0&, \text{if } x \le 0, \\e^{-1 / x^2}&, \text{if } x > 0.\end{cases}\]
>
> Prove that $f$ is indefinitely differentiable on $\mathbb{R}$, and that $f^{(n)}(0) = 0$ for all $n>1$. Consider that $f$ does not have a converging power series expansion $\sum_{n=0}^\infty a_nx^n$ for $x$ near the origin.


**证明** :
当$x>0$时, 这个函数显然是无穷此可导的. 我们要证明当它在 $x=0$ 处可无穷此可导. 先求 $f'(0)$. 做变换 $u=1/t$ 之后可见

\[ f'(0)=\lim_{t\to 0}\frac{f(t) - f(0)}{t} = \lim_{t \to 0}\frac{e^{-1/t^2}}{t} = \lim_{u \to \infty}\frac{u}{e^{u^2}} = 0. \]

由此得出

\[f'(x) = \begin{cases}0&, \text{if }x \le 0, \\\frac{2}{x^3}e^{-1/x^2}&, \text{if }x > 0. \end{cases}\]

我们用归纳法证明: 当 $x > 0$ 且 $n \in \mathbb{N}^+$ 时, 有

\[f^{(n)}(x) = P_n(\frac 1x)e^{-1/x^2}.\]

这里 $P_n(t)$ 是 $t$ 的 $3n$ 次多项式. 当 $n = 1$ 时, 上面的计算表明这是对的. 设 $P_k(t)$ 是 $t$ 的 $3k$ 次多项式, 那么当 $x > 0$ 时, 

\[f^{(k+1)}(x) = \left(P_k(\frac 1x) e^{-1/ x^2} \right)' = \left(P_k(\frac 1x)\frac 2{x^3} - P'_k(\frac 1x)\frac 1{x^2}\right)e^{-1/ x^2}. \]

因此, 

\[P_{k+1}(t) = 2t^3P_k(t)-t^2P'_k(t).\]


由归纳假设, $P_k(t)$ 是 $t$ 的 $3(k+1)$ 次多项式. 现在来证明 $f^{(n)}(0) = 0$ 对一切的 $n \in \mathbb{N}^+$ 均成立. 仍用归纳法. 当 $n = 1$ 时结论已被证明. 设 $f^{(k)}(0) = 0$, 于是

$$f^{(k+1)}(0) = \lim_{t \to 0} \frac{f^{(k)}(t) - f^{(k)}(0)}{t} = \lim_{t \to 0} \frac{f^{(k)}(t)}{t} = \lim_{t \to 0} P_k(\frac 1t)\frac{e^{-1/t^2}}{t} = \lim_{u \to \infty}\frac{uP_k(u)}{e^{u^2}} = 0$$

从而知 $a_n \equiv 0$, 进而 $f(x) \ne \sum_{n = 0}^\infty a_nx^n.$ <span style="float:right">$\square$</span>

---

**Remark** : **<font color = "red"> 这是一个重要的反例!!! 从而我们知道无穷可微函数不一定是实解析函数 </font>**
即 $C^w \subsetneq C^\infty$

上面这个函数在原点附近的任何开邻域都不收敛, 原因是 $f(z) = e^z$ 在无穷远点有**本质奇点(Essential singualrity)**.

---

## 作业题节选

> **习题1** : `(From Ch1 HWXT17)` 设 $U, V$ 是 $\mathbb{C}$ 中的区域, 映射 $f : U \to V$ 称为**开映射**, 如果 $f$ 将$U$ 中的开集映成 $V$ 中的开集; $f$ 称为**逆紧**的, 如果对 $V$ 中的任意紧集 $K \subset V$, $f^{-1}(K)$ 是 $U$ 中的紧集. 证明 : 如果 $f$ 是开且逆紧的映射, 则 $f(U) = V$.

**证明** :
假设 $f$ 非满, 则存在点 $v \in V$ 使得 $v \notin f(U)$. 由于 $f$ 是开映射, $f(U)$ 是 $V$ 中的开集.

+ 我们断言 $f(U) \subsetneq (\overline{f(U)}\cap V)$. 这相当于是说 $f(U)$ 是 $V$- 子拓扑空间中的真开集.  
  假如 $f(U)$ 在 $V$- 拓扑子空间中即开又闭, 从而 $f(U)$ 是 $V$ 的联通分支. 此时只能有 $f(U) = V.$ 矛盾.

存在点 $v \in V \cap (\partial f(U))$, 即 $V$ 属于 $f(U)$ 的边界的点. 对于这样的 $v$, 由于 $V$ 是开集, 存在 $\delta > 0$ 使得有闭圆盘$D_\delta = \{z \in V : |z-v|\le \delta \} \subset V$. 对于每个$n \in \mathbb{N}$, 定义 $D_n = \{z\in V : |z - v| \le \delta / n\}$, 则 $D_n$ 是紧集, 且 $D_{n+1} \subset D_n$.

由于 $v$ 属于 $f(U)$ 的闭包, 故每个 $D_n$ 包含 $f(U)$ 中的点, 从而 $f^{-1}(U) \ne \emptyset$. 由条件, 紧集的原像是紧集, 所以每个 $K_n = f^{-1}(D_n)$ 是紧集, 且由 $D_{n+1} \subset D_n$, 有 $K_{n+1} \subset K_n$, 即 $\{K_n\}$是非空紧集套.

存在复平面中, 紧集套的非空交非空. 任取 $u \in \bigcap _{n=1}^\infty K_n$, 则对每个 $n$, 有 $u \in K_n$, 对应的有 $f(u) \in D_n$. 由于 $f(u) \in \bigcap_{n=1}^\infty D_n = \{v\}$, 这与 $v \in f(U)$ 矛盾! 因此 $f$ 是满射.
<span style="float:right">$\square$</span>