---
title: ELEMENTS
date: 2017-08-29 17:00:00
tags:
- MARKDOWN
- 测试
cover_index: /assets/elements/coverindex.jpg
cover_detail: /assets/elements/coverdetail.jpg
photos:
- /assets/elements/1.jpg
- /assets/elements/2.jpg
- /assets/elements/3.jpg
- /assets/elements/4.jpg
- /assets/elements/5.jpg
- /assets/elements/6.jpg
- /assets/elements/7.jpg
- /assets/elements/8.jpg
- /assets/elements/9.jpg
---

Markdown element test file。       Markdown元素测试文件。



[原生Markdown](https://daringfireball.net/projects/markdown/)允许段落内换行，只需在换行处添加两个或两个以上的空格然后回车即可（单个回车在原生Markdown中被视为一个空格处理，两个及两个以上回车被视为另起段落。多个空格被视为一个空格）。空行为段落的结束，多个空行被视为一个空行。
各个衍生（如[GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/)）Markdown中，段落内换行只需回车即可，不再需要添加空格。多个空格视为一个空格，多个空行视为一个空行，空行为段落的结束。



如果将more注释放在文档开头，则摘要显示为全文（因为文档开头的注释会被忽略）。若有多个more注释，则只有第一个生效。
<!-- more -->



![Want me?-3gg](/assets/elements/10.jpg)![Want me?-3gg](/assets/elements/11.jpg)![Want me?-3gg](/assets/elements/12.jpg)
![Want me?-3gg](/assets/elements/13.jpg)![Want me?-3gg](/assets/elements/14.jpg)![Want me?-3gg](/assets/elements/15.jpg)
![Want me?-3gg](/assets/elements/16.jpg)![Want me?-3gg](/assets/elements/17.jpg)![Want me?-3gg](/assets/elements/18.jpg)

<!-- 如果将more注释放在文档开头，则摘要显示为全文（因为文档开头的注释会被忽略）。若有多个more注释，则只有第一个生效。 -->
<!-- more -->



# *标题*

# Heading 1

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

###### Heading 6

---



# *引用*

> 这是一级引用
> > 这是二级引用

> Every interaction is both precious and an opportunity to delight.

{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}

---



# *代码*

## 代码块

``` PYTHON
# -*- coding:utf-8 -*-
class Solution:
    def Fibonacci_n(self, n):
        #Time Complexity:  O(n)
        #Space Complexity: O(1)
        
        first=1
        second=1
        if n<=0: return 0
        
        while n>2:
            third=first+second
            first=second
            second=third
            n-=1
        return second
    
    def Fibonacci(self, n):
        #Time Complexity:  O(logn)
        #Space Complexity: O(1)
        q=[[1,1],[1,0]]
        
        if n==0: return 0
        res=self.mypower(q,n-1)
        return res[0][0]
    
    def mypower(self, a, n):
        ret=[[1,0],[0,1]]
        while n>0:
            if (n&1)==1:
                ret=self.mymultiply(ret, a)
            n>>=1
            a=self.mymultiply(a, a)
        return ret
    
    #Matrix Multiplication
    def mymultiply(self, a, b):
        c=[[0 for _ in xrange(2)] for _ in xrange(2)]
        
        for i in xrange(2):
            for j in xrange(2):
                c[i][j]=(a[i][0]*b[0][j]+a[i][1]*b[1][j])
        return c

```

## 代码行

进入库文件的`setup.py`目录下，执行`python setup.py install`代码即可安装库文件。

---



# *图片和链接*

在post页面中，图片总共有三种显示格式，分别是单行显示、两张一行显示和三张一行显示，分别对应图片属性`alt`的`-1gg`、`-2gg`、`-3gg`后缀设置，系统会在相应图片标签中添加`gg1`、`gg2`、`gg3`类样式，相应图片的高度为其宽度的自动、一倍、两倍。图片的默认显示格式是单行显示。

不用担心这样会影响图片标题，系统会自动过滤掉这些后缀设置。

![Want me?](/assets/elements/19.jpg)
![Want me?-2gg](/assets/elements/20.jpg)![Want me?-2gg](/assets/elements/21.jpg)
![Want me?-3gg](/assets/elements/22.jpg)![Want me?-3gg](/assets/elements/23.jpg)![Want me?-3gg](/assets/elements/24.jpg)

[北京理工大学][BIT]

***



# *列表*

## 有序列表

1. first
2. second
3. third

## 无序列表

* one thing
  * if I have seen a little further
  * it is by standing on the shoulder of giants
* another thing
* last thing

**粗体**

*斜体*

***粗体斜体***



> 注：以下两个Markdown符号无法生效，原因是为了避免与Latex（[MathJax](https://www.mathjax.org/)插件）中的符号冲突而手动修改了Hexo的Markdown渲染引擎。去掉了`\`符号的转义语义和`_`符号的斜体语义。修改后行内公式`\\(...\\)`和行间公式`\\[...\\]`也同时失效。

_斜体_

F:\\MYBLOG\\node_modules\\marked\\lib\\marked.js

---



# *删除线*

~~这是一条删除线~~

---



# *表格*

| 姓名          | 性别  | 学校                            |
| :----------  | :--- | :------------------------------ |
| Ouyang Tong  | Male | Beijing Institute of Technology |
| 欧阳          | 男   | 北京理工大学                      |
| 欧阳童        | 男    | 北京理工大学                      |

<br/>

---



# *数学公式*

## 行内公式



> 注：在[MathJax](https://www.mathjax.org/)中行内公式有两种写法，分别是`\\(...\\)`和`$...$`，后者默认是禁用的，需要在[MathJax的Javascript配置文件](https://docs.mathjax.org/en/latest/start.html)中手动启用。

When \\(a \ne 0\\), there are two solutions to  \\(ax^2 + bx + c = 0\\) and they are
\\(x = {-b \pm \sqrt{b^2-4ac} \over 2a}\\).

When $a \ne 0$, there are two solutions to  $ax^2 + bx + c = 0$ and they are
$x = {-b \pm \sqrt{b^2-4ac} \over 2a}$.


## 行间公式

\\[
\frac{du}{dt} and \frac{d^2u}{dt^2}
\\]

$$
\frac{\partial u}{\partial t} 
= h^2 \left( \frac{\partial^2 u}{\partial x^2} + \frac{\partial^2 u}{\partial y^2} + \frac{\partial^2 u}{\partial z^2}\right)
$$

$$
\sum_{k=1}^{n} k^2 = \frac{1}{2} n (n+1).
$$

$$
\int_{a}^{b} f(x) dx
$$

$$
\int_{a}^{b} f(x) \, dx
$$

$$
\int_{0}^{+\infty} x^n e^{-x} \, dx = n!. 
$$

$$
\int \cos \theta \, d\theta = \sin \theta.
$$

$$
\int_{0}^{R} \frac{2x\,dx}{1+x^2} = \log(1+R^2)
$$

$$f(x,y,z) = 3y^2z \left( 3 + \frac{7x+5}{1 + y^2} \right).$$

Details to see: [MathJax](http://docs.mathjax.org/en/latest/tex.html)





[BIT]: http://www.bit.edu.cn