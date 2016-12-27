---
title: 从StoryBoard加载控制器
date: 2016-09-20 11:35:52
tags:
---


    1.创建窗口
    self.window = [[UIWindow alloc] initWithFrame:[UIScreen mainScreen].bounds];
    2.加载控制器
    从StoryBoard当中加载控制器
    UIStoryboard *storyBoard = [UIStoryboard storyboardWithName:@"Main" bundle:nil];
    加载剪头指向的控制器
    UIViewController *vc = [storyBoard instantiateInitialViewController];
    3.设置窗口根控制器
    self.window.rootViewController = vc;
    4.显示窗口
    [self.window makeKeyAndVisible];
    
    
    加载控制器的两种方式
    
    0.加载指定的StoryBoard.
    UIStoryboard *storyBoard = [UIStoryboard storyboardWithName:@"Main" bundle:nil];
    1.加载箭头所指向的控制器.
    UIViewController *vc = [storyBoard instantiateInitialViewController];
    2.加载指定标识的控制器.
     UIViewController *vc = [storyBoard 		
     						  instantiateViewControllerWithIdentifier:@"idCongtroler"];