# 基于 `HEXO` 构建的静态博客

## 简介
不定期更新一些软件配置、生活琐事、技术文章、学习笔记之类的文章，希望自己能坚持下去。

## 使用方法
+ 克隆当前创库 -> cd <文件夹名>
+ 安装依赖：`npm install`
+ 本地服务：`npm run server`
+ 清理项目：`hexo clean`
+ 生成静态文件：`hexo g`
+ 部署到线上：`hexo d`

## 博客技术栈
+ 服务器托管：`github pages`
+ 域名：`github pages` 的默认域名
+ 博客主体：`hexo`
+ 部署插件: `hexo-deployer-git`

## 持续化构建
+ travis