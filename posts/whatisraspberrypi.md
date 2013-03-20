---
title: 树莓派（raspberry pi）与互联网程序员
date: '2013-03-20'
description:介绍什么是树莓派
categories:
- raspberry pi
- 树莓派
- 接受
tags:
- raspberry pi
- 树莓派
---

本来想写一篇介绍树莓派的文章，搜索了一下，网上已经有太多，从入门的到精通的，所以放弃，最后只是想介绍一下自己接触树莓派的简单经历和想法。然后放一些我自己看过的文章给大家。

#	化学反应（互联网程序员与硬件）

>因为是历程所以没有实现细节


首次知道树莓派是通过flipboard看新闻，当是知道了卡片计算机，而且很火。 后面再次接触到树莓派是[一粟](http://go.myalert.info/)的网站，发现这种轻量级的网站解决方案，很可爱。

仔细收集相关信息以后，决定买一套，用它来驱动我的智能小车，化学反应从这里就开始了。

从就业以来，玩的都是网站应用程序，了解的也是这方面的知识：HTTP/HTML/CSS/Socket/JAVA/linux等等，对于硬件不是那么熟悉。但树莓派系统是linux，几乎可以安装一切linux已有的软件，自带网络口，提供USB端口，当前PC成熟的硬件，很容易用到树莓派上；而树莓派还提供GPIO引脚，可以控制其他单片机设备，还可以和[Arduino](http://zh.wikipedia.org/wiki/Arduino)协作。

之前用Arduino做过一个智能小车，有了一定的基础，知道直流电机驱动板如何工作，信号量应该是什么样的，而我需要做的是通过GPIO口来控制小车。

很快，我就画出了简单的示意图，用我非常熟悉的解决方案：
![解决方案](http://ww4.sinaimg.cn/mw690/543ff35dgw1e2w66fc6gjj.jpg)

##	驱动小车

驱动小车是通过GPIO口连接直流点击驱动板，通过高低电平信号来控制，而小车的驱动很快就写好了，我用ruby写了一个Car类，来控制小车的前进后退。

	require 'pi_piper' //网上提供的Ruby包，用来控制树莓派的GPIO口，如果你用python，树莓派系统中自带
	
	class Car
	  #attr_reader :ea,:i2,:i1,:eb,:i4,:i3
	  def initialize (options)
	    #左边轮子的控制按钮
	    @ea = PiPiper::Pin.new(:pin => options[:ea], :direction => :out)
	    @i2 = PiPiper::Pin.new(:pin => options[:i2], :direction => :out)
	    @i1 = PiPiper::Pin.new(:pin => options[:i1], :direction => :out)
	    #右边轮子的控制按钮
	    @eb = PiPiper::Pin.new(:pin => options[:eb], :direction => :out)
	    @i4 = PiPiper::Pin.new(:pin => options[:i4], :direction => :out)
	    @i3 = PiPiper::Pin.new(:pin => options[:i3], :direction => :out)
	
	    @ea.on
	    @eb.on
	  end
	  #后退
	  def goback
	    @i2.off
	    @i1.on
	    @i4.on
	    @i3.off
	  end
	  #前进
	  def goahead
	    @i2.on
	    @i1.off
	    @i4.off
	    @i3.on
	  end
	
	  #右转
	  def goright
	    @i2.off
	    @i1.on
	    @i4.off
	    @i3.on
	  end
	  #左转
	  def goleft
	    @i2.on
	    @i1.off
	    @i4.on
	    @i3.off
	  end
	  #停止
	  def stop
	    @i2.off
	    @i1.off
	    @i4.off
	    @i3.off
	  end
	
	end

当写完这个类，基本上驱动小车已经没有任何难度了，剩下的就是控制部分，也是最花时间的部分。

##	控制服务解决方案

*	远程要遥控选择的是无线，买了个一个TL-WN725N的无线网卡解决了无线连接的问题
*	远程控制的程序部分是在树莓派上运行了一个WebSocket的服务器

		require "./car.rb"
		require 'em-websocket'//提供WebSocket服务的包
		require 'pi_piper'
		car = Car.new(:ea=>18,:i2=>15,:i1=>14,:eb=>4,:i4=>3,:i3=>2)
		EM.run {
		  EM::WebSocket.run(:host => "0.0.0.0", :port => 8080) do |ws|
		    ws.onopen { |handshake|
		      puts "WebSocket connection open"
		      # Access properties on the EM::WebSocket::Handshake object, e.g.
		      # path, query_string, origin, headers
	
	      # Publish message to the client
	      ws.send "Welcome,the client has successful connected."
	    }
	
	    ws.onclose {
	        car.stop
	        puts "Connection closed" }
	
	    ws.onmessage { |msg|
	      case msg
	        when "go"
	         car.goahead
	        when "right"
	         car.goright
	        when "left"
	         car.goleft
	        when "back"
	         car.goback
	        else
	         car.stop
	        end
	
	      puts "Recieved message: #{msg}"
	      ws.send "server: #{msg} recieved!"
	    }
		  end
		}

##	遥控客户端

这个没有什么疑问，直接使用Android手机，所需要做的就是开发客户端界面，并通过Websocket发送控制命令。

后续不过瘾，又弄了一个鸡腿（WII的控制手柄）通过蓝牙来控制。

##	化学反应

整个解决方案的速度，远远超过的预期，成熟的软件体系和硬件，让所有解决方案事半功倍，而个人只需要做的是发挥创意。

这就是我和树莓派的第一次亲密接触。


#	网上的一些文章

*	[树莓派Raspberry Pi上手报告](http://www.leiphone.com/raspberry-pi-hands-on.html)
*	[35美元电脑Raspberry Pi的OS是如何诞生的？](http://www.cnbeta.com/articles/230243.htm)
*	[Raspberry Pi（树莓派）试用小记](http://www.cnblogs.com/ma6174/archive/2013/01/25/2875617.html)
*	[使用树莓派制作的远程开门器](http://www.cnblogs.com/guanhe/archive/2012/12/25/2832982.html)
*	[树莓派](http://zh.wikipedia.org/wiki/%E6%A0%91%E8%8E%93%E6%B4%BE)
*	[乐高加上树莓派等于廉价超级计算机？](http://www.inpai.com.cn/doc/pc/182426.htm)


#	阿里同事架设在树莓派上的个人站点

*	[一粟](http://go.myalert.info/)
*	[空无](http://kongwu.net/)
*	[异翅](http://pi.k17.im/)
*	[朴灵](http://jacksontian.eicp.net/)


