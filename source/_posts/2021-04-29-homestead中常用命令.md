---
title: homestead中常用命令
date: 2021-04-29 08:21:06
tags: php
categories: Tips
---

# 记录一些 `homestead` 中常用命令
<!--more-->

## `homestead` 中修改 `php` 内存
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

## `homestead` 中安装 `nfs`
1. 在windows系统下终端运行命令 `vagrant plugin install vagrant-winnfsd`
2. 插件安装成功后按回车将弹出的终端窗口关闭
3. 修改 `Homestead\Homestead.yaml` 文件，在`folders`配置下新增 `type: "nfs"`
```yaml
 folders:
     - map: E:/Home
       to: /home/vagrant/code
+      type: "nfs"
```
4. `Homestead` 目录下运行 `vagrant reload --provision` 

## 备份 `homestead` 中 `nginx` 站点配置
1. 在 code 同级目录新增文件 site.sh 内容如下
``` sh
#!/usr/bin/env bash

time=$(date "+%Y%m%d")

if [ ! -d "/home/vagrant/code/sites-enabled/$time" ];then
  mkdir /home/vagrant/code/sites-enabled/$time
else
  sudo rm -rf /home/vagrant/code/sites-enabled/$time && mkdir /home/vagrant/code/sites-enabled/$time
fi

sudo rsync -auvrtzopgP -L  --progress  /etc/nginx/sites-enabled/ /home/vagrant/code/sites-enabled/$time/
```
2. 两种方式运行这个脚本
    * 手动运行：
        在文件所在目录下运行 `sh site.sh`
    * 定时备份
        + 查看cron是否运行 `ps -ef | grep cron`
        + 编辑crontab文件 `sudo crontab -e`
        + 第一次用这个命令，会让你选择文本编辑器，我选的是vim（输入数字选择就是了！）
        + 添加执行命令 `50 16 * * * /home/vagrant/sites.sh`
        + 重启cron来应用这个计划任务 `sudo service cron restart`

3. 恢复备份
    * 进入`nginx` 目录 `cd /etc/nginx/`
    * 删除 `sites-enabled` 目录 `sudo rm -rf sites-enabled/`
    * 复制备份文件到当前目录 `sudo cp -r ~/code/sites-enabled/20210514/ sites-enabled`
    * 重启 `nginx` 服务 `sudo /etc/init.d/nginx restart`
