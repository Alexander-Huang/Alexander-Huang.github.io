---
layout:     post   				    # 使用的布局（不需要改）
title:      记一次manjaro变arch的奇妙经历 
subtitle:   或将成为安装archlinux最简单的方法?
date:       2019-08-16 				# 时间
author:     Alex 						# 作者
header-img: img/ai-seahouse.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - Linux
    - 终端
---

## 等等，让我先解释一下是怎么发生的...
>emmm，我在酷安上交流Linux使用的时候，因为用了Archlinux的话题，就被”Arch大邪教CN分教“的教职人员以及忠实信徒洗礼了一遍。便下定决心洗心革面，只要有空就入Archlinux。于是前晚上刻好了Archlinux的livecd，准备一气呵成，没想到居然被一个DNS的问题困住了（手机开无加密热点分享给电脑的，有老哥知道解决方法吗？），折腾30分钟无果，只好重启进入Manjaro。这时忽然想起了以前一位Antergos用户一日离奇变Archlinux（Antergos是arch的下游发行版），~~心想，这到底是人性的扭曲，还是道德的沦丧？但还没想出，~~我就对manjaro动了手。



# 搞机过程

**声明：使用以下方法造成的一切后果自行承担，一切问题自己上archwiki解决，不要找我**！

首先在

[]: https://mirrors.tuna.tsinghua.edu.cn/help/archlinux/	"清华大学开源镜像站"

查archlinux的源地址，替换掉/etc/pacman.d/mirrorlist里的manjaro源地址：

```
$sudo vim /etc/pacman.d/mirrorlist
```

其实可以全删掉，就留清华源里面那个。然后致命操作

```
$sudo pacman -Syyu --force
```

（如果你怕自己反悔，可以加一句“--noconfirm”哈哈）然后...重启试试会不会翻车

如果重启后幸运地没有任何问题，那么继续操（zuo）作（si）：
```
$sudo vim /etc/pacman.conf
```
　　修改/etc/pacman.conf，将所有的SigLevel的等号右边通通改成Never。（安装本地软件包那个可不改）
　　以下指令中，凡是提示不能满足依赖关系又不重要的，都暂时删了。如果被错误提示中止，先别忙着继续，Google一下为什么。
```
$sudo pacman -S pacman #不知道是否需要？
$sudo pacman -R manjaro-keyring
$sudo pacman -S archlinux-keyring archlinuxcn-keyring
$sudo pacman-key --init
$sudo pacman-key --populate archlinux manjaro
$sudo pacman-key --refresh-keys
$sudo pacman -S $(pacman -Qenq) #此命令由チェン提供
$sudo pacman -S linux linux-headers --force #把内核换成arch提供
```

如果重启后没事，你就偷着乐吧～

# 后记
　　我使用的是manjaro18.04，安装后通过滚动更新到最新版本，不保证每个版本的manjaro都可以成功，也不保证此方法一直有效。即使你成功了，也有可能会在以后的某次滚动更新中滚挂。~~这不是arch的特性吗？~~如果你们有更稳妥的方法，欢迎分享。

　　其实安装archlinux，用不着完全像ArchWiki教程那样一步一步完全自己配置。某位知乎网友提到，可以将配置比较类似的电脑上的archlinux通过备份还原软件复制到自己的电脑上，再经过一些很简单的配置流程即可。

　　不过，按照Arch wiki安装系统，你可以更深入地了解Linux的系统构成，也可以在解决问题中找到普遍方法。~~貌似Arch用户们更倾向于把这看成是一种挑战，完成安装来证明自己有能力加入大邪～，如同原始部落规定让一定年龄的男孩去野外打一头狼来作为自己已经成年的标志？那我的这个行为该怎么定义？！~~也许这正是arch的精神所在？好吧，等我下次有时间了再折腾。
