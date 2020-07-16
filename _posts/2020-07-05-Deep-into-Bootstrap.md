---
layout: post
title: Bootstrap及其UI样式
featured-image: 
---

# 布局设计、UI设计与样式设计
* ElementUI
* Bootstrap
  * Bootflat
  * BootPress
  * Bootswatch
  * FlatUIFree
* LayUI
* AntDesign
* JQuery EasyUI
* WeUI
* SemanticUI



## LESS/Sass
CSS扩展语言，增加了一些使用扩展。
### Node.js中使用
使用命令行工具将`.less`文件编译为`.css`文件
`npm install less -g`
`lessc -v`
`lessc [option] <source.less> [destination.css]`
### 浏览器中使用
可以再浏览器中使用`less`但是为了性能建议预编译。

    <link rel="stylesheet/less" type="text/css" href="styles.less"/>
    <script src="less.js" type="text/javascript"><script>
可以在使用的时候指定相关的设置，预设相关参数。

    <script src="less.js" data-poll="1000" data-relative-urls="false"></script>
    <link data-dump-line-numbers="all" data-global-vars='{ "myvar": "#ddffee", "mystr": "\"quoted\"" }' rel="stylesheet/less" type="text/css" href="less/styles.less">
浏览器中使用时确保在脚本加载之前加载样式表
### 概览
    变量
    @width: 10px;
    @height: @width + 10px;
    #header {
        width: @width;
        height: @height;
    }
    
    混合是将一组属性从一个规则集合包含到另外一个规则集合中的方法，直接使用现有的一组样式
    .bordered {
        border-top: dotted 1px black;
        border-bottom: solid 1px balck;
    } 
    #menu a{
        color: red;
        .bordered(); 直接包含已有属性样式集合
    }

    嵌套选择添加样式
    #header {
        color: red;
        .navigation {
            font-size: 12px;
        }
        .logo {
            width: 300px;
        }
    }

    @规则可以与选择器以相同的方式嵌套，@规则会被放到前面，其他元素一次后移
    .component {
        width: 300px;
        @media (min-width: 768px) {
            width: 600px;
            @media  (min-resolution: 192dpi) {
                background-image: url(/img/retina2x.png);
            }
        }
        @media (min-width: 1280px) {
            width: 800px;
        }
    }

    运算符可以对任何数字、颜色、变量进行运算
    所有操作数都会被转换成相同的单位，乘除不进行转换 

    转义允许使用任何内容进行原样输出~"..."
    可以导入`.less`文件和.css文件
    @import "library" 默认省略.less后缀名称
    @import  "type.css"

    Less支持一些进行默认操作的函数


## Bootstrap
支持Sass变量、Mixin、响应式栅格系统、自带组件
可以下载源文件和预编译文件

    Bootstrap CSS
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.5.0/dist/css/bootstrap.min.css" integrity="sha384-9aIt2nRpC12Uk9gS9baDl411NQApFmC26EwAOH8WgZl5MYYxFfc+NcPb1dKGj7Sk" crossorigin="anonymous">
    Bootstrap JS都依赖jQuery Popper
    <script src="https://cdn.jsdelivr.net/npm/jquery@3.5.1/dist/jquery.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.0/dist/js/bootstrap.min.js" integrity="sha384-OgVRvuATP1z7JjHLkuOU7Xw704+h835Lr+6QL9UvYjZE3Ipu6Tp75j7Bh/kR0JKI" crossorigin="anonymous"></script>

确保遵循最新的开发标准

     Bootstrap先天针对移动设备，为了确保针对所有设备进行组件的缩小与放大，进行正确的渲染
     <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

### Layout布局
每个元素仅能使用一个数据属性
* 概览
  包含包装容器 强大的网格系统 容易操纵的媒体对象 响应式实体类
  容器是最基本的布局元素，容器用来包含、衬垫等元素，容器可以被嵌套。
  `.container`为每一个响应式断点设置`max-width` 固定宽度
  `.container-fluid`为所有的断点设置`width:100%` 占据全部宽度
  `.container-{}` 直至特定的断点设置`width:100%`
  
根据屏幕响应式布局：

    // Small devices (landscape phones, 576px and up)
    @media (min-width: 576px) { ... }

    // Medium devices (tablets, 768px and up)
    @media (min-width: 768px) { ... }

    // Large devices (desktops, 992px and up)
    @media (min-width: 992px) { ... }

    // Extra large devices (large desktops, 1200px and up)
    @media (min-width: 1200px) { ... }

    // Extra small devices (portrait phones, less than 576px)
    @media (max-width: 575.98px) { ... }

    // Small devices (landscape phones, 576px and up)
    @media (min-width: 576px) and (max-width: 767.98px) { ... }

    // Medium devices (tablets, 768px and up)
    @media (min-width: 768px) and (max-width: 991.98px) { ... }

    // Large devices (desktops, 992px and up)
    @media (min-width: 992px) and (max-width: 1199.98px) { ... }

    // Extra large devices (large desktops, 1200px and up)
    @media (min-width: 1200px) { ... }

* Grid栅格系统
  实用一些列的容器、行、列来布局对齐内容，实用flexbox创建
* 
### Content内容
* Reboot
* Typography
* Code
* Images
* Tables
* Figures
### Components组件
* Alerts
* Badge
* Breadcrumb
* Buttons
* ButtonGroup
* Card
* Carousel
* Collapse
* Dropdowns
* Forms
* InputGroup
* JumpBotron
* ListGroup
* MdeiaObject
* Modal
* Navs
* NavBar
* Pagination
* Popovers
* Progress
* Scrollspy
* Spinners
* Toasts
* Toopyips
  
### Utilities实用工具
* Borders边框
* Clearfix
* Close Icon
* Colors
* Display
* Embed
* Flex
* Float
* Image Replacement
* Interactions
* Overflow
* POsition
* ScreenReaders
* Shadow
* Sizing
* Spacing
* StretchedLink
* Text
* VerticalALign
* Visibility

### Icons图标库
图标全部为SVG文件，默认`width` `height`全部为`1em`
* 直接使用svg标签内嵌在html中
* 使用`<use>`插入到svg标签中
* 作为外部文件引入到`<img>`标签中
* 在CSS文件中使用
<svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-app" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" d="M11 2H5a3 3 0 0 0-3 3v6a3 3 0 0 0 3 3h6a3 3 0 0 0 3-3V5a3 3 0 0 0-3-3zM5 1a4 4 0 0 0-4 4v6a4 4 0 0 0 4 4h6a4 4 0 0 0 4-4V5a4 4 0 0 0-4-4H5z"/>
</svg>

