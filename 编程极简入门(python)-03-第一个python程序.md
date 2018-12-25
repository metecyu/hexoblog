---
title: 编程极简入门(python)-03-第一个python程序
date: 2018-12-13 16:36:01
tags: 教程
id: 2018121302

---
## 简介
在上一节中我们介绍了如何安装python环境，本文将演示如何编写，运行python程序。随后还会介绍python是如何进行基础的数学运算。
学完之后,你将学会用程序进行简单的数学运算，等于拥有了一个python牌的计算器。

<!-- more -->

##一 编写一个python程序**新建一个python程序文件**
先找一个目录作为程序工作目录,本机为**C:\learnPython\learnBase**为了测试,我们先写一个简单的程序 learnBaseRun.py, 目的是在屏幕上输出一行文字.

*learnBaseRun.py文件内容*
```python 
print ' hello i am python '

```
> 可以使用window自带的记事本进行编辑，但更推荐使用支持python语法的文本编辑器如sublime

**运行程序的步骤**
**1** 进入window控制台
同时按下" win + R " 后输入 cmd 

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4296400-49d189e35083c095.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4296400-8a2a84d893c81a3b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**2** 进入python程序所在的目录
cd C:\learnPython\learnBase

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4296400-4b5aac359d7c42ba.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**3** 运行程序
输入"文件名" learnBaseRun.py

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4296400-01e9404c6f1d72a9.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

如看到以上输出则说明程序正常运行.

## 二 数学基础运算(四则运算)
数学运算中的 **加**,**减**,**乘**,**除**在python语言中分别用**+** , **-** , **\*** , **/**  表示

|数学计算|python计算|备注|
|:--|:--:|:--|
|1 加 2|1 + 2| |
|1 减 2|1 - 2| |
|1 乘 2|1 * 2| |
|1 除 2|1.0 / 2.0|当计算结果带有小数点时,就需要在用".0"的形式,以后会作说明|
|1加5后再除2|(1 + 5) / 2|可以加括号来设置运算的优先级 |

**显示运算结果**
我们测试一下上述公式的运算结果
*文件:learnBaseMath.py*
```python

# -*- coding:utf-8 -*- 

print  1 + 2 
print  1 - 2
print  1 * 2
print  1.0 / 2.0
print  (1 + 5) / 2
```

![Paste_Image.png](http://upload-images.jianshu.io/upload_images/4296400-ab225262f6adc999.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


将learnBaseMath.py的输出内容写的更清晰一点,把计算公式也一起输出
*文件:learnBaseMath.py*
```python

# -*- coding:utf-8 -*-

print '1 + 2 = ', 1 +2 
print '1 - 2 = ', 1 - 2
print '1 * 2 = ', 1 * 2
print '1 / 2 = ', 1.0 / 2.0
print '(1 + 5) / 2 = ', (1 + 5) / 2
```

![QQ图片20180528212840.png](https://upload-images.jianshu.io/upload_images/4296400-e562f7186d120871.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

> 说明: print '内容'  代表输出一段字符 ,多个输出之间用' , '隔开.