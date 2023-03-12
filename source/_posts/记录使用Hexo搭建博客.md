---
title: 记录使用Hexo搭建博客
date: 2023-03-06 12:37:19
tags: [博客搭建]
categories: [技术积累]
---

# 前言

Hello！大家好，我是小小峰。

这是本人博客的第一篇文章，用来记录如何使用Hexo搭建基于Github的个人博客。

开学后不知不觉闲了下来，前两天受实验室学弟一天搭了两个网站的启发，忽然萌生了搭建自己博客的念头，这也是自己几年前就想做但由于不懂如何上手一直未做的事情，这次刚好借这个机会了结这个遗憾。

 <!--more-->

刚开始考虑利用Hugo搭建，跟随B站视频无脑点击next，光速部署了一个个人展示主页，感觉求职时可能会有些作用，欢迎大家访问我的个人主页：[Just-Once's HomePage](https://justonce.netlify.app/)

Hugo个人主页的搭建可以参考此视频学习[零编程基础搭建个人主页 | 学术主页 | 网页制作 | Github妙用](https://www.bilibili.com/video/BV1Gz4y1f7Qj/?spm_id_from=333.1007.top_right_bar_window_history.content.click)

本博客的搭建基于Hexo，Hexo个人博客的搭建参考点击量超高的教程进行学习[【基础篇】hexo博客搭建教程](https://www.cnblogs.com/huanhao/p/hexobase.html#github%E9%83%A8%E7%BD%B2)

# 软件安装

## Nodejs + Git

首先安装这两个软件，下载路径为：[下载 | Node.js 中文网](https://nodejs.cn/download/) 和 [Git(git-scm.com)](https://git-scm.com/)

如果安装过了的小伙伴直接跳过进行下一步。

![image-20230311161433733](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311161433733.png)

运行安装包，根据自己的需求选定合适的安装地址，在下一页的设定中保持原有设置，它会自动创建环境变量，十分方便，接着一路点击next等待安装完成。

![image-20230311152324320](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311152324320.png)

同理，Git的安装也大同小异，没有太多坑，网上教程无数，一路next等待安装完成。

![image-20230311152922316](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311152922316.png)

安装完成后可以验证一下，按下键盘`Window 键 + R`，键入`cmd`按下回车，在任意命令行输入如下指令：

> node -v
> npm -v
> git -v

如果没问题应该和我图中显示的内容类似。

![image-20230311161548386](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311161548386.png)

这里大家请注意node的版本，官网下载的node 16往后的版本都是可以的，版本的要求源于图片上传问题，详情可以查看下一个博客教程。

【由于我们需要搭建的是个人博客，必然会涉及到md文件的上传，里面必然会包含图片，可是使用Typora的图片都是保存在本地的，所以直接上传一个包含博客内容的md文件，别人访问博客时是看不到图片的，那该如何解决呢？==> 这就需要配置图床了，将图片上传到云空间，从而给每张图片生成一个链接，这样就可以任意访问了】

## cnmp

接下来安装cnmp，通过国内镜像进行安装。（Tips：个人后续利用npm安装博客特效插件时出现了些小问题，通过cnmp安装成功解决，感觉cnmp还是有些用的，如果不安装的话，后续的Hexo相关操作会出现些小bug。）

> npm install -g cnpm --registry=https://registry.npm.taobao.org

安装完成后通过以下指令进行验证，如果出现下图类似的版本信息意味着安装完成了。

>  cnpm -v

![image-20230311162609696](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311162609696.png)

## Typora（推荐）

Typora是一个markdown【md】编辑器，是非常好用的记录工具，本博客就是利用此软件进行编写的，这里推荐的原因是因为编辑博客内容必然要编写md文件，所以利用此软件进行编辑非常的方便和快捷，下一篇博客将会介绍如何配置Github图床，欢迎大家阅读。

现在的Typora是收费软件，可在其官网下载：[Typora — a markdown editor, markdown reader](https://typora.io/)，也可在网上找到诸多免费资源，如：[Typora免费版，Typora最后一个免费版，安装包合集 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/510731592)，当然有能力的小伙伴还是支持下正版。

# 安装Hexo

在完成上述准备工作后，就可以安装Hexo了，首先创建一个英文名的博客文件夹，在文件夹下右键，打开Git Bash Here，执行以下命令，看到一行绿色的 `+hexo` 代表安装成功了。

> cnpm install hexo-cli -g

如果没有安装cnpm，可能会出现一些奇怪的问题。

安装完成后可以通过以下命令来验证Hexo的版本：

> hexo -v



![](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311164000845.png)

随后就可以进行初始化了，在博客文件夹的根目录下，必须是空文件夹，右键Git Bash Here打开，执行以下命令进行初始化操作。

> hexo init

初始化过程中会从Github上拉取一些内容，可能会卡在`Install dependencies`那一行，这是正常的，如果卡住就按下`ctrl + c`结束，再用国内镜像进行安装，即输入以下指令：

> cnpm install

# 部署和调整博客

安装完成后，执行下列指令启动Hexo，会看到在`localhost: 4000`端口启动，接下来就可以在浏览器打开图中的链接从而访问你的博客啦。

> hexo s

![image-20230311164827861](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311164827861.png)

当然，目前你的博客还空空如也，甚至都没有名字，那么就从修改主题开始进行美化，Hexo的主题可在https://hexo.io/themes/ 里面找到，每个主题都包含预览效果、配置文件和下载地址三个部分，你可以打开项目主页进行下载，并按照Readme文件内容的提示进行相应的配置和修改，不过里面很多主题多多少少是存在些问题的，当使用`hexo s`出现bug或者页面打不开时，停止继续浪费时间，换个主题即可。

当然你可以下载多个不同的主题，他们并不会冲突，都会保存到theme文件夹下，当然有一些主题的配置起来会比较麻烦，可以先选一个简单的项目学习一下，比如next主题、yilia主题，这些都是主流的问题较少的主题。其中next算是最受欢迎的主题了，它有详细的中文文档：[NexT 使用文档 (iissnan.com)](http://theme-next.iissnan.com/)，在这里不做详细介绍了，当然本人使用时出现了些问题，所以没有试验成功。

 以本博客使用的yilia主题为例，在博客根目录下Git Bush Here，并执行以下指令将主题下载到`themes/yilia`文件夹下，当然这个名字是可以改，只是不建议这么做。如果出现下载失败或卡住的情况，可以直接在Github页面中的`Code`按键里面，点击下载zip压缩包，解压后修改名字，放到themes文件夹下也是可以的。

```
$ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```

接着，修改博客根目录下的 `_config.yml` ： `theme: yilia`，这里注意区分博客根目录下的配置文件和主题目录下的配置文件，虽然同名，但一个是配置博客的，一个是配置博客当前使用的主题内容的。随后就可以进行预览了，执行如下指令：

> hexo s

完善的Hexo主题会在项目主页展示详细的配置文件修改方法。如果仍有疑问推荐阅读[【基础篇】hexo博客搭建教程 - huanhao - 博客园 (cnblogs.com)](https://www.cnblogs.com/huanhao/p/hexobase.html#github部署)的6.1、6.2节学习，其中详细介绍了如何修改布局和修改语言。

## 创建博客

【本节默认已经下载了Typora并且配置好了图床，图床的配置参考下一篇博客】

现在我们可以进行博客的创建了，如果是按照上述步骤顺序完成，那么将会在个人主页看到一个Hello Word的默认博客，博客内容在`.\blog\source_posts\hello-world.md`中，可以用Typora打开看一下内容，同时强烈建议提前学习下markdown语法，为后续书写博客做准备，附上一个markdown语法的入门博客[【hexo博客进阶】1.Markdown语法](https://www.cnblogs.com/huanhao/p/markdown.html)

我们使用指令`hexo new`来新建一个博客，该指令会创建一个`文章名.md`文件到`.\blog\source\_posts`下，并按照一定的格式创建抬头内容。（引号可加可不加）

> hexo  new "博客名"

创建完成后，就可以使用Typora打开md文件进行博客内容的编写啦，并通过执行指令`hexo s`重新启动hexo，即可看到hexo自动读取了文件内容，并展示在本地网页上了。

## Github部署

为什么要进行部署呢？因为前面创建的博客目前只能本地访问，还没有上传到网上，利用Github进行部署后，即可将本地内容以`html`的形式上传到一个云端仓库，这样只要用户联网，就可以通过链接访问你的博客了。

Github可以部署一个免费的个人主页，首先我们在创建账号后，需要新建一个仓库，仓库名要和你的Github名字一样，并在后面加上`.github.io`，同时勾选初始化`README`选项，创建完成后点击`Settings –> Pages`设置从一个分支创建。由于初始创建，应该是空的仓库，那么应该是基于main分支构建，我这里设置为master的原因是main分支部署了个人主页。

![image-20230311214732961](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311214732961.png)

接下来创建一个git秘钥，在任意位置打开Git Bash Here，执行如下指令，注意用自己的邮箱替换。

```bash
ssh-keygen -t rsa -C “your_email@youremail.com“
```

然后执行

> cat ~/.ssh/id_rsa.pub

会输出你的密钥，我们复制输出信息，然后打开Github，依次点击头像下的`Settings - SSH - New SSH Key`

![image-20230312150007459](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230312150007459.png)

粘贴你复制的密钥

![image-20230312150036914](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230312150036914.png)

然后打开Git Bush Here，执行：

> ssh -T git@github.com

在需要输入`yes/no`的地方输入`yes`即可，然后回到项目，复制对应分支下`Code`中的SSH地址，将复制到的地址填写进博客目录下`_config.yml`的`deploy`项中即可。

![](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230312145359597.png)

![image-20230311220104861](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230311220104861.png)

紧接着安装一个上传插件，执行上传指令即可上传到指定的Github仓库中。

```
# 安装上传插件
cnpm install hexo-deployer-git --save
# 上传到github
hexo g -d
```

然后打开项目，点击`Settings`，往下找到`Github Pages`，点击`none`，选择`master branch`。

![image-20230312150848830](https://cdn.jsdelivr.net/gh/Just-once/BlogImages/Img/image-20230312150848830.png)

铛铛铛，大功告成啦，现在你可以打开刚刚部署的网址：https://just-once.github.io/ 进行访问。

## 结语

以上就是使用Hexo搭建基于Github的个人主页全过程了，这是我的第一篇文章，以后将在此博客记录更多的学习内容，同时会不定期分享美食打卡、阅读笔记、旅游游记和个人心得等等，喜欢的话就赶快收藏本博客吧。

最后，欢迎大家访问我的个人主页：[Just-Once's HomePage ](https://justonce.netlify.app/) 和个人博客：[Just-Once's Blogs](https://just-once.github.io/)，感谢大家的喜欢和关注，您的赞赏是对我最大的支持和鼓励，后续将继续创作更多的优质内容，如有疑问请直接留言评论，欢迎大家积极转发，我们下次再见！
