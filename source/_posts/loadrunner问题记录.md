title: loadrunner问题记录
date: 2015-08-10 13:54:01
tags: [LoadRuner]
---
1.简介
----------
	HTML-Based是在web测试脚本录制过程中默认选项。它基于界面，将属于一个界面的所有请求放在一个一个Web-url中。
	URL-Based在web测试脚本的录制过程，将每一个http请求放在一个Web-url中可读性较差。

2HTML-Base&URL-Based二者对比
----------
|编号|`HTML_Based` |  `URL_Based`|
|:--:|--|--|
|阅读性|HTML为用户的每一个动作产生单独的步骤，脚本录制结果简洁直接，可阅读性强|将每一个url请求放入web-url中，能更好的控制业务过程|
|选择|基于浏览器的应用选择此项|不是基于浏览器的应用/基于浏览器的应用中的脚本语言/javascript Applets向服务器发出了请求/使用了https协议|

注：录制过程不要使用浏览器的后退功能loadrunner对其支持不是很好。



