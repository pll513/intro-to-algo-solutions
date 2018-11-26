# 第二章 算法基础

### 练习
#### **2.1-1**
> 以图2-2为模型，说明INSERTION-SORT在数组$$A=\langle 31,41,59,26,41,58\rangle$$上的执行过程。

$$
\langle 31,\underline{41},59,26,41,58\rangle\\
\langle 31,41,\underline{59},26,41,58\rangle\\
\langle 31,41,59,\underline{26},41,58\rangle\\
\langle 26,31,41,59,\underline{41},58\rangle\\
\langle 26,31,41,41,59,\underline{58}\rangle\\
\langle 26,31,41,41,58,59\rangle
$$

#### **2.1-2**
> 重写过程INSERTION-SORT，使之按非升序（而不是非降序）排序。

$$\small INSERTION$$-$$\small SORT$$$$(A)$$
$$\boldsymbol{for}$$ $$j=2$$ $$\boldsymbol{to}$$ $$A.length$$
&emsp;&emsp;$$key=A[j]$$
&emsp;&emsp;$$i=j-1$$
&emsp;&emsp;$$\boldsymbol{while}$$ $$i>0$$ $$and$$ $$A[i]\lt key$$
&emsp;&emsp;&emsp;&emsp;$$A[i+1]=A[i]$$
&emsp;&emsp;&emsp;&emsp;$$i=i-1$$
&emsp;&emsp;$$A[i+1]=key$$

#### **2.1-3**
> 考虑以下**查找问题**：
**输入：**$$n$$个数的一个序列$$A=\langle a_1,a_2,\cdots,a_n\rangle$$和一个值$$v$$。
写出**线性查找**的伪代码，它扫描整个序列来查找$$v$$。使用一个循环不变式来证明你的算法是正确的。确保你的循环不变式满足三条必要的性质。

$$\small LINEAR$$-$$\small SEARCH$$$$(A)$$
$$\boldsymbol{for}$$ $$i=1$$ $$\boldsymbol{to}$$ $$A.length$$
&emsp;&emsp;$$\boldsymbol{if}$$ $$v=A[i]$$
&emsp;&emsp;&emsp;&emsp;$$\boldsymbol{return}$$ $$i$$
$$\boldsymbol{return}$$ $$-1$$

#### **2.1-4**
> 考虑把两个$$n$$位二进制数加起来的问题，这两个整数分别存储在两个$$n$$元数组$$A$$和$$B$$中。这两个整数的和应按二进制形式存储在一个$$(n+1)$$元数组$$C$$中。请给出该问题形式化描述，并写出伪代码。

#### **2.2-1**
> 用$$\Theta$$记号表示$$n^3/1000-100n^2-100n+3$$。

$$\Theta(n^3)$$。

#### **2.2-2**
> 考虑排序存储在数组中的$$n$$个数：首先找出$$A$$中的最小元素并将其与$$A[1]$$中的元素进行交换。接着，找出$$A$$中的次最小元素并将其与$$A[2]$$中的元素进行交换。对$$A$$中前$$n-1$$个元素按该方式继续。该算法称为**选择算法**，。写出其伪代码。该算法维持的循环不变式是什么？为什么它只需要对前$$n-1$$个元素进行？用$$\Theta$$记号给出选择排序的最好情况与最坏情况运行时间。

#### **2.2-3**
> 再次考虑线性查找问题。假定要查找的元素等可能地为数组中的任意元素，平均需要检查输入序列的多少元素？最坏情况又如何呢？用$$\Theta$$记号给出线性查找的平均情况和最坏情况运行时间。证明你的答案。

#### **2.2-4**
> 应如何修改一个算法，才能使之具有良好的最好情况运行时间？

