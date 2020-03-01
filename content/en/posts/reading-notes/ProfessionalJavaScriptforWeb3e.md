---
title: "《Javascript高级程序设计》3e读书笔记"
date: 2019-12-11T18:42:55+08:00
draft: false
categories: ["读书笔记"]
tags: ["读书笔记", "Javascript"]
---

原作名《Professional JavaScript for Web》
TODO:待整理

### for-in 语句遍历属性

## 2 种值

基本类型值：Undefined Null Boolean Number String。按值复制。栈内存。非对象。
引用类型值：可能由多个值组成的对象。按引用复制。堆内存。是对象。

## 函数参数只按值传递。即向参数传引用类型值时，会传这个值在内存中的地址复制给一个局部变量，因而这个局部变量的变化会反应在函数的外部

## typeof instanceof 执行环境及作用域

## 4.4 小结

### 数组

Array.length 不是只读的。判断是否数组 Array.isArray(val)
栈方法：push(), pop()
队列方法: shift() push() / unshift() pop()
重排序方法：sort() 默认按字符串从小到大排序，可用 sort(compare)自定义排序 reverse()反转
操作方法：concat() 连接 slice() 切片 splice()多功能
位置方法：indexOf() lastIndexOf()
迭代方法：every() filter() forEach() map() some()
缩小方法: reduce() reduceRight()

### Date 类型

Date.parse() Date.UTC() new Date() Date.new()
日期/时间组件方法：get/setDate()/Month()/seconds()
Regexp 类型
let expression = /pattern/flags;
模式 pattern
标志 flags: g 全局模式 i 不区分大小写 m 多行模式
元字符（模式中使用元字符要转义）
( [ { \ ^ $ | ? * + . ) ] }
let pattern = /[bc]at/I;let pattern2 = new RegExp("[bc]at", "I");
字面量模式等价的字符串
/\[bc\]at/"\\[bc\\]at"
/\.at"\\.at"
/\w\\hello\\123/"\\w\\\\hello\\\\123"
RegExp 实例方法： exec() test()

### Function 类型

每个函数都是 Function 类型的实例。函数名是一个指向函数对象的指针。
函数声明：会被预先读取，使其在任何代码执行前可用。
函数表达式：被执行时才读取。

#### 函数内部属性

2 个特殊对象：
arguments：类数组对象，含所有参数。arguments.callee 指向拥有这个 arguments 对象的函数（严格模式下不能用）。arguments.caller 类似。
this：this 引用的是数据据以执行的环境对象。

#### 函数的属性和方法

length：函数希望接收的命名参数个数。
prototype：引用类型，保存它们所有实例方法的真正所在。
call() apply() bind()：传参，扩充函数赖以运行的作用域。
函数声明 函数表达式 闭包

### String 类型

属性：length
字符方法：charAt() charCodeAt() stringValue[i]
字符串方法：concat() slice() indexOf() lastIndexOf() trim() toUpperCase() match() localCompare()

### 对象

构造函数：通过 new 操作符来调用的函数
