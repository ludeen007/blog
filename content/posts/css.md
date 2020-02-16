+++
title = "学习CSS布局的笔记"
categories = ["notes"]
tags = ["notes", "CSS", "frontend"]
+++

网址 <http://zh.learnlayout.com/>

一、display属性

1. block 块级元素：div，p，form，header，footer，section。
2. inline 行内元素：span，a。
3. none 无：script的默认display值。

二、零碎知识点

1. max-width用来处理小窗口
2. 中英术语：border边框，padding内边距
3. 传统的盒子模型里，边框和内边距会增加撑开元素，新特性box-sizing: border-box属性可以阻止这种行为。

三、position属性

1. static：默认值，表示元素不会特殊定位。其他不是position：static的元素会被positioned。
2. relative：变现和static一样，除非有额外属性。
3. fixed：固定定位，相对视窗来定位，即使页面滚动，元素位置不变。
4. absolute：和fixed类似，但是相对于最近的positioned祖先元素或者body元素。元素位置随页面滚动而移动。

四、float属性

  1. 可用于实现文字环绕图片。

五、clear属性

  1. 用于控制浮动。
  2. 清除浮动（clearfix hack）：设置overflow: auto。

六、百分比宽度

  1. 百分比是一种相对于包含块的计量单位。

七、媒体查询

  1. “响应式设计（Responsive Design）”是一种让网站针对不同的浏览器和设备“呈现”不同显示效果的策略，这样可以让网站在任何情况下显示得很棒！
  2. 媒体查询是做此事所需的最强大的工具。

八、inline-block

  1. 可用于实现很多网格铺满浏览器。

九、column属性

  1. 很新的css属性，可用于实现文字的多列布局。
