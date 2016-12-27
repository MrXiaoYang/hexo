---
title: UIWindow
date: 2016-09-20 11:34:57
tags:
---


	UIWindow是一种特殊的UIView，通常在一个app中至少有一个UIWindow
	iOS程序启动完毕后，创建的第一个视图控件就是UIWindow，接着创建控制器的view，
	最后将控制器的view添加到UIWindow上，于是控制器的view就显示在屏幕上了
	一个iOS程序之所以能显示到屏幕上，完全是因为它有UIWindow
	
	在加载info.plist,判断下是否指定main,如果指定了,就会去加载StoryBoard.
		1.创建一个窗口
		2.加载MainStoryBoard,初始化一个控制器.
		3.把初始化出来的控制器设置为窗口的根控制器.让窗口显示到屏幕上.

	如果没有指定Mian话, 那这个时候就需要我们手动的去创建窗口.
	当info.plist文件没有找到的时候,那么程序就加载完毕,那么在程序加载完毕时要自己手动去创建窗口.
	
	在开发当中,通常都是手动去创建窗口.
	
	1.创建窗口,要有窗口显示,必须要有强引用.窗口也是控件,要想展示出来.必须得要有尺寸.
	  	self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
	2.创建控制器
	    会把控制器的View添加到窗口上.并且有一个旋转的功能.
	    UIViewController *vc = [[UIViewController alloc] init];
	    vc.view.backgroundColor = [UIColor redColor];
	   
	3.设置控制器为窗口的根控制器
		self.window.rootViewController = vc;
	4.显示窗口
		[self.window makeKeyAndVisible];
	
	
	
	在设置rootViewController的时候,会把控制器的View添加到窗口上面.
	[self.window makeKeyAndVisible]的底层实现:
		1.让窗口成为显示状态.
		  窗口默认是隐藏的.hidden = yes.
		  底层做的事件就是:
		   self.window.hidden = NO;
		   
		2.把当前窗口设置成应用程序的主窗口
		   application.keyWindow获得应用程序的主窗口.
	
	
	
	在程序当中,状态栏和键盘,它都属性是一个窗口.可以通过打印的方式来验证.
	设置window的层级.UIWindowLevelNormal它是一个CGFloat类型.
	self.window.windowLevel = UIWindowLevelNormal
	UIWindowLevelNormal < UIWindowLevelStatusBar < UIWindowLevelAlert