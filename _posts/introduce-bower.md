title: 客户端包管理工具bower介绍
date: 2014-03-02 10:00:24
tags: bower
---
客户端(前端/浏览器端)包管理工具是相对于服务器端包管理工具（nodejs的npm,ruby的gem等）的。有了包管理工具，我们可以方便对项目的依赖进行管理：添加依赖，更新依赖，删除依赖。
<!-- more -->

最近在研究客户端包管理工具。[bower](http://bower.io/)是一个不错的包管理工具。

## 安装
bower是依赖node和npm的，使用npm来安装
```
npm install -g bower
```
同时，你也要保证安装了git。

### 对于git的安装以及要求
在windows下，安装git后，要将path中加入git的可执行文件所在地址。具体见http://bower.io/  的A note for Windows users。
或者window下一个比较简单的解决方式是，安装github，在github的命令行下运行bower。

## 使用
bower的用法和npm是基本一致的。熟悉npm的可以使用npm的方式来使用bower。

bower的依赖声明保存于`bower.json`（对应于npm的package.json）。
### 安装模块
```
bower install <package>#<version> [--save[-dev]][-g]
```
选项
* `--save` 将新安装的依赖写入`bower.json`的dependencies属性中
* `--save-dev` 将新安装的依赖写入`bower.json`的devDependencies属性中。devDependencies中里面放的依赖是开发环境中的使用的依赖，如测试，任务管理（grunt）之类的。
* `-g` 全局安装，这意味着你可以在命令行中使用，但不能在代码中使用。

#### 指定安装模块的地址
默认的安装模块的地址为`bower_components`文件夹。要指定安装模块的地址可以在项目根路径下创建`.bowerrc`文件，文件内容为
```
{
  "directory": "your_location"
}
``` 
注意，`.bowerrc`必须和`bower.json`在同一个文件夹下。


### 搜索模块
命令行中使用
```
bower search [<name>]
```
`name`是对`package-name`的模糊匹配。        
也可以在浏览器中打开 http://bower.io/search/ 。

### 更新模块
```
bower update <package-name>
```

### 卸载模块
```
bower uninstall <package-name>
```

### 显示该项目的依赖
```
bower ls
```

### 帮助
帮助概览
```
bower --help
```
某个命令的具体的帮助
```
bower help <command>
```

### 注册自己的模块
还没玩过
```
bower register <my-package-name> <git-endpoint>
```

下面，我还会写两篇文章
* bower与其他客户端包管理工具的比较
* 介绍[grunt-bowercopy](https://www.npmjs.org/package/grunt-bowercopy)：使用grunt-bowercopy将需要的文件从依赖中取出，放到指定位置

## 参考
* http://bower.io/
* https://github.com/bower/bower/wiki/FAQ


