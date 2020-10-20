---
title: sublime-text3
date: 2020-10-19 17:35:19
tags:
---

# 下载
[官网](https://www.sublimetext.com/)  
*tips：也可以联系我获取安装包*

# 安装
没啥好说的直接下一步，下一步一直下去就好了  

# 注册
有能力的可以去购买授权  
*tips：也可以联系我获取试用版*

# 安装插件
1. 安装 package control 官方提供的插件管理系统
	* 首先在[官网](https://packagecontrol.io/installation)上获取到对应版本的代码(3 代版本代码如下)
	``` 
		import urllib.request,os,hashlib; h = '6f4c264a24d933ce70df5dedcf1dcaee' + 'ebe013ee18cced0ef93d5f746d80ef60'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
	```
	* 然后打开软件依据，View-Show Console 打开命令行(快捷键 catrl+`)，输入上面代码回车，等待安装
	* 安装好了之后在，Preferences 菜单下会有一个 package control 选项说明你已经安装成功了
	* 点击这个 Preferences-package control 在跳出的框里选择 install package 
	* 在弹出的框里输入自己需要的插件名称，搜索的结果里直接点击就可安装

2. 前端常用插件
	* Emmet --前端神器不解释
	* chineseLocalizations --语言包，汉化插件
	* AutoFileName --自动获取文件名
	* Bracket Highlighter --括号匹配，高亮标记，便于查看起始和结束标记
	* DocBlockr --生成优美的代码注释
	* HTML-CSS-JS Prettify --格式化代码（ctrl+shift+h），需要安装 node，如果node默认安装在c盘就不用管，否则要修改node路径
	* jQuery --快捷输入jQ函数
	* JavaScript Completions --支持javascript原生语法提示
	* CSS Extended Completions  --关联CSS文件，智能提示css文件中的类名
	* Scss --支持scss文件
	* view in browser --通过默认浏览器打开文件
	* ColorHighlighter -- 颜色高亮
	* Trailing spaces --检测代码中多余的空格，配置好可以一键清除。快捷键配置：在Preferences / Key Bindings – User加上代码（数组内）{ "keys": ["ctrl+shift+t"], "command": "delete_trailing_spaces" }
	* SidebarEnhancements --扩展文件右键功能
	* caniuse_local  --检测html，css之类的语法兼容性
	* Pretty JSON  --json 美化
	* ConvertToUTF8  --文字编码转换
	* Terminal --在当前文件里打开控制台
	* [Side​Bar​Enhancements](https://github.com/52fisher/SideBarEnhancements)  --左侧增强
	* ColorSublime	--主体管理插件
	* Agila Theme  --主题
	* A File Icon --文件类型图标
3. 最后附上常用配置项
	``` JSON
		{
			"color_scheme": "Packages/Color Scheme - Default/Monokai.sublime-color-scheme",
			"ignored_packages":
			[
				"Vintage"
			],
			"theme": "Agila Monokai.sublime-theme",
			"font_face": "Fira Code",
		    "font_size": 12,
		    "word_wrap": "true",
		    "line_padding_top": 2,
		    "line_padding_bottom": 2,
		}
	```