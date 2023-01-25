## 概述

在研究具体的随机现象时我们通常着重关注以下要素：

- 样本空间 $\Omega$，指明随机现象所有可能出现的结果。
- 事件域 $\mathcal{F}$，表示我们所关心的所有事件。
- 概率 $P$，描述每一个事件发生的可能性大小。

## 样本空间、随机事件

### 定义

一个随机现象中可能发生的不能再细分的结果被称为 **样本点**。所有样本点的集合称为 **样本空间**，通常用 $\Omega$ 来表示。

一个 **随机事件** 是样本空间 $\Omega$ 的子集，它由若干样本点构成，用大写字母 $A, B, C, \cdots$ 表示。

对于一个随机现象的结果 $\omega$ 和一个随机事件 $A$，我们称事件 $A$  **发生了** 当且仅当 $\omega \in A$。

例如，掷一次骰子得到的点数是一个随机现象，其样本空间可以表示为 $\Omega=\{1,2,3,4,5,6\}$。设随机事件 $A$ 为“获得的点数大于 $4$”，则 $A = \{ 5, 6 \}$。若某次掷骰子得到的点数 $\omega = 3$，由于 $\omega \notin A$，故事件 $A$ 没有发生。

### 事件的运算

由于我们将随机事件定义为了样本空间 $\Omega$ 的子集，故我们可以将集合的运算（如交、并、补等）移植到随机事件上。记号与集合运算保持一致。

特别的，事件的并 $A \cup B$ 也可记作 $A + B$，事件的交 $A \cap B$ 也可记作 $AB$，此时也可分别称作 **和事件** 和 **积事件**。

## 事件域

研究具体的随机现象时我们需要明确哪些事件是我们感兴趣的。根据随机事件的定义，显然有 $\mathcal{F} \subset 2^{\Omega}$（记号 $2^{\Omega}$ 表示由 $\Omega$ 的所有子集组成的集合族），但 $\mathcal{F} = 2^{\Omega}$ 却不是必须的。这在样本空间 $\Omega$ 有限时可能有些难以理解，毕竟 $2^{\Omega}$ 尽管更大了但仍然有限。而当 $\Omega$ 为无穷集时，$2^{\Omega}$ 的势变得更大，其中也难免会出现一些“性质不太好”且我们不关心的事件，这时为了兼顾这些事件而放弃一些性质就显得得不偿失了。

尽管 $\mathcal{F} = 2^{\Omega}$ 不是必须的，这并不代表 $2^{\Omega}$ 的任一子集都能成为事件域。我们通常会对一些事件进行运算得到的结果事件的概率感兴趣，因此我们希望事件域 $\mathcal{F}$ 满足下列条件：

- $\varnothing \in \mathcal{F}$；
- 若 $A \in \mathcal{F}$，则补事件 $\bar{A} \in \mathcal{F}$；
- 若有一列事件 $A_n \in \mathcal{F}, n = 1, 2, 3\dots$，则 $\bigcup A_n \in \mathcal{F}$。

简言之，就是事件域 $\mathcal{F}$ 对在补运算、和可数并下是封闭的，且包含元素 $\varnothing$。

可以证明满足上述三个条件的事件域 $\mathcal{F}$ 对可数交也是封闭的。

以掷骰子为例，当样本空间记为 $\Omega=\{1,2,3,4,5,6\}$ 时，以下两个集合能够成为事件域：

- $\mathcal{F}_1 = \{ \varnothing, \Omega \}$
- $\mathcal{F}_2 = \{ \varnothing, \{1, 3, 5\}, \{2, 4, 6\}, \Omega \}$

但以下两个集合则不能

- $\mathcal{F}_3 = \{ \varnothing, \{1\}, \Omega \}$（对补不封闭）
- $\mathcal{F}_4 = \{ \{1, 3, 5\}, \{2, 4, 6\} \}$（不含有 $\varnothing$ 且对并不封闭）

## 概率

### 定义

#### 古典定义

在概率论早期实践中，由于涉及到的随机现象都比较简单，具体表现为样本空间 $\Omega$ 是有限集，且直观上所有样本点是等可能出现的，因此人们便总结出了下述定义：

如果一个随机现象满足：

- 只有有限个基本结果；
- 每个基本结果出现的可能性是一样的；

那么对于每个事件 $A$，定义它的概率为

$$
P(A)=\frac{\#(A)}{\#(\Omega)}
$$

其中 $\#(\cdot)$ 表示对随机事件（一个集合）大小的度量。

后来人们发现这一定义可以直接推广到 $\Omega$ 无限的一部分情景中，于是就有了所谓 [几何概型](https://baike.baidu.com/item/%E5%87%A0%E4%BD%95%E6%A6%82%E5%9E%8B/4035773)。

#### 公理化定义

上述基于直观认识的定义在逻辑上有一个很大的漏洞：在定义「概率」这一概念时用到了「可能性」这一说法，产生了循环定义的问题。同时「等可能」在样本空间无限时会产生歧义，由此产生了包括 [Bertrand 悖论](https://baike.baidu.com/item/%E8%B4%9D%E7%89%B9%E6%9C%97%E6%82%96%E8%AE%BA/9241081) 在内的一系列问题。

经过不断探索，苏联数学家柯尔莫哥洛夫于 1933 年在他的《概率论基础》一书中第一次给出了概率的公理化定义：

概率函数 $P$ 是一个从事件域 $\mathcal{F}$ 到闭区间 $[0, 1]$ 的映射，且满足：

- **规范性**：事件 $\Omega$ 的概率值为 $1$，即 $P(\Omega)=1$。
- **可数可加性**：若一列事件 $A_1, A_2, \cdots$ 两两不交，则 $P\left( \bigcup_{i \geq 1} A_i \right) = \sum_{i \geq 1} P(A_i)$。

### 概率函数的性质

对于任意随机事件 $A, B \in \mathcal{F}$，有

- **单调性**：若 $A \subset B$，则有 $P(A) \leq P(B)$。
- **容斥原理**：$P(A+B) = P(A) + P(B) - P(AB)$。
- $P(A - B) = P(A) - P(AB)$，这里 $A - B$ 表示差集。

## 概率空间

我们在一开始提到，研究具体的随机现象时我们通常关注样本空间 $\Omega$、事件域 $\mathcal{F}$ 以及概率函数 $P$。我们将三元组 $(\Omega, \mathcal{F}, P)$ 称为一个概率空间。

概率只有在确定的概率空间下讨论才有意义。我们前面提到的 Bertrand 悖论归根结底就是因对样本空间 $\Omega$ 的定义不明确而产生的。

## 参考资料与注释

[^1]: [概率论（数学分支）\_百度百科](https://baike.baidu.com/item/概率论/829122)

[^2]: [Probability - Wikipedia](https://en.wikipedia.org/wiki/Probability)