# 第16节：with  上下文管理器
## 概述
上下文管理器是一个对象，它定义了在执行with语句时要建立的运行时上下文。上下文管理器处理执行代码块所需的运行是上下文的入口和出口。上下文管理器通常使用with语句调用，但是也可以通过直接调用它们的方法来使用。
## 作用
with还可以处理下文的异常（对里面的错误进行捕获）
## 用途
1. 保存和恢复各种全局状态
2. 锁定和解锁资源
3. 关闭打开的文件
## 重点
```
### 重点来了
# with 上下文管理器
# 语法
# with open('day04.txt','rb') as f:        # open('day04.txt','rb') 作为上下文管理器赋给 f,它会加上 __enter__、__exit__
#     f.read()

# 模拟上下文管理器
class Simple:       # 外边的是全局的，是上文
    def __enter__(self):        # 入口
        print("enter")
        return self
    def __exit__(self, exc_type, exc_val, exc_tb):      # 终究会退出    不管正确与否都要一个出口，可以处理下文的异常（对里面的错误进行捕获）
        print('exit')
        # print("exc_type",exc_type)
        # print("exc_val",exc_val)
        # print("exc_tb", exc_tb)
        # return True     # 不报错了，对错误进行改造
    # def run(self):
    #     print(1/0)
#
# def simple():
#     print("simple")
#     return Simple()

with Simple() as f:
    print("f")
    # f.run()     # 下文
```