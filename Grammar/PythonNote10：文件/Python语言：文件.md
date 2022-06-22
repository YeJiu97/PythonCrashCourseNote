# Python语言：文件

# 读取整个文件

文本文件中存储了大量的数据，要使用文本文件中的信息，首先需要将信息读取到内存中。

我们可以采取一次性读取文件的全部内容的方式：

我们现在本地建立一个文本文件（pi_digits.txt），并且在其中写入π的部分值：

```python
3.1415926
  535
```


接着创建一个程序来读取这个文件，并且将其打印到屏幕上：

```python
with open('pi_digits.txt') as file_object:
  contents = file_object.read()
  print(contents)
```


我们首先用到的是open()函数，open()函数可以用来打开文件，这个函数会接受一个参数，也就是要被打开的文件的名称。

函数open()返回一个表示文件的对象。在这里，open('pi_digits.txt')返回一个表示文件pi_digits.txt的对象；Python将这个对象存储在我们将在后面使用的变量中。

关键字with在不再需要访问文件后将其关闭。在这个程序中，注意到我们调用了open()，但没有调用close()；你也可以调用open()和close()来打开和关闭文件，但这样做时，如果程序存在bug，导致close()语句未执行，文件将不会关闭。

当我们有了文件对象file_object之后，我们便可以调用.read()函数来读取这个文件的全部内容，并且将其作为一个长长的字符串存储在变量contents中。

通过打印contents的值，我们就可以将这个文本文件的全部内容显示出来：

```python
3.1415926

        535
```


我们会发现多了一个空行，这是因为根据你组织文件的方式，有时可能要打开不在程序文件所属目录中的文件。例如，你可能将程序文件存储在了文件夹python_work中，而在文件夹python_work中，有一个名为text_files的文件夹，用于存储程序文件操作的文本文件。

虽然文件夹text_files包含在文件夹python_work中，但仅向open()传递位于该文件夹中的文件的名称也不可行，因为Python只在文件夹python_work中查找，而不会在其子文件夹text_files中查找。要让Python打开不与程序文件位于同一个目录中的文件，需要提供文件路径，它让Python到系统的特定位置去查找。

由于文件夹text_files位于文件夹python_work中，因此可使用相对文件路径来打开该文件夹中的文件。相对文件路径让Python到指定的位置去查找，而该位置是相对于当前运行的程序所在目录的。

在windows系统中，在文件路径中使用反斜杠（\）而不是斜杠（/）：

```python
with open('text_files\filename.txt') as file_object:
```


或者我们可以将文件在计算机中的准确位置告诉Python：

```python
file_path = 'C:\Users\ehmatthes\other_files\text_files\filename.txt'
with open(file_path) as file_object:
```


# 逐行读取

有些情况之下，我们需要的是检查文件中的每一行，来查找特定的信息或者以某一种方式来修改文本中的文本：

```python
filename = 'pi_digits.txt'

with open(filename) as file_object:
  for line in file_object:
    print(line)
```


运行的结果为：

```python
3.1415926

        535
```


同样的我们可以加上.restrip()函数：

```python
3.1415926
        535
```


现在输出的结果便和原文件的相同了。

# 创建一个包含文件各行内容的列表

使用关键字with时，open()返回的文件对象只在with代码块内可用。如果要在with代码块外访问文件的内容，可在with代码块内将文件的各行存储在一个列表中，并在with代码块外使用该列表：

```python
filename = 'pi_digits.txt'

with open(filename) as file_object:
  lines = file_object.readlines()

for line in lines:
    print(line.rstrip())
```


运行的结果为：

```python
3.1415926
        535
```


# 小数点精确

如果我们需要对小数点之后的位置进行精确：

```python
filename = 'pi_digits.txt'

with open(filename) as file_object:
  lines = file_object.readlines()

pi_string = ''

for line in lines:
  pi_string += line.strip()

print(pi_string[:5] + "...")
print(len(pi_string))
```


运行的结果为：

```python
3.141...
12
```


