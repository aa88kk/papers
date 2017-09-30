# Nonlinear Computation in Deep Linear Networks
* Link https://blog.openai.com/nonlinear-computation-in-linear-networks/


今天(20170930), openai的发表了一篇文章, 可能是本年度DL领域最重要的文章之一 .  用一句话概括就是: 利用计算机浮点数计算是非线性的机制,  使线性神经网络可以进行非线性计算. 想法很巧妙.

### 背景知识:
    * 神经网络是由线性的层+非线性的激活函数叠加而成.
    * 如果没有非线性的激活函数, 那么多个线性的层完全可以用一个线性层替换.
    * 计算机因为浮点型长度的限制,  浮点数的计算不能做到真正的线性!
        以float32为例, 最小的数是1 x 2^-126, 小于它的话都算作0.

![float32](/imgs/nonlinear_computation_in_linear_networks/1.png)

### 方法:
    ⋅⋅⋅假设min等于最小的float32, 即min=1 x 2^-126, 那么绝对值在0, min之间, 都取值为0, 即不再是线性. 为了利用这个特性, 需要将参数的绝对值值限制在0, min之间, 从而替代tanh, relu等激活函数. 
    ⋅⋅⋅但是由于数值太小, 没法通过反向传播来训练, 于是openai使用evolution strategies(ES)来优化, (ES也是openai今年很重要的一篇论文, 强烈推荐下)

### 实验结果:
    一个*线性*的神经网:
        training acc : 94%, test acc : 91%.
        traing acc: >99%, test acc 96.7%

### 可能带来的好处:
    可以在任何网络层上生成非线性features,  降低一些rnn的复杂性.
