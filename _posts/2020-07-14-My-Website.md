---
layout: post
catergories: posts
title: Web Architect
subtitle:  项目架构与设计
featured-image:  /images/bing.lylares.com-2020-06-01-1080p_min_min.jpg
tags: [Architect] 
date-string: July 15, 2020
---

# 建站架构总结
## Website Desccription
    
    网站目的：交互式展示结果 
    前端：展示各种图形、图标、可视化结果
        交互式展示 算法/模型 结果

    架构：负载均衡 反向代理 

    后端：计算密集型 数据可视化 算法结果  
        实时运算 
        算法 模型 

    数据资源：图数据库 时间序列数据库 关系数据库 

### 应用架构
需求描述：
    盘前-->盘中-->盘后
    
    盘前、盘后：
    逐日分析
    展示各种算法的结果
    给出交易策略建议

    实时盘中：
    分析跟踪分析市场 评估市场表现 寻找交易机会

    个股分析 
    组合分析
    
数据获取：
    爬虫清洗
    
### 技术架构

* 前端UI设计
  * `Vue`
  * `Bootstrap`
  * `Element`
  * `AntDesign`
  * `JQuery`
  * `D3.js`
* 反向代理负载均衡
  * `Nginx`
* 后端功能支持
  * `SpringBoot`
  * `Django`
  * `Node.js`
* 业务内容
  * 股票市场
  * 基金市场
  * 债券市场
  * 衍生品市场
  * 大宗商品
  * 外汇、贵金属、加密货币...
* 核心模型、算法
  * ML
  * TimeSeris
  * DL
  * 回测
  * 
* 数据库
    * `Mysql`
    * `Neo4j`
    * `Mongodb`
    * `Infludb`
    * `ElasticSearch`
    * `Redis`


# 前端项目创建
`vue` `vue-router` `vuex`
`elementui` `bootstrap`
`axios` 

