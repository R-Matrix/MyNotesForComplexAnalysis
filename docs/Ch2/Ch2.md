---
time : "2025-11-02"
---

# Chapter2 - Cauchy's Theorem and Its Applications

/// quote | Quote

<span style = "font-family: 'Times New Roman';">
The solution of a large number of problems can be reduced, in the last analysis, to the evaluation of definite integrals; thus mathematicians have been muchoccupied with this task... However, among many results obtained, a number were initially discovered bythe aid of a type of induction based on the passagefrom real to imaginary. Often passage of this kind led directly to remarkable results. Nevertheless this part of the theory, as has been observed by Laplace, is subject to various diﬃculties... After having reﬂected on this subject and brought together various results mentioned above, I hope to establish the passage from the real to the imaginary based on a direct and rigorous analysis; my researches have thus led me to the method which is the object of this memoir...
</span>

-- $A.L.Cauchy\, , 1827$
///

## Context

对应 `复变函数简明教程` Ch3 的内容.
主要有 `Goursat定理`, `Cauchy定理` , `Liouville定理`, `Morera定理`, `Cauchy不等式`.

- Stein : `Schwarz Reflect Principle`, `Runge's approximation theorem`
- 复变函数简明教程: `Schwarz引理` 及 非欧几何介绍

同时, 在复变函数简明教程这本书中关于 Cauchy定理 的证明有误, 详细可看 Stein 的 Complex Analysis 的 **Appendix B: Simple Connectivity and Jordan Curve Theorem**. 

*如果有时间我可能会在第二章目录下面梳理并翻译.*

## Exercise

### Exercise 1

/// Question | Exercise 1  $\quad$ ( From Stein Ch2 ET1 )

Prove that

\[\int_0^\infty \sin(x^2)dx = \int_0^\infty \cos(x^2) dx = \frac{\sqrt {2\pi}}{4}.\]

These are the **Fresnel integrals.** Here, $\int_0^\infty$ is interpreted as $\lim_{R \to \infty} \int_0^R .$
[Hint : Integrate the function $e^{-x^2}$ over the path in Figure 14. Recall that $\int_0^\infty e^{-x^2} dx = \sqrt \pi.$]

![Figure 14. The contour in Exercise 1](../img/Ch2/Figure1.svg)
/// figure-caption | 14
The contour in Exercise 1
///

///

/// proof
取 $e^{-z^2}$ 为被积函数, 围道$C$如上图. 由柯西定理, 知

\[ \int_C e^{-z^2}dz = 0.    
\]

我们考虑圆弧

\[\Gamma_R = \{z = Re^{i\theta} : 0 \le \theta \le \frac{\pi}{4}\}, \]

放缩有, 

\begin{align}
\left| \int_{\Gamma_R}e^{-z^2} dz \right| &= \left| \int_0^{\frac{\pi}{4}} e^{R^2(\cos 2\theta + \mathrm{i} \sin 2\theta)} \mathrm{i}Re^{\mathrm{i}\theta} d\theta \right|\\ 
&\le R\int_0^\frac{\pi}{4} e^{-R^2\cos 2\theta} d\theta.
\end{align}

下面我们来估计阶. 对于 $\forall \varepsilon, 0 < \varepsilon < 1$, $\exists \delta > 0$ 使得在 $[\frac{\pi}{4}-\delta, \frac{\pi}{4}]$ 上有

\[-2(\theta - \frac{\pi}{4}) \ge \cos 2\theta \ge -2(\theta - \frac \pi 4) \times \varepsilon, \]

这是由 $\cos 2\theta$ 在 $\frac{\pi}{4}$ 处的 Taylor 公式得来的. 于是有

\[\int_{\frac \pi 4 - \delta} ^ \frac \pi 4 Re^{-R^2[-2(\theta - \frac \pi 4)]} d\theta \le
\int_{\frac \pi 4 - \delta} ^ \frac \pi 4 Re^{-R^2\cos 2\theta} d\theta \le
\int_{\frac \pi 4 - \delta} ^ \frac \pi 4 Re^{-R^2[-2(\theta - \frac \pi 4)\varepsilon]} d\theta,  \]

计算得, 

\[\frac{1-e^{-2\delta R^2}} {2R} \le \int_{\frac \pi 4 - \delta} ^ \frac \pi 4 Re^{-R^2\cos 2\theta} d\theta \le \frac{1-e^{-2\varepsilon\delta R^2}} {2\varepsilon R}, \]

全部乘以 $2R$ 再令 $R \to \infty$ 得

\[ 1 \le \lim_{R \to \infty} 2R \times R\int_{\frac \pi 4 - \delta} ^ \frac \pi 4 Re^{-R^2\cos 2\theta} d\theta \le \frac 1 \varepsilon. \]

由于 $0 < \varepsilon < 1$ 的任意性, 令 $\varepsilon \to 1$, 即得

\[R\int_{\frac \pi 4 - \delta} ^ \frac \pi 4 Re^{-R^2\cos 2\theta} d\theta \sim \frac 1 {2R} \to 0, \: R \to \infty.\]

显然又有

\[R\int_{\frac \pi 4 - \delta} ^ \frac \pi 4 Re^{-R^2\cos 2\theta} d\theta = O(Re^{-\varepsilon R^2}), \: \varepsilon > 0.\]

于是

\[\lim_{R \to \infty} \int_{\Gamma_R}e^{-z^2}dz = 0.\]

回到最初的围道积分, 在 $\theta = \frac \pi 4$ 射线上带入 $z = xe^{i\frac{\pi}{4}}$ 有

\[\int_0^\infty (\frac {\sqrt2} 2 \cos x^2 + \frac {\sqrt2} 2 \sin x^2) + i (\frac {\sqrt2} 2 \cos x^2 - \frac {\sqrt2} 2 \sin x^2) dx = \frac {\sqrt\pi} 2\]

比较实部和虚部即有 

\[\int_0^\infty \sin(x^2)dx = \int_0^\infty \cos(x^2) dx = \frac{\sqrt {2\pi}}{4}.\]
///

<!-- /// details | "另一个我的证明"
    type : proof

利用积分

\[ \int_0^\infty e^{-x^2} dx = \frac{\sqrt \pi}{2}.\]

从而考虑

\[\int_0^\infty \cos x^2 - \mathrm{i} \int_0^\infty \sin x^2 dx = \int_0^\infty e^{-ix^2} dx = \frac 1\xi \int_0 ^\infty e^{-(\xi x)^2} d(\xi x) = \bar \xi \frac {\sqrt \pi} 2 \]

然后比较实部和虚部即可.

/// -->


/// remark | Remark
我们有一般的 Fresnel 积分公式

\[\int_0^\infty \sin x^k dx = \frac 1k \Gamma(\frac 1k) \sin (\frac \pi {2k}), \]

\[\int_0^\infty \cos x^k dx = \frac 1k \Gamma(\frac 1k) \cos (\frac \pi {2k}). \]

其中 $k > 1$.
///

---

### Exercise 2

/// Question | Exercise 2  $\quad$ ( From Stein Ch2 ET2 )

Show that $\int_{0}^\infty \frac{\sin x}{x} dx = \frac{\pi}{2}.$

[Hint: THe integral equals $\frac{1}{2i}\int_{-\infty}^{+\infty}\frac{e^{ix}-1}{x}dx.$ Use the indented semicircle.]
///

/// Proof | Proof

利用欧拉公式, 我们首先有

\[\int_0^\infty \frac {\sin x} x dx = \int_0^\infty \frac {e^{ix} - e^{-ix}} {2ix} dx = \frac{1}{2i}\int_{-\infty}^{+\infty} \frac {e^{ix}} x dx.\]

考虑函数 $\frac{e^{iz}}{z}$, 围道 $\Gamma = \Gamma_R \cup \Gamma_\varepsilon \cup [\pm\varepsilon, \pm R]$, 其中大小圆弧分别为

\[\Gamma_R = \{Re^{i\theta} : 0 \le \theta \le \pi\}, \quad \Gamma_\varepsilon = \{\varepsilon e^{i\theta} : 0 \le \theta \le \pi\}.\]

在大圆弧十, 由控制收敛定理

\begin{align}
\lim_{R \to \infty} \left| \int_{\Gamma_R} \frac{e^{iz}}{z} dz \right| &= \lim_{R \to \infty} \left|\int_0^\pi \frac {e^{iR(\cos \theta + i \sin \theta)}}{Re^{i\theta}} Re^{i\theta} d\theta\right|\\ 
&\le \lim_{R \to \infty} \int_0^\infty e^{-R\sin \theta} d\theta\\
&= 0. 
\end{align}

另一方面, 在小圆弧上, 由控制收敛定理有

\[\lim_{\varepsilon \to 0} \int_{\Gamma_\varepsilon} \frac {e^iz} z dz = \pi i.\]

于是有

\[ \int_{-\infty}^{+\infty} \frac{e^{ix}}{x}dx = \lim_{R \to \infty, \varepsilon \to 0} \int_\Gamma \frac{e^iz} z dz  = \pi i,  \]

故而

\[\int_0^\infty \frac{\sin x}{x} dz = \frac 1 {2i} \int_{-\infty}^{+\infty} \frac{e^ix}{x}dx = \frac \pi 2. \]
///

/// remark
这实际上是著名的 Dirichlet 积分, 有许多证明方法和应用.
///

---
### Exercise 3
/// Question | Exercise 3  $\quad$ ( From Stein Ch2 ET3 )

Evaluate the integrals

\[\int_0^\infty e^{-ax}\cos bx\: \mathrm{d}x \quad\text{and}\quad \int_0^\infty e^{-ax}\sin bx\: \mathrm{d}x, \qquad a>0\]

by integrating $e^{-Ax}, A = \sqrt{a^2 + b^2}$, over an approxiate sector with angle $w$, with $\cos w = a / A.$

///

/// proof
首先有

\[\int_0^\infty e^{-ax}\cos bx\: \mathrm{d}x + i \int_0^\infty e^{-ax}\sin bx\: \mathrm{d}x = \int_0^\infty e^{-(a-ib)x} \mathrm{d}x.\]

考虑函数 $e^{-Az}, A = \sqrt{a^2 + b^2}$, 取围道为: 以$[0, R]$ 和 $[0, Re^{i\theta}]$ 为边的扇形, 其中 $w = \arg (a-ib)$. 则在圆弧上有

\[\left|\int_C e^{-Az}dz \right| \le \int_0 ^ w e^{-AR\cos \theta}\mathrm{d}\theta \to 0, \quad R \to \infty, \]

其中用到 $\cos \theta \ge \cos w = \frac{a}{\sqrt{a^2 + b^2}} > 0$ 以及控制收敛定理. 于是有

\[\int_0^\infty e^{-(a-ib)}e^{iw} \mathrm{d}x = \int_0^\infty e^{-Ax}\mathrm{d}x = \frac 1A, \]

比较实部和虚部得

\begin{cases}
a\int_0^\infty e^{-ax}\cos bx \:\mathrm {d}x + b \int_0^\infty e^{-ax}\sin bx \: \mathrm{d}x  = 1,\\
\\
-b\int_0^\infty e^{-ax}\cos bx \:\mathrm {d}x + a \int_0^\infty e^{-ax}\sin bx \: \mathrm{d}x  = 0,\\
\end{cases}

解得

\[\int_0^\infty e^{-ax}\cos bx \:\mathrm {d}x = \frac a {a^2 + b^2}, \quad \int_0^\infty e^{-ax}\sin bx \:\mathrm {d}x = \frac b {a^2 + b^2}.\]
///

---
### Exercise 4
/// Question | Exercise 4  $\quad$ ( From Stein Ch2 ET4 )
Prove that for all $\xi \in \mathbb{C}$ we have 

$$e^{-\pi\xi^2} = \int_{-\infty}^{+\infty}e^{-\pi x ^ 2}e^{2\pi i x\xi} \:dx.$$
///

/// details | Tips
    type : tip
在正文部分的例题 P42 Example 1 证明了 

> if $\xi \in \mathbb{R}$, then
>
> \[e^{-\pi\xi^2} = \int_{-\infty}^{+\infty}e^{-\pi x ^ 2}e^{2\pi i x\xi} \:dx.\]
///

/// proof
设 $\xi = a + \mathrm{i} b \in \mathbb{C}$, 则

\begin{align}
\int_{-\infty}^{\infty}e^{-\pi x ^ 2}e^{2\pi i x\xi} \:dx &= \int_{-\infty}^{+\infty}e^{-\pi x ^ 2}e^{2\pi i xa} e^{-2\pi xb}\:dx\\
&= e^{\pi b^2}\int_{-\infty}^{\infty}e^{-\pi (x + b) ^ 2}e^{2\pi i xa} \:dx\\
&= e^{\pi b^2}\int_{-\infty}^{\infty}e^{-\pi x ^ 2}e^{2\pi i (x-b)a} \:dx\\
&= e^{\pi b^2} e^{-2\pi i ab} \int_{-\infty}^{\infty}e^{-\pi x ^ 2}e^{2\pi i xa} \:dx\\
&= e^{\pi b^2} e^{-2\pi i ab} e^{-\pi a^2}\\
&= e^{-\pi \xi^2}.
\end{align}
///

---
### Exercise 5
/// Question | Exercise 5  $\quad$ ( From Stein Ch2 ET7 )
Suppose $f : \mathbb{D} \to \mathbb{C}$ is holomorphic. Show that the diameter $d = \sup_{z, w \in \mathbb{D}}|f(z) - f(w)|$ os the image of $f$ satisfies

\[2|f'(0)|\le d.\]

Moreover, it can be shown as that equality holds precisely when $f$ is linear, $f(z) = a_0 + a_1 z.$

**Note**. In connection with this result, see the relationship between the diameter of a curve and Fourier series described in Problem 1, Chapter 4, Book 1.

[Hint: $2f'(0) = \frac{1}{2\pi i}\int_{|\zeta| = r}\frac{f(\zeta) - f(-\zeta)}{\zeta^2}\: d\zeta$ whenever $0 < r < 1$.]
///

/// proof
依据 Hint, 我们有

\begin{align}
2|f'(0)| &= \left| \frac{1}{2\pi i}\int_{|\zeta| = r}\frac{f(\zeta) - f(-\zeta)}{\zeta^2}\: d\zeta\right|\\
&\le \frac{1}{2\pi}\int_{|\zeta| = r}\frac{|f(\zeta) - f(-\zeta)|}{|\zeta^2|}\: |d\zeta| \\
&\le \frac{1}{2\pi}\int_{|\zeta| = r}\frac{d}{r^2}\: ds\\
&= \frac d r
\end{align}

上式对任意 $0 < r < 1$ 都成立, 依 $r$ 的任意性, 令 $r \to 1^-$ 有 $2 |f'(0)| \le d.$
///

/// details | Remark
    type : remark
    open : False
下文来自 Stein. *Fourier Analysis*. Chapter 4 PT1.

> This problem explore another relationship between the geometry of a curve and Fourier series. The diameter od a curve $\Gamma$ parametrized by $\gamma(t) = (x(t), y(t))$ on $[-\pi, \pi]$ is defined by
>
> \[d = \sup_{P, Q \in \Gamma} |P - Q| = \sup_{t_1, t_2 \in [-\pi, \pi]}|\gamma(t_1) - \gamma_(t_2)|.\]
>
> if $a_n$ is the $n^{\text{th}}$ Fourier coefficient of $\gamma(t) = x(t) + iy(t)$ and $l$ denote the length of $\Gamma$, then
>
> 1. $2|a_n| \le d$ for all $n \ne 0$.
> 2. $l \le \pi d$, whenever $\Gamma$ is convex.
>
> Property (1) follows from the fact that
>
> \[2a_n = \frac 1 {2\pi} \int_{-\pi} ^{\pi} [\gamma(t) - \gamma(t+\pi / n)]e^{-int}\: dt.\]
>
> The equality $l = \pi d$ is satisfied when $\Gamma$ is a circle, but surprisingly, this is not the only case. In fact, one finds that $l = \pi d$ is equivalent to $2|a_1| = d$. We re-parametrize $\gamma$ so that for each $t$ in $[-\pi, \pi]$ the tangent to the curve makes an angle $t$ with the $y$-axis. Then, if $a_1 = 1$ we have
>
> \[\gamma'(t) = ie^{it}(1+r(t)), \]
>
> where $r$ is a real-valued function which satisfies $r(t) + r(t + \pi) = 0.$ and $|r(t)| \le 1.$ Figure 7(a) shows the curve obtained by setting $r(t) = \cos (5t)$. Also, Figure 7(b) consists of the curve where $r(t) = h(3t)$, with $h(s) = -1$ if $-\pi \le s \le 0$ and $h(s) = 1$ if $0 < s < \pi$. This curve (which is only piecewise of class $C^1$) is known as the Reuleaux triangle and is the classical example of a curve of constant width which is not a circle.
>
> ![Figure 7](https://pic3.zhimg.com/v2-a34d85214b84251f200e0bd63e6126f2_r.jpg "Figure 7")
> /// caption
> Figure 7
> ///

第一问即为上面的题, 第二问详细见 [知乎链接](https://zhuanlan.zhihu.com/p/656110940 "Stein 《Fourier Analysis》 Chapter 4 习题解答(3) From 元亨利贞");

*知乎作者为 元亨利贞*
///

---
### Exercise 6
/// Question | Exercise 6  $\quad$ ( From Stein Ch2 ET8 )
If $f$ is a holomophic function on the strip $-1 < y < 1, x \in \mathbb{R}$ with

\[|f(z)| \le A(1+|z|)^\eta, \quad \eta\: \text{ is a fixed real number}\]

for all $z$ in that strip, show that for each integer $\eta \ge 0$ there exists $A_n \ge 0$ so that

\[|f^{(n)}(x)| \le A_n (1 + |x|)^\eta, \quad \text{for all $\:x \in \mathbb{R}$}.\]

[Hint: Use the Cauchy inequalities.]
///

/// proof
利用 Cauchy不等式, 有

\[|f^{(n)}(z)|\le \frac{n!\|f\|}{R^n} \le \frac{n!A(1+|z|)^\eta}{R^n}.\]

取 $R = 1 /2$, 即上式为 $|f^{(n)}(z)|\le n!\,2^nA(1+|z|)^\eta$, 这对于任意 $|z-x| < 1 /2$ 都成立.

那么令 $k = (\frac 3 2)^\eta$ , 对任意 $x \in \mathbb{R}$ 满足 

$$
\sup_{|z-x|=1/2}(1+|z|)^\eta \le (\frac 3 2 + |x|)^\eta \le  k \cdot (1+|x|)^\eta.$$

令 $A_n = n!\, 2^n k A$ 即可.
///

---
### Exercise 7
/// Question | Exercise 7  $\quad$ ( From Stein Ch2 ET9 )
Let $\Omega$ be a bounded open subset of $\mathbb{C}$, and $\varphi : \Omega \to \Omega$ a holomorphic function. Prove that if there exists a point $z_0 \in \Omega$ such that

\[\varphi(z_0) = z_0\qquad \text{and} \qquad \varphi'(z_0) = 1\]

then, $\varphi$ is linear.

[Hint: Why can one assume that $z_0 = 0$? Write $\varphi(z) = z + a_nz^n + O(z^{n+1})$ near 0, and prove that if $\varphi_k = \varphi \circ \cdots \circ \varphi$(where $\varphi$ appears $k$ times), then $\varphi_k(z) = z + ka_nz^n + O(z^{n+1})$. Apply the Cauchy inequalities and let $k \to \infty$ to conclude the proof. Here we use the standard $O$ notation, where $f(z) = O(g(z))$ as $z \to 0$ means that $|f(z)| \le C|g(z)|$ for some contant $C$ as $|z| \to 0$.]
///

/// proof
不妨设 $\varphi(0) = 0$, 否则考虑令 $f(z) = \varphi(z + x_0) - z_0$

由于 $\varphi$ 全纯, 因此在 $0$ 处幂级数展开, 得到 $\varphi(z) = z + a_n z^n + O(z^{n+1})$.

利用数学归纳法可知, 

\[\varphi_{k}(z) = z + ka_n z^n + O(z^{n+1}).\]

由于 $\varphi : \Omega \to \Omega$ 且 $\Omega$ 是有界区域, 因此 $|\varphi(z)| \le \operatorname{sup}_{w \in \partial \Omega}(0, w) := M$

也即 $\forall z \in \Omega, |\varphi_k(z)| \le M$

对 $\varphi_k(z)$ 利用 Cauchy 不等式, 得到

\[|ka_n| \le \frac M {R^n}\]

令 $k \to \infty$, 得 $a_n \to 0$, 也即 $\varphi(z) = z.$
///

/// Remark
和上述题比较相像的几个定理.

/// theorem | 定理 1  (Schwarz 引理)
设 $f (z)$ 是从单位圆盘 $D(0, 1)$ 到自身的解析映射, 满足 $f(0) = 0$, 则

1. $\forall z \in D(0, 1)$, $|f(z)| \le |z|$, 且 $|f'(0)| \le 1$;

2. 存在 $z_0 \ne 0$ 使得 $|f(z_0)| = |z_0|$ 或 $|f'(0)| = 1$ 的充要条件是 $f(z) = e^{i\theta}z$, 其中 $\theta \in [0, 2\pi]$ 为常数.
///

/// theorem | 定理 2 (Bieberbach 猜想)
如果 $f(z) = z + a_2z^2 + a_3z^3 + \cdots$ 在 $|z| < 1$ 上单叶, 则 $|a_n| \le n$. 等号成立对某个 $n$ 成立的充要条件是 $f(z)$ 是 Koebe 函数 $K(z) = \frac z {(1-z)^2}$ 的旋转 $k_\theta(z) = e^{-i\theta}K(e^{i\theta}z)$.
///

/// theorem | 定理 3 (Koebe 1/4 - 定理)
设 $f$ 在 $\mathbb{D} = D(0, 1)$ 上单叶且 $f(0) = 0, f'(0) = 1$. 则 $f(\mathbb{D})\supset D(0, \frac 14)$. 并且有偏差估计


1. \(\frac{1-|z|}{(1+|z|)^3} \le |f'(z)| \le \frac {1+|z|}{(1-|z|)^3} \);
   
2. $|\arg f'(z)| \le 2 \ln \frac{1+|z|}{1-|z|}$; 
   
3. $\frac{|z|}{(1+|z|)^2} \le |f(z)| \le \frac{|z|}{(1-|z|)^2}$.

如果不存在 $w \in f(\mathbb{D})$ 使得 $|w| = \frac 14$, 则 $f(z) = k_\theta(z).$

后面两个定理可以参考 
[知乎链接1](https://zhuanlan.zhihu.com/p/25379347 "单叶函数猜想(1): Loewner的贡献 From 单叶函数猜想(1): Loewner的贡献"), 
[知乎链接2](https://zhuanlan.zhihu.com/p/67912434 "复变函数学习笔记(14)——Koebe-Bieberbach定理、deBranges定理 From Fiddie")
///
///

---
### Exercise 8
/// Question | Exercise 8  $\quad$ ( From Stein Ch2 ET10 )
Weierstrass’s theorem states that a continuous function on $[0, 1]$ can be uni-
formly approximated by polynomials. Can every continuous function on the closed
unit disc be approximated uniformly by polynomials in the variable $z$?
///
/// proof
不成立, 如取 $f(z) = Re(z).$
///
/// remark
在正文中, 介绍到了 **Runge's approximation theorem**
/// theorem | 定理 4 (龙格逼近定理)
每一个在包含紧集 $K$ 的开集内全纯的函数可以被奇点在 $K^c$ 上的有理函数一致逼近，如果 $K^c$ 是连通集，上述函数可以在 $K$ 上被多项式一致逼近。
///
///

---
### Exercise 9
/// Question | Exercise 9  $\quad$ ( From Stein Ch2 ET11 )
Let $f$ be a holomorphic function on the dist $D_{R_0}$ centered at the origin and of radius $R_0$.

(a) Prove that whenever $0 < R < R_0$ and $|z| < R$, then
 
$$
f(z) = \frac 1 {2\pi} \int_{0}^{2\pi} f(Re^{i\varphi})\mathrm{Re}\left(\frac {Re^{i\varphi}+z}{Re^{i\varphi}-z} \right) \: d\varphi.
$$

(b) Show that

\[\mathrm{Re}\left(\frac {Re^{i\gamma}+r}{Re^{i\gamma}-r} \right) = \frac {R^2 - r^2}{R^2 - 2Rr\cos \gamma + r^2}\]

[Hint: For the first part, note that if $w = R^2 / \bar z$, then the integral of $f(\zeta)/(\zeta - w)$ around the circle of radius $R$ centered at the origin is zero. Use this, together with the usual Cauchy integral formal, to deduce the desired identity.]