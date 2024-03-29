## 线性/整数/非线性规划

### 1.应用场景

用于求解决策最优化问题

### 2.模型的数学描述

**线性规划**的标准形式：（包含线性目标函数和线性限制）
$$
\min c^Tx
$$

$$
\left\{
    \begin{array}{c}
        Ax \leq B\\
        Aeq \cdot x = beq\\
		lb \leq x \leq ub
    \end{array}
\right.
$$

**整数规划**部分或全部  $x_i$ 要求为整数

**非线性规划**目标函数和/或限制条件为非线性

### 3.模型求解

(1)	Matlab 规划优化工具箱 `optimtool`

(2)	启发式算法



## 动态规划

### 1.应用场景

用于求解决策过程的最优化问题，要求问题符合 *最优子结构、无后效性、子问题重叠* 三个特征

### 2.模型的数学描述

具体问题具体分析



## 图与网络

### 1.应用场景

图与网络规划的优化问题

### 2.经典问题和对应算法

#### 最短路径

单源最短路：Dijkstra 算法

每对顶点之间的最短路：Floyd 算法

#### 最小生成树

Prim 算法与 Kruscal 算法

#### 匹配问题

二分图匹配：[匈牙利算法](https://www.renfei.org/blog/bipartite-matching.html)

带权二分图匹配：[Kuhn-Munkres 算法](https://blog.sengxian.com/algorithms/km)

#### Euler 回路

Euler 图就是从一顶点出发每边恰通过一次能回到出发点的那种图，即不重复地行遍所有的边再回到出发点。

Fleury 算法(p96)

#### 中国邮递员问题

在一个赋权连通图上求一个含所有边的回路，且使此回路的权最小。

单邮递员：[算法和C++代码实现](https://cfonheart.github.io/2018/04/19/%E4%B8%AD%E5%9B%BD%E9%82%AE%E9%80%92%E5%91%98%E9%97%AE%E9%A2%98/)

#### 旅行商

[动态规划 状态转移算法](https://www.cnblogs.com/youmuchen/p/6879579.html)

#### 最大流

Ford-Fulkerson 算法：[Java 代码实现](https://www.imooc.com/article/28306)

最小费用最大流问题：迭代法

#### 统筹问题

求 最早开工时间/最晚开工时间/最短完工时间/关键路径

求 计划网络优化



## 排队论

### 1.应用场景

由于顾客不能立即得到服务，出现排队现象，研究内容有三部分：

(1)	各种排队系统的概率规律性，主要是研究队长分布、等待时间分布和忙期分布等；

(2)	最优化问题，包括最优设计（静态最优）和最优运营（动态最优）；

(3)	排队系统的统计推断，判断一个给定的排队系统符合哪种模型，并对其做进一步分析。

### 2.模型的数学描述

$$
X/Y/Z/A/B/C
$$

$X$ - 顾客到达间隔时间的分布，如指数分布

$Y$ - 服务时间的分布

$Z$ - 服务台数目

$A$ - 系统容量限制

$B$ - 顾客源数目

$C$ - 服务规则，如先到先服务 FCFS



## 对策论

### 1.应用场景

参与者为利益相互冲突的各方，其结局不取决于其中任意一份的努力而是各方所采取的策略的综合结果

### 2.模型的数学描述

局中人的集合 $I = \{1,2,\dots,n\}$

对于每个局中人 $i$，$i\in I$ 都有一个自己的策略集 $S_i$ 

在一局对策中，各局中人选定的策略形成的策略组 $s = (s_1,s_2,\dots,s_n)$ 称为一个局势，全体局势的集合 $S$ 可用各局中人策略集的笛卡儿积表示，即 $S = S_1\times S_2\times \dots \times S_n$

当局势出现后，对策的结果也随之确定。对于任一局势 $s\in S$ ,有一个向量赢得函数 $H(s) = (H_1(s),\dots ,H_n(s))$, $H_i(s)$ 表示局中人 $i$ 在局势 $s$ 中的赢得函数值

对于局中人 $i$ 的最优策略 $s_i^*$  *“最坏情况下最大获得”* ,获得值为 $H_i^*$：
$$
H_i^*(s_i^*) = \max \limits_{s_i} \min \limits_{s_j,j=1,\dots,i+1，\dots,n}H(s_1,\dots,s_i,\dots,s_n)
$$
若有 $s^*=(s_1^*,\dots,s_n^*)$ ，称 $s^*$ 为稳定点

若不存在稳定点，则需要引入 *混合策略*  (任意混合对策问题必存在稳定点) ，对于每个局中人 $i$ ，以 $x_i$ 的概率选用策略 $\alpha_i$，混合策略集 $S_i^*=\{(x_1,\dots,x_m)^T|x_i\geq 0,i = 1,\dots,m;\sum \limits_{i=1}^m x_i = 1\}$



## 层次分析法

### 1.应用场景

层次分析法是对一些较为复杂、较为模糊的问题作出决策的简易方法，特别适用于那些 *难于完全定量分析* 的问题

### 2.基本原理与步骤

(1)	建立递阶层次结构模型

目标层 + 准则层 + 措施层

(2)	构造出各层次中的所有**判断矩阵**

假设要比较 $n$ 个因子 $X= \{ x_1, \dots , x_n \}$ 对某因素 $Z$ 的影响大小

每次取两个因子 $x_i$ 和 $x_j$ ，以 $a_{ij}$ 表示两因子对 $Z$ 的影响大小之比， $A=(a_{ij})_{n\times n}$ 即对比判断矩阵，且有 $a_{ji}=\frac{1}{a_{ij}} $

(3)	**层次单排序**及**一致性检验**

判断矩阵 $A$ 对应于最大特征值 $\lambda_{max}$ 的特征向量 $W$ ，经归一化后即为该层次因素对上一层次某因素的 **相对重要性排序权值**

一致性指标 $CI$
$$
CI = \frac{\lambda_{max}-n}{n-1}
$$
查表得相应的平均随机一致性指标 $RI$

一致性比例 $CR$
$$
CR=\frac{CI}{RI}
$$
若 $CR < 0.1$ ，表明判断矩阵 $A$ 的一致性可接受

(4)	层次总排序及一致性检验。

| 层B\层A 层A的重要性权重 | $A_1$ $a_1$ | $\dots$   | $A_m$ $a_m$ | B层总排序权值                      |
| :---------------------: | ----------- | --------- | ----------- | ---------------------------------- |
|          $B_1$          | $b_{11}$    | $\dots$   | $b_{1m}$    | $\sum \limits_{j=1}^{m} b_{1j}a_j$ |
|        $ \dots $        | $ \dots $   | $ \dots $ | $ \dots $   | $ \dots $                          |
|          $B_n$          | $b_{n1}$    | $ \dots $ | $b_{nm}$    | $\sum \limits_{j=1}^{m} b_{nj}a_j$ |

B层的总排序随机一致性比例（$CI(j)$、$RI(j)$ 已在层次单排序时求得）
$$
CR=\frac{\sum \limits_{j=1}^m CI(j)a_j}{\sum \limits_{j=1}^m RI(j)a_j}
$$
若 $CR < 0.1$ ，表明层次总排序的一致性可接受



## 插值与拟合

### 1.应用场景

**插值** 求过已知有限数据点的近似函数

**拟合** 已知有限个数据点，求近似函数，不要求过已知数据点，只要求在某种意义下它在这些点上的总偏差最小

插值与拟合都是要求 *根据一组数据构造一个函数作为近似*

### 2.方法

基本的、常用的插值：拉格朗日多项式插值、牛顿插值、分段线性插值、Hermite 插值和三次样条插值

常用的拟合：最小二乘法、多项式拟合

Matlab 拟合工具箱 `cftool`

> [回归、插值、逼近、拟合总结](https://blog.csdn.net/daaikuaichuan/article/details/73870209)



## 数据的统计描述和分析

### 1.统计描述

(1)	频数表与直方图

(2)	统计值

表示位置的统计量 - 均值、中值

表示变异程度的统计量 - 方差、标准差、极差

表示分布形状的统计量 - 偏度、峰度

(3)	概率分布

分布函数、密度函数、分位数

### 2.统计分析

(1)	参数估计，即利用样本对总体进行统计推断

点估计和区间估计

Matlab 统计工具箱提供一些具有特定分布总体的区间估计命令，如对于正态总体 `normfit`

(2)	假设检验，即根据样本对所提出的假设作出判断：是接受还是拒绝

$\sigma^2$ 已知，关于 $\mu$ 的检验（$Z$ 检验） `ztest`

$\sigma^2$ 未知，关于 $\mu$ 的检验（$t$ 检验） `ttest`

分布拟合检验，即在不能预知总体服从什么分布时，根据样本来检验关于分布的假设 ->  $\chi^2$ 检验 

专用与检验分布是否为正态 -> 偏锋、峰度检验法