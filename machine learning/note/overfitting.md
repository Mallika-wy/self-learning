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

**Modified cost function**
$$
J(\vec w,b)=\frac{1}{2m}\sum^m_{i=1}(f_{\vec w,b}(\vec x^{(i)})-y^{(i)})^2+\frac{\lambda}{2m}\sum^n_{j=1}w_j^2
$$
$\lambda$ is called a regularization parameter正则化参数。

我们对$\lambda$除以2m的原因是希望在训练集增大时，不需要对$\lambda$进行修改也可以很好地实现对新模型的正则化。

We are not going to penalize the parameter b because it makes very little difference whether you do or not.

新的成本函数包含两项，第一项是mean squared error 均方误差，第二项是regularization term正则项

新的成本函数要求我们既要让均方误差较小，也要让参数保持较小，其中$\lambda$ 是两项相对重要性的体现，确定了两者的权重。

如果$\lambda$为0，模型就会出现overfitt，如果$\lambda$很大，模型就会出现underfit。So what we want is some value of lambda that balances these first and second terms of trading off minimizing the mean squared error and keeping the parameter small.

当具体到某个模型的时候，会选择合适的方法来找到$\lambda$的较好的值。



### regularized linear regression

原理公式：
$$
w_j&=&w_j-\alpha\frac{\part}{\part w_j}J(\vec w,b)\\
b&=&b-\alpha\frac{\part}{\part b}J(\vec w,b)
$$
根据求偏导计算得到：
$$
\frac{\part}{\part w_j}J(\vec w,b)&=&\frac{1}{m}\sum^m_{i=1}(f_{\vec w,b}(\vec x^{(i)})-y^{(i)})x_j^{(i)}+\frac{\lambda}{m}w_j\\

\frac{\part}{\part b}J(\vec w,b)&=&\frac{1}{m}\sum^m_{i=1}(f_{\vec w,b}(\vec x^{(i)})-y^{(i)})
$$

 

$w_j=w_j(1-\alpha\frac{\lambda}{m})-\alpha\frac{1}{m}\sum^m_{i=1}(f_{\vec w,b}(\vec x^{(i)})-y^{(i)})x_j^{(i)}$

因为$1-\alpha\frac{\lambda}{m}$是略小于1的数字，所以可以在每次迭代的时候shrink $w_j$的大小，这就是正则化工作原理。

### regularized logistics regression

$$
J(\vec w,b)=\frac{1}{m}\sum^m_{i=1}[-y^{(i)}log(f_{\vec w,b}(\vec x^{(i)}))-(1-y^{(i)})log(1-f_{\vec w,b}(\vec x^{(i)}))]+\frac{\lambda}{2m}\sum^n_{j=0}w_j^2
$$