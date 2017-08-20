# Adversarial Training For Sketch Retrieval
https://arxiv.org/abs/1607.02748

### * 问题 : 
  在没有大量lablled data的情况下进行visual search.
### * 场景 ：
  * 没有labbled data.
  * 可供训练的数据很少.
### * 利用GAN学习unlabbled data能力。

### * 主要步骤：
1. 如普通GAN那样同时训练 Generator 和 Discriminator.
2. 单独拿出 Discriminator, 去掉最后一层, 然后作为一个Encoder.
3. 搜索时，Encode需要预测的数据, 然后和训练过的进行比较，找出相似度最高的前n个作为结果.
