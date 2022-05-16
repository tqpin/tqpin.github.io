---
title: Lec 04 Duality & Dual Simplex
mathjax: true
toc: true
date: 2022-04-12 16:20:03
tags: 
categories: 
description: 
hidden: true
---

## 1 对偶问题：基本概念
* 基本概念：
	* LP 中 dual 是相互的，即 dual 两次就可以回到原问题；且两个问题的 optimal solution 不同但是 optimal value 相同 $c^Tx=b^T\lambda$  
	* 为了确定任⼀线性规划问题的对偶，可以利⽤对称形式的对偶对或者标准形的对偶对
	* 对偶变量 (dual variable)，对偶问题 (dual problem)，对偶⽬标值 (dual value)，对偶间隙 (duality gap)，对偶理论 (duality)
	* ![[Pasted image 20220412162645.png]]
* 经济学解释 - 配餐问题：primal 就是确定食物数量以满足营养需求，使得花费最小；dual 就是确定每个成分单价
	* ![[Pasted image 20220412162939.png]]
* Duality Scheme
	* ![[Pasted image 20220412163104.png]]
* 




## 2 基本理论：重点&难点

对偶理论
* 弱对偶定理 Weak Duality
	* 观察 duality gap，cvx 和 noncvx 都可满足，其中 LP 能在 optimal 的地方取等号
	* 一定有 duality gap 大于等于 0：$c^Tx-b^T\lambda\geq 0$ [Theorem 4.1.1]
		* Proof：$b^T\lambda=\lambda^Tb=\lambda^TAx\leq c^Tx$ 
	* 推论 1：如果 $c^Tx=b^T\lambda$，那么他们分别是最优解 
		* Proof：$c^Tx^*=\lambda^{*T}b=\leq c^Tx$ 
	* 推论 2：如果两个问题之一无界，另一个问题没有可行解
		* 一种 max 和 min 压缩
* 强对偶定理 Strong Duality
	* 如果两个问题之一有解，则另一个问题也有解，且最优值相等
	* LP 情况下的 Proof：
		* ![[Pasted image 20220412165843.png]]
	* 一般情况下的 Proof 不考虑了（利⽤凸集分离定理证明）
	* 思考题：没讲
		* 写出两阶段法中第⼀阶段的辅助问题的对偶问题？这个对偶问题有最优解吗？为什么？
* 与单纯形法的关系
	* 设标准形线性规划问题有最优解 x*，B 是最优基本可⾏解对应的基，则 $\lambda^*=(c^T_BB^{-1})^T$ 是其对偶问题的最优解
	* 在单纯形法中就是最后一行的结果 ![[Pasted image 20220412182633.png]] 
* 互补松弛条件 (最优解的充分必要条件，即去等号时的条件，即满足强对偶的条件) 有利于解决不等式约束 
	* 应用：20min 左右还可以放求原问题的解
	*  ![[Pasted image 20220412203428.png]]
* 

对偶的几种解释：一开始的那种对偶形式是咋想出来的
* 拉格朗日的解释





## 3 对偶单纯形法
求解的问题类
如何操作
算法终⽌于什么情况
