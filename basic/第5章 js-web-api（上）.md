- w3c标准没有规定任何js基础相关的东西
- 不管什么变量类型、原型、作用域和变量
- 只管定义于浏览器中js操作页面的API和全局变量


#### js内置的全局函数和对象有哪些？

#### js = W3C + ECMA262

## DOM（考基础的部分）
- DOM 是哪种基本数据结构？
- DOM 操作的常用API有哪些？
- DOM 节点attr和property有何区别？

DOM的本质:xml, 树。

html是xml的一种特殊类型，有着自己的约束。

html其实就是一堆字符串，只不过浏览器给解析了。

DOM其实就是“结构化”后的html字符串，并且js和css可以识别和操作的模型。

```
document.getElementById()
document.getElementsByTagName()
document.getElementsByClassName()
document.querySelectorAll()

```

#### js node对象常用属性
style, nodeName, nodeType, className

property是js获取的node节点对象的属性，可以在console面板中去查看；property则更倾向于标签的属性。

## DOM结构操作

```
div1.parentElement
div1.childNodes
div1.removeChild(child[0]) // 注意：text也是子元素之一
div1.createElement('p')
div1.innerHTML = '';
div1.appendChild(p1) // 移动元素也用这个

```


## BOM 浏览器对象模型（知识点很少，考的可能性不大）
- 如何检测浏览器类型？
- 解析url各部分

#### navigator
浏览器的一些属性

#### screen
屏幕的一些基本属性

#### location
地址栏的一些属性

#### history
前进后退等一些历史信息

```
var ua = navigator.userAgent
var isChrome = ua.indexOf('Chrome')

screen.width
screen.height

location.href
location.protocol   // http OR https OR etc.
location.pathname
location.search
location.hash

history.back()
history.forward()
```


