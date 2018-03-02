---
title: JAVA环境变量配置
date: 2015-07-02 16:00:00
tags:
- JAVA
- 环境配置
cover_index: 
cover_detail: 
---

配置Java开发环境必然少不了配置其环境变量，以便在任意处访问Java命令。以下是配置Java环境变量的步骤。



### No.1
在系统变量里点击新建，变量名填写`JAVA_HOME`。

变量名`JAVA_HOME`
变量值`C:\Program Files\Java\jdk1.7.0_21`
<!-- more -->



### No.2
在系统变量里点击新建，变量名填写`CLASSPATH`。

变量名`CLASSPATH`
变量值`.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar`



### No.3
在系统变量里找到Path变量，这是系统自带的环境变量，编辑变量在最后加上`;%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin`。



<br/>
此处路径名称仅供参考。
千万要注意的是，`C:\Program Files\Java\jdk1.7.0_21`后不能有分号，否则第二步和第三步失效。