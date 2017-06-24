---
title: sublime
date: 2017-06-24 07:22:09
tags: sublime
---


## 安装 [sublime](http://www.sublimetext.com/docs) **package control**包管理工具
调出命令行（Ctrl + `）导入Sublime text 3的Package Control的安装代码

`import urllib2,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')`
### 另外提供Sublime text 2的Package Control的安装代码

`import urllib2,os,hashlib; h = '7183a2d3e96f11eeadd761d777e62404' + 'e330c659d4bb41d3bdf022e94cab3cd0'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); by = urllib2.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')`

## 常用包安装
* Boxy Theme 主题相关
* DocBlockr  注释文档
* Emmet      前端

## 开启 Vim 模式
在菜单栏中： Preferences -> Setting - User 即可打开配置文件进行编辑，将 ignored_packages 项的[]里面内容清空："ignored_packages": []
## 常用快捷键
* Ctrl + Shift + p 打开命令窗口
* Ctrl + k / Ctrl + b  打开/关闭左侧工程树
* Ctrl + r 跳转当前页面函数名部分
* F11 全屏
* Alt + Shift + <num> 分屏
* Ctrl + Tab 打开文件之间跳转

## setting 文件配置
	"color_scheme": "Packages/Color Scheme - Default/Monokai.tmTheme",
	"font_size": 13,
	"ignored_packages":
	[
	],
	"tab_size": 4,
	"translate_tabs_to_spaces": true,
	"theme": "Boxy Monokai.sublime-theme",

