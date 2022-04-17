
+++
author = "Yubao"
title = "Debug"
date = "2022-03-10"
description = "Debug Tricks"
image = "img/cover.jpg"
tags = [
    "Debug",
]
archives = ["2022/03"]

+++


# Rosrun

```sh
set(CMAKE_BUILD_TYPE Debug)

rosrun --prefix 'gdb -ex run --args' [package_name] [node_name]
```
