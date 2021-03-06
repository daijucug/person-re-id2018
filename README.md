# person-re-id2018
行人重识别最新进展
# 1、云从
# Learning Discriminative Features with Multiple Granularities for Person Re-Identification
[paper](https://arxiv.org/pdf/1804.01438.pdf)
[code](https://github.com/Gavin666Github/reid-mgn)

   本次云从提出通过融合行人的全局信息以及具有辨识力的多粒度局部信息的思路，为解决ReID问题提供了一个非常不错的思路。云从科技本次提出的方案有几大优势:
（1）结构精巧：该方案实现了端到端的直接学习，并没有增加额外的训练流程;
（2）多粒度：融合了行人的整体信息与有区分度的多粒度细节信息;
（3）关注细节：模型真正懂得什么是人，模型会把注意力放在膝盖，衣服商标等能够显著区分行人的一些核心信息上。

![结构图](https://github.com/ZhangYK124/person-re-id2018/blob/master/img2.jpg)

   多粒度网络(Multiple Granularity Network,MGN)如上图所示，该结构的基础网络部分采用业内最为常用的Resnet50。根据对Resnet50网络以及跨镜追踪的深刻分析，作者创新性地对Resnet50进行了合理的修改，使用Resnet50前三层提取图像的基础特征，而在高层次的语意级特征作者设计了3个独立分支。如图所示，第一个分支负责整张图片的全局信息提取，第二个分支会将图片分为上下两个部分提取中粒度的语意信息，第三个分支会将图片分为上中下三个部分提取更细粒度的信息。这三个分支既有合作又有分工，前三个低层权重共享，后面的高级层权重独立，这样就能够像人类认知事物的原理一样即可以看到行人的整体信息与又可以兼顾到多粒度的局部信息。

   同时文章对损失函数部分也进行了精心而巧妙的设计。三个分支最后一层特征都会进行一次全局MaxPooling操作，而第二分支与第三分支还会分别再进行局部的MaxPooling，然后再将特征由2048维降为256维。最后256维特征同时用于Softmax Loss与Triplet Loss计算。另外，作者在2048维的地方添加一个额外的全局Softmax Loss，该任务将帮助网络更全面学习图片全局特征。

   而在测试的时候只需使用使用256维特征作为该行人的特征进行比较，无需使用2048维的特征，使用欧氏距离作为两个行人相似度的度量。

# 2、腾讯优图
# A Coarse-to-fine Pyramidal Model for Person Re-identification via Multi-Loss Dynamic Training
[paper](https://arxiv.org/abs/1810.12193?context=cs)

总之，本文主要由以下三个贡献：
1）为了放松对强检测模型的假设，我们提出了一种新的粗到细金字塔模型，它不仅融合了局部和全局信息，而且整合了它们之间的渐进线索。2）为了最大限度地利用不同的损失，我们探索了一种动态训练方案，将两种损失无缝地统一起来，并提取出它们之间适当的共享信息，用于学习识别性身份表示。3）该方法在三个数据集上都达到了最先进的结果，最显著的是，我们的方法在数据集CUHK03上超过了当前的最佳方法9.5%。

![结构图](https://github.com/ZhangYK124/person-re-id2018/blob/master/img3.jpg)


# 3、阿里
其性能的提高主要来源于技术层面的创新：该团队通过局部信息的挖掘，致力于解决行人在识别过程中表观姿态变化剧烈，不容易对齐的问题。一方面，通过人体语义分割得到具有强语义信息的部件，并利用注意力机制在其中寻找最具有区分性的区域。另一方面，使用了基于金字塔的水平分块策略，得到行人固定区域的可辨识信息。在训练中，同时采用两种策略相结合的方式，达到行人图片的对齐，从而实现更精准的匹配识别。通过技术上的改进，该方法在三个公开数据库上的效果均优于之前最好方法，特别是mAP指标，分别提升了2%，1.87%，3.39%。

![结构图](https://github.com/ZhangYK124/person-re-id2018/blob/master/img4.jpg)


# 4、文安智能
基于人体关键点的多粒度网络结构

![结构图](https://github.com/ZhangYK124/person-re-id2018/blob/master/img5.jpg)

# 5、千视通

千视通之所以能够得到比较好的结果，最大的原因则是与传统的全局表征或设定好的局部分割方法不同。

一、一般算法只考虑了全局、多粒度及水平汇集讯息，而水平汇集讯息主要用于把图片对齐。在实际的情况下，摄像头的角度多变，同时人行是非刚体，所以，垂直方向也理应同时考虑。对于此种情况，千视通在网络设计上开发了自研的垂直汇集及其关联的算法层，用以更好的适应以上情况。

二、针对损失函数进行改良，千视通的 Re-ID 算法提出了新的方案，能一方面增大类间距离并同时最细化类内距离。这代表能提高所计算出的高维特征向量的唯一性，并能有效的提高可识别率。

# 6、大华

![结构图](https://github.com/ZhangYK124/person-re-id2018/blob/master/img6.jpg)

　　大华股份经过多年的技术积累，对算法进行了持续优化，提出了创新技术方案：基于人体结构的分块模型，提取显著的局部特征；融合多层语义信息，学习不同层级特征，使得特征更具表达能力；利用空间注意力模型解决局部特征对齐问题。


## 效果

![结构图](https://github.com/ZhangYK124/person-re-id2018/blob/master/img7.png)
