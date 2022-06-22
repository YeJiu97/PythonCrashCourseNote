# Python语言：元组

Python 的元组与列表类似，不同之处在于元组的元素不能修改。

元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。

```python
tup1 = ('aaa', 'bbb', 1997, 2000)
tup2 = (1, 2, 3, 4, 5 )
tup3 = "a", "b", "c", "d" 

print(type(tup1))
print(type(tup2))
print(type(tup3))
```


运行的结果为：

```python
<class 'tuple'>
<class 'tuple'>
<class 'tuple'>
```


不过元组中的元素虽然不能够被删除，但是我们可以将两个元组组合成为一个新的元组：

```python
tup1 = ('aaa', 'bbb', 1997, 2000)
tup2 = (1, 2, 3, 4, 5 )
tup3 = "a", "b", "c", "d" 

print(tup1+tup2)
```


运行结果为：

```python
('aaa', 'bbb', 1997, 2000, 1, 2, 3, 4, 5)
```


当然我们也能够删除掉整个元组：

```python
tup = ('aaa', 'bbb')
 
print (tup)
del tup
print ("删除后的元组 tup : ")
print (tup)
```


运行的结果为：

```python
删除后的元组 tup : 
Traceback (most recent call last):
  File "test.py", line 8, in <module>
    print (tup)
NameError: name 'tup' is not defined
```


输出变量会有异常信息。

如果我们有需求，我们也可以将列表转换为元组：

```python
list1= ['Google', 'Taobao', 'Runoob', 'Baidu']
tuple1=tuple(list1)
print(tuple1)
```


