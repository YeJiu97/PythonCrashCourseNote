# Python语言：if语句

# if语句

每条if语句的核心都是一个值为True或False的表达式，这种表达式被称为条件测试。Python 根据条件测试的值为True还是False来决定是否执行if语句中的代码。如果条件测试的值为True，Python就执行紧跟在if语句后面的代码；如果为False，Python就忽略这些代码。

要判断是否相等，我们可以使用==来进行判断：

```python
car = 'Audi'
car.lower() == 'audi'
```


输出的结果为：

```python
true
```


比如说我们在测试用户的用户名是否与他人重合的时候我们可以使用到这个判断。 

要判断两个值是否不等，可结合使用惊叹号和等号（!=），其中的惊叹号表示不，在很多编程语言中都如此：

```python
requested_topping = 'mushrooms'
if requested_topping != 'anchovies':
  print("Hold the anchovies!")
```


输出的结果为：

```python
Hold the anchovies!
```


如果需要对多个条件进行比较，则可以使用and和or两个符号：

```python
num1 = 15
num2 = 20

num3 = 25
num4 = 30

if num1 == 15 and num2 == 20:
  print("All Right")

if num3 == 25 or num4 == 40:
  print("One of them is right")
```


and需要多个条件同时成立才能够成立，而or只需要一个条件成立就能够成立。

# if-else语句

最简单的if语句只有一个测试和一个操作，但是使用了if-else语句之后便可以有两个操作：

```python
num = 50

if num < 60:
  print("不及格")
else:
  print("及格了")
```


输出的结果为：

```python
不及格
```


if-else语句可以演变为if-elif-else语句，用来执行2个以上的条件判断对执行对应的操作：

```python
num = 85

if num < 60:
  print("不及格")
elif 60<=num and num<=80:
  print("及格")
else:
  print("优秀")
```


运行的结果为：

```python
优秀
```


# 用if语句来处理列表

我们可以把if语句和列表相结合：

```python
food_list = ['apple', 'banana','orange']

for food in food_list:
  if food == 'apple':
    print("Apple is here")
  elif food == 'bana':
    print("Banana is here")
  else:
    print("Orange is here")
```


输出的结果为：

```python
Apple is here
Orange is here
Orange is here
```


或者我们可以用来检测列表是否为空：

```python
requested_toppings = []
if requested_toppings:
  for requested_topping in requested_toppings:
    print("Adding " + requested_topping + ".")
  print("\nFinished making your pizza!")
else:
  print("Are you sure you want a plain pizza?")
```


运行结果为：

```python
Are you sure you want a plain pizza?
```


Python语言会在列表至少包含一个元素的时候返回True，而列表为空的是否返回False。

当我们有着多个列表的时候，我们可以：

```python
available_toppings = ['mushrooms', 'olives', 'green peppers','pepperoni', 'pineapple', 'extra cheese']
requested_toppings = ['mushrooms', 'french fries', 'extra cheese']

for requested_topping in requested_toppings:
  if requested_topping in available_toppings:
    print("Adding " + requested_topping + ".")
  else:
    print("Sorry, we don't have " + requested_topping + ".")
  print("\nFinished making your pizza!")
```


运行结果为：

```python
Adding mushrooms.

Finished making your pizza!
Sorry, we don't have french fries.

Finished making your pizza!
Adding extra cheese.

Finished making your pizza!
```


