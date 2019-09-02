---
title: shell 命令实战合集
type: post
tags: ["Shell", "编程"]
date: 2018-12-29T09:21:11.000Z
category: 编程
published: true
---

- shell 示例脚本

```bash
#!/bin/sh
START=$(date +'%Y-%m-%d %H:%M:%S');echo "Start: $START" >/data/database/onekp/nucl-v2/memo/log
for i in `find /data/database/onekp/nucl-v2/samples/ -name "*.fa"`;
do
    dir=`dirname $i`;
    fa=`basename $i`;
    cd $dir; makeblastdb -in $fa -dbtype nucl;
    echo $i >>/data/database/onekp/nucl-v2/memo/log;
done 
END=$(date);echo "End: $END" >>/data/database/onekp/nucl-v2/memo/log
```

- linux 下使用命令排除当前行及下一行的内容

```shell
sed '/关键字/,+1d' file >file2
```

