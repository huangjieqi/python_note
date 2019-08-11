# 1.函数关键字
- 函数也是一个对象
  - 对象是内存中专门用来存储数据的一块区域
  - 函数可以用来保存一些可执行的代码，并且可以在需要时，对这些语句进行多次的调用

# 2.函数的定义
- 函数代码块以 def 关键词开头，后接函数标识符名称和圆括号()。
- 任何传入参数和自变量必须放在圆括号中间。圆括号之间可以用于定义参数。
- 函数的第一行语句可以选择性地使用文档字符串—用于存放函数说明。
- 函数内容以冒号起始，并且缩进。
- return [表达式] 结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回 None。
  - 创建函数：
  ```python
      def 函数名([形参1,形参2,...形参n]) :
          代码块
  ```
    - 函数名必须要符号标识符的规范
        （可以包含字母、数字、下划线、但是不能以数字开头）    
  - 函数中保存的代码不会立即执行，需要调用函数代码才会执行
  - 调用函数：
      函数对象()
  - 定义函数一般都是要实现某种功能的

# 3.函数参数与作用域
## 函数的参数
    - 在定义函数时，可以在函数名后的()中定义数量不等的形参，
        多个形参之间使用,隔开
    - 形参（形式参数），定义形参就相当于在函数内部声明了变量，但是并不赋值
    - 实参（实际参数）
        - 如果函数定义时，指定了形参，那么在调用函数时也必须传递实参，
            实参将会赋值给对应的形参，简单来说，有几个形参就得传几个实参

## 作用域（scope）
### 作用域指的是变量生效的区域
### 在Python中一共有两种作用域
#### 全局作用域
  - 全局作用域在程序执行时创建，在程序执行结束时销毁
  - 所有函数以外的区域都是全局作用域
  - 在全局作用域中定义的变量，都属于全局变量，全局变量可以在程序的任意位置被访问
  
#### 函数作用域
  - 函数作用域在函数调用时创建，在调用结束时销毁
  - 函数每调用一次就会产生一个新的函数作用域
  - 在函数作用域中定义的变量，都是局部变量，它只能在函数内部被访问
  
#### 变量的查找
  - 当我们使用变量时，会优先在当前作用域中寻找该变量，如果有则使用，
      如果没有则继续去上一级作用域中寻找，如果有则使用，
      如果依然没有则继续去上一级作用域中寻找，以此类推
      直到找到全局作用域，依然没有找到，则会抛出异常
          NameError: name 'a' is not defined

# 4.函数返回值
- 返回值，返回值就是函数执行以后返回的结果
- 可以通过 return 来指定函数的返回值
- 可以之间使用函数的返回值，也可以通过一个变量来接收函数的返回值

```python
def sum(*nums):
    # 定义一个变量，来保存结果
    result = 0
    # 遍历元组，并将元组中的数进行累加
    for n in nums :
        result += n
    print(result)

# sum(123,456,789)
 

# return 后边跟什么值，函数就会返回什么值
# return 后边可以跟任意的对象，返回值甚至可以是一个函数
def fn():
    # return 'Hello'
    # return [1,2,3]
    # return {'k':'v'}
    def fn2() :
        print('hello')

    return fn2 # 返回值也可以是一个函数

r = fn() # 这个函数的执行结果就是它的返回值
# r()
# print(fn())
# print(r)

# 如果仅仅写一个return 或者 不写return，则相当于return None 
def fn2() :
    a = 10
    return 

# 在函数中，return后的代码都不会执行，return 一旦执行函数自动结束
def fn3():
    print('hello')
    return
    print('abc')

# r = fn3()
# print(r)

def fn4() :
    for i in range(5):
        if i == 3 :
            # break 用来退出当前循环
            # continue 用来跳过当次循环
            return # return 用来结束函数
        print(i)
    print('循环执行完毕！')

# fn4()

def sum(*nums):
    # 定义一个变量，来保存结果
    result = 0
    # 遍历元组，并将元组中的数进行累加
    for n in nums :
        result += n
    return result

r = sum(123,456,789)

# print(r + 778)

def fn5():
    return 10

# fn5 和 fn5()的区别
print(fn5) # fn5是函数对象，打印fn5实际是在打印函数对象 <function fn5 at 0x05771BB8>
print(fn5()) # fn5()是在调用函数，打印fn5()实际上是在打印fn5()函数的返回值 10
```

# 5.file(文件)

## 打开文件方式（读写两种方式）

open(file, mode='r', buffering=-1, encoding_=None, errors=None, newline=None, closefd=True, opener=None)
使用open函数来打开一个文件
参数：
  file 要打开的文件的名字（路径）
返回值：
  返回一个对象，这个对象就代表了当前打开的文件
### 读取文件的两种方式

```python
import pprint
import os
file_name = 'demo.txt'

with open(file_name , encoding='utf-8') as file_obj:
    # readline()
    # 该方法可以用来读取一行内容
    # print(file_obj.readline(),end='')
    # print(file_obj.readline())
    # print(file_obj.readline())

    # readlines()
    # 该方法用于一行一行的读取内容，它会一次性将读取到的内容封装到一个列表中返回
    # r = file_obj.readlines()
    # pprint.pprint(r[0])
    # pprint.pprint(r[1])
    # pprint.pprint(r[2])

    for t in file_obj:
        print(t)
```
### 文件的写入
```python
# 使用open()打开文件时必须要指定打开文件所要做的操作（读、写、追加）
# 如果不指定操作类型，则默认是 读取文件 ， 而读取文件时是不能向文件中写入的
# r 表示只读的
# w 表示是可写的，使用w来写入文件时，如果文件不存在会创建文件，如果文件存在则会截断文件
#   截断文件指删除原来文件中的所有内容
# a 表示追加内容，如果文件不存在会创建文件，如果文件存在则会向文件中追加内容
# x 用来新建文件，如果文件不存在则创建，存在则报错
# + 为操作符增加功能
#   r+ 即可读又可写，文件不存在会报错
#   w+
#   a+
# with open(file_name , 'w' , encoding='utf-8') as file_obj:
# with open(file_name , 'r+' , encoding='utf-8') as file_obj:
with open(file_name , 'x' , encoding='utf-8') as file_obj:
    # write()来向文件中写入内容，
    # 如果操作的是一个文本文件的话，则write()需要传递一个字符串作为参数
    # 该方法会可以分多次向文件中写入内容
    # 写入完成以后，该方法会返回写入的字符的个数
    file_obj.write('aaa\n')
    file_obj.write('bbb\n')
    file_obj.write('ccc\n')
    r = file_obj.write(str(123)+'123123\n')
    r = file_obj.write('今天天气真不错')
    print(r)
```

## 文件对象的操作方法
```python
import os
from pprint import pprint

# os.listdir() 获取指定目录的目录结构
# 需要一个路径作为参数，会获取到该路径下的目录结构，默认路径为 . 当前目录
# 该方法会返回一个列表，目录中的每一个文件（夹）的名字都是列表中的一个元素
r = os.listdir()

# os.getcwd() 获取当前所在的目录
r = os.getcwd()

# os.chdir() 切换当前所在的目录 作用相当于 cd
# os.chdir('c:/')

# r = os.getcwd()

# 创建目录
# os.mkdir("aaa") # 在当前目录下创建一个名字为 aaa 的目录

# 删除目录
# os.rmdir('abc')

# open('aa.txt','w')
# 删除文件
# os.remove('aa.txt')

# os.rename('旧名字','新名字') 可以对一个文件进行重命名，也可以用来移动一个文件
# os.rename('aa.txt','bb.txt')
os.rename('bb.txt','c:/users/lilichao/desktop/bb.txt')

pprint(r)
```

## [学习对excel及csv文件进行操作](https://www.cnblogs.com/BlueskyRedsea/p/10344506.html)

# 6.os模块

[os模块官方文本](https://docs.python.org/3/library/os.html)
os 模块的常用函数的用法：
```python
import os
# 显示导入依赖模块的操作系统的名称
print(os.name)
# 获取PYTHONPATH环境变量的值
print(os.getenv('PYTHONPATH'))
# 返回当前系统的登录用户名
print(os.getlogin())
# 获取当前进程ID
print(os.getpid())
# 获取当前进程的父进程ID
print(os.getppid())
# 返回当前系统的CPU数量
print(os.cpu_count())
# 返回路径分隔符
print(os.sep)
# 返回当前系统的路径分隔符
print(os.pathsep)
# 返回当前系统的换行符
print(os.linesep)
# 返回适合作为加密使用的、最多3个字节组成的bytes
print(os.urandom(3))
```