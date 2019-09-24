# JS

---

## console的其他方法

### 1. console.log()

### 2. console.dir()

### 3. console.error()
以红色报错的形式输出

### 4. console.time("tag"); console.timeEnd("tag")
设定一个tag标记点，打印之间代码执行时间，误差很大

### 5. Console.assert()
判断第一个参数是否为真，false的话抛出异常并且在控制台输出相应信息。

### 6. Console.clear()
清空控制台。

### 7. Console.count()
以参数为标识记录调用的次数，调用时在控制台打印标识以及调用次数。

### 8. Console.debug()
console.log方法的别称，使用方法可以参考Console.log()

### 9. Console.dir() 
打印一条以三角形符号开头的语句，可以点击三角展开查看对象的属性。

### 10. Console.dirxml() 
如果可以，打印 XML/HTML 元素表示的指定对象，或者 JavaScript 对象视图。

### 11. Console.error()
打印一条错误信息，使用方法可以参考 string substitution。

### 12. Console._exception()   
error方法的别称，使用方法参考Console.error()

### 13. Console.group()
打印树状结构，配合groupCollapsed以及groupEnd方法;

### 14. Console.groupCollapsed()
创建一个新的内联 group。使用方法和group相同，不同的是groupCollapsed打印出来的内容默认是折叠的。

### 15. Console.groupEnd()
结束当前Tree

### 16. Console.info()
打印以感叹号字符开始的信息，使用方法和log相同

### 17. Console.log()
打印字符串，使用方法比较类似C的printf格式输出，可参考 string substitution 。

### 18. Console.profile()
可以以第一个参数为标识，开始javascript执行过程的数据收集。和chrome控制台选项开Profiles比较类似，具体可参考chrome profiles

### 19. Console.profileEnd()
配合profile方法，作为数据收集的结束。

### 20. Console.table()
将数据打印成表格。Console.table [en-US]

### 21. Console.time()
计时器，接受一个参数作为标识。

### 22. Console.timeEnd()
接受一个参数作为标识，结束特定的计时器。

### 23. Console.timeStamp() 
添加一个标记到浏览器的 Timeline 或 Waterfall 工具.

### 24. Console.trace()
打印stack trace.

### 25. Console.warn()
打印一个警告信息，使用方法可以参考 string substitution。


---


## ajax
### get接收

```
const xhr = new XMLHttpRequest()
// 发送
xhr.open("GET",URL,true/false)
// 监听
xhr.send()

xhr.onload/onreadystatechange = () => {
    // 判断ajax本身的状态码
    if(xhr.readyState === 4){
        // 判断服务器状态码
        if( 200 <= xhr.status && xhr.status < 300 || xhr.status === 304 ){
            // 请求成功
            
            // 服务器返回的数据
            xhr.responseText
        }
    }
}
```

### post发送

```
const xhr = new XMLHttpRequest()
xhr.open("POST",URL,true/false)
// 请求头
xhr.setRequestHeader("Content-Type","application/x-WWW-form-urlencoded")
xhr.send("user=xxxx&pwd=xxxx")

xhr.onload/onreadystatechange = () => {
    // 判断ajax本身的状态码
    if(xhr.readyState === 4){
        // 判断服务器状态码
        if( 200 <= xhr.status && xhr.status < 300 || xhr.status === 304 ){
            // 请求成功
            
            // 服务器返回的数据
            xhr.responseText
        }
    }
}

```

### jq封装的方法

```
$.ajax({
    url : url,
    // 根据GET/POST自动选择调用参数
    method : "POST/GET",
    data : {
        user : xxxx,
        pwd : xxxx
    },
    success(data){
        // 请求成功
    },
    error(){
        // 请求失败
    }
})
```

## 跨域
> 浏览器不允许跨域请求
cors、反向代理、jsonp

- 实现跨域：
    - 通过script的src：属性具备跨域请求资源的能力，JSONP形式
    - CORS 在后台程序里，设置可以让对应域进行访问

---

## jsonp
> jsonp是json的一种使用模式
- 作用：跨域获取数据
- callback：回调函数


---- 

# 类库(工具api的集合)
jQuery


# 框架
vue react

# jQuery

## $().each( (i, v, s) => {} )
- i 序号
- v 值，一个个的对象
- s 自己本身

## $().length
长度

## \$("xxx", context)
$("xxx").context指向给的context对象

## \$().get(index)
- $()[index] 转原生对象
- 转jq对象 $(原生对象)

## \$().index()
- 不传值，返回在父级的下标
```
<div></div>
<div>
    <p class="p1"></p>
    <p></p>
</div>
$(".p1").index(); //0
```

## $().data()
> h5规定自定义标签属性前加上data
```
<div data-liuyao="liuyao">
console.log( $("div").data(liuyao) ); //liuyao
```
- removedata() 移除使用jq添加的属性【没什么卵用】

--- 

# jq选择器

## $("xxx:first")
第一个

## $("xxx:last")
最后一个

## $("xxx:not(XXX)")
不包括XXX

## $("xxx:even")

## $("xxx:odd")

## $("xxx:eq(index)")
选择下标为index的

## $("xxx:gt(index)")
选择下标大于index的

## $("xxx:lt(index)")
匹配所有小于给定索引值的元素

## $("xxx:contains(text)")
匹配包含给定文本的元素

## $("xxx:animated")
匹配所有正在执行动画效果的元素

## $(":empty")
匹配所有不包含子元素或者文本的空元素
- 换行的选不到，空格换行属于字符

## $("xxx:parent")
匹配含有子元素或者文本的元素
- 没有子元素或者没有文本就取不到

## $("xxx:has(XXX)")
匹配含有XXX的xxx元素

## $("xxx:hidden")
匹配所有不可见元素，或者type为hidden的元素

## $("xxx:visible")
匹配所有的可见元素

## \$("xxx[attribute]")
> 匹配包含给定属性的元素，attribute元素的属性
- \$("xxx[id=div]")
- \$("xxx[id!=thediv]")
- \$("xxx[id^='t']")
- \$("xxx[id$='v']")
- \$("xxx[id*='edi']")
- \$("xxx[id][class='box'][name]")

## $("xxx:checked")
匹配所有选中的被选中元素


---

# jq属性api
> 处理对象的核心思想：get first / set all

- get(获取)操作默认获取第一个
```
// 获取第一个class为box的name
$(".box").prop("name")
```
- set(设置)操作默认为设置全部
```
// 设置全部class为box的name为aaa
$(".box").prop("name","aaa")
```

## attr
- 主要用来操作自定义属性
- 类似getAttribute和setAttribute操作
- 获取值为布尔值的属性返回布尔值
- 而getAttribute和setAttribute在获取checked此类属性是返回checked的值，不一定返回布尔值

## prop
- 主要用来操作合法属性
- 类似obj.id操作

## removeAttr
删除自定义属性

## removeProp
删除合法属性

## addClass()
添加class类名

## removerClass()
删除class类名

## hasClass()
有没有某某class类名

## toggleClass()
没有添加，有则删除

## html()
- 对应innerHTML
- 没有参数为取值
- 有参数为设置

## text()
- 对应innerText
- 没有参数为取值
- 有参数为设置

## val()
- 对应value
- 没有参数为取值
- 有参数为设置


---

# jqCSSapi

## css()
- 获取时取第一个并只能获取一个属性
```
// 获取高度
$(".box").css("height")
```
- 整个集合全部设置
```
$(".box").css({
    width : 200,
    heigth : 200,
    backgroundColor : "red"
})
```

## offset()
没参数时返回一个包含元素到(视口)文档顶部(包括未显示的top/left区域，包括margin值)的top/left值得对象

## $().offset({top: num,left: num})
当传值的时候，会强制将元素的top/left值变更达到元素距离文档上方、左方的距离只有num值

## $().position()
返回一个包含元素到`定位父级`的top/left值的对象

## $().srollTop()
返回当前元素纵向滚动条的高度

## $().srollTop(num)
当有传值的时候，触发一个事件时，元素纵向滚动条立刻到达设置的num的高度

## $().srollLeft()
返回当前元素的高度

## $().srollLeft(num)
当有传值的时候，触发一个事件时，元素横向滚动条立刻到达设置的num的高度

## $().height()
- 无参数，获取高度
- 有参数，设置高度

## $().width()
- 无参数，获取宽度
- 有参数，设置宽度

## $().innerHeight()
- 无参数，获取内部区域高度(包括补白、不包括边框)
- 对可见和隐藏元素均有效

## $().innerWidth()
- 无参数，获取内部区域宽度(包括补白、不包括边框)
- 此方法对可见和隐藏元素均有效

## $().outerHeight()
- 无参数，获取外部高度(默认包括补白和边框)
- 对可见和隐藏元素均有效

## $().outerWidth()
- 无参数，获取外部宽度(默认包括补白和边框)
- 此方法对可见和隐藏元素均有效


---

# jq文档处理

## $("div").append("<p></p>")
- 向每个匹配的(div)元素内部`追加`(后面)内容(p标签)
- 这个操作与对指定的元素执行appendChild方法，将它们添加到文档中的情况类似
```
$("div").append( (index, html) => {
    console.log(rest);
    // index 为div的下标
    // html为div的内容
    return "<p>111</p>"
})
// ...rest用()框起来
$().append( (...rest) => {
    console.log(rest);
    //
    return "<p>111</p>"
})
```

## $("div").prepend("<p></p>")
- 向每个匹配的(div)元素内部的最前面添加内容(p标签)

## $("p").appendTo("div")
- 会把原始的p移除
- 把所有的p标签(包括内容)放入每一个div中

## $("div").after("<p></p>")
- 向每个匹配的(div)元素的后面添加内容(p标签)

## $("<p></p>").insertAfter("div")
- 把(p标签)内容添加到匹配的(div)元素后面
- 与after一样

## $("div").before("<p></p>")
- 向每个匹配的(div)元素的前面添加内容(p标签)
- 与after相反

## $("<p></p>").insertBefore("div")
- 把(p标签)内容添加到匹配的(div)元素前面
- 与before一样
- 与insertAfter相反

## $("p").wrap("<div class="father"></div>")
- 向匹配的(p)元素每一个都添加一个父级div
- "认爹"

## $("p").unwrap()
- 移除匹配的(p)元素的父级
- "逝父"

## $("p").wrapAll()
- 向匹配的所有(p)元素添加同一个父级div
- "大家一起认一个爹"

## $("div").wrapInner("<div class="father"></div>")
- 将每一个匹配的div元素的子内容(包括文本节点)用一个新的div包裹起来
- "儿子变孙子"

## $("p").replaceWith("<b></b>")
- 将所有匹配的p元素替换成指定的HTML或DOM元素(b标签)

## $("<b></b>").replaceAll("p")
- 用匹配的元素(b标签)替换掉所有匹配到的元素(p标签)

## $("div").empty()
- 把div内的所有元素(包括文本)`全部删除`

## $("p").remove()
- 移除所有匹配的p标签
- "自杀，并且所有遗产都没有"

## $("p").detach()
- 所有绑定的事件、附加的数据等都会保留下来
- "自杀，保留遗产，为了复活"

## $("div").clone(true/false)
- 不传参默认浅克隆，true(深克隆)/false(浅克隆)
    - 与原生不一样
    - 所有找到的div都会被克隆
- 与原生cloneNode(true/false)类似
    - true完全复制(深克隆)
    - false只复制标签外表，不包括内容(浅克隆)
    - 原生克隆不会复制事件(例如click等事件，不管是一级还是二级)
    - 被克隆对象在script中写所有事件和自定义属性都不会克隆
    - 行内事件本质上是自执行的，为零级事件，与js内设置的绑定事件不一样；此时onclick相当于写了标签属性，所以写在行内时会克隆这个属性


---

## id的唯一性
- id获取时，只会获取第一个，后面的不管
- 但不报错


--- 


# es6

## const 常量
- 申明的变量不能进行二次等号赋值，再次赋值会操错；
- 但引用性数据，例如[]数组,{}json对其添加内容不会报错;
- 只是不能改变它的地址指向，它并不是只读的，数组和json添加内容时都没有改变它的地址指向


## 解构赋值

### [] = []/{} = {}
```
// 对应赋值
let [a,b,c] = [1,2,3];
// 匹配模式，同名赋值
// 属性匹配，赋值
let {x: d, y: e,} = {
    x : 4,
    y : 5
}
// 属性名与值一致时可以简写
let {d: d,e: e} = {
    d : 4,
    e : 5
};
let {d,e} = {
    d : 4,
    e : 5
};
```

### 展开运算符“...”
```
let [...a] = [1,2,3]
// 将类数组展开转换成真的数组
let box = [...document.getElementsByTagName("div")]
```

### 惰性求值
```
let {a: f = 1} = {
    a : undefined
}
// f = 1
```

### 默认值
```
function fn(x = 1, y = 2){}
fn()
```

### 使用
```
let { max, min } = Math;
max(1,10) // 10
min(1,10) // 1
```

```
function fn(obj){
    let {a,b,c} = obj;
}
function fn(arr){
    let [a,b,c] = arr;
}
function fn([a,b,c]){
}
let arr = [1,2,3]
fn(arr)
// es6中没arguments，不确定传的参数时用...
function fn(...a){
}
```


---


# es6字符串扩展

## 查询(返回布尔值)

### str.includes(str1, num)
- str内是否存在str1
- 有返回true
- 没有返回false
- num：从什么位置开始
```
let str = "hello javascript"
str.includes("java") //返回true，存在
```

### str.startWith(str1, num)
- str是否以str1开始
- 有返回true
- 没有返回false
- num：从什么位置开始
```
let str = "hello javascript"
str.includes("java") //返回true，存在
```

### str.endWith(str1, length)
- str是否以str1结束
- 有返回true
- 没有返回false
- length：选择字符串长度```

### 


---


### attributes
> 一个节点的所有属性

- nodeName 属性名
- nodeValue 属性值


---


### document.createDocumentFragment()
> dom标签片段仓库

- 虚拟的dom
- 在需要连续添加dom节点时使用
- 提高性能



---

## 回调地狱

## Promise(异步操作)
解决异步回调，但不是最优秀的

```
Promise(异步操作)
    .then(回调---1)
    .then(回调1的回调---2)
    .then(回调2的回调---3)
```

```
new Promise( (resolve, reject) => {
    // resolve成功
    // reject失败
    $.ajax({
        success(msg){
            resolve(msg)
        },
        error(error){}
    })
}).then( (data) => {
    // then的第一个参数为resolve(msg)成功的回调函数传的值
    // 一般接收成功用then
    $.ajax({
        success(msg){
            resolve(msg)
        },
        error(error){}
    })
}).catch( err => {
    // 一般接收失败用catch
    console.log(err)
})
```

### p = Promise.all([new Promise, new Promise, new Promise])
- 所有成功即成功，返回所有成功参数的数组
- 有一个失败即失败，返回第一个失败的结果

### p = Promise.race([p1, p2, p3])
- 最先成功的函数的返回的状态就是他的状态


---

## async函数
es2017提出
