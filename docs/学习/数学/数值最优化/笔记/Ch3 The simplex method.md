---
title: Ch3 The simplex method
mathjax: true
toc: true
date: 2022-04-04 16:55:55
tags: 
categories: 
description: 
---

3.1. Optimality conditions 
3.2. Development of the simplex method 
3.3. Implementations of the simplex method - revised
3.4. Anticycling: lexicography and Bland's rule 
3.5. Finding an initial basic feasible solution 
3.6. Column geometry and the simplex method 
3.7. Computational efficiency of the simplex method 
3.8. Summary 
3.9. Exercises 
3.10. Notes and sources



**我们考虑 standard form**：
$$
\begin{align}
\text{minimize}\ \textbf c'\textbf x \\ 
\text{subject to}\ \textbf A\textbf x=\textbf b\\
\textbf x\geq \textbf 0
\end{align}
$$
Feasible set - $P$
$A$ are $m * n$ 并且行线性无关
$A_i$ is the $ith$ column of the matrix $A$, and $a'_i$ is its $ith$ row

在线性规划中，**局部最优性意味着全局最优性**，因为我们在凸集上优化凸函数
**目标**：给定一个 BFS，找到 cost 下降方向。
Feasible direction：不会移动到 feasible set 以外的方向




Sec. 3.1 Optimality conditions
* 基本解定义：$Ax=b$  的基本解就是方程组 $Bx_B=b$ & $x_N=0$ 的解
	* 基变量 $x_B$ basic variables 和非基变量 $x_N=0$ nonbasic variable
		* 理解：基本解就是满足所有等式约束，并且存在 n 个有效且线性无关的约束；所以对于标准型来说，就是满足 m 行等式约束，还要能挑选出 n-m 个对 x 的约束（因为得满足等式约束，所以一般这 n-m 大于等于约束就会变成等于约束，就是说需要 n-m 个维度等于零）
	* $B (1), ... , B (m)$ : 基变量的 indices
	* $\textbf B = [\textbf A_{B (1)} . . . \textbf A_{B (m)} ]$ : 对应的基矩阵 basis matrix，由 A 的 m 个线性无关的列组成
	* $\textbf x_B = (\textbf x_{B (1)},...,\textbf x_{B(m)})$ : 对应的基变量 basic variables
	* $\textbf x_B=\textbf B^{-1}\textbf b$ : 
	* ![[Pasted image 20220408175810.png]]
* 考虑等式约束 - jth basic direction：找到一个 d，使基本解 x 在满足等式约束，并且除了 jth 非基变量，别的非基变量都保持 0 的情况下（即 dj=1，d_B 也可变）移动到新的基本解 $x:=x+\theta d$ 
* 考虑非负约束->退化的情况
* 考虑 cost function 的变化 - reduce cost：j 方向的单位变化和代偿变化 $\bar c_j = c_j-c^T_BB^{-1}A_j$ [Definition 3.2]；并且发现沿着 basic variable 移动并不会使 cost 下降
* 考虑移动到 optimal 的条件：reduced cost 非负 [Theorem 3.1]




Sec. 3.2 Development ofthe simplex method
* 考虑新基本解的变化幅度 - $\theta$ 的选择：

