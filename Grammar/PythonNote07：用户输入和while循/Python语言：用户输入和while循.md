# Python语言：用户输入和while循环

# input()输入

函数input()让程序暂停运行，等待用户输入一些文本。获取用户输入后，Python将其存储在一个变量中，以方便你使用。

以下就是一个简单的例子：

```python
message = intpu("Enter 'Hello World'")
print(message)
```


运行的结果为：

```python
Enter 'Hello World'Hello World
Hello World
```


input()函数会接受一个参数，不过需要想用户进行说明，让用户知道需要输入什么。

有些情况之下我们需要用户输入一个数字，这个时候我们需要使用int()来讲输入的内容转换为int类型：

```python
number = int(input("Please enter a number here: "))

print(number)
```


运行的结果为：

```python
Please enter a number here: 123321
123321
```


如果我们不适用int()来完成类型的转变，那么我们输入的数字实际上是string类型，而不是int类型。

# while循环

for循环用于针对集合中的每个元素都一个代码块，而while循环不断地运行，直到指定的条件不满足为止。

我们可以使用while循环来数数，比如说：

```python
current_number = 1
while current_number <= 5:
  print(current_number)
  current_number += 1
```


我们首先生成了一个名为current_number的数字，并且将其设置为1；以这个数字为flag，我们进行了一个循环，循环的终止条件为current_number≤5；当这个条件成立的时候，便会执行while代码块中的代码，代码有两行，第一行是打印当前的数字，第二行是将当前的数字的值+1；第二行的代码非常的重要，因为每进行以此循环，数值便会变大一个，如此current_number的值最终便会达到5，这时候while循环的条件判断便会不成立，如此循环便会终止。

通过循环，我可以选择让用户决定何时退出：

```python
message  = ""

while message !="000":
  print("Type something here and i weill repeat it back: ")
  print("\n If you type 000, it will end that program.")
  message = input()
  print(message)
```


运行的结果为

```python
Type something here and i weill repeat it back:

If you type end, it will end that program.
123321
123321
Type something here and i weill repeat it back:

If you type end, it will end that program.
qwerreqw
qwerreqw
Type something here and i weill repeat it back:

If you type end, it will end that program.
end
end
```


但是这个程序有着一个问题，就是会将end也打印出来：

我们可以通过增加if判断语句来消除这个问题：

```python
message  = ""

while message !="end":
  print("Type something here and i weill repeat it back: ")
  print("\nIf you type end, it will end that program.")
  message = input()
  
  if message != "end":
    print(message)
```


运行的结果为：

```python
Type something here and i weill repeat it back:

If you type end, it will end that program.
qwerreq
qwerreq
Type something here and i weill repeat it back:

If you type end, it will end that program.
end
```


在一些复杂的程序中，许多不同的事情会导致程序停止运行，再这样的情况之下我们可以设置一个标志，这个标志可以用来判断整个程序是否处于活动状态，当标志为true的时候会继续运行，而当标志为false的时候程序便会停止运行。

例子如下所示：

```python
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "

active = True
while active:

  message = input(prompt)

  if message == 'quit':
    active = False
  else:
    print(message)
```


我们先将active设置为了True，如此程序最开始会处于活动状态，这样做简化了while语句，因为不需要在其中做任何的比较，相关的逻辑由程序的其他部分处理，只要将变量active为True，循环就可以继续运行。

如果我们需要立即退出while循环，并且不在运行循环中的剩余的代码，也无论条件测试的结果如何，那么我们可以使用break语句，break语句可以用来控制程序流程，可以使用它来控制哪些代码将执行，哪些代码不执行，从而让程序按照要求执行代码：

```python
prompt = "\nPlease enter the name of a city you have visited:"
prompt += "\n(Enter 'quit' when you are finished.) "
while True:
  city = input(prompt)
  if city == 'quit':
    break
  else:
    print("I'd love to go to " + city.title() + "!")
```


运行如下所示：

```python
Please enter the name of a city you have visited:
(Enter 'quit' when you are finished.) New York
I'd love to go to New York!

Please enter the name of a city you have visited:
(Enter 'quit' when you are finished.) San Francisco
I'd love to go to San Francisco!

Please enter the name of a city you have visited:
(Enter 'quit' when you are finished.) quit
```


实际上在Python的任何循环中都可以使用break语句，不单纯的是for循环，if语句，for语句中都可以使用break语句来直接退出。

如果我们希望不再执行接下来的语句，但是也不直接退出循环，而是回到循环的开头先做一次循环判断，那么我们可以使用continue语句：

```python
current_number = 0
while current_number < 10:
  current_number += 1
  if current_number % 2 == 0:
    continue
  
  print(current_number)
```


运行的结果为：

```python
1
3
5
7
9
```


