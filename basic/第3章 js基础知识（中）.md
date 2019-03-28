## 执行上下文

```
console.log(a) // undefined
var a = 100;

foo('zhangsan') // 'zhangsan' 20

function foo(name){
	age = 20
	console.log(name, age)
	var age           // hoisting
}
``

#### js会把变量定义和函数定义（不包括函数表达式，这里指的是函数声明）先拿出来，但函数名和变量名重复的时候，函数的优先级高

#### js中没有块级作用域

## 闭包的使用场景
- 函数作为返回值
- 函数作为参数传递

闭包种类1： 常规类型，即返回函数的类型

闭包种类2： 函数作为参数传递形

```
function f1(){
    console.log(a)
}

function F2(fn){
    var a = 200
    fn()
}

F2(f1)
```


## 题目
- 说一下对变量提升的理解
  > 变量定义
  > 函数声明（注意和函数表达式的区别）
- 说明this集中不同的使用场景
  > 作为构造函数执行
  > 作为普通函数执行
  > 作为对象属性执行
  > call apply bind
- 创建10个<a>标签，点击的时候弹出来对应的序号
- 如何理解作用域
- 实际开发中闭包的应用
  > 封装变量
  > 收敛权限