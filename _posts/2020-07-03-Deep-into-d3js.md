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

## 教程
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



## 布局
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

