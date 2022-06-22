# Python语言：类

# 创建和使用类

我们可以创建Dog类，来存储名字和年龄，并且让每一条小狗有着蹲下和打滚的能力：

```
class Dog():
  """一次模拟小狗的简单尝试"""

  def __init__(self, name, age):
    """初始化属性name和age"""
    self.name = name
    self.age = age

  def sit(self):
    """模拟小狗被命令时蹲下"""
    print(self.name.title() + " is now sitting.")

  def roll_over(self):
    """模拟小狗被命令时打滚"""
    print(self.name.title() + " rolled over!")
```


首先我们用class来进行声明，class可以告诉Python语言这是类类型，需要注意的地方在于首字母需要大写；首先是__init__()方法，这是要给特殊的方法，当你根据Dog类创新实例时，Python都会自动运行它，需要注意的地方在于这里是两个下划线__，这是为了避免Python默认方法与普通方法发生名称冲突，**init__在这里包含了三个形式参数：self，name和age，形式参数self是必不可少的，并且需要在其他形式参数的前面。因为Python调用这个__init**()方法来创建Dog实例时，将自动传入实参self。每个与类相关联的方法调用都自动传递实参self，它是一个指向实例本身的引用，让实例能够访问类中的属性和方法。

初始化属性中，定义的两个变量都有前缀self。。以self为前缀的变量都可供类中的所有方法使用，我们还可以通过类的任何实例来访问这些变量。[self.name](http://self.name) = name获取存储在形参name中的值，并将其存储到变量name中，然后该变量被关联到当前创建的实例。

我们可以使用Dog类来生成一个实例试试看：

```
class Dog():
  """一次模拟小狗的简单尝试"""

  def __init__(self, name, age):
    """初始化属性name和age"""
    self.name = name
    self.age = age

  def sit(self):
    """模拟小狗被命令时蹲下"""
    print(self.name.title() + " is now sitting.")

  def roll_over(self):
    """模拟小狗被命令时打滚"""
    print(self.name.title() + " rolled over!")

my_dog = Dog('willie', 6)

print("My dog's name is " + my_dog.name.title() + ".")
print("My dog is " + str(my_dog.age) + " years old.")
```


运行的结果为：

```
My dog's name is Willie.
My dog is 6 years old.
```


我们首先用Dog()类来对my_dog进行了实例化，然后传递了willie和6两个实参；接着我们使用my_dog.name来访问my_dog中的name的值，同样的用这样的方法访问了my_dog中age的值。

如果我们想要的是调用方法，那么我们可以：

```
class Dog():
  """一次模拟小狗的简单尝试"""

  def __init__(self, name, age):
    """初始化属性name和age"""
    self.name = name
    self.age = age

  def sit(self):
    """模拟小狗被命令时蹲下"""
    print(self.name.title() + " is now sitting.")

  def roll_over(self):
    """模拟小狗被命令时打滚"""
    print(self.name.title() + " rolled over!")

my_dog = Dog('willie', 6)

print("My dog's name is " + my_dog.name.title() + ".")
print("My dog is " + str(my_dog.age) + " years old.")
my_dog.sit()
my_dog.roll_over()
```


运行的结果为：

```
My dog's name is Willie.
My dog is 6 years old.
Willie is now sitting.
Willie rolled over!
```


同样的我们还可以生成多个实例：

```
class Dog():
  """一次模拟小狗的简单尝试"""

  def __init__(self, name, age):
    """初始化属性name和age"""
    self.name = name
    self.age = age

  def sit(self):
    """模拟小狗被命令时蹲下"""
    print(self.name.title() + " is now sitting.")

  def roll_over(self):
    """模拟小狗被命令时打滚"""
    print(self.name.title() + " rolled over!")

my_dog = Dog('willie', 6)
your_dog = Dog('lucy', 3)
print("My dog's name is " + my_dog.name.title() + ".")
print("My dog is " + str(my_dog.age) + " years old.") 
my_dog.sit()
print("\nYour dog's name is " + your_dog.name.title() + ".")
print("Your dog is " + str(your_dog.age) + " years old.")
your_dog.sit()
```


运行的结果为：

```
My dog's name is Willie.
My dog is 6 years old.
Willie is now sitting.

Your dog's name is Lucy.
Your dog is 3 years old.
Lucy is now sitting.
```


# 使用类和实例

我们来实际的使用一下类。

我们首先生成一个表示汽车的类（Car）：

```
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    """初始化描述汽车的属性"""
    self.make = make
    self.model = model
    self.year = year

  def get_descriptive_name(self):
    """返回整洁的描述性信息"""
    long_name = str(self.year) + ' ' + self.make + ' ' + self.model
    return long_name.title()

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
```


运行的结果为：

```
2016 Audi A4
```


类中的每个属性都必须有初始值，哪怕这个值是0或空字符串。在有些情况下，如设置默认值时，在方法__init__()内指定这种初始值是可行的；如果对某个属性这样做了，就无需包含为它提供初始值的形参。

下面来添加一个名为odometer_reading的属性，其初始值总是为0。我们还添加了一个名为read_odometer()的方法，用于读取汽车的里程表：

```
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    """初始化描述汽车的属性"""
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    """返回整洁的描述性信息"""
    long_name = str(self.year) + ' ' + self.make + ' ' + self.model
    return long_name.title()

  def read_odometer(self):
    """打印一条指出汽车里程的消息"""
    print("This car has " + str(self.odometer_reading) + " miles on it.")

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name()) 
my_new_car.read_odometer()
```


运行的结果为：

```
2016 Audi A4
This car has 0 miles on it.
```


要修改属性的值，最简单的方式是通过实例直接访问它。比如说我们可以将里程表读书设置为23：

```
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    """初始化描述汽车的属性"""
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    """返回整洁的描述性信息"""
    long_name = str(self.year) + ' ' + self.make + ' ' + self.model
    return long_name.title()

  def read_odometer(self):
    """打印一条指出汽车里程的消息"""
    print("This car has " + str(self.odometer_reading) + " miles on it.")

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name()) 
my_new_car.read_odometer()

my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```


运行的结果为：

```
2016 Audi A4
This car has 0 miles on it.
This car has 23 miles on it.
```


或者我们可以通过在类的内部提供修改方法的方式，来通过调用这个方法来修改属性的值：

```
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    """初始化描述汽车的属性"""
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    """返回整洁的描述性信息"""
    long_name = str(self.year) + ' ' + self.make + ' ' + self.model
    return long_name.title()

  def read_odometer(self):
    """打印一条指出汽车里程的消息"""
    print("This car has " + str(self.odometer_reading) + " miles on it.")

  def update_odometer(self, mileage):
     """将里程表读数设置为指定的值"""
     self.odometer_reading = mileage

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name()) 
my_new_car.read_odometer()

my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```


运行的结果为：

```
2016 Audi A4
This car has 0 miles on it.
This car has 23 miles on it.
```


我们也可以通过方法来对属性的值进行递增：

```
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    """初始化描述汽车的属性"""
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    """返回整洁的描述性信息"""
    long_name = str(self.year) + ' ' + self.make + ' ' + self.model
    return long_name.title()

  def read_odometer(self):
    """打印一条指出汽车里程的消息"""
    print("This car has " + str(self.odometer_reading) + " miles on it.")

  def update_odometer(self, mileage):
     """将里程表读数设置为指定的值"""
     self.odometer_reading = mileage

  def increment_odometer(self, miles):
     """将里程表读数增加指定的量"""
     self.odometer_reading += miles

my_used_car = Car('subaru', 'outback', 2013)
print(my_used_car.get_descriptive_name())
my_used_car.update_odometer(23500)
my_used_car.read_odometer()
my_used_car.increment_odometer(100)
my_used_car.read_odometer()
```


运行的结果为：

```
2013 Subaru Outback
This car has 23500 miles on it.
This car has 23600 miles on it.
```






# 继承

编写类的时候，并不总是从空白开始的，如果你要编写的类是另一个现成的特殊版本，可以使用继承。一个类继承另一个类的时候，这个类将会自动继另一个类的所有的属性和方法：原有的类被称之为叫做父类，而新的类则被称之为叫做子类。子类不仅仅包含了父类的所有属性和方法，还可以同时定义自己的属性和方法：

```
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    long_name = str(self.year) + " " + self.make + " " + self.model
    return long_name.title()

  def read_odometer(self):
    print("This car has " + str(self.odometer_reading) + " miles on it.")

  def update_odometer(self, mileage):
    if mileage >= self.odometer_reading:
      self.odometer_reading = mileage
    else:
      print("You can not roll back an odometer!")

  def increment_odometer(self, miles):
    self.odometer_reading += miles

class ElectricCar(Car):
  """电动汽车的独特之处"""

  def __init__(self, make, model, year):
    """初始化父类的属性"""
    super().__init__(make, model, year)

my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
```


当我们创建子类的时候，我们的父类需要和子类在同一个文件中，并且需要位于子类之前。我们在定义子类的时候，我们需要在括号中指定父类的名称。

super()是一个特殊的函数，用来帮助Python将父类和子类关联起来，这行代码让Python调用ElectricCar的父类的方法__init__()，让ElectricCar实例包含父类的所有属性。父类也被称之为叫做超类（superclass），名称super也是因此而得名。

我们接下来可以向子类中添加子类所独有的属性和方法：

```
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    long_name = str(self.year) + " " + self.make + " " + self.model
    return long_name.title()

  def read_odometer(self):
    print("This car has " + str(self.odometer_reading) + " miles on it.")

  def update_odometer(self, mileage):
    if mileage >= self.odometer_reading:
      self.odometer_reading = mileage
    else:
      print("You can not roll back an odometer!")

  def increment_odometer(self, miles):
    self.odometer_reading += miles

class ElectricCar(Car):
  """Represent aspects of a car, specific to electric vehicles."""

  def __init__(self, make, model, year):
 
    """
    电动汽车的独特之处
    初始化父类的属性，再初始化电动汽车特有的属性
    """
    super().__init__(make, model, year)
    self.battery_size = 70

  def describe_battery(self):
    """打印一条描述电瓶容量的消息"""
    print("This car has a " + str(self.battery_size) + "-kWh battery.")

my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
my_tesla.describe_battery()
```


在这里我们向子类添加了新的属性self.battery_size，并且我们将其初始值设置为70。根据ElectricCar类创建的所有实例都将包含这个属性，但是所有Car实例都不会包含这个属性；接着我们向子类添加了describe_battery()方法，这个方法会打印有关电瓶的信息。

运行的结果为：

```
2016 Tesla Model S
This car has a 70-kWh battery.
```


我们也可以在子类中重写父类的方法：

```
def ElectricCar(Car):
 --snip--

  def fill_gas_tank():
    """电动汽车没有油箱"""
    print("This car doesn't need a gas tank!")
```


当有人对电动汽车调用方法fill_gas_tank()方法的时候，Python将会忽略Car类中的方法fill_gas_tank()，而是运行上述代码。

# 导入类

随着你不断地给类添加功能，文件可能变得很长，即便你妥善地使用了继承亦如此。为遵循Python的总体理念，应让文件尽可能整洁。为在这方面提供帮助，Python允许你将类存储在模块中，然后在主程序中导入所需的模块。

我们可以创建一个名为car.py的文件，然后将Car类的代码存储在该文件中：

```python
"""一个可用于表示汽车的类"""
class Car():
  """一次模拟汽车的简单尝试"""
  def __init__(self, make, model, year):
    """初始化描述汽车的属性"""
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    """返回整洁的描述性名称"""
    long_name = str(self.year) + ' ' + self.make + ' ' + self.model
    return long_name.title()

  def read_odometer(self):
    """打印一条消息，指出汽车的里程"""
    print("This car has " + str(self.odometer_reading) + " miles on it.")

  def update_odometer(self, mileage):
    """
    将里程表读数设置为指定的值
    拒绝将里程表往回拨
    """

    if mileage >= self.odometer_reading:
      self.odometer_reading = mileage
    else:
      print("You can't roll back an odometer!")

  def increment_odometer(self, miles):
    """将里程表读数增加指定的量"""
    self.odometer_reading += miles
```


接着我们创建一个名为my_car.py的文件，并且在这个文件中我们将会导入Car类并且创建其实例：

```
from car import Car

my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```


运行的结果为：

```
2016 Audi A4
This car has 23 miles on it.
```


我们也可以在一个模块中存储多个类：

```python
"""一个可用于表示汽车的类"""
class Car():
  """一次模拟汽车的简单尝试"""

  def __init__(self, make, model, year):
    """初始化描述汽车的属性"""
    self.make = make
    self.model = model
    self.year = year
    self.odometer_reading = 0

  def get_descriptive_name(self):
    """返回整洁的描述性名称"""
    long_name = str(self.year) + ' ' + self.make + ' ' + self.model
    return long_name.title()

  def read_odometer(self):
    """打印一条消息，指出汽车的里程"""
    print("This car has " + str(self.odometer_reading) + " miles on it.")

  def update_odometer(self, mileage):
    """
    将里程表读数设置为指定的值
    拒绝将里程表往回拨
    """

    if mileage >= self.odometer_reading:
      self.odometer_reading = mileage
    else:
      print("You can't roll back an odometer!")

  def increment_odometer(self, miles):
    """将里程表读数增加指定的量"""
    self.odometer_reading += miles

class Battery():
  """一次模拟电动汽车电瓶的简单尝试"""
  
  def __init__(self, battery_size=60):
    """初始化电瓶的属性"""
    self.battery_size = battery_size

  def describe_battery(self):
    """打印一条描述电瓶容量的消息"""
    print("This car has a " + str(self.battery_size) + "-kWh battery.")

  def get_range(self):
    """打印一条描述电瓶续航里程的消息"""
    if self.battery_size == 70:
      range = 240
    elif self.battery_size == 85:
      range = 270
    else:
      range = 240

    message = "This car can go approximately " + str(range)
    message += " miles on a full charge."
    print(message)

class ElectricCar(Car):
  """模拟电动汽车的独特之处"""
  def __init__(self, make, model, year):

    """
    初始化父类的属性，再初始化电动汽车特有的属性
    """

    super().__init__(make, model, year)
    self.battery = Battery()
```


接着我们创建一个名为my_electric_car.py的文件，导入ElectricCar类，并创建一辆电动汽车了：

```python
from car import ElectricCar

my_tesla = ElectricCar('tesla', 'model s', 2016)

print(my_tesla.get_descriptive_name())
my_tesla.battery.describe_battery()
my_tesla.battery.get_range()
```


运行的结果为：

```python
2016 Tesla Model S
This car has a 70-kWh battery.
This car can go approximately 240 miles on a full charge.
```


