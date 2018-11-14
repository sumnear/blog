---
title: hexo+github搭建博客
date: 2018-11-14 08:54:33
tags: hexo
categories: hexo
---

一、准备环境：

1、安装Node.js环境；

2、安装Git环境，主要是用于直接同步生成的博客；

3、通过npm安装Hexo
{% codeblock %}
输入npm install hexo -g，开始安装Hexo
输入hexo -v，检查hexo是否安装成功
{%  endcodeblock %}
 
 
 二、初始化blog：
 
 1、新建blog文件夹
 
 2、通过Hexo初始化blog
 {% codeblock %}
 进入blog文件夹
 输入hexo init，初始化该文件夹
 输入npm install，安装所需要的组件
 输入hexo g，生成blog发布文件
 输入hexo s，开启服务器
 {% endcodeblock %}
 
 关联Githb
 
1、创建Github账号
 
 2、创建仓库， 仓库名为：<Github账号名称>.github.io
      github repositories  Settings
      {% codeblock %}
     repositories name : sumnear.github.io
     Custom domain 设置自己的域名 sumnear.top
       {% endcodeblock %}
      
 3、将本地Hexo博客推送到GithubPages
 3.1  安装hexo-deployer-git插件。在命令行（即Git Bash）运行以下命令即可：
  {% codeblock %}
  $ npm install hexo-deployer-git --save
  {% endcodeblock %}
  
  3.2   修改_config.yml（在站点目录下）。文件末尾修改为：
   {% codeblock %}
 deploy:
   type: git
   repo: git@github.com:<Github账号名称>/<Github账号名称>.github.io.git
   branch: master
  {% endcodeblock %}
  
3.3 设置Git的user name和email
 {% codeblock %}
git config --global user.name "sumnear"
git config --global user.email "402347012@qq.com"
{% endcodeblock %}
  
3.4 hexo把blog内容推送到github上
 {% codeblock %}
hexo d   
{% endcodeblock %}
 
 
