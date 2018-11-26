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

INSERTION-SORT($$A$$)
**for** $$j=2$$ **to** $$A.length$$
&emsp;&emsp;$$key=A[j]$$
&emsp;&emsp;$$i=j-1$$
&emsp;&emsp;**while** $$i>0$$ and $$A[i]\lt key$$
&emsp;&emsp;&emsp;&emsp;$$A[i+1]=A[i]$$
&emsp;&emsp;&emsp;&emsp;$$i=i-1$$
&emsp;&emsp;$$A[i+1]=key$$

#### **2.1-3**
> 考虑以下**查找问题**：
**输入：**$$n$$个数的一个序列$$A=\langle a_1,a_2,\cdots,a_n\rangle$$和一个值$$v$$。
写出**线性查找**的伪代码，它扫描整个序列来查找$$v$$。使用一个循环不变式来证明你的算法是正确的。确保你的循环不变式满足三条必要的性质。

#### **2.1-4**
> 考虑把两个$$n$$位二进制数加起来的问题，这两个整数分别存储在两个$$n$$元数组$$A$$和$$B$$中。这两个整数的和应按二进制形式存储在一个$$(n+1)$$元数组$$C$$中。请给出该问题形式化描述，并写出伪代码。