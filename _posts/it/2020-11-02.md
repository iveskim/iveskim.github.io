---
layout: post
title: 获取文件后缀名
category: it
tags: [it]
no-post-nav: true
---
## demo 
获取文件名
> 文件名 FULLPATH=backup.tar.gz
> basename “$FULLPATH” .tar.gz 
> backup

判断输入变量为空
```angular2
#!/bin/bash
if [ ! -n "$1" ] ;then
    echo "you have not input a word!"
else
    echo "the word you input is $1"
fi
```

传递脚本参数个数
```angular2
$#	传递到脚本的参数个数
```

shell截取文件名和后缀
```angular2
$fullfile=/the/path/foo.txt
$fullname=$(basename $fullfile)
```
## 参考资料
[Shell 字符串处理、获取文件名和后缀名](https://blog.csdn.net/guojin08/article/details/38704823)
[Shell脚本中判断输入变量或者参数是否为空的方法](https://www.jb51.net/article/56550.htm)
[关于 Shell 参数传递 与 默认值](https://www.linuxidc.com/Linux/2018-11/155618.htm)
[Shell 截取文件名和后缀](http://zuyunfei.com/2016/03/23/Shell-Truncate-File-Extension/)
