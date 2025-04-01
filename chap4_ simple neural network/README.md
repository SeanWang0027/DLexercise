# 1. 全连接神经网络

## 问题描述：

​	利用numpy 和tensorflow 、pytorch 搭建全连接神经网络。使用numpy 实现此练习需要自己手动求导，而tensorflow 和pytorch 具有自动求导机制。





## 数据集:

 	MNIST数据集包括60000张训练图片和10000张测试图片。图片样本的数量已经足够训练一个很复杂的模型（例如 CNN的深层神经网络）。它经常被用来作为一个新 的模式识别模型的测试用例。而且它也是一个方便学生和研究者们执行用例的数据集。除此之外，MNIST数据集是一个相对较小的数据集，可以在你的笔记本CPUs上面直接执行





## 题目要求：

​	补全本章节中所有*.ipynb文件中提示补全的部分。





# 2. 函数拟合

# 2. 函数拟合

## 问题描述：

​	理论和实验证明，一个两层的ReLU网络可以模拟任何函数[1~5]。请自行定义一个函数, 并使用基于ReLU的神经网络来拟合此函数。

### 理论证明如下：
首先说明ReLU只是一个非线性映射，并不是题目描述的“可以模拟任意函数”，但是以ReLU作为激活函数的MLP，在每一层节点的个数充分大时，的确足以拟合“任意定义在紧空间上的连续函数”，而非“任何函数”
先描述Universal Approximator Theorem：令 $\varphi(\cdot)$ 是一个有界且连续的单调上升函数，且 $\varphi(\cdot)$ 不恒为常数，令 $I_m$ 是 $\mathbb{R}^m$ 的一个紧子集，那么对于 $\forall\varepsilon>0,f\in C(I_m),\exists N\in\mathbb{N}$ 和 $v_i,b_i\in\mathbb{R},w_i\in\mathbb{R}^m,(i=1,2,\ldots,N)$, 使得可以定义 $F(x)=\sum_{i=1}^Nv_i\varphi(w_i^Tx+b_i)$ 满足 $|F(x)-f(x)|<\varepsilon$ 对 $\forall x\in I_m$ 成立
显然当 $\varphi=ReLU$ 时，虽然 $\varphi$ 在 $\mathbb{R}$ 上没有上界，不妨取函数$\varphi_{c,d}(x)=ReLU(x-c)-ReLU(x-d),(c<d)$ , $\varphi_{c,d}$ 有界、连续且单调，并且是两个ReLU函数的线性组合，因此可知函数集合 $\{F(x)=\sum_{i=1}^Nv_i\cdot\varphi_{c,d}(w_i^Tx+b_i):v_i,b_i\in\mathbb{R},w_i\in\mathbb{R}^m,N\in\mathbb{N}_+\}$在$C(I_m)$ 上是稠密的
 令$F(x)=\sum_{i=1}^Nv_i\cdot\varphi_{c,d}(w_i^Tx+b_i)=\sum_{j=1}^{2N}v_j^{\prime}\cdot ReLU(w_j^{\prime T}x+b_j^{\prime})$,则所有以ReLU为激活函数的单层神经网络能够表征的函数组成的集合 $\{F(x)=\sum_{i=1}^Nv_i\cdot ReLU(w_i^Tx+b_i):v_i,b_i\in\mathbb{R},w_i\in\mathbb{R}^m,N\in\mathbb{N}_+\}$ 在$C(I_m)$ 上是稠密的

以上得证，验证一个函数为$sin(x)+x/2$，代码放在chap4同目录下的test.ipynb文件中


## 要求: 

 	

- 请自行在函数上采样生成训练集和测试集，使用训练集来训练神经网络，使用测试集来验证拟合效果。
- 可以使用深度学习框架来编写模型，如tensorflow、pytorch、keras等。
  - 如果不使用上述框架，直接用NumPy实现可以最高加5分的附加分。
- 提交时请一并提交代码和报告。
  - 代码建议注释清楚（5分）
  - 报告至少应包含以下部分：（5分）
    - 函数定义、数据采集、模型描述、拟合效果。


## 示例： 

![](fitting.jpg)

## 参考文献： 

[1] G. Cybenko. 1989. Approximation by superpositions of a sigmoidal function.

[2] K. Hornik, M. Stinchcombe, and H. White. 1989. Multilayer feedforward networks are universal approximators.

[3] Moshe Leshno, et al. 1993. Multilayer feedforward networks with a nonpolynomial activation function can approximate any function

[4] Vinod Nair and Geoffrey E. Hinton. 2010. Rectified linear units improve restricted boltzmann machines.

[5] Xavier Glorot, Antoine Bordes, Yoshua Bengio. 2011. Deep Sparse Rectifier Neural Networks. PMLR 15:315-323.

