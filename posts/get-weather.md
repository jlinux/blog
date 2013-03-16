---
title: 获取天气信息
date: '2013-03-16'
description:
categories:
- 2013
- 智能
tags:
- raspberry Pi
- 天气
- 自动获取
---

#	从中国天气网获取天气信息

`TODO：待完成代码，准备初试GO` 

从中国天气网自动获取天气：

杭州地区的获取[URL](http://m.weather.com.cn/data/101210101.html)。

>PS：从JSON的格式上，这个开发团队需要优化对数据结构的设计。

记录一下已经获取并解析好的数据

	{
	  "weatherinfo":{
      "city":"杭州",
      "city_en":"hangzhou",
      "date_y":"2013年3月16日",
      "date":"",
      "week":"星期六",
      "fchh":"18",
      "cityid":"101210101",
      "temp1":"12℃~21℃",
      "temp2":"12℃~22℃",
      "temp3":"13℃~24℃",
      "temp4":"14℃~23℃",
      "temp5":"10℃~15℃",
      "temp6":"12℃~25℃",
      "tempF1":"53.6℉~69.8℉",
      "tempF2":"53.6℉~71.6℉",
      "tempF3":"55.4℉~75.2℉",
      "tempF4":"57.2℉~73.4℉",
      "tempF5":"50℉~59℉",
      "tempF6":"53.6℉~77℉",
      "weather1":"中雨",
      "weather2":"大雨转多云",
      "weather3":"多云转阵雨",
      "weather4":"阵雨转多云",
      "weather5":"阵雨",
      "weather6":"阴转阵雨",
      "img1":"8",
      "img2":"99",
      "img3":"9",
      "img4":"1",
      "img5":"1",
      "img6":"3",
      "img7":"3",
      "img8":"1",
      "img9":"3",
      "img10":"99",
      "img11":"2",
      "img12":"3",
      "img_single":"8",
      "img_title1":"中雨",
      "img_title2":"中雨",
      "img_title3":"大雨",
      "img_title4":"多云",
      "img_title5":"多云",
      "img_title6":"阵雨",
      "img_title7":"阵雨",
      "img_title8":"多云",
      "img_title9":"阵雨",
      "img_title10":"阵雨",
      "img_title11":"阴",
      "img_title12":"阵雨",
      "img_title_single":"中雨",
      "wind1":"南风小于3级转微风",
      "wind2":"微风转西北风小于3级",
      "wind3":"西北风转东南风小于3级",
      "wind4":"东南风转东北风小于3级",
      "wind5":"东北风转东风小于3级",
      "wind6":"东风转东北风小于3级",
      "fx1":"南风",
      "fx2":"微风",
      "fl1":"小于3级",
      "fl2":"小于3级",
      "fl3":"小于3级",
      "fl4":"小于3级",
      "fl5":"小于3级",
      "fl6":"小于3级",
      "index":"较舒适",
      "index_d":"建议着薄外套、开衫牛仔衫裤等服装。年老体弱者应适当添加衣物，宜着夹克衫、薄毛衣等。",
      "index48":"较舒适",
      "index48_d":"建议着薄外套、开衫牛仔衫裤等服装。年老体弱者应适当添加衣物，宜着夹克衫、薄毛衣等。",
      "index_uv":"最弱",
      "index48_uv":"弱",
      "index_xc":"不宜",
      "index_tr":"一般",
      "index_co":"舒适",
      "st1":"22",
      "st2":"13",
      "st3":"22",
      "st4":"13",
      "st5":"24",
      "st6":"14",
      "index_cl":"不宜",
      "index_ls":"不宜",
      "index_ag":"易发"
	}
	}