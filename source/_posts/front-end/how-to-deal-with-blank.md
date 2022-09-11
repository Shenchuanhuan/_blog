title: 特定场景下的空格处理
date: 2021-03-04 10:56:41
categories: 
tags: 
language: zh-CN
cover: /img//
thumbnail: /img//
---

> 假设有这么一个需求，要求将input输入框中的内容展示在web页面上，输入规则是：不允许开头和结尾出现空格，中间允许空格出现。你会如何处理？

常规处理是监听input输入框的输入变化，通过`e.target.value`获取到输入内容，用正则或者`string.trim`去掉首尾空格，再将处理过的值展示在web页面。
这么一看，没有什么问题，但如果输入的值中间存在多个空格，页面上不一定会也展示多个空格。
```
    // 例子-输入值
    inputValue = '我是首尾没有空格但中         间很多空格的内容'
    // 例子-页面展示
    webView = '我是首尾没有空格但中 间很多空格的内容'
```
#### 为什么会产生这样的效果？
浏览器处理空格的基本规则就是: 文字前后部的空格都会被忽略，内部的连续空格只会算作一个。
 > HTML的这种空格处理规则，适用于多种字符。除了普通的空格键，还包括制表符(`\t`)和换行符(`\r` 和 `\n`)。浏览器会自动把这些符号转成普通空格键。

如果需要原样输出空格，有这么几种方案可选：
1. 使用css的 `white-space: pre`
2. 用 `pre` 标签包裹内容
3. 使用 `&nbsp;`来代替空格
4.


---
### 在线demo

<iframe height="265" style="width: 100%;" scrolling="no" title="demo(how to deal with blank)" src="https://codepen.io/KonnieShen/embed/ZEBRdza?height=265&theme-id=dark&default-tab=html,result" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/KonnieShen/pen/ZEBRdza'>demo(how to deal with blank)</a> by konnieshen
  (<a href='https://codepen.io/KonnieShen'>@KonnieShen</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

---
### 引用资源
- [1] [CSS 的空格处理](http://www.ruanyifeng.com/blog/2018/07/white-space.html)