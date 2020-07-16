---
layout: post
catergories: posts
title: Deep into Vue 
subtitle:  关于Vue的原理与使用 
featured-image:  /images/bing.lylares.com-2020-07-13-1080p_min.jpg
tags: [Vue] 
date-string: July 16, 2020
---

# Vue 基础
[TOC]
清理所有不必要的局部安装包 
只保留必要的全局安装包 

    D:\Node\node_global\node_modules
    D:\Node\node_global\全局命令 
        npm npx
        less sass 
        vue vue-cli-service
        vue-init  vue-list
        webpack
    +-- npm@6.14.6
    +-- bootstrap@5.0.0-alpha1
    +-- bootstrap-icons@1.0.0-alpha5
    +-- express@4.17.1
    +-- sass@1.26.9
    +-- less@3.11.3
    +-- popper.js@1.16.0
    +-- react@16.13.1
    +-- react-dom@16.13.1
    `-- webpack@4.43.0
    脚手架新版与旧版
    +-- vue-cli@2.9.6
    +-- @vue/cli@4.4.6
    +-- @vue/cli-service@4.4.6
    +-- @vue/cli-service-global@4.4.6
    Vue 最新稳定版
    +-- vue@2.6.11
    生态系统
    vue
    vue-router
    vuex
    vue-cli
    vue-loader
    vue-server-render
    vue-devtools

## 脚手架与项目配置
`npm view vue` 版本2.6.11
`vue --version` 查看 版本 4.4.6
`vue -V` 新脚手架版本4.4.6
旧版本`vue-cli` 新版本`@vue/cli`
卸载旧版本`npm uninstall vue-cli -g`
安装新版本`npm install -g @vue/cli`

`@vue/cli`是一个全局安装的`npm`包，终端命令`vue`.
`vue create`创建项目 `vue serve`创建想法原型 `vue ui`图像化管理界面. 
一套定义好的插件与配置一般包括`babel``eslint`等. 

`vue/cli-service`是开发环境依赖项，局部安装在具体的项目中，其构建基于`webpack`与`web-dev-server`上.

`vue/cli-plugin-`插件可以提供可选功能工具包，包括`babel/ts`转译、`eslint`集成、`unit test` `end-to-end test`等.


流程：脚手架——>按模板初始化项目——>npm run xxx——>启动编译服务

### `@vue/cli`使用
**npm install -g @vue/cli**
**`vue ui`** 启动并且打开`vue-cli ui`手动配置项目 管理插件
**`vue create hello-world`** 创建一个`vue-cli-service`支持的项目 vue-cli3初始化方式
`vue serve` 快速对.vue文件进行原型开发 在开发模式下零配置启动.js/.vue服务器。以开发模式serve一个.js/,vue文件
`vue build` 以产品模式编译.js/.vue文件。生产环境下零配置构建一个.js/.vue文件
`vue add` 添加插件
`vue config` 检查或者修改配置

vue/cli使用了基于插件的架构，项目的package.json中项目依赖都是`@vue/cli-plugin-`.插件可以修改webpack内部配置，可以向`vue-cli-service`注入命令.可以使用`vue ui`插入或者管理插件.



### `vue-cli`使用 
**npm install -g vue-cli**
**`vue init`** 生成一个项目 vue-cli2初始化方式
`vue init <template-name> <project-name>` 按照指定模板初始化项目 

Vue CLI >= 3 和旧版使用了相同的 vue 命令，所以 Vue CLI 2 (vue-cli) 被覆盖了。如果你仍然需要使用旧版本的 vue init 功能，你可以全局安装一个桥接工具：
`npm install -g @vue/cli-init`



### `vue-cli-service`
`@vue/cli-service`安装了一个`vue-cli-service`的命令.

`npm run dev`2.0启动项目
`npm run serve` 3.0版本启动项目
`npm run build`打包项目 将打包放入`dist`文件夹 
`vue-cli-server serve/build/inspect` 启动服务器/编译产品
`npm run serve/build/`

### 项目配置
ES6 ES5代码转换 
less scss预处理器
font image静态资源解析
js css等文件压缩 
区别开发环境与生产环境
每次打包删除上次打包记录 
项目热更新与懒加载
**进入哪一个目录 npm的局部命令路径就是该目录下的node_modules**
**全局路径唯一 局部路径随路径改变**
`npm list --depth=0`
`npm run dev`脚手架2动项目
`npm run build`打包项目 将打包放入`dist`文件夹 
`npm install xxx@1.2.3`指定版本号
`npm uninstall xxx --save-dev`删除模块
`npm view xxx`查看指定包`package.json`注册信息
`npm update xxx -g`更新全局包
`npm view xx dependencies` 查看包的依赖关系
`npm outdated` 检查是否过时 
`npm root`查看本地安装路径  `npm root -g`查看全局安装路径
`npm cache clean`清除缓存 
`npm start/stop/restart/test  xxx`启动模块
`npm version`查看所有包的版本信息


#### `package.json`
描述项目相关信息

    {
        "name":"项目名称",
        "version":"版本号",
        "description":"",
        "author":"",
        "scripts":{
            运行脚本命令的npm命令缩写
            "dev":""  npm run dev
            "start":"" == npm run start == npm start == node index.js
            "unit":"" npm run unit
            "test":"" npm run test
            :build":"" == npm run build == npm build == node build.js

        },
        "dependencies":{
            项目运行所需要的依赖

        },
        "devDependencies":{
            项目开发所需模块
            ~1.2.3 只安装1.2.x的最新版本 不能低于1.2.3 不会安装1.3.x
            ^1.2.3 安装1.x.x的最新版本 不能低于1.2.3 不会安装2.x.x
            latest 安装最新版本

        },
        "engines":{
            "node":">=",
            "npm":">="
        }
        "browserslist":{
            
        }
    }

直接本地安装模块会安装到本地`node_modules`
`npm install xx --save`添加到依赖项
`npm install xx --save-dev`添加到开发依赖项 
`vue init template xxx` 以`webpack`初始化一个vue项目

    Project/
        build 构建生产版本
            build.js 即packsge.json中的build对应的文件
            check-version.js检测node npm版本实现版本依赖
            utils.js 处理css文件
            vue-loader.conf.js 解析.vue文件将其转换为js模块
            webpack.base.conf.js 开发/生产共同使用的基础配置
            webpack.dev.conf.js 开发配置文件
            webpack.prod.conf.js 生产配置文件
        config webpack文件夹 为build服务
            dev.env.js 开发配置
            index.js
            prod.env.js 发布配置
            test.env.js
        dist
        node_modules
        src源代码
            assets 静态资源
            components组件
            router路由
                index.js实现路由跳转
            views主要页面
            App.vue 项目主视图
            main.js 项目入口 初始化vue实例
        static静态资源文件
        test
        .babelrc babel配置文件
        .editorconfig 编辑器配置文件
        index.html 首页文件  将组件插入该页面中

页面关系：
`index.html`首页

#### `webpack.conf.js`




### ES6中的import 与 export
ES6的模块化语法

    指定导出的名称：
    export {sqrt, exp, diag}
    import {sqrt, exp, diag} from "./lib"

    export function sqrt(x){}
    import {sqrt} from "./lib"

    给导入添加别名
    import {A as A1} from "./lib2.js"
    import {A as A2} from "./lib2.js"

    导入命名空间中的所有对象：
    import * as Lib from "./lib.js"

    一个文件只能有一个默认导出
    不能将var let const用于默认导出 只能是function {} class等对象
    导入默认导出的内容不需要加括号
    export default function(){}
    import ABC from "lib"

    export default {
        sqrt(){},
        log(){}，
        exp(){},
    }
    import Obj from "lib.js"
    Obj.sqrt()

### CommonJS与AMD
Node.js部分支持CMD

    每一个文件就是一个模块 有自己的作用域 文件内部函数变量类都是私有的 其他文件不可见
    如果想要在多个文件之间分享变量 需要将其添加到global对象的属性上

    CMD规定每个文件内容 module表示当前模块 是一个对象 其exports属性是对外的接口 加载某个模块其实就是加载该modules.exports属性
    所有代码运行在块级作用域 不会污染全局作用域
    模块多次加载 但是只会在第一次加载时候运行一次 然后就是读取缓存 要想再次加载 必须清除缓存
    模块加载顺序按照其在文件中出现的顺序  

    每个模块内部 exports指向module.exports 
    不能直接将exports指向一个值 这样将会切断exports与module.exports的联系 
    只能给exports.a 添加属性指向来实现导出
    尽量只使用module.exports 

    requrie的功能是读取并且执行一个js文件 但后返回该模块导出的对象 
    加载文件默认文件后缀为`.js` 
    /开头表示绝对路径  ./开头表示相对路径 
    直接指定名称表示加载默认核心模块或者全局模块
    module.id 模块标识符
    module.filename 模块文件名  
    module.parent 模块的父模块
    module.exports 输出值 

    module.exports.a = 123
    module.exports.sqrt = function (){}
    var obj = require()
    obj.a 
    obj.sqrt()

    exports与module.exports在node执行文件时指向同一个内存区域{}
    module.exports/exports
    require导入的内容是module.exports指向的内容并不是exports指向的内容
    exports只是module.exports的一个引用 

    module.exports = {}
    var obj = require("./lib.js")
    exports.sqrt = function (){}

    require exports module _dirname __filename都是模块对象

    CMD是同步加载模块的 必须按照顺序加载模块 AMD是异步加载的模块的
    一般服务器采用CMD规范 浏览器采用AMD规范
    AMD使用define定义模块


# 组件与路由

`vue-router`Vue官方路由插件 适合构建单页面应用. Vue的单页面应用基于路由与组件，路由用于设定访问路径且将访问呢路径和组件映射起来，通过路由之间的切换实现组件之间的切换.因为Vue多数构建单页面应用，即只有一个`index.html`页面，不用`a`标签进行连接跳转。

# 状态管理

# Vue UI 框架

* Vuetify
* `Element Vue`
* AntDesign Vue
* Bootstrap Vue
* iview