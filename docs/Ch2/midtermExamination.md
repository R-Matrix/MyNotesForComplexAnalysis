---
time : "2025-12-06"
---
# 复分析期中考试

课程代码 : MATH 2609-02

参考书籍 : 谭小江, 伍胜健. 复变函数简明教程. 北京大学出版社, 2006

主要内容(以复变函数简明教程为准) : 

1. 第一章(复数和复数域)
2. 第二章(解析函数)
3. 第三章(Cauchy定理和Cauchy公式) 

## **声明** : 

- ***由于笔者本人是B卷, 所以下面的题号顺序以B卷为例***
- ***下面的内容为笔者本人的答案及感悟, 不确为标准答案, 请读者自已判断对误和以自己情况吸收. 笔者本人对其答案不作担保或其他责任.*** *如果您认为下面的内容有问题或者有其他更好的想法, 欢迎在 github 上提 issue 或者 [发邮件到该邮箱](mailto: dsq1961248553@outlook.com)*

## 主要试题内容及解析

### 第一题(12分)
/// question
设曲线 $\gamma(t) = te^{it}$, 方向为从 $t = 0$ 到 $t = \pi$. 分别计算以下曲线积分

(1) $\int_\gamma \bar z dz;\quad$  
(2) $\int_\gamma |z| dz;\quad$  
(3) $\int_\gamma |z||dz|; \quad$  
(4) $\int_\gamma z(1+|z|^2)^{-1/2}|dz|.$
///

/// details | 解答
    type : proof
$z = \gamma(t) = te^{it}(t \in [0, \pi])$, $\quad dz = (1+it)e^{it}dt$, 

$|z| = |te^{it}| = t$, $\quad |dz| = |\gamma'(t)|dt = \sqrt {1 + t^2} dt$

--- 

(1)

\[\int_\gamma \bar z dz = \int_0 ^ \pi te^{it}(1+it)e^{it} dt = \int_0^\pi t + it^2 dt = (\frac 12 t^2 + \frac i 3 t^3 )\bigg| _0 ^ \pi = \frac 12 \pi^2 + i \frac 3 {\pi^2}. \]

---

(2)

\[\int_\gamma |z|dz = \int_0^\pi t(1+it)e^{it} dt \overset {\text{两次分部积分}}{===} 2 - \pi ^ 2 - i \pi.\]

---

(3)

\[\int_\gamma |z||dz| = \int_0 ^ \pi t\sqrt{1 + t^2}  dt = \frac 13 (1 + t^2)^{\frac 3 2} \bigg| _ 0 ^ \pi = \frac 13 [(1 + \pi ^ 2)^{\frac 32} - 1]\]

---

(4)

\[\int_\gamma z(1+|z|^2)^{-1/2}|dz| = \int_0^\pi te^{it}dt = -2 + i \pi\]
///


---


### 第二题(10分)

/// question
假设 $f : D(0, 1) \to D(0, 1)$ 是解析映射.

(1) 证明 : 对任意 $z \in D(0, 1)$ 都成立 $|f(z) - f(-z)| \le 2|z|.$

(2)上式对某 $z_0 \in D(0, 1)\backslash \{0\}$ 成立等号的充要条件是什么?
///

/// details | 解答
    type : proof
(1) 令 $g(z) = \frac{f(z) - f(-z)}{2}$, 那么 $g : D(0, 1) \to D(0, 1)$ 且 $g(0) = 0$.

由 **Schwarz** 引理得, $|g(z)| \le |z|$, 即 $|f(z) - f(-z)| \le 2|z|.$

(2) 若上式等号成立, 充要条件为 $g(z) = e^{i\theta}z$, 其中 $\theta \in[0, 2\pi]$ 为常数. 下面证明 $f(z) = e^{i\theta}z$ 为充分必要条件.

必要性是容易验证的.

对于充分性, 我们利用 $2g(z) = f(z) - f(-z)$ 两边同时求导, 有 $f'(0) = e^{i\theta}.$

而对于从单位圆盘到单位圆盘的解析映射 $h$ 一定形如 $h(z) = \frac {f(0) + e^{i\theta}z}{1 + \overline{f(0)}e^{i\theta}z}.$ 因此得 $f(0) = 0$, 从而 $f(z) = e^{i\theta}z.$
///

/// remark
关于教材的Schwarz引理在[第109页](../RefSource/Complex_Analysis_zh_cn.pdf/#page=109 "这里不知道为什么无法跳转指定页码, 这里的功能有待查询")
///

---

### 第三题(12分)

///question
求将 $1, 0, -1$ 分别映射至 $i, 1 + i, 1$ 的分式线性映射 $L(z)$, 并求

(1) 单位圆周 $\{|z| = 1\}$;  
(2) 单位开圆盘 $\{|z| <> 1\}$;  
(3) 虚轴 $\mathfrak{R}z = 0$

在 $L$ 映射下的像.
///

/// details | 解答
    type : proof
我们这里当然可以设四个系数进行方程组求解, 这里使用分式线性变换保持交比进行计算.

$$(z, 1, 0, -1) = (L(z), i, 1 + i, 1)$$

即

\[\frac{(z - 0)(1 - (-1))}{(z - (-1))(1 - 0)} = \frac {(L(z) - (1 + i))(i - 1)}{(L(z) - 1)(i - (1 + i))}\]

化简得

\[L(z) = -\frac{1 + i}{iz - 1}.\]

由于分式线性变换把圆和直线映为圆或直线, 从而再考虑点 $z = i$, $L(i) = \frac{1 + i}{2} := w_4$, 发现 $w_1 = i, w_3 = 1$ 与 $w_4$ 三点共线($w_4$ 恰为 $w_1$ 与 $w_3$ 中点), 因此 $L$ 把单位圆周映为直线 $l_1 : x + y - 1 = 0$.

由于分式线性变换在 $\overline {\mathbb C}$ 是解析的, 具有保向性, 从而只需要判断把单位圆盘内部映为直线上方或下方. 考虑 $L(0) = 1 + i$, 因此把单位圆盘映为 $x + y - 1 > 0$ 的区域.

不妨设 $z = it, t \in \mathbb R$, 那么 $L(z) = \frac {1 + i}{1 + t} = \frac {1}{1 + t} + i \frac {1}{1 + t}$, 其满足 $\text{Im}(L(z)) = \text{Re}(L(z))$ , 从而 $L$ 把虚轴映为直线 $x - y = 0$.
///