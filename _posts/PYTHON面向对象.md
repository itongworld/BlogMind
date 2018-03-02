---
title: PYTHON面向对象
date: 2018-01-03 16:00:00
tags:
- PYTHON
- 基础语法
---

## 类的创建
### 新式类与旧式类
所谓的新式类和旧式类之间是有区别的。在Python 3.0中，旧式类的问题不用再担心，因为它们根本就不存在了。在Python 3.0中创建一个旧式类的语法为：
```
class ClassName:
    pass
```

若使用新式类语法，则需要在模块或者脚本开始的地方添加赋值语句`__metaclass__ = type`，或者显式继承新式类，比如`object`等。
```
__metaclass__ = type

class ClassName:
    pass 

# or
class ClassName(object):
    pass
```
如果使用`__metaclass__ = type`或从object继承的方式来定义新式类，那么可以使用`type(s)`查看实例对象所属的类。
<!-- more -->



## 属性、方法和函数
### self
self参数是对于对象自身的引用，绑定方法将其第一个参数，即self参数绑定到所属的实例上而无需显式提供该参数。需要注意的是，self参数并不依赖于调用方法的方式，既可以使用`instance.method()`方式，也可以随意使用其他变量引用同一个方法，此时该变量引用绑定方法`instance.method`，也就意味着这还是会对self参数进行访问，self参数仍旧绑定到类的相同实例上。
```
>>> class A(object):
...     def say(self):
...         print self.name
...
>>> a = A()
>>> a.name = 'Python'
>>> a.say()
Python
>>> b = a.name
>>> b()
Python
```

### 实例属性与类属性
由于Python是动态语言，因而可以动态地添加和修改实例属性和类属性。

对于每个实例对象，允许其拥有各自不同、相互独立的实例属性。而类属性是直接绑定在类上的，因而所有实例对象共享其类的属性。
```
>>> class Student(object):
...     gender = 'Male'
...     def __init__(self, name):
...         self.name = name
...
>>> Student.gender
'Male'
>>> 
>>> s1 = Student("Bob")
>>> s1.gender
'Male'
>>> s2 = Student("Mary")
>>> s2.gender
'Male'
>>> 
>>> Student.gender = 'Female'
>>> s2.gender
'Female'
```

访问类属性可以通过调用类或调用实例对象来实现，但修改类属性只能通过调用类来实现。否则只是在实例对象上绑定了一个同名的实例属性。
```
>>>s1.gender = 'Male'
s1.gender, s2.gender, Student.gender
('Male', 'Female', 'Female')
```
实例对象范围内新绑定的同名实例属性会屏蔽类范围内原有的同名类属性。这与Python函数局部变量与全局变量的行为类似。

### 实例方法与类方法
事实上，在class中定义的实例方法也是类的一个属性，是一个绑定到实例的函数。因此可以动态地把函数绑定到实例上，Python中使用`types.MethodType()`把一个函数转换为绑定到某个实例的方法。
```
>>> class Student(object):
...     def __init__(self, name, score):
...         self.name = name
...         self.score = score
>>> def studentInfo(self):
...     print self.name + str(self.score)
>>> s = Student("OUYANGTONG", 99.5)
>>> studentInfo(s)
OUYANGTONG99.5
>>> 
>>> import types
>>> s.getInfo = types.MethodType(studentInfo, s, Student)
>>> s.getInfo()
OUYANGTONG99.5
>>> s.getInfo
<bound method Student.studentInfo of <__main__.Student object at 0x00000000053F4828>>
```

如果只是将函数赋值给实例的某个属性，则并不能将函数转换为方法，仍需要显式提供self参数。
```
>>> s.getInfo = studentInfo
>>> s.getInfo
<function studentInfo at 0x00000000053FE198>
>>> s.getInfo()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: studentInfo() takes exactly 1 argument (0 given)
```

类方法与类属性相似，都是绑定在某个类上，而非类的实例对象上。
```
>>> class Student(object):
...     gender = 'Male'
...     __studentnumber = 0
...     @classmethod
...     def howmany(cls):
...         return cls.__studentnumber
...     def __init__(self, name):
...         self.name = name
...         Student.__studentnumber = Student.__studentnumber + 1
...
>>> Student.__studentnumber
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: type object 'Student' has no attribute '__studentnumber'
>>> Student.howmany()
0
>>> s1 = Student("Bob")
>>> Student.howmany()
1
>>> s2 = Student("Mary")
>>> Student.howmany()
2
```
通过`@classmethod`装饰器创建类方法，类方法的第一个参数绑定到类本身上而无需显式提供该参数。Python中类方法与静态方法的区别请参看[meaning-of-classmethod-and-staticmethod-for-beginner](https://stackoverflow.com/questions/12179271/meaning-of-classmethod-and-staticmethod-for-beginner)。



## 类的私有化
Python并不直接支持类的私有化，类的属性（实例属性或类属性）或方法都可以在外部进行访问。但是，可以用一些小技巧达到私有化的效果。为了将属性（实例属性或类属性）或方法变为类私有的，而在外部无法访问，只要在它的名字前面加上双下划线即可。而如果名字前后均有双下划线，则其作为Python类中的特殊属性（实例属性或类属性）或特殊方法，则可以在外部进行访问。
```
>>> class Secretive(object):
...     def __inaccessible(self):
...         print "Bet you can't see me..."
...     def accessible(self):
...         print "The secret message is:"
...         self.__inaccessible()
...
>>> s = Secretive()
>>> s.__inaccessible()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Secretive' object has no attribute '__inaccessible'
>>> 
>>> s.accessible()
The secret message is:
Bet you can't see me...
```

然而，Python并没有真正的私有化支持。在类的内部定义中，所有以双下划线开始的名字都被“翻译”成前面加上单下划线和类名的形式。
```
>>> Secretive._Secretive__inaccessible
<unbound method Secretive.__inaccessible>
>>> s._Secretive__inaccessible()
Bet you can't see me...
```

如果不需要使用这种方法但是又不想让其他对象访问内部数据，那么可以使用单下划线。这只是一个约定俗成的习惯，但的确有实际效果。例如，前面有单下划线的名字都不会被带星号的import语句（`from module import *`）导入。



## 类的命名空间
定义类时，所有位于class语句中的代码都在特殊的命名空间中执行——类命名空间。这个命名空间可由类内所有成员访问。类的定义其实就是执行代码块，因此在类的定义区并不限定只能使用def语句。
```
>>> class A(object):
...     print "Class A being defined..."
...
Class A being defined...
```



## 类的继承
Python语言支持多重继承。当使用多重继承时，应当注意各个超类的继承顺序。如果一个相同名字的方法从多个超类继承，则先继承的类中的方法会重写后继承的类中的方法，使后继承的类中的同名方法不可访问。实例属性和类属性的多重访问顺序类同。 子类的同名属性或方法会重写超类的同名属性或方法。

如果超类们共享一个超类，那么在查找给定方法或者属性时访问超类的顺序称为MRO（Method Resolution Order）

Python不支持重载。
```
class Calculator(object):
    shortname = "C"
    def __init__(self):
        self.name = "Calculator"
        self.value = None
    def calculate(self, expression):
        self.value = eval(expression)
    def talk(self):
        print "I can't talk..."

class Talker(object):
    shortname = "T"
    def __init__(self):
        self.name = "Talker"
        self.value = None
    def calculate(self, expression):
        print "I can't calculate..."
    def talk(self):
        print "Hi, my value is", self.value

class TalkingCalculator(Calculator, Talker):
    pass

tc = TalkingCalculator()
tc.talk() #I can't talk...
print tc.name #Calculator
print tc.shortname #C
```