---
layout: post
category: lessons
title: 使用JSDoc3生成javascript项目的API文档
tagline: 使用JSDoc3生成javascript项目的API文档
tags : [开发工具]
---
{% include JB/setup %}

## JSDoc样式的注释 ##

> 选用JSDoc3作为注释规范，文档生成工具使用grunt-jsdoc，本文不再介绍选型过程和原因。对JSDoc3的深入学习使用，可以参考[入口教程http://usejsdoc.org/index.html](http://usejsdoc.org/index.html)。

JSDoc注释的样式如下例，与单行注释 `//` 和多行注释 `/**/` 不同，类似JAVA的JDoc和PHP的PHPDoc。

    /**
    * JSDoc注释。
    */

## JSDoc的常用标签 ##

### 参数注释 ###

`@param` 用于对函数、类的方法的参数进行注释，是JSDoc中最常用的注释标签。

`@param` 注释必须指定一个参数名，也可以有一个用大括号括起来的参数类型，以及参数的描述信息。参数类型可以是javascript内置的数据类型，如Array、Boolean、Date、Function、Number Object 、String 等，也可以是其他JSDoc所支持的（英文没看太懂，以后用到再认真学习）。

> The parameter type can be a built-in JavaScript type, such as string or Object, or a JSDoc namepath to another symbol in your code. If you have written documentation for the symbol at that namepath, JSDoc will automatically link to the documentation for that symbol. You can also use a type expression to indicate, for example, that a parameter is not nullable or can accept any type; see the @type documentation for details.

下面直接使用[http://usejsdoc.org/tags-param.html](http://usejsdoc.org/tags-param.html)文档中的例子，说明 `@param` 标签中如何使用参数名、参数类型和参数描述信息。

只有参数名的注释：

	/**
	 * @param somebody
	 */
	function sayHello(somebody) {
	    alert('Hello ' + somebody);
	}

包括参数名和参数类型的注释：

	/**
	 * @param {string} somebody
	 */
	function sayHello(somebody) {
	    alert('Hello ' + somebody);
	}

包括参数名、参数类型和参数描述的注释：

	/**
	 * @param {string} somebody Somebody's name.
	 */
	function sayHello(somebody) {
	    alert('Hello ' + somebody);
	}

### 返回值注释 ###

`@return` 说明函数的返回值。例如：

- `@return {Number}`
- `@return {Number} Sum of a and b`
- `@return {Number|Array} Sum of a and b or an array that contains a, b and the sum of a and b.`

> 参见：[http://usejsdoc.org/tags-returns.html](http://usejsdoc.org/tags-returns.html)

### 参考引用注释 ###

` @see` 标签可以指向一个相关的引用。示例如下：

	/**
	 * Both of these will link to the bar function.
	 * @see {@link bar}
	 * @see bar
	 */
	function foo() {}
	
	// Use the inline {@link} tag to include a link within a free-form description.
	/**
	 * @see {@link foo} for further information.
	 * @see {@link http://github.com|GitHub}
	 */
	function bar() {}

### 函数注释常用标签 ###

- 
- `@example`	: 示例代码。


### 类注释 ###

- `@name` ：类名
- `@class` ：类描述
- `@constructor` ：表明这是一个构造函数，非常重要
- `@extends` ：类继承的父类
- `@requires` ： 依赖的类
- `@param` ：参数
- `@example` : 示例代码

### 方法注释 ###
### 属性注释 ###
### 事件注释 ###
### 文件注释 ###

- `@overview	`	：对当前代码文件的描述。
- `@copyright`	：代码的版权信息。
- `@author <name> [<emailAddress>]`	：代码的作者信息。
- `@version`		：当前代码的版本。

## Grunt自动构建的配置 ##

Grunt的安装使用，请参考教程[《Grunt的安装和使用》](http://clientlab.github.io/lessons/2013/10/15/installation-and-use-of-grunt/)。

## 参考资料 ##

- [JSDoc 主页](http://usejsdoc.org/index.html) - [GitHub](https://github.com/jsdoc3/jsdoc)
- [NPM模块主页](https://npmjs.org/package/grunt-jsdoc) - [GitHub](https://github.com/krampstudio/grunt-jsdoc-plugin)
- [使用grunt-jsdoc自动化生成javascirpt文档](http://www.w3c.com.cn/%E4%BD%BF%E7%94%A8grunt-jsdoc%E8%87%AA%E5%8A%A8%E5%8C%96%E7%94%9F%E6%88%90javascirpt%E6%96%87%E6%A1%A3)
- [JSDoc模板docstrap](https://github.com/terryweiss/docstrap)
- [JSDoc模板jsdoc3-bootstrap](https://github.com/alivedise/jsdoc3-bootstrap)
- [JSDoc模板minerva](https://github.com/recursivelymade/minerva)
- [使用jsdoc生成组件API文档—jsdoc实战](http://www.36ria.com/5101)