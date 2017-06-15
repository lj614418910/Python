# Python学习笔记

## Day 1

##### 整型与浮点型
- 整数和浮点数在计算机内部存储的方式是不同的，整数运算永远是精确的(包括除法)，而浮点数运算则可能会有四舍五入的误差。
- 十六进制整数前面加`0x`，例如`0xff00`等于`65280`。
- 浮点型可以表示科学计数法，例如`1.23e9`等于`1.23x10^9`。

##### 布尔值
- 布尔值里只有`True`和`Fasle`。
- 布尔运算: 或`or`(全错才为错),且`and`(全对才为对)，非`not`(对错倒置)。
- Python把`0`、`空字符串`、`''`和`None`看成`False`，其他数值和`非空字符串`都看成`True`

##### 空值
- 空值是Python里一个特殊的值，用None表示。None不能理解为0，因为0是有意义的，而None是一个特殊的空值。

##### print
- 写法`print 'hello world'`或`print('hello world')`。
- Python2 里面print可以直接接字符串或者运算。Python3 里面print变成了一个函数，上面的写法不支持了，必须用一个括号括起来，否则会报告语法错误。 
- print会依次打印每个字符串，遇到逗号“,”会输出一个空格，然后将输出的字符串拼接起来。

##### 注释
```
# 这一行全部都是注释...
print 'hello' # 这也是注释
```

## Day 2

##### 变量
- 在Python程序中,变量是用一个变量名表示,变量名必须是大小写英文、数字和下划线`_`的组合，且不能用数字开头。
- 例：执行`a = 'ABC'`,解释器创建了字符串'ABC'和变量a,并把a指向'ABC'。<br/>![](./1.jpg)
- 执行`b = a`,解释器创建了变量b,并把b指向a指向的字符串'ABC'。<br/>![](./2.jpg)
- 执行`a = 'XYZ'`,解释器创建了字符串'XYZ',并把a的指向改为'XYZ',但b并没有更改。<br/>![](./3.jpg)

##### 定义字符串
- 字符串可以用`''`或者`""`括起来表示。
- 转义字符`\`,转义字符`\`不计入字符串的内容中。常用的转义字符有：`\n`表示换行;`\t`表示一个制表符;`\\`表示\字符本身。

##### raw字符串、多行字符串和Unicode字符串
- raw 字符串，里面的字符不需要转义。用法`r'\(~_~)/ \(~_~)/'`，输出`\(~_~)/ \(~_~)/`
- 多行字符串，用法:

	```
	'''abcdefg
		abcdefg
		abcdefg'''
	```
	输出：

	```
	abcdefg
	abcdefg
	abcdefg
	```
- Unicode字符串用u'...'表示;
- 如果中文字符串在Python环境下遇到 UnicodeDecodeError，这是因为.py文件保存的格式有问题。可以在第一行添加注释`# -*- coding: utf-8 -*-`;
- 在最新的Python 3版本中，字符串是以Unicode编码的。
- 可以三者混合着用`ur''' ...'''`。

##### 字符串方法
- Python提供了`ord()`函数获取字符的整数表示，`chr()`函数把编码转换为对应的字符。
- 要计算str包含多少个字符，可以用`len()`函数。

##### 格式化
- 在Python中，采用的格式化方式和C语言是一致的，用%实现，举例如下：

	```
	>>> 'Hello, %s' % 'world'
	'Hello, world'
	>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
	'Hi, Michael, you have $1000000.'
	```
- 常见的占位符有：`%d`整数;`%f`浮点数;`%s`字符串;`%x`十六进制整数。
- 格式化整数和浮点数还可以指定是否补0和整数与小数的位数：

	```
	>>> '%2d-%02d' % (3, 1)
	'3-01'
	>>> '%.2f' % 3.1415926
	'3.14'
	```
- 不太确定应该用什么，%s永远起作用，它会把任何数据类型转换为字符串。
- 有些时候，字符串里面的%是一个普通字符,这个时候需要转义，用`%%`来表示一个`%`。

## Day 3

##### List
- Python内置的一种数据类型是列表：`list`。list是一种有序的集合，可以随时添加和删除其中的元素:`list = ['a','b','c']`
- 用`len()`可以获取list元素的个数:`len(list) >>> 3`
- 用索引来访问list中每一个位置的元素，记得索引是从`0`开始的:`list[0] >>> 'a'; list[1] >>> 'b'; `、`list[2] >>> '3'`
- 当索引超出了范围时，Python会报一个IndexError错误，所以，要确保索引不要越界，记得最后一个元素的索引是`len(list) - 1`。如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素：`list[-1] >>> 'c'`
- list是一个可变的有序表，所以，可以往list中追加元素到末尾：`list.append('d');`、` list >>> ['a','b','c','d']`
- 也可以把元素插入到指定的位置，比如索引号为`1`的位置：`list.insert(1, 'e'); `、`list >>> ['a','e','b','c','d']`
- 要删除list末尾的元素，用`pop()`方法：`list.pop(); ``list >>> ['a','e','b','c']`,pop()里面可以填参数，指定删除哪个元素，而且被删除的元素还会被保存出来`x = list.pop();`、` x >>> 'c'`
- 要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：`list[1]='b', list >>> ['a','b','b','c']`
- list里面的元素的数据类型也可以不同,list元素也可以是另一个list：`list=['a','b','b','c',s]; s=[1,2,3];`、`list >>> ['a','b','b','c',[1,2,3]]; list[4][0] >>> 1`

##### tuple
- 另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改:`t = (1, 2)`
- 定义一个只有1个元素的tuple，如果你这么定义：`t = (1)`,那么`t >>> 1`。这样不是tuple，是`1`这个数！这是因为括号`()`既可以表示tuple，又可以表示数学公式中的小括号，这就产生了歧义，因此，Python规定，这种情况下，按小括号进行计算，计算结果自然是`1`。所以，只有1个元素的tuple定义时必须加一个逗号`,`，来消除歧义：`t = (1,)`

##### “可变的”tuple
- `t = ('a', 'b', ['A', 'B']); t[2][0] = 'X';t[2][1] = 'Y'`、`t >>> ('a', 'b', ['X', 'Y'])`
- 这个tuple定义的时候有3个元素，分别是`'a'`，`'b'`和一个`list`。<br/>![](./4.jpg)<br/>当我们把list的元素'A'和'B'修改为'X'和'Y'后，tuple变为：<br/>![](./5.jpg)
- tuple的元素确实变了，但其实变的不是tuple的元素，而是list的元素。所以，tuple所谓的“不变”是说，tuple的每个元素，指向永远不变。