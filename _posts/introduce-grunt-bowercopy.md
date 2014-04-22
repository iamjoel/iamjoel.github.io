title: grunt-bowercopy介绍
date: 2014-03-21 21:10:06
tags: bower
---
在介绍grunt-bowercopy之前,假定你是熟悉bower和grunt的（在本文末尾中有介绍bower与grunt的链接）。
<!-- more -->

## 用途
对使用bower的项目，安装好依赖后（`bower install`），依赖的目录结构是类似这样的:
![file-dir]({{BASE_PATH}}/image/introduce-grunt-bowercopy/file-dir.jpg)

我们资源的目录是在src下的。我们只需要bower_components下的部分文件。例如对于jquery,我们只需要jquery.min.js，而不需要其他文件。

我们当然可以人肉的从bower_components中复制需要的文件黏贴到src下。但是，好麻烦^-^。况且在一个项目的依赖很多时，依靠人肉，那就一场灾难了。这时候，就到grunt-bowercopy出场的时候了~

[grunt-bowercopy](https://www.npmjs.org/package/grunt-bowercopy)通过声明要源文件和目的地的路径，将文件复制到指定位置。如果该项目没有安装依赖，那么在执行复制任务前，它会自动的执行`bower install`来安装依赖。

grunt-bowercopy是依赖grunt的。

## 安装
```
npm install grunt-bowercopy --save-dev
```

## 示例
`Gruntfile.js`
```
grunt.initConfig({
    bowercopy: {
        options: {
            srcPrefix: 'bower_components'
            //clean: false // default false
        },
        libs: {
            options: {
                destPrefix: 'libs/vendor' //目的地文件夹的路径
            },
            files: {
              'requirejs.js': 'requirejs/require.js'
            }
        }
    }
});
require( "load-grunt-tasks" )( grunt );//加载所有的grunt任务

```
运行`grunt bowercopy`，会将`bower_component/requirejs/require.js` 移动到`libs/vendor/requirejs.js`。

更多选项见 https://www.npmjs.org/package/grunt-bowercopy

## 资源

### bower
http://bower.io/    
http://code.tutsplus.com/tutorials/meet-bower-a-package-manager-for-the-web--net-27774    
http://iamjoel.github.io/2014/03/02/introduce-bower/

### grunt
http://gruntjs.com/getting-started    
http://weblog.bocoup.com/introducing-grunt/

