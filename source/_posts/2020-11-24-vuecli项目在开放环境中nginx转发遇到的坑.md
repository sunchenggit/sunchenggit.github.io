---
title: vuecli项目在开放环境中nginx转发遇到的坑
date: 2020-11-24 08:34:01
tags: vue
categories: 技术随笔
---

> `vuecli`项目在生产环境中如果遇到需要`nginx`做转发到其他域名下面去可能会遇到的坑！

* sockjs-node 报错、已经本地修改文件服务器中能正常监听到文件改变

```javascript
module.exports = {
  ...
  devServer: {
    ...
    // 解决 sockjs-node 接口报错
    public: 'http://www.lanyun.test:9528',
    // 解决 sockjs-node 一直请求接口
    disableHostCheck: true
  },
  configureWebpack: {
    ...
    // 处理 window 下修改文件后，服务器中不能监听变化的问题
    devServer: {
      watchOptions: {
        ignored: /node_modules/,
        poll: true
      }
    }
  }
}

```

* `homestead` 中需要注意安装`npm`依赖会出现问题，建议是不要使用 `sass` 了，准备开始向 `postcss` 上转
如果实在要用sass来写出现报错的时候试一下 `npm rebuild node-sass` 这个命令
