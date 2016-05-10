---
title: 使用github pages和hexo建站遇到的坑
date: 2016-05-10 14:14:28
toc: true
categories:
- 随笔
tags:
- HEXO
- GitHub Pages
- 搭建Blog
- 教程
---

新换了工作之后， 一时比较清闲， ~~再次~~下定决心要开始写博客提升自己， 那么这就是本博客的第一篇了， 记录一些在使用Github-Pages和HXEO建站时遇到的问题。

鉴于网上已经有一百万篇关于Github-Pages和HXEO建站的教程， 本文不会继续拾人牙慧重复记录整个建站的流程， 而是从我个人的角度记录一些建站过程中遇到的“坑”和一些~~菜鸡的~~思考
<!--more-->
## 什么是Github-Pages

- Github-Pages只是一个普通的Github Reponsitory， 所有Github Reponsitory具备的功能， Github-Pages也是一样的。
- Github-Pages是一个稍微特殊的Github Reponsitory， 他的命名必须符合默认的约定 -- *[github-user-name]*.github.io， 他的master分支可以理解为一个静态网站托管空间， 可以通过*[github-user-name]*.github.io从外部访问此网站。
- Github-Pages一般被用作项目或组织的主页， 用于介绍本项目/组织， 也可以用来搭建一个个人博客。

## 什么是HEXO

HEXO是一个基于nodejs的静态网站生成器， 按照官方的说法， HEXO is a powerful blog framework powered by Node.js.

## Github-Pages和HEXO是什么关系

并没有半毛钱的关系。 对于静态网站生成和Github-Pages毫无经验的我， 看到网上推荐Github-Pages + HEXO自建bolg， 于是就跑去官网看教程， Github-Pages的教程非常简单易懂， 而看到HEXO官方教程的时候我就懵逼了。。原因就是这一句

> Once Hexo is installed, run the following commands to initialise Hexo in the target &lt;folder&gt;.

这个`target <folder>`是个什么鬼？ 难道是对应Github-Pages的根目录么？ Init生成的这一堆文件都是什么鬼？ 使用了nodejs， 难道Github-Pages提供了node环境么？
这一串的懵逼终于在看完文档之后得到了解答， 这个`target <folder>`其实只是HEXO的工作目录， HEXO使用nodejs处理这个目录下的文件， 并通过generate生成最终的静态网站， generate出来的内容才是最终需要push到Github的内容。 所以本地Clone的Github-Pages仓库目录， 和HEXO的工作目录其实完全没有关系， HEXO提供了deploy方法自动向某个Github仓库， 但其实我们手动拷贝generate生成的内容， 再push到Github也是一样的效果。

对于用惯了Git的人来说， 肯定希望把HEXO的工作目录也通过Git管理起来， 我个人采取的方案是在Github-Pages的Repo里新建了一个Workspace分支， 用来保存所有的HEXO工作文件， 当然令建一个Repo也是完全可以的。