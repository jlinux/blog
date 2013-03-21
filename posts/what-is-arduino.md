---
title: Arduino简单介绍
date: '2013-03-21'
description:Arduino简单介绍
categories:
- arduino
- 电子积木
tags:
-	arduino
-	电子积木
---



”Arduino 是一款便捷灵活、方便上手的开源电子原型平台，包含硬件（各种型号的arduino板）和软件（arduino IDE)。它适用于艺术家、设计师、爱好者和对于“互动”有兴趣的朋友们。“ ----摘自 Arduino官网。

个人对于Arduino更喜欢的一个名称是：电子积木。通过统一的规范、协议，有很强大的扩展组件，通过简单的连线和组合，就初步实现硬件设备的组合，再通过类C的语言编程，基本就完成了属于自己的电子互动作品。所以它适合于艺术家、设计师、爱好者和对于“互动”有兴趣的朋友们。

Arduino实际上还是单片机的一种，但是他通过开源的方式，类C的高级语言的开发，大大降低了电子的入门门槛；也拉开了开源硬件的大幕。

单从单片机，解决方案有很多，Arduino只是其中一种，而且Arduino也有自己的优缺点：

优点：

*	开源硬件，社区强大，解决方案众多
*	组件丰富
*	类C的高级语言开发，相对于直接用C和汇编，学习和开发成本更低
*	作为艺术或者原型开发，速度很快

缺点：

*	价格偏贵，特别是组件，如果直接购买而不是自己做，那么价格还是偏贵
*	因为用了高级语言，最终编译成的二进制包还是偏大，性能偏弱
*	组件多，但是比较固化，对个性需求满足不够

因为这些特性，所以Arduino适合学习入门、原型开发、艺术、设计师、爱好者等等，如果需要把你做出来的装置批量生产，需要重新花电路图，去掉一些不需要的功能，并进行微型化、集成化、外观设计，最终做大规模的工业化生产。比较好的地方是，因为开源，只要不适用Arduino这个商标，你可以直接使用Arduino的电路图进行定制，这样无需额外开销，你就可以用到成熟、稳定的解决方案。

Arduino本身基于微处理控制器(AVR系列控制器)，它定义了开源的电路图，事先烧入了bootloader，通过板载的USB接口，就可以写入你自己编写的程序。通过固定规范、标准接口、程序编写的定义，完成了一次封装，对普通用户屏蔽了很多实现细节。

Arduino的[标准产品和扩展](http://arduino.cc/en/Main/Products)可以在Arduino官网找到，根据用途不一样，有很多型号可供选择，在[维基百科Arduino](http://zh.wikipedia.org/wiki/Arduino)，可以找到各个主板型号的具体说明。

如果是学习入门，普遍性的选择是Uno或者Mega 2560；如果有固定的实现目标，那么根据其参数选择即可。

>从硬件层面，想要了解Arduino相关主板、扩展组件、套件的，最好的办法是直接去逛淘宝店；种类齐全，说明详细，有些店还带技术指导（特别是小店）。

所有Arduino主板中，最能体现其多样性和多用途的我觉得是LilyPad，一种微型用于可穿戴设备的Arduino主板，这种主板，配套有微型LED组件，导电缝纫线、蜂鸣器、按钮、无线传输模块等等。这些模块，还可以水洗。LilyPad是服装设计、互动艺术和电子电路的跨界结晶。

![LilyPad](http://img02.taobaocdn.com/bao/uploaded/i6/T1K18IXj4nXXaWxxo._082436.jpg_310x310.jpg)
![LilyPad LED Micro](http://img01.taobaocdn.com/bao/uploaded/i1/T1gr0zXl0qXXXdMFA0_034135.jpg_310x310.jpg)
![导电缝纫线](http://img03.taobaocdn.com/bao/uploaded/i7/T1LY8zXcRpXXarvqs2_043124.jpg_310x310.jpg)


作为爱好者，或者有兴趣的朋友，想要入门，可以考虑购买一下的套件：

初级入门购买Arduino的[入门套件](http://item.taobao.com/item.htm?id=13626470565)。

如果觉得不过瘾，还可以购买类似于[自动寻路小车的套件](http://item.taobao.com/item.htm?id=7424526051)。

高富帅，不差钱，可以购买[人形机器人](http://item.taobao.com/item.htm?id=19188632823)。


和Arduino以及开源硬件相关的产品在国内比较大的销售厂商：[DFRobot官方旗舰店](http://dfrobot.taobao.com/) 以及 [奥松机器人](http://robotbase.taobao.com/)，这两家在淘宝上刚好一南一北。还有一家[Seeed Studio](http://www.seeedstudio.com/)。 这三家的质量和信誉都有保证。（这三家是我自己知道的）



>Arduino如何入门，在网上有很多教材，特别推荐同事Misa写的[机器人入门教材](https://github.com/MisaZhu/Robotics/wiki)


>参考网站
>
*	[Arduino百度Wiki](http://baike.baidu.com/view/1268436.htm)
*	[Arduino维基百科](http://zh.wikipedia.org/wiki/Arduino)
*	[Misa机器人相关教材](https://github.com/MisaZhu/Robotics/wiki/04.01%E3%80%81Arduino%E5%9F%BA%E7%A1%80%E7%9F%A5%E8%AF%86)
*	[Arduino中文论坛](http://www.arduino.cn/)


>本文带有很多淘宝连接，这是因为我来之阿里。