---
title: 语音识别
date: '2013-03-17'
description:
categories:
- 2013
- 智能
- 技术储备
- 语音
tags:
- raspberry pi
- 语音 识别
---

{:toc}

#	为什么选择树莓派

选择在树莓派上实现语音控制，主要是三个考虑：

*	成本，相对于硬件解决方案，软件解决方案更廉价；而且从周边的解决方案，树莓派的性价比也比较好
*	扩展性，通过标准的USB接口，我很容易选择PC的扩展方案，廉价，易开发
*	自己更了解PC下的开发

如果没有这些考虑，有更轻松的解决方案: DFRobot Arduino Smart Home kit智能家居语音识别初级套件http://wiki.dfrobot.com.cn/index.php?title=Smart_Home_kit_for_Arduino(SKU:KIT0005)



##	前期技术调研
最开始是选择Julius4作为参考，最后没有成熟的中文文档可以参考，只好放弃。Julius4是日本人开发的一个语音识别引擎，理论上比较适合中文

最后选择的语音识别引擎是：Sphinx。Sphinx的开发社区强大，文章众多，而且看维基百科，居然是[李开复](http://zh.wikipedia.org/wiki/%E6%9D%8E%E5%BC%80%E5%A4%8D)写的第一个版本。


#	在树莓派上实现语音识别



##	一、在淘宝上为树莓派购买了Microphone和USB语音声卡

*	[Microphone](http://item.taobao.com/item.htm?id=16970239607)

*	[USB语音声卡](http://item.taobao.com/item.htm?id=16475229725) 老板还忘记发这个了，幸好从@铁轮 那里弄了一个

##	二、测试录音功能

	sudo modprobe snd_bcm2835 //载入声卡驱动
	arecord -d 10 -D plughw:1,0 test.wav //测试录音
	aplay test.wav //播放录音
	
实际测试音效不是很好，怀疑是声卡的原因


##	三、根据参考过的文章，完成语音识别系统的安装

根据这个博客[Sphinx武林秘籍(上)](http://www.cnblogs.com/huanghuang/archive/2011/07/14/2106579.html)安装Sphinx以及语言模型和声学模型。

从[这里](http://sourceforge.net/projects/cmusphinx/files/)下载以下文件:

*	sphinxbase-0.8.tar.gz
*	pocketsphinx-0.8.tar.gz
*	zh_broadcastnews_16k_ptm256_8000.tar.bz2
*	zh_broadcastnews_64000_utf8.DMP
*	zh_broadcastnews_utf8.dic	

根据这个Blog的介绍，完成了安装和测试，根据其结果，说是准确率非常低。

后续准备根据这个Blog进行优化[Sphinx语音识别学习记录 （四）-小范围语音中文识别](http://www.cnblogs.com/yin52133/archive/2012/07/12/2588201.html)

##	四、解决命令输入准确率的问题

根据两篇博客：

*	[Sphinx语音识别学习记录 （四）-小范围语音中文识别](http://www.cnblogs.com/yin52133/archive/2012/07/12/2588201.html)
*	[Android平台使用PocketSphinx做离线语音识别，小范围语音99%识别率](http://zuoshu.iteye.com/blog/1463867)


>丢脸的是：实在没有看懂反馈的信息，不知道准确率是如何体现的，准备做一个界面调用一下试试

##	通过python或者Go调用



##	要解决的问题



##	做过的其他操作

	export ALSADEV="plughw:1,0" // 设置系统的环境变量以使用麦克风

	sudo apt-get install julius-voxforge //语音合成软件





***

>参考过的文章：
>

*	[Speech Recognition using the Raspberry Pi](http://www.aonsquared.co.uk/raspi_voice_control) 国内很多文章从这里翻译，但是不注明出处，无耻
*	[PocketSphinx语音识别系统的编程](http://jishu521.com/post/zouoxy09/7978108.html)
*	[pocketsphinx开发文档](http://cmusphinx.sourceforge.net/api/pocketsphinx/)
*	[PocketSphinx语音识别系统语言模型的锻炼和声学模型的改进](http://www.myexception.cn/mobile/700769.html)
*	[cmusphinx系列](http://www.cnblogs.com/yin52133/tag/cmusphinx/)
*	[Sphinx武林秘籍(上)](http://www.cnblogs.com/huanghuang/archive/2011/07/14/2106579.html)
*	[语音识别](http://zh.wikipedia.org/wiki/%E8%AF%AD%E9%9F%B3%E8%AF%86%E5%88%AB)
*	[PocketSphinx语音识别系统语言模型的训练和声学模型的改进](http://www.kaifajie.cn/kaifa_qita/5933.html)
*	[Raspberry Pi实作–语音识别控制Maplin USB机械手臂](http://www.it165.net/embed/html/201207/2076.html) 抄袭前面说到的文章
*	[如何使用Julius搭建一个语音识别引擎？](http://blog.csdn.net/habout632/article/details/8632621)
*	[基于Julius的机器人语音识别系统构建](http://www.21ic.com/app/control/201108/91819_2.htm)







