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
    
