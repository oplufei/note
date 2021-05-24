# 规则

## requests库

### 安装

pip install requests

### get()方法

r = requests.get(url, params=None, **kwargs)

url：拟获取页面的url链接

params：url中的额外参数，字典或字节流格式，可选

kwargs： 12个控制访问的参数

```python
def get(url, params=None, **kwargs):
    '''
    Sends a GET request.
    
    :param url: URL for the new :class:'Request' object.
    :param params: (optional) Dictionary or bytes to be set in the query string for the 
    :param \*\*kwargs:
    '''
kwargs.setdefault('allow_redirects', True)
return request('get', url, params=params, **kwargs)
```

get方法使用request方法封装

Response对象： 包含爬虫（服务器资源）返回的内容

Request对象： 向服务器请求资源

### 操作

|        属性         |                       描述                       |
| :-----------------: | :----------------------------------------------: |
|    r.status_code    | HTTP请求的返回状态，200表示连接成功，404表示失败 |
|       r.text        |  HTTP响应内容的字符串形式，即 url对应的页面内容  |
|     r.encoding      |      从HTTP header中猜测的响应内容编码方式       |
| r.apparent_encoding | 从内容中分析出的响应内容编码方式（备选编码方式） |
|      r.content      |             HTTP响应内容的二进制形式             |

#### 例子

```python
>>>import requests
>>>r = requests.get('http://www.baidu.com')
>>>print(r.status_code)
200
>>>type(r)
<class 'requests.models.Response'>
>>>r.headers
{'Cache-Control': 'private, no-cache, no-store, proxy-revalidate, no-transform', 'Connection': 'keep-alive', 'Content-Encoding': 'gzip', 'Content-Type': 'text/html', 'Date': 'Fri, 02 Apr 2021 13:45:58 GMT', 'Last-Modified': 'Mon, 23 Jan 2017 13:28:24 GMT', 'Pragma': 'no-cache', 'Server': 'bfe/1.0.8.18', 'Set-Cookie': 'BDORZ=27315; max-age=86400; domain=.baidu.com; path=/', 'Transfer-Encoding': 'chunked'}
>>>r.text
'<!DOCTYPE html>\r\n<!--STATUS OK--><html> <head><meta http-equiv=content-type content=text/html;charset=utf-8><meta http-equiv=X-UA-Compatible content=IE=Edge><meta content=always name=referrer><link rel=stylesheet type=text/css href=http://s1.bdstatic.com/r/www/cache/bdorz/baidu.min.css><title>ç\x99¾åº¦ä¸\x80ä¸\x8bï¼\x8cä½\xa0å°±ç\x9f¥é\x81\x93</title></head> <body link=#0000cc> <div id=wrapper> <div id=head> <div class=head_wrapper> <div class=s_form> <div class=s_form_wrapper> <div id=lg> <img hidefocus=true src=//www.baidu.com/img/bd_logo1.png width=270 height=129> </div> <form id=form name=f action=//www.baidu.com/s class=fm> <input type=hidden name=bdorz_come value=1> <input type=hidden name=ie value=utf-8> <input type=hidden name=f value=8> <input type=hidden name=rsv_bp value=1> <input type=hidden name=rsv_idx value=1> <input type=hidden name=tn value=baidu><span class="bg s_ipt_wr"><input id=kw name=wd class=s_ipt value maxlength=255 autocomplete=off autofocus></span><span class="bg s_btn_wr"><input type=submit id=su value=ç\x99¾åº¦ä¸\x80ä¸\x8b class="bg s_btn"></span> </form> </div> </div> <div id=u1> <a href=http://news.baidu.com name=tj_trnews class=mnav>æ\x96°é\x97»</a> <a href=http://www.hao123.com name=tj_trhao123 class=mnav>hao123</a> <a href=http://map.baidu.com name=tj_trmap class=mnav>å\x9c°å\x9b¾</a> <a href=http://v.baidu.com name=tj_trvideo class=mnav>è§\x86é¢\x91</a> <a href=http://tieba.baidu.com name=tj_trtieba class=mnav>è´´å\x90§</a> <noscript> <a href=http://www.baidu.com/bdorz/login.gif?login&amp;tpl=mn&amp;u=http%3A%2F%2Fwww.baidu.com%2f%3fbdorz_come%3d1 name=tj_login class=lb>ç\x99»å½\x95</a> </noscript> <script>document.write(\'<a href="http://www.baidu.com/bdorz/login.gif?login&tpl=mn&u=\'+ encodeURIComponent(window.location.href+ (window.location.search === "" ? "?" : "&")+ "bdorz_come=1")+ \'" name="tj_login" class="lb">ç\x99»å½\x95</a>\');</script> <a href=//www.baidu.com/more/ name=tj_briicon class=bri style="display: block;">æ\x9b´å¤\x9aäº§å\x93\x81</a> </div> </div> </div> <div id=ftCon> <div id=ftConw> <p id=lh> <a href=http://home.baidu.com>å\x85³äº\x8eç\x99¾åº¦</a> <a href=http://ir.baidu.com>About Baidu</a> </p> <p id=cp>&copy;2017&nbsp;Baidu&nbsp;<a href=http://www.baidu.com/duty/>ä½¿ç\x94¨ç\x99¾åº¦å\x89\x8då¿\x85è¯»</a>&nbsp; <a href=http://jianyi.baidu.com/ class=cp-feedback>æ\x84\x8fè§\x81å\x8f\x8dé¦\x88</a>&nbsp;äº¬ICPè¯\x81030173å\x8f·&nbsp; <img src=//www.baidu.com/img/gs.gif> </p> </div> </div> </div> </body> </html>\r\n'
>>>r.encoding
'ISO-8859-1'
>>>r.apparent_encoding
'utf-8'
>>>r.encoding = 'utf-8'
>>>r.text
'<!DOCTYPE html>\r\n<!--STATUS OK--><html> <head><meta http-equiv=content-type content=text/html;charset=utf-8><meta http-equiv=X-UA-Compatible content=IE=Edge><meta content=always name=referrer><link rel=stylesheet type=text/css href=http://s1.bdstatic.com/r/www/cache/bdorz/baidu.min.css><title>百度一下，你就知道</title></head> <body link=#0000cc> <div id=wrapper> <div id=head> <div class=head_wrapper> <div class=s_form> <div class=s_form_wrapper> <div id=lg> <img hidefocus=true src=//www.baidu.com/img/bd_logo1.png width=270 height=129> </div> <form id=form name=f action=//www.baidu.com/s class=fm> <input type=hidden name=bdorz_come value=1> <input type=hidden name=ie value=utf-8> <input type=hidden name=f value=8> <input type=hidden name=rsv_bp value=1> <input type=hidden name=rsv_idx value=1> <input type=hidden name=tn value=baidu><span class="bg s_ipt_wr"><input id=kw name=wd class=s_ipt value maxlength=255 autocomplete=off autofocus></span><span class="bg s_btn_wr"><input type=submit id=su value=百度一下 class="bg s_btn"></span> </form> </div> </div> <div id=u1> <a href=http://news.baidu.com name=tj_trnews class=mnav>新闻</a> <a href=http://www.hao123.com name=tj_trhao123 class=mnav>hao123</a> <a href=http://map.baidu.com name=tj_trmap class=mnav>地图</a> <a href=http://v.baidu.com name=tj_trvideo class=mnav>视频</a> <a href=http://tieba.baidu.com name=tj_trtieba class=mnav>贴吧</a> <noscript> <a href=http://www.baidu.com/bdorz/login.gif?login&amp;tpl=mn&amp;u=http%3A%2F%2Fwww.baidu.com%2f%3fbdorz_come%3d1 name=tj_login class=lb>登录</a> </noscript> <script>document.write(\'<a href="http://www.baidu.com/bdorz/login.gif?login&tpl=mn&u=\'+ encodeURIComponent(window.location.href+ (window.location.search === "" ? "?" : "&")+ "bdorz_come=1")+ \'" name="tj_login" class="lb">登录</a>\');</script> <a href=//www.baidu.com/more/ name=tj_briicon class=bri style="display: block;">更多产品</a> </div> </div> </div> <div id=ftCon> <div id=ftConw> <p id=lh> <a href=http://home.baidu.com>关于百度</a> <a href=http://ir.baidu.com>About Baidu</a> </p> <p id=cp>&copy;2017&nbsp;Baidu&nbsp;<a href=http://www.baidu.com/duty/>使用百度前必读</a>&nbsp; <a href=http://jianyi.baidu.com/ class=cp-feedback>意见反馈</a>&nbsp;京ICP证030173号&nbsp; <img src=//www.baidu.com/img/gs.gif> </p> </div> </div> </div> </body> </html>\r\n'
```

r.encoding：从header（头部分）中的charset字段获得，表示服务器对资源的编码有要求，如果无charset字段，则认为编码为ISO-8859-1

r.apparent_encoding： 根据网页内容分析出的编码方式，实实在在的分析内容了

## 爬取网页的通用代码框架

get() 获取网页不一定能实现，需要异常处理

### Requests库的异常

|           异常            |                    说明                     |
| :-----------------------: | :-----------------------------------------: |
| requests.ConnectionError  | 网络连接错误异常，如DNS查询失败、拒绝连接等 |
|    requests.HTTPError     |                HTTP错误异常                 |
|   requests.URLRequired    |                 URL缺失异常                 |
| requests.TooManyRedirects |    重定向异常，超过最大重定向次数时产生     |
|  requests.ConnectTimeout  |           连接远程服务器超时异常            |
|     requests.Timeout      |         超时异常，请求URL超时时产生         |
|                           |                                             |
|                           |                                             |

requests.ConnectTimeout： 仅指与远程服务器连接这个过程

requests.Timeout： 发出URL请求到获得内容整个过程的

理解Response对象很重要，Response返回了网页爬取的所有内容

# 提取

## bs4库

解析、遍历、维护“标签树”的功能库

### 安装

pip install beautifulsoup4

安装小测

```python
import requests
r = requests.get('http://python123.io/ws/demo.html')
demo = r.text
from bs4 import BeautifulSoup
soup = BeautifulSoup(demo, 'html.parser')	#用html解释器来解析
print(soup.prettify())
```

结果（解析成功，说明安装成功）

```
<html>
 <head>
  <title>
   This is a python demo page
  </title>
 </head>
 <body>
  <p class="title">
   <b>
    The demo python introduces several python courses.
   </b>
  </p>
  <p class="course">
   Python is a wonderful general-purpose programming language. You can learn Python from novice to professional by tracking the following courses:
   <a class="py1" href="http://www.icourse163.org/course/BIT-268001" id="link1">
    Basic Python
   </a>
   and
   <a class="py2" href="http://www.icourse163.org/course/BIT-1001870001" id="link2">
    Advanced Python
   </a>
   .
  </p>
 </body>
</html>
```

### 引用方式

#### from bs4 import BeautifulSoup

常用，从库引用 BeautifulSoup 类

##### 理解

库本身解析的是 HTML、XML 文档，文档与标签树一一对应，经过 BeautifulSoup 类的处理，每一个标签树转换为 BeautifulSoup 类，可以认为文档、标签树、BeautifulSoup 类三者等价

通过类使树形成一个变量，从而可以对变量（树）进行处理

##### 操作

###### 两种载入内容方法

```python
from bs4 import BeautifulSoup
soup = BeartifulSoup('<html>data</html>', 'html.parser')
soup2 = BeautifulSoup(open('D://demo.html'), 'html.parser')
```

###### import bs4

需要判断基本变量时使用

### 解析器

|      解析器      |             使用方法             |         条件         |
| :--------------: | :------------------------------: | :------------------: |
| bs4的HTML解析器  | BeautifulSoup(mk, 'html.parser') |      安装bs4库       |
| lxml的HTML解析器 |    BeautifulSoup(mk, 'lxml')     |   pip install lxml   |
| lxml的XML解析器  |     BeautifulSoup(mk, 'xml')     |   pip install lxml   |
| html5lib的解析器 |  BeautifulSoup(mk, 'html5lib')   | pip install html5lib |

### BeautifulSoup 类基本元素

#### Tag

标签，最基本的信息组织单元，分别用 <></> 标明开头和结尾

#### Name

标签的名字，<p>...</p> 名字是'p'，格式：<tag>.name

#### Attributes

标签的属性，字典形式组织，格式：<tag>.attrs

#### NavigableString

标签内非属性字符串，文本节点，<>...</> 中字符串，格式：<tag>.string

#### Comment

标签内字符串的注释部分，一种特殊的 Comment 类型

### 操作

#### 获取标签

##### <变量名>.tag

##### 获取标签名字

##### 获取标签属性

##### 获取非属性字符串

##### 获取注释

