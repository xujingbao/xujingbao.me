---
title: 迁移到Octopress博客
date: 2013-08-11 17:25:01.000000000 +09:00
---

折腾了一个周末，终于把wordpress迁移到了octopress。以下是安装过程中遇到的一些问题:  
<!-- more -->
#### 使用exitwp进行文章转换出现的问题  
如果提示No module named bs4，需要安装BeautifulSoup ; 如果提示No module named yaml，需要安装pyyaml  

#### 在zsh环境下使用rake命令提示zsh: no matches found   new_post等等，是因为其中一些自负不是命令字符，需要进行转义，也可以在~/.zshrc中加入以下内容  
```
alias rake="noglob rake"
```

#### 图片路径的问题  
如果没有使用第三方的图床，wordpress的图片是保存在wp-content/uploads/，直接把这个目录下的图片下载下来，放在/octopress/source/images下，那么在md中可以直接引用/images/pathtoimage.png.  

#### 绑定域名  
在/octopress/source下创建一个名为CNAME的文件，内容就是要绑定的域名。push上去。然后再域名管理中，添加一个CNMAE指向到username.github.io,或者A记录到ip。  

#### invalid byte sequence in US-ASCII (2013.10.04更新)
when running rake generate for octopress, add this to your .profile or .zshrc etc.  
```
LANG=en_US.UTF-8  
LC_ALL=en_US.UTF-8
```