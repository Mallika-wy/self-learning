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