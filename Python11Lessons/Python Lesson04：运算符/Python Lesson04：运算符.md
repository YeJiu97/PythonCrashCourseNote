# Python Lesson04：运算符

## 算数运算符

Python的算数运算符如下所示：以下假设变量： a=10，b=20

|运算符|描述|实例|
|---|---|---|
|+|加 - 两个对象相加|a + b 输出结果 30|
|-|减 - 得到负数或是一个数减去另一个数|a - b 输出结果 -10|
|*|乘 - 两个数相乘或是返回一个被重复若干次的字符串|a * b 输出结果 200|
|/|除 - x除以y|b / a 输出结果 2|
|%|取模 - 返回除法的余数|b % a 输出结果 0|
|**|幂 - 返回x的y次幂|a**b 为10的20次方， 输出结果 100000000000000000000|
|//|取整除 - 返回商的整数部分（向下取整）|>>> 9//2|
|4|||







> -9//2


-5 |

我们可以对算数运算符进行实践：

```python
a = 10
b = 25

print(a+b)
print(a-b)
print(a*b)
print(a/b)
print(a**b)
print(a%b)
print(a//b)
```


运算的结果为：

```python
35
-15
250
0.4
10000000000000000000000000
10
0
```


## 比较运算符

以下假设变量： **a=10，b=20**：

|运算符|描述|实例|
|---|---|---|
|==|等于 - 比较对象是否相等|(a == b) 返回 False。|
|!=|不等于 - 比较两个对象是否不相等|(a != b) 返回 true.|
|<>|不等于 - 比较两个对象是否不相等。python3 已废弃。|(a <> b) 返回 true。这个运算符类似 != 。|
|>|大于 - 返回x是否大于y|(a > b) 返回 False。|
|<|小于 - 返回x是否小于y。所有比较运算符返回1表示真，返回0表示假。这分别与特殊的变量True和False等价。|(a < b) 返回 true。|
|>=|大于等于 - 返回x是否大于等于y。|(a >= b) 返回 False。|
|<=|小于等于 - 返回x是否小于等于y。|(a <= b) 返回 true。|



我们可以进行实践：

```python
a = 10
b = 20

print(a==b)
print(a!=b)
print(a>b)
print(a<b)
print(a>=b)
print(a<=b)
```


运行的结果为：

```python
False
True
False
True
False
True
```


## **Python逻辑运算符**

Python语言支持逻辑运算符，以下假设变量 a 为 10, b为 20:

|运算符|逻辑表达式|描述|实例|
|---|---|---|---|
|and|x and y|布尔"与" - 如果 x 为 False，x and y 返回 False，否则它返回 y 的计算值。|(a and b) 返回 20。|
|or|x or y|布尔"或" - 如果 x 是非 0，它返回 x 的计算值，否则它返回 y 的计算值。|(a or b) 返回 10。|
|not|not x|布尔"非" - 如果 x 为 True，返回 False 。如果 x 为 False，它返回 True。|not(a and b) 返回 False|



我们可以先对and进行实践：

```python
a = 10
b = 20

print(a==a and b==a)   # a==a为true，则返回b==a的结果，结果为False
print(a==b and b==b)   # a==b为False，则返回False，这时候b==b为true，但是没有任何的影响
print(a==b and b==b)   # a==b为False，则直接返回False
print(a==a and b==b)   # a==a为True，这时候返回b==b的结果，所以结果为True
```


运行的结果为：

```python
False
False
False
True
```


同样的，我们也可以对or进行实践：

```python
a = 10
b = 20

# 0表示的是False
# 1表示的是True

print(a or b)   # a这个时候是非0，也就是非False，那么返回的是a的结果
print(0 or b)   # 这个时候是0，也就是False，那么返回的是b的结果
```


运行的结果为：

```python
10
20
```


接着是not：

```python
a = 10
b = 20

# 0表示的是False
# 1表示的是True

print(not a)
print(not b)
print(not 0)
```


运行的结果为：

```python
False
False
True
```


我们可以理解为以0为基准点，如果是0，则是False，如果不是0，则是被判定为True，而not则是结果取反，比如说not 0，就是 不是False，那么结果为True。

