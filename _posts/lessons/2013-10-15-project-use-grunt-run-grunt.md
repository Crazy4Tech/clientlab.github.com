---
layout: post
category: lessons
title: 使用grunt-run-grunt插件组织团队的开发
tagline: 使用grunt-run-grunt插件组织团队的开发
tags : [培训教程, Grunt插件, 项目组织]
---
{% include JB/setup %}

## 项目组织的需求 ##

在组织项目的开发工作时，如果构建方案选型的是Grunt，那么常常有以下几个需求：

1. Gruntfile文件虽然项目的复杂性增加，变的越来越庞大。为了便于开发团队的分工协作，需要在某种程度上分拆Gruntfile，让不同的团队、不同的开发者，或者开发者不同时间的关注点，关注不同的部分。
2. 把Gruntfile拆分成不同的文件后，有统一的入口能够执行整体的构建。分拆后的Gruntfile又要能够不依赖于其他部分的独立构建，确保团队分工的互不干扰。
3. 因为从属于同一个项目，所以package.json和node_modules要能够共用。确保每一部分的开发者，只需要关注Gruntfile的编写，不需要关注有全局共性的package.json和node_modules。

不同的团队、 不同的项目都有不同的细化需求，都会各自选择不同的解决方案。

## Gruntfile的分拆方案 ##

### Gruntfile文件内的逻辑分组 ###

使用任务的目标名称，在逻辑上分组构建任务。这是大多数项目最初会用到的方法，如[grunt中文文档项目(https://github.com/basestyle/grunt-cn)](https://github.com/basestyle/grunt-cn)。

在传递给grunt.initConfig方法的对象中，使用如下类似的不同任务目标名称区分webapp和pc两类任务：

	jshint:{
		webapp: ['app/www/js/main.js'],
		pc: ['js/chart.js','js/common.js','js/demand.js','js/dialog.js','js/formbeautify.js','js/jquery.autopagination.js',
			'js/jquery.cascadeselect.js','js/jquery.datepicker.js','js/jquery.formvalid.js','js/jquery.memberinput.js',
			'js/jquery.multiupload.js','js/jquery.tabs.js','js/pmstation.js','js/project.js','js/setting.js','js/tasktable.js','js/work.js']
	},

在自定义的别名任务中，把两类任务分组成webapp和pc两个单任务：

	grunt.registerTask('webapp', ['htmlhint:webapp','jshint:webapp','uglify:webapp','cssmin:webapp','copy:webapp','replace:webapp']);
	grunt.registerTask('pc', ['jshint:pc','uglify:pc','cssmin:pc','copy:pc','replace:pc']);

如果两类任务调用的任务都相同，也可以使用动态别名任务的方法来处理。

代码示例如下：

	grunt.registerTask('build', 'Run all my build tasks.', function(n) {
	  if (n == null) {
	    grunt.warn('Build num must be specified, like build:001.');
	  }
	  grunt.task.run('foo:' + n, 'bar:' + n, 'baz:' + n);
	});
参见Grunt文档的《常见问题-"动态"别名任务》:

- [中文文档(http://www.gruntjs.org/article/frequently_asked_questions.html)](http://www.gruntjs.org/article/frequently_asked_questions.html)
- [英文文档(http://gruntjs.com/frequently-asked-questions)](http://gruntjs.com/frequently-asked-questions)

### Grunt配置编程处理在不同的文件中 ###

将配置对象拆分出来，然后在Gruntfile.js中require进来，再将这些不同任务的对象组合成一个对象传递给grunt.initConfig就行。这是在我提出的问题（[有没有分拆Gruntfile.js的方案？(https://github.com/basestyle/grunt-cn/issues/34)](https://github.com/basestyle/grunt-cn/issues/34)）后，[TooBug](http://www.toobug.net)[[GitHub](https://github.com/TooBug)]和[Vincent Hou](https://github.com/qivhou)提出的解决方案。

因为没有进一步展开，所以没有示例代码。

### 使用自定义任务把构建任务分解在不同的文件中 ###

我在知乎上提出问题《[有什么方案可以把较为庞大的gruntfile分拆？(http://www.zhihu.com/question/21766711)](http://www.zhihu.com/question/21766711)》,[墨磊](http://morlay.tla42.org/)[[GitHub](https://github.com/morlay)]所提出的解决方案，基本上就是使用自定义任务把构建任务分解在不同的文件中的。

比如，在[gruntjs.com(https://github.com/gruntjs/gruntjs.com)](https://github.com/gruntjs/gruntjs.com)项目中，也是通过把blog、docs等任务从Gruntfile中分拆出来的。

代码示例如下：

  // Load local tasks
  grunt.loadTasks('tasks'); // getWiki, docs tasks
  
  grunt.registerTask('build', ['clean', 'copy', 'jade', 'docs', 'blog', 'plugins', 'concat']);

上例中的docs、blog任务就是放在tasks目录下，使用grunt.loadTasks方法统一加载的。

## 选择grunt-run-grunt插件 ##

前文的所述的几个方案，用于分拆Gruntfile虽然很不错，但是并不能解决最初提出的后两个需求：

- 分拆后的Gruntfile，能够不依赖于其他部分的独立构建。
- package.json和node_modules要能够共用。

## 项目的组织方案 ##