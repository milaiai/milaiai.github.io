---
author: "yubao"
title: "OpenCV"
image: "img/cover.jpg"
draft: false
date: 2021-12-14
description: "OpenCV"
tags: ["OpenCV"]
archives: ["2021/12"]
---


# Possible Errors

## fatal error: dynlink_nvcuvid.h: No such file or directory

```sh
In file included from /home/yubao/Software/opencv/build/modules/cudacodec/opencv_cudacodec_pch_dephelp.cxx:1:
/home/yubao/Software/opencv/modules/cudacodec/src/precomp.hpp:60:18: fatal error: dynlink_nvcuvid.h: No such file or directory
   60 |         #include <dynlink_nvcuvid.h>
         |                  ^~~~~~~~~~~~~~~~~~~
         compilation terminated.
```

cat modules/cudacodec/src/precomp.hpp

```cpp
#if CUDA_VERSION >= 9000
	#include <dynlink_nvcuvid.h>
#else
	#include <nvcuvid.h>
#endif
```

cuda10 does not provide dynlink_nvcuvid.h any more

- [OpenCV CUDA 10 安装 dynlink_nvcuvid.h 问题解决方法](https://www.cnblogs.com/penguins/p/10214817.html)

## error: ‘CODEC_FLAG_GLOBAL_HEADER’ was not declared in this scope

```sh
/home/yubao/Software/opencv/modules/videoio/src/cap_ffmpeg_impl.hpp:1573:21: error: ‘CODEC_FLAG_GLOBAL_HEADER’ was not declared in this scope; did you mean ‘AV_CODEC_FLAG_GLOBAL_HEADER’?
 1573 |         c->flags |= CODEC_FLAG_GLOBAL_HEADER;
      |                     ^~~~~~~~~~~~~~~~~~~~~~~~
      |                     AV_CODEC_FLAG_GLOBAL_HEADER
```

将CODEC_FLAG_GLOBAL_HEADER改为：

AV_CODEC_FLAG_GLOBAL_HEADER

vim modules/videoio/src/cap_ffmpeg_impl.hpp

```cpp
#define AV_CODEC_FLAG_GLOBAL_HEADER (1 << 22)
#define CODEC_FLAG_GLOBAL_HEADER AV_CODEC_FLAG_GLOBAL_HEADER
```

## error: ‘AVFMT_RAWPICTURE’ was not declared in this scope
```sh
/home/yubao/Software/opencv/modules/videoio/src/cap_ffmpeg_impl.hpp:1604:30: error: ‘AVFMT_RAWPICTURE’ was not declared in this scope
 1604 |     if (oc->oformat->flags & AVFMT_RAWPICTURE) {
```


```cpp
#define AVFMT_RAWPICTURE 0x0020
```

## char* str = PyString_AsString(obj)

```sh
/home/ai/yubao/opencv/modules/python/src2/cv2.cpp:652:1: warning: missing initializer for member ‘_typeobject::tp_print’ [-Wmissing-field-initializers]
/home/ai/yubao/opencv/modules/python/src2/cv2.cpp: In function ‘bool pyopencv_to(PyObject*, T&, const char*) [with T = cv::String; PyObject = _object]’:
/home/ai/yubao/opencv/modules/python/src2/cv2.cpp:856:34: error: invalid conversion from ‘const char*’ to ‘char*’ [-fpermissive]
  856 |     char* str = PyString_AsString(obj);
In file included from /home/ai/yubao/opencv/modules/python/src2/cv2.cpp:1498:
/home/ai/yubao/opencv/build/modules/python3/pyopencv_generated_types.h: In function ‘bool pyopencv_to(PyObject*, T&, const char*) [with T = cv::FileNode; PyObject = _object]’:
/home/ai/yubao/opencv/build/modules/python3/pyopencv_generated_types.h:1343:40: warning: implicitly-declared ‘constexpr cv::FileNode& cv::FileNode::operator=(const cv::FileNode&)’ is deprecated [-Wdeprecated-copy]
 1343 |     dst = ((pyopencv_FileNode_t*)src)->v;
```

Solution:

vim /home/ai/yubao/opencv/modules/python/src2/cv2.cpp

```sh
template<>
bool pyopencv_to(PyObject* obj, String& value, const char* name)
{
    (void)name;
    if(!obj || obj == Py_None)
        return true;
    //char* str = PyString_AsString(obj);
    const char* str = PyString_AsString(obj);
    if(!str)
        return false;
    value = String(str);
    return true;
}
```

# References
