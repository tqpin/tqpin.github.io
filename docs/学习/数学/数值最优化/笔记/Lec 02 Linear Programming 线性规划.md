---
title: Lec 02 Linear Programming 线性规划
mathjax: true
toc: true
date: 2022-04-08 14:49:20
tags: 
categories: Coursework
description: 数值最优化 or CME307/MS&E311
---

LP 的定义：目标函数是**线性的**，约束条件是**线性等式**或**不等式**，每个变量都取**实数值**。

## 1 线性规划的典型例子—技巧

* 配餐问题：目标 & cost 向量，大于等于约束
* 运输问题：目标 & cost 矩阵
* 非线性整数规划 - 含绝对值的
	* ==绝对值在目标函数上== [两种方法](https://blog.csdn.net/HsinglukLiu/article/details/123123292?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1.pc_relevant_paycolumn_v3&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1.pc_relevant_paycolumn_v3&utm_relevant_index=1)  #TODO 
	* 绝对值在约束上
* 压缩感知重构算法 - 基追踪：匹配追踪类贪婪迭代算法；凸优化算法或最优化逼近方法：这类方法通过将非凸问题转化为凸问题求解，找到信号的逼近
	* 其中最常用的方法就是[基追踪 BP basis pursuit](https://blog.csdn.net/jbb0523/article/details/51986554) , 像一种最优化准则，可以使用单纯形法、内点法之类的求解（PPT: 7 寻找满足线性系统的稀疏解）
* 模式分类 pattern classification：准确分类？不能完美分开？-> SVM

## 2 解的几何特征—引例

* 考虑二维平面，高维空间同样适合
* **Polyhedron<->LP**：可行集，feasible area
* **图解法**：Cost vector 指向 cost 增加的方向，所以比如 minimize 就需要把 vector 往反方向移动；垂直于需要移动的直线
* **顶点<->解**：考虑顶点的代数刻画和几何描述，研究线性规划的几何特征，寻求有效算法
 
## 3 基本解、基本可行解 (BFS)—基本概念

* 多⾯体 (Polyhedron)，bounded，hyperplane
	* ![[Pasted image 20220408162545.png]] 
* 凸集，保凸运算
	* ![[Pasted image 20220408162611.png]] 
* 极点 (extreme points)，顶点 (vertex)
	* 几何上：即不能位于连接该集合中其它两点的开线段上的点 ![[Pasted image 20220408162653.png]] 
* 积极约束，非积极约束
	* 对于一个点来说，对这些约束进行分类 ![[Pasted image 20220408162932.png]] 
* 基本解，基本可行解 
	* 一个[解释](https://mp.weixin.qq.com/s/N1jCOtfvLtYinrm0YtWi6Q) ：包括 BS、BFS、等价证明 
	* 可行解 feasible solution：字面意思，满足所有约束的解
	* 基本解 BS：若存在 n 个**有效**约束线性无关，且所有等式约束在 x* 处均有效
		* **基本解与多面体的定义形式有关**：就是说可能多面体形状一样但是基本解不同，侧面反映了 BS 和 BFS 是代数定义，而非几何定义 ![[Pasted image 20220409162711.png]]
	* 基本可行解 BFS：若 x* 是 BS 且满足所有约束条件 ![[Pasted image 20220408163208.png]] 
* 顶点<->极点<->基本可行解 #TODO 
	* ![[Pasted image 20220408163300.png]] 
* 极点存在性
	* ![[Pasted image 20220408164828.png]] 
* 极点、基本可行解有限多个：Corollary 2.1 受限于可从 m 个约束中选出多少 n 个约束
	* ![[Pasted image 20220408173905.png]] 
* 极点 (基本可行解) 的最优性 (optimality)：引入 LP 问题，有目标函数 #TODO 看书
	* ![[Pasted image 20220408174535.png]]
	* ![[Pasted image 20220408174545.png]]
* 


## 4 标准型—重点
Standard Form 标准型：极小化、等式约束、变量非负
我们假定矩阵 A 是满秩的，并且结论对于非满秩的都适用

*  [[Ch1 Introduction to linear optimization#线性规划的两种形式|一般转化]] 
* [[Ch1 Introduction to linear optimization#分段线性凸函数|分段线性凸函数]] 
	* 绝对值


## 5 基本定理 (BFS 的存在性、最优值的极点可达性)—重点

考虑标准型下的 BS 和 BFS：
* 定义：基矩阵 (basis matrix)；基变量 (basis variables)
	* Basic matrix 是可逆的因为它的列必须是线性无关的，所以每一个 basic matrix 可以给出一个唯一的基本解，如果基本解非负就是基本可行解
	* [Book:CH2.3] ![[Pasted image 20220408175810.png]]
* 基本可行解及几何意义
	* ![[Pasted image 20220409204149.png]]
* 基本可行解存在性与基本定理 (标准型)
	* 有可行解就有基本可行解；线性规划如果有解就有最优解  ![[Pasted image 20220408181717.png]]
* 极点与基本可行解的等价性 (标准型)
	* ![[Pasted image 20220408203650.png]]
	* ![[Pasted image 20220409204912.png]]
* 线性规划问题解的几种情况
	* ![[Pasted image 20220408203757.png]]
* 




## 6 退化—理解

退化：不止 n 个 active constrains，不止 n-m 个维度是零

![[Pasted image 20220408203828.png]]



