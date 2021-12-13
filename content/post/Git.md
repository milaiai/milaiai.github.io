+++
author = "Yubao"
title = "Git"
date = "2019-03-10"
description = "Git"
image = "img/cover.jpg"
tags = [
    "Tools",
]
archives = ["2019/03"]

+++

# Tips

## Update the http post buffer value

```sh
git config --global http.postBuffer 1048576000
```

# Common Questions

## gnutls_handshake() failed: The TLS connection was non-properly terminated

```shell
Cloning into 'Sophus'...
fatal: unable to access 'https://github.com/yubaoliu/Sophus.git/': gnutls_handshake() failed: The TLS connection was non-properly terminated.
ERROR: Service 'orbslam3' failed to build: The command '/bin/sh -c git clone https://github.com/yubaoliu/Sophus.git && cd Sophus && git checkout master && mkdir build && cd build && cmake .. -DCMAKE_BUILD_TYPE=Release && make -j3 && make install' returned a non-zero code: 128
```

Solution:

```sh
git config --global --unset https.https://github.com.proxy  
git config --global --unset http.https://github.com.proxy
```
## error: RPC failed; curl 56 GnuTLS recv error (-54): Error in the pull function.

Error Message:

```sh
error: RPC failed; curl 56 GnuTLS recv error (-54): Error in the pull function.
fatal: The remote end hung up unexpectedly
fatal: early EOF
fatal: index-pack failed
```

