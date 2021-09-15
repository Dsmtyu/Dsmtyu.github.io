---
layout: post
read_time: true
show_date: true
title:  SublimeText3的使用
date:   2021-09-15 18:21 -0600
description: 冒泡排序算法
img: /posts/20210915/background.jpeg
tags: [Sublime Text3]
author: Albert
---
# Sublime Text3的使用
[__Sublime Text__](https://baike.baidu.com/item/Sublime%20Text) 被称为是程序员必备代码神器，是一个跨平台的编辑器，支持20多种语言编写，自带Python编辑插件。这款神器的优点有很多，这里不一一赘述。  
由于Sublime Text是跨平台编辑器，可以在Windows,macOS,Linux系统运行，这里我们只说Windows 10系统上的。

首先，我们先到[__Sublime Text3__](https://www.sublimetext.com/3)的官网下载对应你系统的版本，右边的 [portable version](https://download.sublimetext.com/Sublime%20Text%20Build%203211%20x64.zip) 是 __.zip__ 便携版本，可直接运行。这里演示 [__.exe__](https://download.sublimetext.com/Sublime%20Text%20Build%203211%20x64%20Setup.exe)  
![image](../assets/img/posts/20210915/exe.jpg)
双击运行，按照提示安装即可。  
安装之后进去，按下 __Crtl+~__ 调出命令输入以下代码
```python
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read()) 
```
就可以安装Package Control组件，安装插件了。

Sublime Text3汉化：
    按下 __Crtl+Shift+P__ 输入install回车，看到已经选中install packag后，再输入localize回车，就会安装汉化插件。