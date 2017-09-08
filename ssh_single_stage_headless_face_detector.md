# SSH: Single Stage Headless Face Detector

* Link https://arxiv.org/abs/1708.03979
* Authors:	Mahyar Najibi, Pouya Samangouei, Rama Chellappa, Larry Davis


![SSH](/imgs/ssh/ssh_3.png)

### * 问题 : 
    如何快速有效的检测出照片中很小的头像. 特别是照片中有很多人.

### * 概括 :
    目前先进的检测算法大都基于CNN, 检测过程分为两个阶段:
    1. 找到所有候选的Object Box.
    2. 对所有候选的Object Box进行分类检测. 这阶段涉及到的Network部分称为Head, 包含了大量的参数.
    并且为了适应不同大小的头像,需要额外生成pyramid图像,即对每个input再生成一些缩放比例的图像.  计算量大.

    而SSH有以下特点 : 
    1. 只有一个检测阶段
    2. 没有了Head(含有很多FC layer), 减少了大量的参数
    3. 可适用不同大小目标, 而不需要生成额外的pyramid input.

### * 算法：类似Region Proposal Network (RPN), 生成一组Anchros. 使用三个Detection module, 分别对应小,中,大头像. 每个module 包含一个binary classifier用来判定,一个regressor用来定位.
和RPN不同的是, 只生成一种长宽比的Anchros, 而RPN需要生成3种.

![SSH Model](/imgs/ssh/ssh_2.png)
