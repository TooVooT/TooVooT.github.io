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

        初始化过程中可以指定默认的简单配置 可以手动选择复杂设置
        包括Babel TS Router Vuex CSS预处理 代码格式化 单元测试 E2E测试  
        使用类风格组件语法
        选择路由histroy设置
        选择less/
        选择ESlint+
        Mocha+Chai/Jest选择
        配置分散独立 还是放在一起
        是否保存此次配置模板
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


#### 静态资源处理
处理静态资源有两种方式
* 通过js导入 或者在template/css中通过相对路径导入 这类引用就将会被webpack打包处理
* 放置在public目录下面通过绝对路径导入 直接拷贝这类资源 不会被weback处理 

在JS CSS .Vue中使用相对路径`./`导入静态资源会被webpack包含到依赖图中。
`<img src="...">` `background:url()` `@import URL`都会被解析为一个模块  
`url(./image)`会被编译到`require(./image)`等 

> 如果URL为绝对路径 将保留不变
> 如果为`./`开头相对路径 将作为一个相对模块请求进行解释 且基于文件系统目录结构进行解析
> 如果~开头其后的任何内容都会作为一个模块请求被解析 可以引用node模块中的资源
> 如果@开头 作为一个模块请求 仅用于模板中 设置一个指向<projectRoot>/src的别名@

任何放在`public/`中的静态资源都会被简单复制 不会经过webpack处理 需要使用绝对路径引用

如果没有将应用部署在域名根部 需要为URL配置公共路径`publicPath`

当你需要在构建输出中指定一个文件的名字。
当你有上千个图片，需要动态引用它们的路径。
当有些库可能和 webpack 不兼容，这时你除了将其用一个独立的 script标签引入没有别的选择。
才考虑使用public文件夹

#### webpack配置
`webpack.conf.js`
vue-cli-service 暴露了 inspect 命令用于审查解析好的 webpack 配置。那个全局的 vue 可执行程序同样提供了 inspect 命令，这个命令只是简单的把 vue-cli-service inspect 代理到了你的项目中。

该命令会将解析出来的 webpack 配置、包括链式访问规则和插件的提示打印到 stdout                 

* development 模式用于 vue-cli-service serve
* production 模式用于 vue-cli-service build 和 vue-cli-service test:e2e
* test 模式用于 vue-cli-service test:unit
注意模式不同于 NODE_ENV，一个模式可以包含多个环境变量。也就是说，每个模式都会将 NODE_ENV 的值设置为模式的名称——比如在 development 模式下 NODE_ENV 的值会被设置为 "development"。

你可以通过为 .env 文件增加后缀来设置某个模式下特有的环境变量。比如，如果你在项目根目录创建一个名为 .env.development 的文件，那么在这个文件里声明过的变量就只会在 development 模式下被载入。
#### babel配置

#### TS配置

#### LESS/SASS配置
CSS预处理器 sass less stylus
css-loader会将编译后的css中的所有url()引用作为模块请求处理。可以使用相对路径 引用静态资源

```javascript
npm install -D sass-loader sass
npm install -D less-loader less
<style lang="sass">
</style>
```

#### ESLint配置

#### UnitTest配置

#### E2E配置


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



### 插件管理
`vue add xxx` 添加插件 
* `@vue/cli-service`
* `@vue/cli-plugin-babel`
* `@vue/cli-plugin-eslint`
* `@vue/cli-plugin-router`
* `@vue/cli-plugin-typescript`
* `@vue/cli-plugin-unit-test`
* `@vue/cli-plugin-vuex`

# 组件
组件由 `<template> <script> <style>`组成 
模板内部指定包含一个父节点 也就是只能由一个顶层`div`
其中的`<route-view`>为子路由视图 后面路由都显示在此处  当跳转某个路由的时候 该路由下面的组件插到此处显示  

脚本通常为ES6 内部包含数据data 生命周期函数等
data属性必须返回方法 

样式默认为全局的 添加`scoped`修改为局部作用 只在该组件上发挥作用
如果需要加载外部css需要`css-loader` 然后在style标签下import外部css文件 

可以在`template`与`script`之间import第三方插件 组件 图片 json文件等
main.js入口文件 加载vue框架 根组件实例 路由设置 Vue实例设置 



# 路由
SPA单页面应用路径管理器。其只有一个完整页面，加载页面时不会记载整个页面，只是更新某个指定容器中的组件，**核心是更新视图不重新请求页面**。

`vue-router`Vue官方路由插件 适合构建单页面应用. Vue的单页面应用基于路由与组件，路由用于设定访问路径且将访问呢路径和组件映射起来，通过路由之间的切换实现组件之间的切换.因为Vue多数构建单页面应用，即只有一个`index.html`页面，不用`a`标签进行连接跳转。

默认情况下的路由是模糊匹配的。
路由就是将对应的URL映射到唯一的组件。
创建路由之后需要将路由实例注入到根实例Vue中，从而使得整个应用都有路由功能。

    to可以指向字符串 默认将会渲染为<a>链接</a>
    也可以为to属性绑定JS表达式
    <router-link :to="home"></router-link>
    也可以通过对象指定绑定
    <router-link :to='{path:"home"}'></router-link>
    可以设置命名路由
    可以设置查询参数

    replace属性，表示当点击链接的时候会调用router.replace()而不是router.push()从而不会再history中留下历史记录
    append属性表示在当前相对路径前面添加路径
    tga属性指明想要将链接渲染为哪种标签，默认为a标签
    active-class设置链接激活的时候的使用的CSS的类名设置相关的样式
    exact-active-class精确匹配链接的时候才会激活对应的CSS类名

### router配置
路由`mode`有两种模式`hash``history`，其中hash模式会在url中添加#，history模式比较难看。

`hash`模式使用URL的hash模拟完整的URL，当URL改变的时候页面不会重新加载，hash(#)是页面的锚点，改变#其后的内容不会重新加载网页，出现在URL中但是不会出现在HTTP请求中，每改变一次＃后的内容都会在浏览器history中增加一个记录。通过锚点值的改变，根据不同的值　，渲染指定DOM位置的不同数据。

`histroy`模式的URL中自带#，`mode: 'history'`，其利用pushState() replaceState()方法记录浏览器记录栈。不过其需要后端配置支持，需要在服务器端添加一个覆盖所有情况`*`的候选资源，当匹配不到任何资源的时候返回同一个`index.html`页面。

**匹配URL与component的时候可以使用/指定具体的规则，也可以使用name指定对应关系**
### 动态路由匹配
把某种模式匹配到的所有路由全部映射到同一个组件，可以使用动态路径参数实现。动态路径参数以冒号`:`开头跟在`path`指定的路径之后，当匹配到该路由之后，URL传递进来的参数值将会传递给`this.$route.params`参数，可以在每个组件内部使用

    {path: '/user/:id', component: XXX}
    this.$route.params.id 获取路由中的id参数
    {path:'/user/:name/post/:id', component:XXX}
    this.$route.params.name 
    this.$route.params.id 

当不同路由匹配到同一个组件的时候，会重用该组件实例，两个路由渲染同一个组件，不会再调用新的声明周期钩子函数。

### 嵌套路由
要在嵌套的路由出口中渲染组件，需要设置在是定的路由中设置`children`属性
在原本的路由页面中为对应的子组件添加children指定符合条件的子路由设置，然后再在该组件中设置router_view出口将适配的子组件渲染到该路由出口  



## router-link
`<router-link to="/xxx></router-link>`是一个链接组件 设置导航链接，其中的`to=`指向目标地址.

router-link创建a标签实现导航链接，还可以通过router实例设置导航链接。
点击该链接之后，会立即把`to=`对应的路径值传递给`router.push()`，这个值可以是一个字符串，可以是一个描述目标位置的对象

    <!-- 字符串 -->
    <router-link to="home">Home</router-link>
    <!-- 渲染结果 -->
    <a href="home">Home</a>
    
    <!-- 使用 v-bind 的 JS 表达式 -->
    <router-link v-bind:to="'home'">Home</router-link>
    
    <!-- 不写 v-bind 也可以，就像绑定别的属性一样 -->
    <router-link :to="'home'">Home</router-link>
    
    <!-- 为to属性绑定一个对象 -->
    <router-link :to="{ path: 'home' }">Home</router-link>
    
    <!-- 使用命名的路由 指定查询参数-->
    < :to="{ name: 'user', params: { userId: 123 }}">User</  router-link>
    
    <!-- 带查询参数，下面的结果为 /register?plan=private -->
    <router-link :to="{ path: 'register', query: { plan: 'private' }}">Register</router-link>    

    当指定replace时候 就不会调用默认的Push() 
    append属性表示在当前的相对路径上添加基路径
    tag属性指定将链接渲染为何种标签 默认为a 
    exact表示精确匹配是否激活
    event声明触发导航的事件 

## router-view
`<router-view></router-view>`为路由出口，根据路由匹配的组件将会在此处渲染。
可以在一个页面内区分不同的router-view设置不同组件显示的区域

可以配合`<transition>`与`<keep-alive>`使用
可以通过`name`属性指定视图的名称方便嵌套视图的设计





## `this.route` 与 `this.$router`
通过在Vue实例中注入路由器，可以在任何组件内部使用`this.$router`访问路由器实例，通过`this.route`访问当前路由。


`this.$route`是路由信息对象，包含path hash query fullPath mathed name等路由信息参数 

    $route.path 字符串 对应当前路由的路径 总是解析为绝对路径
    $route.params 键值对对象包含了动态片段与全匹配片段
    $route.query 键值对对象表示URL查询参数 
    $route.hash 当前路径不带#的hash值
    $route.fullpath 完成解析之后的URL
    $route.matched 数组 包含当前匹配的路径中的所有片段对应的配置参数对象
    $route.name 当前路径名字

`this.$router`路由实例对象 `new VuewRouter()`创建的实例 包含了路由的跳转方法，钩子函数等

    $router.go(-1) 跳转到上一次浏览的页面
    $router.replace("/xxx")跳转到指定地址 不会添加Histroy记录 替换当前的历史记录 
    $router.push("/xx") 通过push进行跳转 会向history添加记录


在Vue实例内部可以使用`$router`访问路由实例，可以调用`this.$router.push()`直接导航到指定的URL，会在history中添加一个新的记录，可以回退到之前的URL。
实际上`<router-link>`被点击的时候总是在内部调用该方法，
`<router-lin :to=""><>` 等价于 `$router.push()` 一个是声明式一个是编程式


在组件中使用`$route`获取路由相关的参数会导致组件与路由的高度耦合，可以使用`props`进行路由解耦，直接传递进来相关的参数即可，这种方式方便组件重用

### vouter-view 命名
除了给路由指定名称之外还可以给视图指定名称，这样就可以同时显示多个视图，彼此区别，而不是只能有一个出口， 如果没有给其指定`name`属性那么默认为`default`.
`<router-view class="view-a" name="a"/>`

一个视图只需要一个组件进行渲染，因此对于同一个要进行渲染的路由，多个视图进行渲染就需要多个组件，此时需要使用`components`而不是单个组件的`component`

#### 嵌套命名视图
可以使用嵌套视图构造复杂应用
也就是在构造路由的时候`children` `component` `components`可以根据需要进行组合构造其那套视图。

    {
      path: '/settings',
      // 你也可以在顶级路由就配置命名视图
      component: UserSettings,
      children: [{
        path: 'emails',
        component: UserEmailsSubscriptions
      }, {
        path: 'profile',
        components: {
          default: UserProfile,
          helper: UserProfilePreview
        }
      }]
    }


### 重定向
重定向就是原本访问的URL直接替换为更改后重定向的的URL
重定向也可以使用routes配置，使用`redirect`指定定向的路径。
重定向的目标可以是一个命名的路由，也可以是一个方法其动态返回重定向的目标

别名是无论访问那一个匹配都似乎一样，使用`alias`设置别名路由路径

### 404页面
输入错误时的提示页面

    {
        path:'*',
        component: Error
    }
    Error.vue

### 导航守卫
阐述或者查询的改变并不会触发进入或者离开导航守卫
可以使用`router.beforeEach`注册全局前置守卫
同样可以设置全局后置守卫

    const router = new VueRouter({ ... })
    router.beforeEach((to, from, next) => {
      // ...
    })
    to 表示即将进入的路由对象 from表示导航即将离开的路由对象 next
    router.afterEach((to, from) => {
      // ...
    })

## 过渡动效
可以使用`<transition>`标签直接给`<router-view>`添加动态过渡效果 

## 数据获取
进入某个路由之后需要从服务器拉取数据，可以有两种方式实现。
* 导航完成之后获取
  先完成导航，然后再接下来的寿命周期钩子中获取数据，在数据获取期间显示加载中。
  马上导航和渲染组件，然后再组件中的`created`钩子中获取数据，在数据获取到之前显示Loading状态。

* 导航完成之前获取 
  导航完成前，在路由进入的守卫中获取数据，在数据获取成功之后执行导航。
  在导航转入新的路由之前获取数据 在`beforeRouteEnter`获取数据，获取成功之后调用next方法

## 滚动行为

 
# 状态管理
## vuex配置


# Vue原理
## 插件
为vue添加全局功能，可以添加全局方法或者prototype，可以添加全局资源，添加实例方法
vue可以`import`直接引入相关库/组件，有的需要`Vue.use()`有的需要`Vue.prototype.$xxx=xxx`.

    import axios from 'axios'
    Vue.prototype.$axios = axios
    全局注册方法 在之后的文件中可以直接通过$axios使用axios
    因为axios没有install方法

`Vue.use()`全局方法使用插件，会自动阻止多次注册相同的插件，需要在`new Vue()`之前完成。必须传入一个对象或者函数对象，如果是`Object`其至少有一个`install`方法.如果是`Function`就将其当作`install`方法。`Vue.use()`会执行install方法，该函数执行传入的第一个参数为`Vue`其他参数为传递的参数。

# Vue UI 框架

* Vuetify
* `Element Vue`
* AntDesign Vue
* Bootstrap Vue
* iview

维护可持续性 扩展性 稳定性 功能性 

## Element UI
* 1构建项目添加库
`npm install element-ui -S` 安装且添加依赖
* 2按照element插件构造element项目
`vue add element`添加ele插件 

引入整个项目：

    import ElementUI from 'element-ui';
    import 'element-ui/lib/theme-chalk/index.css';
    Vue.use(ElementUI);

引入部分组件：

    npm install babel-plugin-component -D
    .babelrc
    {
      "presets": [["es2015", { "modules": false }]],
      "plugins": [
        [
          "component",
          {
            "libraryName": "element-ui",
            "styleLibraryName": "theme-chalk"
          }
        ]
      ]
    }

    import {Dialog, Button} from 'element-ui'
    Vue.use(Dialog);
    Vue.use(Button)
    Vue.prototype.$message = Message 

ELe支持众多组件 可以单独按需引入 可以全部引入。
Element的theme-chalk使用scss编写，可以直接定义scss文件直接import使用

### 基本组件
布局 容器 颜色 字体 边框 图标 按钮 链接

#### 边框设计
基础颜色为蓝色`#409EFF`
字体设置包括字号、字体等
边框样式可以选择实线、虚线
圆角`border-radius:0/2/4px`
投影设置 基础投影`box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04)`浅色投影` box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1)`

图标可以直接使用`<i class="el-icon-iconName">图标名称</i>`添加
element内部支持大量图标，可以直接使用

### 导航
菜单 标签页 面包屑 页头 下拉菜单那 步骤


### 表单
单选 多选 输入 计数 选择 开关 滑块 日期 上传 
### 数据展示
表格 标签 进图条 树形控件 分页 标记 头像 

### 提示
警告 加载 通知

### 其他
对话框 文字提示 弹出 气泡 卡片 折叠面板 时间线 日历 分割线
图片 无限滚动 抽屉

### 特效 