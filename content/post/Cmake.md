+++
author = "Yubao"
title = "Cmake"
date = "2019-03-10"
description = "Cmake"
image = "img/cover.jpg"
tags = [
    "Cmake",
]
archives = ["2019/03"]

+++


# Sophus

```sh
RUN git clone https://github.com/yubaoliu/Sophus.git \
    && cd Sophus \
    && git checkout master \
    && mkdir build \
    && cd build \
    && cmake .. -DCMAKE_BUILD_TYPE=Release \
    && make -j3 \
    && make install 
```

# G2O

```sh
RUN git clone https://github.com/yubaoliu/g2o.git \
    && cd g2o \
    && mkdir build \
    && cd build \
    && cmake .. -DCMAKE_BUILD_TYPE=Release \
    && make -j 3 \
    && make install
```


