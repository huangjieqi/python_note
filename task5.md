# 1.类和对象
## 类(class)
    - 我们目前所学习的对象都是Python内置的对象
    - 但是内置对象并不能满足所有的需求，所以我们在开发中经常需要自定义一些对象
    - 类，简单理解它就相当于一个图纸。在程序中我们需要根据类来创建对象
    - 类就是对象的图纸！
    - 我们也称对象是类的实例（instance）
    - 如果多个对象是通过一个类创建的，我们称这些对象是一类对象
    - 像 int() float() bool() str() list() dict() .... 这些都是类
    - a = int(10) # 创建一个int类的实例 等价于 a = 10
    - 我们自定义的类都需要使用大写字母开头，使用大驼峰命名法（帕斯卡命名法）来对类命名

    - 类也是一个对象！
    - 类就是一个用来创建对象的对象！
    - 类是type类型的对象，定义类实际上就是定义了一个type类型的对象
## 什么是对象？
    - 对象是内存中专门用来存储数据的一块区域。
    - 对象中可以存放各种数据（比如：数字、布尔值、代码）
    - 对象由三部分组成：
        1.对象的标识（id）
        2.对象的类型（type）
        3.对象的值（value）

# 使用类创建对象的流程
    1.创建一个变量
    2.在内存中创建一个新对象
    3.将对象的id赋值给变量

## 类的定义
    - 类和对象都是对现实生活中的事物或程序中的内容的抽象
    - 实际上所有的事物都由两部分构成：
        1.数据（属性）
        2.行为（方法）

    - 在类的代码块中，我们可以定义变量和函数，
        变量会成为该类实例的公共属性，所有的该类实例都可以通过 对象.属性名 的形式访问
        函数会成为该类实例的公共方法，所有该类实例都可以通过 对象.方法名() 的形式调用方法

    - 注意：
        方法调用时，第一个参数由解析器自动传递，所以定义方法时，至少要定义一个形参！

    - 实例为什么能访问到类中的属性和方法
        类中定义的属性和方法都是公共的，任何该类实例都可以访问

        - 属性和方法查找的流程
            当我们调用一个对象的属性时，解析器会先在当前对象中寻找是否含有该属性，
                如果有，则直接返回当前的对象的属性值，
                如果没有，则去当前对象的类对象中去寻找，如果有则返回类对象的属性值，
                如果类对象中依然没有，则报错！

        - 类对象和实例对象中都可以保存属性（方法）
            - 如果这个属性（方法）是所有的实例共享的，则应该将其保存到类对象中
            - 如果这个属性（方法）是某个实例独有，则应该保存到实例对象中     

        - 一般情况下，属性保存到实例对象中
            而方法需要保存到类对象中    


## 创建对象的流程
    p1 = Person()的运行流程
        1.创建一个变量
        2.在内存中创建一个新对象
        3.__init__(self)方法执行
        4.将对象的id赋值给变量

## 类的基本结构  
```python 
    class 类名([父类]) :

        公共的属性...

        # 对象的初始化方法
        def __init__(self,...):
            ...

        # 其他的方法    
        def method_1(self,...):
            ...

        def method_2(self,...):
            ...
```

# 2.正则表达式
正则表达式，简称regex，是文本模式的描述方法。它的设计思想是用一种描述性的语言来给字符串定义一个规则，凡是符合规则的字符串，我们就认为它“匹配”了，否则，该字符串就是不合法的。
## re.match函数
re.match尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match()就返回none。
函数参数说明：
参数|描述
---|:--:|---:
pattern	|匹配的正则表达式
string	|要匹配的字符串。
flags	|标志位，用于控制正则表达式的匹配方式，如：是否区分大小写，多行匹配等等。参见：正则表达式修饰符 - 可选标志
## [其他函数及其方法](https://www.runoob.com/python3/python3-reg-expressions.html)

# 3.re模块
```python
# 正则匹配
import re

# \w与\W 字母数字下划线
print(re.findall('\w', 'hello derek \n 123'))
print(re.findall('\W', 'hello derek \n 123'))
# ['h', 'e', 'l', 'l', 'o', 'd', 'e', 'r', 'e', 'k', '1', '2', '3']
# [' ', ' ', '\n', ' ']

# \s与\S  匹配任意空白字符
print(re.findall('\s', 'hello  egon  123'))  # [' ', ' ', ' ', ' ']
print(re.findall('\S', 'hello  egon  123'))  # ['h', 'e', 'l', 'l', 'o', 'e', 'g', 'o', 'n', '1', '2', '3']

# \n \t都是空,都可以被\s匹配
print(re.findall('\s', 'hello \n egon \t 123'))  # [' ', '\n', ' ', ' ', '\t', ' ']

# \n与\t
print(re.findall(r'\n', 'hello egon \n123'))  # ['\n']
print(re.findall(r'\t', 'hello egon\t123'))  # ['\n']

# \d与\D
print(re.findall('\d', 'hello egon 123'))  # ['1', '2', '3']
print(re.findall('\D', 'hello egon 123'))  # ['h', 'e', 'l', 'l', 'o', ' ', 'e', 'g', 'o', 'n', ' ']

# \A与\Z   \A  匹配字符串开始  \Z 匹配字符串结束
print(re.findall('\Ahe', 'hello egon 123'))  # ['he'],\A==>^
print(re.findall('123\Z', 'hello egon 123'))  # ['he'],\Z==>$

# ^与$
print(re.findall('^h', 'hello egon 123'))  # ['h']
print(re.findall('3$', 'hello egon 123'))  # ['3']

# 重复匹配：| . | * | ? | .* | .*? | + | {n,m} |
# .  匹配任意字符，除了换行符，除非re.DOTALL标记
print(re.findall('a.b', 'a1b'))  # ['a1b']
# a和b中间匹配任意一个字符
print(re.findall('a.b', 'a1b a*b a b aaab'))  # ['a1b', 'a*b', 'a b', 'aab']
print(re.findall('a.b', 'a\nb'))  # []
print(re.findall('a.b', 'a\nb', re.S))  # ['a\nb']
print(re.findall('a.b', 'a\nb', re.DOTALL))  # ['a\nb']同上一条意思一样
print(re.findall('a...b', 'a123b'))  # ['a123b']

# *匹配*号前的字符0次或多次
print(re.findall('ab*', 'bbbbbbb'))  # []
print(re.findall('ab*', 'a'))  # ['a']
print(re.findall('ab*', 'abbbb'))  # ['abbbb']
print(re.findall('ab*', 'abababbabbbb'))  # ['ab', 'ab', 'abb', 'abbbb']

# ?   匹配前一个字符1次或0次
print(re.findall('ab?', 'a'))  # ['a']
print(re.findall('ab?', 'abbb'))  # ['ab']
# 匹配所有包含小数在内的数字
print(re.findall('\d+\.?\d*', "asdfasdf123as1.13dfa12adsf1asdf3"))  # ['123', '1.13', '12', '1', '3']

# .*默认为贪婪匹配
print(re.findall('a.*b', 'a1b22222222b'))  # ['a1b22222222b']

# .*?为非贪婪匹配：推荐使用
print(re.findall('a.*?b', 'a1b22222222b'))  # ['a1b']

# +   匹配前一个字符1次或多次
print(re.findall('ab+', 'abbaabb'))  # ['abb', 'abb']
print(re.findall('ab+', 'abbb'))  # ['abbb']

# {n,m}  匹配前一个字符n到m次
print(re.findall('ab{2}', 'abbb'))  # ['abb']
print(re.findall('ab{2,4}', 'abbb'))  # ['abb']
print(re.findall('ab{1,}', 'abbb'))  # 'ab{1,}' ===> 'ab+'
print(re.findall('ab{0,}', 'abbb'))  # 'ab{0,}' ===> 'ab*'

# []
print(re.findall('a[1*-]b', 'a1b a*b a-b'))  # []内的都为普通字符了，且如果-没有被转意的话，应该放到[]的开头或结尾
print(re.findall('a[^1*-]b', 'a1b a*b a-b a=b'))  # []内的^代表的意思是取反，所以结果为['a=b']
print(re.findall('a[0-9]b', 'a1b a*b a-b a=b'))  #['a1b']
print(re.findall('a[a-z]b', 'a1b a*b a-b a=b aeb'))  # ['aeb']['a=b']
print(re.findall('a[a-zA-Z]b', 'a1b a*b a-b a=b aeb aEb'))  # ['aeb', 'aEb']

# \# print(re.findall('a\\c','a\c')) #对于正则来说a\\c确实可以匹配到a\c,但是在python解释器读取a\\c时，会发生转义，然后交给re去执行，所以抛出异常
print(re.findall(r'a\\c', 'a\c'))  # r代表告诉解释器使用rawstring，即原生字符串，把我们正则内的所有符号都当普通字符处理，不要转义
print(re.findall('a\\\\c', 'a\c'))  # 同上面的意思一样，和上面的结果一样都是['a\\c']

# (): 匹配括号里面的内容
print(re.findall('ab+', 'ababab123'))  # ['ab', 'ab', 'ab']
print(re.findall('(ab)+123', 'ababab123'))  # ['ab']，匹配到末尾的ab123中的ab
print(re.findall('(?:ab)+123', 'ababab123'))  # findall的结果不是匹配的全部内容，而是组内的内容,?:可以让结果为匹配的全部内容

# |
print(re.findall('compan(?:y|ies)', 'Too many companies have gone bankrupt, and the next one is my company'))
```
# 4.datetime模块学习
datatime 模块题共用一些处理日期，时间和时间间隔的函数。这个模块使用面向对象的交互取代了time模块中整形/元组类型的时间函数。
在这个模块中的所有类型都是新型类，能够从python中继承和扩展。
这个模块包含如下的类型：
- datetime代表了日期和一天的时间
- date代表日期，在1到9999之间
- time 代表时间和独立日期。
- timedelta 代表两个时间或者日期的间隔
- tzinfo 实现时区支持
- datetime 类型代表了某一个时区的日期和时间，除非有特殊说明，datetime对象使用的是“naive time”，也就是说程序中datetime的时间跟所在的时区有关联。datetime模块提供了一些时区的支持。

# 5.http请求
http:超文本传输协议
HTTP 是一种请求/响应式的协议。一个客户机与服务器建立连接后，发送一个请求给服务器，请求的格式是：统一资源标识符（URI）、协议版本号，后面是类似 MIME 的信息，包括请求修饰符、客户机信息和可能的内容。服务器接到请求后，给予相应的响应信息，其格式是：一个状态行包括信息的协议版本号、一个成功或错误的代码，后面也是类似 MIME 的信息，包括服务器信息、实体信息和可能的内容。