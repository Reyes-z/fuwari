---
title: 常用hexo命令
tags:
  - 博客
  - Hexo
published: 2020-07-09
category: blog
description: 最早时使用hexo写博客的操作
---

  
# git bash

## 更新网站(不是首次上传)

网站在本地更改完成后先运行

``` bash
hexo s
```

启动本地服务查看是否报错  
之后运行

```bash
hexo g 
hexo d
```

- 只更改yml文件是有时不会更新需要先运行以下代码

``` bash
hexo clean
```

 上传完成后如果访问后并没有更新，  
   手机端：清除浏览器缓存  
   PC端：在浏览器中按Ctrl+F5  
注 博客部署到github上博客会自动更新，部署到gitee上需要手动更新部署

# 网站的编辑

根据上述流程，添加新的文章或是修改文章内容

###### （以上内容写于2020年十月份）

## git bash更新后右键文件不显示

 自本博客搭建以来就~~没怎么更新~~没更新，今天偶然之间想了起来，结果在使用中发现在文件目录下鼠标右键后之前的Git Bush Here不见了，个人推测很大程度上是由于Git Bash更新导致的。  
 以下为我在网上找到的 [解决办法](https://blog.csdn.net/qq_41019529/article/details/110139830?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.control&dist_request_id=990e545b-d131-4ced-aed0-93fe0ccd6643&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-3.control)
