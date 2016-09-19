---
title: 低版本的xcode适配高版本的iOS系统
date: 2016-09-19 16:46:46
tags:
---




将其放到下面目录下就可以了：如图/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/DeviceSupport
这个是xcode8运行iOS10所必须具有的文件夹。 Xcode7在相同路径下添加此文件夹即可

![图](低版本的xcode适配高版本的iOS系统/1.png)