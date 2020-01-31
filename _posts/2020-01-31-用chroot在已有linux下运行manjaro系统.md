

---
layout:     post   				    # 使用的布局（不需要改）
title:      用chroot在已有linux下运行manjaro系统
subtitle:   适用于archlinux和manjaro
date:       2020-01-31 				# 时间
author:     Alex 						# 作者
header-img: img/ai-rainwindow.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签

​    - Linux

​    - 终端



> 这一切的一切都得从一只蝙蝠说起......
>
> 由于这只蝙蝠，本来已经快要结束的寒假，才刚刚开始......
>
> 我从未想过，一只蝙蝠竟然将我和亲爱的老师、同学们残忍地隔绝......

咳咳咳，进入正题

我本来想自己打包一个manjaro的镜像，询问国外大佬后发现需要使用一个manjaro官方提供的一个软件，又发现这个软件是manjaro源特供的，aur和archlinux源都没有...我又不愿意舍弃我心爱的archlinux，也不想装双系统...~~我太tm难了！~~然后我就突然想到两天前用chroot工具从livecd进♂入系统来修复滚挂的经验，准备试试用chroot来开启manjaro。

## 准备工作

你需要：

- 一台装有archlinux或者manjaro的电脑。
- 大概不少于5GB的空余硬盘空间。
- 如果你全盘装一个系统，你很可能需要一个U盘。

## 开始

1.从硬盘中分出不小于5G的分区，随你用什么方法。提示：①在系统运行时是不能从挂在到“/”的分区中分出空间的。②别搞出ntfs啥的格式，推荐ext4和zfs③如果你把系统格式化了...怪我咯？

​	我使用的是manjaro livecd里的kde分区管理工具，分区工作也很容易执行。也可以用windows pe中的分区助手。~~但是对于我，我是打死都不可能用fdisk的，因为fdisk已经在我内心深处留下了不可磨灭的伤痛。~~    

2.在系统任意你想要的位置创建一个文件夹，然后在你的系统里把分区挂载到这个文件夹。~~没错，我用的又是kde分区管理器，你觉得我菜你来打我啊！~~    

3.安装chroot工具`arch-install-scripts`，对于manjaro则是`manjaro-tools-base`。    

4.下载manjaro的bootstrap压缩包，然而我找了几个镜像源都没有，结果发现需要自己制作！而且工具也只有manjaro源下有...~~这让我想起来了某个买口罩的梗...~~所以这里用archlinux的bootstrap代用。懒人戳这里→[链接](https://mirrors.ustc.edu.cn/archlinux/iso/2020.01.01/)    

5.把压缩包解压后，bin、boot、dev、etc等等一大堆文件夹塞进你刚才创建的分区。

6.用arch-chroot(manjaro则为manjaro-chroot)进入这个系统，比如我的分区在/sec-sys(second system)

```
#arch-chroot /sec-sys
```

就进入了这个arch系统，可以进行你熟悉的操作了。

7.那么大佬们又要批评了：这不是manjaro，这是高贵的arch！这时候就需要逆用[Manjaro变arch大法](https://alexander-huang.github.io/2019/08/16/%E8%AE%B0%E4%B8%80%E6%AC%A1manjaro%E5%8F%98arch%E7%9A%84%E5%A5%87%E5%A6%99%E7%BB%8F%E5%8E%86/)

然后，你的manjaro就安装好了。不过，vim等等一样都没有，所以

```
#pacman -S nano vi vim fakeroot screenfetch python sudo
```

剩下的就可以自己搞了，比如新建普通用户等等( ﾟдﾟ)

## 参考资料

1.[Archwiki上关于chroot的介绍](https://wiki.archlinux.org/index.php/Chroot)

2.[Manjaro wiki上关于manjaro-tools的介绍](https://wiki.manjaro.org/index.php?title=Manjaro-tools)