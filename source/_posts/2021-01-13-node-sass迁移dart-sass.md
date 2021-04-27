---
title: node-sass迁移dart-sass
date: 2021-01-13 10:04:08
tags: node
---

> Sass 官方已在 2020-10-26 正式宣布弃用 LibSass，并推荐使用 Dart Sass https://sass-lang.com/blog/libsass-is-deprecated

# 为什么要换掉 node-sass
由于各种原因，我们在安装 node-sass 的过程中经常会出现安装失败的情况，又或者切换了 Node.js 版本发现 node-sass 需要重新安装才能用，如果你在 docker 中安装 node-sass 还会遇到由于缺少各种依赖导致 node-sass build 失败的情况，又或者在国内由于网络原因导致 node-sass 需要的二进制文件下载不下来而 build 失败。

那么，为什么 node-sass 会有这么多问题呢，这就要涉及到另一个项目： LibSass，在很长一段时间里，用 C/C++ 写的 LibSass 一直是 Sass 语言的一个主流实现，其他语言如果要使用 LibSass，需要有建立一个 wrapper 才可以，在 Node.js 环境里，这个 wrapper 就是广为人知的 node-sass，它的作用就是在 Node.js 环境里用 JavaScript 去调用 LibSass，问题的本质还是在 LibSass。

# Dart Sass
上面的这些问题一直广受 JS 社区广大用户的诟病，Sass 官方也意识到了这个问题，所以现在 Sass 官方宣布使用 Dart Sass 作为 Sass 的主要实现：

> Dart Sass is the primary implementation of Sass, which means it gets new features before any other implementation. It's fast, easy to install, and it compiles to pure JavaScript which makes it easy to integrate into modern web development workflows.

和 LibSass 不同，Dart Sass 最终是被编译成纯粹的 JS 代码来执行的，所以如果使用 Dart Sass，上面那些使用 node-sass 出现的问题就不会再遇到了，另外 Dart Sass 和 node-sass 在暴露给用户的 API 方面是保持一致的，这表示几乎可以无痛迁移。

这里用 webpack 举例：

```shell
yarn remove node-sass
yarn add sass
```

修改 webpack 配置，在 sass-loader 的 options 里加一行 implementation: require('sass')

```javascript
// 基于vue-cli 的项目 vue.config.js
module.exports = {
  // 使用 dark-sass 替换 node-sass 来编译 sass 文件
  css: {
    loaderOptions: {
      sass: {
        implementation: require('sass'),
      }
    }
  }
}
```

这样就配置好了，使用上感受不到差异，不过再也不会遇到 node-sass 安装的各种问题了，性能方面，我在自己的项目里也进行了多次测试对比，从我的测试结果和 Dart Sass 给出的 perf 来看，总体性能和 libsass 相比几乎一致，完全不用担心。

> 转载于：[使用 Dart Sass 代替 Node Sass](https://baiyun.me/replace-node-sass-with-dart-sass)