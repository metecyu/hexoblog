---
title: 编程极简入门(python)-07-批量处理
date: 2018-12-25 11:04:01
tags: 教程
id: 2018122503

---
## 简介
本节继续介绍另外一个核心概念--**批量处理**
学完之后, 你可以轻松的让一个方法,或者一段代码执行千遍,万遍.

<!-- more -->
## 一 .计算各个子公司员工的公积金(公司所有员工)

**任务要求**   
计算一家企业所有员工的公积金

|员工|工资|子公司|
|:--|:--|:--|
| 刘一| 5000| 北京分公司 |
| 陈二| 6000 |  北京分公司 |
| 张三| 7000 |  北京分公司 |
|李四| 8000 |  北京分公司 |
| 王五| 9000 |  北京分公司 |


**代码实现**
```python
# -*- coding:utf-8 -*-

def countGjj(staffName,money,city):
  taxRate = 0  
  if city =='beijing':
    taxRate = 0.12 
  elif city =='tianjing':
    taxRate = 0.11 
  else:
    taxRate = 0.07
  tax = money * taxRate
  print u'员工:', staffName ,u'城市:',city,u',税率:',taxRate,u',工资:',money,u',需要缴纳的公积金:',tax 
  return tax

# 值方式 接受参数
countGjj(u'刘一',10000,'beijing')
countGjj(u'陈二',10000,'beijing')
countGjj(u'张三',10000,'beijing')
countGjj(u'李四',10000,'beijing')
countGjj(u'王五',10000,'beijing')

```
**代码问题**
每增加一个员工,都要添加一行代码 当公司有5千名员工时, 代码将会有5千行, 这样显然比较低效. 所以编程语言提供了批量处理(循环)的机制,解决这样的问题. 

## 二 . 批量处理的概念
批量处理 -- 重复执行指定区域内代码的机制.
所以当需要计算机帮我们多次处理的相同的任务, 我们就可以使用批量处理(循环). 譬如:计算每个员工的应缴公积金, 计算当天每个门店的营业收入等等.
**语法 - 循环次数**
在屏幕上打印10次
```python
# -*- coding:utf-8 -*-
# 在屏幕打印10次
for num in range(10):
  str = 'hello world'
  print  str, u'打印', num+1 ,u'次'
```
> num从0开始编号

**语法 - 循环集合元素**
在屏幕上打印集合中的每个元素.
这里有一个新的概念--"集合", 可以理解为存放多个值的变量. 变量值也可以是数值型,字符型.
```python
# -*- coding:utf-8 -*-
numbers = [1,2,3,4,5,6,7,8,9,10]
for num in numbers:
  str = 'hello world'
  print  str, u'打印元素',num
```

## 二 .实例 - 优化
**代码实现**
如果我们参考<<条件判断>>最后的例子,就能马上把代码写出来. 
```python
# -*- coding:utf-8 -*-
# 定义计算公积金方法 ，接收三个参数 员工姓名，工资，城市
def countGjj(staffName,money,city):
  taxRate = 0  
  if city =='beijing':
    taxRate = 0.12 
  elif city =='tianjing':
    taxRate = 0.11 
  else:
    taxRate = 0.07
  tax = money * taxRate
  print u'员工:', staffName ,u'城市:',city,u',税率:',taxRate,u',工资:',money,u',需要缴纳的公积金:',tax 
  return tax

# 定义员工姓名,员工工资 集合
staffNameList = [u'刘一', u'陈二',u'张三',u'李四',u'王五']
staffSalaryList = [5000,6000,7000,8000,9000,10000]
# 元素访问坐标,0为第一个元素.
index = 0 

# 开始循环操作
for oneStaff in staffNameList :
  # 员工姓名,工资
  staffName = staffNameList[index]
  staffSalary = staffSalaryList[index]
  # 计算公积金
  countGjj(staffName ,staffSalary,'beijing')
  index = index + 1
```

**代码输出**
>员工: 刘一 城市: beijing ,税率: 0.12 ,工资: 5000 ,需要缴纳的公积金: 600.0
员工: 陈二 城市: beijing ,税率: 0.12 ,工资: 6000 ,需要缴纳的公积金: 720.0
员工: 张三 城市: beijing ,税率: 0.12 ,工资: 7000 ,需要缴纳的公积金: 840.0
员工: 李四 城市: beijing ,税率: 0.12 ,工资: 8000 ,需要缴纳的公积金: 960.0
员工: 王五 城市: beijing ,税率: 0.12 ,工资: 9000 ,需要缴纳的公积金: 1080.0