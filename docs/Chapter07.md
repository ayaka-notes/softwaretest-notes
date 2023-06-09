---
sidebar_position: 7
title: 第07章 结构性测试
---
## 第07章 结构性测试

### 一、白盒测试

### 1）测试方法

结构性测试的方法：

- 路径测试
- 数据流测试

结构性测试力求提高测试的覆盖率，主要用于软件验证，是一种确认技术。

### 2）黑盒和白盒比较

- 黑盒测试：从用户观点出发，按规格说明书要求的输入数据与输出数据的对应关系设计测试 用例。因此它是根据程序外部特征进行测试
- 白盒测试：根据程序内部逻辑结构进行测试
- 这两类测试方法是从完全不同的起点出发，并且是两个完全对立的出发点。这两类方法各有侧重，在测试的实践中都是有效和实用的。在进行单元测试时大都采用白盒测试，而在系统测试中采用黑盒测试。

> 有了“黑盒”测试，为什么还要“白盒”测试?

- 黑盒测试是从用户的观点出发，根据程序外部特性进行的测试。如果外部特性本身有问题或规格说明的规定有误，用黑盒测试方法是发现不了的。
- 黑盒测试只能观察软件的外部表现，即使软件的输入输出都是正确的，却并不能说明软件就是正确的 。因为程序有可能用错误的运算方式得出正确的结 果，这种情况只有白盒测试才能发现真正的原因。
- 白盒测试能发现程序里的隐患，像内存泄漏、误差累计问题。在这方面，黑盒测试存在严重的不足。

### 二、路径测试

#### 1）程序图

- 程序图是一种有向图，图中的节点表示语句片段，边表示控制流。
- 如果 i 和 j 是程序图中的节点，从节点 i  到节点 j 存在一条边，当且仅当对应节点 j 的语句片段可以在对应节点 i 的语句片段之后立即执行。
- 程序的图是：有向无循环图，才能是正常的程序

#### 2）DD路径图

##### a）定义

- 程序流图是一种有向图，其中的节点表示语句，边表示控制流。
- 对于给定的程序，可以使用多种不同的程序流图，所有这些程序流图，都可以简化为唯一的DD-路径图

##### b）DD路径

DD-路径是程序图中的一条链，使得

- 情况1：由一个节点组成，入度=0。
- 情况2：由一个节点组成，出度=0
- 情况3：由一个节点组成，入度或出度大于或者等于2
- 情况4：由一个节点组成，入度=1并且出度=1
- 情况5：长度大于或者等于2的最大链(单入单出的最大序列)
- DD-路径是程序图中的最小独立路径，不 能被包括在其它DD-路径之中

DD路径定义:对给定用命令语言编写的一段程序, 其DD路径是有向图，其中节点表示程序图的DD 路径，边表示连续DD路径之间的控制流。

#### 3）测试覆盖指标

- 测试的主要评测方法包括覆盖和质量。测试覆盖是对测试完全程度的评测。测试覆 盖是由测试需求和测试用例的覆盖或已执行 代码的覆盖表示的。
- 指标主要分为下面几类：
- C0：所有语句（语句覆盖）
- C1：所有DD路径（分支覆盖）
- C1p：所有判断的每种分支（条件判断）
- C2（C1覆盖+循环覆盖）
- Cd（C1覆盖+DD路径的所有依赖对偶）
- Cmcc：（多条件覆盖）
- Cik：包含最多K次循环的所有程序路径，通常K=2
- Cstart：路径具有统计重要性的部分
- C无穷：所有可能的执行路径

#### 4）几种覆盖

##### a）语句覆盖C0

- 定义：使得程序中每一可执行语句至少被执行一次。
- 注意：并不是要把所有路径都覆盖，下图中蓝色的部分是语句，语句才是核心！

![截屏2023-03-19 23.33.16](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-03-19%2023.33.16.png)

##### b）分支覆盖C1

- 分支覆盖：使程序中的每个逻辑判断的取真取假分支至少经历一次； (C1)

![截屏2023-03-19 23.32.52](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-03-19%2023.32.52.png)

##### c）条件覆盖C1p

- 注意！条件覆盖就需要研究**判断点的条件逻辑**
- 例如，程序有四个条件A＞1、 B=0、A=2、X＞1
- 为了达到条件覆盖的标准，需要有足够的测试用例，使得在判断点有：
- A＞1、A≤1、B=0、B≠0，A=2、A≠2、X＞1、X≤1的情况！
- 当然，比如一个测试用例可以覆盖到多个条件，那就可以抵掉（总之只要覆盖到了条件就行）

##### d）多条件覆盖Cmcc

- 总之，多条件覆盖要求把条件覆盖的各种情况组合起来！
- 注意！虽然满足条件组 合覆盖，但并不能覆盖程序中 的每一条路径，例如路径acd就没有执行，因此，条件组合 覆盖标准仍然是不彻底！

![截屏2023-03-19 23.37.22](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-03-19%2023.37.22.png)

##### d）分支/条件覆盖

- 定义：执行足够的测试用例 ，使得分支中每个条件取到各种可能的值，并使每个分支取到各种可能的结果

##### e）路径测试C无穷

- 路径测试就是设计足够多 的测试用例，覆盖被测试对象中的所有可能路径。
- 例如上图里面的abd、abe、acd、ace路径全部要覆盖掉！

#### 4）循环测试

##### a）单循环测试

- 假设循环次数为N，测试下面几种情况：
- 直接跳过循环、循环次数为1、2、M(M<N),N-1,N,N+1

##### b）嵌套循环测试

- 先测试最内部循环，其它循环次数为1
- 测试第二层循环，其它循环次数为1
- 直到最外部循环完成测试

##### c）级连循环测试

- 分别采用单循环测试方法进行测试

##### d）不规则循环测试

- 无法测试，这谁设计的拉出去打板子，重开吧

##### e）小结

- 无论哪种测试覆盖，即使其覆盖率达到百分之百， 都不能保证把所有隐藏的程序欠缺都揭露出来。
- 提高结构的测试覆盖率只能增强我们对被测软件的 信心，但它绝不是万无一失的

#### 5）McCabe圈数

##### a）基路径的概念与方法

- 基：向量空间的概念，向量空间的基是相互独 立的一组向量，基“覆盖”整个向量空间。使得 该空间中的任何其它向量都可以用基向量表示。
- 基路径：程序图中相互独立的一组路径，使得该程序中的所有路径都可以用基路径表示
- 圈复杂度：是一种为程序逻辑复杂性提供定量测 度的软件度量，将该度量用于计算程序的基本的基本路径数目。
- 基本路径必须从起始点到终止点的路径。

##### b）McCabe圈数V（G）计算方法

- $V(G)=e-n+2p$
- e：边数；n：节点数；p：连接区域数
- 一般一个软件的圈复杂度不能超过10

#### 6） 基于路径的测试讨论

基于路径的测试，从另一个角度去考虑程序测试的完备性，但是没有考虑数据功能，即使满足DD-路径覆盖，和 考虑圈复杂度指标，也仅是测试的下限指标。如左图：S：已说明行为的路径集合； P：已编程实现的路径集合； T：拓扑可达的路径集合；

![截屏2023-03-20 00.01.06](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-03-20%2000.01.06.png)

### 二、数据流测试

#### 1）概念

数据流测试是一种典型的**白盒测试** ，从关注程序中数据及其使用的角度，来设计测试用例的。类似一种路径测试覆盖，但关心的是数据变量而不是程序结构。

定义-使用（def-use）测试：

- 节点$n \in(p)$是变量 $v \in V$的定义节点，记做$DEF (v，n)$，当且仅当变量v的值有对应节点n的语句片处定义。输入、赋值、循环控制语句、过程调用语句。也就是说向内存地址写入值的语句都是使用语句。
- 节点$n \in(p)$是变量 $v \in V$的使用节点，记做$USE (v，n)$，当且仅当变量v的值在对应节点n的语句片处使用。输出语句、赋值语句、条件语句、循环控制语句和过程调用语句，都是可能的使用语句。但 **使用语句不改变变量的值** 。即：从内存地址读取值的语句。使用可以分为两种：

  - 谓词使用：当且仅当语句n是谓词语句
  - 计算使用：当且仅当语句n不是谓词语句，那就是计算
- 关于变量 $v$ 的定义-使用路径，存在一个起点 $Def(v)$ 和一个 $Use(v)$，使得他们分别是变量定义使用路径的起点和终点。
- 关于变量 $v$ 的定义-清除路径，是具有起始和终止节点DEF（v，m）和USE（v，n）的 PATHS（P）中的路径，**使得该路径中没有其它节点是v的定义节点**(也就是说中间没有其他节点，只能被定义一次)。

#### 2）测试覆盖指标

- 全定义准则：每个定义节点到一个使用的定义清除路径。（就是说测试的时候，要覆盖每一个定义使用的路径）
- 全使用准则：每个定义节点到所有使用节点以及后续节点的定义清除路径，都需要覆盖掉
- 考虑到使用分为谓词和计算，所以又有：
  - 全谓词使用/部分计算使用准则：每个定义节点到所有 谓词使用的定义清除路径，若无谓词使用，至少有一 个计算使用的定义清除路径
  - 全计算使用/部分谓词使用准则：每个定义节点到所有 计算使用的定义清除路径，若无计算使用，至少有一 个谓词使用的定义清除路径。
  - 全定义-使用路径准则：每个定义节点到所有使用节点以及后续节点的定义清除路径。包括有一次环路和或无环路的路径。


#### 3）测试方法步骤

- 首先需要把程序的图画出来。目的就是说我们要在数据流测试的时候要把路径的概念引进去。它每一个节点，就是对应的一个行某一行的语句片段。可以把变量的定义使用分的很精细
- 注意有的节点会被重新定义。所以定义节点可能有很多个，使用节点也可能有很多的
- 有的节点可能即是定义节点、又是使用节点`a=a+1`
- 考试内容：考填表和分析

![截屏2023-05-15 18.12.20](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-05-15%2018.12.20.png)

### 三、程序片测试

#### 1）概述

数据流测试还有一种其他比较这个特殊的一个方法，叫做程序片的测试。程序片子测试的话，它也是一个典型的数据流测试。

- 程序切片的定义：给定一个程序P和P中的一个变量集合 V，变量集合V在语句n上的一个片，记做S（V，n），S（V，n）是P中对V中的变量值作出贡献的、有影响的所有语句（编号）的集合。
- 特别要注意的是：**如果是循环语句，循环的开头、结尾都需要算作有贡献的！也会对循环体里面的变量产生影响**
- USE（使用）的形式有：谓词使用、计算使用、输出使用、定位使用、 迭代使用
- DEF（定义）的形式有： 输入定义、赋值定义
- 参考下面的伪代码：

```
7. lockPrice=45.0
8. stockPrice=30.0
9. barrelPrice=25.0
10. totalLocks=0
11. totalStocks=0
12. totalBarrels=0
13. Input(Locks)
14. While NOT(Locks==-1) 
15. Input(stocks,barrels)
16. totalLocks=totalLocks+Locks
17. totalStocks=totalStocks+stocks
18. totalBarrels=totalBarrels+barrels
19. Input(Locks)
20. ENDWhile
21. Output(“Locks sold:”,totalLocks)
22. Output(“Stocks sold:”,totalStocks)
23. Output(“Barrels sold:”,totalBarrels)
24. lockSales=lockPrice*totalLocks
25. stockSales=stockPrice*totalStocks
26. barrelSales=barrelPrice*totalBarrels
27. Sales=lockSales+stockSales+barrelDSales
28. Output(“Total Sales: ”,Sales)
29. If (sales>1800)
30. Then
31. commission=0.10*1000.0
32. commission=commission+0.15*800.0
33. Commission=commission+0.20*(sales-1800.0)
34. Elseif(sales>1000.0
35. Then 
36. commission=0.10*1000.0
37. commission=commission+0.15*(sales-1000.0)
38. Else 
39. commission=0.10*sales
40. EndIf
41. EndIf
42. Output(“commission is $”,commission)
43. End commission
```

- S1：S（Locks,13）={13}：解释，对于十三行的Lock变量有影响的只有13行的自己
- S2：S（Locks,14）={13,14,19,20}，14为什么是，因为 14行是一个循环体判断！可能影响是否Lock的修改
- S3: S（Locks,16）={13,14,19,20} 16？ 16行只是用了一下Lock，而不是修改了Lock的值，所以不算有影响
- S4：S（Locks,19）={13,14,19,20}，20行如果终止了，那就不会再经过，所以要考虑到20行的。
- S5:S(Stocks,15) ={13,14,15,19,20} ，解释：13、14行决定是否进入循环体，19、20决定是否退出循环体，所以有影响！下面的同理
- S6:S(Stocks,17) ={13,14,15, 19,20}，17？ 
- S7:S(Barrels,15) ={13,14,15,19,20} 
- S8:S(Barrels,18) ={13,14,15, 19,20}，18？

#### 2）意义

> 我们前面讲的那个定义使用路径的时候，只是从路径上，这个节点定义了，在那个节点使用了，但是它对数据之间的依赖的关系的考虑不多，但是程序切片的话，它可以把数据之间的依赖的关系考虑的更加这种准确一些。
>
> - 就说每一个变量我对它做出贡献的话，就是说那些语句都对它的值产生了影响，产生影响了以后，我就去可以去测每一个部分的话，它的这个编写的程序是否正确。
> - 如果所有变量的定义和使用是正确的，当然程序就是正确的！

- 如果 $S(commission，42)-S(sales，28) =\{7-39\} - \{7-27\} ={28 \sim 39}$； 将commission的计算分为sales计算和之后的计算， 为错误的定位提供了依据。如果后面的是对的，前面的commission计算有问题，那就差值之间存在问题

### 四、测试的效率

#### 1）停止测试

> 什么时候停止测试？

- 当时间用完时——缺少标准
- 当继续测试没有产生新失效时
- 当继续测试没有发现新缺陷时
- 当无法考虑新测试用例时—原因
- 当回报很小时—基于分析的方法
- 当达到所要求的覆盖时—结构化测试的指标
- 当所有缺陷都已经清除时—难以实现

#### 2）冗余

- 如下图，拓扑路径可能非常多种，但是很多都是无效的路径，最终可以走的只有11条。
- 那我如果使用边界值测试的时候（4N+1=13个测试，发现只测了7个路径），或者用最坏情况的测试（125个，实在是太多了），那将会测试用例非常多冗余

![截屏2023-05-15 19.35.12](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-05-15%2019.35.12.png)

#### 3）评估指标

- 假设功能性测试技术M生成m个测试用例,并且根据标识被测单元中的s个元素的结构性测试指标S来 跟踪这些测试用例。当执行m个测试用例时,会经过 n个结构性测试单元。
- 定义:方法M关于指标S的覆盖是:n与s的比值,记做 C(M,S)。
- 定义:方法M关于指标S的冗余是m与s的比值，记 做R(M,S)
- 定义:方法M关于指标S的净冗余是m与n的比值， 记做NR(M,S)。

- 如下图所示，m是测试用例的数量，n是实际上经过的比如路径的条数，然后s是标准的没有冗余的路径的数量

![截屏2023-05-15 19.45.45](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-05-15%2019.45.45.png)

- 评估不同测试的情况

![截屏2023-05-15 19.48.49](./Chapter07.assets/%E6%88%AA%E5%B1%8F2023-05-15%2019.48.49.png)

