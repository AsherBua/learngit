Python笔记

1.
x = 10
x = x + 2
如果从数学上理解x = x + 2那无论如何是不成立的，在程序中，赋值语句先计算右侧的表达式x + 2，得到结果12，再赋给变量x。由于x之前的值是10，重新赋值后，x的值变成12。

2.
print (10_00_0000_0) #python allow '_' for numbers,

3. a = 'ABC'
    b = a
    a = 'XYZ'
    print(b)
    ![image-20220501161008895](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220501161008895.png)

4. 当Python解释器读取源代码时，为了让它按UTF-8编码读取，我们通常在文件开头写上这两行：
#!/usr/bin/env python3 (windows 不用写这个)
#-*- coding: utf-8 -*-
字符串和编码 https://www.liaoxuefeng.com/wiki/1016959663602400/1017075323632896 

5. list 
list = [' ', ' ' ]
len(list)
list [0]
最后一个元素的检索：len(list) -1 
追加元素到末尾：list.append（’ ‘）
把元素插入到指定的位置，比如索引号为1的位置:list.insert(1, ' ')
删除list的元素: list.pop (1)
list[1] = ' '

6. tuple 元组（有序列表）tuple一旦初始化就不能修改, 如果可能，能用tuple代替list就尽量用tuple
classmates = （’david‘， 'bob'）
只有1个元素的tuple定义时必须加一个逗号,，来消除歧义: t =(1, )

7. dict （key-value）
d ={'mike':95, ’bob' : 40}
通过in判断key是否存在：'mike' in d    (return False or True) 或者 d.get('nike', -1) 返回None或者-1   注意：返回None的时候Python的交互环境不显示结果
删除一个key，对应的value也会删除：d.pop('bob')
是dict的key必须是不可变对象
在Python中，字符串、整数等都是不可变的，因此，可以放心地作为key。而list是可变的，就不能作为key

8. set 
    set和dict的唯一区别仅在于没有存储对应的value，但是，set的原理和dict一样，所以，同样不可以放入可变对象，因为无法判断两个可变对象是否相等，也就无法保证set内部“不会有重复元素”。

![image-20220501230332024](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220501230332024.png)

9. 函数 （是 abs（）这种)
   def my_abs(x):
     if x >= 0:
         return x
     else:
         return -x
   print(my_abs(-99))
   函数体内部的语句在执行时，一旦执行到return时，函数就执行完毕，并将结果返回
   如果没有return语句，函数执行完毕后也会返回结果，只是结果为None。return None可以简写为return
   如果你已经把my_abs()的函数定义保存为abstest.py文件了，那么，可以在该文件的当前目录下启动Python解释器，用from abstest import my_abs来导入my_abs()函数，注意abstest是文件名（不含.py扩展名）: from abstest import my_abs 
   函数可以同时返回多个值，但其实就是一个tuple。

10. 函数传参
    必选参数
    默认参数：(一定用不可变对象，比如None, 2,3)
    可变参数 ：*args, args 接受的是一个tuple/ 可变参数可以直接传入：calc(*numbers)>>calc（1，2，3），又可以先组装list或tuple，再通过 *args传入：func（ *（1，2，3））
    关键字参数 ： **kw， kw接受的是一个dict/ 即可直接传入：func（a=1，b=2），又可以先组装dict，再通过 ** kw传入：func（**{‘a':1,'b':2}) 
    命名关键字参数：命名的关键字参数是为了限制调用者可以传入的参数名，同时可以提供默认值。例如，只接收city和job作为关键字参数 def person(name, age, *, city, job)
    参数定义的顺序：必选参数、默认参数、可变参数、命名关键字参数和关键字参数

    定义命名的关键字参数在没有可变参数的情况下不要忘了写分隔符`*`，否则定义的将是位置参数
    
11. 高级特性
    **切片**：L[0:3] , 取前三个元素. L[-2:], 去倒数两个元素
    **遍历**（迭代）：for key in d, for i, value in enumerate(['A', 'B', 'C']):
    判断是否可迭代：
    from collections.abc import Iterable
    print(isinstance('abc', Iterable)) # str是否可迭代，判断一个对象是否是Iterable对象
    **列表生成式**：写列表生成式时，把要**生成的元素x * x放到前面**，后面跟for循环，就可以把list创建出来
    [x * x for x in range(1, 11) if x % 2 == 0]， 把if写在for前面必须加else，这是因为for前面的部分是一个表达式，它必须根据x计算出一个结果。
    **生成器**： 
    **迭代器**：
    可以被next()函数调用并不断返回下一个值的对象称为迭代器：Iterator。
    可以使用isinstance()判断一个对象是否是Iterator对象：
    from collections.abc import Iterator
    isinstance((x for x in range(10)), Iterator)
    生成器都是Iterator对象，但list、dict、str虽然是Iterable，却不是Iterator。
    把list、dict、str等Iterable变成Iterator可以使用iter()函数：isinstance(iter([]), Iterator)---True
    凡是可作用于for循环的对象都是Iterable类型；
    凡是可作用于next()函数的对象都是Iterator类型，它们表示一个惰性计算的序列；
    集合数据类型如list、dict、str等是Iterable但不是Iterator，不过可以通过iter()函数获得一个Iterator对象。
    **map/reduce**
    **filter()**正确实现一个“筛选”函数. 注意到filter()函数返回的是一个Iterator，也就是一个惰性序列，所以要强迫filter()完成计算结果，**需要用list()函数获得所有结果并返回list。**
    def is_odd(n):
    return n % 2 == 1
    list(filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15]))
    **sorted** sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower, reverse=True)
    ['Zoo', 'Credit', 'bob', 'about']
    
12. 函数式编程
    **返回函数：**
    一个函数可以返回一个计算结果，也可以返回一个函数。
    返回一个函数时，牢记该函数并未执行，返回函数中不要引用任何可能会变化的变量。
    ![image-20220512165848544](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220512165848544.png)
    **匿名函数**
    **装饰器**
    在代码运行期间动态增加功能的方式，称之为“装饰器”
    在 if/else 语句中我们返回 **greet 和 welcome**，而不是 **greet() 和 welcome()**。为什么那样？这是因为当你把一对小括号放在后面，这个函数就会执行；然而如果你不放括号在它后面，那它可以被到处传递，并且可以赋值给别的变量而不去执行它。

![image-20220512215307026](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220512215307026.png)
    **偏函数**
functools.partial的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。

13. 模块
    每一个包目录下面都会有一个__init__.py的文件，这个文件是必须存在的，否则，Python就把这个目录当成普通目录，而不是一个包。
    __init__.py可以是空文件，也可以有Python代码，因为__init__.py本身就是一个模块，而它的模块名就是mycompany。

![image-20220512221247036](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220512221247036.png)

其中if name == 'main'：这句估计很多和我一样的初学者都是不求甚解。 这里作一下解释：

name是一个变量。前后加了爽下划线是因为是因为这是系统定义的名字。普通变量不要使用此方式命名变量。 2：Python有很多模块，而这些模块是可以独立运行的！这点不像C++和C的头文件。 3：import的时候是要执行所import的模块的。 4：name就是标识模块的名字的一个系统变量。这里分两种情况：假如当前模块是主模块（也就是调用其他模块的模块），那么此模块名字就是main，通过if判断这样就可以执行“mian:”后面的主函数内容；假如此模块是被import的，则此模块名字为文件名字（不加后面的.py），通过if判断这样就会跳过“mian:”后面的内容。

通过上面方式，python就可以分清楚哪些是主函数，进入主函数执行；并且可以调用其他模块的各个函数等等。
    
14. 面向对象编程

__init__ 方法的主要作用,就是初始化你的属性
![image-20220513105452458](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220513105452458.png)
注意到`__init__`方法的第一个参数永远是`self`，表示创建的实例本身

**访问限制**：在Python中，实例的变量名如果以_ _开头，就变成了一个私有变量（private），只有内部可以访问，外部不能访问
def print_score(self):
 print('%s: %s' % (self.__name, self.__score))

![image-20220513113853998](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220513113853998.png)

**继承和多态**
isinstance(c, Dog) 可判断变量c,是否是类型Dog，的类型
**获取对象信息**
通过内置的一系列函数，我们可以对任意一个Python对象进行剖析，拿到其内部的数据。
type(), isinstance(), dir(), 
**给class，实例绑定属性，方法**

![image-20220513152231952](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220513152231952.png)

**使用__slots__**
为了达到限制的目的，Python允许在定义class的时候，定义一个特殊的__slots__变量，来限制该class实例能添加的属性：

![image-20220513152357429](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220513152357429.png)

**使用@property**
把一个getter方法变成属性，只需要加上@property就可以了。@property本身又创建了另一个装饰器@score.setter，负责把一个setter方法变成属性赋值

![image-20220513173831051](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220513173831051.png)

**定制类**
__str__,__iter__
__getitem__
__getattr__
__call__

**枚举类**
用Enum
![image-20220514103424962](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514103424962.png)

![image-20220514103443367](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514103443367.png)
value属性则是自动赋给成员的int常量，默认从1开始计数

@unique

![image-20220514103752910](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514103752910.png)

![image-20220514103819018](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514103819018.png)

**type()**
1. type()函数可以查看一个类型或变量的类型，Hello是一个class，它的类型就是type，而h是一个实例，它的类型就是class Hello
    ![image-20220514110321651](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514110321651.png)
    2.type()函数既可以返回一个对象的类型，又可以创建出新的类型，比如，我们可以通过type()函数创建出Hello类，而无需通过class Hello(object)...的定义

  ![image-20220514110456965](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514110456965.png)

**Python 字符串**
1. 字符串是 Python 中最常用的数据类型。我们可以使用引号 ( ' 或 " ) 来创建字符串
2. python 访问子字符串，可以使用方括号来截取字符串，如下实例：print "var1[0]: ", var1[0]
3. 我们可以对字符串进行截取并与其他字符串进行连接，如下实例：print "输出 :- ", var1[:6] + 'Runoob!'
4. Python 转义字符:
![image-20220514111355329](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514111355329.png)
5. Python字符串运算符:
![image-20220514111440429](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514111440429.png)
6. Python 字符串格式化:
![image-20220514111525089](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514111525089.png)
![image-20220514111558690](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514111558690.png)
7. Python 三引号:
Python 中三引号可以将复杂的字符串进行赋值。
Python 三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。
三引号的语法是一对连续的单引号或者双引号（通常都是成对的用）。
![image-20220514111807027](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514111807027.png)

**错误处理**
try...except...finally...
![image-20220514134745722](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514134745722.png)

**调试**
pdb，IDE调试
**单元测试**
**文档测试**
用doctest测试：
![image-20220514142740831](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514142740831.png)
什么输出也没有。这说明我们编写的doctest运行都是正确的。如果程序有问题，比如把`__getattr__()`方法注释掉，再运行就会报错
注意到最后3行代码。当模块正常导入时，doctest不会被执行。只有在命令行直接运行时，才执行doctest。所以，不必担心doctest会在非测试环境下执行。
**文件读写**
读：
`with open('/path/to/file', 'r') as f:
    print(f.read())`//无需调用f.close()
如果文件很小，read()一次性读取最方便；如果不能确定文件大小，反复调用read(size)比较保险；如果是配置文件，调用readlines()最方便
二进制文件: `f = open('/Users/michael/test.jpg', 'rb')`
字符编码:要读取非UTF-8编码的文本文件，需要给open()函数传入encoding参数，例如，读取GBK编码的文件： `f = open('/Users/michael/gbk.txt', 'r', encoding='gbk')`
遇到有些编码不规范的文件，你可能会遇到UnicodeDecodeError，因为在文本文件中可能夹杂了一些非法编码的字符。遇到这种情况，open()函数还接收一个errors参数，表示如果遇到编码错误后如何处理。最简单的方式是直接忽略：`f = open('/Users/michael/gbk.txt', 'r', encoding='gbk', errors='ignore')`
写：
`with open('/Users/michael/test.txt', 'w') as f:
    f.write('Hello, world!')`
如果我们希望追加到文件末尾怎么办？可以传入`'a'`以追加（append）模式写入。

**StringIO:**
StringIO顾名思义就是在内存中读写str。

![image-20220514191729577](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514191729577.png)

**BytesIO**
StringIO操作的只能是str，如果要操作二进制数据，就需要使用BytesIO。
StringIO和BytesIO是在内存中操作str和bytes的方法，使得和读写文件具有一致的接口。
![image-20220514192404164](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514192404164.png)

**操作文件和目录**

![image-20220514194557362](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220514194557362.png)

**序列化 python-JSON**
如果我们要在不同的编程语言之间传递对象，就必须把对象序列化为标准格式，比如XML，但更好的方法是序列化为JSON，因为JSON表示出来就是一个字符串，可以被所有语言读取，也可以方便地存储到磁盘或者通过网络传输。JSON不仅是标准格式，并且比XML更快，而且可以直接在Web页面中读取，非常方便。
![image-20220515114018153](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220515114018153.png)

![image-20220515115453094](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220515115453094.png)
序列化class
![image-20220515115717255](C:\Users\mbai1\AppData\Roaming\Typora\typora-user-images\image-20220515115717255.png)

**进程和线程**(学到进程线程这里)
1. 对于操作系统来说，一个任务就是一个进程（Process），比如打开一个浏览器就是启动一个浏览器进程，打开一个记事本就启动了一个记事本进程，打开两个记事本就启动了两个记事本进程，打开一个Word就启动了一个Word进程。
2. 有些进程还不止同时干一件事，比如Word，它可以同时进行打字、拼写检查、打印等事情。在一个进程内部，要同时干多件事，就需要同时运行多个“子任务”，我们把进程内的这些“子任务”称为线程（Thread）。
