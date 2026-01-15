---
title: Voicemeeter虚拟声卡软件的使用
tags: [Voicemeeter,软件,声卡]
category: 软件使用
image: 'https://img.202261.xyz/blog/202508/Voicemeeter_Banana-4.png'
published: 2025-08-02
description: 我个人的Voicemeeter设置指南
draft: false 
---
## 写作原因

今天在打开电脑看B站时又没了声音，打开声音设置后对着之前折腾的Voicemeeter声卡软件一脸懵B。刚刚又看了一会儿B站教程才想起来这软件到底怎么用，以及去年是怎么设置的。现在记录一下正常的设置来在未来时再面对类似今天的情况下帮助自己。~~怎么上一句怎么写都不顺，反正也没人看，自己能看懂意思得了~~

---


## 电脑声音设置
在声音设置中进行如下设置：
- 播放： 将Voicemeeter Input设置为默认设备
- 录制： 将Voicemeeter Out B1设置为默认设备

不用管其他的，直接设置就完事了

- Voicemeeter Input对应Voicemeeter软件中的virtual input栏下的Voicemeeter Input
- Voicemeeter Out B1对应Voicemeeter软件中输出的B1
## Voicemeeter软件设置
![](https://img.202261.xyz/blog/202508/Voicemeeter_Banana-4.png)
Voicemeeter软件界面就像上图这样，看不到图片的话可以等待加载，加载不好的话就是图床炸了。
### Stereo input部分
三个都一样，每个部分都是Voicemeeter把你选择的设备输入（例如麦克风）根据面板设置进行处理，处理之后输出到该部分右侧你点亮的按钮中。
图中点亮了B1，就代表把选择的物理硬件耳机麦克风处理后输出到Voicemeeter Out B1，也就是刚设置的系统使用的默认录制设备。
### Virtual input部分
左右两个分别对应Voicemeeter Input，Voicemeeter AUX Input。
图中使用的是刚设置的Voicemeeter Input，将该输出经过处理后输出到A1中。也就是将刚设置的默认播放设备（Voicemeeter Input）输出到（A1）中。
### 最右侧部分
上部A1，A2，A3可以选择分别要使用的物理硬件，图中选择的就是耳机。
中间为选择的音轨进行录制的组件，可以点亮右侧按钮后进行录制。
下侧分别是A1，A2，A3，B1，B2。可以在此在最终输出之前进行进一步处理。

