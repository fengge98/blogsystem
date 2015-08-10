title: Git使用记录
date: 2015-08-10 11:20:24
tags: [Git]
---

##授权
生成密钥和公钥

    ssh-keygen -t rsa -C "yourmail@g.com"

注：	

    ssh-keygen在git的安装目录的"bin"目录下。
	windows下填写路径是填写绝对路径，公钥密钥放在git安装      
	目录下的".ssh"文件夹中。例如D:\Git\.ssh\id_rsa     
	此时会创建D:\Git\.ssh文件夹并在其中生成名为id_rsa的一对密钥。
	其中将公钥添加到github.com网站中就可以通过命令行对其进行各种操作。

##登录github.com添加远程仓库。

使用免费的只能选择public模式，添加title和description。完成并记录git clone url（形如：git@github.com\username\projectname）

    git remote add origin git@github.com:fengge98\test.git
创建一个名为origin的远程库关联到账户fengge98下名为test.git的工程

    git push -u origin master
第一次由于远程仓库没有内容使用-u参数，将当前分支master中commit后的内容推送到origin远程库，并将远程库master和当前master关联方便以后的推送和拉取


##本地编写代码

    git branch asdf
    git checkout adsf       #创建名为asdf的分支 并切换到asd
    git checkout -b asdf    #创建名为asdf的分支 并切换到asd
    git add test1.py
    git add test2.py
    ...
    git commit -m "description"
    add并commit				#其中description部分填写当前版本的改动 
    git checkout master  	#切换到主分支
    git merge asdf   		#将adsf提交的改动合并到master分支
    git push   				#将当前版本代码推送到远程库





