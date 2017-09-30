# Nonlinear Computation in Deep Linear Networks
* Link https://blog.openai.com/nonlinear-computation-in-linear-networks/


今天, openai的发表了一篇重磅文章, 可能是本年度DL领域最重要的文章之一 .  用一句话概括就是: 利用计算机浮点数计算是非线性的机制,  使线性神经网络可以进行非线性计算. 想法真的是非常巧妙.

### 背景知识:

    * 神经网络是由线性的层+非线性的激活函数叠加而成.
    * 如果没有非线性的激活函数, 那么多个线性的层完全可以用一个线性层替换.
    * 计算机因为浮点型长度的限制,  浮点数的计算不能做到真正的线性!
        以float32为例, 最小的数是1 x 2^-126, 小于它的话都算作0.

### 实验结果:
    一个*线性*的神经网,  training acc : 94%, test acc : 91%.
    traing acc: > 99%, test acc 96.7%

### 方法:
    利用浮点数计算的非线性特点, 不需要tanh, relu等激活函数,就可以使得一个线性的神经网络进行非线性的计算.

### 可能带来的好处:
    可以在任何网络层上生成非线性features,  降低一些rnn的复杂性.
