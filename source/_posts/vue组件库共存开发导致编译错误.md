---
title: vue组件库共存开发导致编译错误
date: 2020-04-14 18:46:31
categories: 
  - vue
  - element-ui
  - ant-design-vue
tags: 
  - vue
  - element-ui
  - ant-design-vue
  - $attr is readonly
  - $listeners is readonly
---

![ant-design-vue](https://vuejsexamples.com/content/images/2016/08/20160827214833.jpg)


**在 vue 组件库中, elementUI 是一个质量相对很高的组件库了, 组件比较全面也很好用
但在我使用`el-dialog`与`el-drawer`组件的并且出现多级嵌套的时候问题就来了, 经常遇到遮罩层无法关闭, 子弹窗在父弹窗的下面的情况, 也查了很多遍官方文档, 例如官方文档是使用 `append-to-body`与`modal-append-to-body`去解决这个问题, 但仍然无法根治, 但是项目初期就是选择的 elementUI 的组件库, 目前想去替换掉的话显然是不现实的, 所以只好考虑兼容的办法, 单独定义弹窗和抽屉组件到自己的组件库中进行使用**

<!-- more -->



