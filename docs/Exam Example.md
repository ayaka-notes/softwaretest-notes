---
sidebar_position: 64
title: 考试样例题
---

> 以下是考试的样题！供复习使用。

考试复习的要点：
- 大部分题目都是例子，很少有抄PPT的题目
- 白盒测试的：路径、数据流、肯定会有题目的
- 集成测试的基本方式是吧？我们讲过几类，另外比如说有变异测试。
- 回归测试怎么做、系统测试。
- 给你例子，设计测试用例，多看课本
- 题量尽可能减少。


阅读下面的伪代码，完成题目（请以代码前面的行号为准！）：

```
1.	Program SalerReward (INPUT,OUTPUT)
2.		Dim apple, huawei, xiaomi As Integer
3.		Dim day As Integer
4.		Dim applePrice, huaweiPrice, xiaomiPrice As Double
5.	    Dim appleProfit, huaweiProfit, xiaomiProfit As Double
6.		Dim totalApple, totalHuawei, totalXiaomi As Interger
7.		Dim appleSales, huaweiSales, xiaomiSales As Interger
8.		Dim totalSales, totalProfits, profitRate As Double
9.		Dim reward As String

10.		applePrice = 10,000
11.		huaweiPrice = 5,000
12.		xiaomiPrice = 2,000
13.		appleProfit = 3,000 // rate = 30%
14.		huaweiProfit = 1,000 //rate = 20%
15.		xiaomiProfit = 200 // rate = 10%
16.		totalApple = 0
17.		totalHuawei = 0
18.		totalXiaomi = 0
19.		day = 1
20.		While (day <=30)
21.			Input(apple, huawei, xiaomi)
22.			totalApple = totalApple + apple
23.			totalHuawei = totalHuawei + huawei
24.			totalXiaomi = totalXiaomi + xiaomi
25.			day = day + 1
26.		EndWhile
27.		Output("Apple sold: ", totalApple)
28.		Output("Huawei sold: ", totalHuawei)
29.		Output("Xiaomi sold: ", totalXiaomi)
30.		appleSales = applePrice * totalApple
31.		huaweiSales = huaweiPrice * totalHuawei
32.		xiaomiSales = xiaomiPrice * totalXiaomi
33.		totalSales = appleSales + huaweiSales + xiaomiSales
34.		Output("Total sales: ", totalSales)
35.		totalProfits = appleProfit * totalApple +
                         huaweiProfit * totalHuawei +
                     xiaomiProfit * totalXiaomi
36.		profitRate = totalProfits / totalSales // 计算利润率
37.		Output("Total profits: ", totalProfits)
38.		If (totalSales >= 100,000)
39.		Then
40.			If (profitRate >= 0.2) 
41.			Then
42.				reward = "Diamond"
43.			Else If (profitRate < 0.2 && profitRate >= 0.15) 
44.			Then
45.				reward = "Gold"
46.			Else
47.				reward = "Silver"
48.			Endif
49.		Else If (totalSales < 100,000 && totalSales >= 60,000)
50.		Then
51.			If (profitRate >= 0.2)
52.			Then
53.				reward = "Gold"
54.			Else 
55.				reward = "Silver"
56.			Endif
57.		Else If (profitRate >= 0.2)
58.		Then
59.			reward = "Silver"
60.		Else 
61.			reward = "No Reward"
62.		Endif
63.		Output("Reward is: ", reward)
64.	End SalerReward
```


#### 一、定义使用路径部分

1）填写完成定义使用路径的表格

| 变量名   | 定义节点 | 使用节点 |
| ------------ | ------------ | ------------ |
| **apple**    | 21           | 22           |
| **huawei**   | 21           | 23           |
| **xiaomi**   | 21           | 24           |
| appleProfit  |              |              |
| huaweiProfit |              |              |
| xiaomiProfit |              |              |
| day          |              |              |
| applePrice   |              |              |
| huaweiPrice  |              |              |
| xiaomiPrice  |              |              |
| totalApple   |              |              |
| totalHuawei  |              |              |
| totalXiaomi  |              |              |
| appleSales   |              |              |
| huaweiSales  |              |              |
| xiaomiSales  |              |              |
| totalSales   |              |              |
| totalProfits |              |              |
| profitRate   |              |              |
| reward       |              |              |


2）根据程序片测试的方法，请写出以下变量的程序切片

- totalApple
- reward
- profitRate
- huaweiSales

#### 二、DD路径部分

- 画出相关的DD路径图
- 计算基本路径的数量，并写出所有的基本路径