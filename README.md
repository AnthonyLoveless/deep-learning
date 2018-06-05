# deep-learning
personal practice
---------------
深度学习个人练习，该项目内容包括：<br>
1.deep_neural_network_v1.py：自己实现的最简单的深度神经网络（多层感知机),不包含正则化,dropout,动量等...总之是最基本的,只有fp和bp。<br><br>
2.deep_neural_network_v2.py: 自己实现的最简单的深度神经网络（多层感知机）,和v1的唯一区别在于：v1中fp过程,caches每一层存储的是（w,b,z,A_pre）,
而v2每一层存储的是（w,b,z,A）, 第0层存储的（None,None,None,X）,X即A0。    `个人更推荐用v2版本`.

关于具体的推导实现讲解，请移步本人的CSDN博客：https://blog.csdn.net/u012328159/article/details/79485767<br><br>
3.deep_neural_network_ng.py ---改正版ng在Coursera上的深度神经网络<br>
**具体主要改正的是对relu激活函数的求导，具体内容为:<br>**
def relu_backward(dA, cache):<br>
	"""
	Implement the backward propagation for a single RELU unit.
	
	Arguments:
	dA -- post-activation gradient, of any shape
	cache -- 'Z' where we store for computing backward propagation efficiently
	Returns:
	dZ -- Gradient of the cost with respect to Z
	"""
	Z = cache
	A = np.maximum(0, Z)
	dZ = dA * np.int64(A > 0) # np.int64(A > 0)是A对Z求导
	return dZ
**ng在作业中写的relu导数（个人认为是错的）为：<br>**
def relu_backward(dA, cache):<br>
    """
    Implement the backward propagation for a single RELU unit.
    Arguments:
    
    dA -- post-activation gradient, of any shape
    cache -- 'Z' where we store for computing backward propagation efficiently
    Returns:
    dZ -- Gradient of the cost with respect to Z
    """
    Z = cache
    dZ = np.array(dA, copy=True) # just converting dz to a correct object.
    
    # When z <= 0, you should set dz to 0 as well. 
    dZ[Z <= 0] = 0
    
    assert (dZ.shape == Z.shape)
    
    return dZ
<br>
<br>
4.compare_initializations.py： 比较了四种初始化方法（初始化为0，随机初始化，Xavier initialization和He initialization），具体效果见CSDN博客：https://blog.csdn.net/u012328159/article/details/80025785
<br>
<br>
5.deep_neural_network_with_L2.py: 带L2正则项正则项的网络（在deep_neural_network.py的基础上增加了L2正则项）
<br>
<br>
6.deep_neural_network_with_dropout.py ：带dropout正则项的网络（在deep_neural_network.py的基础上增加了dropout正则项），具体详见CSDN博客：
https://blog.csdn.net/u012328159/article/details/80210363
<br>
<br>
7. gradient_checking.py： use gradient checking in dnn，梯度检验，可以检查自己手撸的bp是否正确。具体原理，详见我的CSDN博客：https://blog.csdn.net/u012328159/article/details/80232585
<br>
<br>
8. deep_neural_network_with_gd.py：实现了三种梯度下降，包括：batch gradient descent（BGD）、stochastic gradient descent（SGD）和 mini-batch gradient descent。具体内容见我的CSDN博客：https://blog.csdn.net/u012328159/article/details/80252012
<br>
<br>
9. deep_neural_network_with_optimizers.py：实现了深度学习中几种优化器，包括：momentum、nesterov momentum、Adagrad、Adadelta、RMSprop、Adam。关于这几种算法，具体内容，见本人的CSDN博客：https://blog.csdn.net/u012328159/article/details/80311892
<br>
<br>

<br>
<br>
--------
动态更新.................
