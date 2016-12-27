---
title: UIApplication
date: 2016-09-20 11:33:10
tags:
---


			
###	UIApplication功能

	1.设置应用提醒数字
	    获取UIApplication对象
	    UIApplication *ap = [UIApplication sharedApplication];
	    
	    在设置之前, 要注册一个通知,从ios8之后,都要先注册一个通知对象.才能够接收到提醒.
	    UIUserNotificationSettings *notice = [UIUserNotificationSettings   
	    	settingsForTypes:UIUserNotificationTypeBadge categories:nil];
	    注册通知对象
	    [ap registerUserNotificationSettings:notice];
	    设置提醒数字
	    ap.applicationIconBadgeNumber = 10;
	2.设置连网状态
	   ap.networkActivityIndicatorVisible = YES;
	3.设置状态栏
		应用程序的状态栏,默认是交给控制器来管理的.
		控制器提供的方法,可以直接重写这个方法
		在控制器当中设置状态栏样式
		-(UIStatusBarStyle)preferredStatusBarStyle{
    		return UIStatusBarStyleLightContent;
    	}
    	
    	隐藏状态栏,通过控制器的方式.同样实现方法:
    	返回NO时为不隐藏
    	返回YES时为隐匿
    	-(BOOL)prefersStatusBarHidden{
    		return NO;
    	}
    	
    	通常在开发当中都是应用程序来管理状态栏的.来做统一管理,不然的话, 会有很多个控制器.会非常的麻烦.
    	想要让应用程序管理状态栏,要在info.plist当中进行配置,
    	添加一个key值:是最后一个,View controller-based status bar appearance
    	设置为NO.就是应用程序来管理了.
    	
    	通过UIApplication来管理状态.
    	1.获取UIApplication
    	UIApplication *ap = [UIApplication sharedApplication];
    	2.设置状态栏样式.
        ap.statusBarStyle = UIStatusBarStyleLightContent;
        3.设置状态的隐藏
        ap.statusBarHidden = YES;
		
    	
	4.跳转网页
		UIApplication *ap = [UIApplication sharedApplication];
		URL:协议头://域名
		应用程序通过协议头的类型,去打开相应的软件.
    	NSURL *url =[NSURL URLWithString:@"http://www.baidu.com"];
    	[ap openURL:url];


			
###	UIApplication代理和程序的启动流程.

	所有的移动操作系统都有个致命的缺点：app很容易受到打扰。比如一个来电或者锁屏会导致app进入后台甚至被终止
	还有很多其它类似的情况会导致app受到干扰，在app受到干扰时，会产生一些系统事件，
	这时UIApplication会通知它的delegate对象，让delegate代理来处理这些系统事件
	
	delegate可处理的事件包括：
	应用程序的生命周期事件(如程序启动和关闭)
	系统事件(如来电)
	内存警告
	...
	
	UIApplication会在程序一启动时候创建一个遵守UIApplicationDelegate代理.
	这个就是我们程序一创建时的AppDelegate类.AppDelegate就是遵守了UIApplicationDelegate协议.
	在这个类中很定义很多监听系统事件的方法.同时也定义了一些应用程序的生命周期方法.
		
	主要方法有:
	
	 应用程序的生命周期
	 应用程序启动完成的时候调用
	- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
	    NSLog(@"%s",__func__);
	    return YES;
	}
	
	 当我们应用程序即将失去焦点的时候调用
	- (void)applicationWillResignActive:(UIApplication *)application {
	    NSLog(@"%s",__func__);
	}
	
	 当我们应用程序完全进入后台的时候调用
	- (void)applicationDidEnterBackground:(UIApplication *)application{
	   NSLog(@"%s",__func__);
	}
	
	 当我们应用程序即将进入前台的时候调用
	- (void)applicationWillEnterForeground:(UIApplication *)application {
	  NSLog(@"%s",__func__);}
	
	 当我们应用程序完全获取焦点的时候调用
	 只有当一个应用程序完全获取到焦点,才能与用户交互.
	- (void)applicationDidBecomeActive:(UIApplication *)application {
	    NSLog(@"%s",__func__);
	}
	
	 当我们应用程序即将关闭的时候调用
	- (void)applicationWillTerminate:(UIApplication *)application {
	   NSLog(@"%s",__func__);
	}

	2.应用程序的程动原理
		
		程序启动时执行main函数,在main函数当中有以下操作.
		int main(int argc, char * argv[]) {
		  @autoreleasepool {
        	第三个参数:UIApplication类名或者子类的名称 nil == @"UIApplication"
        	第四个参数:UIApplication的代理的代理名称
       		NSStringFromClass:把类名转化字符串
        	NSStringFromClass好处:1.有提示功能 2.避免输入错误
           return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
    	  }
    
    	}
	
	底层原理为:
		1.根据principalClassName传递的类名创建UIApplication对象
		2.创建UIApplication代理对象,给UIApplication对象设置代理
		3.开启主运行事件循环,处理事件,保持程序一直运行.
		4.加载info.plist,判断下是否指定main,如果指定了,就会去加载StoryBoard.