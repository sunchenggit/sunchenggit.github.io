---
title: homestead中常用命令
date: 2021-04-29 08:21:06
tags: php
categories: Tips
---

# 记录一些homestead中常用命令
<!--more-->

## homestead中修改php内存
``` shell
# 查看php内存相关信息
php -i | grep memor
# 找到php配置所在目录
php -i | grep php.ini
# 编辑配置文件
sudo vim /etc/php/7.3/cli/php.ini
# 找导对应行
memory_limit => 512M
# 修改为
memory_limit => -1
# 重启php服务
sudo /etc/init.d/php7.3-fpm reload
```