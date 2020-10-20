---
title: node-seeting
date: 2020-10-19 17:31:53
tags:
---

# Node安装与配置

1. 直接[官网](https://nodejs.org/zh-cn/)下载`windows`版本安装

2. 更换源为淘宝镜像源
```
npm config set registry http://registry.npm.taobao.org
// 运行成功之后可通过下面的方式验证
npm config get registry
// 或
npm info express
// 或 在个人文件夹里的 .npmrc 文件加上下面代码
registry=https://registry.npm.taobao.org/
puppeteer_download_host=https://npm.taobao.org/mirrors
electron_mirror=https://npm.taobao.org/mirrors/electron/
sass_binary_site=https://npm.taobao.org/mirrors/node-sass/
// 或则用命令设置 node-sass 的安装地址
npm config set sass_binary_site https://npm.taobao.org/mirrors/node-sass/
```

3. 更换源之后运行下面命令来更新npm的版本
```
npm i npm -g
```
4. 或者使用cnpm来代替npm的使用
```
npm install -g cnpm --registry=https://registry.npm.taobao.org
```

# npm 常用命令

* 查看当前目录已安装依赖
```
npm list --depth=0
```
* 查看全局目录已安装依赖
```
npm list --depth=0 --global
```