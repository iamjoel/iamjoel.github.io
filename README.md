## iamjoel.github.io
管理博客内容的源码(.md)与配置

### 博客皮肤 [pacman](https://github.com/A-limon/pacman)

皮肤安装方式    
1. git clone https://github.com/A-limon/pacman.git themes/pacman
1. 将上面下载的皮肤放到themes文件夹下
1. 修改`/themes/pacman/_config.yml`

### 内容映射
* 博客内容的源码 _post/ -> source/_post/
* 配置文件
    * config/package.json -> package.json
    * config/Gruntfile.js -> Gruntfile.js
    * config/_config.yml -> _config.yml
* 皮肤 theme/_config.yml -> themes/pacman/_config.yml