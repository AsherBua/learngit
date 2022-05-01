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

