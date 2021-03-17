# Python学习

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

2类共4种表示方法：单引号，双引号，单内有双，双内有单

#### 字符串的序号

| 反向递减序号 |  -5  |  -4  |  -3  |  -2  |  -1  |
| ------------ | :--: | :--: | :--: | :--: | :--: |
|              |  这  |  是  |  字  |  符  |  ：  |
| 正向递增序号 |  0   |  1   |  2   |  3   |  4   |

由左到右：正向

由结尾处到头部：反向

使用 [ ]  获取字符串中一个或多个字符

#### 字符串基本表达

##### 索引

返回字符串中单个字符   <字符串>[M]

```python
"请输入："[0]		# 获取字符串中的首字符
TempStr[-1]		  # 获取字符串中的倒数第一个字符
```

##### 切片

返回字符串中的一段字符子串 <字符串>[M:N]

```python
"请输入："[1:3]		#获取第1个、第2个字符，不到第3个字符
TempStr[0:-1]		#获取除最后一个字符串以外的
```

###### 高级用法

使用 [M: N: K] 根据步长对字符串切片

```python
<字符串>[M:N:K]	# M缺失表示至开头，N缺失表示至结尾
```

实例

```python
"〇一二三四五六七八九十"[:3]			# 〇一二
"〇一二三四五六七八九十"[1:3:2]		# 一三五七
"〇一二三四五六七八九十"[::-1]			# 十九八七六五四三二一〇
```

##### 转义符 \ （反斜杠）

表示特定字符的本意

|         输入         |          输出          |
| :------------------: | :--------------------: |
| "这里有个双引号(\")" |   这里有个双引号(")    |
|          \b          |          回退          |
|          \n          | 换行，光标移动到下行首 |
|          \r          | 回车，光标移动到本行首 |

#### 字符串操作符

|  操作符及使用  |                 描述                 |
| :------------: | :----------------------------------: |
|     x + y      |        连接两个字符串 x 和 y         |
| n * x 或 x * n |            复制n次字符串x            |
|     x in s     | x 是 s 的子串，返回 True，否则 False |

##### 实例  获取星期字符串

输入： 1-7 的整数，表示星期几

输出： 输入整数对应的星期字符串

例如： 输入 3 ，输出 星期三

```python
# 获取星期字符串（我）
X = input("请输入1-7的整数：")
Y = "一二三四五六日"[eval(X) - 1]
print("星期{}".format(Y))
```

```python
# 课程——练习切片用法
weekStr = "星期一星期二星期三星期四星期五星期六星期日"
weekId = eval(input("请输入星期数字（1-7）："))
pos = (weekId -1) * 3
print(weekStr[pos: pos+3])
```

```python
# 课程——练习切片用法——精简
weekStr = "一二三四五六日"
weekId = eval(input("请输入星期数字（1-7）："))
print("星期" + weekStr[weekId-1])
```

#### 字符串处理函数

| 函数及使用 |                       描述                        |
| :--------: | :-----------------------------------------------: |
|   len(x)   |   长度，返回字符串x的长度，len("一二三456") = 6   |
|   str(x)   |  任意类型x所对应的字符串形式，str(1.23) = "1.23"  |
|   hex(x)   | 整数x的十六进制小写形式字符串，hex(425) = "0x1a9" |
|   oct(x)   |  整数x的八进制小写形式字符串，oct(425) = "0o651"  |
|   chr(u)   |         u为Unicode编码，返回其对应的字符          |
|   ord(x)   |         x为字符，返回其对应的Unicode编码          |

#### 字符串处理方法

方法：面向对象 编程中一个专有名词，特指<a>.<b>() 风格中的函数 <b>.()

方法本身也是函数，但是与对象<a>有关

|          方法及使用          |                             描述                             |
| :--------------------------: | :----------------------------------------------------------: |
|         str.lower()          |    返回字符串的副本，全部字符小写， "AbC".lower() = "abc"    |
|         str.upper()          |    返回字符串的副本，全部字符大写，"AbC".upper() = "ABC"     |
|     str.split(sep=None)      | 返回一个列表，由str根据sep被分隔的部分组成， "A,B,C".split(",") = ['A','B','C'] |
|        str.count(sub)        | 返回子串sub在str中出现的次数，"an apple a day".count('a') = 4 |
|    str.replace(old, new)     | 返回字符串str副本，所有old子串被替换为new子串，"python".replace("n","n123.io") = "python123.io" |
| str.center(width[,fillchar]) | 格式处理，字符串str根据宽度width居中，fillchar可选，"python".center(20, "=") = '=======python=======' |
|       str.strip(chars)       | 从str中去掉在其左侧和右侧chars中列出的字符，"= python=".strip(" =np") = 'ytho' |
|        str.join(iter)        | 在iter变量除最后元素外每个元素后增加一个str，主要用于字符串分隔等， ",".join("12345") = '1,2,3,4,5' |

#### 字符串类型格式化

格式化是对字符串进行格式表达的方式，用槽机制+.format()实现

##### .format() 方法

<模板字符串>.format(<逗号分隔的参数>) 

##### 槽

占位信息符，{} 表示，只在字符串中有用

```python
"{}:计算机{}的CPU占用率为{}%".format("2018-10-10","C",10)
"{1}:计算机{0}的CPU占用率为{2}%".format("2018-10-10","C",10)
```

结果

'2018-10-10:计算机C的CPU占用率为10%'

'C:计算机2018-10-10的CPU占用率为10%'

##### 槽内部对格式化的配置

{<参数序号> : <格式控制标记>}

控制元素

1. 引导符号“：”
2. <填充>：用于填充的单个字符
3. <对齐>： 左对齐"<"  右对齐">" 居中对齐"^"
4. <宽度>：槽设定的输出宽度
5. <,>：数字的千位分隔符
6. <.精度>：浮点数小数精度或者字符串最大输出长度
7. <类型>：以什么类型将变量放入槽中整数类型 b, c, d, o, x, X    浮点数类型 e, E, f, %

前三个一组，后三个一组

```python
"{0:=^20}".format("PYTHON")
"{0:+>20}".format("BIT")
"{:10}".format("BIT")
```

结果

"=======PYTHON======="    

放入槽中的format方法中的第0个参数以居中对齐方式显示，输出宽度20个字符，用 = 填充

"+++++++++++++++++BIT"

放入槽中的format方法中的第0个参数以右对齐方式显示，输出宽度20个字符，用 + 填充

"BIT       "

省略<填充><对齐>，默认左对齐，填充空格

```python
"{0:,.2f}".format(12345.6789)
"{0:b},{0:c},{0:d},{0:o},{0:x},{0:X}".format(425)
"{0:e},{0:E},{0:f},{0:%}".format(425)
```

结果

'12,345.68'

整数部分用千位分隔符分隔方便阅读，小数部分保留两位精度

'110101001,Ʃ,425,651,1a9,1A9'

分别呈现数字425的 二进制数，Unicode编码对应的字符形式，十进制，八进制，十六进制小写，十六进制大写

'4.250000e+02,4.250000E+02,425.000000,42500.000000%'

### 数字类型

#### 整数类型

数学中的整数，带正负号 如+1 -1

可正可负，没有取值范围限制

```python
pow(x,y)			# 计算x的y次幂
pow(2,pow(2,15))
```

4种进制表示形式

1. 十进制：     1010，-127
2. 二进制：     以0b或者0B开头，如 0b010，-0B010
3. 八进制：     以0o或者0O开头，如 0o123，-0O123
4. 十六进制： 以0x或者0X开头，如 0x9a，-0X89 

#### 浮点数类型

数学中的实数，带正负号、小数点，如  +1.0 -1.0

取值范围和小数精度有限制，常规计算可忽略

##### 取值范围

pow(-10, 308) - pow(10, 308)

##### 精度

 pow(10, -16)

##### round() 函数

1. 浮点数间运算存在不确定尾数（因为浮点数对应二进制数是截取了53位的无限小数）

2. 处理方法

   ```python
   round(x, d)			# 对x四舍五入，保留d位小数
   0.1+0.2 == 0.3		# False
   round(0.1+0.2, 1)	# True
   ```

   浮点数间运算及比较用

   不确定尾数一般发生在 pow(10, -16) 左右，round()有效

##### 科学计数法

字母e或E作为幂的符号，以10为基数

```python
<a>e<b>			# a * pow(10, b)
4.3e-3			# 0.0043
9.6E5			# 960000.0
```

#### 复数类型

同数学中复数概念

空间变换，尤其是复变函数相关科学体系，常用

```python
z = 1.23e-4 + 5.6e + 89j
z.real							# 获得实部
z.imag							# 获得虚部
```

#### 数值运算操作符

| 操作符及使用 |                 描述                 |
| :----------: | :----------------------------------: |
|    x + y     |                  加                  |
|    x - y     |                  减                  |
|    x * y     |                  乘                  |
|    x / y     |   除，浮点数形式，10/3 = 3.3333333   |
|    x // y    |          整数除，10//3 = 3           |
|     + x      |                x 本身                |
|     - y      |               y 的负值               |
|    x % y     |            余数，10%3 = 1            |
|    x ** y    |          幂运算， pow(x, y)          |
|              | 当 y 是小数，开方运算， 4 ** 0.5 = 2 |

| 增强操作符及使用 |             描述             |
| :--------------: | :--------------------------: |
|     x op= y      | x = x op y  , op为二元操作符 |
|      x += y      |          x = x + y           |
|      x -= y      |          x = x - y           |
|      x *= y      |          x = x * y           |
|      x /= y      |          x = x / y           |
|     x  //= y     |          x = x // y          |
|      x %= y      |          x = x % y           |
|     x **= y      |          x = x ** y          |

#### 数值运算函数

|    函数及使用    |                             描述                             |
| :--------------: | :----------------------------------------------------------: |
|      abs(x)      |                 绝对值，abs(-10.01) = 10.01                  |
|   divmod(x, y)   |       商余，同时输出商和余数， divmod(10, 3) = (3, 1)        |
| pow(x, y [, z])  | 幂余，(x**y)%z，[..]表示参数z可省略， pow(3, pow(3, 99), 10000) = 4587 |
|  round(x[, d])   | 四舍五入，d保留小数位，默认值为0， round(-10.123, 2) = -10.12 |
| max(a,b,c,...,n) |                最大值，max(1, 9, 4, 3, 5) = 9                |
| min(a,b,c,...,n) |                最小值，min(1, 9, 4, 3, 5) = 1                |
|      int(x)      |   强制类型转换为整数，int(123.45) = 123, int("123") = 123    |
|     float(x)     | 强制类型转换为浮点数， float(123) = 123.0, float("123") = 123.0 |
|    complex(x)    |           强制转换类型为复数，complex(4) = 4 + 0j            |

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

## 语句

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

用保留字 ***if  elif  else***  构成条件判断的分支结构

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

#### 单分支结构 if

```python
# 猜数字
guess = eval(input())		# 常组合用来转换获得数字
if guess == 99:
    print("猜对了")
```

永远会执行语块1

```python
if True:
    print("语块1")
```

永远不会执行语块1

```python
if False:
    print("语块1")
```

#### 二分支结构 if...else...

```python
# 猜数字
guess = eval(input())		
if guess == 99:
    print("猜对了")
else:
    print("猜错了")
```

语块2永远不会被执行，语块1永远执行

```python
if True:
    print("语块1")
else:
    print("语块2")
```

```python
if not True:
    print("语块2")
else:
    print("语块1")
```

紧凑形式，适用简单表达式

```python
# 猜数字紧凑形式
guess = eval(input())
print("猜{}了".format("对" if guess == 99 else "错"))
```

<表达式1> if <条件> else <表达式2>

表达式不支持赋值，紧凑形式不是语句不能赋值

#### 多分支结构 if..elif..else..

```python
# 成绩分级
score = eval(input())
if score < 60:
    grade = "E"
elif score >=60 and score < 70:
    grade = "D"
elif score >= 70 and score < 80:
    grade = "C"
elif score >= 80 and score < 90:
    grade = "B"
else :
    grade = "A"
print(grade)
```

#### 条件判断及其组合

| 操作符  |   描述   |
| :-----: | :------: |
|    <    |   小于   |
|   < =   | 小于等于 |
|   > =   | 大于等于 |
|    >    |   大于   |
|   = =   |   等于   |
|   ! =   |  不等于  |
| x and y |  逻辑与  |
| x or y  |  逻辑或  |
|  not x  |  逻辑非  |

#### 程序异常处理 try..except..

##### 基本使用

```python
try : 
    num = eval(input("输入一个整数："))
    print(num**2)
except :
    print("输入的不是整数")
```

发生异常后，try接收到异常，输入except后语句

##### 针对特定异常类型处理

```python
try : 
    num = eval(input("输入一个整数："))
    print(num**2)
except NameError:
    print("输入的不是整数")
```

标注异常类型后仅响应该异常，异常类型名等同于变量，该名称是系统设定的

##### 高级用法 try..except..else..finally..

```python
try :
    <语句块1>			
except :
    <语句块2>		# 语句1异常执行
else :
    <语句块3>		# 语句1不发生异常执行
finally :
    <语句块4>		# 一定执行
```

#### 实例

```python
# BMI指数，同时输出国际、国内的
height, weight = eval(input("请输入身高（米）和体重（公斤）[逗号隔开]："))		# 获取用户输入
bmi = weight / pow(height, 2)	# 计算公式
print("BMI 数值为：{:.2f}".format(bmi))
who, nat = "", ""
if bmi < 18.5:
    who, nat = "偏瘦", "偏瘦"
elif 18.5 <= bmi < 24:
    who, nat = "正常", "正常"
elif 24 <= bmi < 25:
    who, nat = "正常", "偏胖"
elif 25<= bmi < 28:
    who, nat = "偏胖", "偏胖"
elif 28<= bmi < 30:
    who, nat = "偏胖", "肥胖"
else :
    who, nat = "肥胖", "肥胖"
print("BMI指标为：国际“{0}”,国内“{1}”".format(who,nat))
```

注意

1. 多分支条件之间的覆盖
2. 可运行但是不正确，关注分支
3. 读程序先看分支，可以提高效率

## 函数

### 简单函数

根据输入参数产生不同输出的功能过程

类似数学中的函数  <函数名>（<参数>）

```python
print("123")		#打印输出”123“
eval(TempStr[0:-1])		#TempStr[0:-1] 是参数
```

####  input()

输入函数，   <变量> = input（<提示信息字符串>）

```python
TempStr = input('请输入：')
'''
	从控制台获得用户输入
	TempStr 保存用户输入的信息
	‘请输入：’ 是提示信息
'''
```

#### print()

输出函数， print(<拟输出字符串或字符串变量>)

以字符形式向控制台输出结果

```python
print('输入格式错误')   
```

格式化方法

```python
 print("转换后的温度是{:.2f}F".format(F))
```

format() 中的值 F 按照 {} 里面的内容调整后嵌入输出

```
#输入123456789.01234567F
68587087.23C
```

#### eval()

评估函数 ，去掉参数最外侧引号并执行余下语句

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

### 函数的定义 def

函数是一种功能的抽象，一般表达特定功能

函数是一段具有特定功能的、可重用的语句组，表现为一段代码

```python
def <函数名>(<参数(0个或多个)>):
    <函数体>
    return<返回值>
```

等价于 <函数名> = lambda <参数> : <表达式> （详见lambda函数）

实例

```python
# 计算 n !
def fact(n):
    s = 1
    for i in range(1, n+1):
        s *= i
    return s
```

结果

```python
>>>			
```

函数在定义时，指定的参数是一种占位符，为形式参数

函数定义后，不调用不执行

```python
# 计算 10 !
def fact(n):
    s = 1
    for i in range(1, n+1):
        s *= i
    return s
a = fact(10)
print(a)
```

结果

```
3628800
```

调用函数时，输入——实际参数（10）——用来替换形式参数 n，处理——函数体，输出——结果（3628800）

### 函数的参数传递

参数传递： 函数调用时，怎么将实际的值给定到参数上。默认是参数按照位置的方式给定参数，也可以按照名称的方式传递

#### 无参数

函数可以有参数，也可以没有，但是必须保留括号

```python
def fact():
    print("我也是函数")
```

#### 可选参数的传递——赋初值

函数定义时可以为某些参数指定默认值，构成可选参数

必选参数必须放在可选参数前面

```python
# 计算 n !// m —— 根据位置传递参数
def fact(n, m = 1):
    s = 1
    for i in range(1, n+1):
        s *= i
    return s // m
a = fact(10)
print(a)
a = fact(10, 5)
print(a)

# 计算 n !// m —— 根据名称传递参数
def fact(n, m = 1):
    s = 1
    for i in range(1, n+1):
        s *= i
    return s // m
print(fact(m=5, n=10))
```

结果

```
3628800
725760
725760
```

#### 可变参数传递—— *b

函数定义时设计可变数量的参数，即不确定参数总数量，给几个根据调用时候的确定

```python
# 计算 n ! 乘数
def fact(n, *b):
    s = 1
    for i in range(1, n+1):
        s *= i
    for item in b:
        s *= item
    return s
print(fact(3, 3))
print(fact(3, 2, 5))
```

*b： 可变参数

结果

```
18
60
```

### 函数的返回值 return

函数可以返回 0 个或多个结果

return： 传递返回值

函数可以有返回值，也可以没有，可以有 return，也可以没有

```python
# 计算 n !// m —— 返回值
def fact(n, m = 1):
    s = 1
    for i in range(1, n+1):
        s *= i
    return s // m, n, m
print(fact(10, 5))
a,b,c = fact(10, 5)
print(a,b,c)
```

结果

```python
(725760, 10, 5)			# 结果为一种组合数据类型——元组类型
725760 10 5
```

### 局部变量和全局变量 global

局部变量： 函数内部使用的变量

全局变量： 整个程序使用的变量

#### 使用规则1 局部变量和全局变量是不同的变量

1. 局部变量是函数内部的占位符，与全局变量可能重名但不同

   ```python
   n, s = 10, 100			# 此时 s 是全局变量
   def fact(n):
       s = 1				# 此时 s 是局部变量
       for i in range(1, n+1):
           s *= i
       return s			# 此处局部变量 s = 3628800
   print(fact(n), s)		# 此处全局变量 s = 100
   ```

   结果

   ```
   3628800 100
   ```

2. 函数运算结束后，局部变量被释放（即不存在了）

3. 可以使用 global 保留字在函数内部使用全局变量

   ```python
   n, s = 10, 100			
   def fact(n):
       global s				
       for i in range(1, n+1):
           s *= i
       return s			
   print(fact(n), s)
   ```

   结果

   ```
   362880000 362880000
   ```

#### 规则2 局部变量为组合数据类型且未创建，等同于全局变量

```python
# 等同于全局变量的情况
ls = ["F", "f"]			# 通过使用 [] 真实创建了一个全局变量列表ls
def func(a):
    ls.append(a)		# 此处 ls 是列表类型，未真实创建，等同于全局变量
    return
func("C")				# 全局变量 ls 被修改
print(ls)

# 局部变量情况
ls = ["F", "f"]	
def func(a):
    ls = []
    ls.append(a)		# 此处 ls 是列表类型，真实创建，是局部变量
    return
func("C")				# 局部变量 ls 被修改
print(ls)
```

结果

```
['F', 'f', 'C']
['F', 'f']
```

组合类型就是由多个数组成的

### lambda函数

返回函数名作为结果， <函数名> = lambda <参数> : <表达式>

##### 用法

1. 是一种匿名函数，即没有名字的函数
2. 使用 lambda 保留字定义，函数名是返回结果
3. 用于定义简单的、能够在一行内表示的函数

```python
>>>f = lambda x, y : x + y
>>>f(10, 15)

f = lambda : "一串字符"
print(f())
```

结果

```
25
一串字符
```

#### 注意

1. 谨慎使用lambda函数
2. lambda函数主要用于一些特定函数或方法的参数
3. lambda函数有固定使用方式，建议逐步掌握
4. 一般情况使用 def 定义普通函数

## 程序的循环结构

### 遍历循环 for..in..

```python
for <循环变量> in <遍历结构> :
    <语句块>
```

作用

1. 从遍历结构中逐一提取元素放到循环变量中
2. 完整遍历所有元素后结束
3. 每次循环，所获得元素放入循环变量，并执行一次语句块
4. 由多个元素构成的数据类型都可以用 for..in.. 来遍历包含元素

##### 计数循环 for...in range() 

按照一定次数循环执行一组语句

```python
for <循环变量> in range (<参数>):
	<被循环执行的语句>
```

<循环变量>： 每次循环的计数，0 ~ （<次数> - 1）

range()： 产生数字序列（循环计数序列），产生循环

range(N)：  0 到 N-1 整数序列

range(M, N, K)： M 到 N-1以 K 为步长的整数序列

```python
for i in range(5):
    print(i)
    
for i in range(5):
    print("hello:",i)
    
for i in range(2,5):
    print(i)
    
for i in range(1,6,2):
    print(i)
```

输出结果

```
0
1
2
3
4
hello: 0
hello: 1
hello: 2
hello: 3
hello: 4
2
3
4
1
3
5
```

print()中间加 ‘，’，输出结果之间自动加空格 

##### 字符串遍历循环 for c in s...

```python
for c in s:
    <语句块>
```

s： 字符串，遍历字符串每个字符，产生循环

c： 与保留字不同的都可以，习惯用c

```python
for c in "Python123" :
    print(c,end=",")
```

结果

```
P,y,t,h,o,n,1,2,3,
```

##### 列表遍历循环 for item in ls...

```python
for item in ls :
    <语句块>
```

ls： 列表，遍历其每一个元素，产生循环

```python
for item in [123, "PY", 456] :
    print(item,end=",")
```

结果

```
123,PY,456,
```

##### 文件遍历循环

```python
for line in fi :
    <语句块>
```

fi： 文件标识符，遍历其每行，产生循环

### 无限循环 while

由条件控制的循环运行方式

反复执行语句块，直到条件不满足时结束

```python
a = 3
while a > 0 :
    a = a - 1
    print(a)
    
a = 3
while a > 0 :
    a = a + 1
    print(a)
```

结果

```python
2
1
0
4
5
6
……
（按ctrl + c）
Traceback (most recent call last):
  File "C:\Users\Administrator\Desktop\test.py", line 9, in <module>
    print(a)
KeyboardInterrupt
```

ctrl + c 强制退出当前程序执行

### 循环控制保留字 

#### continue

结束档次循环，继续执行后续次数循环

```python
for c in "PYTHON" :
    if c == "T" :		# 是 T 就不打印
        continue
    print(c, end="")
```

结果

```
PYHON
```

#### break

跳出并结束当前整个循环，并执行循环后的语句

###### 单层循环实例

```python
for c in "PYTHON" :
    if c == "T" :		# 是 T 就结束，只打印 T 之前的
        break
    print(c, end="")
```

结果

```
PY
```

###### 多层循环实例

```python
s = "PYTHON"
while s != "" :     # 字符串不为空
    for c in s :    # 打印字符串中每个元素
        print(c, end="")    
    s = s[:-1]      # 去掉最后一个字符

print("\n")    
    
s = "PYTHON"
count = 1
while s != "" :     # 字符串不为空
    print("第{}轮".format(count))
    for c in s :    # 打印字符串中元素
        if c == "O" :	
            break		# 遇到H结束
        print(c, end="")
    count += 1
    s = s[:-1]      # 去掉最后一个字符
    print("\n")
```

结果

```
PYTHONPYTHOPYTHPYTPYP

第1轮
PYTH

第2轮
PYTH

第3轮
PYTH

第4轮
PYT

第5轮
PY

第6轮
P
```

一个 break 保留字只能跳出一层循环

break、continue 都可以与 for、while 搭配使用

### 循环的扩展用法——循环与else

```python
for <循环变量> in <遍历结构> :
    <语句块1>
else :
    <语句块2>
    
while <条件> :
    <语句块1>
else :
    <语句块2>
```

else 作用

1. 当循环没有被 break 语句退出时，执行 else 语句块
2. else 语句块作为“正常”完成循环的奖励
3. 与异常处理中 else 的用法相似

```python
print("无break")
for c in "PYTHON" :
    if c == "T" :
        continue
    print(c, end="")
else :
    print("正常退出")

print("有break")
for c in "PYTHON" :
    if c == "T" :
        break
    print(c, end="")
else :
    print("正常退出")  
```

结果

```
无break
PYHON正常退出
有break
PY
```

用 else 可以判断程序是否被 break 结束，利于程序逻辑设计

## Python标准库——turtle库

实现基本图形绘制功能

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

##### 基本代码

```python
#PythonDraw.py
import turtle								#引入绘图库 
turtle.setup(650, 350, 200, 200)			# 设置窗体
turtle.penup()								#抬起画笔
turtle.fd(-250)								#移到左侧
turtle.pendown()							#落下画笔
turtle.pensize(25)							#设置画笔
turtle.pencolor("purple")					#
turtle.seth(-40)							#
for i in range(4):							#循环绘制路径形成身体
    turtle.circle(40, 80)
    turtle.circle(-40, 80)
turtle.circle(40, 80/2)						#画头
turtle.fd(40)
turtle.circle(16, 180)
turtle.fd(40 * 2/3)
turtle.done()								#运行后程序不退出
```

基本代码分析

1. tutle.xxx：<a>.<b>() 编码风格

2. 库引用——扩充Python程序功能的方式

   ```python
   import <库名>
   <库名>.<函数名>(<函数参数>)
   ```

   

##### 简洁代码

```python
from turtle import* 
setup(650, 350, 200, 200)			
penup()								
fd(-250)								
pendown()							
pensize(25)							
pencolor("purple")					
seth(-40)							
for i in range(4):
    circle(40, 80)
    circle(-40, 80)
circle(40, 80/2)
fd(40)
circle(16, 180)
fd(40 * 2/3)
done()
```

简洁代码分析

1. 库引用方法——from 配合 import使用

   ```python
   from <库名> import <函数名>
   from <库名> import *
   <函数名>(<函数参数>)
   ```

   

2. 优点： 简洁，不用频繁使用 turtle.

   缺点： 与用户自定义的函数重名，产生函数冲突

   使用： 程序短，只使用定义库

##### 建议代码风格

```python
import turtle as t								 
t.setup(650, 350, 200, 200)			
t.penup()								
t.fd(-250)								
t.pendown()							
t.pensize(25)							
t.pencolor("purple")					
t.seth(-40)							
for i in range(4):
    t.circle(40, 80)
    t.circle(-40, 80)
t.circle(40, 80/2)
t.fd(40)
t.circle(16, 180)
t.fd(40 * 2/3)
t.done()
```

分析

1. 库引用方法——as 配合 import 使用

   ```python
   import <库名> as <库别名>
   <库别名>.<函数名>(<函数参数>)
   ```

   

2. 优点： 给调用的外部库关联一个更短、更适合自己的名字

​                   冗余少，避免函数重名

#### 绘图窗体

##### turtle.setup(width, height, startx, starty)

startx, starty 可选：绘图窗体左上角位置相对于屏幕左上角（是坐标原点）的坐标

width, height：窗口本身的宽度、高度

setup()不是必须的

```python
turtle.setup(800, 400, 0, 0)			#在屏幕左上角
turtle.setup(800, 400)					#默认在正中心
```

#### 坐标体系

##### 绝对坐标

（0， 0）原点：海龟初始位置

x轴（0， +∞）：海龟向右行进

​      （-∞， 0）：海龟向左行进

y轴（0， +∞）：海龟向上行进

​      （-∞， 0）：海龟向下行进

###### turtle.goto(x, y)   

到指定位置	

```python
#绘制五边形
import turtle
turtle.goto(100, 100)
turtle.goto(100, -100)
turtle.goto(-100, -100)
turtle.goto(-100, 100)
turtle.goto(0, 0)
```

##### 海龟坐标（详见运动控制）

以海龟前进方向的前后左右确定

##### 角度坐标体系 （方向控制函数）

控制海龟面对的方向： 绝对角度 & 海龟角度

###### turtle.seth(angle)	绝对度数

```python
#画斜Z
import turtle
turtle.seth(45)
turtle.fd(100)
turtle.seth(-90)
turtle.fd(100)
turtle.seth(45)
turtle.fd(100)
```

###### turtle.left(angle)	 相对度数

###### turtle.right(angle)  相对度数

```python
#画斜Z（与上同）
import turtle
turtle.left(45)
turtle.fd(100)
turtle.right(135)
turtle.fd(100)
turtle.left(135)
turtle.fd(100)
```

#### RGB色彩体系 turtle.colormode()

红蓝绿三个通道颜色及颜色组合

每色取值范围：	0 - 255（整数）

​                               0 - 1（小数）

turtle库默认用小数值表示颜色

```python
turtle.colormode(1.0)			#RGB小数值模式
turtle.colormode(255)			#RGB整数值模式
```

#### 画笔控制函数

1. 画笔操作后一直有效，一般成对出现

   ##### turtle.penup()

   别名：turtle.pu() 抬起画笔，海龟在飞行

   ##### turtle.pendown()

    别名：turtle.pd() 落下画笔，海龟在爬行

2. 笔画设置后一直有效，直至下次重新设置

   ##### turtle.pensize(width)      

   别名 turtle.width(width)  画笔宽度，海龟的腰围

   ##### turtle.pencolor(color)     

   画笔颜色，海龟在涂装，color 颜色字符串或RGB值    

```python
turtle.pencolor("purple")		     # 颜色字符串,小写
turtle.pencolor(0.63, 0.13, 0.94)	 #RGB小数值
turtle.pencolor((0.63, 0.13, 0.94))  #RGB元组值     
```

#### 运动控制函数（海龟角度）

控制海龟行进： 走直线 or 走曲线

##### turtle.forward(d)

 别名： turtle.fd(d)

向前行进，海龟走直线

d： 行进距离，负数倒退

##### turtle.circle(r, extent=None)

根据半径 r 绘制 extent 角度的弧形

r：默认圆心在海龟左侧 r 距离的位置

extent： 绘制角度，默认是360度整圆

## Python标准库——time库

time库是Python中处理时间的标准库

作用

1. 计算机时间的表达
2. 提供获取系统时间病格式化输出功能
3. 提供系统级精确计时功能，用于程序性能分析

使用

```python
import time
time.<b>()
```

### 时间获取

#### time()

获取当前时间戳（当前系统中表示时间的浮点数），即计算机内部时间值

```python
time.time()
```

表示从1970年1月1日0:00开始到当前时刻为止的以秒为单位的数值

结果

1615110472.680751

#### ctime()

获取当前时间并以易读方式表示，返回字符串

```python
time.ctime()
```

结果

'Sun Mar  7 17:51:42 2021'

#### gmtime()

获取当前时间，表示为计算机可处理的时间格式

```python
time.gmtime()
```

结果

time.struct_time(tm_year=2021, tm_mon=3, tm_mday=7, tm_hour=9, tm_min=54, tm_sec=14, tm_wday=6, tm_yday=66, tm_isdst=0)

### 时间格式化

将时间以合理方式展示出来，类似字符串的，也需要展示模板，由特定格式化控制符组成

将计算机内部时间中表达的年月日时分秒等与时间有关的信息用变量形式合理组合并合理输出，通过控制来表达输出格式

#### strftime(tpl, ts)

tpl： 格式化模板字符串，用来定义输出效果

ts：  计算机内部时间类型变量

```python
t = time.gmtime()
time.strftime("%Y-%m-%d %H:%M:%S",t)
```

结果

'2021-03-07 10:04:13'

| 格式化字符串 | 时期/时间说明 |      值范围       |
| :----------: | :-----------: | :---------------: |
|      %Y      |     年份      | 0000~9999，如1900 |
|      %m      |     月份      |       01~12       |
|      %B      |   月份名称    | January~December  |
|      %b      | 月份名称缩写  |      Jan~Dec      |
|      %d      |     日期      |       01~31       |
|      %A      |     星期      |   Monday~Sunday   |
|      %a      |   星期缩写    |      Mon~Sun      |
|      %H      | 小时（24h制） |       00~23       |
|      %I      | 小时（12h制） |       01~12       |
|      %p      |    上/下午    |      AM, PM       |
|      %M      |     分钟      |       00~59       |
|      %S      |      秒       |       00~59       |

#### strptime(str, tpl)

str： 字符串形式的时间值

tpl： 格式化模板字符串，用来定义输入效果

```python
timeStr = '2018-01-26 12:55:20'
time.strptime(timeStr, "%Y-%m-%d %H:%M:%S")
```

结果

time.struct_time(tm_year=2018, tm_mon=1, tm_mday=26, tm_hour=12, tm_min=55, tm_sec=20, tm_wday=4, tm_yday=26, tm_isdst=-1)

### 程序计时应用

程序计时： 测量起止动作所经历时间的过程

#### perf_counter()

精准的测量时间函数，能够获取计算机中CPU以其频率运行的时钟，从而记录时间的流逝

使用时，返回一个CPU级别的精确时间计数值，单位为秒

由于这个计数值起点不确定，连续调用差值才有意义

```python
start = time.perf_counter()
end = time.perf_counter()
end - start
```

结果

7.290818217000037

#### sleep(s)

产生时间函数，让程序去休眠s秒或者产生一定的时间

s： 拟休眠的时间，单位是秒，可以是浮点数

```python
def wait():
    time.sleep(3.3)
wait()
```

结果

输入weit()后，当前程序停滞3.3秒后退出

休眠即程序停在原位不进行其他操作，等待3.3秒

### 实例 文本进度条

#### 分析问题

生成一个有开始结束标记、有一定进度百分比表示的进度条格式

##### 简单静态代码

```python
#TextProBar1.py
import time
scale = 10
print("------执行开始------")
for i in range(scale+1):
    a = '*' * i
    b = '.' * (scale - i)
    c = (i/scale)*100
    print("{:^3.0f}%[{}->{}]".format(c,a,b))
    time.sleep(0.1)
print("------执行结束------")
```

结果

```
------执行开始------
 0 %[->..........]
10 %[*->.........]
20 %[**->........]
30 %[***->.......]
40 %[****->......]
50 %[*****->.....]
60 %[******->....]
70 %[*******->...]
80 %[********->..]
90 %[*********->.]
100%[**********->]
------执行结束------
```

##### 单行静态刷新代码

刷新： 用后打印的字符信息覆盖之前的信息

刷新的本质要求

1. 不能换行，print() 需要被控制
2. 要能回退，打印后光标退回到之前的位置，使用 \r

```python
import time
for i in range(11):
    print("\r{:3}%".format(i), end="")
    time.sleep(0.1)
```

结果

```
0%  1%  2%  3%  4%  5%  6%  7%  8%  9% 10% 
```

按顺序一个一个打印出，不换行

因为IDLE是开发环境，为了保证测试运行效果，\r 被屏蔽了，所以全部显示了，用控制台就可以显示单行刷新了

win用命令行类似的工具

linux用B shell等一些文本的shell工具

##### 完整效果代码

```python
#TextProBar2.py
import time
scale = 50
print("执行开始".center(scale//2, "-"))
start = time.perf_counter()
for i in range(scale+1):
    a = '*' * i
    b = '.' * (scale - i)
    c = (i/scale)*100
    dur = time.perf_counter() - start
    print("\r{:^3.0f}%[{}->{}]{:.2f}s".format(c,a,b,dur),end='')
    time.sleep(0.1)
print("\n"+"执行结束".center(scale//2,'-'))
```

#### 扩展

计时方法扩展： 计时方法适用各类需要统计时间的计算问题

进度条扩展： 在任何运行时间需要较长的程序中、希望提高用户体验的应用中增加进度条，提高人机交互体验

## Python标准库——random库

使用随机数的 Python 标准库，用于生成随机数

------

### 标准库

 随 Python 解释器自带，不需要安装，使用 import 调用

------

计算机产生的数据都是根据复杂运算得到，所以不能产生真正意义上的随机数，但是可以产生伪随机数

### 伪随机数

采用梅森旋转算法生成的（伪）随机序列中的元素

### random库常用函数

#### 基本随机数函数

------

##### 梅森旋转算法（**Mersenne twister**）

一个伪随机数发生算法。由松本真和西村拓士在1997年开发，基于有限二进制字段上的矩阵线性递归。可以快速产生高质量的伪随机数，修正了古典随机数发生算法的很多缺陷。

整个算法主要分为三个阶段：

第一阶段：获得基础的梅森旋转链；

第二阶段：对于旋转链进行旋转算法；

第三阶段：对于旋转算法所得的结果进行处理；

算法实现的过程中，参数的选取取决于梅森素数，故此得名。

##### 梅森素数

由梅森数而来。

所谓梅森数，是指形如2^p－1的一类数，其中指数p是素数，常记为Mp 。如果梅森数是素数，就称为梅森素数。

用因式分解法可以证明，若2^n－1是素数，则指数n也是素数；反之，当n是素数时，2^n－1（即Mp）却未必是素数。前几个较小的梅森数大都是素数，然而梅森数越大，梅森素数也就越难出现。

目前仅发现51个梅森素数，最大的是M82589933（即282589933－1），有24862048位。

------

##### 1.seed(a=None)

初始化给定的随机数种子，默认为当前系统时间

```python
random.seed(10)			# 产生种子10对应的序列
```

结果

```
不显示，此时序列已经产生，使用 random（）可以看到展示结果，种子10对应第一个是0.5714025946899135
```

##### 2.random()

生成一个 [0.0， 1.0) 之间的随机小数

```python
import random
random.seed(10)
random.random()
random.seed(10)
random.random()
```

结果

```
0.5714025946899135
0.5714025946899135
```

seed 相同，产生的序列相同，随机数相同

#### 扩展随机数函数

##### 3.randint(a, b)

生成一个 [a, b] 之间的整数

```python
random.randint(10, 100)
```

结果

```
83
```

##### 4.randrange(m, n[, k])

生成一个 [m, n) 之间以 k 为步长的随机整数

```python
random.randrange(10, 100, 10)
```

结果

```
10
70
80……
```

##### 5.getrandbits(k)

生成一个 k 比特长的随机整数

```python
random.getrandbits(16)
```

结果

```
13506
```

##### 6.uniform(a, b)

生成一个 [a, b] 之间的随机小数

```python
random.uniform(10, 100)
```

结果

```
51.632245728365426
```

##### 7.choice(seq)

从序列 seq 中随机选择一个元素

```python
random.choice([1,2,3,4,5,6,7,8,9])
```

结果

```
5
```

##### 8.shuffle(seq)

将序列 seq 中元素随机排列，返回打乱后的序列

```python
s = [1,2,3,4,5,6,7,8,9]
random.shuffle(s)
print(s)

# 等价于
import random ; s = [1,2,3,4,5,6,7,8,9] ; random.shuffle(s) ; print(s)
```

写在一行用 ; 隔开 

结果

```
[1, 4, 2, 6, 9, 5, 7, 8, 3]
```

具备使用随机数的能力

1. 能够利用随机数种子产生“确定”的伪随机数
2. 能够产生随机整数
3. 能够对序列类型进行随机操作

#### 实例 圆周率计算——蒙特卡罗方法

##### 一般数学公式

$$
\pi = \sum_{k=0}^\infty[\frac{1}{16^k}(\frac{4}{8k+1}-\frac{2}{8k+4}-\frac{1}{8k+5}-\frac{1}{8k+6}]
$$

（公式编辑语法使用 Ketax）

代码实现

```python
# CalPi1
pi = 0		# 初始值
N = 100		# 累加数量，即循环数
for k in range(N) :     # 公式
    pi += 1/pow(16,k)*(\        # \ 是换行符
       4/(8*k+1) - 2/(8*k+4) - \
       1/(8*k+5) - 1/(8*k+6))
print("圆周率值是：{}".format(pi))
```

结果

```
圆周率值是：3.141592653589793
```

##### 蒙特卡罗方法

Monte Carlo method，是一种计算方法。原理是通过大量随机样本，去了解一个系统，进而得到所要计算的值。

它诞生于上个世纪40年代美国的"曼哈顿计划"，名字来源于赌城蒙特卡罗，象征概率。

用蒙特卡罗方法计算圆周率π。

正方形内部有一个相切的圆，它们的面积之比是π/4。

现在，在这个正方形内部，随机产生10000个点（即10000个坐标对 (x, y)），计算它们与中心点的距离，从而判断是否落在圆的内部。如果这些点均匀分布，那么圆内的点应该占到所有点的 π/4，因此将这个比值乘以4，就是π的值。

代码实现

```python
# CalPi2
'''
1.设正方形内切圆为单位圆，圆心为原点，半径为1
2.取正方形第一象限内的小正方形，包含内切圆的四分之一3.向小正方形内撒点，落在圆里就是圆的面积，落在圆外的方形里就是方形面积，方形面积和扇形面积比为圆周率
'''
from random import random
from time import perf_counter       # 计时
DARTS = 1000*1000         # 撒点总量，当前区域中
hits = 0.0		# 圆内部点数量，目前的
start = perf_counter()	# 当前系统时间值
for i in range(1, DARTS+1):     # 循环撒点
    x, y = random(), random()   # 生成坐标值，单位圆所以取值在[0,1)
    dist = pow(x**2 + y**2, 0.5)    # 点到圆心距离
    if dist <= 1.0:     # 距离不大于半径，落在圆内
        hits = hits +1
pi = 4 * (hits/DARTS)
print("圆周率值是：{}".format(pi))
print("运行时间是：{:.5f}s".format(perf_counter()-start))
```

结果

```
圆周率值是：3.144072
运行时间是：1.42109s
（第二次运行）
圆周率值是：3.141508
运行时间是：1.32696s
```

##### 举一反三

1. 程序性能： 关注循环
2. 计算思维： 数学——计算
3. 特定图形面积，可用蒙特卡罗方法，工程计算中常用