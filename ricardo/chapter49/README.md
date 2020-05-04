# 推荐系统
### 基于相似度协同过滤
#### 电影推荐
- 用户评分标准化，让不同用户的打分具有可比性
- 衡量和其他用户或者物品之间的相似度。找到相似的电影/相似用户
- 基于相似度，给相似的用户推荐其未看过的电影，给看某种电影的用户推荐看这种电影的用户看的电影
- 这都是建立在电影已经被人工分类的基础上
- 还有就是 矩阵的操作、变换

# SVD 奇异值分解，对未分类的电影和用户关系进行统计 推荐
- 如果矩阵 X 是对称的方阵，那么我们可以求得这个矩阵的特征值和特征向量，并把矩阵 X 分解为特征值和特征向量的乘积。
V 是这 n 个特征向量所张成的 n×n 维矩阵，而 Σ 是这 n 个特征值为主对角线的 n×n 维矩阵。这个过程就是特征分解
- 最终，SVD 分解把原来的“词条 - 文档”关系，转换成了“词条 - 语义概念 - 文档”的关系。而在推荐系统的应用场景下，对用户评分矩阵的 SVD 分解，能够帮助我们找到电影中潜在的“主题”，比如科幻类、动作类、浪漫类、传记类等等。分解之后所得到的奇异值 σ 对应了一个“主题”，σ 值的大小表
- X’X 这两个对称矩阵的特征分解，求得分解后的 U 矩阵、V 矩阵和 Σ 矩阵。另外，我们也解释了在用户对电影评分的应用场景下，SVD 分解后的 U 矩阵、V 矩阵和 Σ 矩阵各自代表的意义，其中 Σ 矩阵中的奇异值表示了 SVD 挖掘出来的电影主题，U 矩阵中的奇异向量表示用户对这些电影主题的评分，而 V 矩阵中的奇异向量表示了电影和这些主题的相关程度。