# 熵、信息增益和卡方：如何寻找关键特征？
### 什么是特征选择？
- 我今天要聊的特征选择，会聚焦在监督式学习中的特征处理方法。
- 监督式学习，是指通过训练资料学习并建立一个模型，并依此模型推测新的实例，主要包括分类（Classification）和回归（Regression）。
### 监督式机器学习的主要步骤
- 数据的准备
- 特征工程
- 模型拟合
- 离线和在线测试
#### 特征工程
- 原始特征到计算机数据的转化 ：如何把现实世界中水果的各类特征转化为计算机所能理解的数据，这个过程其实就是最初级的特征工程
- 特征选择
- 缺失值的填补
- 异常值的去除
##### 特征选择
> 对于分类问题，我们更关心的是如何正确地把一篇文章划分到正确的分类中。一个好的特征选择，应该可以把那些对分类有价值的信息提取出来，而过滤掉那些对分类没有什么价值的信息
- 如果一个特征，经常只在某个或少数几个分类中出现，而很少在其他分类中出现，那么说明这个特征具有较强的区分力，它的出现很可能预示着整个数据属于某个分类的概率很高或很低。是否属于少数几个类这一点，可以使用信息熵来衡量,计算出每个特征所对应的数据集之熵，我们就可以按照熵值由低到高对特征进行排序，挑选出排列靠前的特征。
- 如果基于某个特征的划分，所产生的信息增益越大，说明这个特征对于分类的判断越有价值。所以，我们可以为计算基于每个特征的划分，所产生的信息增益，然后按照增益值由高到低对特征进行排序，挑选出排列靠前的特征。

##### 利用卡方检验进行特征选择
- 特征/分类
- 如果两者独立，证明特征和分类没有明显的相关性，特征对于分类来说没有提供足够的信息量。反之，如果两者有较强的相关性，那么特征对于分类来说就是有信息量的，是个好的特征。为了检验独立性，卡方检验考虑了四种情况的概率：P(fi​,cj​) 、P(fi​ˉ​,cj​ˉ​)、P(fi​,cj​ˉ​) 和 P(fi​ˉ​,cj​)。
- 在这四种概率中，P(fi​,cj​) 和 P(fi​ˉ​,cj​ˉ​) 表示特征 fi​ 和分类 cj​ 是正相关的。如果 P(fi​,cj​) 很高，表示特征 fi 的出现意味着属于分类 cj​ 的概率更高；
- 如果 P(fi​ˉ​,cj​ˉ​) 很高，表示特征 fi​ 不出现意味着不属于分类 cj​ 的概率更高。类似地，P(fi​,cj​ˉ​) 和 P(fi​ˉ​,cj​) 表示特征 fi​ 和分类 cj​ 是负相关的。如果 P(fi​,cj​ˉ​) 很高，表示特征 fi​ 的出现意味着不属于分类 cj​ 的概率更高；如果 P(fi​ˉ​,cj​) 很高，表示特征 fi​ 不出现意味着属于分类 cj​ 的概率更高。
- 如果特征和分类的相关性很高，要么是正向相关值远远大于负向相关值，要么是负向相关值远远大于正向相关值。如果特征和分类相关性很低，那么正向相关值和负向相关的值就会很接近。卡方检验就是利用了正向相关和负向相关的特性。