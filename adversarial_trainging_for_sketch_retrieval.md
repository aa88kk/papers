# Adversarial Training For Sketch Retrieval
[链接]https://arxiv.org/abs/1607.02748

### * 问题 : 
  在没有大量lablled data的情况下进行检索.
### * 场景 ：
  * 没有labbled data.
  * 可供训练的数据很少.
  * 类似文中提及的示例，检索古代文献中的字符.

### * 算法：利用GAN学习unlabbled data能力, 将 Discriminator 作为 Encoder。

### * 方法步骤：
1. 如普通GAN那样同时训练 Generator 和 Discriminator.
![Train GAN](/imgs/adversarial_trainging_for_sketch_retrieval/2.png)
2. 单独拿出 Discriminator, 去掉最后一层, 然后作为一个Encoder.
3. 搜索时，Encode需要预测的数据, 然后和训练过的进行比较，找出相似度最高的前n个作为结果.
![Search](/imgs/adversarial_trainging_for_sketch_retrieval/3.png)


### * 其他 :
  作者们比较了两种GAN, 一种受Sketch-A-Net启发的GAN更robust, 对于旋转等变换的容错度更高, 参数更少.

### * 结论 :
  GAN 作为一种Unsupervised Representation Learning方法，可以和CNN结合，在缺乏labled数据的情况下进行训练, 检索.
