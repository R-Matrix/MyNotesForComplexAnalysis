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

(1) $\int_\gamma \bar z dz;\quad$ (2) $\int_\gamma |z| dz;\quad$ (3) $\int_\gamma |z||dz|; \quad$ (4) $\int_\gamma z(1+|z|^2)^{-1/2}|dz|.$
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
关于教材的[12](../RefSource/Complex_Analysis_zh_cn.pdf/#page=100)


///