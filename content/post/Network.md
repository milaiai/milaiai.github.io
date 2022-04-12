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

# Sftp

- 安装 ssh 服务端
sudo apt-get install openssh-server
- 显示 sshd 即可以成功连接
ps -e |grep ssh
- 如果不显示 sshd
sudo /etc/init.d/ssh start

- [SSH能连接上，但SFTP不能/无法连接的三个解决方案](https://blog.csdn.net/qq_37435462/article/details/113962129)

无解，继续Google解决办法 https://www.linuxquestions.org/questions/linux-server-73/can't-get-sftp-logging-to-work-931609/ 收到启发，将 /etc/ssh/sshd_config 中的

Subsystem      sftp    /usr/libexec/openssh/sftp-server
改为
Subsystem       sftp    internal-sftp

重启sshd后，sftp正常工作了。

但是原因仍然不知为何，回头看看，发现 /usr/libexec/openssh/sftp-server 没有任何权限：
# ll /usr/libexec/openssh/sftp-server
----------. 1 root root 63544 2月  22 2013 /usr/libexec/openssh/sftp-server

正常情况应该是这样：
# ll /usr/libexec/openssh/sftp-server
-rwxr-xr-x. 1 root root 63544 Nov 23  2013 /usr/libexec/openssh/sftp-server

咨询大师说 停止openssh 服务 rm sftp-server文件  正常的scp 过去 再启动openssh
但是我是远程操作，生产系统，不敢停止openssh服务，万一连不上就瓜了，大师建议那就先这样用着。

Note：/usr/libexec/openssh/sftp-server没任何权限，root用户都没法删除修改。

重启sshd
[root@k8s-master d138]# systemctl restart sshd
现在就可以连上SFTP了
