---
title: hexo的搭建
date: 2016-08-31 11:12:57
tags:
---


####  1.需要安装的应用程序
-	###  node.js [地址](https://nodejs.org/en/)
-	###  集成git，安装xcode即可 

-	###  安装hexo
`终端输入 $ sudo npm install -g hexo-cli`（sudo 执行管理员权限）

####  2.使用Hexo来显示博客

#####  创建一个文件夹（blogxxx）（所有命令都是在该文件中）

-	进入到根目录执行命令
	-	cd blogxxx
	-	hexo init 
	-	npm install
	-	hexo s (运行hexo,以后要在本地运行博客只要输入该命令即可)
		-	http://localhost:4000/ 复制网址即可预览
	-	Ctrl+C(停止运行)
	
####   配置_config.yml文件 
#####  (1).显示图片的方法，使用asset-image：

-	cd到文件目录下，执行 npm install https://github.com/CodeFalling/hexo-asset-image --save
-	修改_config.yml 中有 post_asset_folder:`true`
-	在source/_posts中创建一个xxx.md文件同名的文件夹xxx,该xxx文件夹放入xxx.md文件中使用到的图片,在xxx.md中引用图片方式为：`![图片名称](xxx/图片名称带格式后缀)`

#####  (2).主题
-	git clone https://github.com/wuchong/jacman.git themes/jacman
	-	jacman文件夹下，从终端进入删除掉相关的.git和.gitignore文件
	-	在_config.yml文件中搜索theme，将theme：xxx设置为 theme： jacman（主题名）


####  3.关联github仓库的链接
-	在_config.yml文件中 ，将deploy改为
	-	type: git
	-	repository: 仓库链接
	-	branch: master（分支）

###关键步骤：关联命令

-	npm install hexo-deployer-git --save

设置url
-	在 `_config.yml` 文件中的 `http://yoursite.com` 替换为 `http://仓库名.github.io`

####  hexo 相关命令
###  设置git身份信息
-	####  git config --global user.name "你的用户名"
-	####  git config --global user.email "你的邮箱"
-	####  hexo clean 清理
-	####  hexo g 生成静态站点(位于public目录)
-	####  hexo deploy 发布
-	####  hexo deploy --generate 生成静态站点并发布


###  hexo的哪些文件需要上传到github上
####hexo/
-	不需要上传
	- public/         生成的静态页面，由hexo deploy自动上传到gh-page分支
	- node_modules/   hexo需要的模块，不需要上传GitHub
	- package.json    记录hexo需要的包信息，不需要上传GitHub
	- .gitignore      hexo生成默认的.gitignore，它已经配置好了不需要上传的hexo文件
-	需要上传
	- themes/         主题文件，需要上传GitHub的dev分支
	- source/        博文md文件，需要上传GitHub的dev分支
	- _config.yml     全局配置文件，需要上传GitHub的dev分支