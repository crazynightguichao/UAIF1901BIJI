# 第12节：面向对象OOP
面向对象OOP
（Object Oriented Programming）
## 类与对象概述
```
类：类是对象的抽象，比如飞机图纸，月饼模具
对象：对象是类的实例，比如飞机、月饼
面向对象的三大特点：封装、继承（默认继承object）、多态
关系：类是对象的模型，对象是类的具体实例化
```
## 语法
```
"""
class  类名(基类、父类)
    # 实例属性
    def __int__(self):   # self => this 实例 ;  __int__ => constructor (构造函数)
        self.name='wss'
        self.age = 18
    # 实例方法
    def say(self):
        print(self.name)
"""
```
```
# class Person:
#     def __init__(self,name='wss',age=18):
#         self.name= name
#         self.age = age
#     def say(self):
#         print("my name is %s"%self.name)
#     def a(self):
#         print("I am %s years old"%self.age)
# # 实例化，创建对象
# xm = Person('小明',17)
# xm.say()
# xm.a()
```
## [案例](https://note.youdao.com/ynoteshare1/index.html?id=99ead3ea1cecda9dae486ee0b81568e8&type=note)
### 案例一：时钟
```
## 创建一个时钟类
# 属性  小时:分钟:秒钟
# 方法
# run  表跑起来
# set  设置时间
# print（obj）  输出现在的时间
# class Clock:
#     def __init__(self,hou=0,min=0,sec=0):     # 魔法方法
#         self.hou = hou
#         self.min = min
#         self.sec = sec
#     def __str__(self):    # 对实例的描述  print(obj) 打印 __str__()魔法方法的返回值
#         return '%0.2d:%0.2d:%0.2d'%(self.hou,self.min,self.sec)
#     def run(self):
#         while True:
#             print(self)
#             time.sleep(1)   # 阻塞代码
#             self.sec += 1
#             if self.sec>59:
#                 self.min+=1
#                 self.sec=0
#                 if self.min>59:
#                     self.hou+=1
#                     self.min=0
#                     if self.hou>23:
#                         self.hou=0
#
#
# c1 = Clock(0,0,0)
# c1.run()
```
### 案例二：烤地瓜
```
## 创建一个烤地瓜类
# 属性：
# cookedLevel：这是数字；0~3表示还是生的，超过3表示半生不熟，超过5 表示已经烤好了，超过8表示已经烤成了木炭！地瓜刚开始的时候是生的。
# cookedString：这是字符串；描述地瓜的生熟程度
# condiments:这是地瓜的配料表，比如番茄酱、芥末酱
# 方法：
# cook() 把地瓜烤一段时间
# addCondiments() 给地瓜添加配料
# __init__() 设置默认属性
# __str__() 让print的结果看起来更好一些

class Potato:
    def __init__(self,cookedLevel=0,cookedString='生',condiments='番茄酱'):
        self.cookedLevel = cookedLevel
        self.cookedString = cookedString
        self.condiments = condiments
        self.condimentsList = ['芥末酱','番茄酱','甘梅酱']
    def __str__(self):
        return '您好，这是您的%s口味的%s的地瓜'%(self.condiments,self.cookedString)
    def cook(self,min):
        # while True:                    # 没有这行代码，结果打印一行
        #     time.sleep(1)                     # 阻塞代码
            self.cookedLevel += min             # 每秒加一
            if self.cookedLevel>=0 and self.cookedLevel<4:
                self.cookedString = '生'
            elif self.cookedLevel<6:
                self.cookedString = '半生不熟'
            elif self.cookedLevel<8:
                self.cookedString = '可以享用了'
            elif self.cookedLevel>=8:
                self.cookedString = '糊巴了'
    def addCondiments(self,num):
        self.condiments = self.condimentsList[num]


# 客户来了
p1 = Potato()
p2 = Potato()
p3 = Potato()
p4 = Potato()

p1.cook(2)
p2.cook(5)
p3.cook(7)
p4.cook(9)

p1.addCondiments(0)
p2.addCondiments(2)
p3.addCondiments(1)
p4.addCondiments(2)

print(p1)
print(p2)
print(p3)
print(p4)
```
### 案例三：绝地求生
[链接1](https://blog.csdn.net/weixin_33965305/article/details/88115529)
## 类变量（类可以使用的属性）与实例变量（实例可以使用的属性）
* 类变量：定义在类中，可以被类方法（修改），可以被实例访问
* 实例变量：实例变量只能实例调用，且权重大（优先级大），它是后写的，可以把之前的内容覆盖掉
### 案例
```
# class P:
#     sex = '男'       # 类变量，能够被实例继承（图纸）
#
#     def __init__(self):
#         self.name = 'xm'        # 实例属性，实例变量
#         self.sex = '男'          # 实例变量只能实例调用，且权重大（优先级大），它是后写的，可以把之前的内容覆盖掉
#
#     @staticmethod  # 静态类方法，什么都不能调用，就是一个普通的公共函数功能， 连指针都没有
#     def say2():
#         print("this is static")
#
#     @classmethod        # 类方法，可调用类变量
#     def setSex(cls,sex):
#         print(cls.name)
#         cls.sex = sex
#
#     def say1(self):      # 实例方法，可调用实例的方法和属性，还可以调用继承过来的类变量
#         print(self.name)
#         print(self.sex)


# xm = P()
# # xm.sex = '女'        # 创建了实例属性（实例对象），给实例重新赋予属性
# P.sex = '女'       # 所有的实例用的都是同一个类变量
# print(xm.sex)       # 类变量可以被实例调用，实例变量与类变量重名时，优先调用实例变量
# print(P.sex)        # 类变量也可以被类调用

# xh = P()
# xh.say1()
# xh.say2()

# xm = P()
# print(xm.name)
# print(xm.sex)   # 小明的sex继承的类变量
# P.setSex('女')   # 调用类方法，修改类变量
# print(xm.sex)
# xm.setSex('男')     # xm这个实例调用了继承的类方法，修改了类变量
# print(xm.sex)
# xm.sex = '女'    # 添加了实例属性sex，覆盖了继承来的类变量sex，并没有修改了类变量
# print(xm.sex)
# print(P.sex)
```
## 静态类方法、类方法、实例方法
### 静态类方法
@staticmethod
### 类方法
@classmethod
```
"""
静态方法：通过@staticmethod 装饰，不依赖于类变量、类方法，实例变量、实例方法
类方法：通过@classmethod 装饰，修改类变量
实例方法：可调用实例的方法和属性，还可以调用继承过来的类变量
"""
```
## 私有属性和私有方法
__spam
```
所谓私有，就是在外部不能调用，方法之间可以使用的
私有方法以及属性需要在方法名或属性名前加"__",但是python中没有真正的私有方法、私有属性

# class P():
#     def __init__(self,name,age):
#         self.__name = name
#         self.__age = age
#     def say(self):
#         print("my name is %s"%self.__name)      #内部可以使用__name
#
# p = P('小红',19)
# print(dir(p))
# p.__name = "肖红"     # 外部不可使用__name
# p._P__name = "肖红"       # 君子协议，但是可以强制改
# p.say()
```
## 装饰器
```
@property 私有：将方法改成一个同名的属性，这个属性不能修改（因为就没有这个属性，只能看）

# class P():
#     def __init__(self,name,age):
#         self.__name = name
#         self.__age = age
#     def say(self):
#         print("my name is %s"%self.__name)
#
#     @property       # 装饰器
#     def name(self):
#         return self.__name
#
# p = P('小红',19)
# print(dir(p))
# p.name = "1234"   # 只能让外部看，不能修改（比如，血量，枪，金币）
# print(p.name)
```
### 类装饰器
```
def MyClass(obj):
    obj.age = 19        # 类变量
    obj.say = lambda cls:print(cls.age)     # 类方法
    return obj

@MyClass
class P:
    def __init__(self,name):
        self.name = name
class A:

p = P("小红")
print(dir(p))
```
### 实例方法装饰器
```
import time

def sumtime(fn):
    def newFn(self,*args,**kwargs):
        start = time.time()
        fn(self,*args,**kwargs)
        end = time.time()
        print("%s你好帅"%self.name)
        print("总时间：%s"%(end-start))
    return newFn
## 实例方法装饰器
class P:
    def __init__(self,name):
        self.name = name
    @sumtime
    def run(self):
        time.sleep(1)
        print(self.name)

p = P("wss")
p.run()
```
## super()
* super 相当于this指针，用来引用父类而不必显式地指定它们的名称
## 魔法方法
* __slots__  限制Class属性和方法
* __name__   类名字
```
# class P:
#     """
#     Person类    人类
#     """
#     def __init__(self):
#         pass
#     __slots__ = ['name','sex']
#     __name__ = "Person"
#     def run(self):
#         print(self.__doc__)
#
# p = P()
# P.name = "wss"
# p.sex = "男"
# # p.age = 18
# print(dir(p))
# print(p.__doc__)
```
* print(self.__doc__)  类文档字符串、开头注释
```
# 拿到函数的注释
# def fn():
#     """
#     this is fn
#     :return:
#     """
#     pass
# print(fn.__doc__)
```
* __new__  与  __init__  关系
```
__new__   ：第一步、创建一个对象，必须有返回值。把实例创建出来，可能任何属性都没有

__init__    ：第二步、给实例初始化，赋予属性


# __new__  与  __init__  关系
# class Car:
#     def __init__(self):
#         self.color = ""
#
# class BMW(Car):
#     def __new__(cls, *args, **kwargs):      # 第一步、创建一个对象，必须有返回值。把实例创建出来，可能任何属性都没有
#         print("new")
#         return super().__new__(BMW)
#
#     def __init__(self):     # 第二步、给实例初始化，赋予属性
#         print("init")
#         self.pingpai = ''
#
#     def __del__(self):
#         print('del')
#
# b = BMW()       # b运行完被回收了
# # print(dir(b))
# del b
# print(b)
```
* __str__   给实例一个描述
* __del__   实例注销时调用
* [常用魔法方法](https://blog.csdn.net/yunyi4367/article/details/79052970)
## 验证
```
ifinstance（）来检查一个实例的类型
print(isinstance(obj，class))  验证obj是否为class的实例

lssubclass（）来检查类的继承关系
print(issubclass(P,A))

type（）查看类型

dir（）获取对象的属性和方法
```
## 元类

