title: 记录hexo+icarus主题搭建博客遇到的问题
date: 2021-01-05 10:37:05
categories: 
- 日常捣鼓
tags: 
- hexo
- icarus
language: zh-CN
cover: /img/202101/blog-photo.jpg
thumbnail: /img/202101/blog-photo.jpg
---

Q1: 文章配置封面图和缩略图不展示
> 通过cover和thumbnail可以分别配置封面图和最近文章模块里的缩略图。这两个的值是一个以 `/` 开头的（绝对路径）图片所在位置路径。
不展示是由错误的图片路径设置导致的。正确的图片路径应该是：`/img/****`，对应到文件夹内，应该是 `/public/img`文件夹。
why: 服务器上部署的博客根目录就是`hexo generator`生成的`public`文件夹。也可以直接在浏览器地址栏输入图片路径，通过图片是否能够显示来检测路径是否正确。
    
<!--more-->

Q2: 在博客首页点击某篇文章标题，没有跳转到文章详情页跳转而是下载了该篇文章
> 这是因为链接地址配置不正确(配置文件：`_config.yml`)
错误的配置: `permalink: :category/:post_title`
正确的配置: `permalink: :category/:post_title/`
关键点在于有没有最后的`/`
为什么是:category、:post_title?这些是hexo里的变量，[详情看这里](https://hexo.io/zh-cn/docs/permalinks)

Q3: 博客部署到github-pages上样式丢失,但是本地预览样式存在
> 错误配置URL导致。
配置：`_config.yml`中的url: `http(s)://xxxxx.github.io/`, root: `/blog/`
url：配置部署网站的整个url，如果有二级目录，则root要写二级，比如说我的博客是放在blog下的，博客首页的访问地址是：`https://shenchuanhuan.github.io/blog`，那么url可以写 `https://shenchuanhuan.github.io/blog`，root则需要配置为 `/blog/`,在[hexo的配置里也有提及到](https://hexo.io/zh-cn/docs/configuration)

Q4: 如何添加评论插件？
> 因为很多插件都需要注册，所以选择了gitalk。详见[这里](https://blog.zhangruipeng.me/hexo-theme-icarus/Plugins/Comment/icarus%E7%94%A8%E6%88%B7%E6%8C%87%E5%8D%97-%E7%94%A8%E6%88%B7%E8%AF%84%E8%AE%BA%E6%8F%92%E4%BB%B6/)
如果按教程配置好了后，发现可以登录，但是无法评论或者评论框上有`Error: Not Fount`红色报错，可以检查一下`_config.icarus.yml`里`comment`配置项 `repo`是不是正确，repo要填写项目名，不是项目地址。评论是会作为issues出现在你配置的这个项目里的。
