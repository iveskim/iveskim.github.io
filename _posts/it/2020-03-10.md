---
layout: post
title: jenkins 不同步删除文件
category: it
tags: [it]
no-post-nav: true
---


不使用增量同步，同步前先删除文件  --delete-before
用rsync删除目标目录：
rsync --delete-before -a -H -v --progress --stats /tmp/test/ log/

选项说明：
--delete-before 接收者在传输之前进行删除操作
--progress 在传输时显示传输过程
--a 归档模式，表示以递归方式传输文件，并保持所有文件属性
--H 保持硬连接的文件
--v 详细输出模式
--stats 给出某些文件的传输状态