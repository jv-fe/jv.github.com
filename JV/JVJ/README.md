##YEOMAN

Yeoman 是由三个工具的组成：YO、GRUNT、BOWER

YO：Yeoman核心工具，项目工程依赖目录和文件生成工具，项目生产环境和编译环境生成工具。

GRUNT：前端构建工具，jQuery就是使用这个工具打包的。

BOWER：Web 开发的包管理器，概念上类似 npm，npm 专注于 NodeJs 模块，而 bower 专注于 CSS、JavaScript、图像等前端相关内容的管理。

##安装Yeoman

    npm install -g yo 

默认相应的把yo grunt bower都安装好了，它将自动安装Grunt和Bower。

安装YO生成器，这样可以自己编写生成器

npm install -g generator-generator

`当前安装版本（2014.09.17）`

yo -v 1.2.1

grunt -version grunt-cli 0.1.13

bower -v 1.3.9

##配置grunt

进入JV/JVJ目录

配置package.json文件,(`需要部署的还需要配置Gruntfile.js`)


```javascript
{
  "name": "jvj",
  "version": "0.1.0",
  "repository": {
    "type": "git",
    "url": "https://github.com/qinliang760/qinliang760.github.com/JV/JVJ.git"
  },  
  "path":{
      "tmpl":["E:/myfile/git_new/qinliang760.github.com/JV/JVJ/jv-plugins"],
    "root":"E:/myfile/git_new/qinliang760.github.com/JV/JVJ",
    "cssRoot":"E:/myfile/git_new/qinliang760.github.com/JV/JVJ/jv-plugins",
    "jsRoot":"E:/myfile/git_new/qinliang760.github.com/JV/JVJ/jv-plugins"
  },
  "devDependencies": {
    "grunt": "~0.4.5",
    "grunt-usemin": "~2.0.1",
    "grunt-contrib-concat": "~0.3.0",
    "grunt-contrib-uglify": "~0.4.0",
    "grunt-contrib-cssmin": "~0.9.0",
    "grunt-contrib-htmlmin": "~0.3.0",
    "grunt-contrib-watch": "~0.6.1",
    "grunt-contrib-imagemin": "~0.8.0",
    "grunt-contrib-jshint": "~0.10.0",
    "grunt-contrib-connect": "~0.8.0",
    
    "chalk": "~0.4.0",
    "compare-version": "~0.1.0",
    "multiline": "^0.3.4",
    "pkg-name": "~0.1.0",
    "yeoman-generator": "~0.16.0"    
  }
}
```
安装依赖

    npm install

安装的依赖包会自动放在node_modules目录


##bower的使用

    cache:bower缓存管理
    help:显示Bower命令的帮助信息
    home:通过浏览器打开一个包的github发布页
    info:查看包的信息
    init:创建bower.json文件
    install:安装包到项目
    link:在本地bower库建立一个项目链接
    list:列出项目已安装的包
    lookup:根据包名查询包的URL
    prune:删除项目无关的包
    register:注册一个包
    search:搜索包
    update:更新项目的包
    uninstall:删除项目的包

##准备开发一个jquery插件
    yo jvj



