---
title: Ch1 Introduction to linear optimization
mathjax: true
toc: true
date: 2022-04-01 14:31:30
tags: 
categories: 
description: 
---

一些**定义**：
* decision variables 决策变量
	* free or unrestricted variable
* objective function or cost function
* ==feasible== solution 或者 feasible vector：满足所有 constrain 的决策变量 x
* feasible set 或者 feasible region：决策变量集合
* ==optimal== feasible solution 或者 optimal solution：最小化决策函数的 feasible solution
	* optimal cost（可以是 unbounded 负无穷）






## 线性规划的两种形式
* general form：对决策变量没有约束，不等式约束是 componentwise 的，A 的形状就是一行一个等式左项 ![[Pasted image 20220401144215.png]] 
* standard form 标准型，一般算法第一步都是化成标准型
	* 满足：约束都是等式；决策变量都 ≥ 0
	*  ![[Pasted image 20220401150811.png]] 


任何形式的线性规划问题都可以**转化**成 standard form： 
* 两个问题是等价的意思是：给定一个问题的 feasible solution，我们可以为另一个问题构造一个具有相同 cost 的 feasible solution；对于 optimal cost 和 solution 也同理
* 转化方式：
	* 等式约束 = 大于等于+小于等于
	* Elimination of free variables：对于无限制的决策变量 x，可以替代成两个整数相减，$x^+ - x^-$  
	* Elimination of inequality constraints：对于不等式约束，可以增加松弛变量 slack variable，![[Pasted image 20220401151806.png]] 
	* 对于非严格不等式约束 p14






## 分段线性凸函数
线性规划可解决 cost function 是**分段线性凸函数**，而这种函数可以逼近更一般的凸函数；但这样的逼近并不总是一个好主意，因为它可以把光滑函数变成非光滑函数

**Piecewise linear convex** functions
$$
f(\textbf x) = max_{i=l,...,m}(\textbf c'_i\textbf x+d_i)
$$
属于一种凸函数，可用于近似别的凸函数
比如：绝对值函数

*  原问题：（minimize Piecewise linear convex） ![[Pasted image 20220401163528.png]] 
* 转化：（decision variables are z and x） ![[Pasted image 20220401163644.png]] 

这种函数形式也适用:  $f(\textbf x) = max_{i=l,...,m}(\textbf f'_i\textbf x+g_i)$
Note: $f$ is the piecewise linear convex function






三种**绝对值**的等价形式：c 非负，可以表示为分段线性凸函数，但有点难度
![[Pasted image 20220401165642.png]] 
但可以修改成如下：
![[Pasted image 20220401165655.png]] 
或者引入新变量，可以证明 optimal 等价的时候 x+ 和 x- 必定有一个等于零：
![[Pasted image 20220401165713.png]] 





应用：
* minimize the largest residual
* 时序变化：$\textbf x (t+1)=\textbf A\textbf x (t)+\textbf B\textbf u (t),y (t)=\textbf c'\textbf x(t)$ 
* 火箭控制






图形表示
* general form：向量移动 Example 1.8 给出了 feasible set 和 optimal solution 个数的一些情况
* standard form：一个平面，高维



 