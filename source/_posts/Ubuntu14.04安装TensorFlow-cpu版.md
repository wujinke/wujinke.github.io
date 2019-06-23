---
title: Ubuntu14.04安装TensorFlow-cpu版
date: 2019-06-13 15:05:07
tags: [深度学习, TensorFlow, 虚拟环境]
---

# TensorFlow的安装

首先安装python3的pip3工具，命令如下

```
sudo apt-get install python3-pip python3-dev
```

安装完之后需要更新一下pip3

```
sudo pip3 install --upgrade pip
```

然后安装 TensorFlow

```
sudo pip3 install --upgrade tensorflow
```

在安装的过程可能遇到 不能安装six这个问题，因此还要安装这个依赖

```
sudo pip3 install six --upgrade
```

即可完成。

<!--more-->

# 虚拟环境

当然为了考虑到机器上可能会有多个版本，可以创建虚拟环境，在虚拟环境下进行安装。

```
sudo pip3 install virtualenv
%创建一个名为TensorFlow的虚拟环境
virtualenv --system-site-packages ~/tensorflow
%激活虚拟环境
source ~/tensorflow/bin/activate
```

为了使jupyter notebook 使用不同的虚拟环境

```
%为虚拟环境创建kernel
pip3 install -n 环境名称 ipykernel
python -m ipykernel install --user --name 环境名称 (--display-name "显示的名称")
```

# 端口映射

为了使jupyter notebook 可以被远程使用

```
sudo apt install openssh-server
sudo service ssh start
%关闭防火墙
sudo ufw disable
%有时候可能存在公钥缓存，使得连接失败，因此需要清除公钥
ssh-keygen -R "你的远程服务器ip地址" 
```

