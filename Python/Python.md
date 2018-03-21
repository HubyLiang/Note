### Python学习
#### 1. 运算符与表达式
1. 按要求输出
```python
name = "Python"
age = 15

print("{} was {} years old".format(name, age))
# 保留小数点后三位
print("{0:.3f}".format(1.0 / 3))
# 使用 ^ 定义填充文本,例如 '___hello___'
print("{0:_^11}".format("hello"))
# 基于关键字输出
print("{name} wrote {book}".format(name='Swaroop',book='A Byte of Python'))
# 不换行打印
print("Hello ",end="")
print("World",end="")
```
#### 2. 控制流
1. if
```python
# if语句
number = 23
guess  = int(input("Enter a number："))

if number == guess:
    print("Congratulations")
elif number < guess:
    print("应该为较小的一个数")
else:
    print("应该为较大的一个数")

print("if 判断语句完成")
```
2. while
```python
# while 语句
number = 23
running = True

while running:
    guess = int(input("Enter a number:"))

    if guess == number:
        print("恭喜你猜对了")
        running = False
    elif guess > number:
        print("应该是较小的一个数")
    else:
        print("应该是较大的一个数")
else:
    print("The while loop is over")

print("while 循环语句结束")
```
3. for
```python
# For 循环
for i in range(0,5,2):
    print(i)
else:
    print("The for loop is over")
```
4. break语句
```python
# break语句
while True:
    s = input("Enter a String")
    if s == "quit":
        break
    print("length of the String is ",len(s))
print("Done")
```
5. continue语句
```python
while True:
    s = input("Enter something:")
    if s == "quit":
        break
    if len(s) < 3:
        print("too short")
        continue
    print("Input is of sufficient length,the length is {}".format(len(s)))
```
#### 3. 函数
1. 定义  
函数（Functions）是指可重复使用的程序片段。  
2. 函数格式
```python
# 函数
def say_hello():
    # 函数体
    print("Hello Python")
# 函数结束

say_hello() # 函数调用
```
3. 函数参数  
   1. 函数参数与变量类似，而它的值在我们调用函数时已被u定义，且函数运行时均已赋值完成。  
函数定义时为形参(Parameters),调用函数时所提供给函数的值被成为实参(Arguments)。  
案例  
   2. python的值传递。  
当在一个函数定义中声明的变量时，它们不会以任何方式与身处函数之外但同名的变量产生任何关系。
```python
# 比较两数大小
def print_max(a,b):
    if a > b:
        print("The max number is {}".format(a))
    elif a < b:
        print("The max number is {}".format(b))
    else:
        print("Two numbers are equals")

print_max(5,5) # 函数调用
```

```python
#Python的值传递
x = 50

def func(x):
    print("x is {}".format(x))
    x = 2
    print("Change local x to ",x)

func(x)
print("x is still ",x)
```                   
4. global 语句  
全局变量关键字 **global**
如果不使用 global 语句，是不可能为一个定义于函数之外的变量赋值。
```python
x = 50
y = 100

def func():
    global x, y

    print("x is ", x)
    print("y is ", y)

    # 函数内部定义局部参数 x
    x = 2
    print("Change global x to ", x)

func()
print("Value of x is ", x)
print("Value of y is ", y)
```
5. 默认参数值  
注意：
    1. 默认参数值应该是不可变的，即为常数。  
    2. 只有那些位于参数列表末尾的参数才能被赋予默认参数值，即在函数的参数列表中，拥有默认参数值的参数不能位于没有默认参数值的参数之前。这是因为值是按参数所处的位置来依次分配的。举例：def func(a, b = 5) 有效; 但 def func(a = 5, b) 无效。
```python
def say(message, times=2):
    print(message * times)

say("Hello ")
say("World ", 5)
```
6. 关键字参数  
通过命名关键字来指定函数中的参数。  
优点：
    1. 不用考虑参数的顺序
    2. 我们可以只对部分需要的参数赋值，其余参数使用默认值。<br>

```python
def func(a, b=5, c=10):
    print("a is ", a, " and b is ", b, " and c is ", c)

func(3)
func(3, 4, 5)
func(3, c=10)
func(c=10, b=5, a=1)
```

7. 可变参数  
使用 * 号可以实现可变字符串  
工作原理：
    1. 当我们声明一个诸如  **\*param** 的星号参数时，boing此处开始直到结束的所有位置参数 (Positional Arguments) 都将被收集并汇集成一个称为 param 的元组(Tuple)
    2. 当我们声明一个诸如  **\*\*param** 的双星参数时，从此处开始直至结束的所有关键字参数都被收集并汇集成一个名为param的字典(Dictionary)
```python
def total(a=5, *numbers, **phonebook):
    print('a', a)

    # 遍历元组中所有项目
    for single_item in numbers:
        print("single_item", single_item)

    # 遍历字典中的所有项目
    for first_part, second_part in phonebook.items():
        print(first_part, second_part)


print(total(10, 1, 2, 3, Jack=3306, John=8080, Inge=6379))
```
8. return 语句  
中断函数，返回一个值。  
注意：
    1. 如果 return 语句没有搭配任何一个值则代表 返回None。
    2. 如果没有显示的写 return 语句，则默认返回 return none。  
    3. Python 中的 pass 语句用于指示一个没有内容的语句块。
```python
def maximum(x, y):
    if x > y:
        return x
    elif x == y:
        return "The numbers are equals"
    else:
        return y

print(maximum(2, 3))
```

9. DocStrings  
Documentation String 文档字符串   
帮助我们更好的记录程序并让其更加易于理解。  
约定：  
    1. 文档字符串所约定的是一串多行字符串，其中第一行以某一大写字母开始，以句号结束。  
    2. 第二行为空行。
    3. 第三行为详细的解释说明。  
我们使用函数 \_\_doc\_\_ 来获取 类似 print_max 函数的文档字符串属性。
```python
def print_max(x, y):
    '''打印两个数值中的最大值。

    这两个数都应该是整数
    '''
    # 如果可能，则将其转换至整数类型
    x = int(x)
    y = int(y)

    if x > y:
        print(x, 'is maximum')
    else:
        print(y, 'is maxium')


print_max(3, 5)
print(print_max.__doc__)
```

10. 总结  

#### 4. 模块 Modules
一个模块可以被其他程序导入并运用其功能。  
其中一个最简便的方法： 创建一个包含函数和变量、且以 .py 为后缀的文件。

1. 标准库模块

    详细说明：
      1. 首先我们通过 import 语句导入 sys 模块。sys 模块包含了与Python解释器及其环境相关的功能，即所谓的系统功能。当python运行 import sys 这一语句时，它会开始寻找 sys模块。
      2. 如果不是一个已编译好的模块，即用python编写的模块，那么python解释器将会从它的sys.path 变量所提供的目录下进行搜索。如果找到了对应模块，则该模块中中的语句将会开始运行。注意：初始化工作只需要我们在第一次导入模块时完成。

```python
import sys
import os

print("The command line arguments are:")
for i in sys.argv:
    print(i)

print("\n\n The PythonPath is ",sys.path,"\n")
print(os.getcwd())  # 查看当前程序所处的目录
```

2. 按字节码编译的 .pyc 文件  
创建按字节码编译的文件，以 .pyc 为其扩展名，它将python转换成中间形式的文件。可以帮助我们更快捷的完成模块的导入。  

3. from ... import 语句  
可以直接将argv变量导入到我们的程序中。(例如)避免每次都要输入 sys  
警告： 一般来说，我们应该避免使用from ... import 语句。一是避免了程序中可能出现的名称冲突，同时也使程序更加易读。  
```python
from math import sqrt
print("sqrt:",sqrt(100))

# 推荐使用这种导入方式
import math
print(math.sqrt(100))
```

4. 模块的  \_\_name\_\_    
当模块第一次被导入时，他所包含的代码将被执行。通过这一特性来使模块以不同的方式运行，而这取决于它是为自己所用还是从其他模块中导入而来。  
原理：每一个Python模块都定义了它的 \_\_name\_\_属性。如果它与 \_\_main\_\_ 属性相同，则代表这一模块是用户独立运行。
```python
if __name__ == "__main__":
    print("The program is being run by itself")
else:
    print("I'm being imported from another module")
```
5. 编写我们自己的模块    
每一个Python程序同时也是一个模块，我们只需要保证它以 .py 为扩展名即可。  
要注意的是：被导入的模块 和 使用被导入模块的模块 应该在同一个 目录下 或者 放置在 sys.path 所列出的其中一个目录下。
一个简单的模块导入案例：    
```python
# mymodule.py
def say_hi():
    print("Hi,this is mymodule speak")

__version__ = "0.1"

# ------------------------------------------------

# 使用 import 导入模块
# mymodule_demo.py
import mymodule

mymodule.say_hi()
print("version:",mymodule.__version__)
```
6. dir 函数    
内置的 dir() 函数能够返回由对象所定义的名称列表。如果这一对象是一个模块，则该列表会包括模块内所定义的函数、类与变量。     
dir() 函数接受参数。如果参数是模块名称，函数将返回这一指定模块的名称列表。如果没有提供参数，则将返回当前模块的名称列表。  
dir() 函数能够对任何对象工作
```python
>>> import sys
>>> dir(sys)
['__displayhook__', '__doc__', '__excepthook__', '__interactivehook__', '__loader__', '__name__', '__package__', '__spec__' ...]
>>> dir()  # 注意：被导入模块也是属性列表的一部分。
['__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'sys']
>>> a = 5
>>> dir()  
['__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'a', 'sys']
>>> del a  # 删除一个变量或名称，运行后，我们不能再次访问该变量。即不存在。
>>> dir()
['__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'sys']
>>> print(a)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'a' is not defined
>>>
```

#### 6. 数据结构
1. 概念   
提供一种结构，能将一些数据聚合在一起。
2. 4种内置数据结构  
列表List，元组Tuple，字典DIctionary，集合Set  

   1. **列表 List**   
    列表List用于保存一系列有序项目的集合。即，我们可以利用列表保存一串项目的序列。    
    项目的列表u应该用 **[]** 括起来，一旦我们创建了一张列表，我们就可以添加、移除或者搜索列表中的项目。  
    即，列表List 是**可变的**。  
    **列表是使用对象与类的实例**。当我们创建一个变量 i 并将整数 5 赋值给它，我们可以认为这个过程实在创建了一个 int 类的对象实例。
    ```python
    # 购物列表
    shoplist = ["apple","mango","carrot","banana"]

    print("I've",len(shoplist),"items to purchase")

    print("These items are:",end=" ")
    for item in shoplist:
        print(item,end=" ")

    print("\n-------------------------")

    print("I also have buy rice.")
    shoplist.append("rice")
    print("My shopping list is now",shoplist)

    print("-------------------------")

    print("I'll sort my list now.",)
    # 影响的是列表本身，而不是返回一个修改过的列表
    shoplist.sort()
    print("Sorted shopping list is",shoplist)
    shoplist.sort(reverse=True)
    print("Sorted shopping list is",shoplist)

    print("-------------------------")

    print("The first item I will buy is ",shoplist[0])
    olditem = shoplist[0]
    del shoplist[0]
    print("I bought the ",olditem)
    print("My shopping list is now",shoplist)
    ```
   2. **元组 Tuple**  
   元组是用于将多个对象保存在一起。可以近似的看作为列表List，但元组不能提供列表类所提供的丰富的方法功能，因为**元组是不可变的**。我们不能编辑或者更改元组。    
   元组是通过特别指定项目来定义的。使用 () 来定义元组，中间通过逗号进行分割。  
   元组通常用于保证某一语句或用户定义的函数可以安全的采用一组数值，即 **元组内的数值不会改变**.    
   注意：  
   包含 0个或1个 项目的元组。
   ```python
   # 一个空的元组使用一对 ()
   myempty = ()
   # 只包含一个项目的元组必须在第一个项目(也是唯一一个)后面加上一个 ','  
   singleton = (1,)
   ```

   ```python
   # 明了胜于晦涩,显示优于隐式
   # 推荐使用 () 声明元组
   zoo = ("python","elephant","penguin")
   print("Number of animals in the zoo",len(zoo))

   new_zoo = ("monkey","camel",zoo)
   print("Number of cages in the new_zoo is",len(new_zoo))
   print("All number in new_zoo are",new_zoo)

   # 索引 index 从0 开始.类似于数组.
   print("Animals brought from old zoo are",new_zoo[2])
   print("Last animal brought from old zoo is",new_zoo[2][2])
   print("Number of animals in the new zoo is",len(new_zoo)-1+len(new_zoo[2]))
   ```  
   3. **字典 Dictionary**  
   字典就像一本地址薄，如果你知道了他的姓名，就可以在字典中找到其地址或者能够联系上对方的更多的详细信息。简单的来说，就是我们将键(Keys)和值(Values)联系到一起。(就是Java中的HashMap) 注意的是，**键必须是唯一的**.此外，只能使用不可变对象(如字符串)作为字典的键。
