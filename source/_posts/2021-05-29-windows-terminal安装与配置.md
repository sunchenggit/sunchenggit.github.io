---
title: windows-terminal安装与配置
date: 2021-05-29 13:40:12
tags: terminal
categories: Tool
---

# 安装主软件和插件
1. `windows-terminal`在win10自带的商店里或者[github](https://github.com/microsoft/terminal/releases)中下载
2. `pwsh7` 在[github](https://github.com/PowerShell/PowerShell/releases/tag/v7.1.3)中下载
3. 安装 `scoop` 在上面两个软件安装好后，在`pwsh`里输入下面命令运行
``` shell
iwr -useb get.scoop.sh | iex
```
4. 安装插件
```shell
# 1. 安装 PSReadline 包，该插件可以让命令行很好用，类似 zsh
Install-Module -Name PSReadLine -AllowPrerelease -Force

# 2. 安装 posh-git 包，让你的 git 更好用
Install-Module posh-git -Scope CurrentUser

# 3. 安装 oh-my-posh 包，让你的命令行更酷炫、优雅
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json

# 4. 安装[Nerd Fonts](https://www.nerdfonts.com/)
```

5. 配置pwsh启动项
``` shell
# 1. 在终端中输入(注：code 是安装后vscode后自带的命令)编辑打开的文件
code $PROFILE
# 1-1. 上一步不行的话，可以到目录 `C:\Users\[你的用户文件夹]\Documents\PowerShell` 中新建 `Microsoft.PowerShell_profile.ps1`文件

# 2. 在`Microsoft.PowerShell_profile.ps1`文件输入下面字符后保存当前文件
Invoke-Expression (oh-my-posh --init --shell pwsh --config "$(scoop prefix oh-my-posh)/themes/jandedobbeleer.omp.json")
Import-Module posh-git
Import-Module PSReadLine
```

6. 其他对于`windows terminal`的配置截止`2021-05-29`都是可以在此软件中直接勾选配置的

# 相关文档地址
1. [windows terminal](https://docs.microsoft.com/zh-cn/windows/terminal/)
2. [scoop](https://scoop.sh/)
3. [ohmyposh](https://ohmyposh.dev/)
4. [nerdfonts](https://www.nerdfonts.com/)
5. [powershell](https://docs.microsoft.com/zh-cn/powershell/)