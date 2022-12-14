# Python
[面试题地址](https://github.com/kenwoodjw/python_interview_question#1%E6%9C%89%E4%B8%80%E4%B8%AAjsonline%E6%A0%BC%E5%BC%8F%E7%9A%84%E6%96%87%E4%BB%B6filetxt%E5%A4%A7%E5%B0%8F%E7%BA%A6%E4%B8%BA10k
)

## 文件
### 文件使用方式标识

'r':默认值，表示从文件读取数据。

'w':表示要向文件写入数据，并截断以前的内容

'a':表示要向文件写入数据，添加到当前内容尾部

'r+':表示对文件进行可读写操作（删除以前的所有数据）

'r+a'：表示对文件可进行读写操作（添加到当前文件尾部）

'b':表示要读写二进制数据

## 对象
### 实例方法、类方法、静态方法的区别
1，实例方法
  - 在类中定义，self 为第一个参数
  - 可以通过实例和类去调用
  - 实例调用时，会自动化把当前调用对象当做self传入
  - 类调用时，不会自动传递self，需要我们手动传递

2，类方法
  - 类内部 @classmethod 修饰的方法
  - 第一个参数默认是cls，也会被自动传递
  - 也可以通过类和实例去调用
 
3，在类中 @staticmethod 修饰的方法
  - 静态方法不需要指定参数
  - 静态方法可以通过类和实例去调用  
  - 基本上是一个和当前类无关的方法，它只是一个保存到当前类中的函数
  - 静态方法一般都是一些工具方法，和当前类无关
  -
### dict 和 tuple 及 list 的区别
  - tuple 不可变对象，list和dict都是可变对象
  - list 有序；dict 无序，键值对形式存储
  - list 查找速度慢，需要有序查找；dict 查找速度快，不管有多少个元素时间都一样
  - list 可以重复，存放任意对象 ； dict 的 key 为不可变对象，且不可重复（字典的值可以是任意对象）

### 集合
  - 集合中只能存储不可变对象
  - 集合中存储的对象是无序（不是按照元素的插入顺序保存）
  - 集合中不能出现重复的元素

### JSON 和 dict 的区别
  - JSON 是一种数据格式，纯字符串。dict 是一种完整的数据结构；
  - dict 是一个完整的数据结构，是对 Hash Table 这一数据结构的一种实现，是一套从存储到提取都封装好了的方案。它使用内置的哈希函数来规划 key 对应 value 的存储位置，从而获得O（1）的数据读取速度；
  - JSON 的 key 只能是字符串，Python 的 dict 可以是任何可 hash 对象（不可变对象）；
  - JSON 的 key 可以是有序、可重复的；dict 的 key 不可重复，且无序；
  - JSON 任意 key 存在默认值 undefined，dict 默认没有默认值；
  - JSON 访问方式可以是[],也可以是.，遍历方式分 in、of；dict 的 value 仅可以下标访问；
  - dict 可以嵌套 tuple，JSON 里只有数组；

## 底层
### Python 会不会出现内存泄漏，为什么？
  - python 使用的是引用计数器算法，只有引用个数为0的对象才会被回收，如何存在循环依赖，则永远不会被回收
  - Python 中的整数可以无穷大，如果只申请内存不释放，也会发生内存泄露
  - 第三方库引起的
 
### Python 的同步和异步
  - 同步：调用者得到了最终结果，并且在得到结果之前不干别的事
  - 异步：调用者没有得到最终结果，而是拿到了一个临时结果，调用者先去干别的事

## 基本语法
### python中内置的数据结构有几种
  - 整型 int、 浮点型 float、 复数 complex
  - 字符串 str、 列表 list、 元组 tuple
  - 字典 dict 、 集合 set
  - Python3 中没有 long，只有无限精度的 int

### Python中变量的作用域？

L: local 函数内部作用域

E: enclosing 函数内部与内嵌函数之间

G: global 全局作用域

B: build-in 内置作用

python在函数里面的查找分为4种，称之为LEGB，也正是按照这是顺序来查找的

### python为什么没有函数重载机制？

函数重载主要是为了解决两个问题。 1。可变参数类型。 2。可变参数个数。

另外，一个基本的设计原则是，仅仅当两个函数除了参数类型和参数个数不同以外，其功能是完全相同的，此时才使用函数重载，如果两个函数的功能其实不同，那么不应当使用重载，而应当使用一个名字不同的函数。

好吧，那么对于情况 1 ，函数功能相同，但是参数类型不同，python 如何处理？答案是根本不需要处理，因为 python 可以接受任何类型的参数，如果函数的功能相同，那么不同的参数类型在 python 中很可能是相同的代码，没有必要做成两个不同函数。

那么对于情况 2 ，函数功能相同，但参数个数不同，python 如何处理？大家知道，答案就是缺省参数。对那些缺少的参数设定为缺省参数即可解决问题。因为你假设函数功能相同，那么那些缺少的参数终归是需要用的。

好了，鉴于情况 1 跟 情况 2 都有了解决方案，python 自然就不需要函数重载了。

### 位置参数与关键字参数
  - 位置参数
    位置参数就是将对应位置的实参复制给对应位置的形参
    第一个实参赋值给第一个形参，第二个实参赋值给第二个形参 。。。
    fn(1 , 2 , 3)

  - 关键字参数
    关键字参数，可以不按照形参定义的顺序去传递，而直接根据参数名去传递参数
    fn(b=1 , c=2 , a=3)
    print('hello' , end='')
    位置参数和关键字参数可以混合使用
    混合使用关键字和位置参数时，必须将位置参数写到前面
    
### 默认参数
 定义一个函数
 定义形参时，可以为形参指定默认值
 指定了默认值以后，如果用户传递了参数则默认值没有任何作用
 如果用户没有传递，则默认值就会生效
        def fn(a = 5 , b = 10 , c = 20):
           print('a =',a)
           print('b =',b)
           print('c =',c)
### 不定长参数

  定义一个函数，可以求任意个数字的和
  def sum(*nums):
     # 定义一个变量，来保存结果
     result = 0
     # 遍历元组，并将元组中的数进行累加
      for n in nums :
         result += n
     print(result)


### 函数调用参数的传递方式是值传递还是引用传递？

函数的传值到底是值传递还是引用传递、要分情况：

不可变参数用值传递：像整数和字符串这样的不可变对象，是通过拷贝进行传递的，因为你无论如何都不可能在原处改变不可变对象。

可变参数是引用传递：比如像列表，字典这样的对象是通过引用传递、和C语言里面的用指针传递数组很相似，可变对象能在函数内部改变。

### 为什么函数名字可以当做参数用?
Python中一切皆对象，函数名是函数在内存中的空间，也是一个对象

### Python中pass语句的作用是什么？
 在编写代码时只写框架思路，具体实现还未编写就可以用pass进行占位，是程序不报错，不会进行任何操作。

### 回调函数，如何通信的?

回调函数是把函数的指针(地址)作为参数传递给另一个函数，将整个函数当作一个对象，赋值给调用的函数。

###  lambda 函数？
    匿名函数 lambda 函数表达式 （语法糖）
    lambda函数表达式专门用来创建一些简单的函数，他是函数创建的又一种方式
    语法：lambda 参数列表 : 返回值
    匿名函数一般都是作为参数使用，其他地方一般不会使用


    def fn5(a , b):
        return a + b
    
    fn6 = lambda a,b : a + b
       print(fn6(10,30))
       
### 什么是闭包？
在函数内部再定义一个函数，并且这个函数用到了外边函数的变量，那么将这个函数以及用到的一些变量称之为闭包。
通过闭包可以创建一些只有当前函数能访问的变量，可以将一些私有的数据藏到的闭包中

形成闭包的要件
  ① 函数嵌套
  ② 将内部函数作为返回值返回
  ③ 内部函数必须要使用到外部函数的变量
 

def make_averager():
    # 创建一个列表，用来保存数值
    nums = []

    # 创建一个函数，用来计算平均值
    def averager(n) :
        # 将n添加到列表中
        nums.append(n)
        # 求平均值
        return sum(nums)/len(nums)

    return averager

averager = make_averager()


### Python中的可变对象和不可变对象？

不可变对象，该对象所指向的内存中的值不能被改变。当改变某个变量时候，由于其所指的值不能被改变，相当于把原来的值复制一份后再改变，这会开辟一个新的地址，变量再指向这个新的地址。

可变对象，该对象所指向的内存中的值可以被改变。变量（准确的说是引用）改变后，实际上其所指的值直接发生改变，并没有发生复制行为，也没有开辟出新的地址，通俗点说就是原地改变。

Pyhton中，数值类型(int 和float)，字符串str、元组tuple都是不可变类型。而列表list、字典dict、集合set是可变类型

### Python的魔法方法

魔法方法就是可以给你的类增加魔力的特殊方法，如果你的对象实现（重载）了这些方法中的某一个，那么这个方法就会在特殊的情况下被Python所调用，你可以定义自己想要的行为，而这一切都是自动发生的，它们经常是两个下划线包围来命名的（比如__init___,__len__),Python的魔法方法是非常强大的所以了解其使用方法也变得尤为重要!

__init__构造器，当一个实例被创建的时候初始化的方法，但是它并不是实例化调用的第一个方法。

__new__才是实例化对象调用的第一个方法，它只取下cls参数，并把其他参数传给__init___.

___new__很少使用，但是也有它适合的场景，尤其是当类继承自一个像元组或者字符串这样不经常改变的类型的时候。

__call__让一个类的实例像函数一样被调用

__getitem__定义获取容器中指定元素的行为，相当于self[key]

__getattr__定义当用户试图访问一个不存在属性的时候的行为。

__setattr__定义当一个属性被设置的时候的行为

__getattribute___定义当一个属性被访问的时候的行为

### 生成器与 yield
在 Python 中，使用了 yield 的函数被称为生成器（generator）。

跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。

在调用生成器运行的过程中，每次遇到 yield 时函数会暂停并保存当前所有的运行信息，返回 yield 的值, 并在下一次执行 next() 方法时从当前位置继续运行。

调用一个生成器函数，返回的是一个迭代器对象。

