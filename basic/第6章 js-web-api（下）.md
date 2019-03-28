## 事件

- 编写一个通用的事件监听函数？
```
function bindEvent(elem, type, selector, fn) {
    if (fn == null) {
        fn = selector
        selector = null
    }

    elem.addEventListener(type, function (e) {
        var target
        if (selector) {
            target = e.target
            if (target.matches(selector)) {
                fn.call(target, e)
            }
        }
    })
}

// 使用代理
var div1 = document.getElementById('div1')
bindEvent(div1, 'click', 'a', function (e) {
    console.log(this.innerHTML)
})


// 不使用代理
var div1 = document.getElementById('a1')
bindEvent(div1, 'click', function (e) {
    console.log(this.innerHTML)
})
```
- 描述事件冒泡？
  > 事件只能往上冒泡
```
var p1 = document.getElementById('p1')
var body = document.body
bindEvent(p1, 'click', function(e){
    e.stopPropatation()
    alert('激活')
})

bindEvent(body, 'click', function(e){
    alert('激活')
})

<body>
    <div id="div1">
        <p id="p1">激活</p>
        <p id="p2">取消</p>
        <p id="p3">取消</p>
        <p id="p4">取消</p>
    </div>
    <div id="div2">
        <p id="p5">取消</p>
        <p id="p6">取消</p>
    </div>
</body>
```
- 对于一个无限下拉加载图片的页面，如何给每个图片绑定事件？
  > 事件代理
```
<div id="div1">
    <a href="">a1</a>
    <a href="">a2</a>
    <a href="">a3</a>
    <a href="">a4</a>
    <!-- 会随时新增更多 a 标签 -->
</div>

var div1 = document.getElementById('div1')
div1.addEventListener('click', function(e){
    var target = e.target
    if(target.nodeName === 'A'){
        alert(target.innerHTML)
    }
})
```
现在对低IE版本兼容性问题，了解即可，无需深究。

事件代理的好处
- 代码简洁
- 提高浏览器的执行效率

## 常用状态码
- 2xx 表示成功处理请求。如200
- 3xx 需要重定向，浏览器直接跳转
- 4xx 客户端请求错误，如404
- 5xx 服务器端错误

## readyState
- 0: （为初始化）还没有调用send()方法
- 1：（载入）已调用send()方法，正在发送请求
- 2：（载入完成）send()方法执行完成，已经接收到全部响应内容
- 3：（交互）正在解析响应内容
- 4：（完成）响应内容解析完成，可以在客户端调用了

## Ajax
- 手动编写一个ajax，不依赖于第三方库
```
var xhr = new XMLHttpRequest()
xhr.open("GET", "api", false)
xhr.onreadystatechange = function () {
    // 这里执行函数异步执行，可参考之前的异步模块
    if (xhr.readyState == 4) {
        if (xhr.status == 200) {
            alert(xhr.responseText)
        }
    }
}
```

- 跨域的几种实现方式

XMLHttpRequest是ajax最核心的api

IE低版本使用ActiveXObject和W3C不一样

## 跨域

- 前端使用JSONP来解决
- 服务端设置http header来解决

原因：浏览器有同源策略，不允许ajax访问其他域口

跨域的条件：协议、域名、端口有一个不同就算跨域。

但是有三个标签允许跨域行为：
- `<img src="xxx">`
- `<link href="xxx">`
- `<script src="xxx">`

#### 三个标签的使用场景
- `<img>`用于打点统计，统计网站可能是其他域
- `<link>`  `<script>` 可以使用CDN
- `<script>` 可以用于JSONP

！！！所有的跨域请求都必须经过信息提供方的允许

JSONP来解决
```
<script>
    window.callback = function(data){
        // 这是我们跨域得到的数据
        console.log(data)
    }
</script>
<script src="http://coding.imxxx.com/api.js"></script>
<!-- 以上将返回 callback({x:100, y:200}) -->
```
服务器设置http header头来解决


## 存储

- 描述一下cookie，sessionStorage，localStorage的区别？
sessionStorage，localStorage会慢慢被取代，
cookie是用于客户端和服务端通信的，被借用于本地存储的功能，
cookie太小，只有4k，
所有的http请求都带着，
api简单，只能覆盖重写，

sessionStorage，localStorage是HTML5专门为存储设计，最大容量5M，
API简单易用，
`localStorage.setItem(key, value), localStorage.getItem(key, value)`
建议localStorage.setItem(key, value), localStorage.getItem(key, value)配合try-catch使用