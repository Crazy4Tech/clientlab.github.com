---
layout: post
category: lessons
title: Grunt的安装和使用
tagline: Grunt的安装和使用
tags : [培训教程, Grunt]
---
{% include JB/setup %}

## 安装Grunt前的准备 ##

> 本教程的内容较少原创，多从其他文档上摘录。详见参考资料部分。

Grunt是一个自动化的项目构建工具。Grunt和Grunt的插件都是通过Node.js的包管理器npm来安装和管理的。

安装Grunt之前，可以在命令行中运行`node -v`查看你的Node.js版本。0.8.0及以上版本的Node.js才能很好的运行Grunt。

如果还没有安装Node.js，需要先从[Node.js(http://nodejs.org/)网站](http://nodejs.org/)下载安装。

> Node.js安装中，以及后继的其他安装中，可能需要系统管理员权限。

## 安装CLI ##

为了方便使用Grunt，你应该在全局范围内安装Grunt的命令行接口(CLI)。

在命令行中，执行如下命令：

	npm install -g grunt-cli

这条命令将会把grunt命令植入到你的系统路径中，这样就允许你从任意目录来运行它(定位到任意目录运行grunt命令)。

## 用一个现有的Grunt项目进行工作 ##

### 安装和执行Grunt ###

假设已经安装好Grunt CLI，并且项目也已经使用一个package.json和一个Gruntfile文件配置好了，那么接下来用Grunt进行工作就非常容易了：

1. 进入到项目的根目录(在命令行面板定位到项目根目录。在windows系统下，也可以进入项目根目录的文件夹后，按Shift+鼠标右键，打开右键菜单，选择“在此处打开命令窗口(W)”)。
2. 运行npm install安装项目相关依赖(插件，Grunt内置任务等依赖)。
3. 使用grunt(命令)运行Grunt。

### 仅安装Grunt ###

使用下面的命令会在全局中安装最新版的Grunt。

	npm install grunt --save-dev -g

### Grunt 0.3说明 ###

如果你从Grunt 0.3升级而来的，请确保先卸载全局的grunt(使用下面的命令)：

	npm uninstall -g grunt

## 准备一个新的Grunt项目 ##

一个标准的配置过程需要给项目添加两个文件：package.json和Gruntfile。

**package.json**：用于存储已经作为npm模块发布的项目元数据(也就是依赖模块)。

**Gruntfile.js**：用于配置或者定义Grunt任务和加载Grunt插件的。

### 快速工作的项目脚手架 ###

#### 安装grunt-init ####

`grunt-init` 是一个用于自动创建项目的脚手架工具。

应该先在命令行中进行全局安装：

	npm install -g grunt-init

这样，会把grunt-init命令植入到你的系统路径，从而允许你在任何目录中都可以运行它。

#### 安装和使用grunt-init模板 ####

把需要的模板放在你的 `~/.grunt-init/` 目录中（在Windows平台是%USERPROFILE%/.grunt-init目录）。

建议使用如下的git clone命令把这个模板克隆到该目录：

	git clone https://github.com/clientlab/grunt-init-gruntfile.git ~/.grunt-init/gruntfile

在Windows平台上稍微有些不方便，但是可以在文件浏览器中输入%USERPROFILE%，定义到该目录下，然后创建相关目录，把文件Copy进去。

最终的文件目录结构，如下：

	.grunt-init/
	.grunt-init/gruntfile/
	.grunt-init/gruntfile/README.md
	.grunt-init/gruntfile/template.js
	.grunt-init/gruntfile/root/

然后进入一个准备开发项目的空目录，按Shift+鼠标右键，打开右键菜单，选择“在此处打开命令窗口(W)”，打开命令行，执行如下程序：

	grunt-init gruntfile

> 请注意，此模板将在当前目录中生成文件，如果你不想覆盖现有文件，一定要使用一个新的空目录。

## 参考资料 ##
- [Node.js 官网(http://nodejs.org)](http://nodejs.org)
- [Grunt 官网](http://www.gruntjs.com) - [[GitHub](https://github.com/gruntjs/)] [[中文文档](http://www.gruntjs.org/)]
- [git工具的安装](http://windows.github.com/)
- [其他常用 grunt-init 模板](https://github.com/gruntjs/)
- [grunt-init 自定义模板开发](http://www.gruntjs.org/article/project_scaffolding.html)