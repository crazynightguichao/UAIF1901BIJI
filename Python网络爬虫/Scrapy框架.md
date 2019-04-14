# 第6节：Scrapy框架
[Scrapy框架](https://scrapy-chs.readthedocs.io/zh_CN/latest/)
## [安装](http://www.scrapyd.cn/doc/124.html)
```
scrapy
安装
1.pywin32   http://sourceforge.net/projects/pywin32/    #选择对应版本    (用Anaconda拷过来的安装包安的pywin32)
2.Twisted   http://www.lfd.uci.edu/~gohlke/pythonlibs/#twisted   #选择对应版本
把下载文件放在项目中，pip install **.whl （对应的pip install Twisted-18.9.0-cp36-cp36m-win32.whl）
3.pip install Scrapy
```
## 概述
![image]()
## 四个文件
```
items.py
数据：先创建数据（模型），以一个对象的形式存储
可以在里边写两个方法

middlewares.py
中间件：添加额外功能 (钩子函数)

pipelines.py
管道：数据会输出，输出到piplines.py 管道里，爬一个输出一个，输出一个存一个

settings.py
对爬虫进行设置
```
```
先运行 spiders 里的爬虫文件；然后保存数据类型在items.py；然后数据会输出，输出到piplines.py 管道里，爬一个输出一个，输出一个存一个，还可以继续创建管道。
每个文件都有不同的功能。

## 步骤
# 1.创建项目   scrapy startproject tutorial(项目名称)
# 2.增加items.py  创建数据模型
# 3.创建爬虫文件      scrapy genspider dmoz(爬虫名称)   站点(域名)  “爬虫的主力”
# 4.运行      scrapy crawl dmoz(爬虫名称)  在项目里的任何位置都可以运行【有时会出现问题：处理方法：pip install pypiwin32或pip3 install pypiwin32 或 python -m pip install pypiwin32}】
# scrapt.cfg   配置项
# spiders 文件里边放的是爬虫的所有内容，只要有__init__.py  就证明是一个包，可以被调用。
# douban  也是一个包
```
## 爬取的循环
![image]()
## [运行流程、架构概览](https://scrapy-chs.readthedocs.io/zh_CN/latest/topics/architecture.html#)
![image]()