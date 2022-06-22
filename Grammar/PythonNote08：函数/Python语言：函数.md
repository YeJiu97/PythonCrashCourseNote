# Python语言：函数

# 定义函数

以下是一个打印问候语的简单函数，函数名称为greet)user():

```python
def greet_user():
  """用来显示简单的问候语"""
  print("Hello Users!")

greet_user()
```


运行的结果为：

```python
Hello Users!
```


def是definition的缩写，def关键字会告诉Python我们要定义一个函数，这就是函数定义；greet_user()则是函数的名称，默认为无参数，但是可以添加参数来为之后的代码提供信息；而结尾则是:冒号；在这之后则是"""xxxx"""，这里的文本是文档字符串的注释，用来描述函数是用来做什么的，需要用三个引号（单引号或者双引号都可以）来标明；这之后面试代码，代码在函数被调用的时候会被执行。

最后greet_user()则是对函数的调用，注意不要遗漏()，如果仅仅是greet_user则不是对这个函数的调用。

我们可以想函数传递一个参数，让函数打印出来这个参数：

```python
def greet_user(user_name):
  """用来显示简单的问候语"""
  print("Hello Users!"+ " " + user_name)

user_name = input("Please enter a number here: ")
greet_user(user_name)
```


运行的结果为：

```python
Please enter a number here: John
Hello Users! John
```


在这里user_name是一个形式参数，因为这个参数的只是一个形式，用来指向被传递进来的数据，而John则是一个实际参数，实际参数是调用函数的时候传递给函数的信息。

# 实际参数

实际参数的第一种形式是位置实参：

```python
def describe_pet(animal_type, pet_name):
   """显示宠物的信息"""
   print("\nI have a " + animal_type + ".")
   print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet('hamster', 'harry')
```


运行的结果为：

```
I have a hamster.
My hamster's name is Harry.
```


对于位置实参而言，顺序非常的重要，否则会：

```python
def describe_pet(animal_type, pet_name):
   """显示宠物的信息"""
   print("\nI have a " + animal_type + ".")
   print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet('harry','hamster')
```


变成了：

```
I have a harry.
My harry's name is Hamster.
```


关键字实参则是给函数传递 名称-值 对：

```
def describe_pet(animal_type, pet_name):
  """显示宠物的信息"""
  print("\nI have a " + animal_type + ".")
  print("My " + animal_type + "'s name is " + pet_name.title() + ".")

describe_pet(animal_type='hamster', pet_name='harry')
```


运行的结果为：

```
I have a hamster.
My hamster's name is Harry.
```


调用这个函数时，我们向Python明确地指出了各个实参对应的形参。看到这个函数调用时，Python知道应该将实参'hamster'和'harry'分别存储在形参animal_type和pet_name中。

另一种情况是我们可以使用默认值，在编写函数的时候可以给每个形式参数指定默认值：

```
def describe_pet(pet_name, animal_type='dog'):
  """显示宠物的信息"""
  print("\nI have a " + animal_type + ".")
  print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet(pet_name='willie')
```


运行的结果为：

```
I have a dog.
My dog's name is Willie.
```


# 返回值

函数并非总是直接显示输出，相反，它可以处理一些数据，并返回一个或一组值。

一下是一个函数：

```
def get_formatted_name(first_name, last_name):
  """返回整洁的姓名"""
  full_name = first_name + ' ' + last_name
  return full_name.title()
musician = get_formatted_name('jimi', 'hendrix')
print(musician)
```


运行的结果为：

```
Jimi Hendrix
```


我们也可以让实参变成可选的，以下是一个例子：

```
def get_formatted_name(first_name, middle_name, last_name):
  """返回整洁的姓名"""
  full_name = first_name + ' ' + middle_name + ' ' + last_name
  return full_name.title()

musician = get_formatted_name('john', 'lee', 'hooker')
print(musician)
```


运行的结果为：

```
John Lee Hooker
```


但是对于一些人而言没有middle_name，所以在这样的情况之下，我们可以这样写：

```
def get_formatted_name(first_name, last_name, middle_name=''):
  """返回整洁的姓名"""
  if middle_name:
    full_name = first_name + ' ' + middle_name + ' ' + last_name
  else:
    full_name = first_name + ' ' + last_name
  return full_name.title()

musician = get_formatted_name('jimi', 'hendrix')
print(musician)
musician = get_formatted_name('john', 'hooker', 'lee')
print(musician)
```


运行的结果为：

```
Jimi Hendrix
John Lee Hooker
```


# 传递列表

向函数传递列表很有用，这种列表包含的可能是名字、数字或更复杂的对象（如字典）。将列表传递给函数后，函数就能直接访问其内容。下面使用函数来提高处理列表的效率。

我们可以写一个这样的程序：

```
def greet_users(names):
  """向列表中的每位用户都发出简单的问候"""
  for name in names:
    msg = "Hello, " + name.title() + "!"
    print(msg)

usernames = ['hannah', 'ty', 'margot']
greet_users(usernames)
```


运行的结果为：

```
Hello, Hannah!
Hello, Ty!
Hello, Margot!
```


# 传递任意数量的实参

有些情况我们并不知道函数需要接受多少个实参，但是Python语言允许函数从调用语句中收集任意数量的实参。

这是一个例子：

```
def make_pizza(*toppings):
  """打印顾客点的所有配料"""
  print(toppings)

make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')
```


形参名*toppings中的星号让Python创建一个名为toppings的空元组，并将收到的所有值都封装到这个元组中。

运行的结果为：

```
('pepperoni',)
('mushrooms', 'green peppers', 'extra cheese')
```


我们可以将print修改成一个循环语句：

```
def make_pizza(*toppings):
  """概述要制作的比萨"""
  print("\nMaking a pizza with the following toppings:")
  for topping in toppings:
    print("- " + topping)

make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')
```


运行的结果为：

```
Making a pizza with the following toppings:
- pepperoni

Making a pizza with the following toppings:
- mushrooms
- green peppers
- extra cheese
```


# 将函数存储在模块中

要让函数是可导入的，得先创建模块。模块是扩展名为.py的文件，包含要导入到程序中的代码。

创建一个名为pizza.py的文件：

```
def make_pizza(size, *toppings):
"""概述要制作的比萨"""
  print("\nMaking a " + str(size) +
    "-inch pizza with the following toppings:")
  for topping in toppings:
    print("- " + topping)
```


然后我们可以创建另一个名为为making_pizzas.py的文件，然后在这个文件中导入刚才刚创建的模块：

```
import pizza
pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```


运行的结果为：

```
Making a 16-inch pizza with the following toppings:
- pepperoni

Making a 12-inch pizza with the following toppings:
- mushrooms
- green peppers
- extra cheese
```


