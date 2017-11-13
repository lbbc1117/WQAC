# WQAC

Wikipedia QA in Chinese

**[中文维基百科问答语料采集项目](http://blank)**
	
![Stage](https://img.shields.io/badge/当前阶段-数据采集-green.svg)
![Progress](http://progressed.io/bar/0?title=Progress)

## WQAC vs SQuAD

  <span style="color:white"></span> | WQAC     | SQuAD
---|--------- | -------------
**文本来源**|维基百科（中文）|维基百科（英文）
**段落数**|46000+ | 20000+
**每段问题数**|8～10 | 3～5
**问题改述\***|<div style="color:green">✔︎</div>|<div style="color:red">✘</div>

＊ 问题改述 即 Question Paraphrase，采集时要求志愿者将同一问题用不同方式提2次


	
## 项目计划

1. **数据采集**。

	以互联网为媒介，由志愿者提交问答数据。
	
2. **数据审核**。

	组织少数志愿者，以审核者的身份，对第一阶段收集的数据作质量检查，筛选出不过关的数据。
	
3. **数据二次采集**。

	对第二阶段中质量不过关的数据进行二次采集。
	
4. **数据整理与发布**。

	对二次采集后的数据再次进行检查，若有必要，还会发起第三次采集；若数据质量总体良好，则公开发布WQAC数据集。	

## 项目愿景

随着深度学习理论与技术的进步，在很多应用场合下，计算机的能力已经超过人类，例如图像领域的人脸识别、物体追踪，控制领域的Atari游戏、围棋，自然语言领域的语音识别、机器翻译等等。

这样一种机器在各方面对人类追赶甚至超越的局面，是否说明我们已经或即将创造出与人类同级别的“智能”？

答案是否定的。理由如下：

1. **不同领域中，深度学习技术依然“各自为战”**
	
	用于人脸识别的模型不会下围棋、用于识别语音的模型看不懂表情、用于文本分类的模型又听不到声音。这些模型功能上就是一个个专家系统，只用来解决一类问题，也只能解决好这类问题，好比一个人有千里眼，却没长耳朵、鼻子、嘴巴。
	
2. **在很多领域中，深度学习技术患有“数据饥渴”**

	许多研究者将数据比喻为机器学习的“火箭燃料”。一般来说，在大量数据上训练的平庸模型的表现会比在少量数据上训练的伟大模型要好得多。一个硬盘就可以装满人类诞生以来所创造的所有文字，机器可以短时间内把这些文字“阅读”多遍，但我们依然没有发明出写作水平超过莎士比亚、罗曼罗兰、鲁迅的模型，即便模型的“阅读量”已经高出这些作家若干个数量级。
	
3. **在一些领域中，深度学习技术还在“咿呀学语”**

	例如在复杂控制领域，实体机器人的寻线和避障能力还远不及人类，波士顿动力的“大狗”机器人依然需要美军士兵通过遥控器控制方向、花几千大洋买的扫地机器人在狭窄空间可能会闷头乱撞找不到出口；在机器阅读理解方面，得益于SQuAD数据集的发布，一年多来取得了巨大进步，但依然距离人类平均水平有一定差距，我们的WQAC项目就是受到SQuAD的启发而发起。
	
--------
	
**[SQuAD](https://rajpurkar.github.io/SQuAD-explorer/)** [[1]](#ref1) 由斯坦福大学于2016年6月发布，之后迅速成为机器阅读理解领域的“标准”数据集，类似于ImageNet之于图像识别。SQuAD之所以成功有2点原因：

1. **SQuAD提供了一种更贴近实用的问答机制**

	数据集中的问题基于给定文本提出，问题的答案也必须来自文本（从文本中截取的某段子文本）。其他阅读理解数据集，有些是完形填空的形式，这种形式应用场合太少；有些是多个答案中做选择，也面临应用场合少的问题；还有一些允许开放性答案，需要模型具有背景知识才能回答，方向是没问题的，但是步子迈大了。SQuAD要求的问答形式够简单，但同时要求模型具有推理能力、注意力机制等，想在该数据集上达到人类水平，也是极具挑战的。

2. **SQuAD数据有足够的质量与数量**

	有些数据集有很高的质量，例如 MCTest [[2]](#ref2) 收集了660篇故事文本，每篇包含4个问题，每个问题提供4个答案供选择。该数据集由人类手动创建，质量较高，但其有限的数据量难以用于训练具有高泛化能力的模型。有些数据集数据量惊人，例如 CNN／Daily Mail [[3]](#ref3) 的文档达到十万级，问题达到百万级。该数据集采用完形填空的形式提问，生成问题的过程可以一定程度自动化，所以能够轻易产生大量数据。然而，在其诞生后不久，就有研究表明完形填空对模型的推理能力要求较低，在此类数据集上取得优异表现并不困难 [[4]](#ref4)。
	
--------

SQuAD 的文本来自于英文维基百科（Wikipedia），每段文本有3～5个问题。问题的采集过程通过众包的方式、以互联网为媒介完成：他们在 Daemo [[5]](#ref5) 平台雇用了若干人，每个人被要求在4分钟内完成对一个段落的提问，每小时薪酬9美元。该项目要求被雇用人员在 Daemo 平台的 Human Intelligence Tasks (HITs) 被接受率在 97% 以上，并且至少有过 1000 次提交，以保证问题质量。

目前为止，很多知名的深度学习科研团队都在 SQuAD 竞赛中提交了自己的模型，这些团队包括：微软亚洲研究院、Salesforce、复旦大学、科大讯飞等。截至2017年11月11日，表现最好的模型是哈工大与科大讯飞合作的`Interactive AoA Reader+`(ensemble)。其 EM 和 F1 得分分别为 79.083	和 86.450，相应的人类表现为 82.304 和 91.221，这已经是一个非常振奋人心的成绩！并且从数据集发布，到取得目前的成绩只用了1年又4个月！

可以推断，英文世界中将很快会出现基于深度学习技术的高质量的阅读理解服务。首先获益的将是那些有在线客服业务的企业。最可能的技术路线是这样的：

> 1. 公司提供完整、详细的产品文档D
> 2. 基于文档D，组织人力生成一批问答数据S
> 3. 将某个在SQuAD上达到或超越人类水平的模型M，在S上作迁移学习，得到M1
> 4. 将模型M1封装为线上服务，部分取代或取代人工客服
	
难怪刘强东说：“机器人把人所有的工作都做了，共产主义在我们这一代就可以实现”。

所以，我们希望，在中文世界中，也能够有一个质量高、数量大的数据集，成为自动化问答技术的基础。这就是 WQAC 项目的初衷与愿景。

### 参考文献

[1] <span id="ref1">Rajpurkar et al. Squad: 100,000+ questions for machine comprehension of text. arXiv2016.</span>

[2] <span id="ref2">M. Richardson, C. J. Burges, and E. Renshaw. 2013.
Mctest: A challenge dataset for the open-domain machine
comprehension of text. In Empirical Methods in
Natural Language Processing (EMNLP), pages 193–
203.</span>

[3] <span id="ref3">K. M. Hermann, T. Kocisk ˇ y, E. Grefenstette, L. Espeholt, ´
W. Kay, M. Suleyman, and P. Blunsom. 2015. Teaching
machines to read and comprehend. In Advances in
Neural Information Processing Systems (NIPS).</span>

[4] <span id="ref4">D. Chen, J. Bolton, and C. D. Manning. 2016. A
thorough examination of the CNN / Daily Mail reading
comprehension task. In Association for Computational
Linguistics (ACL).</span>

[5] <span id="ref5">S. N. Gaikwad, D. Morina, R. Nistala, M. Agarwal,
A. Cossette, R. Bhanu, S. Savage, V. Narwal, K. Rajpal,
J. Regino, et al. 2015. Daemo: A self-governed
crowdsourcing marketplace. In Proceedings of the
28th Annual ACM Symposium on User Interface Software
& Technology, pages 101–102.</span>