# Higher-Order-Approximation-Explosion

Higher Oder Approximation of DSGE

全文约2800字,预计需12分钟阅读全文

为什么要做高阶近似？（1）福利分析；（2）更精确；（3）状态依赖效应；（4）不确定性冲击。经验数据显示较大规模的冲击时，高阶近似可能会“爆炸(explosion)”。通常，我们会：（1）减少冲击规模；（2）采用pruning；还有一种方式（3）非线性移动平均（NLMA）。今天，我们就给大家介绍一下这些方法及code的用法。

正文

金融危机后，人们越来越认识到宏观经济的非线性效应。DSGE模型也不像过去一样用一阶近似，而更多的使用高阶近似。

Dynare中现在也可以使用高阶近似（基于2阶和3阶近似）。高阶近似有许多好处：

（1）对于福利分析来说，用高阶近似更加恰当，参见【免费下载】Dynare v4.5 - User Guide for Advanced Topics中的福利分析章节；
（2）高阶近似更加精确；

（3）高阶近似允许我们来研究状态依存效应，即脉冲响应依赖于冲击发生时的初始状态；

（4）如果我们想要研究不确定性冲击（即外生冲击方差的冲击，二阶矩冲击），就必须用到3阶近似。
 
但是，我们在做高阶近似的时候，可能会出现高阶状态空间表达式的系数“爆炸”（explosion）的情况。那么，这个时候，我们怎么计算脉冲响应，并得到模拟结果呢？

今天就为大家提供几种解决方案。


一、模型

本文的基准模型来自E. Sims（2017）：“Using Dynare”。

\sigma