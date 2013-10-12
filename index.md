---
layout: page
title: 客户端技术实验室
tagline: 学习和研究互联网客户端javascript方面的技术
---
{% include JB/setup %}

## 组织的项目库 ##

### 学习研究类 ###

#### advertisement ####

学习和研究广告投放系统的前端技术

GitHub：[https://github.com/clientlab/advertisement](https://github.com/clientlab/advertisement)

#### analytics ####

学习和研究监测分析系统的前端技术

GitHub：[https://github.com/clientlab/analytics](https://github.com/clientlab/analytics)

### 工具类 ###

#### grunt-clientlab-filter ####

执行查找替换指定占位符的GRUNT任务

GitHub：[https://github.com/clientlab/grunt-clientlab-filter](https://github.com/clientlab/grunt-clientlab-filter)

### 参考资源类 ###

#### jekyll ####

当前组织首页使用的博客引擎

GitHub：[https://github.com/mojombo/jekyll](https://github.com/mojombo/jekyll)

#### jekyll-bootstrap ####

当前组织首页使用的博客引擎（使用了bootstrap框架）

GitHub：[https://github.com/plusjade/jekyll-bootstrap](https://github.com/plusjade/jekyll-bootstrap)

#### themes.jekyllbootstrap.com ####

博客引擎的皮肤项目

GitHub：[https://github.com/plusjade/themes.jekyllbootstrap.com](https://github.com/plusjade/themes.jekyllbootstrap.com)

#### theme-tom ####

当前组织首页使用的博客引擎的项目

GitHub：[https://github.com/jekyllbootstrap/theme-tom](https://github.com/jekyllbootstrap/theme-tom)

## 组织的成员 ##

- [周培公](http://www.peigong.tk) - [GitHub](https://github.com/)
- [听歌](https://github.com/TingGe)
- [尘埃](https://github.com/chenai1112)
- [onionyy](https://github.com/onionyy)

## 最新的文章 ##

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
