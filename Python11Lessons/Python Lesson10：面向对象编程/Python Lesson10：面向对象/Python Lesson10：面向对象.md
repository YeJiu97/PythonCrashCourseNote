# Python Lesson10：面向对象编程

## 面向对象

面向对象技术如下所示：

1. 类(Class): 用来描述具有相同的属性和方法的对象的集合。它定义了该集合中每个对象所共有的属性和方法。对象是类的实例。
2. 方法：类中定义的函数。
3. 类变量：类变量在整个实例化的对象中是公用的。类变量定义在类中且在函数体之外。类变量通常不作为实例变量使用。
4. 数据成员：类变量或者实例变量用于处理类及其实例对象的相关的数据。
5. 方法重写：如果从父类继承的方法不能满足子类的需求，可以对其进行改写，这个过程叫方法的覆盖（override），也称为方法的重写。
6. 局部变量：定义在方法中的变量，只作用于当前实例的类。
7. 实例变量：在类的声明中，属性是用变量来表示的，这种变量就称为实例变量，实例变量就是一个用 self 修饰的变量。
8. 继承：即一个派生类（derived class）继承基类（base class）的字段和方法。继承也允许把一个派生类的对象作为一个基类对象对待。例如，有这样一个设计：一个Dog类型的对象派生自Animal类，这是模拟"是一个（is-a）"关系（例图，Dog是一个Animal）。
9. 实例化：创建一个类的实例，类的具体对象。
10. 对象：通过类定义的数据结构实例。对象包括两个数据成员（类变量和实例变量）和方法。

## 类

类对象支持两种操作：属性引用和实例化。

```python
class Car():
  """一个车的类"""

  # 首先设置了一个类变量，也就是轮胎的数量
  wheel_Number = 4

  def print_Wheel_Number(self):
    print("车子的轮胎数量是: 4")

# 我们通过Car()函数来将一个Car实例化
car_One = Car()

# 然后来访问这个类的属性和方法
print("轮胎的数量为：", car_One.wheel_Number)
car_One.print_Wheel_Number()
```


运行的结果为：

```python
轮胎的数量为： 4
车子的轮胎数量是: 4
```


类有一个名为 **init**() 的特殊方法（构造方法），该方法在类实例化时会自动调用，像下面这样：

```python
def __init__(self):
    self.data = []
```


我们将car class的代码进行稍微的改写：

```python
class Car():
  """一个车的类"""

  def __init__(self, light, wheel):
    self.l = light
    self.w = wheel

# 我们通过Car()函数来将一个Car实例化
car_One = Car(2, 4)

print("车子的车灯的数量为{},车子的轮子数量为{}".format(car_One.l, car_One.w))
```


在类的内部，使用 **def** 关键字来定义一个方法，与一般函数定义不同，类方法必须包含参数 self, 且为第一个参数，self 代表的是类的实例。

```python
class student():
  """一个学生类型"""

  def __init__(self, name, id, age):
    """名字，id和年龄"""
    self.name = name
    self.id = id
    self.age = age

  def printInformation(self):
    """用来打印学生的信息"""

    print("学生的名字为{}，学生的id为{}，学生的年龄为{}".format(self.name, self.id, self.age))

studentOne = student("John", "001", "16")

studentOne.printInformation()
```


再上述代码中，我们创建了一个student类型，并且给出了name，id和age三个属性，接着我们使用init来对其进行初始化，以及我们呢使用了printInformation函数来打印学生的信息。

接着我们用student类来生成了一个对象studeOne，并且通过init函数来给出了这个对象的具体的属性，然后我们调用了printInformation函数来将这个对象的属性打印出来。

## 单继承

Python 同样支持类的继承，如果一种语言不支持继承，类就没有什么意义。

我们可以之前的代码进行修改，来演示继承是如何运作的：

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

# 然后我们来生成一个person和一个student进行尝试
person_One = person("John", "16")
person_One.printInformation()

print("   ")

student_One = student("Jobs", "18", "123")
student_One.printInformation()

print("   ")

# 接着让我们来对子类实例调用父类的被覆写的方法
super(student, student_One).printInformation()
```


运行的结果为：

```python
姓名为：John
年龄为：16
   
学生的姓名为：Jobs
学生的年龄为：18
学生的ID为：123
   
姓名为：Jobs
年龄为：18
```


在这个程序的最后一部分，我们使用了super函数来调用了父类中被子类覆写的方法：

```python
super(子类名, 子类生成的实列名).方法名称()
```


所以在这个时候我们输出的结果为：

```python
姓名为：Jobs
年龄为：18
```


因为父类person中的printInformation函数只输出了name和age两个属性。



