---
title: hexo的多台设备之间的同步
date: 2019-06-23 11:08:50
tags: [hexo, 同步]
---

最近实验室换了新的电脑，想到我的blog还在原先的电脑上呢，不能就这样放弃了blog之旅，因此希望在之后换电脑的时候可以方便的实现hexo博客的搬运。因此写下这篇博客来备忘。

首先，需要在自己的github上的blog的repository中创建一个hexo的分支，来存放hexo的一些配置文件。如下的是我的分支存放的

![1561285894092](C:\Users\USER\AppData\Roaming\Typora\typora-user-images\1561285894092.png)

创建分支 

```
git remote add origin git@github.com:用户/用户.github.io.git #连接到远程的GitHub上
git branch hexo #创建一个hexo的分支
git remote add origin git@github.com:yourname/yourname.github.io.git  #将本地与Github项目对接
git push origin hexo #push到github项目的hexo的分支上
```

并且设置hexo为默认分支，这样在之后的一些操作比较方便

在别的电脑是执行如下操作

```
git remote add origin git@github.com:用户/用户.github.io.git #连接到远程的GitHub上
git clone git@github.com:用户/用户.github.io.git #将远程的GitHub项目下载到本地
进入clone的文件中
npm install    #注意，这里一定要切换到刚刚clone的文件夹内执行，安装必要的所需组件，不用再init
#生成新的笔记  可能用到 hexo clean 命令
hexo new post "new blog name"   #新建一个.md文件，并编辑完成自己的博客内容
hexo g   
hexo d 
#下面是将配置提交给GitHub
git add .
git commit -m hexo
git push  //更新分支
```

由上面步骤可以实现不同电脑之间的hexo同步