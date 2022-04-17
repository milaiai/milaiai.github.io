+++
author = "Yubao"
title = "Ctags-VIM"
date = "2019-03-10"
description = "Ctags"
image = "img/cover.jpg"
tags = [
    "VIM",
]
archives = ["2019/03"]

+++



![](https://image.vimjc.com/images/691e0c29gy1fnnj08ml3qg20k807x3zq.gif)

Command	Function
Ctrl + ]	Go to definition
Ctrl + T	Jump back from the definition
Ctrl + W Ctrl + ]	Open the definition in a horizontal split
:ts <tag_name>	List the tags that match <tag_name>
:tn	Jump to the next matching tag
:tp	Jump to the previous matching tag

# Shortcuts
- Ctrl+] : 取出当前光标下的word作为tag的名字并进行跳转。
- Ctrl+t or Ctrl + o: 跳转到前一次的tag处
- Ctrl+w+]: 分割当前窗口，并且跳转到光标下的tag

# Ctags

- 查看ctags支持的语言
```sh
ctags --list-languages
```
- 查看语言和扩展名的对应关系
```sh
ctags --list-maps
```
- 查看ctags可以识别和记录的语法元素
```sh
ctags --list-kinds
ctags --list-kinds=c++
```
- 对当前目录下所有ctags支持的语言格式文件生成tags
```sh
ctags -R *
```
ctags 默认并不会提取所有标识符的tag标签，以下命令可以生成更加详细的tag文件

```sh
ctags -R --c++-kinds=+p+l+x+c+d+e+f+g+m+n+s+t+u+v --fields=+liaS --extra=+q
```

- 只对特定文件生成tags
```sh
ctags `find -name "*.h"`
```
- 用于跳转到指定的tag。例如：
```sh
tag tagname
```
- 列出曾经访问过的tag的列表

```sh
tags
```
- 同名tag
如果存在多个同名的tag，tag命令会给出一个tag的列表，可以通过键入tag的序号来选择tag；也可以通过tselect来过滤tag，如：:tselect tagname

如果要在多个tag间移动，可以使用如下命令：
```sh
:tfirst             go to first match
:[count]tprevious   go to [count] previous match
:[count]tnext       go to [count] next match
:tlast              go to last match
```
- 其他
如果是多个tags文件，可以通过设置tags选项来引入更多的tags文件。例如: :set tags=./tags, ./../tags, ./*/tags

使用tag命令时，可以输入部分tag名，然后使用Tab键进行补全。

# References
- [ Vim自动生成tags插件vim-gutentags安装和自动跳转方法-Vim插件(10)](https://vimjc.com/vim-gutentags.html)
- [Vim使用ctags实现函数跳转-Vim入门教程(13)](https://vimjc.com/vim-ctag.html)
