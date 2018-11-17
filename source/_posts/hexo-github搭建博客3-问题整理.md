---
title: hexo-github搭建博客3-问题整理
date: 2018-11-16 17:06:56
tags:
---

{% blockquote %}
持续更新：
{% endblockquote %}

### [hexo官方文档](https://hexo.io/zh-cn/docs/)

### 2d插件  
1.安装这个live2d插件  
检查package.json里有没有 hexo-heloper-live2d 依赖，有的话先卸载了，然后重新安装一下。
{% codeblock %}
 npm uninstall hexo-helper-live2d  
 npm install --save hexo-helper-live2d
{% endcodeblock %}  

2.下载动画model   
  [点这里](https://github.com/xiazeyu/live2d-widget-models.git)  
  `https://github.com/xiazeyu/live2d-widget-models.git`   
3.将packages里面所有的模版放到你博客的node_modules目录里   
4.配置博客的配置文件，_config.yml  
   ```
# Live2D
## https://github.com/xiazeyu/live2d-widget.js
## https://l2dwidget.js.org/docs/class/src/index.js~L2Dwidget.html#instance-method-init
live2d:
  model:
    scale: 1
    hHeadPos: 0.5
    vHeadPos: 0.618
  display:
    superSample: 2
    width: 150
    height: 300
    position: right
    hOffset: 0
    vOffset: -20
  mobile:
    show: true
    scale: 0.5
  react:
    opacityDefault: 0.7
    opacityOnHover: 0.2

```

### 载入图片

1 把主页配置文件_config.yml 里的post_asset_folder:这个选项设置为true，之后生成的博文则会在同路径下增加一个同名文件夹，用来放资源。

2 执行 npm install hexo-asset-image --save

3 最后在xxxx.md中想引入图片时，先把图片复制到xxxx这个文件夹中，然后只需要在xxxx.md中按照markdown的格式引入图片：
\!\[你想输入的替代文字](xxxx/图片名.jpg)

### CNAME 问题  
`gitpage`里面可以设置自己的域名访问，首先域名配置`CNAME` = 自己的 gitpage，然后在仓库设置 `custom domain` ；  
  每次 hexo deploy 之后，custom domain 都会被重置为空，在hexo的`source目录`下 新建一个 `CANME 文件`，在里面写上你自己的域名，之后再提交就不会有问题啦！！  

### 搜索    
[我用的主题](https://github.com/ZEROKISEKI/hexo-theme-cube)
搜索框的设计样式参考了ppoffice的设计样式,只要进行输入即可进行对应的搜索, 此功能需要在您的Hexo站点上进行hexo-generator-json-content的安装和设置  
`npm install hexo-generator-json-content --save`  
然后在您的Hexo站点的_config.yml(非主题的_config.yml)上进行对应的设置:  
```
jsonContent:
  pages:
    title: true
    text: true
    path: true
    preview: true
  posts:
    title: true
    text: true
    path: true
    preview: true
```


### tags和categories页面
默认是没有 categories 和 tags 的；
```
hexo new page "tags"  
hexo new page "categories"  
```


编辑source下的tags和categories目录下的md文件  
``` 
type: "tags"
layout: "tags"


type: "categories"
layout: "categories"
```