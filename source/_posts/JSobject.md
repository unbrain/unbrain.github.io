---
title:  JS　里面的对象
reward: true
toc: true
tags:
	- __proto__
	- JavaScript
---



## 全局对象 window

ECMAScript 规定全局对象叫做 global，但是浏览器把 window 作为全局对象（浏览器先存在的）

window 就是一个哈希表，有很多属性。

<!--more-->

window 的属性就是全局变量。

这些全局变量分为两种：

1. 一种是 ECMAScript 规定的
   - global.parseInt
   - global.parseFloat
   - global.Number
   - global.String
   - global.Boolean
   - global.Object
2. 一种是浏览器自己加的属性
   - window.alert
   - window.prompt
   - window.comfirm
   - window.console.log
   - window.console.dir
   - window.document
   - window.document.createElement
   - window.document.getElementById

所有 API 都可以在 MDN 里找到详细的资料。

今天我们学习第一种全局变量。

## 全局函数

1. Number
   var n = new Number(1) 创建一个 Number 对象
   1 与 new Number(1) 的区别是什么？

   ```javascript
   var n = 2
   var n.xxx = 2
   console.log(n.xxx)//undefined
   ```

2. String
   var s = new String('hello') 创建一个 String 对象
   'hello' 与 new String('hello') 的区别是什么？看内存图

3. Boolean
   var b = new Boolean(true) 创建一个 Boolean 对象
   true 与 new Boolean(true) 的区别是什么？看内存图

   ```javascript
   var f1 = false
   var f2 = new Boolean(false)
   if(f1){console.log(f1)}
   if(f2){console.log(f2)}//f2
   ```

4. Object
   var o1 = {}
   var o2 = new Object()
   o1 和 o2 没区别

## 公用的属性藏在哪

所有对象都有 toString 和 valueOf 属性，那么我们是否有必要给每个对象一个 toString 和 valueOf 呢？

明显不需要。

JS 的做法是把 toString 和 valueOf 放在一个对象里（暂且叫做公用属性组成的对象）

然后让每一个对象的 `__proto__` 存储这个「公用属性组成的对象」的地址。