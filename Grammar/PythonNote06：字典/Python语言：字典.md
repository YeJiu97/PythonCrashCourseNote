# Python语言：字典

# 创建与访问

字典是一种可变容器模型，且可存储任意类型对象。

键一般是唯一的，如果重复最后的一个键值对会替换前面的，值不需要唯一。

值可以取任何数据类型，但键必须是不可变的，如字符串，数字或元组。

我们可以生成一个字典来存储学生信息：

```python
student_information = {'s111':'John', 's112':'Harry', 'a113':'Joe'}
print(student_information["a113"])

student = student_information["s111"]
print(student)
```


运行的结果为：

```python
Joe
John
```


# 使用字典

要添加键—值对，可依次指定字典名、用方括号括起的键和相关联的值。

例子为：

```python
student_information = {'s111':'John', 's112':'Harry', 'a113':'Joe'}
student_information['s114'] = "Smith"

print(student_information['s114'])
```


运行的结果为：

```python
Smith
```


需要注意的是，对于字典而言，字典中的键值对不存在着位置，也就是说我们并不能够通过索引来访问键值对。

要修改字典中的值，可依次指定字典名、用方括号括起的键以及与该键相关联的新值。

```python
student_information = {'s111':'John', 's112':'Harry', 'a113':'Joe'}
student_information['s111'] = 'Jobs'

print(student_information['s111'])
```


运行的结果为：

```python
Jobs
```


如果要删除，则可以使用del语句来进行删除：

```python
student_information = {'s111':'John', 's112':'Harry', 'a113':'Joe'}
print(student_information)

del student_information['s111']
print(student_information)
```


运行的结果为：

```python
{'s111': 'John', 's112': 'Harry', 'a113': 'Joe'}
{'s112': 'Harry', 'a113': 'Joe'}
```


# 遍历字典

如果我们想要遍历字典，我们同样可以采取for循环来遍历所有的键值对：

```python
user_0 = {
  'username': 'efermi',
  'first': 'enrico',
  'last': 'fermi',
 }
for key, value in user_0.items():
  print("\nKey: " + key)
  print("Value: " + value)
```


运行的结果为：

```python
Key: username
Value: efermi

Key: first
Value: enrico

Key: last
Value: fermi
```


如果我们并不需要遍历所有的键值，而是仅仅需要遍历所有的值，那么我们可以使用keys()函数来实现：

```python
user_0 = {
  'username': 'efermi',
  'first': 'enrico',
  'last': 'fermi',
 }

for user in user_0.keys():
  print(user.title())
```


运行的结果为：

```python
Username
First
Last
```


