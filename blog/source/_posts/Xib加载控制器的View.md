---
title: Xib加载控制器的View
date: 2016-09-20 11:36:36
tags:
---


####	加载的步骤为:
	1.创建Xib
	2.往xib当中拖入一个View.
	3.设置Xib的file's owner类型为要设置的那个控制器.
	4.把View与file's owner连线.	(注意, 只有设置了file's owner类型才能够进行拖线.)
	
	initWithNibName:为要加载的Xib的名称.
	 MyViewController *vc = [[MyViewController alloc] initWithNibName:@"VC" bundle:nil];
	 
	 
####	xib使用注意事项:
	 1.如果一个view从xib中加载,就不能用[xxx alloc] init] 和 [xxx alloc] initWithFrame:]创建
	 2.如果一个xib经常被使用,应该提供快速构造类方法
	 3.如果一个view从xib中加载:
           用代码添加一些子控件,得在 initWithCoder: 和 awakeFromNib 创建
     4.如果一个view从xib中加载,会调用initWithCoder: 和 awakeFromNib,不会调用init和initWithFrame:方法