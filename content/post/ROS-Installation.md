+++
author = "Yubao"
title = "ROS Installation"
date = "2019-03-10"
description = "ROS Installation"
image = "img/cover.jpg"
tags = [
    "ROS",
]
archives = ["2021/12"]

+++

- [rosdep update 超时失败2021最新解决方法](https://blog.csdn.net/Kenny_GuanHua/article/details/116845781)

# rosdep update

Error Message:

````sh
Warning: running 'rosdep update' as root is not recommended.
  You should run 'sudo rosdep fix-permissions' and invoke 'rosdep update' again without sudo.
  ERROR: error loading sources list:
          ('The read operation timed out',)
          reading in sources list data from /etc/ros/rosdep/sources.list.d
          Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml
          Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/base.yaml
          Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/python.yaml
          Hit https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/ruby.yaml
          Hit https://raw.githubusercontent.com/ros/rosdistro/master/releases/fuerte.yaml
          Query rosdistro index https://raw.githubusercontent.com/ros/rosdistro/master/index-v4.yaml
          Skip end-of-life distro "ardent"
          Skip end-of-life distro "bouncy"
          Skip end-of-life distro "crystal"
          Skip end-of-life distro "dashing"
          Skip end-of-life distro "eloquent"
          Add distro "foxy"
          ERROR: Service 'rdsslam' failed to build: The command '/bin/sh -c rosdep update' returned a non-zero code: 1
```
