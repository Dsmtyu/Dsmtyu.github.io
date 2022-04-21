---
layout: post
title:  Sublime Text3的使用
date:   2021-09-15
header-img: img/posts/20210915/background.jpeg
tags:
    - Sublime Text3
author: Albert
catalog: true
---
## Sublime Text3的使用
[Sublime Text](https://baike.baidu.com/item/Sublime%20Text) 被称为是程序员必备代码神器，是一个跨平台的编辑器，支持20多种语言编写，自带Python编辑插件。这款神器的优点有很多，这里不一一赘述。  
由于Sublime Text是跨平台编辑器，可以在Windows,macOS,Linux系统运行，这里我们只说Windows 10系统上的。

首先，我们先到[Sublime Text3](https://www.sublimetext.com/3)的官网下载对应你系统的版本，右边的 [portable version](https://download.sublimetext.com/Sublime%20Text%20Build%203211%20x64.zip) 是 __.zip__ 便携版本，可直接运行。这里演示 [__.exe__](https://download.sublimetext.com/Sublime%20Text%20Build%203211%20x64%20Setup.exe)  
![](/img/posts/20210915/exe.jpg)
双击运行，按照提示安装即可。  
安装之后进去，按下 __Crtl+~__ 调出命令输入以下代码
```python
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
```
就可以安装Package Control组件，安装插件了。

### Sublime Text3汉化：
按下 __Crtl+Shift+P__ 输入install回车，看到已经选中install packag后，再输入localize回车，就会安装汉化插件。

### sublime Text3配置C/C++
首先下载MinGW的C语言内核，这里提供一种[MinGW](https://sourceforge.net/projects/mingw/)下载地址。下载完成后按照提示安装，配置环境变量，重启。
进入Sublime Text，Tools(工具)-->编译系统-->新建编译系统。如图所示。
![](/img/posts/20211003/2021-10-03.jpg)
输入如下代码(C.sublime-build)。
```json
// windows环境
{

	"working_dir": "$file_path",

	"cmd": "gcc -Wall \"$file_name\" -o \"$file_base_name\"",

	"file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",

	"selector": "source.c",

	"variants":

	[

	{

	     "name": "Run",

	     "shell_cmd": "gcc -Wall \"$file\" -o \"$file_base_name\" && start cmd /c \"${file_path}/${file_base_name} & pause\""

	}

	]

}

```
![](img/posts/20211003/2021-10-03%20113246.jpg)
C++配置如下(C++.sublime-build)。
```json
// windows系统
{
	"cmd": ["g++", "${file}", "-o", "${file_path}/${file_base_name}"],
	"file_regex": "^(..[^:]*):([0-9]+):?([0-9]+)?:? (.*)$",
	"working_dir": "${file_path}",
	"selector": "source.c, source.c++",

	"variants":
	[
		{
			"name": "Run",
			"cmd": ["cmd", "/c", "g++", "${file}", "-o", "${file_path}/${file_base_name}", "&&", "cmd", "/c", "${file_path}/${file_base_name}"]
		},
		{
			"name": "RunInCommand",
			"cmd": ["cmd", "/c", "g++", "${file}", "-o", "${file_path}/${file_base_name}", "&&", "start", "cmd", "/c", "${file_path}/${file_base_name} & pause"]
		}
	]
}
```
现在C/C++已经可以运行了。
