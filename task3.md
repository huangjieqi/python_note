# 1.dict字典

## 定义
- 字典属于一种新的数据结构，称为映射（mapping）
- 字典的作用和列表类似，都是用来存储对象的容器
- 列表存储数据的性能很好，但是查询数据的性能的很差
- 在字典中每一个元素都有一个唯一的名字，通过这个唯一的名字可以快速的查找到指定的元素
- 在查询元素时，字典的效率是非常快的
- 在字典中可以保存多个对象，每个对象都会有一个唯一的名字
这个唯一的名字，我们称其为键（key），通过key可以快速的查询value
这个对象，我们称其为值（value）
所以字典，我们也称为叫做键值对（key-value）结构
每个字典中都可以有多个键值对，而每一个键值对我们称其为一项（item）

## 创建

```python

# 字典
# 使用 {} 来创建字典
d = {} # 创建了一个空字典

# 创建一个保护有数据的字典
# 语法：
#   {key:value,key:value,key:value}
#   字典的值可以是任意对象
#   字典的键可以是任意的不可变对象（int、str、bool、tuple ...），但是一般我们都会使用str
#       字典的键是不能重复的，如果出现重复的后边的会替换到前边的
# d = {'name':'孙悟空' , 'age':18 , 'gender':'男' , 'name':'sunwukong'}
d = {
'name':'孙悟空' , 
'age':18 , 
'gender':'男' , 
'name':'sunwukong'
}

# print(d , type(d))

# 需要根据键来获取值
# print(d['name'],d['age'],d['gender'])

# 如果使用了字典中不存在的键，会报错
# print(d['hello']) KeyError: 'hello'
```

## 字典的方法

```python
# 创建字典
# 使用{}
# 语法：{k1:v1,k2:v2,k3:v3}

# 使用 dict()函数来创建字典
# 每一个参数都是一个键值对，参数名就是键，参数名就是值（这种方式创建的字典，key都是字符串）
d = dict(name='孙悟空',age=18,gender='男') 

# 也可以将一个包含有双值子序列的序列转换为字典
# 双值序列，序列中只有两个值，[1,2] ('a',3) 'ab'
# 子序列，如果序列中的元素也是序列，那么我们就称这个元素为子序列
# [(1,2),(3,5)]
d = dict([('name','孙悟饭'),('age',18)])
# print(d , type(d))
d = dict(name='孙悟空',age=18,gender='男') 

# len() 获取字典中键值对的个数
# print(len(d))

# in 检查字典中是否包含指定的键
# not in 检查字典中是否不包含指定的键
# print('hello' in d)

# 获取字典中的值，根据键来获取值
# 语法：d[key]
# print(d['age'])

# n = 'name'
# print(d[n])

# 通过[]来获取值时，如果键不存在，会抛出异常 KeyError
# get(key[, default]) 该方法用来根据键来获取字典中的值
#   如果获取的键在字典中不存在，会返回None
#   也可以指定一个默认值，来作为第二个参数，这样获取不到值时将会返回默认值
# print(d.get('name'))
# print(d.get('hello','默认值'))

# 修改字典
# d[key] = value 如果key存在则覆盖，不存在则添加
d['name'] = 'sunwukong' # 修改字典的key-value
d['address'] = '花果山' # 向字典中添加key-value

# print(d)
# setdefault(key[, default]) 可以用来向字典中添加key-value
#   如果key已经存在于字典中，则返回key的值，不会对字典做任何操作
#   如果key不存在，则向字典中添加这个key，并设置value
result = d.setdefault('name','猪八戒')
result = d.setdefault('hello','猪八戒')

# print('result =',result)
# print(d)

# update([other])
# 将其他的字典中的key-value添加到当前字典中
# 如果有重复的key，则后边的会替换到当前的
d = {'a':1,'b':2,'c':3}
d2 = {'d':4,'e':5,'f':6, 'a':7}
d.update(d2)

# print(d)
# 删除，可以使用 del 来删除字典中的 key-value
del d['a']
del d['b']

# popitem()
# 随机删除字典中的一个键值对，一般都会删除最后一个键值对
#   删除之后，它会将删除的key-value作为返回值返回
#   返回的是一个元组，元组中有两个元素，第一个元素是删除的key，第二个是删除的value
# 当使用popitem()删除一个空字典时，会抛出异常 KeyError: 'popitem(): dictionary is empty'
# d.popitem()
# result = d.popitem()

# pop(key[, default])
# 根据key删除字典中的key-value
# 会将被删除的value返回！
# 如果删除不存在的key，会抛出异常
#   如果指定了默认值，再删除不存在的key时，不会报错，而是直接返回默认值
result = d.pop('d')
result = d.pop('z','这是默认值')

# del d['z'] z不存在，报错
# result = d.popitem()
# result = d.popitem()
# result = d.popitem()
# result = d.popitem()

# clear()用来清空字典
d.clear()

# print('result =',result)
# print(d)

# copy()
# 该方法用于对字典进行浅复制
# 复制以后的对象，和原对象是独立，修改一个不会影响另一个
# 注意，浅复制会简单复制对象内部的值，如果值也是一个可变对象，这个可变对象不会被复制
d = {'a':1,'b':2,'c':3}
d2 = d.copy()
# d['a'] = 100

d = {'a':{'name':'孙悟空','age':18},'b':2,'c':3}
d2 = d.copy()
d2['a']['name'] = '猪八戒'


print('d = ',d , id(d))
print('d2 = ',d2 , id(d2))
```

# 2.集合

特性
- 集合和列表非常相似
- 不同点：
1. 集合中只能存储不可变对象
2. 集合中存储的对象是无序（不是按照元素的插入顺序保存）
3. 集合中不能出现重复的元素

## 创建
```python
# 集合
# 使用 {} 来创建集合
s = {10,3,5,1,2,1,2,3,1,1,1,1} # <class 'set'>
# s = {[1,2,3],[4,6,7]} TypeError: unhashable type: 'list'
# 使用 set() 函数来创建集合
s = set() # 空集合
# 可以通过set()来将序列和字典转换为集合
s = set([1,2,3,4,5,1,1,2,3,4,5])
s = set('hello')
s = set({'a':1,'b':2,'c':3}) # 使用set()将字典转换为集合时，只会包含字典中的键
```

## 方法

```python
# 创建集合
s = {'a' , 'b' , 1 , 2 , 3 , 1}

# 使用in和not in来检查集合中的元素
# print('c' in s)

# 使用len()来获取集合中元素的数量
# print(len(s))

# add() 向集合中添加元素
s.add(10)
s.add(30)

# update() 将一个集合中的元素添加到当前集合中
#   update()可以传递序列或字典作为参数，字典只会使用键
s2 = set('hello')
s.update(s2)
s.update((10,20,30,40,50))
s.update({10:'ab',20:'bc',100:'cd',1000:'ef'})

# {1, 2, 3, 100, 40, 'o', 10, 1000, 'a', 'h', 'b', 'l', 20, 50, 'e', 30}
# pop()随机删除并返回一个集合中的元素
# result = s.pop()

# remove()删除集合中的指定元素
s.remove(100)
s.remove(1000)

# clear()清空集合
s.clear()

# copy()对集合进行浅复制

# print(result)
print(s , type(s))

```

# 3.判断语句（要求掌握多条件判断）
## 条件判断语句（if语句）
```
语法：if 条件表达式 : 
          代码块
执行的流程：if语句在执行时，会先对条件表达式进行求值判断，
  如果为True，则执行if后的语句
  如果为False，则不执行
默认情况下，if语句只会控制紧随其后的那条语句，如果希望if可以控制多条语句，
  则可以在if后跟着一个代码块
 ```
## if-else语句
```
语法： 
  if 条件表达式 :
      代码块
  else :
      代码块
执行流程：
  if-else语句在执行时，先对if后的条件表达式进行求值判断
      如果为True，则执行if后的代码块
      如果为False，则执行else后的代码块
```

if-elif-else语句
```
语法：
  if 条件表达式 :
      代码块
  elif 条件表达式 :
      代码块
  elif 条件表达式 :
      代码块
  elif 条件表达式 :
      代码块
  else :
      代码块
      
执行流程：
  if-elif-else语句在执行时，会自上向下依次对条件表达式进行求值判断，
      如果表达式的结果为True，则执行当前代码块，然后语句结束
      如果表达式的结果为False，则继续向下判断，直到找到True为止
      如果所有的表达式都是False，则执行else后的代码块
  if-elif-else中只会有一个代码块会执行
```

## 练习1：打印99乘法表
```python
#   1*1=1
#   1*2=2 2*2=4
#   1*3=3 2*3=6 3*3=9
#   ...                 9*9=81

# 创建一个外层循环来控制图形的高度
i = 0
while i < 9:
    i += 1
    
    # 创建一个内层循环来控制图形的宽度
    j = 0
    while j < i:
        j += 1
        print(f"{j}*{i}={i*j} ",end="")

    print()
```

# 4.三目表达式
```python
a=1
b=2
c=’’
c=‘xxx’ if a>b else c =‘zzzzz’
```
条件为真时，是if判断条件，条件假时，是else的判断条件；
# 5.循环语句
```
循环语句可以使指定的代码块重复指定的次数
循环语句分成两种，while循环 和 for循环
while循环
语法：
  while 条件表达式 :
      代码块
  else :
      代码块
执行流程：
  while语句在执行时，会先对while后的条件表达式进行求值判断，
      如果判断结果为True，则执行循环体（代码块），
      循环体执行完毕，继续对条件表达式进行求值判断，以此类推，
      直到判断结果为False，则循环终止，如果循环有对应的else，则执行else后的代码块
```


