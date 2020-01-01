---
title: Python学习笔记(1)
date: 2016-07-01 14:12:30
tags: Python
categories: 服务端
---

### 纯函数式编程
- 特点：不需要变量、没有副作用、测试简单
- 支持高阶编程，可以把函数作为参数、代码简洁


map()是 Python 内置的高阶函数，它接收一个函数 f 和一个 list，并通过把函数 f 依次作用在 list 的每个元素上，得到一个新的 list 并返回。
map()函数不改变原有的 list，而是返回一个新的 list。
s.strip(rm) 删除 s 字符串中开头、结尾处的 rm 序列的字符。
当rm为空时，默认删除空白符（包括'\n', '\r', '\t', ' ')

内层函数引用了外层函数的变量（参数也算变量），然后返回内层函数的情况，称为闭包（Closure）

关键字lambda 表示匿名函数，冒号前面的 x 表示函数参数

包里要有一个 __init__.py的文件，python才会当做包处理


try 的作用是捕获错误，并在捕获到指定错误时执行 except 语句。
Python 3.x已经改进了整数的除法运算，“/”除将得到浮点数，“//”除才仍是整数
在Python 3.x中，字符串统一为unicode，不需要加前缀 u，而以字节存储的str则必须加前缀 b

### 模块管理工具
- easy_install
- pip

类名以大写字母开头，紧接着是(object)，表示该类是从哪个类继承下来的
super(Student, self).__init__(name, gender) 去初始化父类，否则，继承自 Person 的 Student 将没有 name 和 gender
在一条继承链上，一个实例可以看成它本身的类型，也可以看成它父类的类型
动态语言和静态语言（例如Java）最大的差别之一。动态语言调用实例方法，不检查类型，只要方法存在，参数正确，就可以调用

对象里的方法要有参数
Python的网络服务器有TCPServer、UDPServer、UnixStreamServer、UnixDatagramServer，而服务器运行模式有 多进程ForkingMixin 和 多线程ThreadingMixin两种
用 type() 函数获取变量的类型，它返回一个 Type 对象
用 dir() 函数获取变量的所有属性
已知一个属性名称，要获取或者设置对象的属性，就需要用 getattr() 和 setattr( )函数

```
for k, v in arg.iteritems():
    setattr(self, k, v)
```
如果一个属性由双下划线开头(__)，该属性就无法被外部访问
如果一个属性以"__xxx__"的形式定义，那它又可以被外部访问了，以"__xxx__"定义的属性在Python的类中被称为特殊属性，有很多预定义的特殊属性可以使用，通常我们不要把普通属性用"__xxx__"定义
以单下划线开头的属性"_xxx"虽然也可以被外部访问，但是，按照习惯，他们不应该被外部访问。

del p1.address 删除实例属性
types.MethodType() 把一个函数变为一个方法
函数调用不需要传入 self，但是方法调用需要传入 self

通过标记一个 @classmethod，该方法将绑定到 Person 类上，而非类的实例。类方法的第一个参数将传入类本身，通常将参数名命名为 cls，上面的 cls.count 实际上相当于 Person.count。

sorted() 按照默认的比较函数 cmp 排序
```
def count():
    fs = []
    for i in range(1, 4):
        def f(j):
            def g():
                return j*j
            return g
        r = f(i)
        fs.append(r)
    return fs
f1, f2, f3 = count()
print f1(), f2(), f3()
```

有的是Math.
有的是数值.
有的是函数()

python起服务，连接服务器
装饰器

递推法??

```
def __init__(self, num):
    a, b, L = 0, 1, []
        for n in range(num):
            L.append(a)
            a, b = b, a + b
        self.numbers = L
```

有理数运算
```
@property
def grade(self):
    if self.score >= 80:
        return 'A'
    elif self.score < 60:
        return 'C'
    else:
        return 'B'
```

lambda函数是一个简短的匿名函数。

lambda函数可以接受任意数量的参数，但只能包含一个表达式。

__slots__是指一个类允许的属性列表
所有的函数都是可调用对象。
一个类实例也可以变成一个可调用对象，只需要实现一个特殊方法__call__()


后续多线程，数据库，web编程，脚本，爬虫