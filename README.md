# 前端开发总结与分享

进入宏电已有一个多月，开发过程中自然会遇到一些问题和痛点，针对这些问题和痛点，我选择性地作出了总结。下面就开始跟大家分享我的总结，也就是今天的主题内容--前端开发总结与分享。希望这次分享，能带给大家更有效的开发助力。
## 工作篇
先来总结一下这一个月来的工作任务。

balabala...

接下来的内容，我会按照css, es，vue和element-ui展开，其中主要包括开发中遇到的问题与相关处理办法，以及自己对相关技术的见解。
## CSS篇
这部分主要提出两个实用技巧和一些实用的设计原则。
### 认识[box-sizing](http://www.w3school.com.cn/cssref/pr_box-sizing.asp)
> `box-sizing` 属性允许您以特定的方式定义匹配某个区域的特定元素。
> - 为元素设定的宽度和高度决定了元素的边框盒。
> - 就是说，为元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制。
> - 通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度。

```css
div {
  box-sizing: border-box;
}
```
`height` = `border-top` + `padding-top` + `content` + `padding-bottom` + `border-bottom`;

宽度同理。

### 你将离不开的Flex布局
网页布局是CSS的重点应用之一。

> 布局的传统解决方案，基于盒状模型，依赖 `display` 属性 + `position`属性 + `float`属性。它对于那些特殊布局非常不方便，比如，垂直居中就不容易实现。

> 2009年，W3C 提出了一种新的方案--Flex 布局，可以简便、完整、响应式地实现各种页面布局。目前，它已经得到了所有浏览器的支持，这意味着，现在就能很安全地使用这项功能。

> Flex布局已成为布局首选方案。

详情可见：
- [Flex布局教程--阮一峰](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)

### 大家都应该懂一点的设计原则
了解以下几点实用设计原则，你就可以设计出简单，大方，得体，灵活的UI界面。

- [亲密性](https://ant.design/docs/spec/proximity-cn#%E7%BA%B5%E5%90%91%E9%97%B4%E8%B7%9D%E5%85%B3%E7%B3%BB)
- [对齐](https://ant.design/docs/spec/alignment-cn#%E8%A1%A8%E5%8D%95%E7%B1%BB%E5%AF%B9%E9%BD%90)
- [对比](https://ant.design/docs/spec/contrast-cn#%E4%B8%BB%E6%AC%A1%E5%85%B3%E7%B3%BB%E5%AF%B9%E6%AF%94)
- [足不出户](https://ant.design/docs/spec/stay-cn#%E8%A6%86%E7%9B%96%E5%B1%82)
- [即时反应](https://ant.design/docs/spec/reaction-cn#%E5%8F%8D%E9%A6%88%E6%A8%A1%E5%BC%8F)
- 单一职责
- 一致性与单一数据源

以上一部分摘自Ant-Design设计语言，一部分来自自己的总结。

## ES篇

该部分主要分享`ECMAScript5`和`ECMAScript6`一些实用的特性。

### [ES5数组相关API](https://www.cnblogs.com/mingbo-zhang/p/10190812.html)
- `forEach()`
- `map()`
- `filter()`
- `some()`
- `every()`
- `reduce()`

### [ES6实用特性](https://www.jianshu.com/p/287e0bb867ae)
- 箭头函数
- 字符串模板
- 函数默认值
- Object.assign()
- 解构
- 展开运算符

## Vue篇

### 双向绑定

- 单向数据流与双向绑定
- 双向绑定原理

### 组件

#### 单文件组件

- 完整语法高亮
- CommonJS模块
- 组件作用域的CSS

#### 组件核心概念

- 属性
- 事件
- 插槽
- 指令

#### [生命周期](https://segmentfault.com/a/1190000011381906)

#### 自定义组件

- 公共组件
- 业务组件

### 注意事项与技巧

- v-if与v-show
- 状态初始化
- key属性
- 数据驱动视图的更新
- this与箭头函数在Vue中的使用
- 正确使用生命周期
- 计算属性与侦听器（计算属性setter）
- 过滤器的使用
- 函数式组件

## ElementUI篇

### 正确选用消息提示组件

### layout布局的应用场景

### 页面组件大小的集中管理

### 上传文件组件使用注意事项

- accept
- 手动上传

### vue数据驱动视图的体现

### 表单校验功能注意事项（绑定正确的值）

### [表格组件表头错位问题](https://blog.csdn.net/jackie_bobo/article/details/86064112/)

### 弹出框组件的应用场景

## 其他

### 相关工具（Vetur, ESLint, Prettier, vue-devtools, FeHelper）

#### Vetur

- 语法高亮
- 标签补全、模板生成
- Lint检查
- 格式化

#### ESLint

- 代码规范
- 错误检查

#### Prettier

- 格式化

#### [vue-devtools](https://github.com/vuejs/vue-devtools)

- 集成Vuex
- 可远程调试
- 性能分析（新版本）

#### [FeHelper](https://www.baidufe.com/fehelper)

- 前端实用工具插件

以上就是我此次分享的全部内容，不足之处，还望指正。
