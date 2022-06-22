# Python办公：读写CSV文件

## 什么是CSV文件

CSV （逗号分隔值）是一种简单的文件格式，用于存储表格数据，例如电子表格或数据库。CSV 文件以纯文本形式存储表格数据（数字和文本）。

文件的每一行都是一条数据记录。每条记录由一个或多个字段组成，以逗号分隔。使用逗号作为字段分隔符是此文件格式名称的来源。

对于在 Python 中处理 CSV 文件，有一个名为 `csv` 的内置模块。

## 写入CSV文件

写入 CSV 文件我们借助 Python 的内置库 `csv`，生成一个 `csvwriter` 对象，可以选择一行一行写入，也可以选择一次写入多行。

```python
import csv   # 首先导入csv模块

# 给出标题
fields = ['名字', '职位', '工龄', '评分']

# 使用[]来创建数组
rows = [["小红", "CEO", "2", "9.9"],
    ["小蓝", "Boss", "3", "9.5"],
    ["小红", "Manager", "3.4", "9.0"],
    ["小白", "Worker", "4.5", "9.2"]]

# 写入到csv文件中
with open('employees.csv', 'w') as csvfile:
  # 创建一个csv writer 对象
  csvwriter = csv.writer(csvfile)
  # 一次写一行
  csvwriter.writerow(fields)
  # 一次写入多行
  csvwriter.writerows(rows)
```


运行的结果为：

![](image/0llc7irgtb.png "")

## 读取

读取 CSV 文件我们借助 Python 的 `csv` 内置库，生成一个 `csvreader` 对象。

我们在之前的代码之后加入一段代码，最终：

```python
import csv
  
fields = ['Name', 'Branch', 'Year', 'CGPA']
  
rows = [ ['Nikhil', 'COE', '2', '9.0'],
         ['Sanchit', 'COE', '2', '9.1'],
         ['Aditya', 'IT', '2', '9.3'],
         ['Sagar', 'SE', '1', '9.5'],
         ['Prateek', 'MCE', '3', '7.8'],
         ['Sahil', 'EP', '2', '9.1']]
 
  
# writing to csv file
with open('demo.csv', 'w') as csvfile:
    # 创建一个 csv writer 对象
    csvwriter = csv.writer(csvfile)
    # 一次写一行
    csvwriter.writerow(fields)
    # 一次写入多行
    csvwriter.writerows(rows)

with open('demo.csv','r') as csvfile:
    csvreader=csv.reader(csvfile)
    print(list(csvreader))
```


运行的结果为：

```python
[['名字', '职位', '工龄', '评分'], [], ['小红', 'CEO', '2', '9.9'], [], ['小蓝', 'Boss', '3', '9.5'], [], ['小红', 'Manager', '3.4', '9.0'], [], ['小白', 'Worker', '4.5', '9.2'], []]
```


