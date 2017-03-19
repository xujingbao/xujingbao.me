---
title: OSX升级失败后的无限菊花
date: 2013-09-16 15:32:24.000000000 +09:00
---

#### 问题现象  
10.8.5直接安装10.9 DP7出现错误，重启后无限菊花。  
无Time Machine备份。  
开机Command+R 通过磁盘管理工具Reinstall a new copy of OS X无效，因为10.9已是最新版T-T  
尝试过将菊花的电脑作为目标磁盘，通过火线连接，挂载到另一台Mac，失败。。  
<!-- more -->
#### 解决方案  
在其他电脑上制作了一个U盘系统盘（就是将一个完成OSX安装到了U盘),这个比较简单，就是要把U盘设置为GUID分区表，然后将10.9的安装到上边。  
然后在菊花的电脑的上开机按Option，选择U盘启动。因为系统完全从这个U盘启动，速度很慢。  
进入系统后，可以看到挂载的原硬盘，这时候把10.9的安装镜像copy到原硬盘上。双击开始安装，位置就是原硬盘大概20多分钟，系统就安装好了，再次进入系统就是崭新的10.9了，而且用户数据都在的。  