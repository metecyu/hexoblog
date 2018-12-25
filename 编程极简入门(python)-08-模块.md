---
title: 编程极简入门(python)-08-模块
date: 2018-12-25 11:41:01
tags: 教程
id: 2018122504

---
## 简介
本节继续介绍另外一个核心概念--**模快**
学完之后, 你会发现看似非常复杂的功能,其实已经有很多组织或个人帮你封装成模块,就等着你用呢.

<!-- more -->

## 一 .模块的概念
在之前的课程中我们已经学习了编程语言中最核心的概念, 理论上已经可以使用这些概念开发出任何想要的程序. 但实际上,除了掌握编程语法以外,我们还需要掌握相应的业务.否则也很难完成. 譬如想读取一个excel文件就必须先了解excel文件的格式,如果不会又该怎么办呢?好在还有不少精通excel文件格式的程序员, 而且他们已经把excel常用的操作封装成方法.  我们只要直接使用就行.
**模块的概念**: 
特定业务方法的集合, 如上文中提到的excel常用操作就可以看作一个模块.

**使用模块的优点**:  
1 降低了开发的复杂度,不需要了解具体细节就能使用.
2 提高程序质量,尽量使用一些常用的模块,问题会相对少很多.
3 提高开发效率    

## 二 . 使用模块的例子
任务: 计算各个子公司员工的公积金
**任务要求**   
1. 计算一家企业所有员工的公积金.
2. 需要从excel中读取员工信息 

**员工信息**
|员工|工资|子公司|
|:--|:--|:--|
| 刘一| 5000| 北京分公司 |
| 陈二| 6000 |  北京分公司 |
| 张三| 7000 |  北京分公司 |
|李四| 8000 |  北京分公司 |
| 王五| 9000 |  北京分公司 |

**安装第三发库**
安装过程不做详细说明, 在搜索引擎中查找 "python 安装 xlrd" 可以找到很多相关文章.
**代码实现**
```python
# -*- coding:utf-8 -*-
import xlrd
#根据索引获取Excel表格中的数据  
def readExcelData(file,col):
    #data = open_excel(file)
    data = 'unOpen'
    try:
        data = xlrd.open_workbook(file)  
    except Exception,e:
        print str(e)
    table = data.sheets()[0] # 第一个sheet
    nrows = table.nrows #行数
    list=[]
    for rownum in range(nrows):
        list.append(table.cell(rownum,col).value)
        # print  table.cell(rownum,0).value
        # print  table.cell(rownum,1).value
        # print  table.cell(rownum,2).value
    return list
# 计算税率
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
staffNameList =  readExcelData('file.xls',0) 
staffSalaryList = readExcelData('file.xls',1)
cityList = readExcelData('file.xls',2) 

# 元素访问坐标,0为第一个元素.
index = 0 
# 开始循环操作
for oneStaff in staffNameList :
    # 员工姓名,工资
    staffName = staffNameList[index]
    staffSalary = staffSalaryList[index]
    city = cityList[index]
    # 计算公积金
    countGjj(staffName ,staffSalary,city)
    index = index + 1
```

**代码输出**
>员工: 刘一 城市: beijing ,税率: 0.12 ,工资: 5000 ,需要缴纳的公积金: 600.0
员工: 陈二 城市: beijing ,税率: 0.12 ,工资: 6000 ,需要缴纳的公积金: 720.0
员工: 张三 城市: beijing ,税率: 0.12 ,工资: 7000 ,需要缴纳的公积金: 840.0
员工: 李四 城市: beijing ,税率: 0.12 ,工资: 8000 ,需要缴纳的公积金: 960.0
员工: 王五 城市: beijing ,税率: 0.12 ,工资: 9000 ,需要缴纳的公积金: 1080.0