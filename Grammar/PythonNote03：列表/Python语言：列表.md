# Python语言：列表

# 列表与列表的访问

列表是由一系列按照特定顺序排列的元素组成。

在Python中，用方括号[]来表示列表，并用逗号来分隔其中的元素。

一下是一个简单的例子：

```python
studentName = ["aaa", "bbb", "ccc"]
```


我们可以用直接打印的方式打印出来列表中的内容：

```python
['aaa', 'bbb', 'ccc']
```


可见直接打印将会将列表以整个列表的形式打印出来，包括了[]和""。

我们可以通过元素所在的位置的方式来对列表中的某一个元素进行访问：

```python
studentName = ["aaa", "bbb", "ccc"]
print(studentName[1])
```


运行的结果为：

```python
bbb
```


这是因为对于Python语言而言，索引是从0开始而不是从1开始的。

如果我们想要访问的是我们日常生活中所认为的第一个元素，那么我们需要制定的索引是0：

```python
studentName = ["aaa", "bbb", "ccc"]
print(studentName[0])
```


运行的结果为：

```python
aaa
```


如果我们想要访问的是列表中的最后一个元素，则可以直接使用-1作为索引值：

```python
studentName = ["aaa", "bbb", "ccc"]
print(studentName[-1])
```


运行的结果为：

```python
ccc
```


我们可以在访问列表的值的同时使用该值进行赋值：

```python
studentName = ["aaa", "bbb", "ccc"]
message = "The first student's name is :" + studentName[0]
print(message)
```


运行的结果为：

```python
The first student's name is :aaa
```


# 修改，添加和删除元素

列表的使用大多数是动态的，列表被创建之后还会出现删除，修改，增添等操作。

如果我们要修改列表的某一个元素，我们可以指定列表名和需要被修改的元素的索引，再指定该元素的新值：

```python
studentName = ["aaa", "bbb", "ccc"]
studentName[0] = "aaac"
print(studentName)
```


运行的结果为：

```python
['aaac', 'bbb', 'ccc']
```


如果我们要做的是添加新值，则可以采用append()函数来在末尾进行添加：

```python
studentName = ["aaa", "bbb", "ccc"]
studentName.append("ddd")
print(studentName)
```


运行的结果为：

```python
['aaa', 'bbb', 'ccc', 'ddd']
```


我们其实也可以先创建一个空列表，然后再通过一系列的append()语句来添加元素，例子如下所示：

```python
studentName = []
studentName.append("aaa")
studentName.append("bbb")
studentName.append("ccc")

print(studentName)
```


运行的结果为：

```python
['aaa', 'bbb', 'ccc']
```


但是还有一种情况是，我们并不是在列表的末尾插入一个新的元素，而是需要在列表的指定位置插入一个新的元素，这个时候我们就需要用到insert()函数了：

```python
studentName = ['aaa', 'bbb', 'ddd']
studentName.insert(2, "ccc")

print(studentName)
```


运行的结果为：

```python
['aaa', 'bbb', 'ccc', 'ddd']
```


insert()函数的语法如下所示：

```python
insert(positionValue, elementValue)
```


positionValue表示的是插入的索引位置，而elementValue表示的是插入的元素的值。

如果我们需要做的是从既有的列表中删除某一个指定的元素，那么我们可以使用del语句来进行删除：

```python
studentName = ['aaa', 'bbb', 'ddd']
del studentName[0]

print(studentName)
```


运行的结果为：

```python
['bbb', 'ddd']
```


需要注意的是，如果我们使用的是del语句来进行删除，那么被删除的值就无法在被访问了。

有些时候我们需要将一个值从列表中删除，但是同时我们还需要使用到这个值，这个时候我们就可以使用pop()函数来进行：

```python
StudentListOne = ["L11", "L12", "L13"]
StudentListTwo = ["L21"]

StudentListTwo.append(StudentListOne.pop())

print(StudentListTwo)
print(StudentListOne)
```


在这里，我们将StudenListOne这一列表中的最后一个元素弹出，并且使用这个被弹出的元素的值，然后通过append()函数来讲其添加到StudentListTwo这一列表的末尾。

当然pop()函数不仅仅是能够弹出列表末尾的元素，只需要在括号中添加元素的索引位置，便可以弹出指定位置的元素：

```python
StudentListOne = ["L11", "L12", "L13"]
StudentListTwo = ["L21"]

StudentListTwo.append(StudentListOne.pop(0))

print(StudentListTwo)
print(StudentListOne)
```


运行的结果为：

```python
['L21', 'L11']
['L12', 'L13']
```


有些时候我们并不清楚需要被弹出的元素的具体的索引位置，但是我们知道需要被弹出的元素的具体的值，这个时候我们就可以使用remove()函数来进行操作：

```python
StudentListOne = ["L11", "L12", "L13"]
StudentListOne.remove("L11")

print(StudentListOne)
```


运行的结果为：

```python
['L12', 'L13']
```


不过需要注意的是，remove()函数只会删除列表中第一个与制定值相符合的元素，如果存在着多个与指定值相符合的元素，则需要通过反复的调用remove()函数来进行删除：

```python
StudentListOne = ["L11", "L12", "L13", "L11"]
StudentListOne.remove("L11")

print(StudentListOne)
```


运行的结果为：

```python
['L12', 'L13', 'L11']
```


如果我们想要对列表进行排序，则可以使用sort()函数进行实现：

```python
StudentListOne = ["L13", "L12", "L11"]
StudentListOne.sort()

print(StudentListOne)
```


运行的结果为：

```python
['L11', 'L12', 'L13']
```


如果我们需要的是逆向排序，则需要向sort()函数传递reverse=True作为参数值：

```python
StudentListOne = ["L13", "L12", "L11"]
StudentListOne.sort(reverse=True)

print(StudentListOne)
```


运行的结果为：

```python
['L13', 'L12', 'L11']
```


还有一些特殊的情况，那就是我们并不想要改变列表中元素的排序，但是同时我们想要获得列表中的元素被排序之后的结果：

```python
StudentListOne = ["L13", "L12", "L11"]

print(sorted(StudentListOne))
print(StudentListOne)
```


运行的结果为：

```python
['L11', 'L12', 'L13']
['L13', 'L12', 'L11']
```


可以使用sorted()进行操作并没有改变原来的列表的值。

如果我们想要反转列表中的元素，则可以使用reverse()函数来进行实现：

```python
StudentListOne = ["L13", "L12", "L11"]
StudentListOne.reverse()

print(StudentListOne)
```


运行的结果为：

```python
['L11', 'L12', 'L13']
```


需要注意的是，reverse()函数是永久的改变了列表中的元素的排列，当然我们可以再次使用reverse()函数，从而是列表中的元素回到原来的排列。

# 遍历整个列表

如果我们需要将列表中的每一个元素分别打印出来，这个时候我们就可以使用for循环来进行实现：

```python
studentName = ["aaa","bbb","ccc","ddd"]
for student in studentName:
    print(student)
```


运行的结果为：

```python
aaa
bbb
ccc
ddd
```


在这一个例子中使用到了for循环，for X in Xs可以被理解为对于在Xs中的每一个X而言。Xs是一个列表，但是X仅仅是一个临时变量，所以X的名称并不重要，只需要不与其他的变量的名称相互重合。

相对于其他的编程语言通过（）或者｛｝来进行标注，Python语言使用缩进来进行表示，有着相同缩进的代码是同一个代码块。

不要遗漏冒号。

# 创建数值列表

如果我们需要生成一系列的数字，那么我们可以使用range()函数来进行：

```python
for value in range(5):
    print(value)
```


运行的结果为：

```python
0
1
2
3
4
```


通过输出的结果不难发现：

1. Python语言是从0开始生成数字的
2. 括号中的数字并不会被生成

如果我们希望从1开始生成，那么我们就需要制定初始生成值：

```python
for value in range(1,5):
  print(value)
```


结果为：

```python
1
2
3
4
```


如果我们希望包含数值我，那么我们给出的结束值需要是6：

```python
for value in range(1,6):
  print(value)
```


运行的结果为：

```python
1
2
3
4
6
```


当我们通过range()函数生成了一组数字之后，我们可以使用list()函数将其转换为一个列表：

```python
numbers = list(range(1,6))
print(numbers)
```


运行的结果为：

```python
[1, 2, 3, 4, 5]
```


或者我们也可以制定步长：

```python
even_numbers = list(range(2,11,2))
print(even_numbers)
```


运行的结果为：

```python
[2, 4, 6, 8, 10]
```


函数range()从2开始数，然后不断地加2，直到达到或超过终值（11）。

我们也可以将range()函数和append()函数相互结合来生成列表：

```python
squares = []
for value in range(1,11):
  square = value**2
  squares.append(square)

print(squares)
```


输出的结果为：

```python
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```


对于数字列表，有着min()，max()和sum()三个简单的函数来对其进行处理：

```python
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
print(min(digits))
print(max(digits))
print(sum(digits))
```


运行的结果为：

```python
0
9
45
```


# 获得部分列表

与range()函数一样，我们可以通过指定第一个元素和最后一个元素的索引，来获得一个列表的切片：

```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print(players[0:3])
```


运行的结果为：

```python
['charles', 'martina', 'michael']
```


可以发现无论是range()还是[]切片，实际上都是采用左闭右开的原则，即包括左边的数值，但是不包括右边的数值。

同样的我们还可以将切片和循环组合使用：

```python
players = ['charles', 'martina', 'michael', 'florence', 'eli']
print("Here are the first three players on my team:")
for player in players[:3]: 
  print(player.title())
```


运行的结果为：

```python
Here are the first three players on my team:
Charles
Martina
Michael
```


要复制列表，可创建一个包含整个列表的切片，方法是同时省略起始索引和终止索引（[:]）：

```python
my_foods = ['pizza', 'falafel', 'carrot cake']
friend_foods = my_foods[:]

print("My favorite foods are:")
print(my_foods)

print("\nMy friend's favorite foods are:")
print(friend_foods)
```


运行的结果为：

```python
My favorite foods are:
['pizza', 'falafel', 'carrot cake']

My friend's favorite foods are:
['pizza', 'falafel', 'carrot cake']
```




