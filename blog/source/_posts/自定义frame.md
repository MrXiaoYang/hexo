---
title: 自定义控件的frame
date: 2016-09-05 12:00:29
tags:
---

```
#import <UIKit/UIKit.h>

@interface UIView (Frame)

@property (nonatomic, assign) CGFloat xy_x;
@property (nonatomic, assign) CGFloat xy_y;
@property (nonatomic, assign) CGFloat xy_width;
@property (nonatomic, assign) CGFloat xy_height;
@property (nonatomic, assign) CGFloat centerX;
@property (nonatomic, assign) CGFloat centerY;

@end

#import "UIView+Frame.h"

@implementation UIView (Frame)

- (void)setXy_x:(CGFloat)xy_x
{
    CGRect frame = self.frame;
    frame.origin.x = xy_x;
    self.frame = frame;
}
- (CGFloat)xy_x
{
    return self.frame.origin.x;
}

- (void)setXy_y:(CGFloat)xy_y
{
    CGRect frame = self.frame;
    frame.origin.y = xy_y;
    self.frame = frame;
}
- (CGFloat)xy_y
{
    return self.frame.origin.y;
}

- (void)setXy_width:(CGFloat)xy_width
{
    CGRect frame = self.frame;
    frame.size.width = xy_width;
    self.frame = frame;
}
- (CGFloat)xy_width
{
    return self.frame.size.width;
}

- (void)setXy_height:(CGFloat)xy_height
{
    CGRect frame = self.frame;
    frame.size.height = xy_height;
    self.frame = frame;
}
- (CGFloat)xy_height
{
    return self.frame.size.height;
}

- (void)setCenterX:(CGFloat)centerX
{
    CGPoint center = self.center;
    center.x = centerX;
    self.center = center;
}
- (CGFloat)centerX
{
    return self.center.x;
}

- (void)setCenterY:(CGFloat)centerY
{
    CGPoint center = self.center;
    center.y = centerY;
    self.center = center;
}
- (CGFloat)centerY
{
    return self.center.y;
}

@end
```