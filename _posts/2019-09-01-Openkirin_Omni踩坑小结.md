---
layout:     post   				    # 使用的布局（不需要改）
title:      Openkirin Omni踩坑小结
subtitle:   居然是第一次刷原生...
date:       2019-09-01 				# 时间
author:     Alex 						# 作者
header-img: img/ai-star-track.jpg 	
catalog: true 						# 是否归档
tags:								#标签
    - Android
    - Notes
---


机型：华为P10p emui9.0 Android9.0

### 0.解锁码
　　我也不知道有什么渠道可以付费申请到解锁码，因为我是在官方通道关闭前1小时内申请的🤣需要的可以去酷安上问问已经解锁的酷友。

### 1.emui9.1刷完变砖
　　官网没有明确说明支持emui9.1，9.1测试版貌似可以，但只要更新内容中出现过erofs文件系统就别直接刷了。刷完就会变砖。
解决方案是通过华为手机管家（hisuite）连接手机，然后降级至emui9.0再刷。

### 2.开机转圈圈
　　重启进入rec双清，拔掉sim卡即可。最好在设置向导结束后再插上sim卡连接网络。

### 3.习惯指纹手势，不习惯虚拟键
　　在omnigears > device features里面打开指纹手势，设置成原来的指纹手势即可（但没有震动反馈）。然后可以在omnigears > buttons里面关闭“显示导航栏”。

### 4.显示过小
　　可以在显示 > 显示大小里面调节界面显示大小，但对部分应用无效（如知乎），一部分应用甚至会显示过大（如微信）。
　　更好的方法是通过adb shell调试，输入
```
wm density #后面跟你要的dpi
```
（我用的600，感觉挺舒服）提示：AndroidP都需要打开传输文件才能使用adb调试。但是调了过后微信还是有点大。。。

### 5.提示无法访问互联网
删除默认用HTTPS
```
adb shell settings delete global captive_portal_https_url
adb shell settings delete global captive_portal_http_url
```
分别修改两个地址
```
adb shell settings put global captive_portal_http_url http://captive.v2ex.co/generate_204
adb shell settings put global captive_portal_https_url https://captive.v2ex.co/generate_204
```
方法来自 [evil42](https://www.evil42.com/index.php/archives/17/)，当然，如果你有root权限，你可以试试[CaptiveMgr清除x和! ](https://www.coolapk.com/apk/tech.evlsoc.captivemgr)
### 6.发热，续航尿崩
　　使用一些工具管理一下就行了，比如绿守和黑域。我用的绿守无root模式（其实就是帮你手动强行停止）。用了过后充电发热、续航尿崩的现象都有所缓解。今天中度使用，续航约13小时😆（之前emui也才9小时呢）有些没必要的Google服务也可以停用，避免后台耗电。
　　可以安装一个lawnchair或者nova之类的桌面，然后设置一个手势用来手动休眠应用，用起来就很爽了🤔
　　旧手机也可以换一下电池，但本人学生党，没钱😫

### 7.动画过于浮夸
　　开发人员选项里将三种动画都设为0.5x。

### 其他问题
- 安装软件有时会卡住，退回桌面也是安装软件的画面。可以重启解决；安装时不要乱按，一般不会发生。
- 接电话（不是主动拨打）后还是有电话铃声😥可以接电话后静音。    
- 系统圆角实在太大了！有时候字都挤到圆角上了，特难受。

　　谁去xda反馈一下......
### 补充
现在在openkirin rr养老了。感觉rr问题比omni要少很多。不过安装软件偶尔还是会卡，而且安全补丁都是老早以前的了。
