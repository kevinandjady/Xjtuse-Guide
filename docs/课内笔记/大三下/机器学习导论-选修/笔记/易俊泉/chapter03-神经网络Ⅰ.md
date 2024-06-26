[TOC]

# 第三课——神经网络Ⅰ

## 神经网络引入

### 逻辑回归的二阶段表示

#### 逻辑回归

输入与输出之间的映射关系如下
$$
P(y=1|x;w,b)=\frac{1}{1+e^{-(w^Tx+b)}}
$$
其中，𝑥为输入特征，𝑦为输出标记$y=\{0,1\}$（即二分类任务），𝒘,𝑏为学习参数。

> 𝒘是权重，b是偏值bias

#### 逻辑回归的二阶段表示

:one: **求和**summing function
$$
R^P\rightarrow R
$$

$$
z=w^Tx+b=w_1x_1+...+w_px_p+b
$$

:two: **挤压**sigmoid function
$$
R\rightarrow \{0,1\}
$$

$$
\hat y=P(y=1|x;w,b)=\frac{1}{1+e^{-z}}=\frac{e^{z}}{e^z+1}
$$

挤压函数就是之前逻辑回归学到的sigmoid function：

![image-20220319224232752](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721970.png)

<img src="https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722007.png" alt="image-20220319224911567" style="zoom:50%;"/>

### 神经元

在生物神经网络中，每个神经元与其它神经元相连，当它“兴奋”时，向其它神经元发送化学物质。

在机器学习中，将生物模型抽象为下图所示的简单神经网络模型。神经元接收来自其它神经元传递过来的输入信号，输入信号通过带权重的连接进行传递，然后通过<mark>“激活函数”</mark>产生神经元输出

<img src="https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722008.png" alt="image-20220319225112364" style="zoom:67%;"/>

**神经元**：一个神经元是由线性变换和非线性变换共同构成的

因此，逻辑回归是包含一个神经元的神经网络

![image-20220319230559000](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721972.png)

## 神经网络

神经网络包含多个神经元，输入𝒙与多个神经元相连。W需要从向量扩展为矩阵。

<mark>𝑊𝑖𝑗表示的**向量x的第𝑗个元素与向量𝑍的第𝑖个元素之间的连接权重**</mark>

![image-20220319230903851](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721973.png)

对于上图的神经网络，W如下：

![image-20220319231013344](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721975.png)

### 具有一个隐藏层的神经网络

![image-20220319231727169](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721976.png)

构造特征的特征

<img src="https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722010.png" alt="image-20220319231811728" style="zoom:67%;"/>

h1是隐藏层的输出

### 具有两个隐藏层的神经网络

![image-20220319232102321](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721978.png)

:one: 多元线性回归直接建立了输入和输出的关系

:two: 逻辑回归利用一个summing function和sigmoid function建立了输入和输出的关系

:three: 神经网络利用了多个summing function和sigmoid function建立了输入和输出的关系

> 神经网络本质上就是一个复合函数
>
> 这里都是全连接

### 非线性激活函数

引入非线性激活函数的目的是得到非线性决策面

> 不论网络多深，线性激活函数只能输出线性决策面（输出是输入的线性函数）。
>
> 非线性激活函数可以逼近任意复杂函数。

<img src="https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722012.png" alt="image-20220319232757886" style="zoom:67%;"/>

<img src="https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722014.png" alt="image-20220319233111998" style="zoom:80%;"/>

当$\hat y=\frac{1}{2}$是无法进行判断的，此时使之成立的边界称为决策面

**常用的非线性激活函数**

| 名字                                   | 图形                                                         | 方程                                                         | 导数                                                         |
| -------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Binary step                            | ![image-20220320103516147](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721980.png) | ![image-20220320101646493](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721981.png) | ![image-20220320102547211](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721982.png) |
| <mark>Logistic(a.k.a Soft step)</mark> | ![Image for post](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721983.png) | ![](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721984.png) | ![image-20220320102646642](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721985.png) |
| TanH                                   | ![Image for post](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721986.png) | ![image-20220320102804371](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721988.png) | ![image-20220320102720150](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721989.png) |
| ReLU                                   | ![Image for post](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721990.png) | ![image-20220320102252623](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721991.png) | ![image-20220320102510609](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721992.png) |



Hidden layer（隐层）的个数大于1的神经网络，称为深度神经网络

## 训练神经网络

### 损失函数

#### 二分类损失

逻辑回归中，使用对数似然度量损失（每个样本属于其真实标记的概率越大越好）

![image-20220320104901264](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721993.png)

<mark>交叉熵代价函数cross entropy loss</mark>
$$
E=loss=-\log P(Y=\hat y|X=x)=-y\log(\hat y)-(1-y)\log(1-\hat y)
$$

> $y$是真实输出，$\hat y$是预测输出
>
> $\hat y =f_\theta(x)=\frac{e^{wx+b}}{e^{wx+b}+1}$

损失函数一定是一个**标量**

#### 多分类损失



![image-20220320110332270](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721995.png)

Softmax函数：将各个输出节点的输出值范围映射到[0,1]，并且约束各个输出节点的输出值的和为1的函数

<mark>交叉熵代价函数cross entropy loss</mark>
$$
E=loss=-\sum_{j=1,...,K}y_j\log\hat y_j
$$

> 其中$y_j$是One-Hot向量：真实标签的位置为1，其他位置为0
>
> One-Hot编码，又称为一位有效编码，主要是采用N位状态寄存器来对N个状态进行编码，每个状态都由他独立的寄存器位，并且在任意时候只有一位有效。

例如，对于$y^T=(0 \ 1\ 0),\hat y^T=(\ 0.1\ 0.7\ 0.2)$，其损失函数为$E=-(0\times \log0.1+1\times\log0.7+0\times\log0.2)=-\log 0.7$
$$
E=loss=\frac{1}{2}||y-\hat y^2||=\frac{1}{2}\sum^K_{j=1}(y_j-\hat y_j)^2
$$

#### 回归损失

与分类网络的不同之处：输出层不再包含“Sigmoid”函数

**使用二次代价函数**
$$
E=loss=\frac{1}{2}||y-\hat y^2||=\frac{1}{2}\sum^K_{j=1}(y_j-\hat y_j)^2
$$

### 反向传播

目标：寻找使损失达到最小的神经网络权重

如何学习神经网络权重𝑊𝐿？使用梯度下降$W_L(t+1)=W_L(t)-\eta \frac{\partial E}{\partial W_L(t)}$

> 其中$\eta$为学习率

如何得到𝑊1,…,𝑊𝐿−1层的权重？使用反向传播Backpropagation

> 重复应用微积分的链式法则
>
> 局部最小化目标函数
>
> 要求网络所有的“块”（blocks）都是可微的

#### 数学符号说明

Hadamard (哈达玛)乘积/schur 乘积：

假设𝑠和𝑡是两个同样维度的向量，使用𝑠∘𝑡(或𝑠⊙𝑡)来表示按元素的乘积: (𝑠⊙𝑡)𝑗= 𝑠𝑗𝑡𝑗
$$
\begin{bmatrix}
1\\2
\end{bmatrix}
\odot
\begin{bmatrix}
3\\4
\end{bmatrix}
=\begin{bmatrix}
1*3\\2*4
\end{bmatrix}=
\begin{bmatrix}
3\\8
\end{bmatrix}
$$

#### 回归示例

就是复合函数求偏导

![image-20220320112945459](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721998.png)

可见已经比较复杂了

#### 二分类示例

包含一个隐层的二分类神经网络：

![image-20220320113413869](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695721999.png)

**对w2的偏导求解还比较简单**

![image-20220320113953437](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722001.png)

**对W1的偏导就复杂很多**

<img src="https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722015.png" alt="image-20220320114345749" style="zoom:67%;"/>

<img src="https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722017.png" alt="image-20220320114904350" style="zoom:80%;" />

$w_{ij}^1$表示输入𝒙 的第𝑗个元素到第1个隐层的 第 𝑖个神经元的权重

![image-20220320115125012](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722003.png)

首先推导关于𝑾𝟏的第一列 $w_1^1$求导结果,然后推导到第j列，最后得到关于这个矩阵的偏导

![image-20220320115629384](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722004.png)

## 深度神经网络学习

![image-20220320115938109](https://raw.githubusercontent.com/yijunquan-afk/img-bed-1/main/img12/1695722006.png)

**前向传播加反向传播**

| 传播方向 | 前向传播                                           | 反向传播                                |
| -------- | -------------------------------------------------- | --------------------------------------- |
| 步骤     | 1、给定一个初始的权重W                             | 1、计算误差损失$E(y,\hat y)$            |
|          | 2、输入x                                           | 2、通过链式法则（复合函数求导）计算梯度 |
|          | 3、通过复合函数$\hat y=f_3(f_2(f_1(x)))$计算预测值 |                                         |
| 更新内容 | 已知边，更新圆圈内容                               | 已知圆圈内容，更新边（权重）            |

重复迭代前向和反向步骤，直至算法收敛。

## 参考资料

[1]庞善民.西安交通大学机器学习导论2022春PPT

[2]周志华.机器学习.北京:清华大学出版社,2016

[3\][Activation Functions in Neural Network](https://medium.com/swlh/activation-functions-in-neural-network-eb0ab4bb493)

