---
layout:     post   				    # 使用的布局（不需要改）
title:      记一次manjaro变arch的奇妙经历
subtitle:   已经引起教主的极度不满（持续更新中）
date:       2019-08-16 				# 时间
author:     Alex 						# 作者
header-img: img/ai-newheadpic.png 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - Linux
    - 终端
---

## 等等，让我先解释一下是怎么发生的...
>emmm，我在酷安上交流Linux使用的时候，因为用了Archlinux的话题，就被”Arch大邪教CN分教“的教职人员以及忠实信徒洗礼了一遍。便下定决心洗心革面，只要有空就入Archlinux。于是前晚上刻好了Archlinux的livecd，准备一气呵成，没想到居然被一个DNS的问题困住了（手机开无加密热点分享给电脑的，有老哥知道解决方法吗？），折腾30分钟无果，只好重启进入Manjaro。这时忽然想起了以前一位Antergos用户一日离奇变Archlinux（Antergos是arch的下游发行版），~~心想，这到底是人性的扭曲，还是道德的沦丧？但还没想出，~~我就对manjaro动了手。



# 搞机过程

**声明：以下方法并非正常操作，不保证不会出现问题，出现问题后可以在Google、archwiki等处寻找解决方案、或者询问各位大佬。因为使用以下方法导致损失请自行负责，本人不承担任何责任。使用者应具有基本的独立解决问题的能力！再次提醒：数据无价，请谨慎！**！

首先在

[]: https://mirrors.tuna.tsinghua.edu.cn/help/archlinux/	"清华大学开源镜像站"

查archlinux的源地址，替换掉/etc/pacman.d/mirrorlist里的manjaro源地址：

```
$sudo vim /etc/pacman.d/mirrorlist
```

其实可以全删掉，就留清华源里面那个。然后

```
$sudo pacman -S pacman #不知道是否需要？
$sudo pacman -R manjaro-keyring
$sudo pacman -S archlinux-keyring archlinuxcn-keyring
$sudo pacman-key --init
$sudo pacman-key --populate archlinux
$sudo pacman-key --refresh-keys
$sudo vim /etc/pacman.conf
```

　　修改/etc/pacman.conf，将所有的SigLevel的等号右边通通改成Never。（安装本地软件包那个可不改）
　　以下指令中，凡是提示不能满足依赖关系又不重要的，都暂时删了。如果被错误提示中止，先别忙着继续，Google一下为什么。
```
$sudo pacman -S $(pacman -Qenq)
$sudo pacman -Syyu
$sudo pacman -S linux linux-headers  #把内核换成arch提供
$sudo pacman -S pacman-mirrorlist #直接选择卸载pacman-mirrors
```

如果重启后没事，你就偷着乐吧～

**备选方案**：如果以上方案行不通，可以将
```
#pacman -Qenq | pacman -S -
#pacman -Syyu
```
替换为
```
$sudo pacman -Syyu --overwrite '*' #没有尝试过...
```
为了减小滚挂的概率，在之后仍然*推荐*执行
```
$sudo pacman -S $(pacman -Qenq)
```

# 后记
　　我使用的是manjaro18.04，安装后通过滚动更新到最新版本，不保证每个版本的manjaro都可以成功，也不保证此方法一直有效。即使你成功了，也有可能会在以后的某次滚动更新中滚挂。~~这不是arch的特性吗？~~如果你们有更稳妥的方法，欢迎分享。

　　其实安装archlinux，用不着完全像ArchWiki教程那样一步一步完全自己配置。某位知乎网友提到，可以将配置比较类似的电脑上的archlinux通过备份还原软件复制到自己的电脑上，再经过一些很简单的配置流程即可。

　　不过，按照Arch wiki安装系统，你可以更深入地了解Linux的系统构成，也可以在解决问题中找到普遍方法。~~貌似Arch用户们更倾向于把这看成是一种挑战，完成安装来证明自己有能力加入大邪～，如同原始部落规定让一定年龄的男孩去野外打一头狼来作为自己已经成年的标志？那我的这个行为该怎么定义？！~~也许这正是arch的精神所在？好吧，等我下次有时间了再折腾。

# 一点补充
1.根据网友的反馈，在操作后出现“syntax：/etc/pacman.conf“之类的字样，只需要编辑pacman.conf，注释掉”syncfirst“一行即可。

2.还有一个自己遇到的问题，就是发现无法更新linux内核，screenfetch始终显示manjaro字样。可以先删掉/boot/initramfs-linux.img,initramfs-linux-fallback.img,vmlinuz-linux三个文件，然后
```
$sudo pacman -S linux
$sudo grub-mkconfig -o /boot/grub/grub.cfg
```
   重启就好了。


3.如果执行过程中遇到任何软件包不符合依赖关系，请大胆卸载。特别是pamac-cli,pamac-gtk-pamac-common,manjaro-system-utility等包。在变成arch后如需继续使用图形化包管理器pamac-gtk，可以从aur获取。
 ```
$yay -S pamac-aur
```
4.本人极度diss某些认为Archlinux用户高人一等的思想。你可以认为“arch用户比manjaro用户更厉害”，这是无可厚非的，可是你不能歧视manjaro用户。我承认Manjaro有许多亟待完善的地方，但不能因此否定manjaro官方团队和社区的努力。如果你对manjaro有一些合理意见，我可以帮你转达manjaro的开发者们。（我在manjaro英文tg群）    
5.听说还有一个arcolinux，非常像archlinux哦~~（疯狂暗示）~~
6.这个帖子不会再继续更新了。需要使用类似方法的可以了解一下endeavour os，只需要修改/usr/lib/os-release和/etc/lsb-release即可。

7.猜猜我发现了什么
![JxYHz9.jpg](https://s1.ax1x.com/2020/05/02/JxYHz9.jpg)
~~风评被害~~
老子~~金盆洗手~~不干了！

**最近更新于2020年5月2日22：31**，如果发现问题，欢迎在以下评论区或者酷安反馈。
