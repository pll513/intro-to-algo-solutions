# 第2章 算法基础

## 练习

### **2.1-1**

> 以图2-2为模型，说明INSERTION-SORT在数组$$A=\langle 31,41,59,26,41,58\rangle$$上的执行过程。

$$
\langle 31,\underline{41},59,26,41,58\rangle\\
\langle 31,41,\underline{59},26,41,58\rangle\\
\langle 31,41,59,\underline{26},41,58\rangle\\
\langle 26,31,41,59,\underline{41},58\rangle\\
\langle 26,31,41,41,59,\underline{58}\rangle\\
\langle 26,31,41,41,58,59\rangle
$$

### **2.1-2**

> 重写过程INSERTION-SORT，使之按非升序（而不是非降序）排序。

$$\small \!{\rm INSERTION\verb|-|SORT}(A)\\ 1\quad \boldsymbol{for}\ j=2\ \boldsymbol{to}\ A.length\\ 2\quad \qquad key=A[j]\\ 3\quad \qquad i=j-1\\ 4\quad \qquad \boldsymbol{while}\ i>0\ {\rm and}\ A[i]\lt key\\ 5\quad \qquad \qquad A[i+1]=A[i]\\ 6\quad \qquad \qquad i=i-1\\ 7\quad \qquad A[i+1]=key$$

### **2.1-3**

> 考虑以下**查找问题**： **输入：**$$n$$ 个数的一个序列 $$A=\langle a_1,a_2,\cdots,a_n\rangle$$ 和一个值 $$v$$ 。 写出**线性查找**的伪代码，它扫描整个序列来查找 $$v$$ 。使用一个循环不变式来证明你的算法是正确的。确保你的循环不变式满足三条必要的性质。

$$\small \!{\rm LINEAR\verb|-|SEARCH}(A)\\ 1\quad \boldsymbol{for}\ i=1\ \boldsymbol{to}\ A.length\\ 2\quad \qquad \boldsymbol{if}\ v==A[i]\\ 3\quad \qquad \qquad \boldsymbol{return}\ i\\ 4\quad \boldsymbol{return} \ \rm NIL$$ 

**循环不变式：**在 $$\boldsymbol{for}$$ 循环的每次迭代开始时 $$v$$ 不在 $$A[1..i-1]$$ 中 ，即 $$v$$ 在 $$A[i..n]$$ 中。

**初始化：**第一次循坏开始前 $$i=1$$ ， $$A[1..0]$$ 不包含任何元素，$$v$$ 不在 $$A[1..0]$$ 中，即在 $$A[1..n]$$ 中寻找 $$v$$ 。

**保持：**进入循环前已经有 $$v$$ 不在 $$A[1..i-1]$$ 中 。若有 $$v==A[i]$$ ，则 $$i$$ 就是所找元素位置；否则 $$v$$ 不在 $$A[1..i]$$中，对 $$\boldsymbol{for}$$ 循环的下一次迭代增加 $$i$$ 将保持循环不变式。

**终止：**循环终止时 $$i=n+1$$ 。这意味着 $$v$$ 不在 $$A[1..n]$$ 中。

### **2.1-4**

> 考虑把两个$$n$$位二进制数加起来的问题，这两个整数分别存储在两个$$n$$元数组$$A$$和$$B$$中。这两个整数的和应按二进制形式存储在一个$$(n+1)$$元数组$$C$$中。请给出该问题的形式化描述，并写出伪代码。

$$\small \!{\rm BINARY\verb|-|ADD}(A,B,C)\\ \ \ 1\quad carry=0\\  \ \ 2\quad \boldsymbol{for}\ i=A.length\ \boldsymbol{to}\ 1\\ \ \ 3\quad \qquad sum = A[i] + B[i] + carry\\  \ \ 4\quad \qquad\boldsymbol{if} sum > 1\\ \ \ 5\quad \qquad\qquad carry = 1\\  \ \ 6\quad \qquad\qquad C[i+1] = sum - 2\\ \ \ 7\quad \qquad\boldsymbol{else}\\  \ \ 8\quad \qquad\qquad carry = 0\\  \ \ 9\quad \qquad\qquad C[i+1] = sum\\ 10\quad C[1] = carry$$ 

### **2.2-1**

> 用$$\Theta$$记号表示$$n^3/1000-100n^2-100n+3$$。

$$\Theta(n^3)$$。

### **2.2-2**

> 考虑排序存储在数组中的$$n$$个数：首先找出$$A$$中的最小元素并将其与$$A[1]$$中的元素进行交换。接着，找出$$A$$中的次最小元素并将其与$$A[2]$$中的元素进行交换。对$$A$$中前$$n-1$$个元素按该方式继续。该算法称为**选择算法**。写出其伪代码。该算法维持的循环不变式是什么？为什么它只需要对前$$n-1$$个元素进行？用$$\Theta$$记号给出选择排序的最好情况与最坏情况运行时间。

$$\small \!{\rm SELECTION\verb|-|SORT} (A)\\  1\quad n=A.length\\  2\quad \boldsymbol{for}\ j=1\ \boldsymbol{to}\ n-1\\  3\quad \qquad smallest=j\\  4\quad \qquad \boldsymbol{for}\ i=j+1\ \boldsymbol{to}\ n\\  5\quad \qquad\qquad \boldsymbol{if} A[i]<A[smallest]\\  6\quad \qquad\qquad\qquad smallest=i\\  7\quad \qquad {\rm exchange}\ A[j]\ {\rm with}\ A[smallest]$$

在每次进入外部的 $$\boldsymbol{for}$$ 循环前， $$A[1..j-1]$$ 包含 $$A$$ 中最小的 $$j-1$$ 个元素且它们已按从小到大排列。因为循环终止时 $$j=n$$ ，此时 $$A[1..n-1]$$包含 $$A$$ 中最小的 $$n-1$$ 个元素，剩下的 $$A[n]$$ 就是A的最大元素。

### **2.2-3**

> 再次考虑线性查找问题。假定要查找的元素等可能地为数组中的任意元素，平均需要检查输入序列的多少元素？最坏情况又如何呢？用$$\Theta$$记号给出线性查找的平均情况和最坏情况运行时间。证明你的答案。

平均情况需要检查 $$n/2$$ 个元素。最坏情况需要检查 $$n$$ 个元素。平均和最坏情况的运行时间都为 $$\Theta(n)$$ 。不证明了吧。

### **2.2-4**

> 应如何修改一个算法，才能使之具有良好的最好情况运行时间？

没这个必要，先有蛋后有鸡。

### 2.3-1

> 使用图2-4作为模型，说明归并排序在数组 $$A=\langle 3,41,52,26,38,57,9,49\rangle$$ 上的操作。

$$
\langle 3,9,26,38,41,49,52,57\rangle\\
\langle 3,26,41,52\rangle\quad\langle 9,38,49,57\rangle\\
\langle 3, 41\rangle\quad\langle 26,52\rangle\quad\langle 38,57\rangle\quad\langle 9,49\rangle\\
\langle 3\rangle \langle 41\rangle\quad\langle 52\rangle \langle 26\rangle\quad\langle 38\rangle \langle 57\rangle\quad\langle 9\rangle \langle 49\rangle\\
$$

### 2.3-2

> 重写过程 $$\small \rm MERGE$$ ，使之不使用哨兵，而是一旦数组 $$L$$ 或 $$R$$ 的所有元素被复制回 $$A$$ 就立刻停止，然后把另一个数组的剩余部分复制回 $$A$$ 。

$$\small \!{\rm MERGE} (A,p,q,r)\\  \ \ 1\quad n_1 = q - p + 1\\ \ \ 2\quad n_2 = r - q\\ \ \ 3\quad {\rm let}\ L[1..n_1]\ {\rm and}\ R[1..n_2]\ {\rm be\ new\ arrays}\\ \ \ 4\quad \boldsymbol{for}\ i=1\ \boldsymbol{to}\ n_1\\  \ \ 5\quad \qquad L[i]=A[p+i-1]\\ \ \ 6\quad \boldsymbol{for}\ j=1\ \boldsymbol{to}\ n_2\\  \ \ 7\quad \qquad R[i]=A[q+j]\\ \ \ 8\quad i=1\\ \ \ 9\quad j=1\\  10\quad k=p\\ 11\quad \boldsymbol{while}\ i \leq n_1\ {\rm and}\ j \leq n_2\\ 12\quad \qquad\boldsymbol{if}\ L[i] \leq R[j]\\ 13\quad \qquad\qquad A[k]=L[i]\\ 14\quad \qquad\qquad i=i+1\\ 15\quad \qquad\boldsymbol{else}\\ 16\quad \qquad\qquad A[k]=R[j]\\ 17\quad \qquad\qquad j=j+1\\ 18\quad \qquad k=k+1\\ 19\quad \boldsymbol{for}\ i=i\ \boldsymbol{to}\ n_1\\ 20\quad \qquad A[k]=L[i]\\ 21\quad \qquad k=k+1\\ 22\quad \boldsymbol{for}\ j=j\ \boldsymbol{to}\ n_2\\ 23\quad \qquad A[k]=R[j]\\ 24\quad \qquad k=k+1$$

### 2.3-3

> 使用数学归纳法证明：当 $$n$$ 刚好是 $$2$$ 的幂时，以下递归式的解是 $$T(n)=n\lg n$$ 。 $$\\T(n) = \begin{cases} 2 & \text{若 $n=2$} \\2T(n/2)+n & \text{若 $n=2^k,k>0$} \end{cases}$$

对 $$k$$ 归纳，证明 $$T(2^k)=2^k\lg{2^k}$$， $$k\geq 1$$ ： $$k=1$$ 时， $$T(2^1)=2\lg2=2$$ ，递归式成立； $$k\geq 1$$ 时，有 $$T(2^{k+1})=2 T(2^k)+2^{k+1}=2^{k+1}\lg{2^k}+2^{k+1}\lg2=2^{k+1}\lg{2^{k+1}}$$ ，递归式也成立，得证。

### 2.3-4

> 我们可以把插入排序表示为如下的一个递归过程。为了排序 $$A[1..n]$$，我们递归地排序 $$A[1..n-1]$$ ，然后把 $$A[n]$$ 插入已排序的数组 $$A[1..n-1]$$ 。为插入排序的这个递归版本的最坏情况运行时间写一个递归式。

$$
\\T(n) = \begin{cases} c & \text{若 $n=1$} \\T(n-1)+cn & \text{若 $n\gt 1$} \end{cases}
$$

### 2.3-5

> 回顾查找问题，注意到，如果序列 $$A$$ 已排好序，就可以将该序列的中点与 $$v$$ 进行比较。根据比较的结果，原序列中有一半就可以不用再做进一步的考虑了。**二分查找**重复这个过程，每次都将序列剩余部分的规模减半。为二分查找写出迭代或递归的伪代码。证明：二分查找的最坏情况运行时间为 $$\Theta(\lg n)$$ 。

直接把迭代版本和递归版本的答案都搬过来：

$$\small \!{\rm ITERATIVE\verb|-|BINARY\verb|-|SEARCH}(A,v,low,high)\\ 1\quad \boldsymbol{while}\ low \leq high\\ 2\quad \qquad mid=\lfloor(low+high)/2\rfloor\\ 3\quad \qquad \boldsymbol{if}\ v==A[mid]\\ 4\quad \qquad\qquad \boldsymbol{return}\ mid\\ 5\quad \qquad \boldsymbol{elseif}\ v>A[mid]\\ 6\quad \qquad\qquad low = mid + 1\\ 7\quad \qquad \boldsymbol{else}\ high=mid-1\\ 8\quad \boldsymbol{return}\ {\rm NIL}$$ 

$$\small \!{\rm RECURSIVE\verb|-|BINARY\verb|-|SEARCH}(A,v,low,high)\\ 1\quad \boldsymbol{if}\ low \gt high\\ 2\quad \qquad \boldsymbol{return}\ {\rm NIL}\\ 3\quad mid=\lfloor(low+high)/2\rfloor\\ 4\quad \boldsymbol{if}\ v==A[mid]\\ 5\quad \qquad\boldsymbol{return}\ mid\\ 6\quad \boldsymbol{elseif}\ v>A[mid]\\ 7\quad \qquad\boldsymbol{return}\ \small {\rm RECURSIVE\verb|-|BINARY\verb|-|SEARCH}(A,v,mid+1,high)\\ 8\quad \boldsymbol{else}\ \boldsymbol{return}\ \small {\rm RECURSIVE\verb|-|BINARY\verb|-|SEARCH}(A,v,low,mid-1)$$ 

每次迭代或者递归调用都可以把问题规模缩小一半。可以写出二分查找的递归式为 $$T(n)=T(n/2)+c$$，因此二分查找的最坏情况运行时间为 $$\Theta(lg n)$$ 。

### 2.3-6

> 注意到2.1节中的过程 $$\small \rm INSERTION\verb|-|SORT$$ 的第5~7行的 $$\boldsymbol{while}$$ 循环采用了一种线性查找来（反向）扫描已排好序的子数组 $$A[1..j-1]$$ 。我们可以使用二分查找来把插入排序的最坏情况总运行时间改进到 $$\Theta(n\lg n)$$ 吗？

不能。设每次进入外循环已排好序的子数组为 $$A[1..k-1]$$ ，虽然可以使用二分查找 $$\Theta(\lg k)$$的运行时间内找到插入位置 $$p$$ ，但挪动位置 $$p$$ 后面的元素 $$A[p+1..k-1]$$ 仍需要 $$\Theta(k)$$ 的运行时间。

### \*2.3-7

> 描述一个运行时间为 $$\Theta(n\lg n)$$ 的算法，给定 $$n$$ 个整数的集合 $$S$$ 和另一个整数 $$x$$ ，该算法能确定 $$S$$ 中是否存在两个其和刚好为 $$x$$ 的元素。

$$\small \!{\rm TWO\verb|-|SUM}(S,x)\\ \ \ 1\quad n=S.length\\ \ \ 2\quad {\rm MERGE\verb|-|SORT}(S,1,n)\\ \ \ 3\quad low=1\\ \ \ 4\quad high=n\\ \ \ 5\quad \boldsymbol{while}\ low\lt high\\ \ \ 6\quad \qquad sum=S[low]+S[high]\\ \ \ 7\quad \qquad \boldsymbol{if}\ sum\lt x\\ \ \ 8\quad \qquad\qquad low=low+1\\ \ \ 9\quad \qquad \boldsymbol{elseif}\ sum\gt x\\ 10\quad \qquad\qquad high=high-1\\ 11\quad \qquad \boldsymbol{else}\ \boldsymbol{return}\ {\rm true}\\ 12\quad \boldsymbol{return}\ {\rm false}$$ 

$$\small {\rm TWO\verb|-|SUM}$$ 接收一个数组 $$S$$ 和整数 $$x$$ 作为输入参数，首先对 $$S$$ 进行升序排列，接着用 $$low$$ 和 $$high$$ 分别从头和尾寻找结果。$$\small {\rm MERGE\verb|-|SORT}$$ 需要 $$\Theta(n\lg n)$$ 的运行时间； $$\boldsymbol{while}$$ 循环需要 $$\Theta(n)$$ 的运行时间，故 $$\small {\rm TWO\verb|-|SUM}$$ 总共耗费 $$\Theta(n\lg n)$$ 的运行时间。

相关问题：[https://leetcode.com/problems/two-sum/description/](https://leetcode.com/problems/two-sum/description/)

## 思考题

### 2-1

> _（在归并排序中对小数组采用插入排序）_虽然归并排序的最坏情况运行时间为 $$\Theta(n\lg n)$$ 。而插入排序的最坏情况运行时间为 $$\Theta(n^2)$$ ，但是插入排序中的常量因子可能使得它在 $$n$$ 较小时，在许多机器上实际运行地更快。因此，在归并排序中当子问题变得足够小时，采用插入排序来使递归时的叶**变粗**是有意义的。考虑对归并排序的一种修改，其中使用插入排序来排序长度为 $$k$$ 的 $$n/k$$ 个子表，然后使用标准的合并机制来合并这些子表，这里 $$k$$ 是一个待定的值。

> **a.** 证明：插入排序最坏情况可以在 $$\Theta(nk)$$ 时间内排序每个长度为 $$k$$ 的 $$n/k$$ 个子表。

排序一个长度为 $$k$$ 的子表在最坏情况下需要 $$\Theta(k^2)$$ 的时间，共有 $$n/k$$ 个这样的子表，故总时间是 $$n/k\cdot\Theta(k^2)=\Theta(nk)$$ 。

> **b.** 表明在最坏情况下如何在 $$\Theta(n\lg{(n/k)})$$ 时间内合并这些子表。

自底向上两个两个一组合并长度为 $$k$$ 的子表。

忽略边界条件，如果有 $$n/k$$ 个这样的子表，那第 $$1$$ 次合并后还剩下 $$n/2k$$ 个长度为 $$2k$$ 的子表；第 $$2$$ 次合并后还剩下 $$n/4k$$ 个长度为 $$4k$$ 的子表；以此类推，第 $$\lg{(n/k)}$$ 次合并后剩下1个长度为 $$n$$ 的子表，此时合并已经完成。注意到第 $$i$$ 次合并需要 $$\Theta(n/(2^{i-1}k)\cdot 2^{i-1}k)=\Theta(n)$$ 的运行时间，即每次合并都需要 $$\Theta(n)$$的运行时间 。所以，总合并时间为 $$\lg{(n/k)}\cdot\Theta(n)=\Theta(n\lg{n/k})$$ 。

> **c.** 假定修改后的算法的最坏运行时间为 $$\Theta(nk+n\lg{(n/k)})$$ ，要使修改后的算法与标准的归并排序具有相同的运行时间，作为 $$n$$ 的一个函数，借助 $$\Theta$$ 记号， $$k$$ 的最大值是什么？

因为 $$1\leq k\leq n$$ ，所以 $$n\lg{(n/k)}$$ 这一项的的贡献介于 $$\Theta(n)$$ 和 $$\Theta(n\lg n)$$ 之间，这不会使得修改后的算法运行时间渐进大于归并排序。所以这里只需要考虑 $$nk$$ 对 $$\Theta$$ 的贡献就可以了。设 $$k=f(n)$$ ，显然 $$f(n)$$ 不能渐进大于 $$\Theta(\lg n)$$ 。

> **d.** 在实践中，我们应该如何选择 $$k$$ ？

实践中还要考虑被 $$\Theta$$ 记号省略的常数因子，数据的输入规模以及程序的运行环境等要素，所以需要根据实际的程序运行时间来确定 $$k$$ 的取值。

### 2-2

> _（冒泡排序的正确性）_冒泡排序是一种流行但低效的排序算法，它的作用时反复交换相邻的未按次序排列的元素。
>
> $$\small \!{\rm BUBBLESORT}(A)\\ 1\quad \boldsymbol{for}\ i=1\ \boldsymbol{to}\ A.length-1\\ 2\quad\qquad \boldsymbol{for}\ j=A.length\ \boldsymbol{downto}\ i+1\\ 3\quad\qquad\qquad \boldsymbol{if}\ A[j]\lt A[j-1]\\ 4\quad\qquad\qquad\qquad {\rm exchange}\ A[j]\ {\rm with}\ A[j-1]$$

> **a.** 假设 $$A'$$ 表示 $$\small {\rm BUBBLESORT}(A)$$ 的输出。为了证明 $$\small {\rm BUBBLESORT}$$ 正确，我们必须证明它将终止并且有： $$A'[1]\leq A'[2]\leq\cdots\leq A'[n]\tag{2.3}$$ 其中 $$n=A.length$$ 。为了证明 $$\small {\rm BUBBLESORT}$$ 确实完成了排序，我们还需要证明什么？下面两部分将证明不等式 $$\small (2.3)$$ 。

还需要证明 $$A'$$ 由原来在 $$A$$ 中的元素组成，即 $$A'[1..n]$$ 是 $$A[1..n]$$ 的一个排列。

> **b.** 为第2~4行的 $$\boldsymbol{for}$$ 循环精确地说明一个循环不变式，并证明该循环不变式成立。你的证明应该使用本章中给出的循环不变式证明的结构。

我们记 $$n=A.length$$ 。

**循环不变式：**在2~4行的 $$\boldsymbol{for}$$ 循环的每次迭代开始时， $$A[j..n]$$ 由原来在 $$A[j..n]$$ 中的元素组成，并且 $$A[j]$$ 是 $$A[j..n]$$ 的最小元素。

**初始化：**循环的第一次迭代前 $$j=n$$ ， $$A[n...n]$$ 只包含 $$A[n]$$ 一项，自然也有 $$A[n]$$ 是最小元素。

**保持：**进入循环前我们已经有 $$A[j..n]$$ 由原来在 $$A[j..n]$$ 中的元素组成，并且 $$A[j]$$ 是 $$A[j..n]$$ 中的最小元素。算法在循环内比较 $$A[j]$$ 和 $$A[j-1]$$ 的大小，把较小的元素交换到原来$$A[j-1]$$ 所在位置，这使得循环结束后有 $$A[j-1..n]$$ 由原来在 $$A[j-1..n]$$ 中的元素组成，并且 $$A[j-1]$$ 是 $$A[j-1..n]$$ 中的最小元素。对 $$\boldsymbol{for}$$ 循环的下一次迭代 $$j$$ 变成 $$j-1$$ 将保持循环不变式。

**终止：**循环终止时 $$j=i$$ ，此时 $$A[i..n]$$ 由原来在 $$A[i..n]$$ 中的元素组成，并且 $$A[i]$$ 是 $$A[i..n]$$ 中的最小元素。

> **c.** 使用\(b\)部分证明的循环不变式的终止条件，为第1~4行的 $$\boldsymbol{for}$$ 循环说明一个循环不变式，该不变式将使你能证明不等式 $$\small (2.3)$$ 。你的证明应该使用本章中给出的循环不变式证明的结构。

**循环不变式：**在1~4行的 $$\boldsymbol{for}$$ 循环的每次迭代开始时，满足（1） $$A[1..n]$$ 由原来在 $$A[1..n]$$ 中的元素组成；（2） $$A[1..i-1]$$ 由 $$A[1..n]$$中最小的 $$i-1$$ 个元素组成，即 $$A[1..i-1]$$ 中的任意元素都不大于 $$A[i..n]$$ 中的任意元素；（3） $$A[1..i-1]$$ 中的元素已升序排列。

**初始化：**循环的第一次迭代前 $$i=1$$ ， $$A[1...0]$$ 不包含任何元素，自然满足以上3个条件。

**保持：**由于内循环只是对 $$A[i..n]$$ 中的元素做重新排列，且没有改变 $$A[1..j-1]$$ 中的元素，所以循环不变式中的条件1始终被外循环保持；又内循环在 $$A[i..n]$$ 中找到最小的元素移动到原来 $$A[i]$$ 所在位置，因为进入外循环前我们有 $$A[1..i-1]$$ 中的元素不大于 $$A[i..n]$$ 中的元素且升序排列，所以现在有 $$A[i]$$ 不小于 $$A[1..i-1]$$ 中的任意元素。因此，结束此次外循环时 $$A[1..i]$$ 由 $$A[1..n]$$中最小的 $$i$$ 个元素组成且它的元素按升序排列。对外层 $$\boldsymbol{for}$$ 循环的下一次迭代 $$i$$ 变成 $$i+1$$ 将保持循环不变式的条件2和条件3。

**终止：**循环终止时 $$i=n+1$$ ，此时 $$A[1..n]$$ 包含 $$A$$ 中的所有元素，由原来在 $$A[1..n]$$ 中的元素组成，并且满足 $$A[1]\leq A[2]\leq\cdots\leq A[n]$$，这证明了冒泡排序算法的正确性 。

> **d.** 冒泡排序的最坏情况运行时间是多少？与插入排序的运行时间相比，其性能如何？

如果每次比较都需要交换元素，并假定每次比较和交换元素所需时间恒定，为 $$c$$ ，那么冒泡排序的最坏情况运行时间为 $$\displaystyle \sum_{i=1}^{n-1}\sum_{j=i+1}^{n}c=c\sum_{i=1}^{n-1}(n-i)=c\sum_{i=1}^{n-1}i=cn(n-1)/2=\Theta(n^2)$$ 。在最好情况下冒泡排序算法仍然需要进行 $$n(n-1)/2$$ 次比较，所以运行时间为 $$\Theta(n^2)$$ 。与插入排序比较的话，最坏情况虽然都为 $$\Theta(n^2)$$ ，但冒泡排序采用两两交换来改变元素位置，所以可能会慢一些。最好情况下该冒泡排序算法渐进大于插入排序算法。

### 2-3

> _（霍纳（Horner）规则的正确性）_给定系数 $$a_0$$ ， $$a_1$$ ， $$\cdots$$ ， $$a_n$$ 和 $$x$$ 的值，代码片段 
>
> $$\small \!\hspace{0.067em}1\quad y=0\\ 2\quad \boldsymbol{for}\ i=n\ \boldsymbol{downto}\ 0\\ 3\quad\qquad y=a_i+x\cdot y$$ 
>
> 实现了用于求值多项式
>
> $$\displaystyle P(x)=\sum_{k=0}^{n}a_kx^k=a_0+x(a1+x(a_2+\cdots+x(a_{n-1}+xa_n)\cdots))$$ 
>
> 的霍纳规则。

> **a.** 借助 $$\Theta$$ 记号，实现霍纳规则的以上代码片段的运行时间是多少？

$$\Theta(n)$$ 。

> **b.** 编写伪代码来实现朴素的多项式求值算法，该算法从头开始计算多项式的每个项。该算法的运行时间是多少？与霍纳规则相比，其性能如何？

$$\small \!\hspace{0.067em} 1\quad \boldsymbol{for}\ i=n\ \boldsymbol{downto}\ 0\\ 2\quad \qquad m=1\\ 3\quad \qquad \boldsymbol{for}\ j=1\ \boldsymbol{to}\ i\\ 4\quad \qquad\qquad m=m\cdot x\\ 5\quad \qquad y=y+a_i\cdot m$$ 

$$\Theta(n^2)$$ 。大概会慢一点吧。

> **c.** 考虑以下循环不变式：在2~3行 $$\boldsymbol{for}$$ 循环每次迭代的开始有
>
> $$\displaystyle y=\sum_{k=0}^{n-(i+1)}a_{k+i+1}x^k$$ 
>
> 把没有项的和式解释为等于 $$0$$ 。遵照本章中给出的循环不变式证明的结构，使用该循环不变式来证明终止时有 $$\displaystyle y=\sum_{k=0}^{n}a_{k}x^k$$ 。

**初始化：**第一次 $$\boldsymbol{for}$$ 循坏迭代开始前 $$i=n$$ ， $$\displaystyle y=\sum_{k=0}^{-1}a_{k+n+1}x^k=0$$ ，这意味着循环不变式在循环开始前成立。

**保持：**进入循环后， $$y$$ 的值更新了，有

$$
\begin{aligned}
y&=a_i+x\cdot \sum_{k=0}^{n-(i+1)}a_{k+i+1}x^k\\
&=a_i+\sum_{k=0}^{n-(i+1)}a_{k+i+1}x^{k+1}\\
&=a_ix^0+\sum_{k=1}^{n-i}a_{k+i}x^k\\
&=\sum_{k=0}^{n-i}a_{k+i}x^k=\sum_{k=0}^{n-((i-1)+1)}a_{k+(i-1)+1}x^k
\end{aligned}
$$

对 $$\boldsymbol{for}$$ 循环的下一次迭代， $$i$$ 变为 $$(i-1)$$ 将保持循环不变式。

**终止：**循环终止时 $$i=-1$$ ，带入 $$i$$ 的值我们得到 $$\displaystyle y=\sum_{k=0}^{n}a_kx^k$$ 。

> **d.** 最后证明上面给出的代码片段将正确地求由系数$$a_0$$ ， $$a_1$$ ， $$\cdots$$ ， $$a_n$$ 刻画的多项式的值。

前人之述备矣。

### 2-4

> _（逆序对）_假设 $$A[1..n]$$ 是一个有 $$n$$ 个不同数的数组。若 $$i\lt j$$ 且 $$A[i]\gt A[j]$$ ，则对偶 $$(i,j)$$ 称为 $$A$$ 的一个**逆序对**（inversion）。

> **a.** 列出数组 $$\langle 2,3,8,6,1\rangle$$ 的 $$5$$ 个逆序对。

$$(1,5)$$ ， $$(2,5)$$ ， $$(3,4)$$ ， $$(3,5)$$ ， $$(4,5)$$ 。

> **b.** 由集合 $$\langle 1,2,\cdots,n\rangle$$中的元素构成的什么数组具有最多的逆序对？它有多少逆序对？

当数组降序排列时具有最多逆序对，共有 $$\small \displaystyle \sum_{i=0}^{n}(i-1)=\frac{n(n-1)}{2}$$ 组逆序对。

> **c.** 插入排序的运行时间与输入数组中的逆序对的数量之间是什么关系？证明你的回答。

设输入数组 $$A[1..n]$$ 的逆序对数量为 $$n_r$$，那么插入排序的运行时间为 $$\Theta(n_r+n)$$ 。如果我们用 $$r_j$$表示由 $$A[j]$$ 和 $$A[1..j-1]$$ 中的元素组成的逆序对的总数，注意到 $$r_1=0$$ 。所以我们有 $$\small \displaystyle n_r=\sum_{j=1}^{n}r_j=\sum_{j=2}^{n}r_j$$。接着我们分析 $$\small \rm INSERTION\verb|-|SORT$$ 算法。为了简化问题，我们忽略 $$\boldsymbol{for}$$ 和 $$\boldsymbol{while}$$ 循环中的边界条件，设算法的第2~4行和第8行的每次运行时间恒定，为 $$c_1$$ ；第6~7行每次运行的时间恒定，为 $$c_2$$ （ $$c_1$$ 包含了对变量 $$j$$的修改和判断， $$c_2$$ 包含了对变量 $$i$$ 的修改和判断 ）。由插入排序保持的循环不变式我们知道在进入第5行 $$\boldsymbol{while}$$ 前， $$A[1..j-1]$$ 由原来 $$A[1..j-1]$$ 中的元素组成且已升序排列。而 $$\boldsymbol{while}$$循环的循环次数是 $$A[1..j-1]$$中所有比 $$A[j]$$ 大的元素，这恰好就是 $$r_j$$。所以插入排序的总运行时间 $$\small \displaystyle T=\sum_{j=2}^{n}(c_2r_j+c_1)=c_2n_r+c_1n-c_1=\Theta(n_r+n)$$ 。进一步我们可以得出结论：当输入数组升序排列时，插入排序的逆序对数为 $$0$$ ，运行时间为 $$\Theta(n)$$ ；当输入数组降序排列时，插入排序的逆序对数最大，运行时间为 $$\Theta(n^2)$$ 。

> **d.** 给出一个确定在 $$n$$ 个元素的任何排列中逆序对数量的算法，最坏情况需要 $$\Theta(n\lg n)$$ 时间（_提示：_修改归并排序）。

