title: ubuntu下python+django环境搭建
date: 2015-08-10 13:09:36
tags: [django]
---
一，首先列出需要安装的东西：
----------

|名称|说明|命令|
|---|---|---|
|python2.7|这个安装就不用多说了linux都会自带的
|easy_install|一个能安装python工具的命令|`sudo apt-get install python-setuptools`
|pip|python包管理工具|`sudo easy install pip`
|git|版本管理工具实现多人合作开发|`sudo apt-get install git`
|django|项目开发框架（建议先不要安装在全局）|`sudo easy install django`
|virtualenv|提供一个用于开发的模拟环境 |`sudo easy installvirtualenv`
|sublime|编辑器                                     
      到这里需要安装的东西就没有啦~


 二，使用virtualenv建立虚拟开发环境
----------
转到开发目录（cd filename / 打开filename  cd ..  /后退   mkdir filename/ 创建名为filename的文件）用到的3基本个命令
执行命令：virtualenvenv                   #创建名为env的环境
执行命令：source env/bin/activate   #进入env环境    这时命令行前面会有（env）这个标志
执行命令：pipfreeze                          #查看当前env目录下安装包的情况 正常情况下是什么都没有 或是默认安装几个重要包
执行命令：pip install django            #安装djangodjango框架安装在env环境中 
再次执行：pip freeze                          #会发现多了一个django
三，使用django创建一个工程
----------


执行命令：django-admin.py startproject mysite #创建一个名为mysite的django工程
进入mysite目录：cd mysite
执行命令：python manage.py runserver
在浏览器地址栏输入：http://127.0.0.1:8000/      #会发现它已经在工作了