---
title: "Hugo+Github Pages搭建个人博客"
date: 2019-12-08T19:55:48+08:00
draft: false
---

大家好，最近在学习如何使用hugo配合github pages搭建个人博客，将学习过程分享给大家。（我是win10 x64）
# 一、安装hugo
1. 安装包地址:<https://github.com/gohugoio/hugo/releases>  
   找到hugo_xxx_windows-64bit.zip的安装包进行下载
2. 解压缩到本地 \D:\Software\hugo\目录，只需要留下hugo.exe
3. 打开系统环境变量添加path路径:D:\Software\hugo\
4. 打开vscode,重启cmder终端，运行hugo version命令,如果正常显示版本号，则安装成功。

# 二、搭建个人博客并本地预览
进入hugo官网，按hugo官网的步骤操作，地址：<https://gohugo.io/getting-started/quick-start/>  
1. 创建一个目录用于存放博客项目，例如blog  
2. 新建hugo站点：  
   进入blog目录，新建一个hugo项目，即hugo站点，命令如下：
```
      hugo new site [project-name]
```  

我的站点名叫rukamina.github.io-creator;  
创建完成后，在rukamina.github.io-creator文件夹下会生成多个文件夹  

```
├── archetypes # 存放生成博客的模版
├── assets # 存放被 Hugo Pipes 处理的文件
├── config # 存放 hugo 配置文件 支持 JSON YAML TOML 三种格式配置文件
├── content # 存放 markdown 文件
├── data # 存放 Hugo 处理的数据
├── layouts # 存放布局文件
├── static # 存放静态文件 图片 CSS JS文件
└── themes # 存放主题
```  
3. 下载博客主题  
   创建完成后，进入rukamina.github.io-creator目录，运行命令  
   由于我下载不了官网的默认主题，在网上找了一个：  

```
    git clone https://github.com/olOwOlo/hugo-theme-even themes/even
```  
   进入themes\even\exampleSite目录，拷贝content文件夹和config.toml文件到根目录下，覆盖原来的配置，并根据自己的需要配置config.toml文件，配置引用：  
   [主题配置文件]<https://github.com/nusr/blog/blob/master/config.toml>
4. 新建博客  
   下载完成后在rukamina.github.io-creator目录下运行：  

```
     hugo new post/我的第一篇博客.md
```  
   运行后在content/post目录下新建博客文章成功，使用md语法编辑文章内容  
   md简单语法可参照文章<https://blog.csdn.net/weixin_42262935/article/details/81201447>;  
   注意：  
   * dtraft：ture是草稿，要改成false才能发布；  
   * 博客的时间一定得是当前时间或之前的，否则展示不了未来时间的博客
     
5. 本地查看博客，运行命令
```
    hugo server -D
```  
即开启了本地服务器，在运行结果中有博客本地地址，我的是http://localhost:1313/，  
按住ctrl，鼠标单击即可访问。  
6. 换肤
   * 进入hugo的themes官网，点击一个主题，点击homegate,按文章运行命令下载主题  
   * 修改config.toml文件主题为刚下载的主题  

 # 三、将博客配置到github上
7. 进入rukamina.github.io-creator目录，运行命令：  
```
hugo
```  

运行后会出现一个public目录，  
在根目录下新建文件.gitignore，文件中输入/public/，忽略public，public可以自成一个仓库  
进入public目录，运行命令
```
git init  
git add .  
git commit . -v
```  
2. 提交到本地仓库后，进入github个人首页，新建一个名为rukamina（个人github用户名小写）.github.io的仓库
 重新回到public目录，运行命令：  
```
git remote add git@github:xxx.git  
git push -u origin master
```  
把本地仓库代码提交到远程仓库后，打开settings,下划拉到github pages,
设置成master后出现的网址就是博客地址，博客配置到github上成功。  
3. 如果新增了新的博客文章或者博客有变动，则：  
* 重新回到根目录下，运行hugo命令；
* 进入public命令，再次git add,git commit ,git push操作. 
4. hugo插入图片  
可百度输入 hugo插入图片了解。

 本文参考原文<https://juejin.im/post/5cc41bfef265da036505031c>；  
 如有不对，欢迎指正，谢谢
