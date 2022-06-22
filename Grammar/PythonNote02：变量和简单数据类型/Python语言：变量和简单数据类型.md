# Python语言：变量和简单数据类型

# 变量与命名规则

我们首先编写一个 HelloWorld.py文档，并且让程序输出Hello World：

```python
print("Hello World")
```


输出的结果为：

```python
Hello World
```


或者我们也可以这么写：

```python
message = "Hello World"
print(message)
```


运行的结果为：

```python
Hello World
```


对于HelloWorld.py文档而言，HelloWorld是文件的名称，而.py则标注了文件的类型，.py指出了这是一个Python语言文件。

在第二个例子中，message是一个变量；=号意味着赋值，将=号的右边的值赋值到等号的左边的变量中；而“Hello World”则是复制的具体的内容。

print()则是一个Python语言内置的function，能够将括号中的内容打印出来。

在Python语言中，变量的名称需要遵守这些基本的规则，如果违反这些规则，则将会引发错误：

1. 变量名只能包含字母、数字和下划线。变量名可以字母或下划线打头，但不能以数字打头，例如，可将变量命名为message_1，但不能将其命名为1_message。
2. 变量名不能包含空格，但可使用下划线来分隔其中的单词。例如，变量名greeting_message可行，但变量名greetingmessage会引发错误。
3. 不要将Python关键字和函数名用作变量名，即不要使用Python保留用于特殊用途的单词，如print。
4. 变量名应既简短又具有描述性。例如，name比n好，student_name比s_n好，name_length比length_of_persons_name好。
5. 慎用小写字母l和大写字母O，因为它们可能被人错看成数字1和0。

如果想要知道Python语言都有那些keyword，我们可以通过导入keyword这一个modules来进行查询：

```python
import keyword
print(keyword.kwlist)
```


运行的结果为：

```python
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 
'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 
'else', 'except', 'finally', 'for', 'from', 'global', 
'if', 'import', 'in', 'is', 'lambda', 
'nonlocal', 'not', 'or', 'pass', 'raise', 
'return', 'try', 'while', 'with', 'yield']
```






# 字符串

字符串便是一串字符，在Python语言中，可以用单引号进行表示，也可以使用双引号进行表示：

```python
"Hello World"

'Hello World'
```


这两者实际上是同一回事。

在Python语言中，字符串可以简单的通过+号来进行合并：

```python
first_name = "John"
last_name = "Smith"
full_name = first_name +" "+ last_name
print(full_name)
```


运行的结果为：

```python
John Smith
```


但是我们并不能够通过-号来进行删减，如果我们这么做，则会报错：

![](image/image.png "")

不过我们可以通过使用*号来输出制定数量的字符串：

```python
message = "Hello"
message*5
```


运行的结果为：

```python
'HelloHelloHelloHelloHello'
```


可以发现message变量中的内容被输出了五次。

Python语言为string内置了许多function，这里介绍一些常用的function和对这些function进行演示。

Python isalnum() 方法检测字符串是否由字母和数字组成，如果 string 至少有一个字符并且所有字符都是字母或数字则返回 True,否则返回 False，语法为：

```python
str.isalnum()
```


例子为：

```python
str = "abc"
print(str.isalnum())

str = "abc abc"
print(str.isalnum())
```


输出的结果为：

```python
True
False
```


Python isalpha() 方法检测字符串是否只由字母组成，如果字符串至少有一个字符并且所有字符都是字母则返回 True，否则返回 False，语法为：

```python
str.isalpha()
```


例子如下所示：

```python
str = "runoob";
print str.isalpha();

str = "runoob菜鸟教程";
print str.isalpha();

str = "this is string example....wow!!!";
print str.isalpha();
```


运行的结果为：

```python
True
False
False
```


Python isdecimal() 方法检查字符串是否只包含十进制字符。这种方法只存在于unicode对象。如果字符串是否只包含十进制字符返回True，否则返回False。

例子如下所示：

```python
str = u"this2009";  
print str.isdecimal();

str = u"23443434";
print str.isdecimal();
```


运行的结果为：

```python
False
True
```


Python isspace() 方法检测字符串是否只由空格组成。如果字符串中只包含空格，则返回 True，否则返回 False。isspace()方法语法：

```
str.isspace()
```


一个例子为：

```
#!/usr/bin/python

str = "       ";
print str.isspace();

str = "This is string example....wow!!!";
print str.isspace();
```


这个例子的输出结果为：

```
True
False
```


Python lower() 方法转换字符串中所有大写字符为小写。返回将字符串中所有大写字符转换为小写后生成的字符串。

lower()方法语法：

```
str.lower()
```


例子为：

```python
str = "THIS IS STRING EXAMPLE....WOW!!!";

print str.lower();
```


输出的结果为：

```python
this is string example....wow!!!
```


Python title() 方法返回"标题化"的字符串,就是说所有单词都是以大写开始，其余字母均为小写(见 istitle())。返回"标题化"的字符串,就是说所有单词都是以大写开始。title()方法语法：

```
str.title();
```


例子为：

```python
str = "this is string example....wow!!!";
print str.title();
```


以上实例输出结果如下：

```
This Is String Example....Wow!!!
```


Python upper() 方法将字符串中的小写字母转为大写字母。返回小写字母转为大写字母的字符串。upper()方法语法：

```
str.upper()
```


一个例子：

```python
str = "this is string example....wow!!!";

print "str.upper() : ", str.upper()
```


结果为：

```python
str.upper() :  THIS IS STRING EXAMPLE....WOW!!!
```






# 数字

数字可以使用+，-，*，/，四个符号来进行简单的四则运算：

```python
print(10+10)
print(10-10)
print(10*10)
print(10/10)
```


结果如下所示：

```python
20
0
100
1.0
```


Python还支持幂运算：

```python
print(10**2)
```


运行的结果为：

```python
100
```


在使用数字的时候，我们需要避免类型出错误：

```python
age = 23
message = "Happy " + age + "rd Birthday!"
print(message)
```


运行的结果为：

```python
Traceback (most recent call last):
File "birthday.py", line 2, in <module>
message = "Happy " + age + "rd Birthday!"
TypeError: Can't convert 'int' object to str implicitly
```


这是因为对于age这个变量，python面领着字符串和数字两种情况，在这样的情况之下，python无法进行分辨，所以报错。

我们需要做的是将int类型转换为string类型：

```python
age = 23
message = "Happy " + str(age) + "rd Birthday!"
print(message)
```


运行的结果为：

```python
Happy 23rd Birthday!
```


Python同样的为数字提供了大量的内置函数。

abs() 函数返回数字的绝对值。函数返回x（数字）的绝对值。

以下是 abs() 方法的语法:

```
abs( x )
```


以下展示了使用 abs() 方法的实例：

```python
print "abs(-45) : ", abs(-45)
print "abs(100.12) : ", abs(100.12)
print "abs(119L) : ", abs(119L)
```


以上实例运行后输出结果为：

```
abs(-45) :  45
abs(100.12) :  100.12
abs(119L) :  119
```


ceil() 函数返回数字的上入整数。函数返回数字的上入整数。

以下是 ceil() 方法的语法:

```
import math

math.ceil( x )
```


以下展示了使用 ceil() 方法的实例：

```python
import math   # This will import math module

print "math.ceil(-45.17) : ", math.ceil(-45.17)
print "math.ceil(100.12) : ", math.ceil(100.12)
print "math.ceil(100.72) : ", math.ceil(100.72)
print "math.ceil(119L) : ", math.ceil(119L)
print "math.ceil(math.pi) : ", math.ceil(math.pi)
```


以上实例运行后输出结果为：

```
math.ceil(-45.17) :  -45.0
math.ceil(100.12) :  101.0
math.ceil(100.72) :  101.0
math.ceil(119L) :  119.0
math.ceil(math.pi) : 4.0
```


cmp(x,y) 函数用于比较2个对象，如果 x < y 返回 -1, 如果 x == y 返回 0, 如果 x > y 返回 1。

以下是 cmp() 方法的语法:

```
cmp( x, y )
```


以下展示了使用 cmp() 方法的实例：

```
print "cmp(80, 100) : ", cmp(80, 100)
print "cmp(180, 100) : ", cmp(180, 100)
print "cmp(-80, 100) : ", cmp(-80, 100)
print "cmp(80, -100) : ", cmp(80, -100)
```


以上实例运行后输出结果为：

```
cmp(80, 100) :  -1
cmp(180, 100) :  1
cmp(-80, 100) :  -1
cmp(80, -100) :  1
```


exp() 方法返回x的指数，e^x。

以下是 exp() 方法的语法:

```
import math

math.exp( x )
```


以下展示了使用 exp() 方法的实例：

```
import math   # 导入 math 模块

print "math.exp(-45.17) : ", math.exp(-45.17)
print "math.exp(100.12) : ", math.exp(100.12)
print "math.exp(100.72) : ", math.exp(100.72)
print "math.exp(119L) : ", math.exp(119L)
print "math.exp(math.pi) : ", math.exp(math.pi)
```


以上实例运行后输出结果为：

```
math.exp(-45.17) :  2.41500621326e-20
math.exp(100.12) :  3.03084361407e+43
math.exp(100.72) :  5.52255713025e+43
math.exp(119L) :  4.7978133273e+51
math.exp(math.pi) :  23.1406926328
```


max() 方法返回给定参数的最大值，参数可以为序列。

以下展示了使用 max() 方法的实例：

```python
print "max(80, 100, 1000) : ", max(80, 100, 1000)
print "max(-20, 100, 400) : ", max(-20, 100, 400)
print "max(-80, -20, -10) : ", max(-80, -20, -10)
print "max(0, 100, -400) : ", max(0, 100, -400)
```


以上实例运行后输出结果为：

```
max(80, 100, 1000) :  1000
max(-20, 100, 400) :  400
max(-80, -20, -10) :  -10
max(0, 100, -400) :  100
```


min() 方法返回给定参数的最小值，参数可以为序列。

以下是 min() 方法的语法:

```
min( x, y, z, .... )
```


以下展示了使用 min() 方法的实例：

```
print "min(80, 100, 1000) : ", min(80, 100, 1000)
print "min(-20, 100, 400) : ", min(-20, 100, 400)
print "min(-80, -20, -10) : ", min(-80, -20, -10)
print "min(0, 100, -400) : ", min(0, 100, -400)
```


以上实例运行后输出结果为：

```
min(80, 100, 1000) :  80
min(-20, 100, 400) :  -20
min(-80, -20, -10) :  -80
min(0, 100, -400) :  -400
```


pow() 方法返回 x^y（x 的 y 次方） 的值。

以下是 math 模块 pow() 方法的语法:

```
import math

math.pow( x, y )
```


以下展示了使用 pow() 方法的实例：

```python
import math   # 导入 math 模块
 
print "math.pow(100, 2) : ", math.pow(100, 2)
# 使用内置，查看输出结果区别
print "pow(100, 2) : ", pow(100, 2)
 
print "math.pow(100, -2) : ", math.pow(100, -2)
print "math.pow(2, 4) : ", math.pow(2, 4)
print "math.pow(3, 0) : ", math.pow(3, 0)
```


以上实例运行后输出结果为：

```
math.pow(100, 2) :  10000.0
pow(100, 2) :  10000
math.pow(100, -2) :  0.0001
math.pow(2, 4) :  16.0
math.pow(3, 0) :  1.0
```


sqrt() 方法返回数字x的平方根。

以下是 sqrt() 方法的语法:

```
import math

math.sqrt( x )
```


以下展示了使用 sqrt() 方法的实例：

```
import math   # This will import math module

print "math.sqrt(100) : ", math.sqrt(100)
print "math.sqrt(7) : ", math.sqrt(7)
print "math.sqrt(math.pi) : ", math.sqrt(math.pi)
```


以上实例运行后输出结果为：

```
math.sqrt(100) :  10.0
math.sqrt(7) :  2.64575131106
math.sqrt(math.pi) :  1.77245385091
```


# 如何写注释

Python中的注释有单行注释和多行注释。

Python中单行注释以 **#** 开头，例如：：

```python
# 这是一个注释
print("Hello, World!")
```


多行注释用三个单引号 **'''** 或者三个双引号 **"""** 将注释括起来。

单引号（'''）

```python
'''
这是多行注释，用三个单引号
这是多行注释，用三个单引号 
这是多行注释，用三个单引号
'''
print("Hello, World!")
```


双引号（"""）

```python
"""
这是多行注释，用三个双引号
这是多行注释，用三个双引号 
这是多行注释，用三个双引号
"""
print("Hello, World!")
```


# Python之禅

经验丰富的程序员倡导尽可能避繁就简。Python社区的理念都包含在Tim Peters撰写的“Python之禅”中。要获悉这些有关编写优秀Python代码的指导原则，只需在解释器中执行命令import this。

```python
import this
```


运行的结果为：

```python
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```


