---
title: 完成静态Blog的搭建
date: '2013-03-15'
description: 从rubyonrails移植到静态Blog引擎Gor
categories:
---

###选择错误

之前在树莓派上搭建站点时，因为觉得rubyonrails搭建比较迅速，于是就选择了rubyonrails。

这个选择后面看来是一个错误，因为树莓派本身的性能偏低，运行rubyonrails还是比较吃力，当是访问这个网站，页面展示的时间需要10秒钟以上。

这个并不是rubyonrails的错误，是我选择的错误。

###重新选择

决定更换网站底层时，就开始选型，最后发现[hugozhu](http://hugozhu.myalert.info/)网站采用的Gor，其效果非常好。调查以后，决定按照他的方案来搭建整个网站。

PS。gor 是使用golang实现的类Ruhoh静态博客引擎(Ruhoh like),基本兼容ruhoh 1.x规范。

从这次的选择来看，为树莓派编程，还是要选取一个高级、速度快、占用系统资源小的语言，这样看来Go就很合适。

只不过对于我来说，我需要重新了解一门新的语言。


###写Blog的好习惯

在这件事情上，充分证明了写Blog记录技术历程的好处，可以给自己一个记录，可以给别人一个帮助。

看我自己能坚持多久。