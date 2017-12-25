# python基础知识

* pythonV1.6   
* pythonV2.0-----V2.6  V2.7
* pythonV3.0------V3.6

现在用2.7版本较多，这是由于现在很多第三方插件都支持V2.7，V3和V2在语法上有差异，所以V2上的pyhon无法直接在V3上运行

Python官方网站：    [python 官网](https://www.python.org)     可在官网上下载python onwindows 

 

高阶动态编程语言

python的两种模式

* 交互模式
* 文本模式 



交互模式

``` shell
# python
Python 2.7.5 (default, Aug  4 2017, 00:39:18) 
[GCC 4.8.5 20150623 (Red Hat 4.8.5-16)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()
```

``` shell
# python
Python 2.7.5 (default, Aug  4 2017, 00:39:18) 
[GCC 4.8.5 20150623 (Red Hat 4.8.5-16)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print 'hello world'
hello world
>>> prite 'hello world'
  File "<stdin>", line 1
    prite 'hello world'
                      ^
SyntaxError: invalid syntax
>>>
```

` SyntaxError: invalid syntax  `语法错误：不可用的语法

 

文本模式

``` shell
# cat 1.py 
print 'hello world'
```

``` shell
# python 1.py 
hello world
```



python文件类型

* 源代码
* 字节代码
* 优化代码



源代码：python源代码文件以.py结尾，由python程序解释，不需要编辑

``` shell
# ./1.py 
./1.py: line 1: print: command not found
```

如果希望像运行一个程序一样运行python脚本，可以在脚本首行前面加上#！，用于解释脚本的程序的绝对路径

``` shell
# ./1.py 
hello world
# cat 1.py 
#!/bin/python
print 'hello world'
```

字节代码：python源文件编译后生成扩展名为.pyc的文件

``` shell
# cat 2.py 
import py_complie 

py_complie.complie('1.py')
```

利用compile模块

``` shell
# python 2.py 
Traceback (most recent call last):
  File "2.py", line 1, in <module>
    import py_complie 
ImportError: No module named py_complie
```

` ImportError: No module named py_complie  `complie模块编写错误，出现报错找不到该模块

``` shell
# cat 2.py 
import py_compile 

py_compile.compile('1.py')
# python 2.py
```

作用是编辑1.py

``` shell
# ls
1.py  1.pyc  2.py
```

打开看1.pyc可以看到

``` shell
# vim 1.pyc 

^Có
3®7Zc^@^@^@^@^@^@^@^@^A^@^@^@@^@^@^@s   ^@^@^@d^@^@GHd^A^@S(^B^@^@^@s^K^@^@^@hello worldN(^@^@^@^@(^@^@^@^@(^@^@^@^@(^@^@^@^@s^D^@^@^@1.pyt^H^@^@^@<module>^B^@^@^@s^@^@^@^@
```

.pyc已经被编译

 

优化代码：经过优化的文件扩展名为.pyo

``` shell
# python -O -m py_compile 1.py
# ls
1.py  1.pyc  1.pyo  2.py
# cat 1.pyo 
 
3®7Zc@s	dGHdS(s
               hello worldN((((s1.py<module>s[root@stack03 python]#
# python 1.pyo 
hello world
```

# 数字和表达式

需要注意的是

``` shell
>>> 1/2
0
```

另外，Python中被称为浮点数（Float，或者Float-point Number），如果参与运算的两个数中有一个数为浮点数，则运算结果亦为浮点数

如果希望Python只执行普通的除法，可以在程序前加上语句，或者直接在解释器里面执行它

``` shell
>>> from __future__ import division
>>> 1/2
0.5
```

整除： `//`

取余：%

幂：**

## 长整型

非常大的数字才需要长整型，长整型的表示方式为：`10000000000L`（理论上加上小写的`l`也行，不过非常像数字1，所以不推荐）

 长整型和普通整数可以混合使用。

十六进制：0xAF  =  175

八进制：010 = 8

## 变量

变量基本上就是代表（或者引用）某值的名字

``` shell
>>> x = 3
>>> x * 2
6
```

变量可以包括字母、数字和下划线。变量不能以数字开头。

## 语句

表达式：某件事情

语句：做某件事情

## 获得用户输入

input()语句

``` shell
>>> input("x: ")
x: 123
123
```

## 函数

``` shell
>>> 2**3
8
>>> pow(2,3)
8
```

函数就像小型程序一样，可以用来实现特定的功能。

通常，会把上面类似`pow`等标准函数成为内建函数。

上例中使用函数的方式叫做调用函数。

## 模块

可以把模块想象成导入到pyhotn以增强其功能的扩展。

``` shell
>>> import math
>>> math.floor(32.9)
32.0
```

用import 导入了模块，然后按照“模块.函数”的格式使用这个模块的函数。

在确定不会导入多个同名函数的情况下，如果希望不要在每次调用函数的时候都协商模块的名字，可以使用import命令的另一种形式

``` shell
>>> from math import sqrt 
>>> sqrt(9)
3.0
```

使用"from模块import函数"这种形式的import命令之后，就可以直接使用函数，而不需要模块名作为前缀。

如果使用这种方式Import，那么就无法使用普通的sqrt()函数。

## 复数

``` shell
>>> import cmath
>>> cmath.sqrt(-1)
1j
```

# 注释

通过井号 \#

## 字符串

字符串在几乎所有真是可用的python程序中都会存在，并且有多种用法，其中最主要的用法就是表示一些文本，比如这个感叹号"Hello world!"

### 单引号和双引号

两个都存在的时候，建议单引号在外，双引号在内

\对字符串中的引号进行转义

``` shell
>>> 'Let\'s go!'
"Let's go!"
```

### 字符串表示

str：通过str()函数，把值转换为合理形式的字符串

repr：会创建一个字符串，以合法的python表达式的形式来表示值

``` shell
>>> print repr(10000L)
10000L
>>> print str(10000L)
10000
```

### input()和rawinput()

input会假设用户输入的是合法的python表达式，例如

``` shell
>>> input("name:")
name:xu
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<string>", line 1, in <module>
NameError: name 'xu' is not defined
>>> input("name:")
name:"xu"
'xu'
```

需要自己定义输入的是什么类型

rawinput会把所有输入当作原始数据，放入到字符串中

除非对input有特别的需求，否则应该尽可能使用raw_input函数

## 长字符串、原始字符串、Unicode

长字符串：   \```   \*****    \``` 可以使用三个引号或者三个双引号

原始字符串：r'   \**\**** '  原始字符串以r开头，原始字符串不会吧反斜线当作特殊字符

Unicode：u\`   \**\*\*\*\*   `unicode字符串以u开头





# 总结

* 算法
* 表达式
* 变量
* 语句
* 函数
* 模块
* 程序
* 字符串

