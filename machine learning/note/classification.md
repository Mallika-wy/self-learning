binary classification

negative class and positive class

decision boundary：$z=0$

## logistic regression 逻辑回归

**sigmoid function:**
$$
f_{\vec w,b(\vec x)}&=&p(y=1|\vec x;\vec w,b)\\
&=&\frac{1}{1+e^{-(\vec w \cdot \vec x+b)}}
$$
**loss function:**
$$
L(f_{\vec w,b}(\vec x^{(i)}),y^{(i)})=-y^{(i)}log(f_{\vec w,b}(\vec x^{(i)}))-(1-y^{(i)})log(1-f_{\vec w,b}(\vec x^{(i)}))
$$
这个loss function是通过概率论中的最大似然法求得，其良好的性质为它是一个凸函数convex，即它只有一个全局最小值（single global minimum）

**cost function:**
$$
J(\vec w,b)=\frac{1}{m}\sum^m_{i=1}[L(f_{\vec w,b}(\vec x^{(i)}),y^{(i)})]
$$
**gradient descent:**

原理公式：
$$
w_j&=&w_j-\alpha\frac{\part}{\part w_j}J(\vec w,b)\\
b&=&b-\alpha\frac{\part}{\part b}J(\vec w,b)
$$
根据求偏导计算得到：
$$
\frac{\part}{\part w_j}J(\vec w,b)&=&\frac{1}{m}\sum^m_{i=1}(f_{\vec w,b}(\vec x^{(i)})-y^{(i)})x_j^{(i)}\\

\frac{\part}{\part b}J(\vec w,b)&=&\frac{1}{m}\sum^m_{i=1}(f_{\vec w,b}(\vec x^{(i)})-y^{(i)})
$$

1. 与线性回归相同的是，每次都是同时更新

2. 尽管公式长得完全一样，但是model即方程变了

3. 我们可以使用learning curve来monitor gradient descent，这个与线性回归一样
4. use **vectorization** to make gradient descent run faster for logistic regression
5. we can use **feature scaling** to help gradient descent to converge faster