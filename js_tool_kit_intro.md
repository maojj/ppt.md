#JSToolKit 介绍


##主要内容
1. JSToolKit是什么
1. 需求及产生过程
    * 原始出发点
    * 如何解决?
    * 重构
1. 特点
    * 模块化
    * 分层
    * core
    * web
    * jq
    * mvc
    * 自动化
1. 应用
    * Editor
    * htmlParser.js
    * 组合使用
1. 感想
    * 自动化单元测试很重要

###JSToolKit是什么
一个高度分层的js工具库, 强通用性和高扩展性

###需求及产生过程

####原始出发点
1. 编辑器需要改进
    * 输入输出内容系统过滤
    * word粘贴时内容转换
    * 性能
    * bugs
1. WebClipper输入内容系统过滤
1. 编辑器开发中遇到的问题
    * jquery黑盒, e.g. $('selector', article) 触发DOMSubTreeModify
    * jquery 对DocumentFragment不能良好操作
    * querySelector(), querySelectorAll() 不能支持复杂选择器, e.g. querySelector('[src=http://xxxxx]')

####如何解决?
要满足以上需求, 需要做以下工作
1. htmlParse.js 作为独立工程
    * 编辑器输入输出系统过滤
    * WebClipper输入系统过滤
    * 其他的输入源
1. 编辑器过滤器细化管理
    * 性能
1. 编辑器全新的粘贴流程
    * 性能
    * PC端word粘贴时内容转换
    * 规避一部分bug
1. 编辑器中的DOM 操作
    * jquery黑盒
    * 修复原始某些api bug

####重构
1. 要完成以上工作以满足需求, 编辑器改动非常大
1. 尽可能复用已有的编辑器模块, 比如PC端的编辑器按钮拦
1. 无底层基础库支持, 重构痛苦

###JSToolKit特点

####高度分层
1. 模块化 -> seajs
1. [core](https://dev.corp.youdao.com/svn/outfox/products/YNote/JSToolKit/JSToolKit-core)
1. [web](https://dev.corp.youdao.com/svn/outfox/products/YNote/JSToolKit/JSToolKit-web)
1. [jq](https://dev.corp.youdao.com/svn/outfox/products/YNote/JSToolKit/JSToolKit-jq)
1. [mvc](https://dev.corp.youdao.com/svn/outfox/products/YNote/JSToolKit/JSToolKit-mvc)
1. 依赖关系
```
[-- web --] [-- jq --] [-- mvc --]
[------------ core --------------]
```

####core
1. underscore.js
1. string 常用处理
    * 借鉴[underscore.string](http://epeli.github.io/underscore.string/)
1. console
    * window.DEBUG
    * console.DEBUG
    * console.log()
    * console.warn()
    * console.error()
    * DEBUG模式下输出信息
    * 非DEBUG模式下为空函数
1. events
    * 自定义事件on()/off()/trigger()
    * 借鉴Backbone.Event
1. Class
    * 类似Backbone.View, 但更抽象
1. 强通用性
    * 与DOM无关

####web
1. dom: DOM 操作
    * query.one()/query.all() 替代 querySelector(), querySelectorAll(), 并增强
    * insert, insertHTML....
1. bom
    * userAgent
1. event: DOM事件处理相关
1. ani: 动画
1. 兼容IE6+, Chrome, Firefox, Opera
    * 与jQuery 1.x 保持一致, see http://jquery.com/browser-support/

####jq/mvc
1. jquery/backbone 封装

####自动化
1. gruntjs 打包
1. QUnit 单元测试

##应用
1. Editor重构
1. htmlParser.js
1. 高度分层便于组合使用
    * core
    * core + web
    * core + jq
    * core + jq + mvc

##感想
1. 自动化单元测试很重要










