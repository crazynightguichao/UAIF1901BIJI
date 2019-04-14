# 第4节：pip（包管理工具操作）
* pip install novas（下载包裹）机器学习、
* pip install requests == 2.6.0（下载版本）
* pip uninstall novas
* pip show flask（显示包裹信息）
* pip list（显示所有包裹）
* pip freeze > requirements.txt
将安装的包裹列表输出到requirements.txt中（生成了一个提示文件）,以便执行pip install -r requirements.txt（虚拟环境被删掉，只下载了项目代码，自己创建回原虚拟环境（tutorial-env\Scripts\activate.bat）。执行pip install -r requirements.txt（下载回之前输到txt文件的包裹），然后pip list 查看时就有了之前被删掉的安装的包裹。）
```
上传到github时，不上传虚拟环境：删掉这个虚拟文件，在项目文件上右击新建一个文件名为.gitignore，在新建的文件里面写上tutorial-env（忽略的文件名，以便后续安装回该虚拟环境文件夹），VCS里的git里的add直接发布，或者在命令行直接写命令一直到git push推上去，进github主页里就没有那个文件了。
```