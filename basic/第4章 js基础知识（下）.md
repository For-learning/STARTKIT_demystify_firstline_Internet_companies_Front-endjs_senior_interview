# 题目
- 同步和异步的区别是什么？分别举例子
  > 是否阻塞程序的执行，和`alert()`对比
- 一个关于setTimeout()的笔试题
- 前端使用异步的场景有哪些
  > 定时任务：setTimeout setInterval
  > ajax请求，动态img加载
  > 事件绑定: 其实就是异步绑定监听事件，等待用户行为。

# 异步和单线程

## 使用一个图片加载的方式展示异步

```
	console.log('start');
	var img = document.createElement('img');
	img.onload = function () {
		console.log('loaded');
	}

	img.src = '/xxx.png';
	console.log('end');
```

## Who said setTimeout function is precious?
```
	console.log(Date.now());
	setTimeout(function () {
		console.log(Date.now());
	}, 3000)

	console.log('start')
	for (var i = 0; i < 3000000000; i++) {
		
	}
	console.log('end')
```


# 其他知识补充
- 获取2017-06-10格式的日期
```
	function formatDate(dt) {
		if (!dt) {
			dt = new Date()
		}

		var year = dt.getFullYear()
		var month = dt.getMonth() + 1
		var date = dt.getDate()

		return `${year}-${month}-${date}`
	}
```
- 获取随机数，要求长度一致的字符串格式
  > Math.random() // 0 < result < 1

```
var random = Math.random() + '0000000000'; // 后面加上10个0是一种技巧来防止slice函数报错
var result = random.slice(0, 10);
```
- 写一个遍历对象和数组的通用forEach函数
```
	function forEach(obj, fn) {
		var key
		// 判断是不是数组
		if (obj instanceof Array) {
			obj.forEach(function(item, index){
				fn(index, item)
			})
		} else {
			for (key in obj) {
				fn(key, obj[key])
			}
		}
	}
```
- forEach
- every
- some : 是否有一个是满足条件的则返回true
- sort
```
arr.sort(function (a, b) {
	return a - b // descend
	return b - a // ascend
})
```
- map
- filter

## How to loop a object?
```
	var obj = {
		x: 100,
		y: 200,
		z: 300
	}

	var key
	for (key in obj) {
		if (obj.hasOwnProperty(key)) { // Important! 防止__proto__遍历
			console.log(key, obj[key])
		}
	}
```