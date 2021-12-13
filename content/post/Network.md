+++
author = "Yubao"
title = "Network"
date = "2019-03-10"
description = "Network"
image = "img/cover.jpg"
tags = [
    "Network",
]
archives = ["2019/03"]

+++

# DNS

vim /etc/resolv.conf

```sh
nameserver 8.8.8.8
nameserver 8.8.4.4
```

# github


- [rosdep update 超时失败2021最新解决方法](https://blog.csdn.net/Kenny_GuanHua/article/details/116845781)
- GitHub Proxy: https://ghproxy.com/


# APT

```sh
$ sudo touch /etc/apt/apt.conf.d/proxy.conf
$ sudo gedit /etc/apt/apt.conf.d/proxy.conf
```

```sh
Acquire {
  HTTP::proxy "http://127.0.0.1:8080";
    HTTPS::proxy "http://127.0.0.1:8080";
    }
```
