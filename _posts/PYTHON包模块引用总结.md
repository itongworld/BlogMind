---
title: PYTHON包/模块引用总结
date: 2017-05-09 16:00:00
tags:
- Python
- 基础语法
---

## 同一目录下的引用
如果要引用的包（含有`__init__.py`文件的文件夹）或模块（即`py`文件）和当前文件在同一个目录下，则直接`import`即可。

注意，如果将包作为普通模块导入的话，即`import mypackage`，那么只是导入了这个包下的`__init__.py`模块，其他python模块并没有导入。此时如果调用该包下某个模块的类`mypackage.mymodel.classA`，则会报错`AttributeError`。

所以，在引用时通常是引用到具体的模块或所有的模块，而不是包。另外，如果使用`import mypackage.mymodel`语句导入模块，则在使用时模块时要使用完整的路径，即`obj=mypackage.mymodel.classA()`，如果只使用模块名，即`obj=mymodel.classA()`，则会报错`NameError`。
<!-- more -->

## 不同目录下的引用
如果要引用的包或模块和当前文件不在同一个目录下，则需要告诉Python解释器去哪里寻找需要的包或模块。通常有下面几种方式。

### 1. sys.path.append
在需要引用的文件中添加以下代码：
```PYTHON
import sys
sys.path.append(r'C:\Users\OUYANG\Desktop\te\mmm')

#or
sys.path.append(r'mmm')
```
当前文件在te文件夹下，引用包在mmm文件夹下。绝对路径和相对路径均可，但必须是包的路径，即不能写成`sys.path.append(r'C:\Users\OUYANG\Desktop\te\mmm\mypackage')`或`sys.path.append(r'mmm\mypackage')`，否则会报错`ImportError`。


### 2. XXX.pth文件
在`PythonInstallDirectory\Lib\site-packages`目录下新建`XXX.pth`文件，文件名称可以自定。然后在文件中添加引用包或模块的绝对路径`C:\Users\OUYANG\Desktop\te\mmm\mm`，同样必须是包的路径，否则会报错`ImportError`。


### 3. site-packages目录
将需要引用的包或模块放在`PythonInstallDirectory\Lib\site-packages`目录下即可正常引用。


### 4. PYTHONPATH环境变量
新建系统变量，变量名为`PYTHONPATH`，变量值为引用包或模块的绝对路径，必须是包的路径，否则会报错`ImportError`。

## Import语句
使用`import`语句引用的包或模块名不能含有空格，但是如果不方便更改包或模块名，可以使用python内置`__import__`函数，其实`import`语句就是通过`__import__`内置函数实现的。

例如以下代码：
```PYTHON
m168 = __import__('[168]Excel Sheet Column Title')
print dir(m168)
s168=m168.Solution()
title=s168.convertToTitle(res)
```
虽然某些编辑器可能会有无法解析的错误，但此时引用包或模块确实已经引用了，可以忽略这种错误。