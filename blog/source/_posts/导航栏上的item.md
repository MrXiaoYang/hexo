---
title: 导航栏上的item
date: 2016-09-05 12:48:45
tags:
---



```
#import <UIKit/UIKit.h>

@interface UIBarButtonItem (Items)

/** 图片 高亮图片 */
+ (UIBarButtonItem *)itemWithImage:(UIImage *)image heghImage:(UIImage *)heghImage target:(id)target action:(SEL)action;

/** 图片 选择图片 */
+ (UIBarButtonItem *)itemWithImage:(UIImage *)image selImage:(UIImage *)selImage target:(id)target action:(SEL)action;

/** 图片 高亮图片 标题*/
+ (UIBarButtonItem *)itemWithImage:(UIImage *)image heghImage:(UIImage *)heghImage target:(id)target action:(SEL)action title:(NSString *)title;

@end

#import "UIBarButtonItem+Items.h"

@implementation UIBarButtonItem (Items)

/** 图片 高亮图片 */
+ (UIBarButtonItem *)itemWithImage:(UIImage *)image selImage:(UIImage *)selImage target:(id)target action:(SEL)action
{
    UIButton *btn = [UIButton buttonWithType:UIButtonTypeCustom];
    [btn setImage:image forState:UIControlStateNormal];
    [btn setImage:selImage forState:UIControlStateSelected];
    [btn addTarget:target action:action forControlEvents:UIControlEventTouchUpInside];
    [btn sizeToFit];
    UIView *contantView = [[UIView alloc] init];
    contantView.frame = btn.bounds;
    [contantView addSubview:btn];
    return [[UIBarButtonItem alloc] initWithCustomView:contantView];
}

/** 图片 选择图片 */
+ (UIBarButtonItem *)itemWithImage:(UIImage *)image heghImage:(UIImage *)heghImage target:(id)target action:(SEL)action
{
    UIButton *btn = [UIButton buttonWithType:UIButtonTypeCustom];
    [btn setImage:image forState:UIControlStateNormal];
    [btn setImage:heghImage forState:UIControlStateSelected];
    [btn addTarget:target action:action forControlEvents:UIControlEventTouchUpInside];
    [btn sizeToFit];
    UIView *contantView = [[UIView alloc] init];
    contantView.frame = btn.bounds;
    [contantView addSubview:btn];
    return [[UIBarButtonItem alloc] initWithCustomView:contantView];
}

/** 图片 高亮图片 标题*/
+ (UIBarButtonItem *)itemWithImage:(UIImage *)image heghImage:(UIImage *)heghImage target:(id)target action:(SEL)action title:(NSString *)title
{
    UIButton *btn = [UIButton buttonWithType:UIButtonTypeCustom];
    [btn setImage:image forState:UIControlStateNormal];
    [btn setImage:heghImage forState:UIControlStateHighlighted];
    [btn addTarget:target action:action forControlEvents:UIControlEventTouchUpInside];
    [btn setTitle:title forState:UIControlStateNormal];
    [btn setTitleColor:[UIColor blackColor] forState:UIControlStateNormal];
    [btn setTitleColor:[UIColor redColor] forState:UIControlStateHighlighted];
    [btn sizeToFit];
    btn.contentEdgeInsets = UIEdgeInsetsMake(0, -20, 0, 0);
    
    UIView *contantView = [[UIView alloc] init];
    contantView.frame = btn.bounds;
    [contantView addSubview:btn];
    return [[UIBarButtonItem alloc] initWithCustomView:contantView];
}

@end

```

