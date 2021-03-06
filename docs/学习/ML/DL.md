---
title: Deep Learning
mathjax: true
date: 2020-08-21 16:13:29
---



# Approach to AI 

符号主义是通过一个基于规则的系统，输入知识，手动设置规则，推理得到输出；

经典机器学习从输入的知识中，手动进行特征选择，按照一定算法从特征域映射到输出域；

表示学习希望改善特征选择的过程，即运用ML发掘表示本身，目标是分离出能解释观察数据的差变因素 factor of variation，他们通常不是可以直接观测到的量，很难直接被人工描述。之一的代表是自编码器 autoencoder

DL是表示学习的另一种，希望让计算机通过简单的概念构建复杂的概念，即通过一层层简单的函数不断映射原输入空间，进行更加复杂的特征抽象，从而学习到一个数据的正确表示（这是DL的解释之一）

![Figure 1.5: Flowcharts showing how the different parts of an AI system relate to each other within different AI disciplines. Shaded boxes indicate components that are able to learn from data.](image-20200822114636624.png)

DL在简单的表示和架构设计中，也可以加入人类的经验；并且让计算机根据层次化的概念体系理解世界，而每一层概念都是较为简单的映射；这样一层层得到一个很深的网络，因此被称为 Deep Learning。DL从某种角度来说，就是学习多层次的组合

虽然大多数情况下，模型组基本不包括真实数据的生成过程

# 基于梯度的学习

深度网络导致损失函数往往是**非凸**的，所以无法保证全局收敛，只能用迭代的方法使梯度不断下降，从而找到一个较小值；这种非凸性还使得算法对初始参数值非常敏感，所以我们在初始化参数是往往选择一个小随机数

这种策略需要我们选择一个损失函数（代价函数），神经网络的损失函数一般就这么几种基本模式，然后再加上正则化项

一般来说，参数模型定义了分布 $p(y|x;\theta)$ ，并简单的运用最大似然原理，所以我们可以使用数据分布和模型分布之间的交叉熵作为损失函数：MLE

也可以不预测完整概率分布，而预测给定x条件下的y的某种统计量：MAP

代价函数的梯度必须非常大而且易于预测，否则会在很多的隐藏层中逐渐趋于饱和，比如指数函数在很大的负值时，负对数似然函数可以有效消除这些函数的饱和问题

另外一种思路是把学习一组参数改成选择一个函数，我们可以把损失函数看做一个**泛函**，用变分法求得最佳解

损失函数的选择与输出单元密切联系，而隐藏单元的设计是一个非常活跃的研究领域，似乎没有很明确的指导性理论



# 架构设计

架构是指网络的整体结构：应该具有多少单元、单元之间如何连接；对于前馈来说，层的连接是顺序的，所以架构设计主要考虑深度和每层宽度；考虑如何连接层与层，还有更多结构，比如CNN的稀疏连接

**万能近似定理**指明具有线性输出层和至少一层具有任何一种压缩性质的激活函数的隐藏层网络，给予足够多的隐藏单元，可以近似任意Borel可测函数



# 正则化

指用来减少测试误差（可能增加训练误差）的策略

* 约束和惩罚加入先验知识，使模型向其靠近
* 简单化模型
* 其他，比如集成的方法（bagging boosting）；Dropout；对抗训练



# 优化





# Feedforward Neural Network

深度前馈网络 = 前馈神经网络 = （多层感知机 MLP）

前馈是指信息流的单向流动，从输入x流经定义f流到输出y，没有反馈连接；CNN就是一种前馈神经网络，而RNN则是有反馈的网络

线性模型的能力被局限在线性空间中，它无法理解两个变量的相互作用，为了扩展线性模型，我们希望找到一个映射先作用于x，比如核方法；DL就是学习这个映射，人类只需要设计一个带参数的函数组，然后通过不断优化损失函数来接近正确的函数

## XOR

通过添加一个隐藏层来学习一个非线性映射



# CNN

























