title: 反射型XSS(心伤的瘦子)
date: 2015-08-10 10:47:07
tags: [XSS]
---

    1.查看`< / "`等字符的过滤情况如果没有，直接X.

[ 什么都没过滤的入门情况](http://www.wooyun.org/bugs/wooyun-2010-015957)

    2.考虑用`&#x`的形式代替，如果没有过滤`& #` 理论上可以代替任意字符，但是一般都会将&过滤为`&amp`. 

[输出在`<script></script>`之间的情况](http://www.wooyun.org/bugs/wooyun-2010-015959)//这里构造的代码没懂
[输出在HTML属性里的情况](http://www.wooyun.org/bugs/wooyun-2010-015963)


    3.gbXXXX系列的可以考虑使用宽字符`%c0`杀掉双引号，可能是因为过滤的正则写的有问题.

[宽字节复仇记 [QQ邮箱基本通用]](http://www.wooyun.org/bugs/wooyun-2010-015969)


    4.`location.href="........."+"&ss=aaaa\"+"&from==1;function from(){}//"+"&param=";

如上所示代码：	
1用\来闭合双引号,//注视掉后面代码
2将=改为==提高优先级
3可是在解析时浏览器提示from未声明，浏览器会优先解析function XXX(){} 的JS函数，添加如上代码
4发现空格被过滤掉了用/**/代替空格 
[反斜线复仇记](http://www.wooyun.org/bugs/wooyun-2010-015979)

    5.输出出现在注释中使用换行符`%0a` 来使之后的代码生效。\.

[换行符复仇记](http://www.wooyun.org/bugs/wooyun-2010-016003)

     6.前面知识的综合应用

```
http://cgi.data.tech.qq.com/index.php?mod=search&type=data&site=digi&libid=2&curpage=1&pagenum=30&filterattr=138,138|16|4,5,4,5&filtervalue=3500-4000,%B4%F3%D3%DA4000|%D0%FD%D7%AA|WCDMA,WCDMA,HSDPA,HSDPA&tplname=centersearch.shtml&orderby=aaaa%c0%5c%0aalert(1);//
```
目标参数orderby
	
	1.使用换行符`%0a`使JS代码生效
	2.使用反斜线`%5c`解决语法错误，但是发现\被过滤为\\
	3.使用宽字符`%c0`杀掉一个反斜线最终保留一个反斜线，成功构造如上代码

以上资料来自[心伤的瘦子](http://www.wooyun.org/whitehats/%E5%BF%83%E4%BC%A4%E7%9A%84%E7%98%A6%E5%AD%90)@[乌云](http://www.wooyun.org)
