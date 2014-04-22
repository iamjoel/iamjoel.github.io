title: hexo
date: 2014-02-03 10:45:49
tags: hexo
---
## 关于hexo
[hexo](http://zespia.tw/hexo/)是一个基于Node.js的静态博客程序，可以方便的生成静态网页托管在github和Heroku上。作者是来自台湾的@tommy351。<!--more-->引用@tommy351的话，hexo：
> 快速、简单且功能强大的 Node.js 博客框架。
A fast, simple & powerful blog framework, powered by Node.js.

类似于jekyll、Octopress、Wordpress，我们可以用hexo创建自己的博客，托管到github或Heroku上，绑定自己的域名，用markdown写文章。

## 安装
```
npm install -g hexo
```

## 初始化
```
hexo init
```

## 创建文章
```
hexo new '文章名'
```
然后可以去source/_posts/文章名.md 去编辑文章内容

## 预览
```
hexo generate
hexo server
```
然后访问`http://127.0.0.1:4000/`

## 命令缩写
hexo g == hexo generate    
hexo d == hexo deploy    
hexo s == hexo server    
hexo n == hexo new 

# tips
* 有的时候当你修改页面或更改配置后发现并没有立即生效，可以执行`hexo clean`然后再启动`hexo server`
* 在文档中插入`<!--more-->`就可以将文章分隔，more以上的部分会已摘要的形式显示，当查看全文时more以下的部分才会显示出来。也可以在Markdown文件中定义`description`。   

## 参考及更多
* http://yangjian.me/workspace/building-blog-with-hexo/
* http://zespia.tw/hexo/
* http://zipperary.com/2013/05/28/hexo-guide-1/#more
* http://zipperary.com/2013/05/28/hexo-guide-2/ 