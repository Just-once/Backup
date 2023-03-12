---
title: Typora配置Github图床
date: 2023-03-12 19:32:28
tags: [博客搭建]
categories: [技术积累]
---

## 前言

 在完成个人博客搭建后，就可以尽情书写文章了，这里推荐使用Typora进行编写。虽然说`md`文件打开方式有很多，例如`JetBrain`系列、`VSCode`甚至连记事本都可以进行阅读，但编辑时通常会涉及到图片上传，这个时候用上述软件就显得不那么方便了，而Typora提供了一个非常方便的解决方案，不仅可以随意插入和预览，而且可以直接连接到图床，使我们设定好图床后，可以直接将图片粘贴到文档中，从而实现图片的自动上传，没错，就是这么的丝滑。

<!--more-->

 在未设置图床之前，我们插入到文档中的图片会保存到本地的一个文件夹下，即：

```
C:\Users\xxxxx\AppData\Roaming\Typora\typora-user-images
```

 如果直接将这个`md`文档作为博客内容发布，别人访问博客时是看不到里面的图片的，而那些下载的md文档可以看到图片，是因为里面的图片细看的话都是一个个具体的链接，这就是我们为什么要设置图床的原因了，即利用图床，将`md`文档中的图片自动变成一个个具体的链接，实现方式其实也很简单，就是完成图床配置后，文档的图片会被自动上传到云端仓库，从而为每张图片生成一个独一无二的链接。

## 软件下载

 在Typora的文件—偏好设置中，有一个图像设置，其中提供了一个上传服务设定的选项，在`Windows`上提供了三个选择，分别是PicGo的命令行模式、PicGo的app模式、普通命令行模式，为了操作的简便直接选择app模式。

![image-20230312195613756](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230312195613756.png)

这里需要下载PicGo软件[PicGo Download](https://molunerfinn.com/PicGo/)，点击它提供的下载链接，下载它的最新版，点击安装，接着在上图PicGo路径中找到安装的PicGo软件即可。

![image-20230304214524590](https://cdn.jsdelivr.net/gh/Huangzhw0221/BlogImages/img/image-20230304214524590.png)

## 设置图床

 接下来进行PicGo图床的配置，这里以Github设置为例。

![image-20230312200416276](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230312200416276.png)

从上往下逐项看，第一个需要设置一个仓库名，那么我们就在自己的Github仓库中新建一个存放图片的仓库，然后填入即可。

![image-20230312200555443](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230312200555443.png)

 这里的存储路径就是子文件夹名称，大家可以自定义文件夹名，最好使用`README`文档进行记录，方便使用图床时根据需求分清哪个文件夹对应的是哪个应用的图床。

 接下来设定Token，这里需要我们填写一个新生成的token，如图所示，在头像下依次点击`Settings –>Developer settings - Token(classic)`，点击生成一个新token(classic)。

![](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311215701853.png)

 在Note一栏填一个用途方便自己记住，过期时间根据自己定，scopes中只需要勾选一个repo即可。这里注意，生成的token只会显示一次，所以千万别直接关闭了页面，不然就找不到了，当然可以再次重复上述操作。将token复制粘贴到`设定Token`中即可。

![image-20230304215736524](https://cdn.jsdelivr.net/gh/Huangzhw0221/BlogImages/img/image-20230304215736524.png)

最后，在自定义域名处输入如下地址即可，注意用自己的Github名和仓库名替换引号内容哈，这样就大功告成啦！

```bush
$ https://cdn.jsdelivr.net/gh/"github-name"/"repo-name"
```

这个操作其实是使用了`jsdelivr`加速，可以让我们无须担心国内防火墙的问题从而影响使用，最后别忘了`设为默认图床并保存`哦，赶快打开PicGo上传张图片试下吧！

## 结语

趁着刚搭完还热乎，抓紧记录下博客搭建的过程，方便后续回忆，这也是使用个人博客的一个好处，可以用这种朴素且及时的方式随心所欲地记录下某一过程，相比在CSDN、知乎这样的网站写文章，显然使用md写博客要更加地轻松自在。以后将在此网站记录更多的学习内容，同时会分享美食打开、阅读笔记、旅游游记和个人心得等，喜欢的话就赶快收藏吧。

最后，欢迎大家访问我的个人主页：[Just-Once’s HomePage](https://justonce.netlify.app/)和个人博客：[Just-Once’s Blogs](https://just-once.github.io/)，感谢大家的支持和关注，你的赞赏是对我最大的鼓励，后续将会继续创作更多的优质内容，如有问题欢迎大家留言评论和转发，期待下一次的相遇，拜拜！
