---
layout: default
title: default ediotconfig setting
date: 2020-11-24 16:16:24
tags: ediotconfig
categories: 技术随笔
---

> 项目中常用的配置项，要想应用这些样式编辑器必须安装 .editorconfig 插件

```
# http://editorconfig.org
root = true

# 可指定文件后缀
[*]
# 字符编码
charset = utf-8
# 缩进样式 - 空格 / tab
indent_style = space
# 缩进字符 - 2个
indent_size = 2
# 换行符 = lf(linux/os) / crlf(windows)
end_of_line = lf
# 在文件末尾插入新行
insert_final_newline = true
# 除去换行行首的任意空白字符
trim_trailing_whitespace = true

[*.md]
insert_final_newline = false
trim_trailing_whitespace = false

```


