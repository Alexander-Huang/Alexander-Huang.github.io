---




layout:     post   				    # 使用的布局（不需要改）
title:      Archlinux+Budgie体验小记 				# 标题 
subtitle:   大型真香现场（你还要香几次??）    #副标题
date:       2020-01-23 				# 时间
author:     Alex 						# 作者
header-img: img/ai-dark-whale.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - Linux
    - 安利
---

## 前言

**声明：该文章首发于Coolapk** [原文链接](https://www.coolapk.com/feed/16030672?shareKey=Nzg5NjNkYTA3MmMwNWUyOTg3MWU~&shareUid=1340820&shareFrom=com.coolapk.market_10.0.1) 

几天前我写了一篇gnome boxes的动态登上了头条，本以为这下子就可以从level 4直接升级到level 5，结果

[![1EPDyD.md.jpg](https://s2.ax1x.com/2020/01/22/1EPDyD.md.jpg)](https://imgchr.com/i/1EPDyD)

果然，降维打击过后人民生活日益艰苦.........所以我只好被迫营业，写篇图文试试看能不能升级(ノへ￣、)
在接触budgie之前，我还体验过Gnome，KDE，xfce，dde等等，可是都不如我意(￣_,￣ )（有的是渣机带不动Σ( ° △ °|||)︴

### GNOME

**优点：**
1.界面美观大方，虽然默认主题很吃藕，但是只要换一个主题马上让人眼前一亮。
2.操作方便，感觉像是“要用的功能都收集好了，不会用的功能都藏起来了”，所有会用到的功能都能凭借直觉找到，控件排列一点都不杂乱。
3.插件多样，可定制性较强。
**缺点：**
1.各种莫名其妙的bug和视觉瑕疵，时隐时现。
2.很多主题的窗口圆角参差不齐，有些窗口形如面包片，甚至有的窗口有一个或三个圆角，剩下的是直角。小圆角还看得过去，用大圆角的主题真的让非强迫症都想打人。
3.登录管理器gdm和锁屏巨丑，而且还不统一。gdm的主题是可以改，但是超麻烦，而且容易引出各种bug。（gdm主题其实算是“全局”主题）
4.插件并不是原生支持，在使用中会有各种小问题（比如曾经的dash-to-dock会在gdm上显示dock，后来已修复），据网友反馈，有的插件甚至会造成桌面崩溃。
5。内存和cpu占用真的多啊。天下苦GNOME久矣。

### KDE

**优点：**
1.德国boy出品，稳得一匹，gnome很多小问题kde都没有，比如窗口圆角，gdm不好改，插件各种问题。
2.自定义性强，哪儿不顺眼改哪儿。
3.模糊效果和各种动态效果超级好看。
4.既自带qt主题设置又自带gtk主题设置，比gnome-tweaks不知道高到哪里去了。
5.在显示较多控件的情况下有条不紊。
6.对于kde connect的原生支持，让手机和电脑双剑合璧，用过的都说好。
7.在美化做到如此程度的情况下内存占用较少，相比起gnome简直一个天上一个地下。

**缺点：**
1.新手不友好。看着特别容易晕菜，想要的功能有时候找不到，需要用一段时间来磨合。
2.默认主题吃藕。换了主题还是吃藕。怎么改都吃藕。最后只有来一张二次元壁纸提升一下整体观感...也许是我的审美观念已经被苹果的“大道至简”和Google的“material design”绑架了...
3.用着不舒服。怎么配都不舒服。
4.对gtk应用的兼容很不好，经常边角是直角，阴影也没有。

[![1VlHd1.md.jpg](https://s2.ax1x.com/2020/01/23/1VlHd1.md.jpg)](https://imgchr.com/i/1VlHd1)

我配置的kde不算是吃藕吧！但我就是觉得吃藕。。。

### xfce

**优点：**
1.占用极小。无论是内存还是cpu还是硬盘，总之一个字，小！在极其渣的电脑上也能流畅运行。
2.在应用上部分地学习了gnome简洁的特点，比如thunar文件管理器就做得不错。
**缺点：**
1.虽然同为GTK阵营，但xfce的美观度和gnome相比还是有很大差距。
2.xfce并不能很好地兼容gnome系的软件，比如（我仿佛记得）相册运行就有问题。
3.几乎算是没有自定义插件。xfce-look.org相比起gnome-look.org或是kde-look.org寒酸了许多。

然后我就遇到了budgie[受虐滑稽]budgie是一个重写了gnome-shell的gnome，把gdm替换为lightdm，换掉了gnome几乎所有会造成卡顿的模块[受虐滑稽]相当于一个预先安装了gnome全家桶并且调大了字体的xfce[受虐滑稽][受虐滑稽][受虐滑稽]只是不能装插件[捂脸]

### dde

**优点：**
1.界面美观，几乎可以媲美mac os，无可挑剔的美观度。
2.对国产软件似乎有优化，打开速度明显优于gnome、kde、xfce之流。
**缺点：**
1.界面较为简陋，需要用到的工具会经常找不到，最后往往会发现是真的没有。（比如我打开相册，想裁剪一张图片，或者是在上面画两笔，再或是打个马赛克，结果发现并没有这个选项。）
2.（据其他网友反馈）内存占用高。在我的电脑上不算高。
3.gtk主题不能全局更换，对dde全家桶不起作用。
4.对gnome系软件兼容不行。
5.自定义不行。

于是乎进入主题——

## Budgie截图与介绍

[![1Eir90.md.png](https://s2.ax1x.com/2020/01/22/1Eir90.md.png)](https://imgchr.com/i/1Eir90)

桌面，和gnome一样不能换图标w(ﾟДﾟ)w

[![1EF3VJ.md.png](https://s2.ax1x.com/2020/01/22/1EF3VJ.md.png)](https://imgchr.com/i/1EF3VJ)

侧边栏Raven

[![1VlxQe.md.png](https://s2.ax1x.com/2020/01/23/1VlxQe.md.png)](https://imgchr.com/i/1VlxQe)

通知中心也在Raven里面

[![1V19eA.md.png](https://s2.ax1x.com/2020/01/23/1V19eA.md.png)](https://imgchr.com/i/1V19eA)

gnome的设置界面，原封不动地来到了budgie

[![1V1VSS.md.png](https://s2.ax1x.com/2020/01/23/1V1VSS.md.png)](https://imgchr.com/i/1V1VSS)

budgie的桌面设置，相当于gnome-tweaks



[![1V1Kwn.md.png](https://s2.ax1x.com/2020/01/23/1V1Kwn.md.png)](https://imgchr.com/i/1V1Kwn)

登录窗口设置（其实是lightdm）

[![1V1GSU.md.jpg](https://s2.ax1x.com/2020/01/23/1V1GSU.md.jpg)](https://imgchr.com/i/1V1GSU)

手机照的登录窗口，这真是不能用截图键啊喂！

[![1V1dT1.md.png](https://s2.ax1x.com/2020/01/23/1V1dT1.md.png)](https://imgchr.com/i/1V1dT1)

sudo的登录验证框



[![1V1DfK.md.png](https://s2.ax1x.com/2020/01/23/1V1DfK.md.png)](https://imgchr.com/i/1V1DfK)

Tilix（默认是gnome-terminal，我换成了这个）

[![1V1cOH.md.png](https://s2.ax1x.com/2020/01/23/1V1cOH.md.png)](https://imgchr.com/i/1V1cOH)主题

左手wps右手mindmaster（思维导图）

[![1V1HXQ.md.png](https://s2.ax1x.com/2020/01/23/1V1HXQ.md.png)](https://imgchr.com/i/1V1HXQ)

死宅离不了的网易云，在kde下没有阴影，现在看着舒服了

[![1V1jkq.md.png](https://s2.ax1x.com/2020/01/23/1V1jkq.md.png)](https://imgchr.com/i/1V1jkq)

图标变形的kde connect（自己装的），与nautilus配合得比较好，配置后可以得到和kde下相同的体验

[![1V3p1U.md.png](https://s2.ax1x.com/2020/01/23/1V3p1U.md.png)](https://imgchr.com/i/1V3p1U)

可以设置hot corner，不过居然需要先添加小部件再在小部件里设置？好奇怪

主题包是arc，图标主题是flat-remix，zsh主题是powerlevel10k（并非oh-my-zsh里的）
平常资源占用很少，8G内存只占了4%，还是比较舒服了(′▽`〃)现在再次养老，看能养老到什么时候ヽ(✿ﾟ▽ﾟ)ノ

## 以下为酷安废话

加个话题 #Linux# 
再py几个酷友[@领主巴尔扎克](http://www.coolapk.com/u/1257621) [@这个世界](http://www.coolapk.com/u/655105) [@生来彷徨的人](https://codedreamz.github.io) 
[@酷安小编](http://www.coolapk.com/u/12202) ━━(￣ー￣*|||━━你懂的。

[原文链接](https://www.coolapk.com/feed/16030672?shareKey=Nzg5NjNkYTA3MmMwNWUyOTg3MWU~&shareUid=1340820&shareFrom=com.coolapk.market_10.0.1) 以后图文都在酷安首发，看看能不能多涨点经验。