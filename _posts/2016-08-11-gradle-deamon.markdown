---
layout: post
title: 使用Gradle Daemon加速项目构建
date: 2016-08-11 15:32:24.000000000 +09:00
tag: Gradle 
---
![Gralde Logo](/assets/images/20160811/gradle-logo.jpg)

### Gradle构建块
每个Gradle构建都包含三个基本构建块：project，task和property。每个构建至少一个project，进而又包含一个或多个task。project和task暴露的属性可以用来控制构建。

在Gradle术语中，一个项目（project）代表一个正在构建的组件（比如，一个JAR文件），或一个想要完成的目标，如部署应用程序。每个Gradle构建脚本至少定义一个项目，当构建进程启动后，Gradle基于build.gradle中的配置实例化org.gradle.api.Project类，并且能够通过project变量使其隐式可用。

一个project可以创建新的task，添加依赖关系和配置，并应用插件和其他的构建脚本。
![Gralde Project](/assets/images/20160811/gradle_project.png)
![Gralde Project](/assets/images/20160811/gradle_class.png)

### 构建过程
构建初始化的很多工作是Java虚拟机的启动，加载虚拟机环境，加载class文件。
> 初始化->配置阶段->执行阶段

#### Gradle Daemon介绍
Gradle 守护进程（有时也称为构建守护进程） 的目的是改善 Gradle 的启动和执行时间。
![Gralde Project](/assets/images/20160811/gradle_fork.png)

### 配置与管理
#### 使用Gradle命令行选项调用在单个构建时选择启用或禁用后台守护进程

```  
gradle —daemon 
gradle --no-daemon
```  

#### 两种推荐的方式使守护进程持续与环境
通过环境变量 - 给GRADLE_OPTS环境变量添加-Dorg.gradle.daemon=true标识  
通过属性文件 - 给<<GRADLE_USER_HOME>>/gradle.properties文件
添加org.gradle.daemon=true


#### 在Windows中，该命令将使当前用户启用守护：
```  
(if not exist "%HOMEPATH%/.gradle" mkdir "%HOMEPATH%/.gradle") && (echo foo >> "%HOMEPATH%/.gradle/gradle.properties")  
```  
#### 在类Unix操作系统，以下的Bash shell命令将使当前用户启用守护进程：
``` 
ouch ~/.gragradle/gradle.propertiesdle/gradle.properties && echo "org.gradle.daemon=true" >> ~/.
```
一旦以这种方式在构建环境中启用了守护进程,所有的构建将隐含一个守护进程.

### 使用注意事项
#### 什么时候使用Gradle守护进程
官方建议在开发环境中使用Gradle的守护进程,不建议在持续集成环境和构建服务器环境中使用守护进程.

#### Gradle Daemon默认启用状态:
1.IDE等工具默认使用Gradle进行构建
2.命令行模式下，除非已经制定，否则不会使用Gradle Demon

#### 守护进程内存占用情况:
JVM的最小堆内存 < Gradle Daemon < 1G的堆内存

#### 多个Daemon
Daemon没有闲置或者版本不兼容等，启动新的Daemon

#### 关闭控制台提示
通过-no daemon的命令行选项禁用,或将org.gradle.deamon的值设置为false



