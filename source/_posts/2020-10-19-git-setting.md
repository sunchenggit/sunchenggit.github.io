---
title: git-setting
date: 2020-10-19 17:34:44
tags:
---

# 基本设置

1. 初始化用户名、邮箱以及颜色
```
git config --global user.name "suncheng"
git config --global user.email "157600408@qq.com"
git config --global color.ui true
```

2. 生成ssh密钥
```
ssh-keygen -t rsa -C "157600408@qq.com" 
```

# 常用命令
1. 初始化，添加修改，提交修改，推到服务器
```
git init
git add .
git commit -m "描述"
git push
```

2. 拉取线上特定分支到本地
```
git checkout -b 本地分支名 origin/线上分支名
```

3. 推送本地分支到线上
```
git push --set-upstream origin 本地分支名
```

4. 换行符转换的问题
    * 设置自动转换选项autocrlf
    * $ git config --local core.autocrlf true | input | false 
        1. true 表示开启自动转换，迁入时将文件换行风格转换成Unix风格，迁出时根据本地系统确定是否转换成CRLF
        2. input 表示迁入的时候将换行风格转换成Unix风格，迁出时不做处理。
        3. false 表示迁入迁出都不对换行风格进行处理
```
    git config --local core.autocrlf input
```

# mac下密钥位置
> open ~/.ssh
