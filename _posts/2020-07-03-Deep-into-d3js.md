

[Toc]
## SVG
可所方式矢量图形SVG使用XML定义图像，浏览器使用每一个点与线打印而不是像素填充。
svg标记中包含基本的标签与CSS属性描述

        <svg width="10" height="10">
        <rect x="0" y="0" width="10" height="10" fill="blue" />
        </svg>
最常用的标签
> `text` 创建文本元素
> `circle/rect/line`创建特定图形
> `path` 两点之间连线
> `textpath` 两点之间创建路径并且创建一个链接的文本元素
> `polygon` 允许创建任意类型的多边形 属性`points=`接受一系列x y坐标,`fill-rule`指定填充规则
> `polyline`多点连接曲线
> `g` 单独的一组元素 对元素进行分组 可以指定`id=`区分每一组

坐标从绘图区域左上角开始`(0,0)` 从左到右x从上到下y
任何SVG元素都可以接受`style`属性 类似HTML标签　
`style="fill:red"`指定颜色
`fill-opacity`，背景颜色不透明度
`stroke`，定义边框颜色
`stroke-width`，设置边框宽度

如果可以与 SVG 交互（SVG 在 HTML 中是内联的），则可以使用 JavaScript 更改任何 SVG 属性

您可以使用 CSS 更改 SVG 图像的任何样式。SVG 属性可以很容易地在 CSS中 被覆盖，并且它们比 CSS 具有更低的优先级。它们的行为不像具有更高优先级的内联 CSS
### path
最强大与最复杂的
属性`d=`表示方向命令 以特定的方向名称首字母与坐标组成
`M` 表示移动，它接受一组 x，y 坐标
`L` 表示直线将绘制到它接受一组 x，y
`H` 是一条水平线，它只接受 x 坐标
`V` 是一条垂直线，它只接受 y 坐标
`Z` 表示关闭路径，并将其放回起始位置
`A` 表示 Arch，它自己需要一个完整的教程
`Q` 是一条二次 Bezier 曲线，同样，它自己也需要一个完整的教程

## D3js
`D3`可以将数据绑定到选择的`Dom`树上，然后将该数据设置选择`Dom`对象的属性
基于`CSS`选择器，选择网页中的一个或者多个元素。
`select()`匹配给定的CSS选择器 仅选择一个`Dom`元素，如果有多个匹配元素则仅选择一个元素
`selectAll()`通过匹配给定的CSS选择器选择所有的合适的`Dom`元素
* 通过HTML标记选择默认的元素 `p` `div` `body`
* 通过HTML元素`class`选择 `.class`
* 通过HTML元素`id`选择 `#id`

`append()`将新元素作为当前选择元素的最后一个子元素添加，可以修改元素的样式、属性、文本内容
`text()`设置所选择的元素的内容 
`.html()`设置所选择的元素的HTML内容
`.attr()`添加或者更新所选元素的属性
`.style()`设置所选元素的样式属性
`.classed()`专门设置HTML元素的`class`属性

选择元素 添加数据 使用数据修改元素属性
数据连接的目的是使用给定的数据集合映射现有文档元素，根据给定的数据集创建文档的虚拟表示，并且提供使用虚拟表示的方法。
`.enter()`提供对剩余数据的元素，未映射到现有元素的数据 输出之前没有图形元素的数据集项 添加不足Dom元素
`.append("p")`从相应元素创建新元素
`.exit()`从数据集中动态删除数据项 输出不再存在数据的图形元素集 移除多余Dom
`.remove()`删除元素

`.data()` 将数据集分配给HTML选择的元素集合 
`.datum()`为HTML元素中的单个元素设置值 
设置完可以重新选择 重新设置 重新更新
设置的匿名函数参数一个是数据项对应数值`d`，一个是data中数据的索引`i` `this`表示当前Dom元素的引用
## 操作步骤
* 1 数据获取 `csv` `json` `Array` 
* 2 界面尺寸 `width` `height` `margin`
* 3 选择元素 `body` 
* 4 添加svg面板
* 5 坐标 坐标组 比例尺 坐标 添加
* 6 绘图 
## API
可以单独获取某一个模块 也可 获取整个库 
主要分为 数据结构模块 布局模块 基本配置模块 动作事件模块 
#### Fetches 数据获取
* `d3.csv()`
* `d3.json()`
* `d3.text()`
* `d3.image()`
* `d3.buffer()`
* `d3.html()`
* `d3.svg()`
#### Selection 选择元素
* `d3.event` 访问用于交互的当前用户事件
* `d3.mouse` 获取相对于指定容器的鼠标位置
* `d3.select` 从当前文档中选择一个元素
* `d3.selectAll` 从当前文档总选择多个元素
* `d3.selction` 增强选择器原型
* `d3.touch` 获取相对指定容器的单点触摸位置
针对选择的对象进行操作
* `selection.append` 创建并且添加一个对象
* `selection.attr` 获取或者设置属性的值
* `selection.call` 为当前选择调用一个函数
* `selection.classed` 添加或者移除一个CSS类
* `selection.data` 计算相关连接时取得或者设置一组元素的数据
* `.datum`取得或者设置某个元素的连接 不必设置连接
* `.each` 为每一个选中的元素调用函数
* `.empty`选择为空则返回true
* `.enter`为缺失的元素返回占位符
* `.exit`返回不需要的元素
* `.filter`基于数据过滤选择
* `html`取得或者设置innerHTML内容
* `insert`在已经存在的元素之前插入一个元素
* `interrupt`如果有过渡效果立即终端
* `node`返回选择中的第一个节点
* `on`交互式添加或者移除事件监听器
* `order`重新排列文档元素
* `property`取得或者设置行内属性
* `remove`移除当前元素
* `select`为每个选中的选择再选择额一个后代元素
* `selectAll`每个选中的元素选择多个后代元素
* `size`返回选择的元素数
* `sort` 基于数据排列文档中的元素
* `text` 取得或者设置文本内容
* `tansition` 在选中的元素上开启过渡
  
#### Axes 轴
#### Colors 颜色
#### Random 
#### Arrays 数组
#### Collections 组合
#### Hierarchy 层次
计算层次布局之前需要一个根节点，如果`JSON`数据可以直接使用，其已经具有层次。
* `d3.hierarchy(data, [children])` 指定的数据必须有一个表示根节点的对象
* `d3.pack()`打包布局
* `d3.partition()`邻接图 分区图
* `d3.treemap()`
* `de.tree()`
* `d3.cluster()`
#### Scales
#### Paths 路径
#### Brushes 选择区域
#### Shapes 基本图形
* `arc()`
* `line()`
* `pie()`
* `curve()`
* `areas()`
* `links()`
#### Geography 地理
#### Forces 力图
#### Chords 弦图
#### Contours
#### Dispatches
#### Easings 平滑过渡
#### Interpolators 插值
#### Polygon 二维多边形
#### Quardtrees 四叉树
#### Time
#### Transitions动画过度
#### Zooming 缩放
#### Dragging  拖拽



## 常用布局
* bubble气泡图
* packing 打包图
* bunding 捆图
* force 力导向图
* chord弦图、
* tree 树状图、
* cluster集群
* histogram直方图
* partition分区图
* stack 堆栈图
* treemap矩阵树图
* hierarchy层级图

