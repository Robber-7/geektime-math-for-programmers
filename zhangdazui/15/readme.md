# 15 | 从树到图：如何让计算机学会看地图？

地图导航的算法，先把交通地图转为图的模型。图中的每个结点表示一个地点，每条边表示一条道路或者交通工具的路线。同时边是有权重的，可以是时间的，距离的权重。

广度优先搜索只测量通路的长度，而不考虑每条边上的权重。那么广度优先搜索就无法高效地完成这个任务。

广度优先和深度优先处理地图导航的问题，会出现两个问题；

1. 由于要遍历所有可能的通路，因此一个点可能会被访问多次。
2. 如果某个结点 x 和起始点 s 之间存在多个通路，每当 x 到 s 之间的最优路线被更新之后，我们还需要更新所有和 x 相邻的结点之最优路线，计算复杂度会很高。

## Dijkstra 算法

Dijkstra 算法的核心思想是,如果已经找出某个节点的最优解，之后就无须再考虑该节点。可以有效的减少访问节点的次数，而提高效率。

### Dijkstra 算法的步骤

**符号说明：**

- s => source，表示图中的起始点；
- w => weight, w[s,m] 表示 s 到 m 的权重；
- mw => min_weight, mw[m] 表示从起点 s 到 m 的最小权重；
- F => Finish 表示已经找到最小权重的结点之集合；

#### 步骤一、初始化

1. 把起始点 s 的最小权重赋为 0，也就是 mw[s] = 0。
2. 往集合 F 里添加结点 s，F 包含且仅包含 s。
3. 假设结点 s 能直接到达的边集合为 M，对于其中的一条边 m，则把 mw[m] 设为 w[s, m]，同时对于所有其他 s 不能直接到达的结点，将通路的权重设为无穷大。

#### 步骤二、重复流程

1. 查找最小 mw。
2. 更新权重。

### 归纳法证明 Dijkstra 算法正确性

**命题：** Dijkstra 算法都可以找到任意点 m 和起始点 s 之间拥有最小权重的通路。

**证明：** 

1. 首先，当 n=1 的时候，也就是只有起始点 s 和另一个终止点的时候，Dijkstra 算法的初始化阶段的第 3 步，保证了命题的成立。
2. 假设 n=k-1 的时候命题成立，表明从点 s 到 k-1 个终点的任何一个时，Dijkstra 算法都能找到拥有最小权重的通路。那么再增加一个结点 x，Dijkstra 算法同样可以为包含 x 的 k 个终点找到最小权重通路。

### 思考题

1、 如果边的权重是负数，我们还能用今天讲的 Dijkstra 算法吗？

答： 如果权重都是负数可以使用 Dijkstra 算法。 如果有正数有负数无法使用。因为当我们将一个结点放在 F 里面，该节点将不再进行后续的处理的是前提，同时权重一定是单调递增的，或者递减。而出现混合值得时候这样的前提就不满足了。

2、 如果地图中存在多条最优路径，也就是说多条路径的权重和都是相等的，那么我刚刚介绍的 Dijkstra 算法应该如何修改呢？

答： F 中的节点最小值变为一个集合。