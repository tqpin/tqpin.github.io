---
title: Ch2 The geometry of linear programmIng
mathjax: true
toc: true
date: 2022-04-03 15:37:49
tags: 
categories: 
description: 
---

我们研究多面体的基本几何性质，并且用在高维多面体时基本上是正确的

主要结果：当且仅当非空多面体不包含直线时，它至少有一个角点，在这种情况下，线性规划问题的最优解的搜索可以限制在角点



**Polyhedron** - 线性规划问题的可行解集是一个多面体
![[Pasted image 20220404110626.png]]
Polyhedron with single linear constraint：hyperplane，halfspace，a 垂直于平面，ax≥b 指向 a 的方向
![[Pasted image 20220404111710.png]]


Bounded 说明有一个 K ≥ |S|
![[Pasted image 20220404111119.png]]


**Convex Sets**
一个集合是凸集的定义（两个向量的 weighted average）：
![[Pasted image 20220404112400.png]]
定义 convex combination，convex hull，k 可以无限，有限就是凸集：
![[Pasted image 20220404112934.png]]
Theorem 2.1（Proof. p45）
* 凸集的交是凸的
* 每个多面体都是凸集
* 一个凸集的有限个元素的 convex combination 也属于该集合
* 有限个向量的凸包是一个凸集



## 三种定义"corner"以及等价性

**Extreme point**：不能表示为多面体中其他两个点的凸组合
这个定义完全是几何的，并没有利用多面体在线性约束上的性质
![[Pasted image 20220404115604.png]]
**Vertex**：具有该多面体作为可行解集的线性规划问题的唯一最优解
这个定义也是几何的，是指当且仅当 P 完全在 x 的 hyperplane 的一侧
![[Pasted image 20220404120014.png]]

> 我们希望有一个定义，它依赖于用线性约束表示的多面体，并将其简化为代数检验。为了提供这样的定义，我们需要更多的术语。
> We would like to have a definition that relies on a representation of a polyhedron in terms of linear constraints and which reduces to an algebraic test. In order to provide such a definition, we need some more terminology.

Active or binding：考虑多面体的线性约束的条件在取等号时的情况，等号也满足就称为 active
![[Pasted image 20220404122534.png]]
更一般的，只考虑一个点的 active 约束的性质，关注 n 个线性独立的约束：
![[Pasted image 20220404122545.png]]
Algebraic definition of a corner point：有 n 个线性无关的 active constraints 的 feasible solution
因为我们只对 feasible solution 感兴趣，所有的约束都是 active 的。这就给出了一个寻找 corner points 的方法：
* 施加等式约束
* 要求足够多的 active 的附加约束
* 这样就得到了 n 个线性无关的 active 约束，就根据 Theorem2.2 我们能确定一个唯一的 x*
**Basic solution** 所有等式约束 active 且存在 n 个线性无关的约束 which 可能不在 constraints 内，**basic feasible solution** 所有 constrain 变成等号也满足：
![[Pasted image 20220404123439.png]]


这三个是等价的术语，几何和代数定义的区别大概是 x 表示为点还是向量：
![[Pasted image 20220404123830.png]]


Corollary 2.1 给定有限个数的线性不等式约束，就只能有有限个数的基本或基本可行解。
Adjacent basic solutions：能找到 n - 1 个线性无关的约束，对这两个 basic solution 都是有效的



Polyhedra in standard form
：$P = \{\textbf x \in R^n | \textbf A \textbf x = \textbf b, \textbf x ≥ \textbf 0\}$  
一般假设 A mxn 的 m 行是线性无关的

关于约束矩阵的列置零：
![[Pasted image 20220404153108.png]]
如果我们存在这个 basic solution，我们就可以这样置零
就是我们要找到 n 个独立的 constrain 满足目标约束，才能说这个 x 是 basic solution；然后我们已经有了 m 个独立的行向量约束，其他维度就应该置零。
这样就能有 Procedure for constructing basic solutions，并且如果它是非负的，那就是基本可行解了；所以基本可行解也可以通过这个步骤得到
Basic variables 和 nonbasic 和 basis matrix
Correspondence of bases and basic solutions
Adjacent basic solutions and adjacent bases：如果它们共享除了一列之外的所有基
The full row rank assumption on A：如果 A 不满秩的话，上述结论也不会失去一般性


Degeneracy：如果 x 处有超过 n 个约束是 active 的，那么 basic solution x 是退化的



Extreme points 的存在性
极值点的存在取决于一个多面体是否包含一条直线
Theorem 2.6 & Corollary 2.2



Optimality of extreme points
Theorem 2.7：只要线性规划问题存在一个 optimal solution，只要可行集至少有一个极值点，我们总能在可行集的极值点集合内找到一个 optimal solution
![[Pasted image 20220404163402.png]]

Theorem 2.8：只要 P 有至少一个 extreme point，并且 optimal cost 是有限的，那么存在一个 extreme point 是 optimal 的（就不需要保证 P 存在 optimal 了，比 2.7 更强）

Corollary 2.3：非空多面体上最小化 c'x 的线性规划问题，要么存在一个 optimal 要么 cost 无穷。


Representation of bounded polyhedra 以及 Projections of polyhedra: Fourier-Motzkin elimination 略过了


关于线性规划问题的解的主要结论：
* 如果可行集非空有界，则存在一个最优解。此外，还存在一个极值点的最优解。
* 如果可行集无界，则存在以下可能性：
	* 存在一个是极值点的最优解。
	* 存在一个最优解，但没有一个最优解是极值点。(这只会发生在可行集没有极值点的情况下; 当问题以标准形式出现时，这种情况就不会发生。)
	* The optimal cost 无穷.