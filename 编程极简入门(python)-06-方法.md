---
title: 编程极简入门(python)-06-方法
date: 2018-12-25 10:45:01
tags: 教程
id: 2018122502

---
## 前言
本节继续介绍另外一个核心概念--**方法 **
学完之后，你可以将程序中重复的代码打包（封装）成方法，大大减少代码的数量

## 一 .计算公司员工的公积金（包含子公司）
要求  计算一家企业所有员工的公积金.
> 大型企业在北京,天津都有分公司,个人所交的公积金按照所在子公司的所在城市.
> 北京:12% ,天津11%
员工名单(为了简化,我们只选取2位员工)
<!-- more -->

|员工|工资|子公司|
|:--|:--|:--|
| 张三| 10000 | 北京分公司 |
| 李四| 10000 | 天津分公司 |

**代码实现**
如果我们参考<<条件判断>>最后的例子,就能马上把代码写出来. 
```python
# -*- coding:utf-8 -*-
# 计算第1个员工的公积金
staffName = u'张三'
money = 10000 #工资
city = 'beijing' #城市 

taxRate = 0  #税率
tax= 0    #税金

if city =='beijing':
   taxRate = 0.12 
elif city =='tianjing':
   taxRate = 0.11 
else:
    taxRate = 0.07 

tax = money * taxRate 
print u'员工:', staffName ,u'城市:',city,u',税率:',taxRate,u',工资:',money,u',需要缴纳的公积金:',tax 

# 计算第2个员工的公积金
staffName = u'李四'
money = 10000 #工资
city = 'tianjing' #城市 

taxRate = 0  #税率
tax= 0    #税金

if city =='beijing':
   taxRate = 0.12 
elif city =='tianjing':
   taxRate = 0.11 
else:
    taxRate = 0.07 

tax = money * taxRate 
print u'员工:', staffName ,u'城市:',city,u',税率:',taxRate,u',工资:',money,u',需要缴纳的公积金:',tax 
```
**代码问题**
尽管上述代码可以正常运行,但却有一个比较严重的问题,就是只要新增一个员工,就要增加一段非常类似一段代码. 更严重的问题是,如果计算税金的逻辑一旦发生变化, 那么就要修改每个计算税金的地方.

## 二 . 方法的概念
"方法"(也叫"函数")是编程语言中最重要的概念, 和数学中的"函数"概念非常相似 y=f(x) ,给定一个变量值x,返回 f(x).  
便于理解：
从使用者角度来看，可以把“方法”理解为一种“服务”。
**方法的组成部分**
1. 方法参数 (非必要,可多个参数)
2. 方法业务
3. 方法返回结果  (非必要)
```python
 def 方法名（参数1，参数2 ...）：
    方法业务
    return 返回值
```
## 二 .优化后的实例
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


# 变量方式接受参数
staffName = u'张三'
money = 10000 #工资
city = 'beijing' #城市 
countGjj(staffName,money,city)

# 值方式 接受参数
countGjj(u'李四',10000,'tianjing')

# 返回值
tax = countGjj(u'王五',10000,'shanghai')
print u'方法返回值, 税率:' , tax
```
**代码输出**
> 员工: 张三 城市: beijing ,税率: 0.12 ,工资: 10000 ,需要缴纳的公积金: 1200.0
员工: 李四 城市: tianjing ,税率: 0.11 ,工资: 10000 ,需要缴纳的公积金: 1100.0
员工: 王五 城市: shanghai ,税率: 0.07 ,工资: 10000 ,需要缴纳的公积金: 700.0
方法返回值, 税率: 700.0