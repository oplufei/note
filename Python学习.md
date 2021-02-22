# Python学习

[TOC]

## 编程解决问题的步骤

1. 分析问题

   分析问题的计算部分——想清楚

   ​								   ——使用编程能够解决问题的哪一个计算需求

2. 划分边界

   划分问题的功能边界——规划IPO

3. 设计算法

   设计问题的求解算法——关注算法本身

4. 编写程序

   编写问题的计算程序——编程序

5. 调试测试

   调试程序使正确运行——运行调试

6. 升级维护

   适应问题的升级维护——更新完善

## 实例练习

### 根据半径r计算圆面积

交互式（使用IDL）、文件式（文本文件运行）

```python
r = 25
area = 3.1415 * r * r
print(area)
print("{:.2f}".format(area))
```

### 同切圆绘制

```python
import turtle
turtle.pensize(2)
turtle.circle(10)
turtle.circle(40)
turtle.circle(80)
turtle.circle(160)
```

### 五角星绘制

```python
from turtle import *
color('red','red')
begin_fill()
for i in range(5):
    fd(200)
    rt(144)
end_fill()
done()
```

### 温度转换

#### 需求分析

两种温度体系转换——摄氏度转换为华氏度

​							  ——华氏度转换为摄氏度

#### 问题分析

计算部分的理解和确定

1. 直接将温度值进行转换
2. 将温度信息发布的声音或图像形式进行理解和转换
3. 监控温度信息发布渠道，实时获取并转换温度值

#### 划分边界

选择第一种运算

1. 输入：带华氏或摄氏标志的温度值

   标识放在温度最后，F表示华氏度，C表示摄氏度

2. 处理：根据温度标志选择适当的温度转换算法

3. 输出：带摄氏或华氏标志的温度值

#### 设计算法

根据公式
$$
C = (F-32)/1.8
$$

$$
F = C*1.8+32
$$

其中，C表示摄氏温度，F表示华氏温度

```python
#TempConvert.py
TempStr = input("请输入带有符号的温度值：")
if TempStr[-1] in ['F','f']:
    C = (eval(TempStr[0:-1]) - 32)/1.8
    print("转换后的温度是{:.2f}C".format(C))
elif TempStr[-1] in ['C','c']:
    F = 1.8*eval(TempStr[0:-1]) + 32
    print("转换后的温度是{:.2f}F".format(F))
else:
    print("输入格式错误")

```

## 语法元素

### 注释

```python
#单行缩进
'''多行缩进第一行
   多行缩进第二行'''
```

### 命名

规则：大小写字母、数字、下划线、汉字等字符及组合

注意事项

1. 大小写敏感

   Pe pe 是不同变量

2. 首字母不能是数字

   123P 不合法

3. 不与保留字相同

### 保留字

被编程语言内部定义并保留使用的标识符

Python语言有33个保留字（也叫关键字）

|   **and**    |   **as**   |  **assert**  |
| :----------: | :--------: | :----------: |
|  **break**   | **class**  | **continue** |
|   **def**    |  **del**   |   **elif**   |
|   **else**   | **except** | **finally**  |
|   **for**    |  **from**  |  **global**  |
|    **if**    | **import** |    **in**    |
|    **is**    | **lambda** |   **None**   |
| **nonlocal** |  **not**   |    **or**    |
|   **pass**   | **raise**  |  **return**  |
|   **try**    | **while**  |   **with**   |
|  **yield**   | **FALSE**  |   **TRUE**   |

## 数据类型

供计算机程序理解的数据形式

程序设计语言不允许存在语法歧义，需要定义数据的形式供计算机车给你需理解

程序设计语言要通过一定方式向计算机表达数据的形式

### 字符串

```python
"字符串由一对单引号或一对双引号表示，单双引号一样的没区别"
'字符串是字符的有序序列，可以对其中的字符进行索引，“字”是本段的第0个字符'
```

计算机概念中，序号的开始序号一般都是“0”

#### 索引

返回字符串中单个字符   <字符串>[M]

```python
"请输入："[0]		#获取字符串中的首字符
TempStr[-1]			#获取字符串中的倒数第一个字符
```

#### 切片

返回字符串中的一段字符子串 <字符串>[M:N]

```python
"请输入："[1:3]		#获取第1个、第2个字符，不到第3个字符
TempStr[0:-1]		#获取除最后一个字符串以外的
```

### 数字类型

整数：数学中的整数，带正负号 +1 -1

浮点数：数学中的实数，带正负号、小数点 +1.0 -1.0

### 列表类型

由0个或多个数据组成的有序序列

用[]表示，逗号”，“分隔各元素

```python
[元素1, 元素2, ……, 最后一个元素]
```

用保留字 in 判断一个元素是否在列表中

```python
TempStr[-1] in ['C', 'c']	#判断TempStr赋值后的最后一个字符是不是C/c
```

## 语句与函数

### 赋值语句

由赋值符号构成的一行代码

作用

1. 给变量赋予新的数据值

   ```python
    C = (eval(TempStr[0:-1]) - 32)/1.8	 #右侧运算结果赋给变量C
   ```

   

2. 右侧的数据类型同时作用于变量

   ```python
   TempStr = input("请输入带有符号的温度值：")
   '''	 
       input()返回一个字符串，TempStr也是字符串
   '''
   ```

   

### 分支语句

由判断条件决定程序运行方向的语句

用保留字 ***if  elif  else***  构成条件判断的分之结构

```python
if TempStr[-1] in ['F','f']:
    C = (eval(TempStr[0:-1]) - 32)/1.8
    print("转换后的温度是{:.2f}C".format(C))
'''
	如果条件为True，执行冒号后面内容
	否则冒号后面跳过
	冒号及后续缩进用来表示后续语句与条件的所属关系
'''
```



### 函数

根据输入参数产生不同输出的功能过程

类似数学中的函数  <函数名>（<参数>）

```python
print("123")		#打印输出”123“
eval(TempStr[0:-1])		#TempStr[0:-1] 是参数
```

## 函数应用

### 输入函数

  <变量> = input（<提示信息字符串>）

```python
TempStr = input('请输入：')
'''
	从控制台获得用户输入
	TempStr 保存用户输入的信息
	‘请输入：’ 是提示信息
'''
```

### 输出函数

print(<拟输出字符串或字符串变量>)

以字符形式向控制台输出结果

```python
print('输入格式错误')   
```

格式化方法

```python
 print("转换后的温度是{:.2f}F".format(F))
```

### 评估函数

eval()

去掉参数最外侧引号并执行余下语句

```python
eval('1')
eval('1+2')
eval('"1+2"')
```

结果：

1

3

‘1+2’

```python
eval("print('hello')")		#输出 hello
eval('print('hello')')		#SyntaxError: invalid syntax
eval('print("hello")')		#输出 hello
eval("print("hello")")		#SyntaxError: invalid syntax
```

作用：能将任何字符串语句的信息变成Python语句

## 基本图形绘制

### 实例练习

用程序绘制一条蟒蛇

#### 分析问题

1. 设计蟒蛇形象

   类似粗波浪线

2. 计算机绘图是什么原理

   一段程序为何能够产生窗体？

   为何能在窗体上绘制图形？

3. Python绘制蟒蛇从哪里开始

   如何绘制一条线？

   如何绘制一个弧形？

   如何绘制一个蟒蛇？

#### 算法代码

```python
#PythonDraw.py
import turtle								#引入绘图库 
turtle.setup(650, 350, 200, 200)			#
turtle.penup()								#
turtle.fd(-250)								#
turtle.pendown()							#
turtle.pensize(25)							#
turtle.pencolor("purple")					#
turtle.seth(-40)							#
for i in range(4):
    turtle.circle(40, 80)
    turtle.circle(-40, 80)
turtle.circle(40, 80/2)
turtle.fd(40)
turtle.circle(16, 180)
turtle.fd(40 * 2/3)
turtle.done()
```

### Python标准库——turtle库

#### 绘图窗体

```python
turtle.setup(width, height, startx, starty)
```

startx, starty 可选：绘图窗体左上角位置相对于屏幕左上角（是坐标原点）的坐标

width, height：窗口本身的宽度、高度

setup()不是必须的

```python
turtle.setup(800, 400, 0, 0)			#在屏幕左上角
turtle.setup(800, 400)					#默认在正中心
```

#### 坐标体系

绝对坐标

（0， 0）原点：海龟初始位置

x轴（0， +∞）：海龟向右行进

​      （-∞， 0）：海龟向左行进

y轴（0， +∞）：海龟向上行进

​      （-∞， 0）：海龟向下行进