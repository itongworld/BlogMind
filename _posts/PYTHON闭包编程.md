---
title: PYTHON闭包编程
date: 2016-06-05 19:50:00
tags: 
- Python
- 基础语法
---


## 返回函数
Python中的函数不但可以返回`int`、`str`、`list`、`dict`等数据类型，还可以返回函数。

例如，定义一个返回函数`g`的函数`f`，代码如下：
```PYTHON
def f():
	print 'call f()...'
	#define g
	def g():
		print 'call g()...'
	#return g
	return g
```
仔细观察上面的函数定义，我们在函数内部又定义了一个函数`g`。由于函数也是一个对象，函数名就是指向函数的变量，所以最外层函数可以返回这个变量`g`，也就是内层函数本身。
<!-- more -->

调用函数`f`，则会得到`f`返回的那个函数：
```PYTHON
>>> x=f()
call f()...
>>> x
<function f at 0x0000000002CC2048>
>>> x()
call g()...
```
请注意区分返回函数和返回值：
```PYTHON
def myabs():
	return abs

def myabs2(x):
	return abs(x)
```

返回函数可以将一些计算延迟执行。例如，定义一个普通的求和函数：
```PYTHON
def calc_sum(lst):
	return sum(lst)
```
调用`calc_sum()`函数时，将立刻计算并得到结果：
```PYTHON
>>> calc_sum([1, 2, 3, 4])
10
```
但是，如果返回一个函数，就可以延迟计算：
```PYTHON
def calc_sum(lst):
	def lazy_sum():
		return sum(lst)
	return lazy_sum
```
调用`calc_sum()`函数并没有计算出结果，对返回的函数进行调用时才得到结果：
```PYTHON
>>> f=calc_sum([1, 2, 3, 4])
>>> f
<function g at 0x0000000002CC20B8>
>>> f()
10
```
此时由于可以返回函数，我们在后续的代码里就可以决定何时调用该函数。

### 示例1
请编写一个函数`calc_prod(lst)`，参数为`list`，返回值为计算参数元素乘积的函数。
```PYTHON
def calc_prod(lst):
	def lazy_prod():
		def f(x, y):
			return x * y
		return reduce(f, lst, 1)
	return lazy_load
```
测试：
```PYTHON
>>> f=calc_prod([1, 2, 3, 4])
>>> print f()
24
```

## 闭包
在函数内部定义的函数和外部定义的函数是一样的，只是它们无法被外部访问。例如：
```PYTHON
def g():
	print 'g()...'

def f():
	print 'f()...'
	return g
```
而将`g`的定义移入函数f内部，可以防止其他代码调用`g`：
```PYTHON
def f():
	print 'f()...'
	def g():
		print 'g()...'
	return g
```
但是，考察上一节定义的`calc_sum()`函数，发现无法把`lazy_sum`移动到`calc_sum`外部，因为它引用了`calc_sum`函数的参数。


像这种，内层函数引用外层函数（定义内层函数的环境中的）局部变量，然后返回内层函数的情况，称为闭包（Closure）。
闭包的特点是，返回函数引用了外层函数的局部变量。** 所以，要正确使用闭包，需要确保引用的局部变量在返回函数后不能改变。**例如，希望一次返回三个函数分别计算`1*1`，`2*2`，`3*3`：
```PYTHON
def count():
	fs=[]
	for i in range(1, 4):
		def f():
			return i*i
		fs.append(f)
	return fs
```
然而调用结果：
```PYTHON
>>> f1, f2, f3=count()
>>>f1()
9
>>>f2()
9
>>>f3()
9
```
原因就是当`count()`函数返回了三个函数时，这三个函数所引用的变量`i`的值已经变成了`3`。由于`f1`，`f2`，`f3`并没有被调用，所以此时它们并未计算`i*i`，当各个函数被调用时`i`值为`3`，所以函数都会返回`9`。
因此，返回函数不要引用任何循环变量，或者后续会发生变化的任何变量。

### 示例2
改写`count()`函数，使其返回能正确计算`1*1`，`2*2`，`3*3`的函数。

考察下面的函数：
```PYTHON
def f(j):
	def g():
		return j*j
	return g
```
它可以正确地返回一个函数`g`，`g`所引用的变量`j`不是循环变量，因此将正常执行。在`count()`函数循环内部，如果借助`f`函数，就可以避免引用循环变量`i`。
```PYTHON
def count():
	fs=[]
	for i in range(1, 4):
		def f(j):
			def g():
				return j*j
			return g
		r=f(i)
		fs.append(r)
	return fs
```
调用返回函数：
```PYTHON
>>> f1, f2, f3=count()
>>> print f1(), f2(), f3
1, 4, 9
```




