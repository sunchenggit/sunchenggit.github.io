---
title: yarn-setting
date: 2020-10-19 17:33:43
tags:
---
# yarn 常用命令

1. 怎么查看yarn全局安装的模块位置
```
yarn global dir
```
<!--more-->

2. 查看当前源
```
yarn config get registry
```
3. 设置默认源
```
yarn config set registry https://registry.npm.taobao.org/
```
4. 查看yarn的bin目录
```
yarn global bin
```
5. 将这个目录加入 环境变量