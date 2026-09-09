---
title: transformer学习
published: false
layout: post
author: 陈家辉
tags:
- 学习
- transformer
---

# 从函数到神经网络

符号主义：function describe the world -> 联结主义：通过猜来找到这个函数

线性函数：f(x) = wx+b

非线性函数：f(x) = g(wx+b^2) g()->激活函数
激活函数可以无限套娃，但是一般不会超过3层。被套在中间的函数，就叫隐藏层，这个复杂函数就是神经网络。
![神经网络](/img/in-post/transformer/image_1.png)

根据已知的xy，才出w和b的取值。

神经网络：可以简单的看成一个非常复杂的非线性函数

# 计算神经网络参数

![损失函数](/img/in-post/transformer/image_2.png)

损失函数常用的一种是均方误差(MSE)：
$ MSE = \frac{1}{n}\sum_{i=1}^{n}(y_i-\hat{y}_i)^2 $

![alt text](/img/in-post/transformer/image_3.png)

泛化能力： 模型在未见过的数据上的表现能力

过拟合：模型在训练数据上的表现很好，但是在未见过的数据上的表现很差。

![alt text](/img/in-post/transformer/image_4.png)
正则化：为了防止过拟合，引入正则化项。
![alt text](/img/in-post/transformer/image.png)

防止过拟合的方法：
1. 增加数据量
2. 减少模型复杂度
3. 引入正则化项
4. dropout
5. 提前终止训练

训练过程会遇到的问题：
1. 计算开销
2. 收敛速度
3. 梯度消失/爆炸
... 这部分先略过


# 从矩阵到CNN

将加减乘除改为矩阵的写法，这种写法的好处就是可以利用gpu的并行计算能力，加速计算。

![alt text](/img/in-post/transformer/image_6.png)

将叉乘改为卷积操作，通过卷积层降低神经网络复杂度，成为卷积神经网络CNN
![alt text](/img/in-post/transformer/image_7.png)

![alt text](/img/in-post/transformer/image_8.png)

卷积层：卷积层的作用是提取特征，通过卷积核在输入特征图上滑动，计算卷积核与输入特征图的重叠部分的点积，得到输出特征图的一个像素值。

池化层：池化层的作用是提取输入的部分特征，以减少特征图的大小，从而减少参数数量，同时保留重要的特征。

# 从词嵌入到RNN

如何识别一句话里面每个字的褒贬呢？

词表：词汇表是所有可能出现的词的集合，每个词都有一个唯一的编号。但是这种方式无法表示词与词之间的关系，比如“我”和“你”的关系。
![alt text](/img/in-post/transformer/image_11.png)
one-hot编码：将每个词都标识一个唯一的编号，然后将这个编号转换为一个向量，向量的长度等于词汇表的大小，向量中只有一个元素为1，其他元素为0。维度过高，同时也无法表示词与词之间的关系。

![alt text](/img/in-post/transformer/image_10.png)

词嵌入：将每个词都转换为一个低维向量，这个向量可以表示词与词之间的关系。


