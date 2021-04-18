---
layout: post
title: Virtualenv创建Python3环境
category: it
tags: [python]
no-post-nav: true
---
```
# 创建虚拟环境
$ virtualenv -p python3 ~/FOLDER-PATH/venv3
# 或更具体的指定路径（同样适用于Python2的安装）
$ virtualenv -p /usr/local/opt/python/libexec/bin/python ~/FOLDER-PATH/venv3

# 进入虚拟环境
$ source ~/FOLDER-PATH/venv3/bin/activate

# 退出环境
deactivate
```
参考文献：
[Virtualenv创建Python3环境](https://www.jianshu.com/p/1f4fa9eb1ef6)