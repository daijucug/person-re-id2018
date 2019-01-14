# person-re-id2018
行人重识别最新进展
# 1、云从
# Learning Discriminative Features with Multiple Granularities for Person Re-Identification
本次云从提出通过融合行人的全局信息以及具有辨识力的多粒度局部信息的思路，为解决ReID问题提供了一个非常不错的思路。云从科技本次提出的方案有几大优势:
（1）结构精巧：该方案实现了端到端的直接学习，并没有增加额外的训练流程;
（2）多粒度：融合了行人的整体信息与有区分度的多粒度细节信息;
（3）关注细节：模型真正懂得什么是人，模型会把注意力放在膝盖，衣服商标等能够显著区分行人的一些核心信息上。

![结构图](https://github.com/ZhangYK124/person-re-id2018/blob/master/img1.jpg)
