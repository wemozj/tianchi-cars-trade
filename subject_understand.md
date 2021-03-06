# 二手车交易价格预测之赛题理解

## 1. 赛题目标

赛题目标是：预测二手车的交易价格。

## 2. 评测标准

评价标准为MAE(Mean Absolute Error)，平均绝对值误差。

真实值：
$$
y=\left(y_{1}, y_{2}, \cdots, y_{n}\right)
$$
预测值：
$$
\hat{y}=\left(\hat{y}_{1}, \hat{y}_{2}, \cdots, \hat{y}_{n}\right)
$$
该模型的MAE计算公式为：
$$
M A E=\frac{\sum_{i=1}^{n}\left|y_{i}-\hat{y}_{i}\right|}{n}
$$

### 3. 结果提交形式

> SaleID, price
> 150000,687
> 150001,1250

### 4. 数据概况

15万条数据作为训练集；5万条作为测试集。

每一列代表一种特征属性；未告知数据列所属的性质为匿名特征。

- SaleID - 销售样本ID
- name - 汽车编码
- regDate - 汽车注册时间
- model - 车型编码
- brand - 品牌
- bodyType - 车身类型
- fuelType - 燃油类型
- gearbox - 变速箱
- power - 汽车功率
- kilometer - 汽车行驶公里
- notRepaireDamage - 汽车有尚未修复的损坏
- regionCode - 看车地区编码
- seller - 销售方
- offerType - 报价类型
- creatDate - 广告发布时间
- price - 汽车价格
- v_0', 'v_1', 'v_2', 'v_3', 'v_4', 'v_5', 'v_6', 'v_7', 'v_8', 'v_9', 'v_10', 'v_11', 'v_12', 'v_13','v_14' 【匿名特征，包含v0-14在内15个匿名特征】

### 5. 进一步赛题分析
拟解决的问题：
- 找出/挖掘关键特征
- 估摸用什么方法解决问题
- 数据额如何进行预处理
- 评价指标

## 1.4 经验总结
作为切入一道赛题的基础，赛题理解是极其重要的，对于赛题的理解甚至会影响后续的特征工程构建以及模型的选择，最主要是会影响后续发展工作的方向，比如挖掘特征的方向或者存在问题解决问题的方向，对了赛题背后的思想以及赛题业务逻辑的清晰，也很有利于花费更少时间构建更为有效的特征模型，赛题理解要达到的地步是什么呢，把一道赛题转化为一种宏观理解的解决思路。 以下将从多方面对于此进行说明：

1） 赛题理解究竟是理解什么： 理解赛题是不是把一道赛题的背景介绍读一遍就OK了呢？并不是的，理解赛题其实也是从直观上梳理问题，分析问题是否可行的方法，有多少可行度，赛题做的价值大不大，理清一道赛题要从背后的赛题背景引发的赛题任务理解其中的任务逻辑，可能对于赛题有意义的外在数据有哪些，并对于赛题数据有一个初步了解，知道现在和任务的相关数据有哪些，其中数据之间的关联逻辑是什么样的。 对于不同的问题，在处理方式上的差异是很大的。如果用简短的话来说，并且在比赛的角度或者做工程的角度，就是该赛题符合的问题是什么问题，大概要去用哪些指标，哪些指标是否会做到线上线下的一致性，是否有效的利于我们进一步的探索更高线上分数的线下验证方法，在业务上，你是否对很多原始特征有很深刻的了解，并且可以通过EDA来寻求他们直接的关系，最后构造出满意的特征。

2） 有了赛题理解后能做什么： 在对于赛题有了一定的了解后，分析清楚了问题的类型性质和对于数据理解的这一基础上，是不是赛题理解就做完了呢? 并不是的，就像摸清了敌情后，我们至少就要有一些相应的理解分析，比如这题的难点可能在哪里，关键点可能在哪里，哪些地方可以挖掘更好的特征，用什么样得线下验证方式更为稳定，出现了过拟合或者其他问题，估摸可以用什么方法去解决这些问题，哪些数据是可靠的，哪些数据是需要精密的处理的，哪部分数据应该是关键数据（背景的业务逻辑下，比如CTR的题，一个寻常顾客大体会有怎么样的购买行为逻辑规律，或者风电那种题，如果机组比较邻近，相关一些风速，转速特征是否会很近似）。这时是在一个宏观的大体下分析的，有助于摸清整个题的思路脉络，以及后续的分析方向。

3） 赛题理解的-评价指标： 为什么要把这部分单独拿出来呢，因为这部分会涉及后续模型预测中两个很重要的问题： 1． 本地模型的验证方式，很多情况下，线上验证是有一定的时间和次数限制的，所以在比赛中构建一个合理的本地的验证集和验证的评价指标是很关键的步骤，能有效的节省很多时间。 2． 不同的指标对于同样的预测结果是具有误差敏感的差异性的，比如AUC，logloss, MAE，RSME，或者一些特定的评价函数。是会有很大可能会影响后续一些预测的侧重点。

4） 赛题背景中可能潜在隐藏的条件： 其实赛题中有些说明是很有利益-都可以在后续答辩中以及问题思考中所体现出来的，比如高效性要求，比如对于数据异常的识别处理，比如工序流程的差异性，比如模型运行的时间，比模型的鲁棒性，有些的意识是可以贯穿问题思考，特征，模型以及后续处理的，也有些会对于特征构建或者选择模型上有很大益处，反过来如果在模型预测效果不好，其实有时也要反过来思考，是不是赛题背景有没有哪方面理解不清晰或者什么其中的问题没考虑到。