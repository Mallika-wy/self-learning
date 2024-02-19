# 机器学习

机器学习分类：

1. supervised learning监督学习
2. unsupervised learning无监督学习
3. reinforcement learning强化学习

前两机器学习用的最多。

practical advice for applying learning algorithms。

学习算法是工具。 

![image-20240216111559653](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240216111559653.png)

监督学习的定义：



监督学习的分类：

- 回归 regression：

  the learning algorithm has to predict numbers from infinitely many possible output numbers

- 分类 classification

  the learning algorithm has to make a prediction of a  category, all of a small set of possible outputs 

非监督学习：

Data only comes with inputs x, but not output labels y. Algorithm has to find structure in the data.

- 聚类算法 clustering:

  Group similar data points together.

  it takes data without labels and tries to automatically group them into clusters

- 异常检测 anomaly detection:

- 数据降维dimensionality reduction







## 线性回归模型

回归有很多种，诸如：线性回归，多项式回归，支持向量机回归，决策树回归，随机森铃回归等。

数据的展现形式：图与表

The dataset that is used to train the model is called a training set.

x (lowercase) = "input" variable feature

y (lowercase) = "output" variable or "target" variable

m = number of training examples

(x,y) = single training example

$(x^{(i)},y^{(i)})$ = $i^{th}$ training example

![image-20240217101257886](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240217101257886.png)

在某个训练集执行学习算法，得到函数f即特定模型。当我们输入input feature时，调用模型，我们可以得到y的估计值prediction，用$\hat{y}$来表示。这里的y是训练集中的实际真实值，我们得到的只是对真实值的预测。

如果输入的信息只有一个，那么我们说这是一个linear regression with one variable。

如果说output target只有一个，那我们说这是一个

univariable linear regression。



## cost function

成本函数有什么用

对于直线回归，如何计算成本函数

对于有两个变量的函数，如果画成员函数图的话，就是三维的，可以用等高线图来表达

## gradient descent

该算法是用来求使成本函数值最小时的各个参数值的。

从一个起点开始梯度下降，最终只会到达唯一的一个点。从不同的起点开始梯度下降，可能到达不同的点。最终都会到达局部最小值。

$w=w-\alpha \frac{\part}{\part w}J(w,b)$

这里的$\alpha$是学习率learning rate，决定每次w的更新变化多少。学习率的值在0和1之间。如果大，那么每次更新w就会变化更多。（向山谷迈进一大步）

将成本函数与梯度下降结合实现第一个回归算法，线性回归算法。



## 多维特征

如何将线性回归变得更加强大，而不仅仅是局限于一个变量。



multiple linear regression

vectorization

Numpy中有方法dot实现两个向量的点乘

为什么矢量化的方法计算更加快，因为每一个乘积项计算是同时进行的。  

对于线性回归算法，可以使用normal equation来求解w和b，它有很多缺点，其不能应用于其他学习算法，同时当number of features is large，该方法比较慢。

feature scaling（特征缩放）

当不同特征之间的范围差距很大时，会导致梯度下降运行缓慢，所以需要重新缩放不同特征，使其具有可比较烦值范围。

平均归一化和Z-socre归一化

如何判断梯度下降是否收敛：

学习曲线（横坐标是迭代次数，纵坐标是成本j），如果J在某次迭代后增加，那么就是学习率设置不佳。

如何设置一个合适的学习率  

如何针对一个问题选择合适的特征，特征工程

polynomial regression多项式回归，该方法包含特征工程和特征缩放两种技术。





## 分类算法

