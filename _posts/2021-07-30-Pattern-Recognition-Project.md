---
layout: post
title:  "模式识别课程大作业 Shopee 商品图像检索"
date:   2021-07-30
categories: pattern-recognition
tags: deep-learning pytorch kaggle
author: Jingxuan Yang
mathjax: true
---

* content
{:toc}

## 大作业项目简介

在如今的信息科技时代, 带有拍照功能的移动设备如手机、相机等得到了极大的普及和流行, 各种各样的图片和视频可以随时随地获得, 并借助互联网快速传播, 这种趋势使得网络上的数字图片和视频数据呈现出爆炸式的增长. 

大量的数字图像信息给人们生产生活带来了许多便利的同时, 也给海量图像数据管理带来了挑战, 研究从海量的图像数据库中高效地查询到感兴趣的图像的技术变得越来越重要, 这种从图像数据库中查找给定图像的技术称为**图像检索**. 






![图像检索系统, 图片来源: https://www.ssla.co.uk/image-retrieval-system/](https://gitee.com/jingxuanyang/picture/raw/master/2021-7-30/1627636504234-image-retrieval-system-300x160.png)


当前的图像检索方法按照数据有无标注可以划分为：监督、无监督、半监督、弱监督以及伪监督和自监督方法；按照模型主体结构又包括：自编码网络、孪生网络、对抗生成网络、注意力网络、循环神经网络等；按照特征的形式可以分为：二进制描述、实数特征描述以及聚合描述；按照检索方式又可以分为：基于文本的检索、基于内容的检索以及文本与图像多模态的检索三类方法. 

本项目要求在数据集中找出与给定查询图像属于相同商品类别的图像，数据集来自 Kaggle 竞赛 **Shopee - Price Match Guarantee**, 竞赛链接如下:

> https://www.kaggle.com/c/shopee-product-matching/overview

![Shopee - Price Match Guarantee 竞赛界面](https://gitee.com/jingxuanyang/picture/raw/master/2021-7-30/1627635598696-4.png)

数据集包含 `train.csv` 和 `test.csv` 两个 `csv` 文件以及 `train_images/` 和 `test_images/` 两个图像文件夹. 

`train.csv` 文件包含 34250 行数据, 其前 5 行如下表所示:

![`train.csv` 表格前5行](https://gitee.com/jingxuanyang/picture/raw/master/2021-7-30/1627634859125-2.png)

表格第一列为索引, 第二列为每张图片独特的识别 id, 第三列为图片文件名, 第四列为图片感知哈希值, 第五列为图像的标题, 主要为印尼语和部分英语, 第六列为图像的标签, 相同的标签表示图像为同一个类别, 表格中没有缺失数据. 

`train_images/` 文件夹包含 32412 张图片, 图片的文件名与 `train.csv` 中的 image 列相对应.

![`train_images/` 文件夹部分图片](https://gitee.com/jingxuanyang/picture/raw/master/2021-7-30/1627634993858-3.png)

针对上述研究任务, 基于多个机器学习模型进行了探索、研究和分析. 本项目全部代码和报告均在GitHub开源, 地址如下:

> https://github.com/jingxuanyang/Shopee-Product-Matching

![Shopee-Product-Matching 项目界面](https://gitee.com/jingxuanyang/picture/raw/master/2021-7-30/1627634169707-1.png)

## 研究报告简介

本文使用机器学习相关算法研究商品图像检索问题, 基于每个商品的图像信息和文本描述信息, 给定查询图片和文本, 在数据集中寻找与查询图片相似的图片, 输出全部相似图片的集合. 

上述任务可以划分为三个子任务: 仅利用图像信息进行检索, 仅利用文本信息进行检索以及同时利用图像信息与文本信息进行检索. 

+ 针对仅利用图像信息进行检索, 本文建立了 resnet50, resnext50\_32x4d, densenet121, efficientnet\_b3, eca\_nfnet\_l0, 图像模型 Ensemble 等 **6 个图像模型**. 

+ 针对仅利用文本信息进行检索, 本文建立了 tf-idf, bert-base-multilingual-uncased, bert-base-indonesian-1.5G, distilbert-base-indonesian, paraphrase-xlm-r-multilingual-v1, paraphrase-distilroberta-base-v1, 文本模型 Ensemble 等 **7 个文本模型**.

+ 针对同时利用图像信息与文本信息进行检索，本文建立了 TF-IDF 与 ResNet 取并集, SBERT 与 NFNet 取并集, TF-IDF 与 ResNet 度量层输出融合, SBERT 与 NFNet 度量层输出融合, 图像 Ensemble 与 文本 Ensemble 取并集等 **5 个图像文本融合模型**.

从机器学习的角度出发, 本文基于数据分布特性和嵌入空间特性提出了 **Min2 最少两个原则**以及 **INB 迭代邻域混合**两种模型改进方法, 这两种改进方法都使得原有模型的性能有了较大的提升.

针对数据集划分, 基于保证训练集, 验证集与测试集的数据保持相同分布的原则, 本文利用机器学习工具包 scikit-learn 提供的 `GroupKFold` 函数将数据分为数量相等 5 个组, 并按组划分为 3:1:1 的三份, 分别为训练集, 验证集与测试集. 

对于评价指标, 本文选择选择**精确率**, **召回率**以及 **F1 分数**, 并且计算方式为按行计算并取平均值. 精确率可以表示找到的相似图片是否准确, 而召回率可以表示找到的相似图片是否全面, 最终模型的性能评价采用精确率与召回率的综合评定指标 F1 分数来确定.

仅利用图像信息进行检索任务中, NFNet 模型性能最优, 仅利用文本信息进行检索任务中, SBERT 模型性能最优, 同时利用图像信息与文本信息进行检索任务中, NFNet 与 SBERT 强强联合进行度量层输出融合性能最优, 而且综合来看文本模型的 F1 分数均大于图像模型的 F1 分数. 

所有的 18 个模型中, 以 F1 分数为评价依据, 性能最优的模型为 NFNet 模型 eca\_nfnet\_l0 与 SBERT 模型 paraphrase-xlm-r-multilingual-v1 进行度量层输出融合得到的模型, 其结果为 

$$
  \begin{aligned}
    \overline{F1}&=0.888967\\
    \bar{R}&=0.928442\\
    \bar{P}&=0.893179\\
  \end{aligned}
$$

对于实验结果, 本文分析了模型超参数对性能的影响, 针对每个模型都得到了更优的模型超参数. 并且本文分析了特征的重要性, 发现文本特征对于本次任务比图像特征更加重要. 

本文还进行了错误分析, 案例分析以及实验结果的可视化分析, 对模型在不同数据集上的表现进行了全面深入和可视化的详细分析. 

最后本文对 Min2 和 INB 两种改进方法得到的结果进行了分析, 这两种改进方法都使得原有模型的性能有了较大的提升.


## 研究报告全文

![](../figures/prproject/report_Page_01.jpg)
![](../figures/prproject/report_Page_02.jpg)
![](../figures/prproject/report_Page_03.jpg)
![](../figures/prproject/report_Page_04.jpg)
![](../figures/prproject/report_Page_05.jpg)
![](../figures/prproject/report_Page_06.jpg)
![](../figures/prproject/report_Page_07.jpg)
![](../figures/prproject/report_Page_08.jpg)
![](../figures/prproject/report_Page_09.jpg)
![](../figures/prproject/report_Page_10.jpg)

![](../figures/prproject/report_Page_11.jpg)
![](../figures/prproject/report_Page_12.jpg)
![](../figures/prproject/report_Page_13.jpg)
![](../figures/prproject/report_Page_14.jpg)
![](../figures/prproject/report_Page_15.jpg)
![](../figures/prproject/report_Page_16.jpg)
![](../figures/prproject/report_Page_17.jpg)
![](../figures/prproject/report_Page_18.jpg)
![](../figures/prproject/report_Page_19.jpg)
![](../figures/prproject/report_Page_20.jpg)

![](../figures/prproject/report_Page_21.jpg)
![](../figures/prproject/report_Page_22.jpg)
![](../figures/prproject/report_Page_23.jpg)
![](../figures/prproject/report_Page_24.jpg)
![](../figures/prproject/report_Page_25.jpg)
![](../figures/prproject/report_Page_26.jpg)
![](../figures/prproject/report_Page_27.jpg)
![](../figures/prproject/report_Page_28.jpg)
![](../figures/prproject/report_Page_29.jpg)
![](../figures/prproject/report_Page_30.jpg)

![](../figures/prproject/report_Page_31.jpg)
![](../figures/prproject/report_Page_32.jpg)
![](../figures/prproject/report_Page_33.jpg)
![](../figures/prproject/report_Page_34.jpg)
![](../figures/prproject/report_Page_35.jpg)
![](../figures/prproject/report_Page_36.jpg)
![](../figures/prproject/report_Page_37.jpg)
![](../figures/prproject/report_Page_38.jpg)
![](../figures/prproject/report_Page_39.jpg)
![](../figures/prproject/report_Page_40.jpg)

![](../figures/prproject/report_Page_41.jpg)
![](../figures/prproject/report_Page_42.jpg)
![](../figures/prproject/report_Page_43.jpg)
![](../figures/prproject/report_Page_44.jpg)
![](../figures/prproject/report_Page_45.jpg)
![](../figures/prproject/report_Page_46.jpg)
![](../figures/prproject/report_Page_47.jpg)
![](../figures/prproject/report_Page_48.jpg)
![](../figures/prproject/report_Page_49.jpg)
![](../figures/prproject/report_Page_50.jpg)

![](../figures/prproject/report_Page_51.jpg)
![](../figures/prproject/report_Page_52.jpg)
![](../figures/prproject/report_Page_53.jpg)
![](../figures/prproject/report_Page_54.jpg)
![](../figures/prproject/report_Page_55.jpg)
![](../figures/prproject/report_Page_56.jpg)
![](../figures/prproject/report_Page_57.jpg)
![](../figures/prproject/report_Page_58.jpg)
![](../figures/prproject/report_Page_59.jpg)
![](../figures/prproject/report_Page_60.jpg)

![](../figures/prproject/report_Page_61.jpg)
![](../figures/prproject/report_Page_62.jpg)
![](../figures/prproject/report_Page_63.jpg)
![](../figures/prproject/report_Page_64.jpg)
![](../figures/prproject/report_Page_65.jpg)
![](../figures/prproject/report_Page_66.jpg)
![](../figures/prproject/report_Page_67.jpg)
![](../figures/prproject/report_Page_68.jpg)
![](../figures/prproject/report_Page_69.jpg)
![](../figures/prproject/report_Page_70.jpg)

![](../figures/prproject/report_Page_71.jpg)
![](../figures/prproject/report_Page_72.jpg)
![](../figures/prproject/report_Page_73.jpg)
![](../figures/prproject/report_Page_74.jpg)
![](../figures/prproject/report_Page_75.jpg)
![](../figures/prproject/report_Page_76.jpg)
![](../figures/prproject/report_Page_77.jpg)
![](../figures/prproject/report_Page_78.jpg)
![](../figures/prproject/report_Page_79.jpg)
![](../figures/prproject/report_Page_80.jpg)
