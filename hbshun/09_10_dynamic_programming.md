# 动态规划

>终于到动态规划了，白天过了一遍，发现看不太懂😔，2014年10月左右的时候，前东家多益的笔试题就遇到背包问题，后来查了查是需要用动态规划来解决，然后就没有然后了。一晃5年多过去了，岁月如梭，这次再搞不懂，按律当斩。但是看起来还是有点难度的。加油！

我们并不用处理所有可能的情况，只要找到满足条件的最优解就行了。在这种情况下，我们需要在各种可能的局部解中找到那些可能达到最优的局部解，而放弃其他的局部解。这个寻找最优解的过程其实就是动态规划。

需要通过子问题的最优解，推导出最终问题的最优解，因此特别注重子问题之间的转移关系。

子问题之间的转移成为“**状态转移**”，用户刻画这些状态转移的表达式成为**状态转移方程**。

找到合适的状态转移方程，是动态规划的关键。

## 编辑距离

![](./assets/09_1.jpg)

**查询推荐** 搜索下拉提示和关键词纠错。对于用户的输入，查找相似的关键词并返回。

从一个字符串到另一个字符串所需的最少的编辑次数叫做 **编辑距离**。

编辑操作分为三种：
* 替换一个字符
* 插入一个字符
* 删除一个字符

状态转移，mouuse mouse看起来很简单，但实际情况中是非常复杂的，各种长度的字符串。


我们并不需要排列的所有可能性，而只是关心最优解

* 最简单的情况，A和B都是空字符，编辑距离是0。
* A增加一个字符，编辑距离增加1.  B增加一个字符，编辑距离增加1.
* A和B都增加一个字符，不相等就替换+1，相等则不变
* 

