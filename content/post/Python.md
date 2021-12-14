+++
author = "Yubao"
title = "Python"
date = "2019-03-10"
description = "Python"
image = "img/cover.jpg"
tags = [
    "Python",
]
archives = ["2019/03"]

+++

# Pip source list

https://www.cnblogs.com/chenjo/p/14071864.html

~/.pip/pip.conf

```sh
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
[install]
trusted-host=mirrors.aliyun.com
```

# Set source list for **pip install**

```sh
pip install pymysql -i https://pypi.tuna.tsinghua.edu.cn/simple/


// 国内源
pip install 包名-i http://pypi.douban.com/simple/ --trusted-host pypi.douban.com
```

# References
- [pip安装包报错Could not find a version that satisfies the requirement pymysql (from versions: none)](https://zhuanlan.zhihu.com/p/361790784)
