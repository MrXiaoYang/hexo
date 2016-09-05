---
title: UITableViewCell的相关知识
date: 2016-09-05 10:00:17
tags:
---

###	1.每个cell之间有`固定的间距`

![cell样例](UITableViewCell的相关知识/cell样例.png)
###在自定义cell的.m文件中`重写`：

	- (void)setFrame:(CGRect)frame
	{
    	frame.size.height -= XMGMarin;
    
    	[super setFrame:frame];
	}
	
