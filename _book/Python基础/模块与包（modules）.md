# 第18节：模块与包（modules）
## 模块
模块与包是任何大型程序的核心，就连python安装程序本身也是一个包

定义：是一个包含python定义和语句的脚本文件，模块相当于文件
## 包
### 定义：是模块的集合，包类似于文件夹
### 分类
* 正规包
    文件夹中包含 __init__.py  文件
* 命名空间包
    不包含__init__.py  文件  （）、 不受物理位置限制
### 常用操作
#### 导入模块的方式
```
爬虫可以协同开发  （爬虫、 pip、 登录问题，实现不同功能的代码放到一起，就需要模块。每一个模块里都有命名的空间，变量函数都在这个空间里。）

from mymodules import aa
import mymodules.aa
import mymodules.aa as aa     # 起别名
aa.aa1()
from mymodules import aa as a
a.aa1()
from .mymodules import aa       # 不会报红线错，但是主文件不行，不能这样用
aa.aa1()
from mymodules.sonModules import bb
bb.bbfun()
from mymodules.sonModules import bb
bb.bbfun()
from mymodules.sonModules.bb import *       # 把bb里的命名空间导入到了主运行函数里 ； from 后跟包或者由包组成的路径  ；import 后跟 模块 ； as 后跟别名
bbfun()
aa1()
```
```
模块的导入顺序

re.py   先从当前目录寻找包，然后从系统路径中寻找
sys.path  列表数据 中保存的寻址路径   cmd 中执行  import sys -> sys.path    可以添加自己的路径
```
```
相对路径导入包中子模块

在非主运行包中 可以使用 相对路径的方式导入  
. 当前  
.. 上一级
```
```
运行包

__main__   可以使包直接运行   
cd desktop -> python demo
```
```
通过字符串导入包

# 通过字符串导入包 : 有一堆包，可以遍历导入。scrappy里的setting里的中间件，遍历那个对象（字符串），然后根据键的排序调用：collections。
import time
import importlib
time = importlib.import_module("time")
time.sleep(1)
print(time)
```
### 相关属性
```
print(__file__)     # 保存的文件的路径
print(__name__)     # __main__  包的注释，主运行的文件，给赋上main
print(__package__)      # None  默认情况下是None，作为模块
print(__path__)    #包命名空间
```