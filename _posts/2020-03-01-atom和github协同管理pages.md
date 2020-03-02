---
layout:     post   				    # 使用的布局（不需要改）
title:      atom和github协同管理pages
subtitle:   这才领会到了“21st editor”的强大
date:       2020-03-01 				# 时间
author:     Alex 						# 作者
header-img: img/ai-dreamarea.jpg 	#这篇文章标题背景图片
catalog: true 						# 是否归档
tags:								#标签
    - GitHub
    - Git
    - Notes
---

## 介绍
### 什么是Atom？
Atom —— “A hackable text editor for the 21th century.”  
Atom 是github专门为程序员推出的一个跨平台文本编辑器。具有简洁和直观的图形用户界面，并有很多有趣的特点：支持CSS，HTML，JavaScript等网页编程语言。它支持宏（插件十分丰富），自动完成分屏功能，集成了文件管理器。  
*至于我为不用VScode？因为...*
### 什么是Git？
Git是由Linus Torvalds~~教主~~为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。目前Git已经可以部署到所有常见平台上。
> 簡單的說，Git 就像玩遊戲的時候可以儲存進度一樣。舉例來說，為了避免打頭目打輸了而損失裝備，又或是打倒頭目卻沒有掉落期望的珍貴裝備，你也許在每次要去打頭目之前之前記錄一下，在發生狀況的時候可以載入舊進度，再來挑戰一次。（来源：[什么是git][4383cde6]

  [4383cde6]: https://gitbook.tw/chapters/introduction/what-is-git.html
### 那...什么是Github？
GitHub是一个比酷安大很多的世界级的~~同性交友平台~~。介绍完毕。
## 开始
**注意：此教程以~~(Arch)~~GNU/Linux平台为例，MacOS平台应该也可以参考，windows...好久没用windows了，我真的不知道怎么用...（Windows平台推荐GitHub Desktop）**  
首先获取Atom（[官网](https://atom.io/)） 还有Git。  
对于Archlinux用户，它们已经在official repository里面了！    
然后这里假设你已经有了一个GitHub帐号，而且已经在上面搭建了一个pages，但你不会用git，也没有用过Atom（就像我）。如果你有其他问题，欢迎在评论区交流。    
### 配置Atom
首先打开Atom：
![3gsO00.png](https://s2.ax1x.com/2020/03/01/3gsO00.png)
你就会骂道：什么垃圾软件！连中文也不支持！瞧不起我们中国人是不是！     
别急，慢慢来嘛～打开terminal，输入
```   
$apm config set registry http://registry.npm.taobao.org #换了国内源还是慢    
$apm search chinese #搜索中文语言支持
$apm install simplified-chinese-menu #装Atom-simplified-chinese装不上...
$apm install markdown-writer #提供完整的markdown支持，可以帮你省些事，也不用死记语法
```
小提示：Atom里ctrl+shift+p可以查找并执行各种命令（比如打开设置，新建文件等等），而且部分命令的快捷键也会出现在查找结果的后面，很方便，不必每次去翻菜单。
然后这个中文支持...只覆盖了菜单和设置。~~瞧不起中国人实锤了~~
![3ggKc4.png](https://s2.ax1x.com/2020/03/01/3ggKc4.png)
### 配置git与github
首先，你需要在电脑上生成SSH key来连接github。（其实还有其他方法，但我喜欢这种）这里以Linux为例，其他平台可以参考这个：[官网中文教程](https://help.github.com/cn/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
```
$ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
因为本人不那么注意安全，所以下面索要的一切内容直接一路回车一把梭。在意这个问题的看这里：[链接](https://help.github.com/cn/github/authenticating-to-github/working-with-ssh-key-passphrases)   
生成之后，在~/.ssh/id_rsa.pub领取你的密钥，并将它填入GitHub>（右上角）>Settings>SSH and GPG keys>New SSH key，备注随便填。密钥应该长这样：    
`ssh-rsa O-oooooooooo AAAAE-A-A-I-A-U- JO-oooooooooooo AAE-O-A-A-U-U-A- E-eee-ee-eee AAAAE-A-E-I-E-A- JO-ooo-oo-oo-oo EEEEO-A-AAA-AAAA Youremail@emailaddress.com`    
![3RPtQf.jpg](https://s2.ax1x.com/2020/03/02/3RPtQf.jpg)
然后开始clone你的pages repo到本地：
```
$ git clone git@github.com:your_account/your_pages.github.io.git
```
~~我相信没人会傻到真的1：1照抄上面的指令然后告诉我有问题。~~   
~~而且我最近发现英语水平问题真的会阻碍一个人从小白到高手的蜕变。~~   
然后你就会发现，github真tmd慢。[加速方法](https://zhuanlan.zhihu.com/p/65154116),（但是有一个小问题，就是不能用ipaddress来查，因为会把你绕到美国服务器去。用这个http://tool.chinaz.com/ ）   
当然，速度提升不很大。   
### 在Atom里载入Git repo
复制完后打开Atom，在菜单>文件>添加项目文件夹，添加你刚才的文件夹。然后扩展>GitHub>Toggle Git Tab,按下那个蓝色的按钮（忘记名字了），如果弹出文本框回车就行。在最上面的选择框选择你的pages repo。   
现在我们来试试配置成功了没：    
1. 让鼠标指针靠近左边框，点击出现的箭头拉出project文件列表，    
2. 在你的pages项目下随便找一个文件夹右键new file，取名test.md;    
3. 写下# test，**保存**；
4. 在刚刚的位置toggle git tab，点击unstaged changes右边的stage all，    
5. 在commit文本框中随便输入一些信息，点击commit to master，   
6. 在右下角点击push，   
7. 稍等片刻，在浏览器中打开你的pages的repo页，看看有没有更新。
![3RPhTJ.png](https://s2.ax1x.com/2020/03/02/3RPhTJ.png)

如果有，恭喜，你成功了！
### 后续配置
ctrl+,呼出设置，扩展>markdown writer中修改设置使之更符合你的习惯以及你的pages的规范。
## 完成！
然后也许你可以用这个写一篇blog来庆祝一下？
![3RCebQ.png](https://s2.ax1x.com/2020/03/02/3RCebQ.png)
