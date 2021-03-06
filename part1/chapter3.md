# 第3章 函数的增长

## 练习

### 3.1-1

> 假设 $$f(n)$$ 与 $$g(n)$$ 都是渐进非负函数。使用 $$\Theta$$ 记号的基本定义来证明 $$max(f(n),g(n))=\Theta(f(n)+g(n))$$ 。

首先我们有：

$$
max(f(n),g(n))-(f(n)+g(n))=-min(f(n),g(n))\leq 0
$$

接着我们又有：

$$
max(f(n),g(n))-1/2(f(n)+g(n))\\=1/2(max(f(n),g(n))-min(f(n),g(n)))\geq 0
$$

所以存在 $$c_1=1/2$$ ， $$c_2=1$$ ， $$n_0=1$$ 使得 $$0\leq c_1(f(n)+g(n))\leq max(f(n),g(n))\leq c_2(f(n)+g(n))$$ 对所有的 $$n\geq n_0$$ 恒成立，得证。

### 3.1-2

> 证明：对任意实常量 $$a$$ 和 $$b$$ ，其中 $$b>0$$ ，有 $$(n+a)^b=\Theta(n^b)$$ 。

我们试图使 $$c_1n^b\leq (n+a)^b\leq c_2n^b$$ ，取 $$c_1=d_1^b$$ ， $$c_2=d_2^b$$ 。所以我们现在的目的是找到 $$d_1$$ 和 $$d_2$$ 满足 $$d_1n\leq n+a\leq d_2n$$ 。所以存在 $$0\lt d_1\lt 1$$ ，对所有的 $$n\geq n_1=max(\lceil -a/(1-d_1) \rceil,1)$$ ，有 $$d_1n\leq n+a$$ ；存在 $$d_2\gt 1$$ ，对所有的 $$n\geq n_2=max(\lceil a/(d_2-1) \rceil,1)$$ ，有 $$n+a\leq d_2n$$ 。综上，存在 $$c_1\gt 0$$ ， $$c_2\gt 0$$ ， $$n_0=max(n_1,n_2)\gt 0$$ ，使得对所有 $$n\geq n_0$$ ，有 $$0\leq c_1n^b\leq (n+a)^b\leq c_2n^b$$ ，所以 $$(n+a)^b=\Theta(n^b)$$ 。

### 3.1-3

> 解释为什么“算法 $$A$$ 的运行时间至少是 $$O(n^2)$$ ”这一表述是无意义的。

柯南连载了至少不超过20年。

### 3.1-4

> $$2^{n+1}=O(2^n)$$ 成立吗？ $$2^{2n}=O(2^n)$$ 成立吗？

$$2^{n+1}=2\cdot 2^n=O(2^n)$$ ，成立； $$2^{2n}={(2^n)}^2=\omega (2^n)$$ ，不成立。

### 3.1-5

> 证明定理3.1。

如果我们有 $$f(n)=\Theta(g(n))$$ ，那么存在 $$c_1\gt 0$$ ， $$c_2\gt 0$$ ， $$n_0\gt 0$$ ，使得对所有 $$n\geq n_0$$ ，有 $$0\leq c_1g(n)\leq f(n)\leq c_2g(n)$$  。这蕴含着 $$f(n)=O(g(n))$$ 以及 $$f(n)=\Omega (g(n))$$ 。

如果 $$f(n)=O(g(n))$$且 $$f(n)=\Omega (g(n))$$ ，那么存在 $$c_1>0$$ ， $$n_1\gt 0$$ ，使得对所有 $$n\geq n_1$$ ，有 $$0\leq f(n)\leq c_1g(n)$$ ；存在 $$c_2>0$$ ， $$n_2\gt 0$$ ，使得对所有 $$n\geq n_1$$ ，有 $$0\leq c_2g(n)\leq f(n)$$ 。所以存在 $$c_1>0$$ ， $$c_2>0$$ ， $$n_0=max(n_1,n_2)\gt 0$$ ，使得对所有 $$n\geq n_0$$ ，有 $$0\leq c_2g(n)\leq f(n)\leq c_1g(n)$$ 。所以 $$f(n)=\Theta(g(n))$$ 。

### 3.1-6

> 证明：一个算法的运行时间为 $$\Theta(g(n))$$ 当且仅当其最坏情况运行时间为 $$O(g(n))$$ ，且其最好情况运行时间为 $$\Omega(g(n))$$ 。

3.1-5是我父亲 **。**

### 3.1-7

> 证明： $$o(g(n))\cap\omega(g(n))$$ 为空集。

我们不妨先假设存在 $$f(n)$$ 使得 $$f(n)=o(g(n))=\omega(g(n))$$ 。那么根据定义，我们有任意 $$c_1>0$$ ，存在 $$n_1$$ ，使得对所有 $$n\geq n_1$$ ， $$0\leq f(n)\lt c_1g(n)$$ ；任意 $$c_2>0$$ ，存在 $$n_2$$ ，使得对所有 $$n\geq n_2$$ ， $$0\leq c_2g(n)\lt f(n)$$ 。取 $$c=c_1=c_2$$ ，并取 $$n_0=max(n_1,n_2)$$ ，于是对所有 $$n\geq n_0$$ ，我们有 $$cg(n)\lt f(n)<cg(n)$$ 。显然这样的 $$f(n)$$ 不存在，得证。

### 3.1-8 

> 可以扩展我们的记号到有两个参数 $$m$$ 和 $$n$$ 的情形，其中的 $$n$$ 和 $$m$$ 可以按不同速率独自地趋于无穷。对于给定的函数 $$g(n,m)$$ ，用 $$O(g(n,m))$$ 来表示以下函数集：
>
> $$O(g(n,m))=\{f(n,m):存在正常量c、n_0和m_0，使得对所有n\geq n_0或m\geq m_0，有0\leq f(n,m)\leq cg(n,m)\}$$ 
>
> 对 $$\Omega(g(n,m))$$ 和 $$\Theta(g(n,m))$$ 给出相应的定义。

$$\Omega(g(n,m))=\{f(n,m):存在正常量c、n_0和m_0，使得对所有n\geq n_0或m\geq m_0，有0\leq   cg(n,m)\leq f(n,m)\}$$ 

$$\Theta(g(n,m))=\{f(n,m):存在正常量c_1、c_2、n_0和m_0，使得对所有n\geq n_0或m\geq m_0，有0\leq c_1g(n,m)\leq f(n,m)\leq c_2g(n,m)\}$$ 

### 3.2-1

> 证明：若 $$f(n)$$ 和 $$g(n)$$ 是单调递增的函数，则 $$f(n)+g(n)$$ 和 $$f(g(n))$$ 也是单调递增的，此外，若 $$f(n)$$ 和 $$g(n)$$ 是非负的，则 $$f(n)\cdot g(n)$$ 是单调递增的。

$$x_2\geq x_1$$ 时，因为 $$f(n)$$ 和 $$g(n)$$ 单调递增，所以 $$f(x_2)+g(x_2)-(f(x_1)+g(x_1))=(f(x_2)-f(x_1))+(g(x_2)-g(x_1))\geq 0$$ 。所以 $$f(n)+g(n)$$ 单调递增。

$$x_2\geq x_1$$ 时，因为 $$g(n)$$ 单调递增，所以 $$g(x_2)\geq g(x_1)$$ ，又因为 $$f(n)$$ 单调递增，所以 $$f(g(x_2))\geq f(g(x_1))$$ 。所以 $$f(g(n))$$ 单调递增。

$$x_2\geq x_1$$ 时，因为 $$f(n)$$ 和 $$g(n)$$ 单调递增且非负，所以 $$f(x_2)\cdot g(x_2)-f(x_1)\cdot g(x_1)\geq f(x_1)\cdot g(x_2)-f(x_1)\cdot g(x_1)=f(x_1)(g(x_2)-g(x_1))\geq 0$$ 。所以 $$f(n)\cdot g(n)$$ 单调递增。

### 3.2-2

> 证明等式\(3.16\)。

设 $$c=b^x$$ ，则 $$a^{\log_bc}=a^x$$ ， $$c^{\log_ba}=(b^x)^{\log_ba}=(b^{\log_ba})^x=a^x$$ ，所以 $$a^{\log_bc}=c^{\log_ba}$$ 。

### 3.2-3

> 证明等式\(3.19\)。并证明 $$n!=\omega(2^n)$$ 且 $$n!=o(n^n)$$ 。

由\(3.18\)，我们有 $$\displaystyle n!=\sqrt{2\pi n}(\frac{n}{\mathrm{e}})^n(1+\Theta(\frac{1}{n}))$$ ，两边取对数，于是有：

$$
\begin{aligned} \lg{(n!)}&=\frac{1}{2}\lg (2\pi)+\frac{1}{2}\lg n+n(\lg n-\lg \mathrm{e})+\lg{(1+\Theta(\frac{1}{n}))}\\
&=\Theta(n\lg n)-\Theta(n)+\Theta(\lg n)+\lg(1+\Theta(\frac{1}{n}))+\Theta(1)\\
&=\Theta(n\lg n)
\end{aligned}
$$

$$n$$ 趋于无穷时， $$\displaystyle \lg(1+\Theta(\frac{1}{n}))$$ 这一项趋于 $$0$$ ， $$\Theta(n)$$ 、 $$\Theta(\lg n)$$ 和 $$\Theta(1)$$ 这几项的贡献相较于 $$\Theta(n\lg n)$$ 可以忽略，所以 $$\lg(n!)=\Theta(n\lg n)$$ 。

首先我们可以用归纳法证明 $$n!\gt n\cdot 2^n$$ ，其中 $$n\geq 6$$ 。因为 $$n\gt c\gt 0$$ 时我们有 $$n\cdot 2^n\gt c\cdot 2^n$$ ，所以对任意 $$c\gt 0$$ ，存在 $$n_0=max(c+1,6)$$ ，对所有 $$n\geq n_0$$ ，有 $$0\leq c\cdot 2^n\lt n\cdot 2^n \lt n!$$ 。所以 $$n!=\omega(2^n)$$ 。

首先我们可以用归纳法证明 $$n!\lt n^{n-1}$$ ，其中 $$a = b$$ 。因为 $$n\gt 1/c \gt 0$$ 时我们有 $$n!\lt cn\cdot n!$$ ，取 $$n_0=max(1/c+1,3)$$ ，所以当 $$n\geq n_0$$ 时，有 $$n!\lt cn\cdot n!\lt cn\cdot n^{n-1}=cn^n$$ 。所以对任意 $$c\gt 0$$ ，存在 $$n_0=max(1/c+1,3)$$ ，对所有 $$n\geq n_0$$ ，有 $$0\leq n!\lt cn^n$$ 。所以 $$n!=o(n^n)$$ 。

### \*3.2-4

> 函数 $$\lceil\lg n\rceil !$$ 多项式有界吗？函数 $$\lceil\lg {\lg n}\rceil !$$ 多项式有界吗？

$$\lceil\lg n\rceil !$$ 不是多项式有界。 $$\lceil\lg {\lg n}\rceil !$$ 多项式有界。

首先我们证明 $$f(n)$$ 多项式有界等价于 $$\lg(f(n))=O(\lg n)$$ 。

如果 $$f(n)$$ 多项式有界，那么存在 $$c\gt 0$$ ， $$n_0\gt 0$$ ，对所有 $$n\geq n_0$$ ，有 $$f(n)\leq cn^k$$ 。两边取对数，我们有 $$\lg(f(n))\leq \lg c+k\lg n$$ 。又当 $$n\gt c^{1/k}$$ 时，有 $$\lg c \lt k\lg n$$ ，所以 $$\lg(f(n))\leq 2k\lg n$$ ，所以存在 $$d=2k\gt 0$$ ， $$n_1=max(n_0,c^{1/k})$$ ，对所有 $$n\geq n_1$$ ，有 $$\lg(f(n))\leq d\lg n$$ 。所以我们得到 $$\lg(f(n))=O(\lg n)$$ 。

如果 $$\lg(f(n))=O(\lg n)$$ ，那么存在 $$c\gt 0$$ ， $$n_0\gt 0$$ ，对所有 $$n\geq n_0$$ ，有 $$\lg(f(n))\leq c\lg n$$ 。当 $$k\geq 1$$ 时，有 $$\lg(f(n))\leq c\lg n+\lg k=\lg(kn^c)$$ ，所以存在 $$k\gt 0$$ ， $$n_0\gt 0$$ ，对所有 $$n\geq n_0$$ ，有 $$f(n)\leq\ kn^c$$ ，所以 $$f(n)$$ 多项式有界。

由\(3.19\)，我们有 $$\lg(\lceil\lg n\rceil!)=\Theta(\lceil\lg n\rceil\lg \lceil\lg n\rceil)$$ 。又因为当 $$n\geq2$$ 时，有 $$\lg n \leq\lceil\lg n\rceil\lt\lg n+1\leq 2\lg n$$ ，所以 $$\lg(\lceil\lg n\rceil!)=\Theta(\lg n\lg {\lg n})=\omega(\lg n)\neq O(\lg n)$$ 。所以 $$\lceil\lg n\rceil !$$ 不是多项式有界的。

类似地，我们有： 

$$
\begin{aligned}
\lg(\lceil\lg \lg n\rceil!)&=\Theta(\lceil\lg\lg n\rceil\lg \lceil\lg\lg n\rceil)\\&=\Theta(\lg\lg n \lg \lg\lg n)\\&=o((\lg\lg n)^2)\\&=o(\lg n)
\end{aligned}
$$

上式第3行到第4行成立是因为 $$\lg^2 n=o(n)$$ （至于这个为什么成立，两边取下对数就好了），接着用 $$\lg n$$ 代换 $$n$$ 可以得到结果。所以 $$\lg(\lceil\lg \lg n\rceil!)$$ 是多项式有界的。

### \*3.2-5

> 如下两个函数中，哪一个渐进更大些： $$\lg{(\lg^*n)}$$ 还是 $$\lg^*{(\lg n)}$$ ？

$$\lg^*{(\lg n)}$$ 渐进更大些。

我们用 $$p(k)$$ 表示由 $$k$$ 个 $$2$$ 堆叠起来形成的幂。 $$p(1)=2$$ ， $$p(2)=2^2$$ ， $$p(3)=2^{2^2}$$ ，以此类推。取 $$n=p(k)$$ ，有 $$\lg{(\lg^*(p(k)))}=\lg k$$ ， $$\lg^*{(\lg (p(k)))}=\lg^*(p(k-1))=k-1=\omega(\lg k)$$ 。所以 $$\lg{(\lg^*n)}=o(\lg^*{(\lg n)})$$ ， $$\lg^*{(\lg n)}$$ 渐进更大。

### 3.2-6

> 证明：黄金分割率 $$\phi$$ 及其共轭数 $$\hat\phi$$ 都满足方程 $$x^2=x+1$$ 。

这是道送分题。

### 3.2-7

> 用归纳法证明：第 $$i$$ 个斐波那契数满足等式 $$\displaystyle F_i=\frac{\phi^i-\hat\phi^i}{\sqrt{5}}$$ ，其中 $$\phi$$ 是黄金分割率且 $$\hat\phi$$ 是其共轭数。

$$\displaystyle F_0=\frac{\phi^0-\hat\phi^0}{\sqrt{5}}=0$$ ， $$\displaystyle F_1=\frac{\phi^1-\hat\phi^1}{\sqrt{5}}=\frac{\frac{1+\sqrt{5}}{2}-\frac{1-\sqrt{5}}{2}}{\sqrt{5}}=1$$ 。当 $$i=0$$ 和 $$i=1$$ 时等式成立。

$$i\geq 1$$ 时，因为 $$\phi+\hat\phi=1$$ ，且 $$\phi\hat\phi=-1$$ ，我们有：

$$
\begin{aligned}
F_{i-1}+F_i&=\frac{\phi^{i-1}-\hat\phi^{i-1}}{\sqrt{5}}+\frac{\phi^i-\hat\phi^i}{\sqrt{5}}\\
&=\frac{(\phi^i-\hat\phi^i)(\phi+\hat\phi)-(\phi\hat\phi)\phi^{i-1}+(\phi\hat\phi)\hat\phi^{i-1}}{\sqrt{5}}\\
&=\frac{\phi^{i+1}-\hat\phi^{i+1}+\phi^i\hat\phi-\hat\phi^i\phi-\phi^i\hat\phi+\hat\phi^i\phi}{\sqrt{5}}\\
&=\frac{\phi^{i+1}-\hat\phi^{i+1}}{\sqrt{5}}\\
&=F_{i+1}
\end{aligned}
$$

所以我们有 $$\displaystyle F_i=\frac{\phi^i-\hat\phi^i}{\sqrt{5}}$$ ， $$i\geq 0$$ 。

### 3.2-8

> 证明： $$k\ln k=\Theta(n)$$ 蕴含着 $$k=\Theta(n/\ln n)$$ 。

**比较怂的做法：**

由渐进记号的对称性，我们有：

$$
n=\Theta(k\ln k)
$$

两边取对数，得到：

$$
\ln n=\Theta(\ln k +\ln{\ln k})=\Theta(\ln k)
$$

所以存在 $$c_1\gt0$$ ， $$c_2\gt0$$ ， $$c_3\gt0$$ ， $$c_4\gt0$$ ， $$n_0\gt 0$$ ，使得对所有 $$n\geq n_0$$ ，有：

$$
c_1k\ln k\leq n \leq c_2k\ln k\\
c_3\ln k \leq \ln n \leq c_4\ln k
$$

两式相除我们有：

$$
\frac{c_1}{c_4}k \leq \frac{n}{\ln n}\leq \frac{c_2}{c_3}k
$$

所以 $$\displaystyle \frac{n}{\ln n}=\Theta(k)$$ ，再次利用对称性我们有 $$k=\Theta(n/\ln n)$$ 。

**比较扛的做法：**

已知 $$k\ln k=\Theta(n)$$ ，所以存在 $$n_0\gt 0$$ ，对所有 $$n\geq n_0$$ ，有：

$$
c_1n\leq k\ln k\leq c_2n\tag{1}
$$

在 $$(1)$$ 的两边除以 $$\ln n$$ 我们得到：

$$
\frac{\ln k}{c_2\ln n}k\leq\frac{n}{\ln n}\leq \frac{\ln k}{c_1\ln n}k \tag{2}
$$

 在 $$(1)$$ 两边取对数得到 $$\ln c_1+\ln n \leq \ln k+\ln\ln k\leq c_2+\ln n$$ ，所以对于 $$k\geq3$$ （根据题设，显然 $$k\neq\Theta(1)$$ ，所以存在 $$n_1\gt 0$$ ，对所有 $$n\geq n_1$$ ，有 $$k\geq 3$$ ），我们有：

$$
\ln c_1+\ln n \leq 2\ln k\\
\ln k\leq \ln c_2+\ln n\tag{3}
$$

整理 $$(3)$$ ，对于 $$n\geq 3$$ ，我们有：

$$
\frac{1}{2}+\frac{\ln c_1}{2\ln n}\leq\frac{\ln k}{\ln n}\leq 1+\frac{\ln c_2}{\ln n}\tag{4}
$$

在 $$(4)$$ 中我们取 $$c_1\gt 1$$ ， $$c_2\gt 1$$ ， $$n\geq c_2$$ ，就可以得到：

$$
\frac{1}{2}\leq\frac{\ln k}{\ln n}\leq 2\tag{5}
$$

最后把 $$(5)$$ 代入 $$(2)$$ ，我们有：

$$
2c_1\frac{n}{\ln n}\leq k\leq\frac{c_2}{2}\frac{n}{\ln n}
$$

所以 $$k=\Theta(n/\ln n)$$ 。

## 思考题

### 3-1

> _（多项式的渐进行为）_假设 $$\displaystyle p(n)=\sum^d_{i=0}a_in^i$$ 是一个关于 $$n$$ 的 $$d$$ 次多项式，其中 $$a_d\gt 0$$ ， $$k$$ 是一个常量。使用渐进记号的定义来证明下面的性质。

> **a.** 若 $$k\geq d$$ ，则 $$p(n)=O(n^k)$$ 。

$$\displaystyle p(n)=\sum^d_{i=0}a_in^i\leq\sum^d_{i=0}a_in^d=(\sum^d_{i=0}a_i)n^d\leq(\sum^d_{i=0}a_i)n^k$$ 

所以存在 $$\displaystyle c=\sum^d_{i=0}a_i\gt 0$$ ，使得对所有 $$n\geq 0$$ ，有 $$0\leq p(n)\leq cn^k$$ ，所以 $$p(n)=O(n^k)$$ 。

> **b.** 若 $$k\leq d$$ ，则 $$p(n)=\Omega(n^k)$$ 。

$$\displaystyle p(n)=\sum^d_{i=0}a_in^i\geq a_dn^d\geq a_dn^k$$ 

所以存在 $$\displaystyle c=a_d\gt 0$$ ，使得对所有 $$n\geq 0$$ ，有 $$0\leq cn^k\leq p(n)$$ ，所以 $$p(n)=\Omega(n^k)$$ 。

> **c.** 若 $$k=d$$ ，则 $$p(n)=\Theta(n^k)$$ 。

\(a\)和\(b\)告诉我们 $$\displaystyle a_dn^k\leq p(n)\leq(\sum^d_{i=0}a_i)n^k$$ ，所以存在 $$\displaystyle c_1=a_d\gt 0$$ ， $$\displaystyle c_2=\sum^d_{i=0}a_i\gt 0$$ ，对所有 $$n\geq 0$$ ，有 $$0\leq c_1n^k\leq p(n)\leq c_2n^k$$ ，所以 $$p(n)=\Theta(n^k)$$ 。

> **d.** 若 $$k\gt d$$ ，则 $$p(n)=o(n^k)$$ 。

$$\displaystyle p(n)=\sum^d_{i=0}a_in^i\leq\sum^d_{i=0}a_in^d=(\sum^d_{i=0}a_i)n^d$$ 

对于任意的 $$c\gt 0$$ ，只要有 $$\displaystyle n\gt \sqrt[k-d]{\sum^d_{i=0}a_i/c}$$ ，就有 $$p(n)\lt cn^k$$ 。所以对于任意的 $$c\gt 0$$ ，存在 $$\displaystyle n_0=\left\lceil(\sum^d_{i=0}a_i/c)^{1/(k-d)}\right\rceil+1$$ ，使得对所有的 $$n\geq n_0$$ ，有 $$0 \leq p(n)\lt cn^k$$ ，所以 $$p(n)=o(n^k)$$ 。

> **e.** 若 $$k\lt d$$ ，则 $$p(n)=\omega(n^k)$$ 。

$$\displaystyle p(n)=\sum^d_{i=0}a_in^i\geq a_dn^d$$ 

对于任意的 $$c\gt 0$$ ，只要有 $$\displaystyle n\gt \sqrt[d-k]{c/a_d}$$ ，就有 $$p(n)\gt cn^k$$ 。所以对于任意的 $$c\gt 0$$ ，存在 $$\displaystyle n_0=\left\lceil(c/a_d)^{1/(d-k)}\right\rceil+1$$ ，使得对所有的 $$n\geq n_0$$ ，有 $$0\leq cn^k \lt p(n)$$ ，所以 $$p(n)=\omega(n^k)$$ 。

### 3-2

> _（相对渐进增长）_为下表中的每对表达式 $$(A,B)$$ 指出 $$A$$ 是否是 $$B$$ 的 $$O$$ 、 $$o$$ 、 $$\Omega$$ 、 $$\omega$$ 或 $$\Theta$$ 。假设 $$k\geq 1$$ 、 $$\varepsilon\gt 0$$ 且 $$c\gt 1$$ 均为常量。回答应该以表格的形式，将“是”或“否”写在每个空格中。

| $$A\qquad B$$  | $$O$$  | $$o$$  | $$\Omega$$  | $$\omega$$  | $$\Theta$$  |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $$\lg^k n\qquad n^\varepsilon$$  | 是 | 是 | 否 | 否 | 否 |
| $$n^k\qquad c^n$$  | 是 | 是 | 否 | 否 | 否 |
| $$\sqrt{n}\qquad n^{\sin n}$$  | 否 | 否 | 否 | 否 | 否 |
| $$2^n\qquad 2^{n/2}$$  | 否 | 否 | 是 | 是 | 否 |
| $$n^{\lg c}\qquad c^{\lg n}$$  | 是 | 否 | 是 | 否· | 是 |
| $$\lg{(n!)}\qquad\lg{(n^n)}$$  | 是 | 否 | 是 | 否 | 是 |

### 3-3

> _（根据渐进增长率排序）_

> **a.** 根据增长的阶来排序下面的函数，即却出满足 $$g_1=\Omega(g_2)$$ ， $$g_2=\Omega(g_3)$$ ， $$\cdots$$ ， $$g_{29}=\Omega(g_{30})$$的函数的一种排列 $$g_1$$ ， $$g_2$$ ， $$\cdots$$ ， $$g_{30}$$ 。把你的表划分成等价类，使得函数 $$f(n)$$ 和 $$g(n)$$ 在想同类中当且仅当 $$f(n)=\Theta(g(n))$$ 。

| 1 | 2 | 3 | 4 | 5 | 6 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $$2^{2^{n+1}}$$  | $$2^{2^n}$$  | $$(n+1)!$$  | $$n!$$  | $$\mathrm{e}^n$$  | $$n\cdot 2^n$$  |

| 7 | 8 | 9 | 10 | 11 | 12 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $$2^n$$  | $$\displaystyle (\frac{3}{2})^n$$  | $$n^{\lg \lg n}$$ $$(\lg n)^{\lg n}$$  | $$(\lg n)!$$  | $$n^3$$ | $$n^2$$ $$4^{\lg n}$$ |

| 13 | 14 | 15 | 16 | 17 | 18 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $$n\lg n$$ $$\lg(n!)$$ | $$n$$ $$2^{\lg n}$$  | $$(\sqrt{2})^{\lg n}$$  | $$2^{\sqrt{2\lg n}}$$  | $$\lg^2 n$$  | $$\ln n$$  |

| 19 | 20 | 21 | 22 | 23 | 24 |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $$\sqrt{\lg n}$$  | $$\ln\ln n$$  | $$2^{\lg^* n}$$  | $$\lg^*(\lg n)$$ $$\lg^* n$$  | $$\lg{(\lg^* n)}$$  | $$1$$ $$n^{1/\lg n}$$  |

一些事实：

$$
n^{\lg \lg n}=(2^{\lg n})^{\lg{\lg n}}=(2^{\lg{\lg n}})^{\lg n}=(\lg n)^{\lg n}\\\quad\\
4^{\lg n}=(2^2)^{\lg n}=(2^{\lg n})^2=n^2\\\quad\\
n^{1/\lg n}=n^{\log_n{2}}=2
$$

> **b.** 给出非负函数 $$f(n)$$ 的一个例子，使得对所有在\(a\)部分中的函数 $$g_i(n)$$ ， $$f(n)$$ 既不是 $$O(g_i(n))$$也不是 $$\Omega(g_i(n))$$ 。

$$f(n)=[\sin(n\pi+\pi/2)+1]\cdot2^{2^{n+2}}$$ 。当 $$n=2k$$ 时， $$f(n)$$ 比\(a\)部分所有函数增长快；当 $$n=2k+1$$ 时， $$f(n)=0$$ 。因此 $$f(n)$$ 既不是 $$O(g_i(n))$$也不是 $$\Omega(g_i(n))$$ 。

### 3-4

> _（渐进记号的性质）_假设 $$f(n)$$ 和 $$g(n)$$ 为渐进正函数。证明或反驳下面的每个猜测。

> **a.** $$f(n)=O(g(n))$$ 蕴含 $$g(n)=O(f(n))$$ 。

不成立。

取 $$f(n)=n$$ ， $$g(n)=n^2$$ ，则有 $$f(n)=O(g(n))$$ ，但 $$g(n)=\omega(f(n))\neq O(f(n))$$ 。

> **b.** $$f(n)+g(n)=\Theta(min(f(n),g(n)))$$ 。

不成立。

取 $$f(n)=n$$ ， $$g(n)=n^2$$ ，则有 $$min(f(n),g(n))=n$$ ，所以 $$f(n)+g(n)=n^2+n=\Theta(n^2)\neq\Theta(n)$$ 。 

> **c.** $$f(n)=O(g(n))$$ 蕴含 $$\lg(f(n))=O(\lg(g(n)))$$ ，其中对所有足够大的 $$n$$ ，有 $$\lg(g(n))\geq 1$$ 且 $$f(n)\geq 1$$ 。

成立。

由已知存在 $$c\gt 0$$ ， $$n_0\gt 0$$ ，对所有 $$n\geq n_0$$ ，有 $$0\leq f(n)\leq cg(n)$$ ；存在 $$n_1\gt 0$$ ，对所有 $$n\geq n_1$$ ，有 $$\lg(g(n))\geq 1$$ 且 $$f(n)\geq 1$$。取 $$n_2=max(n_0,n1)$$ ，则对所有 $$n\geq n_2$$ ，有：

$$
0\leq \lg(f(n))\leq\lg c+\lg(g(n))=(\frac{\lg c}{\lg(g(n))}+1)\lg(g(n))\leq (\lg c+1)\lg(g(n))
$$

所以 $$\lg(f(n))=O(\lg(g(n)))$$ 。

> **d.** $$f(n)=O(g(n))$$ 蕴含 $$2^{f(n)}=O(2^{g(n)})$$ 。

不成立。

取 $$f(n)=2n$$ ， $$g(n)=n$$ ，则有 $$f(n)=O(g(n))$$ ，但 $$2^{f(n)}=2^{2n}=\omega(2^n)\neq O(2^{g(n)})$$ 。

> **e.** $$f(n)=O((f(n))^2)$$ 。

不成立。

取 $$f(n)=1/n$$ ， $$(f(n))^2=1/n^2$$ ，则有 $$f(n)=\omega((f(n))^2)\neq O((f(n))^2)$$ 。

> **f.** $$f(n)=O(g(n))$$ 蕴含 $$g(n)=\Omega(f(n))$$ 。

成立。

因为 $$f(n)=O(g(n))$$ ，所以存在 $$c\gt 0$$ ， $$n_0\gt 0$$ ，对所有 $$n\geq n_0$$ ，有 $$0\leq f(n)\leq cg(n)$$ ，所以 $$0\leq 1/cf(n)\leq g(n)$$ ，所以 $$g(n)=\Omega(f(n))$$ 。

> **g.** $$f(n)=\Theta(f(n/2))$$

不成立。

取 $$f(n)=2^{2n}$$ ，则 $$f(n/2)=2^n=o(f(n))\neq \Theta(f(n))$$ 。

> **h.** $$f(n)+o(f(n))=\Theta(f(n))$$ 。

成立。

由已知存在 $$c_1\gt 0$$ ， $$c_2\gt 0$$ ， $$n_0\gt 0$$ ，对所有 $$n\geq n_0$$ ，有 $$c_1f(n)\leq o(f(n))\leq c_2f(n)$$ ，所以 $$(1+c_1)f(n)\leq f(n)+o(f(n))\leq (1+c_2)f(n)$$ ，所以 $$f(n)+o(f(n))=\Theta(f(n))$$ 。

### 3-5

> _（_ $$O$$ _与_ $$\Omega$$ _的一些变形）_某些作者用一种与我们稍微不同的方式来定义 $$\Omega$$ ；假设我们使用 $$\Omega^{\infty}$$ （读作“ $$\Omega$$ 无穷”）来表示这种可选的定义。若存在正常量 $$c$$ ，使得对无穷多个整数 $$n$$ ，有 $$f(n)\geq cg(n)\geq 0$$ ，则称 $$f(n)=\Omega^{\infty}(g(n))$$ 。

> **a.** 证明：对渐进非负的任意两个函数 $$f(n)$$ 和 $$g(n)$$ ，或者 $$f(n)=O(g(n))$$ 或者 $$f(n)=\Omega^\infty(g(n))$$ 或者两者均成立，然而，如果使用 $$\Omega$$ 来代替 $$\Omega^\infty$$ ，那么该命题并不为真。

考虑 $$f(n)\neq O(g(n))$$ 的情况，则不存在 $$n_0$$ 使对所有 $$n\geq n_0$$ ，有 $$0\leq f(n)\leq cg(n)$$ ，此时存在一个集合 $$A$$ ，当 $$n\in A$$ 时有 $$f(n)\gt cg(n)$$ 。集合 $$A$$ 一定有无穷多个元素，因为如果 $$A$$ 元素有限，记 $$A$$ 中最大的元素为 $$n_1$$ ，则我们取 $$n_0=n_1+1$$ ，可以使得 $$0\leq f(n)\leq cg(n)$$ ，这与 $$f(n)\neq O(g(n))$$ 矛盾。因此要么 $$f(n)=O(g(n))$$ ，要么 $$n\geq n_0$$ 时，存在无穷多个 $$n$$ 使 $$f(n)\geq cg(n)\geq 0$$ ，即 $$f(n)=\Omega^{\infty}(g(n))$$ 。两者都成立的情况也是存在的，比如 $$f(n)=\Theta(g(n))$$ 时。 

> **b.** 描述用 $$\Omega^\infty$$ 代替 $$\Omega$$ 来刻画程序运行时间的潜在优点与缺点。

优点：从\(a\)中讨论的内容我们知道 $$\Omega^\infty$$ 可以和 $$O$$ 很好地关联起来，比如如果 $$f(n)\neq\Omega^\infty(g(n))$$ ，我们就能直接得到 $$f(n)=O(g(n))$$ 。相比之下 $$\Omega$$ 就做不到。所以 $$\Omega^\infty$$ 对研究程序运行时间上界限可能更友好一点。

缺点： $$\Omega^\infty$$ 对下界的定义更宽泛，不能像 $$\Omega$$ 一样准确地给出程序运行时间的一个下界。

> 某些作者也用一种稍微不同的方式来定义 $$O$$ ；假设使用 $$O'$$ 来表示这种可选的定义。我们称 $$f(n)=O'(g(n))$$ 当且仅当 $$\left\lvert f(n)\right\lvert =O(g(n))$$ 。

> **c.** 如果使用 $$O'$$ 代替 $$O$$ 但仍然使用 $$\Omega$$ ，定理3.1中的“当且仅当”的每个方向将出现什么情况？

$$O$$ 的定义蕴含 $$O'$$ ，所以 $$\Theta$$ 成立可以推出 $$O'$$ 和 $$\Omega$$ ；但反过来不成立，因为 $$O'\not\Rightarrow O$$ ，比如 $$f(n)$$ 存在无穷多个负值时既不是 $$O$$ 也不是 $$\Omega$$ 。

> 有些作者定义 $$\widetilde O$$ （读作“软 $$O$$ ”）来意指忽略对数因子的 $$O$$ ：
>
> $$\widetilde O(g(n))=\{f(n):存在正常量c，k和n_0，使得对所有n\geq n_0，有0\leq f(n)\leq cg(n)\lg^k(n)\}$$

> **d.** 用一种类似的方式定义 $$\widetilde\Omega$$ 和 $$\widetilde\Theta$$ 。证明与定理3.1相对应的类似结论。

$$\widetilde \Omega(g(n))=\{f(n):存在正常量c，k和n_0，使得对所有n\geq n_0，有0\leq cg(n)\lg^k(n) \leq f(n)\}$$ 

$$\widetilde \Theta(g(n))=\{f(n):存在正常量c_1，c_,2，k和n_0，使得对所有n\geq n_0，有0\leq c_1g(n)\lg^k(n) \leq f(n)\leq c_2g(n)\lg^k(n)\}$$ 

当且仅当的证明比较简单，不写了吧。

### 3-6

> （多重函数）我们可以把用于函数 $$\lg^*$$ 中的重复操作符 $$*$$ 应用于实数集上的任意单调递增函数 $$f(n)$$ ，对给定的常量 $$c\in \mathbf{R}$$ ，我们定义多重函数 $$f_c^*$$ 为
>
> $$f_c^*(n)=min\{i\geq 0：f^{(i)}(n)\leq c\}$$ 
>
> 该函数不必再所有情况下都为良定义的。换句话说，值 $$f_c^*(n)$$ 是为缩小其参数到 $$c$$ 或更小所需要函数 $$f$$ 重复应用的数目。
>
> 对如下每个函数 $$f(n)$$ 和常量 $$c$$ ，给出 $$f_c^*(n)$$ 的一个尽量紧确的界。

| $$f(n)$$  | $$c$$  | $$f_c^*(n)$$  |
| :---: | :---: | :---: |
| $$n-1$$  | $$0$$  | $$\Theta(n)$$  |
| $$\lg n$$  | $$1$$  | $$\Theta(\lg^* n)$$  |
| $$n/2$$  | $$1$$  | $$\Theta(\lg n)$$  |
| $$n/2$$  | $$2$$  | $$\Theta(\lg n)$$  |
| $$\sqrt{n}$$  | $$2$$  | $$\Theta(\lg \lg n)$$  |
| $$\sqrt{n}$$  | $$1$$  | 发散 |
| $$n^{1/3}$$  | $$2$$  | $$\Theta(\lg \lg n)$$  |
| $$n/\lg n$$  | $$2$$  | $$\Theta(\lg n/\lg \lg n)$$  |

$$f(n)=n-1,\ c=0$$ ：调用 $$n$$ 次可以把 $$n$$ 降到 $$0$$ ， $$\Theta(n)$$ 。

$$f(n)=\lg n,\ c=1$$ ： $$\lg^*n$$ 就是这样定义的， $$\Theta(\lg^* n)$$ 。

$$f(n)=n/2,\ c=1$$ ： $$n=2^k$$ 时需要调用 $$k$$ 即 $$\lg n$$ 次把 $$n$$ 降到 $$2^0$$ ， $$\Theta(\lg n)$$ 。

$$f(n)=n/2,\ c=2$$ ：同上， $$n=2^k$$ 时需要调用 $$\lg n-1$$ 次把 $$n$$ 降到 $$2^1$$ ，还是 $$\Theta(\lg n)$$ 。

$$f(n)=\sqrt{n},\ c=2$$ ： $$n=2^{2^k}$$ 时需要调用 $$k$$ 即 $$\lg\lg n$$ 次把 $$n$$ 降到 $$2^{2^0}$$ ， $$\Theta(\lg \lg n)$$ 。

$$f(n)=\sqrt{n},\ c=1$$ ：调用多少次都没用。

$$f(n)=n^{1/3},\ c=2$$ ： $$n=2^{3^k}$$ 时需要调用 $$k$$ 即 $$\log_3\lg n$$ 次把 $$n$$ 降到 $$2^{3^0}$$ ， $$\Theta(\lg \lg n)$$ 。

$$f(n)=n/\lg n,\ c=2$$ ：这个就比较厉害了。我做的时候把问题转化了一下，把 $$n$$ 写成 $$2^k$$ 的形式来研究 $$k$$ 的变化。 令 $$g(k)=k-\ln k$$ ，则 $$f^*_2(n)=g^*_1(k)=min(i\geq 0：g^{(i)}(k)\leq 1\}$$ 。也就是说不断对 $$k$$ 调用 $$g(k)$$ 使 $$k\leq 1$$ 。先下结论，对于比较大的 $$k$$ ，我们有：

$$
\frac{k-1}{\ln k}\leq g^*_1(k)\leq 2\frac{k-1}{\ln k}\tag{*}
$$

如果 $$(*)$$ 式成立我们就能得到 $$f^*_2(n)=\Theta((\lg n -1)/\lg \lg n)=\Theta(\lg n/\lg \lg n)$$ 这一结论。下面我们尝试证明 $$(*)$$ 式成立。

如果记每次调用 $$g(k)$$ 时 $$k$$ 减少的量为 $$d(k)$$ 。如果 $$k=k_0$$ ，则本次调用 $$d(k_0)=\lg k_0$$ ，下一次调用 $$d(k_0-\lg k_0)=\lg(k_0-\lg k_0)\lt d(k_0)$$ ，所以 $$d(k)$$ 随着 $$k$$ 减小而减小。

记 $$h(k)=\lg k-\lg(k-\lg k)$$ ，则 $$\displaystyle h'(k)=\frac{1-\lg k}{k(k-\lg k)}\lt 0$$ 。所以 $$h(k)$$ 单调递减，因此 $$h(k)$$ 随 $$k$$ 减小而增大，所以 $$d(k)$$ 随着 $$k$$ 减小而减小的得越来越快。 

现在计第 $$i$$ 次调用 $$g(k)$$ 时 $$d(k)$$ 的值为 $$d_i$$ ，第 $$1$$ 次一直到第 $$i$$ 次 $$k$$ 的总减少量为 $$D_i$$。下面证明：

$$
\frac{d1}{2}m \leq D_m\leq d_1m\tag{1}
$$

因为 $$d_1\gt d_2\gt\cdots\gt d_m$$ ，所以 $$\displaystyle D_m=\sum_{i=1}^n d_i\leq \sum_{i=1}^n d_1=d_1 m$$ ，这样我们证明了 $$(1)$$ 式的右边。如果 $$d_p\leq d_1/2$$ ， $$d_{p+1}\gt d_1/2$$ 且 $$0\lt d_{p+q}\lt d_1/2$$ ，由前述 $$d(k)$$ 的性质，必有 $$p\leq q$$ 。当 $$m\leq p$$ 时 $$\displaystyle D_m=\sum_{i=1}^md_i\geq \sum_{i=1}^m\frac{d1}{2}=\frac{d1}{2}m$$ 。 $$m=p+q\gt p$$ 时： 

$$
\begin{aligned}
D_m&=\sum_{i=1}^{p+q} d_i\\
&=\sum_{i=1}^{p} d_i+\sum_{i=p+1}^{p+q} d_i\\
&=\sum_{i=1}^{p}(d_i-\frac{d_1}{2}+\frac{d_1}{2})+\sum_{i=p+1}^{p+q} (d_i-\frac{d_1}{2}+\frac{d_1}{2})\\
&=\frac{d1}{2}m+\sum_{i=1}^{p}(d_i-\frac{d_1}{2})-\sum_{i=p+1}^{p+q} (\frac{d_1}{2}-d_i)\\
&\geq \frac{d1}{2}m+\frac{p(d_1-d_1/2+d_p-d_1/2)}{2}-\frac{q(d_1/2-d_{p+1}+d_1/2-d_{p+q})}{2}\\
&\geq \frac{d1}{2}m+\frac{p(d_1/2)}{2}-\frac{q(d_1/2-d_{p+q})}{2}\\
&\geq \frac{d1}{2}m+\frac{q(d_1/2-d_1/2+d_{p+q})}{2}=\frac{d1}{2}m+\frac{q}{2}d_{p+q}\geq \frac{d1}{2}m
\end{aligned}
$$

所以 $$(1)$$ 式成立。经过 $$g^*_2(k)$$ 次调用， $$k\leq 1$$ ，则 $$D(g^*_1(k))\approx  k-1$$ ，又 $$d_1=\lg k$$ ，代入 $$(1)$$ 式我们可以得到 $$(*)$$ 式。所以 $$f^*_2(n)=g^*_1(k)=\Theta(k/\lg k)=\Theta(\lg n/\lg \lg n)$$ 。

