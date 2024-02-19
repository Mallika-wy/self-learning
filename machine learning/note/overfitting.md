# overfitting 过拟合

## what is overfitting

定义：If we have too many features, the learned hypothesis may fit the training set very well, but fail to generalize to new examples.

fit the training set very well指的是loss function的值很小，甚至等于零。

所以过拟合就是损失函数极小但泛化性能差的情况。落实在分类问题上就是训练集的损失函数值很小，但是验证集/测试集上的损失函数值很大。

**线性回归例子：**

![image-20240219224701164](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240219224701164.png)

对于房价预测问题，

第一个模型用线性方程来拟合，发现该模型的cost很大，我们把在训练集上偏差很大的情况叫做欠拟合（underfitting），又叫做高偏差（high bias）

第二个模型刚刚好。

第三个模型引入高次项，尽管该模型对于训练集的样本拟合的很好，但是对于测试集就会出现损失函数很大的境况，这个叫做过拟合（ovefitting），又叫做高方差（high variance）

**Logistic回归**

![image-20240219225147680](C:\Users\lenovo\AppData\Roaming\Typora\typora-user-images\image-20240219225147680.png)

## 解决过拟合

1. 获得更多的训练数据，增大训练集。collect more data
2. 如果feature过多，可能会出现过拟合，此时可以选择the most appropriate set of features(特征选择)。该方法有个缺点：丢弃很多信息。select feature
3. regularization（正则化）,reduce size of parameter。保留所有feature，但是尝试减少参数的大小



## regularization 详细总结

正则化是用来防止模型过拟合而采取的手段。我们对代价函数增加一个限制条件，限制其较高次参数大小不能过大。