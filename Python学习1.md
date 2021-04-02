# Python学习1


## 编程解决问题的步骤


1. 分析问题
分析问题的计算部分——想清楚
								   ——使用编程能够解决问题的哪一个计算需求
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

​                              ——华氏度转换为摄氏度

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
C = \frac{F-32}{1.8}
$$

$$
F = C\times1.8+32
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

| **and** | **as** | **assert** |
| :---: | :---: | :---: |
| **break** | **class** | **continue** |
| **def** | **del** | **elif** |
| **else** | **except** | **finally** |
| **for** | **from** | **global** |
| **if** | **import** | **in** |
| **is** | **lambda** | **None** |
| **nonlocal** | **not** | **or** |
| **pass** | **raise** | **return** |
| **try** | **while** | **with** |
| **yield** | **FALSE** | **TRUE** |

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
| 反向递减序号 | -5 | -4 | -3 | -2 | -1 |
| --- | :---: | :---: | :---: | :---: | :---: |
|  | 这 | 是 | 字 | 符 | ： |
| 正向递增序号 | 0 | 1 | 2 | 3 | 4 |

由左到右：正向


由结尾处到头部：反向


使用 [ ]  获取字符串中一个或多个字符


#### 字符串基本表达


##### 索引


返回字符串中单个字符   <字符串>[M]


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
"〇一二三四五六七八九十"[1:3:2]		# 一
"〇一二三四五六七八九十"[1::2]		    # 一三五七九
"〇一二三四五六七八九十"[::-1]			# 十九八七六五四三二一〇
```


##### 转义符 \ （反斜杠）


表示特定字符的本意

| 输入 | 输出 |
| :---: | :---: |
| "这里有个双引号(")" | 这里有个双引号(") |
| \\b | 回退 |
| \\n | 换行，光标移动到下行首 |
| \\r | 回车，光标移动到本行首 |

#### 字符串操作符
| 操作符及使用 | 描述 |
| :---: | :---: |
| x + y | 连接两个字符串 x 和 y |
| n _ x 或 x _ n | 复制n次字符串x |
| x in s | x 是 s 的子串，返回 True，否则 False |

##### 实例  获取星期字符串


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
| 函数及使用 | 描述 |
| :---: | :---: |
| len(x) | 长度，返回字符串x的长度，len("一二三456") = 6 |
| str(x) | 任意类型x所对应的字符串形式，str(1.23) = "1.23" |
| hex(x) | 整数x的十六进制小写形式字符串，hex(425) = "0x1a9" |
| oct(x) | 整数x的八进制小写形式字符串，oct(425) = "0o651" |
| chr(u) | u为Unicode编码，返回其对应的字符 |
| ord(x) | x为字符，返回其对应的Unicode编码 |

```python
'''
恺撒密码是古罗马恺撒大帝用来对军事情报进行加解密的算法，它采用了替换方法对信息中的每一个英文字符循环替换为字母表序列中该字符后面的第三个字符，即，字母表的对应关系如下：‪‬‪‬‪‬‪‬‪‬‮‬‫‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬

原文：A B C D E F G H I J K L M N O P Q R S T U V W X Y Z‪‬‪‬‪‬‪‬‪‬‮‬‫‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬

密文：D E F G H I J K L M N O P Q R S T U V W X Y Z A B C‪‬‪‬‪‬‪‬‪‬‮‬‫‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬

对于原文字符P，其密文字符C满足如下条件：C=(P+3) mod 26‪‬‪‬‪‬‪‬‪‬‮‬‫‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬

上述是凯撒密码的加密方法，解密方法反之，即：P=(C-3) mod 26‪‬‪‬‪‬‪‬‪‬‮‬‫‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬

假设用户可能使用的输入包含大小写字母a~zA~Z、空格和特殊符号，请编写一个程序，对输入字符串进行恺撒密码加密，直接输出结果，其中空格不用进行加密处理。使用input()获得输入。'''
P = input()
t = ""
for c in P:
    if "a" <= c <= "z":
        t += chr(ord("a")+((ord(c)-ord("a"))+3)%26)
    elif "A" <= c <= "Z":
        t += chr(ord("A")+((ord(c)-ord("A"))+3)%26)
    else:
        t += c
print(t)
```

结果

```
输入： python is an excellent language 5 哈哈哈
输出： sbwkrq lv dq hafhoohqw odqjxdjh 5 哈哈哈
```

#### 字符串处理方法

##### 方法：面向对象 编程中一个专有名词，特指[.**() 风格中的函数 .()**]()

方法本身也是函数，但是与对象有关

|          方法及使用          |                             描述                             |
| :--------------------------: | :----------------------------------------------------------: |
|         str.lower()          |    返回字符串的副本，全部字符小写， "AbC".lower() = "abc"    |
|         str.upper()          |    返回字符串的副本，全部字符大写，"AbC".upper() = "ABC"     |
|     str.split(sep=None)      | 返回一个列表，由str根据sep被分隔的部分组成， 即 按照指定字符分隔字符串为数组，"A,B,C".split(",") = ['A','B','C'] |
|        str.count(sub)        | 返回子串sub在str中出现的次数，"an apple a day".count('a') = 4 |
|    str.replace(old, new)     | 返回字符串str副本，所有old子串被替换为new子串，即替换字符串中特定字符，"python".replace("n","n123.io") = "python123.io" |
| str.center(width[,fillchar]) | 格式处理，字符串str根据宽度width居中，fillchar可选，"python".center(20, "=") = '=python=' |
|       str.strip(chars)       | 从str中去掉在其左侧和右侧chars中列出的字符，即去掉字符串两侧指定字符，"= python=".strip(" =np") = 'ytho' |
|        str.join(iter)        | 在iter变量除最后元素外每个元素后增加一个str，主要用于字符串分隔等， ",".join("12345") = '1,2,3,4,5' |

```python
'''
字符串分段组合
获得输入的一个字符串s，以字符减号(-)分割s，将其中首尾两段用加号(+)组合后输出。
'''
s = input()
ls = s.split("-")
print("{}+{}".format(ls[0], ls[-1]))
```

结果

```
输入：Alice-Bob-Charis-David-Eric-Flurry
输出：Alice+Flurry
```

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
3. <对齐>： 左对齐"<"  右对齐">" 居中对齐"^"
4. <宽度>：槽设定的输出宽度
5. <,>：数字的千位分隔符
6. <.精度>：浮点数小数精度或者字符串最大输出长度
7. <类型>：以什么类型将变量放入槽中整数类型 b, c, d, o, x, X    浮点数类型 e, E, f, %

前三个一组，后三个一组


```python
"{0:=^20}".format("PYTHON")
"{0:+>20}".format("BIT")
"{:10}".format("BIT")
```


结果


"=PYTHON="


放入槽中的format方法中的第0个参数以居中对齐方式显示，输出宽度20个字符，用 = 填充


"+++++++++++++++++BIT"


放入槽中的format方法中的第0个参数以右对齐方式显示，输出宽度20个字符，用 + 填充


"BIT       "


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

###### 槽的嵌套用法——星号三角形

读入一个整数N，N是奇数，输出由星号字符组成的等边三角形，要求：‪‬‪‬‪‬‪‬‪‬‮‬‫‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‫‬‮‬‪‬‪‬‪‬‪‬‪‬‮‬‪‬‭‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬ 

第1行1个星号，第2行3个星号，第3行5个星号，依次类推，最后一行共N的星号。‪‬‪‬‪‬‪‬‪‬‮‬‫‬‫‬‪‬‪‬‪‬‪‬‪‬‮‬‭‬‪‬

```python
n = eval(input())
for i in range(1,n+1,2):
    print("{0:^{1}}".format('*'*i, n))
    
# 等价写法
n = eval(input())
for i in range(1,n+1,2):
    print("{:^{}}".format('*'*i, n))
```

结果

```python
5
  *  
 *** 
*****
5
  *  
 *** 
*****
```

槽中可以嵌套槽，用来表示宽度、填充等含义。

##### 格式输出注意事项——输出超长怎么表示

```python
s='PYTHON'
print({0:3}".format(s))
```

结果

```
PYTHON
```

{0:3}表示输出的宽度是3，但如果字符串超过长度3，则以字符串长度显示。

### 数字类型


#### 整数类型


数学中的整数，带正负号 如+1 -1


可正可负，没有取值范围限制


```python
pow(x,y)			# 计算x的y次幂
pow(2,pow(2,15))
```


4种进制表示形式


1. 十进制：     1010，-127
2. 二进制：     以0b或者0B开头，如 0b010，-0B010
3. 八进制：     以0o或者0O开头，如 0o123，-0O123
4. 十六进制： 以0x或者0X开头，如 0x9a，-0X89

#### 浮点数类型


数学中的实数，带正负号、小数点，如  +1.0 -1.0


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
| 操作符及使用 | 描述 |
| :---: | :---: |
| x + y | 加 |
| x - y | 减 |
| x * y | 乘 |
| x / y | 除，浮点数形式，10/3 = 3.3333333 |
| x // y | 整数除，10//3 = 3 |
| + x | x 本身 |
| - y | y 的负值 |
| x % y | 余数，10%3 = 1 |
| x ** y | 幂运算， pow(x, y) |
|  | 当 y 是小数，开方运算， 4 ** 0.5 = 2 |

| 增强操作符及使用 | 描述 |
| :---: | :---: |
| x op= y | x = x op y  , op为二元操作符 |
| x += y | x = x + y |
| x -= y | x = x - y |
| x *= y | x = x * y |
| x /= y | x = x / y |
| x  //= y | x = x // y |
| x %= y | x = x % y |
| x **= y | x = x ** y |

#### 数值运算函数
| 函数及使用 | 描述 |
| :---: | :---: |
| abs(x) | 绝对值，abs(-10.01) = 10.01 |
| divmod(x, y) | 商余，同时输出商和余数， divmod(10, 3) = (3, 1) |
| pow(x, y [, z]) | 幂余，(x**y)%z，[..]表示参数z可省略， pow(3, pow(3, 99), 10000) = 4587， pow(4, 0.5) = 2 |
| round(x[, d]) | 四舍五入，d保留小数位，默认值为0， round(-10.123, 2) = -10.12 |
| max(a,b,c,...,n) | 最大值，max(1, 9, 4, 3, 5) = 9 |
| min(a,b,c,...,n) | 最小值，min(1, 9, 4, 3, 5) = 1 |
| int(x) | 强制类型转换为整数，int(123.45) = 123, int("123") = 123 |
| float(x) | 强制类型转换为浮点数， float(123) = 123.0, float("123") = 123.0 |
| complex(x) | 强制转换类型为复数，complex(4) = 4 + 0j |

#### 实例 天天向上系列

##### v1  1‰的力量

一年365天，每天进步1‰，累计进步多少

一年365天，每天退步1‰，累计退步多少

```python
dayup = pow(1.001, 365)
daydown = pow(0.999, 365)
print("向上：{:.2f}, 向下：{:.2f}".format(dayup, daydown))
```

结果

```
向上：1.44, 向下：0.69
```

##### v2  5‰和1%的力量

一年365天，每天进步5‰或1%，累计进步多少

一年365天，每天退步5‰或1%，累计剩下多少

```python
#天天向上 5‰和1%的力量
dayfactor = 0.005
dayup = pow(1+dayfactor, 365)
daydown = pow(1-dayfactor, 365)
print("向上：{:.2f}, 向下：{:.2f}".format(dayup, daydown))
```

结果

```
向上：6.17, 向下：0.16
```

##### v3  工作日的力量

一年365天，一周5个工作日，每天进步1%

一年365天，一周2个休息日，每天退步1%

```python
# 天天向上的力量
dayup = 1.0
dayfactor = 0.01
for i in range(365):
    if i % 7 in [6,0]:
        dayup = dayup*(1-dayfactor)
    else:
        dayup = dayup*(1+dayfactor)
        
print("工作日的力量：{:.2f}".format(dayup))
```

结果

```
工作日的力量：4.63
```

##### v4  工作日的努力

工作日模式要努力到什么水平，才能与每天努力1%一样

思路一： 数学思维，列公式

思路二： 暴力求解，用计算机模拟，用“笨办法”试错

```python
# 天天向上的力量-工作日的努力
def dayUP(df):
    dayup = 1
    for i in range(365):
        if i % 7 in [6, 0]:
            dayup = dayup * (1 - 0.01)
        else:
            dayup = dayup * (1 + df)
    return dayup
dayfactor = 0.01
while dayUP(dayfactor) < 37.78:
    dayfactor += 0.001
print("工作日的努力参数是: {:.3f}".format(dayfactor))
```

结果

```
工作日的努力参数是：0.019
```

### 组合数据类型

#### 理解

把一组数据当成一个数据来处理

让程序更好地组织一组数据

三种主流组合数据类型

#### 集合类型

多个元素的无序组合

##### 理解

1. 与数学中集合概念一直

2. 集合元素之间无序，每个元素唯一，不存在相同元素

3. 集合元素不可更改，不能是可变数据类型

   因为集合里面每一个元素不能重复，可变可能导致重复，所以必须是不可变数据类型

   不可变：整数、浮点数、复数、字符串、元组

##### 定义

1. 集合用 {} 表示，元素间用逗号分隔
2. 建立集合类型用 {} 或 set()
3. 建立空集合类型，必须使用 set()
4. 重点1： 每个元素唯一，不存在相同元素
5. 重点2： 集合元素之间无序

###### 使用 {} 建立集合

```python
A = {"python", 123, ("python", )}
```

print(A) 结果

```
{'python', 123, ('python',)}
```

###### 使用set() 建立集合

```python
B = set("pypy123")
```

print(B) 结果

```
{'p', '1', '3', '2', 'y'}
```

对比

```python
C = {"python", 123,"python", 123}
```

print(C) 结果

```
{'python', 123}
```

##### 集合操作符

|      操作符      |                   描述                   |
| :--------------: | :--------------------------------------: |
|      S \| T      |           并 ，返回一个新集合            |
|      S - T       |            差，返回一个新集合            |
|      S & T       |            交，返回一个新集合            |
|      S ^ T       | 补，返回一个新集合，不同时存在S和T的元素 |
| S <= T  或 S < T |       返回True/False，判断子集关系       |
| S >= T 或 S > T  |       返回True/False，判断包含关系       |

##### 集合增强操作符

| 操作符  |                 描述                  |
| :-----: | :-----------------------------------: |
| S \|= T | 更新集合S，包括在集合S和T中的所有元素 |
| S -= T  | 更新集合S，包括在集合S但不在T中的元素 |
| S &= T  | 更新集合S，包括同时在集合S和T中的元素 |
| S ^= T  | 更新集合S，包括集合S和T中的非相同元素 |

实例

```python
A = {"P", "Y", 123}
B = set("PYPY123")
print(A-B)
print(A&B)
print(B-A)
print(A|B)
print(A^B)
```

结果

```
{123}
{'P', 'Y'}
{'2', '3', '1'}
{'Y', '3', '1', 'P', 123, '2'}
{123, '2', '3', '1'}
```

##### 集合的处理方法

|   操作函数   |                       描述                        |
| :----------: | :-----------------------------------------------: |
|   S.add(x)   |                  x不在S中，加入                   |
| S.discard(x) |            移除S中元素x，x若不在不报错            |
| S.remove(x)  |       移除S中元素x，x若不在产生KeyError异常       |
|  S.clear()   |                  移除S中所有元素                  |
|   S.pop()    | 随机返回S的一个元素，更新S，若S空产生KeyError异常 |
|   S.copy()   |                返回集合S的一个副本                |
|    len(S)    |                   返回S元素个数                   |
|    x in S    |               在，True，不在，False               |
|  x not in S  |               不在，True，在，False               |
|    set(x)    |                强制转换为集合类型                 |

###### 遍历集合

for...in...方式

```python
A = {'p', 'y', 123}
for item in A:
    print(item, end='')
print('\n')
print(A)
```

结果

```python
y123p

{'y', 123, 'p'}
```

 while方式

```python
A = {'p', 'y', 123}
try:
    while True:
        print(A.pop(), end='')
except :
    pass
print('\n')
print(A)
```

结果

```python
123py

set()	# 空集
```

##### 应用

###### 包含关系比较

```python
>>>'p' in {'i', 123}
False
>>>'p' >= ''
True
```

###### 数据去重

利用元素不能重复的特点

```python
ls = ['s', 'p', 'p', 'y', 123, 123]
s = set(ls)
print(s)
lt = list(s)	# 保留原数据类型
print(lt)
```

结果

```
{'s', 123, 'p', 'y'}
['s', 123, 'p', 'y']
```

#### 序列类型

##### 理解

###### 具有先后关系的一组元素

1. 序列是一维元素向量，元素类型可以不同

2. 类似数学元素序列：

   
   $$
   s_0, s_1,...,s_{n-1}
   $$
   
3. 元素间由序号引导，通过下标访问序列的特定元素

4. 序列是一个基类类型，不直接使用，而是使用序列类型的衍生——字符串类型、元组类型、列表类型

###### 序号的定义

1. 元素存在正向递增序号的索引关系
2. 元素存在反向递减序号的索引关系

序列类型通用操作符

```python
x in s
x not in s
s + t
s*n/n*s
s[i]
s[i: j]/s[i: j: k]
```

逆序/取反

```python
ls[::-1]
```

序列类型通用函数和方法

```python
len(s)
min(s)
max(s)
s.index(x)
s.index(x, i, j)
s.count(x)
```

##### 元组

######  理解

序列类型的一种扩展，将元素进行有序的排列，用（）组织

1. 是一种序列类型，一旦创建就不能被修改

2. 使用小括号()或tuple()创建，元素间用逗号‘，’分隔

3. 可以使用或不使用小括号

   ```python
   def func():
       return 1,2
   ```

   1,2 是元组类型

###### 例子

```python
>>>creature = 'cat', 'dog', 'tiger', 'human'
>>>creature
('cat', 'dog', 'tiger', 'human')
>>>color = (0x001100, 'blue', creature)
>>>color
(4352, 'blue', ('cat', 'dog', 'tiger', 'human'))
```

继承了序列类型的全部通用操作

操作后不能修改，因此没有特殊操作

```python
>>>creature = 'cat', 'dog', 'tiger', 'human'
>>>creature[::-1]
('human', 'tiger', 'dog', 'cat')
```

creature[::-1]：不改变原有creature变量的值，而是生成新元组值

```python
>>>color = (0x001100, 'blue', creature)
>>>color[-1][2]
'tiger'

>>>color[-2][2]
'u'
```

##### 列表类型

###### 理解

是序列类型的一种扩展，十分常用

1. 是一种序列类型，创建后可以随意修改
2. 使用方括号[]或list()创建，元素间用逗号','分隔
3. 列表中各元素类型可以不同，无长度限制
4. 由0个或多个数据组成的有序序列


```python
[元素1, 元素2, ……, 最后一个元素]
```


用保留字 in 判断一个元素是否在列表中


```python
TempStr[-1] in ['C', 'c']	#判断TempStr赋值后的最后一个字符是不是C/c
```

###### 例子

```python
>>>ls = ['cat', 'dog', 'tiger', 1024]	# 说明1
>>>ls
['cat', 'dog', 'tiger', 1024]
>>>lt = ls	# 说明2
>>>lt
['cat', 'dog', 'tiger', 1024]
```

说明1： 使用[]，实际创建了一个新的序列

说明2： 赋值只是赋给了一个新的名字，没有创建新序列，相当于重新命名

###### 常用操作

|       函数       |             描述             |
| :--------------: | :--------------------------: |
|    ls[i] = x     |       第i个元素替换为x       |
| ls[i: j: k] = lt |        ls切片后取名lt        |
|    del ls[i]     |        删除第i个元素         |
| del ls[i: j: k]  | 删除第i到第j以k为步长的元素  |
|     ls += lt     | 更新ls，将lt元素加到列表ls后 |
|     ls *= n      |     更新ls，元素重复n次      |

例子

```python
>>>ls = ['cat', 'dog', 'tiger', 1024]
>>>ls[1: 2] = [1, 2, 3, 4]
['cat', 1, 2, 3, 4, 'tiger', 1024]
>>>del ls[::3]
[1, 2, 4, 'tiger']
>>>ls *= 2
[1, 2, 4, 'tiger', 1, 2, 4, 'tiger']
```

运算会作用到列表本身，所以列表里面的元素会相应变化

|      方法       |             描述             |
| :-------------: | :--------------------------: |
|  ls.append(x)   |      列表最后增加元素x       |
|   ls.clear()    |       删除列表所有元素       |
|    ls.copy()    | 生成新列表，赋值ls中所有元素 |
| ls.insert(i, x) |        第i位增加元素x        |
|    ls.pop(i)    |     取出第i位元素并删除      |
|  ls.remove(x)   |    出现的第一个元素x删除     |
|  ls.reverse()   |             反转             |

例子

```python
>>>ls = ['cat', 'dog', 'tiger', 1024]
>>>ls.append(1234)
['cat', 'dog', 'tiger', 1024, 1234]
>>>ls.insert(3, "human")
['cat', 'dog', 'tiger', 'human', 1024, 1234]
>>>ls.reverse()
[1234, 1024, 'human', 'tiger', 'dog', 'cat']
```

##### 序列类型应用场景

###### 序列主要应用场景是***数据表示***

1. 元组用于元素不改变的，更多用于固定搭配场景
2. 列表更加灵活，是最常用的序列类型
3. 最主要作用： 表示一组有序数据，进而操作它们

元素遍历 for item in ls / for item in tp

###### 数据保护

如果不希望数据被程序改变，转换成元组类型

```python
>>>ls = ['cat', 'dog', 'tiger', 1024]
>>>lt = tuple(ls)
>>>lt
('cat', 'dog', 'tiger', 1024)
```

无论程序后续怎么操作，数据值都不会改变

合作编程时候使用较多

##### 实例 基本统计值计算

###### 问题分析

需求： 给出一组数，有个概要理解

做法： 基本统计值分析

1.  总数： len()
2. 求和: for...in
3. 平均值: 求和/总数
4. 方差：根据公式求解
5. 中位数： 排序，然后 奇数找中间一个，偶数找中间2个取平均数
6. ……

###### 代码

不确定数量的用户输入

```python
#CalStatistics V1
def getNum():	#获取用户不定长度的输入
    nums = []
    iNumStr = input('请输入数字（回车退出）：')
    while iNumStr != "":
        nums.append(eval(iNumStr))
        iNunStr = input('请输入数字（回车退出）：')
    return nums
```

平均值

```python
def mean(numbers):
    s = 0.0
    for num in numbers:
        s = s + num
    return s / len(numbers)
```

方差

```python
def dev(numbers, mean):
    sdev = 0.0
    for num in numbers:
        sdev = sdev + (num - mean)**2
    return pow(sdev / (len(numbers)-1), 0.5)
```

中位数（需要排序）

```python
def median(numbers):
    sorted(numbers)		#排序函数
    size = len(numbers)
    if size % 2 == 0:
        med = (numbers[size//2-1] + numbers[size//2])/2		#偶数，取中间两个平均值
    else :
        med = numbers[size//2]		#奇数，取中间
    return med
```

调用

```python
n = getNum()
m = mean(n)
print("平均值:{},方差:{:.2},中位数:{}。".format(m, dev(n,m),median(n)))
```

掌握

1. 获得多数据输入的方法
2. 使用多个函数，通过参数传递方式，将复杂功能分隔为较小的功能，再将小功能块组织起来完成用户需求

###### 举一反三

技术能力方面的掌握和扩展

1. 获取多个数据： 从控制台获取多个不确定数据的方法，使用while
2. 分隔多个函数： 模块化设计方法
3. 充分利用函数： Python提供内置函数（几十个）

#### 字典类型

##### 理解

“映射”： 一种键（索引）和值（数据）的对应

映射类型由用户为数据定义索引

索引类似为属性，索引对应的数据就是属性的内容

字典类型是映射的体现，是映射的一种衍生形式

##### 定义

字典类型通过键值对来进行数据索引的扩展

1. 键值对： 键是数据索引的扩展
2. 字典是键值对的集合，键值对之间无序
3. 使用大括号 { } 和 dict( ) 创建，键值对用冒号 : 表示

```python
{<键1>:<值1>, <键2>:<值2>,..., <键n>:<值n>}
```

##### 用法

1. <字典变量> = {<键1>:<值1>, <键2>:<值2>,..., <键n>:<值n>}
2. <值> = <字典变量>[<键>]
3. <字典变量>[<键>] = <值>

——[ ] 用来向字典变量中索引或增加元素

###### 例子

```python
>>>d = {'中国':'北京', '美国':'华盛顿', '法国':'巴黎'}
>>>d
{'中国': '北京', '美国': '华盛顿', '法国': '巴黎'}
>>>d["中国"]
'北京'
>>>de = {} ; type(de)	#函数type(x)检测变量x类型
<class 'dict'>
>>>a = set() ; type(a)		#对比集合类型，生成空集合
<class 'set'>
```

##### 操作

|     函数或方法      |                    描述                    |
| :-----------------: | :----------------------------------------: |
|      del d[k]       |            删除键k对应的数据值             |
|       k in d        |                 键k是否在d                 |
|      d.keys()       |              返回所有的键信息              |
|     d.values()      |              返回所有的值信息              |
|      d.items()      |            返回所有的键值对信息            |
| d.get(k, <default>) | 键k存在，返回相应值，不在则返回<default>值 |
| d.pop(k, <default>) |  键k存在，取出相应值，不在返回<default>值  |
|     d.popitem()     |      随机取一个键值对，以元组形式返回      |
|      d.clear()      |               删除所有键值对               |
|       len(d)        |                  返回个数                  |

例子

```python
>>>d = {'中国':'北京', '美国':'华盛顿', '法国':'巴黎'}
>>>'中国' in d
True
>>>d.keys()
dict_keys(['中国', '美国', '法国'])
>>>d.values()
dict_values(['北京', '华盛顿', '巴黎'])
```

d.keys() d.values() 不返回列表类型，返回的是字典的keys类型、values类型，可以用for...in...遍历，不能当做列表类型操作

```python
>>>d.get('中国', '伊斯兰堡')
'北京'
>>>d.get('巴基斯坦', '伊斯兰堡')
'伊斯兰堡'
```

##### 字典类型的应用场景

以键值对形式表达映射关系

利用键进行元素遍历 for k in d:

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


用保留字 **_if  elif  else_**  构成条件判断的分支结构


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
| 操作符 | 描述 |
| :---: | :---: |
| < | 小于 |
| < = | 小于等于 |
| > = | 大于等于 |
| > | 大于 |
| = = | 等于 |
| ! = | 不等于 |
| x and y | 逻辑与 |
| x or y | 逻辑或 |
| not x | 逻辑非 |

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


#### 实例 BMI指数


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


类似数学中的函数  <函数名>（<参数>）


```python
print("123")		#打印输出”123“
eval(TempStr[0:-1])		#TempStr[0:-1] 是参数
```


#### input()


输入函数，   <变量> = input（<提示信息字符串>）


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

#### 函数是一段具有特定功能的、可重用的语句组，表现为一段代码


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

### 代码复用

把代码当成资源进行抽象

#### 代码资源化

程序代码是一种用来表达计算的“资源”

#### 代码抽象化

使用函数等方法对代码赋予更高级别的定义

#### 代码复用

同一份代码在需要时可以被重复使用，需要抽象

使用函数和对象，通过封装，将功能进一步抽象

函数和对象是代码复用的两种主要形式

函数：将代码命名，在代码层面建立初步抽象

对象：属性和方法，在函数之上再次组织进行抽象

在面向对象的程序设计中具体理解

在抽象基础上，进行模块化设计

#### 模块化设计

核心思想：分而治之

通过函数或对象封装将程序划分为模块及模块间的表达

具体包括：主程序、子程序、子程序之间的关系

一般将子程序看做模块，主程序看做模块与模块之间的关系

##### 紧耦合模式

两个部分之间交流很多，无法独立存在

##### 松耦合模式

两个部分之间交流较少，之间有非常清晰简单的接口，可以独立存在

编程时，使用函数将一段代码与代码的其他部分分开

函数的参数和返回值就是这段函数与其他代码之间的交流通道

交流通道越少越清晰，函数复用可能性越高

##### 适用原则

模块（函数）内部尽量紧耦合，通过局部变量进行数据传输

模块（函数）之间尽量松耦合，尽可能减少函数参数和传递值

### 函数递归

调用函数自身

类似数学归纳法

#### 两个关键特征

##### 链条

计算过程存在递归有序的链条

##### 基例

存在一个或多个不需要再次递归的基例

#### 实例 递归的实现

$$
n! = \begin{cases}
1 &\text{}n = 0\\
n(n-1)! &\text{}otherwise
\end{cases}
$$

##### 分析

使用函数 + 分支语句

1. 递归本身是一个函数，需要函数定义方式描述
2. 函数内部，采用分支语句对输入参数判断
3. 基例和链条，分别编写对应代码

##### 代码（定义函数通过调用使用）

```python
def fact(n):
    if n == 0:
        return 1
    else :
        return n*fact(n-1)
```

##### 递归实例 字符串反转

###### 使用切片

```python
s[::-1]
```

###### 使用递归

```python
def rvs(s):
    # 判断基例——最小的字符串——空——反转是自身
    if s == "":
        return s
    else :
    # 构造链条
        return rvs(s[1:]+s[0])
```

##### 递归实例 斐波那契数列

$$
F(n) = \begin{cases}
1 &\text{}n=1\\
1 &\text{}n=2\\
F(n-1)+F(n-2) &\text{}otherwise
\end{cases}
$$

```python
def f(n):
    if n == 1 or n == 2:
        return 1
    else :
        return f(n-1)+f(n-2)
```

##### 汉诺塔

三根柱子，一根柱子从下往上按照大小顺序摞着64片黄金圆盘，把圆盘从下面开始按大小顺序重新摆放在另一根柱子上，按规定，小圆盘上不能放大圆盘，三根柱子之间一次只能移动一个圆盘

```python
count = 0
def hanoi(n, src, dst, mid):
    global count
    if n == 1:
        print("{}:{}->{}".format(1,src,dst))
        count += 1
    else :
        hanoi(n-1, src, mid, dst)
        print("{}:{}->{}".format(n,src,dst))
        count += 1
        hanoi(n-1, mid, src, dst)
hanoi(3, "A", "B", "C")
print(count)
```

结果

```
1:A->B
2:A->C
1:B->A
3:A->B
1:C->B
2:C->A
1:B->C
7
```

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

#### 计数循环 for...in range()


按照一定次数循环执行一组语句


```python
for <循环变量> in range (<参数>):
	<被循环执行的语句>
```


<循环变量>： 每次循环的计数，0 ~ （<次数> - 1）


range()： 产生数字序列（循环计数序列），产生循环


range(N)：  0 到 N-1 整数序列


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


#### 字符串遍历循环 for c in s...


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


#### 列表遍历循环 for item in ls...


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


#### 文件遍历循环


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


##### 单层循环实例


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


##### 多层循环实例


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

## 文件

### 理解

类型

使用

打开文件

关闭文件

文件内容的读取

数据的文件写入


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


1. tutle.xxx：是一种编码风格

2. 库引用——扩充Python程序功能的方式

  import <库名>
  <库名>.<函数名>(<函数参数>)
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


1. 库引用方法——from 配合 import使用```python
from <库名> import <函数名>
from <库名> import *
<函数名>(<函数参数>)
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
import <库名> as <库别名>
<库别名>.<函数名>(<函数参数>)
2. 优点： 给调用的外部库关联一个更短、更适合自己的名字； 冗余少，避免函数重名              


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


      （-∞， 0）：海龟向左行进


y轴（0， +∞）：海龟向上行进


      （-∞， 0）：海龟向下行进


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


###### turtle.right(angle)  相对度数


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


                               0 - 1（小数）


turtle库默认用小数值表示颜色


```python
turtle.colormode(1.0)			#RGB小数值模式
turtle.colormode(255)			#RGB整数值模式
```


#### 画笔控制函数


1. 画笔操作后一直有效，一般成对出现

   #####  turtle.penup()

   别名：turtle.pu() 抬起画笔，海龟在飞行

   ##### turtle.pendown()

   别名：turtle.pd() 落下画笔，海龟在爬行

2. 笔画设置后一直有效，直至下次重新设置

   ##### turtle.pensize(width)

   别名 turtle.width(width)  画笔宽度，海龟的腰围

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


'Sun Mar  7 17:51:42 2021'


#### gmtime()


获取当前时间，表示为计算机可处理的时间格式


```python
time.gmtime()
```


结果

```
time.struct_time(tm_year=2021, tm_mon=3, tm_mday=7, tm_hour=9, tm_min=54, tm_sec=14, tm_wday=6, tm_yday=66, tm_isdst=0)
```


### 时间格式化


将时间以合理方式展示出来，类似字符串的，也需要展示模板，由特定格式化控制符组成


将计算机内部时间中表达的年月日时分秒等与时间有关的信息用变量形式合理组合并合理输出，通过控制来表达输出格式


#### strftime(tpl, ts)


tpl： 格式化模板字符串，用来定义输出效果


ts：  计算机内部时间类型变量


```python
t = time.gmtime()
time.strftime("%Y-%m-%d %H:%M:%S",t)
```


结果

```
'2021-03-07 10:04:13'
```

| 格式化字符串 | 时期/时间说明 | 值范围 |
| :---: | :---: | :---: |
| %Y | 年份 | 0000~9999，如1900 |
| %m | 月份 | 01~12 |
| %B | 月份名称 | January~December |
| %b | 月份名称缩写 | Jan~Dec |
| %d | 日期 | 01~31 |
| %A | 星期 | Monday~Sunday |
| %a | 星期缩写 | Mon~Sun |
| %H | 小时（24h制） | 00~23 |
| %I | 小时（12h制） | 01~12 |
| %p | 上/下午 | AM, PM |
| %M | 分钟 | 00~59 |
| %S | 秒 | 00~59 |

#### strptime(str, tpl)


str： 字符串形式的时间值


tpl： 格式化模板字符串，用来定义输入效果


```python
timeStr = '2018-01-26 12:55:20'
time.strptime(timeStr, "%Y-%m-%d %H:%M:%S")
```


结果

```
time.struct_time(tm_year=2018, tm_mon=1, tm_mday=26, tm_hour=12, tm_min=55, tm_sec=20, tm_wday=4, tm_yday=26, tm_isdst=-1)
```


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

```
7.290818217000037
```


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

我自己喜欢的排版

```python
import time as t
scale = 50
start = t.perf_counter()
for i in range(scale+1):
    a = "*" * i
    b = "." * (scale-i)
    c = int(i/scale * 100)			# 强制转换整数，对应百分数的输出形式{:d}
    dur = t.perf_counter() - start
    print("\r{:d}%[{}->{}]{:.2f}s".format(c,a,b,dur), end="")
    t.sleep(0.1)
print("执行结束".center(scale//2, "-"))
```

#### 扩展


计时方法扩展： 计时方法适用各类需要统计时间的计算问题


进度条扩展： 在任何运行时间需要较长的程序中、希望提高用户体验的应用中增加进度条，提高人机交互体验


## Python标准库——random库


使用随机数的 Python 标准库，用于生成随机数

---

### 标准库


随 Python 解释器自带，不需要安装，使用 import 调用

---

计算机产生的数据都是根据复杂运算得到，所以不能产生真正意义上的随机数，但是可以产生伪随机数


### 伪随机数


采用梅森旋转算法生成的（伪）随机序列中的元素


### random库常用函数


#### 基本随机数函数

---

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


用因式分解法可以证明，若2n－1（即Mp）却未必是素数。前几个较小的梅森数大都是素数，然而梅森数越大，梅森素数也就越难出现。


目前仅发现51个梅森素数，最大的是M82589933（即282589933－1），有24862048位。

---

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
2. 特定图形面积，可用蒙特卡罗方法，工程计算中常用

## 综合实例——绘制七段数码管

### 基本思路

步骤1：绘制单个数字对应的数码管

步骤2：获得一串数字，绘制对应的数码管

步骤3：获得当前系统时间，绘制对应的数码管

```python
import turtle, time
def drawGap():			# 美化，线条间加一定间隔
    turtle.penup()
    turtle.fd(5)
    
def drawLine(draw):     # 绘制单段数码管
    drawGap()
    turtle.pendown() if draw else turtle.penup()
    turtle.fd(40)
    drawGap()
    turtle.right(90)
    
def drawDigit(digit):   # 根据数字绘制七段数码管
    drawLine(True) if digit in [2,3,4,5,6,8,9] else drawLine(False)
    drawLine(True) if digit in [0,1,3,4,5,6,7,8,9] else drawLine(False)
    drawLine(True) if digit in [0,2,3,5,6,8,9] else drawLine(False)
    drawLine(True) if digit in [0,2,6,8] else drawLine(False)
    turtle.left(90)
    drawLine(True) if digit in [0,4,5,6,8,9] else drawLine(False)
    drawLine(True) if digit in [0,2,3,5,6,7,8,9] else drawLine(False)
    drawLine(True) if digit in [0,1,2,3,4,7,8,9] else drawLine(False)
    turtle.left(180)
    turtle.penup()      # 为绘制后续数字确定位置
    turtle.fd(20)       # 为绘制后续数字确定位置
    
def drawDate(date):     # 获取要输出的数字
    turtle.pencolor("red")
    for i in date:
        if i == '-':
            turtle.write("年",font=("Arial", 18, "normal"))
            turtle.pencolor("green")
            turtle.fd(40)
        elif i == '=':
            turtle.write("月",font=("Arial", 18, "normal"))
        elif i == '+':
            turtle.write("日",font=("Arial", 18, "normal"))
        else:
            drawDigit(eval(i))      # 通过eval()函数将数字变为整数
            
def main():             # 设置主函数main来设置初始值
    turtle.setup(800, 350, 200, 200)
    turtle.penup()
    turtle.fd(-300)
    turtle.pensize(5)
    drawDate(time.strftime("%Y-%m=%d+", time.gmtime()))
    turtle.hideturtle()
    turtle.done()
    
main()
```
### 举一反三

1. 理解方法思维
模块化思维： 确定模块接口，封装功能
规则化思维： 抽象过程为规则，计算机自动执行
化繁为简： 将大功能变为小功能组合，分而治之

1. 应用问题的扩展
绘制带小数点的七段数码管
带刷新的时间倒计时效果
绘制高级的数码管

## 第三方库-PyInstaller库

使用前需要额外安装

官网： http://www.pyinstaller.org

### 安装方法

cmd (command)命令行 ，运行 pip 指令

```c
pip install pyinstaller
```

### 简单使用

源代码目录下，运行 cmd 

```c
pyinstaller -F <文件名.py>
```

生成三个新目录： build、pycache、dist

 build、pycache 可以删除不影响

dist里面的 .exe 文件为可执行文件

### 常用参数

|        参数         |                描述                |
| :-----------------: | :--------------------------------: |
|         -h          |              查看帮助              |
|       --clean       |      清理打包过程中的临时文件      |
|    -D， --onedir    |       默认值，生成dist文件夹       |
|    -F, --onefile    | 在dist文件夹中只生成独立的打包文件 |
| -i <图标文件名.ico> | 指定打包程序使用的图标（icon）文件 |

#### 实例 源代码关联图标打包

```python
pyinstaller -i bird3.ico -F PythonDraw.py
```

### 综合实例 科赫雪花小包裹

分形几何： 一种迭代的几何图形，广泛存在于自然界中

分形几何中有一种特殊曲线——科赫曲线，也叫雪花曲线

#### 分析

1. 递归思想

   函数 + 分支	def koch(size, n) :

2. 递归链条

   线段的组合	for angle in [0, 60, -120, 60] -> turtle.left(angle) koch(size/3, n-1)

3. 递归基例

   初始线段	n == 0 -> turtle.fd(size)

#### 代码

##### koch曲线

```python
# KochDrawv1
import turtle
def koch(size, n):
    if n == 0:
        turtle.fd(size)
    else :
        for angle in [0, 60, -120, 60]:
            turtle.left(angle)
            koch(size/3, n-1)
def main():
    turtle.setup(800, 400)
    turtle.penup()
    turtle.goto(-300, -50)
    turtle.pendown()
    turtle.pensize(2)
    koch(600, 3)	# 3阶科赫曲线，阶数
    turtle.hideturtle()
main()
```

##### 科赫雪花

```python
# KochDrawv2
import turtle
def koch(size, n):
    if n == 0:
        turtle.fd(size)
    else :
        for angle in [0, 60, -120, 60]:
            turtle.left(angle)
            koch(size/3, n-1)
def main():
    turtle.setup(600, 600)
    turtle.penup()
    turtle.goto(-200, 100)
    turtle.pendown()
    turtle.pensize(2)
    level = 3	# 3阶科赫曲线，阶数
    for i in range(2):
        koch(400, level)
        turtle.right(120)
    koch(400, level)
    turtle.hideturtle()
main()
```

#### 举一反三

##### 绘制条件扩展

1. 修改分形几何绘制阶数
2. 修改基本定义及旋转角度
3. 修改绘制基础框架图形

##### 分形几何千千万

1. 康托尔集
2. 谢尔宾斯基三角形
3. 门格海绵
4. 龙形曲线
5. 空间填充曲线

##### 深入理解函数递归的思想

## 第三方库——jieba库

### 基本

优秀的中文分词第三方库

中文文本之间每个汉子是连续书写的，需要通过特殊手段（即分词）获得单个的词语

#### 安装

pip install jieba

#### 分词原理

1. 通过中文词库确定汉字之间的关联概率
2. 汉字间概率大的组成词组，形成分词结果
3. 除了分词，还可以添加自定义词组

#### 使用

##### 精确模式

把文本精确的切分开，不存在冗余单词，最常用

##### 全模式

把文本中所有可能的词语都扫描出来，有冗余

##### 搜索引擎模式

在精确模式基础上，对长词再次切分，特定场合用的多

#### 常用函数

|            函数             |                    描述                     |
| :-------------------------: | :-----------------------------------------: |
|        jieba.lcut(s)        | 精确模式，返回一个列表类型的分词结果（例1） |
| jieba.lcut(s, cut_all=True) |                   全模式                    |
|  jieba.lcut_for_search(s)   |                  搜索引擎                   |
|      jieba.add_word(w)      |             向分词词典增加新词w             |

例1

```python
>>>jieba.lcut('中国是一个伟大的国家')
['中国','是'，'一个','伟大','的','国家']
```

例2

```python
>>>jieba.lcut('中国是一个伟大的国家',cut_all=True)
['中国','国是',''是'，'一个','伟大','的','国家']
```

例3

```python
>>>jieba.lcut_for_search('中华人民共和国是伟大的')
['中华','华人','人民','共和','共和国','中华人民共和国','是','伟大','的']
```

#### 要点

jieba.lcut(s)

精确处理分词并返回列表

### 实例 文本词频统计

#### 问题分析

需求

一篇文章，出现了哪些词？哪些词出现得最多？

#### 英文文本 Hamlet

```python
#CalHamletV1
def getText():
    #读取文本
    txt = open('Hamlet.txt', 'r').read()
    #小写处理
    txt = txt.lower()
    #替换特殊符号为空格
    for ch in '|"#$%&()+_-,/\:;<=>?@[\\]^{}~':
        txt = txt.replace(ch, ' ')
    return txt

hamletTxt = getText()
words = hamletTxt.split()
counts = {}
#遍历所有单词并记录对应出现次数
for word in words:
    counts[word] = counts.get(word,0) + 1
#列表的sort方法，对列表按照键值对的第2个元素从大到小排序
items = list(counts.items())
items.sort(key=lambda x:x[1], reverse=True)
#前10个出现最多的单词和对应次数打印    
for i in range(10):
    word, count = items[i]
    print('{0:<10}{1:>5}'.format(word, count))
```

比价复杂的是 items.sort 方法和 lambda函数 的使用，常用搭配，自学

结果

```python

```

#### 中文文本 《三国演义》人物出场统计

##### 基础版

```python
#CalThreeKingdomsV1
import jieba
txt = open('threekindoms.txt', 'r', encoding='utf-8').read()
words = jieba.lcut(txt)
counts = {}
for word in words:
    if len(word) == 1:
        continue
    else :
        counts[word] = counts.get(word,0) + 1
items = list(counts.items())
items.sort(key=lambda x:x[1], reverse=True)
for i in range(15):
    word, count = items[i]
    print('{0:<10}{1:>5}'.format(word, count))
```

结果

```

```

人物出场次数的目标有差距，需要调整

词频统计基础上面向问题改造

对一些具有相同意义的词关联上，不是人名的排除

##### 升级版

```python
#CalThreeKingdomsV2
import jieba
#多次运行基础版，找到排除词加入
excludes = {"将军","却说","荆州","二人","不可","不能","如此"}
txt = open("threekingdoms.txt", "r", encoding='utf-8').read()
words  = jieba.lcut(txt)
counts = {}
for word in words:
    if len(word) == 1:
        continue
    elif word == "诸葛亮" or word == "孔明曰":
        rword = "孔明"
    elif word == "关公" or word == "云长":
        rword = "关羽"
    elif word == "玄德" or word == "玄德曰":
        rword = "刘备"
    elif word == "孟德" or word == "丞相":
        rword = "曹操"
    else:
        rword = word
    counts[rword] = counts.get(rword,0) + 1
for word in excludes:
    del counts[word]
items = list(counts.items())
items.sort(key=lambda x:x[1], reverse=True) 
for i in range(10):
    word, count = items[i]
    print ("{0:<10}{1:>5}".format(word, count))
```

#### 举一反三

对其他的文本进行词频分析，找到重点

绘制词云