# node


---

#第一章 认识node.js

## 一、了解node.js
> node.js使用了一个事件驱动、非阻塞式I/O的模型，使其轻量又高效。 

- I/O密集
- CPU密集


> BS 浏览器和后端
CS 客户端和后端



---

## 二、学习node

### 1. 引用require
- 缓存：在同一个模块中，第一次引入一个模块时，会有缓存；第二次引用时不会再去调用模块，而是直接使用第一次调用过的模块


### 2. 输出exports
- 最终输出的是module.exports
- 而exports和module.exports是引用关系
- exports指向module.exports

> 导入模块输出的数据 
<1>. 添加属性时使用exports
<2> 而直接赋值时使用module.exports

```
exports.a = "ly"
exports = function(){}
//直接赋值则改变了exports指向，此时得不到exports的值
```


> 模块化编程：不污染全局变量，

```
//这是01.js文件
//require函数的返回值就是exports对象
let a = require("./02.js")
console.log(a)
//运行结果：{n:"刘谣"}
```
```
//这是02.js
let n = "刘谣"
exports.n = n
```

---

## 三、原生模块

### 1. 模块引用
- 原生模块优先
- 不写路径时默认在node原生模块中找
- 默认找node_modules里的某个模块中的index.js运行


### 2. path模块
（1）路径变量

- __dirname 当前目录路径
- __filename 当前文件路径

（2）路径拼接

- path.join()
    - 单纯的拼接
- path.resolve()
    - 从当前目录出发
    - 会解析"/"根目录
    
（3）path.relative

- 得到两个文件之间的相对路径

（4）path.parse

- 格式化路径


### 3. url模块
- 解析url

> map数据类型：键 => 值
用get取值：map.get(键) = 值


### 4. events模块

(1) EventEmitter类
```
const EventEmitter = require("events").EventEmitter
let x = new EventEmitter
//绑定事件
x.on("fn",()=>{})
//解绑事件
x.off("fn")
//触发事件
x.emit("fn") 
```


(2) newListener事件

- 绑定后就会触发，不需要手动触发
- 新增监听器时触发


(3) removeListener

- 移除监听器时触发



---


## 四、文件操作

### 1. fs.readFile("")
