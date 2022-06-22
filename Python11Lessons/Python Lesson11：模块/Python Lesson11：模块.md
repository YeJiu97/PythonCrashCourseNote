# Python Lesson11：模块

模块是一个包含所有你定义的函数和变量的文件，其后缀名是.py。模块可以被别的程序引入，以使用该模块中的函数等功能。这也是使用 python 标准库的方法。

我们可以创建一个用来输出个人信息的模块，称之为叫做personalInformation.py：

```python
def printInformation(name, age):

  print("用户的名字为：{}".format(name))
  print("用户的年龄为：{}".format(age))

  print("欢饮你！")
```


接着我们再创建一个名为importTry.py的python文件：

```python
import personalInformation

personalInformation.printInformation("Jobs", "20")
```


运行的结果为：

```python
用户的名字为：Jobs
用户的年龄为：20
欢饮你！
```


可以发现我们在importTry.py文件中导入了personalInformation.py文件，并且被导入的文件中的功能可以被我们使用。

如此，我们可以尝试着将之前的类打包在一个文件当中，等我们需要的时候再使用这个文件：

```python
class person():
  """人的类，每一个人都具有的最基础的属性"""

  # 先给出person类的基本属性
  # 如果一个属性是私有的，则可以使用 __来声明，比如 __name就是name属性是私有的
  name = ''
  age = ''

  def __init__(self, name, age):
    """"每个人都有姓名和年龄"""
    self.name = name
    self.age = age

  def printInformation(self):
    print("姓名为：{}".format(self.name))
    print("年龄为：{}".format(self.age))

class student(person):
  """学生类，继承person，但是具备了studentID这个属性"""
  
  # student 类的属性
  studentID = ''

  def __init__(self, name, age, studentID):
    
    # 调用父类的构造函数
    person.__init__(self, name, age)
    self.studentID = studentID

  # 对父类的函数进行覆写
  def printInformation(self):
    print("学生的姓名为：{}".format(self.name))
    print("学生的年龄为：{}".format(self.age))
    print("学生的ID为：{}".format(self.studentID))
```


我们将person class和student class写在p_s.py文件中，接着我们在object01.py中调用这个模块：

```python
import p_s

# 然后我们来生成一个person和一个student进行尝试
person_One = p_s.person("John", "16")
person_One.printInformation()

print("   ")

student_One = p_s.student("Jobs", "18", "123")
student_One.printInformation()
```


运行的结果为：

```python
姓名为：John
年龄为：16
   
学生的姓名为：Jobs
学生的年龄为：18
学生的ID为：123
```


模块是一个非常有用的功能，我们可以将一些常用的代码写在模块里面，等需要的时候再进行调用。

Python 的 from 语句让你从模块中导入一个指定的部分到当前命名空间中，语法如下：

```python
from modname import name1[, name2[, ... nameN]]
```




