# Python语言：异常检测

# 异常

Python使用被称之为叫做异常的特殊对象来管理程序执行期间发生的错误。

每当发生让Python不知所措的错误的时候，它都会创建一个异常对象。如果编写了处理改异常的代码，那么程序将会继续运行，如果未对异常进行处理，程序将会停止运行，并且显示一个traceback，其中包含了关于异常的报告。

# 处理ZeroDivisionError 异常

一个常见的错误就是将一个数字除以0：

```React JSX
print(10/0)
```


运行的结果为：

```React JSX
Traceback (most recent call last):
  File "division.py", line 1, in <module>
    print(10/0)
ZeroDivisionError: division by zero
```


错误ZeroDivisionError是一个异常对象。Python无法按你的要求做时，就会创建这种对象。在这种情况下，Python将停止运行程序，并指出引发了哪种异常，而我们可根据这些信息对程序进行修改。下面我们将告诉Python，发生这种错误时怎么办；这样，如果再次发生这样的错误，我们就有备无患了：

```React JSX
try:
 print(10/0)
except ZeroDivisionError:
 print("You can't divide by zero!")
```


我们将导致错误的代码行print(5/0)放在了一个try代码块中。如果try代码块中的代码运行起来没有问题，Python将跳过except代码块；如果try代码块中的代码导致了错误，Python将查找这样的except代码块，并运行其中的代码，即其中指定的错误与引发的错误相同。

try代码块中的代码引发了ZeroDivisionError异常，因此Python指出了该如何解决问题的except代码块，并运行其中的代码。这样，用户看到的是条友好的错误消息，而不是traceback：

```React JSX
You can't divide by zero!
```


如果try-except代码块后面还有其他代码，程序将接着运行，因为已经告诉了Python如何处理这种错误。下面来看一个捕获错误后程序将继续运行的示例。

# 使用异常来避免崩溃

发生错误时，如果程序还有工作没有完成，妥善地处理错误就尤其重要。这种情况经常会出现在要求用户提供输入的程序中；如果程序能够妥善地处理无效输入，就能再提示用户提供有效输入，而不至于崩溃。

我们可以创建一个执行除法的简单计算器：

```python
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")

while True:
  first_number = input("\nFirst number: ")
  if first_number == 'q':
    break
  second_number = input("Second number: ")
  if second_number == 'q':
    break
  answer = int(first_number) / int(second_number)
  print(answer)
```


这个程序提示用户输入一个数字，并将其存储到变量first_number中；如果用户输入的不是表示退出的q，就再提示用户输入一个数字，并将其存储到变量second_number中。接下来，我们计算这两个数字的商（即answer）。这个程序没有采取任何处理错误的措施，因此让它执行除数为0的除法运算时，它将崩溃：

```python
Give me two numbers, and I'll divide them.
Enter 'q' to quit.
First number: 5
Second number: 0
Traceback (most recent call last):
 File "division.py", line 9, in <module>
 answer = int(first_number) / int(second_number)
ZeroDivisionError: division by zero
```


程序崩溃有两个问题：

1. 不懂技术的用户会面领着麻烦
2. 懂技术的用户可能通过traceback来获得开发人员不希望用户知道的信息

这个时候我们就需要使用异常捕获来处理这个问题：

```python
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")
while True:
  first_number = input("\nFirst number: ")
  if first_number == 'q':
    break
  
  second_number = input("Second number: ")
  try:
    answer = int(first_number) / int(second_number)
  except ZeroDivisionError:
    print("You can't divide by 0!")
  else:
    print(answer)
```


我们让Python尝试执行try代码块中的除法运算，这个代码块只包含可能导致错误的代码。依赖于try代码块成功执行的代码都放在else代码块中；在这个示例中，如果除法运算成功，我们就使用else代码块来打印结果。

测试如下所示：

```python
Give me two numbers, and I'll divide them.
Enter 'q' to quit.

First number: 5
Second number: 0
You can't divide by 0!

First number: 5
Second number: 2
2.5

First number: q
```


try-except-else代码块的工作原理大致如下：Python尝试执行try代码块中的代码；只有可能引发异常的代码才需要放在try语句中。有时候，有一些仅在try代码块成功执行时才需要运行的代码；这些代码应放在else代码块中。except代码块告诉Python，如果它尝试运行try代码块中的代码时引发了指定的异常，该怎么办。

还有一种情况是我们并不需要让用户知道发生了什么，或者提醒用户要做什么：

```python
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")
while True:
  first_number = input("\nFirst number: ")
  if first_number == 'q':
    break
  
  second_number = input("Second number: ")
  try:
    answer = int(first_number) / int(second_number)
  except ZeroDivisionError:
    pass
  else:
    print(answer)
```


这个时候except中的内容修改成pass就可以了。

# Python异常类型

以下为Python语言的异常类型：

|异常名称|描述|
|---|---|
|BaseException|所有异常的基类|
|SystemExit|解释器请求退出|
|KeyboardInterrupt|用户中断执行(通常是输入^C)|
|Exception|常规错误的基类|
|StopIteration|迭代器没有更多的值|
|GeneratorExit|生成器(generator)发生异常来通知退出|
|StandardError|所有的内建标准异常的基类|
|ArithmeticError|所有数值计算错误的基类|
|FloatingPointError|浮点计算错误|
|OverflowError|数值运算超出最大限制|
|ZeroDivisionError|除(或取模)零 (所有数据类型)|
|AssertionError|断言语句失败|
|AttributeError|对象没有这个属性|
|EOFError|没有内建输入,到达EOF 标记|
|EnvironmentError|操作系统错误的基类|
|IOError|输入/输出操作失败|
|OSError|操作系统错误|
|WindowsError|系统调用失败|
|ImportError|导入模块/对象失败|
|LookupError|无效数据查询的基类|
|IndexError|序列中没有此索引(index)|
|KeyError|映射中没有这个键|
|MemoryError|内存溢出错误(对于Python 解释器不是致命的)|
|NameError|未声明/初始化对象 (没有属性)|
|UnboundLocalError|访问未初始化的本地变量|
|ReferenceError|弱引用(Weak reference)试图访问已经垃圾回收了的对象|
|RuntimeError|一般的运行时错误|
|NotImplementedError|尚未实现的方法|
|SyntaxError|Python 语法错误|
|IndentationError|缩进错误|
|TabError|Tab 和空格混用|
|SystemError|一般的解释器系统错误|
|TypeError|对类型无效的操作|
|ValueError|传入无效的参数|
|UnicodeError|Unicode 相关的错误|
|UnicodeDecodeError|Unicode 解码时的错误|
|UnicodeEncodeError|Unicode 编码时错误|
|UnicodeTranslateError|Unicode 转换时错误|
|Warning|警告的基类|
|DeprecationWarning|关于被弃用的特征的警告|
|FutureWarning|关于构造将来语义会有改变的警告|
|OverflowWarning|旧的关于自动提升为长整型(long)的警告|
|PendingDeprecationWarning|关于特性将会被废弃的警告|
|RuntimeWarning|可疑的运行时行为(runtime behavior)的警告|
|SyntaxWarning|可疑的语法的警告|
|UserWarning|用户代码生成的警告|



在考虑异常的时候可以对照着选择。

