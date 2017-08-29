---
title: elements
date: 2017-08-29 17:00:00
tags: 测试
cover_index: /assets/1.jpg
cover_detail: /assets/2.jpg
photos:
- /assets/1.jpg
- /assets/2.jpg
- /assets/3.jpg
- /assets/5.jpg
- /assets/7.jpg
- /assets/8.jpg
- /assets/9.jpg
- /assets/10.jpg
- /assets/11.jpg
---



Markdown element test file。
Markdown元素测试文件。



[原生Markdown](https://daringfireball.net/projects/markdown/)允许段落内换行，只需在换行处添加两个或两个以上的空格然后回车即可（单个回车在原生Markdown中被视为一个空格处理，两个及两个以上回车被视为另起段落。多个空格被视为一个空格）。空行为段落的结束，多个空行被视为一个空行。
各个衍生（如[GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/)）Markdown中，段落内换行只需回车即可，不再需要添加空格。多个空格视为一个空格，多个空行视为一个空行，空行为段落的结束。




九宫格beta
![Want me?](/assets/6.jpg)![Want me?](/assets/4.jpg)![Want me?](/assets/5.jpg)
![Want me?](/assets/1.jpg)![Want me?](/assets/2.jpg)![Want me?](/assets/3.jpg)
![Want me?](/assets/22.jpg)![Want me?](/assets/11.jpg)![Want me?](/assets/23.jpg)

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
>> 这是二级引用

> Every interaction is both precious and an opportunity to delight.

{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html  Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}

___


# *代码*
代码块

```python
import __ouyang__
import __future__
def dfs(roo):
	if root:
		print root.val
		dfs(root.left)
		dfs(root.right)
def dfs(root):
	if root:
		print root.val
		dfs(root.left)
		dfs(root.right)
def dfs(root):
	if root:
		print root.val
		dfs(root.left)
		dfs(root.right)
def dfs(root):
	if root:
		print root.val
		dfs(root.left)
		dfs(root.right)

def dfs(root):
	if root:
		print root.val
		dfs(root.left)
		dfs(root.right)
def dfs(root):
	if root:
		print root.val
		dfs(root.left)
		dfs(root.right)
def dfs(root):
	if root:
		print root.val
		dfs(root.left)
		dfs(root.right)

```
代码行

执行`python setup.py install`代码安装python库。

---


# *图片和链接*
![Want me?](/assets/4.jpg)
[北京理工大学][BIT]

***


# *列表*
有序列表
1. first
2. second
3. third

无序列表
* one thing
	* if I have seen a little further
	* it is by standing on the shoulder of giants
* another thing
* last thing

***粗体斜体***
** *粗体斜体2* **
** 粗体 **
*斜体*

---


# *删除线*
~~这是一条删除线~~

---


# *表格*

|姓名|性别|学校|
|:---|:---|:---|
|欧阳Tong|男|北京理工大学|
|欧阳|男|北京理工大学|
|欧阳童|男|北京理工大学|

<br/>

---


# *数学公式*

When \\(a \ne 0\\), there are two solutions to  \\(ax^2 + bx + c = 0\\) and they are
$$x = {-b \pm \sqrt{b^2-4ac} \over 2a}$$

$$
\frac{du}{dt} and \frac{d^2u}{dt^2}
$$

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



\begin{align}
\cos2\theta &= \cos^2\theta - \sin^2\theta \\\
&= 2\cos^2\theta-1
\end{align}


The \\emph{characteristic polynomial} \\(\chi(\lambda)\\) of the
\\(3 \times 3\\) matrix
$$
\left( \begin{array}{ccc}
a & b & c \\\ 
d & e & f \\\
g & h & i \end{array}\right)
$$
is given by the formula
$$
\chi(\lambda) = \left| \begin{array}{ccc}
\lambda - a & -b & -c \\\
-d & \lambda - e & -f \\\
-g & -h & \lambda - i \end{array} \right|.
$$

$$
\begin{array}{c|lcr}
n & \text{Left} & \text{Center} & \text{Right} \\\
\hline
1 & 0.24 & 1 & 125 \\\
2 & -1 & 189 & -8 \\\
3 & -20 & 2000 & 1+10i \\\
\end{array}
$$


\begin{align}
\sqrt{37} & = \sqrt{\frac{73^2-1}{12^2}} \\\
 & = \sqrt{\frac{73^2}{12^2}\cdot\frac{73^2-1}{73^2}} \\\
 & = \sqrt{\frac{73^2}{12^2}}\sqrt{\frac{73^2-1}{73^2}} \\\
 & = \frac{73}{12}\sqrt{1 - \frac{1}{73^2}} \\\ 
 & \approx \frac{73}{12}\left(1 - \frac{1}{2\cdot73^2}\right)
\end{align}



Details to see: [MathJax](http://docs.mathjax.org/en/latest/tex.html)


[BIT]: http://www.bit.edu.cn