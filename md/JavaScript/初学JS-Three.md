# JS

---


## 一、变量的两种声明方式
### <1> var：声明所有的数据类型
【变量什么都可以存】

### <2> function：专门用来声明函数
【函数也是一种变量】
#### ① 有名函数

```
function fn(){}
```

#### ② 匿名函数
function (){}
直接这样写是会报错的，匿名函数必须付给某个对象（变量或者事件）

#### ③ 函数的声明
A. 函数的声明
```
function fn(){}
```
B. 函数表达式
```
var fn = function(){}
```

#### ④ 函数的执行方式
A. 自执行
加括号
B. 被动执行


> <font color='red'>注意：</font>
变量不一定是函数，但是函数名可以叫做变量
这里的fn可以叫 `函数fn` ，也可以叫 `变量fn`
function fn(){}

---

## 二、对属性的操作

### 1、获取属性
getAttribute('属性名')

### 2、修改属性
setAttribute('属性名','值')

### 3、删除属性
removeAttribute('属性名')

### 4、判断属性是否存在
hasAttribute('属性名')


----
## 三、数据类型

### 1、数字类型
number

### 2、string类型
字符串只是数据，不是类型，所有带引号包裹的都是字符串，字符串的类型为string类型

### 3、boolean类型
布尔值 true/false

### 4、undefined
未定义，没有值，系统默认给的值

### 5、null
空，空的指针对象，表示没有对象，这里不该有值

### 6、object


## 四、if、switch、三目运算

### 1、if
* 六种转换成false
0，"" 空字符串，undefined，null，false，NaN

### 2、switch

### 3、三目运算



----

## 五、作用域

### 1、全局变量
直接在script标签下声明的变量

### 2、局部变量
所有的花括号都会形成单独的作用域
> <font color='red'>but 在ES5中，for and if 的 {} 是不存在作用域的，only 函数</font>

### 3、向外找

---

## 六、continue / break

### 1、continue跳出当前一层循环

### 2、break跳出整个循环


----

## 七、转换

### 1、Number()
对一个字符串整体进行转换，非法的就转换成NaN

> 转换成布尔值为false的有：
null undefined 0 NaN false ""
NaN === NaN ; NaN == NaN 都是false，自己都不等于自己

> 出现NaN的情况：
进行了非法的数学运算，或者字符串,undefined,{} json

> 转换成0：""空字符串，null,false,空数组[ ],

### 2、parseInt()
从做到有右检查，遇到非数字就停止，转换出前面的数字，还有取整的功能

> 转换成NaN：""空字符串,布尔值，空数组

---

## 八、获取元素样式

### 1、getComputedStyle();
不兼容IE8及以下浏览器
写法：getComputedStyle().width

### 2、obj.currentStyle;
IE8及以下兼容写法
写法：obj.currentStyle.width


## 九、JS解析顺序

### 1、编译

### 隐式过程：传参（在编译最后，执行之前执行，也可以理解为优先级更高）

### 2、执行

```
var num = 5;
(function fn(num){
    alert(num);     //5
    var num = 10;
    alert(num);     //10
})(num);

-------------------

var num = 5;
(function fn(num){
    alert(num);     //5
    var num;
    alert(num);     //5
})(num);
```

----

## 十、数据类型

1、引用型数据类型
object 每var一个都会新建一个内存地址去存放这个object
而其他的五种数据类型，属于基本数据类型，是直接比较值，只比较数据值的‘形’是否一样

2、基本数据类型

----

## 字符串
字面量/直接量创建


1、charAt（）兼容IE7以下的字符串查找

2、indexOf('val',num);
查询字符，val查询值，num开始下标
找不到返回-1

3、lastIndexOf();
从后面往前找

4、charCodeAt();
查询下标，返回ASCII码

5、fromCharCode();

6、substring();截取字符串
substring('num1','num2')：num1开始位置，num2结束位置，不包含num2下标的字符，区间表示为 [num1，num2)；
substring('num1')：相当于 [num1，∞)

7、substr('num','sum');
num开始下标，sum长度

8、slice();

9、replace 替换



### 9、split('val');切割字符串
以val为条件切割字符串，返回切割后的数据


----

## 数组

1、创建
```
var arr1 = [];
var arr2 = Array();
var arr3 = new Array();

```

2、indexOf('val');
查询值val,返回下标

3、pop

4、shift

5、unshift

6、jion

7、sort 排序

8、reverse 反向

9、concat 连接数组

10、Array.isArray() 判断数组

11、filter 过滤，去重
return self.indexOf(item)===index;

12、map 遍历数组，不改变原数组

13、forEach 遍历数组，改变原数组

----

## 冒泡排序
虚拟数组思想

两数交换位置
```
arr[j] = [ arr[j-1] , arr[j-1] = arr[j] ][0]
```

----
## json 

实际上来说是一个字符串类型
{}内的内容所有的内容必须用双引号

```
var json = '{"name":"刘谣"，"age":"20"}'; 
```

所有的数据传输都是字符串形式


### 方法
1、JSON.stringify()反序列化
将对象转换成json字符串格式

2、JSON.parse()序列化
将json字符串转换成object对象，常用


---

类数组
一个对象有规律数字的属性名（下标），并且有length属性，可以通过普通的for来遍历的对象


---

数组也是一个特殊的对象类型

---
function

函数是一个特殊的对象类型


----

作业知识点：

.classList
.add()  加类名
.remove()   移除类名
.toggle()   切换类名（有则删，无则加）
.contains()    返回布尔值（有true，无false）

----


## 定时器

### setTimeout();
只执行一次

> 启动定时器，参数1：处理函数/回调函数，参数2：时间间隔

回调函数：函数a作为参数传入函数b，由函数b执行函数a，那么函数a就叫做回调函数。


```
function fn(){}
setTimeout(fn,1000); 1秒之后执行fn
```

### setTnterval();
循环执行


### 清除定时器
参数为序号
clearTimeout();
clearInterval();

```
var timer1 = setInterval(function (){
    console.log();
}，10000)
```

---

浏览器的最低频率一般是 13 - 20 之间


---

Math函数

### Math.ceil()向上取整

### Math.floor()向下取整

### Math.round()四舍五入

### Math.random()随机数

### Math.max()返回较大的一个值

### Math.min()返回较小的一个值

### Math.sin()
三角函数中：接收的是弧度制


----


## 节点

元素节点

文本节点

属性节点

注释节点


### 获取节点

1、obj.childNodes 获取所有的子节点

【子节点：IE8及以下都会忽略空格和换行】

#### 2、obj.children 获取所有的子`元素`节点

3、obj.nodeType 获取节点的类型，返回其编号
元素节点：1
属性节点：2
文本节点：3
注释节点：8

4、obj.tagName 获得`元素节点`的名称

5、obj.nodeName 获取所有节点的`节点名称`

6、obj.getAttributeNode() 获取指定节点的指定属性节点名称，【不常用】

``以下方法不常用``
7、obj.firstChild 获取第一个子节点

8、obj.lastChild 获取最后一个子节点

9、obj.firstElementChild 获取第一个子元素节点，【不兼容IE8，一般不用】

10、obj.lastElementChild 获取最后一个子元素节点，【同上】

11、obj.nextSibling 下一个兄弟节点【同上】

12、obj.nextElementSibling 下一个兄弟元素节点【同上】

13、obj.previousSibling 上一个兄弟节点【同上】

14、obj.previousElementSibling 上一个兄弟元素节点【同上】

#### 15、obj.parentNode 获取父节点，没有兼容性问题

16、obj.offsetParent 返回定位了的父级元素，它相对于谁定位的，谁就是他的定位父级

17、obj.childElementCount 获取子元素节点的个数【不兼容IE8及以下】

#### 常用方法:
children , offsetParent , parentNode ， tagName

#### 创建一个元素节点
document.createElement(obj)
以前之前用“ innerHTML += ” ，添加标签时，实际上只是一个字符串，在使用时还需要获取元素
obj.appendChild(div);

```
<div id="wrap"></div>
<script>
    var oWrap = ducoment.getElementById("wrap");
    var div = document.createElement("div");
    
    //相比“ += ”的方法，这种方法对于添加事件，添加id更方便
    div.onclick = function (){
        console.log("这是一个div元素节点");
    }
    div.id = "box";
    //在oWrap最后面添加一个节点，只能是节点，不能加 "" ，不然就变成字符串
    oWrap.appendChild(div);
    
    //innerHTML 在只是写一个文本时，用这个更合适

</script>
```

#### 克隆节点
节点.cloneNode(bool);
参数默认为false；
true 深度克隆，复制所有
false 浅度克隆，不复制内容

添加子节点
obj.insertBefore(要添加的子节点，需要放在哪个子节点的前面)

删除子节点
obj.removeChild(节点) 通过父节点删除子节点

替换子节点
obj.replaceChild(子节点，被替换的节点)


---

## css试图模式

### client
获取文档可视区域的宽高（不包括滚动条）
1、clientWidth
2、clientHeight

获取边框厚度
3、clientTop 元素上边框厚度
4、clientLeft 元素左边框厚度

### inner
获取窗口的可视区域宽高（包括滚动条）
【IE8以下不兼容】
1、innerWidth
2、innerHeight

### offset 与定位有关
获取元素的实际大小，即content+padding+border，即写的是宽高是多少就是多少
1、offsetWidth
2、offsetHeight

获取从元素的`外边框开始`到定位父级的`内边框`距离（不包括定位父级的边框）
3、offsetTop 元素顶部到定位父级的顶部的距离
4、offsetLeft 元素左部到定位父级的左部的距离


### scroll
获取元素Content+padding的大小，当元素内容的东西超出的时候，会把超出的部分算进去；当超出时，下padding可能就没有了，这时算的就是上padding到内容底部的距离。
【当元素有overflow：hidden时，得到的是上下padding+content+超出的部分】
1、scrollWidth
2、scrollHeight

获取X，Y轴方向被挡住的那部分大小
3、scrollTop
4、scrollLeft



### page
1、pageY 到document的y轴方向的距离，包括没有显示的部分

----


## 事件对象

1、DOM零级事件，绑定on+"...."事件
即obj.onclick，这种事件没有兼容性问题
只同一个对象绑定的相同事件只能有一个
事件对象e

```
document.onclick = function(e){
    //兼容IE
    e = e || window.event;//事件对象
    
}
```

2、监听事件
DOM二级事件
obj.addEventListener("事件类型"，事件函数(回调函数)，布尔值);
兼容IE：obj.attachEvent("事件类型"，事件函数)；
IE不支持捕获
布尔值：
    默认false：冒泡；
    true：捕获；（与冒泡相反，从最上面的事件向下调用）
    
事件捕获：父级事件向下执行到子级事件；
捕获比冒泡优先，并且比冒泡执行快一点

```
obj.addEventListener("click",function(){
    e.stopPropagation();//也能阻止冒泡事件
});
```

3、事件冒泡
子集将一直向上调用父级事件，直到document

阻止事件冒泡
e.stopPropagation();
兼容IE：e.cancelBubble = true;
true阻止，false不阻止
```
obj.onclick = function(e){
    e = e || window.event;
    e.cancelBubble = true;//IE写法
    e.stopPropagation();//阻止冒泡事件，即所有的父级事件都不执行
}

```

4、解绑监听事件
obj.removeEventListener("事件类型"，函数名);
兼容IE
obj.detachEvent("事件类型"，函数名);


---

### 事件代理
触发事件源的元素
e.target
e.srcElement


---
DOM零级事件
obj.onclick = function (){}
DOM二级事件
obj.addEventListener("click",function(){});

DOM零级事件即使不点击时，也开辟了内存把function存起来了，并将obj的onclick的属性指向这个function；
而DOM二级事件则是，当触发这个事件时才会开辟内存读取这个function，没有触发时不会读取function


---


### 阻止默认行为

#### 1、oncontextmenu
检测鼠标右键单击
阻止默认行为：e.preventDefault();
IE8及以下：e.returnValue = false;
true 不阻止， false 阻止；
```
//1、return false也能阻止默认行为，但是只能在DOM零级事件中使用
document.oncontextmenu = function (){
    return false;
}
//而在DOM二级事件中就无法使用了
document.addEventListener("contextmenu",function (){
    return false;
})

//2、零级二级都可以
document.oncontextmenu = function (){
    //阻止默认行为
    //鼠标右键时不弹窗
    e.preventDefault();
    //IE
    e.returnValue = false;
    //兼容写法
    e.preventDefault ? e.preventDefault() : e.returnValue = false;
}
```

#### 2、onmousedown
左键右键都能够监听
（不能在这里面阻止默认行为）


----

### 鼠标滚动事件

#### 1、document.onscroll
监听浏览器的滚动条变化，只要滚动条的滑块发生了变化就会被触发；

#### 2、document.onmousewheel
只监听鼠标滚轮的滚动事件，而直接拖动滚动条的滑块是不会被触发的；
【火狐浏览器没有onmousewheel属性]
火狐浏览器写法：document.DOMmouseScroll
【但是在火狐里面不能以DOM零级的方式绑定滚轮事件，所以要DOM二级事件写法】

判断滚轮方向：
e.wheelDelta
向下滚动 ： -120，
向上滚动 ： +120；

火狐 ：
e.detail
向下滚动 ： +3，
向上滚动 ： -3；
```
document.onmousewheel = function(){
    //滚轮方向
    console.log(e.wheelDelta);

}
//兼容火狐浏览器：DOMmouseScroll,但是在火狐里面不能以DOM零级的方式绑定滚轮事件
documnet.DOMmouseScroll = function (){
}//不会触发

document.addEventListener("DOMMoueScroll",function(e){
    e = e || window.event;
    console.log(e.detail);
},false);
```

---
### 鼠标滚轮事件兼容

```
//用户写的函数
function wheel(e,d){
    console.log( d );//鼠标滚动方向的判断数值
    console.log("事件处理函数");
}
//调用自定义滚轮函数
mouseWheel(document,wheel);
//鼠标滚轮兼容函数
function mouseWheel(dom,efn){
    var type;
    
    //真正的事件处理函数，用来处理很多统一的值
    function fn(e){
        e = e || window.event;
        //统一滚动方向数值，+1向上，-1向下
        var direction = e.wheelDelta/120 || -e.detail/3;
        //每次调用fn之后改变this指向，并且把鼠标滚动方向，数值都传出去给用户的wheel函数
        //判断用户函数的返回值是否为false，即用户是否要阻止浏览器的默认行为
        if ( efn.call(dom, e, direction) === false ){
            //判断是否为IE8及以下
            if ( dom.addEventListener ){
                e.preventDefault();//阻止默认行为
            } else{
                e.returnValue = false;
            }
        }
    }
    
    //判断浏览器，火狐与其他浏览器
    if ( dom.onmousewheel === null ){
        //其他浏览器
        type = "mousewheel";
    } else {
        //火狐浏览器
        type = "DOMMouseScroll";
    }
    
    //判断IE浏览器，决定绑定方式
    if ( dom.addEventListener ){
        dom.addEventListener( type, fn );
    } else{
        dom.attachEvent( "on"+type, fn );
    }
}
```

``注：所有on....事件的默认值都为null``



---

## BOM 


---

## 表单事件

onblur 失去焦点
onfocus 获得焦点

obj.focus(); 给元素自动聚焦，必须是能获取到光标的元素

obj.onchange
当能获得焦点的元素内容被改变并且元素失去焦点之后会被触发，优先级比onblur高一点

obj.oninput
当内容改变时马上触发



## 键盘事件

obj.onkeydown
当按下键盘时立即触发


```
obj.onkeydown = funcion(e){
    console.log(e.key);//直接返回按键名称
    console.log(e.code);//返回带标识的 按键名称
    console.log(e.keyCode);//按键的编码
}
```

obj.onkeypress
按下键盘触发【只会相应数字键，字母键等能输出文字的键，不响应功能键】

obj.onkeyup
按键抬起时触发

判断alt和ctrl有没有触发
e.altKey
e.ctrlKey

---

## 正则表达式
【正则匹配的是连续性的字符】

match方法
根据字符串查找相同的字符串，符合条件的字符串放到数组中并返回

* 正则表达式可以直接写中文

```
var str = /学习/; //字面量方式  str既是一个正则规则
//构造函数形式
var reg = new RegExp("学习"); //正则
```


### text(str) 正则的方法
检测str中有没有符合正则规则匹配的字符串
有符合条件的：返回true
没有：返回false

### 元字符
【在正则有特殊意义】

\d ：匹配数字
\D ：匹配非数字

\s ：匹配空格
\S ：非k空格

\w ：数字、字母、下划线
\W ：非字符，除了\w之外的所有字符

\b ：独立部分/单词边界
```
var reg = /\bhappy\b/; //只会匹配为happy的完整的独立的单词
```
\B ：非单词边界

. ：匹配任意的字符，不包括\n \r

\r ：制表符，【基本用不到】

\ ：反斜杠，转移，会把紧跟着的字符转义为别的意义


#### 量词
规则后面写，给某一个相同的规则设定连续出现多少次

> 量词的匹配模式：
贪婪匹配：默认从最高次数匹配，知道底线次数；如果不满足底线次数，则跳过。
var reg = /\d{2,5}/;【从5次开始匹配】

> 懒惰匹配：从低次开始匹配，在贪婪模式后加“ ？”；
var reg = /\d{2,5}?/;【从2次开始匹配】

```
var reg = /\d{5}/; //匹配5个连续数字
var reg= /\d{1,9}/; //最少1个，最多9个
var reg= /\d{1,}/; //最少1个，上不封顶
```
1、* --> {0,} 0到正无穷，所有，不限个数
2、+ --> {1,} 1到正无穷，最少要有一个
3、? --> {0,1} 要么没有，要么一个


#### 修饰符/标识符

g ：golbal 全局匹配
```
var str = "123abc456def";
var reg = /\d/g;
```

i ：忽略大小写
```
var str = "123abc456def";
var reg = /ABC/ig;
```

m ：换行匹配
```
var str = "\n123abc456def\n";
var reg = /ABC/igm;
```

() ：组/子项，只会匹配一个整体
    \1 代表第一个子集匹配的内容
    \2 代表第二个子集匹配的内容
```
var str = "abccccabc";
var reg = /adc+/g; // [abcccc,abc]
var reg2 = /(abc)+/g; //[abc,abc]
```


[] ：字符集
    字段：返回两个字符Unicode码之间的所有码对应的字符
    [0-9][a-z][A,Z]  可以一起写[0-9a-zA,Z]
    [()//?+*{}-] 这些在字符串中都是无意义的，普通符号
    [059] 匹配0或者5或者9

```
var str = "14376423987";
var reg = /[1-5]/g; //[1,4,3,4,2,3]
```

中文编码 ：\u4e00-\u9fa5

| ：或者，“|”前面的一个整体和后面的一个整体

^ ：以什么开始的字符
【在字符集中表示除了^跟着的字符以外的东西】

$ ：以什么结束的字符



---

## 存储/缓存数据

### cookie
上限4kb，数据默认有时间限制，默认是一次会话的时间（打开一个窗口，关闭后就结束）
过期时间可以设置：每次与后台交互请求的时候，都会自动发送cookie过去，如果遇上和cookie里的数据没有很大关系的请求时，发送cookie就是占用资源

> 大部分的cookie必须在服务器下存储，cookie是在document下的
传输的必须是字符串，键值对
```
document.cookie = "name=刘谣";
document.cookie = "age=20";
//设置到期时间,一天
document.cookie = "name=刘谣;expire" + new Date(new Data().getTime()+24*60*60*1000).toUTCString();
```


### localStorage和sessionStorage
同：
存储的数据没有上限
在window下

异：
localStorage：永久保存，除非认为清楚或者清楚浏览器缓存
>不需要服务器也可以

sessionStorage：一次会话的时间，并且不能设置过期时间

【以上三种都遵守同源策略】

```
localStorage.setItem("name","刘谣");
localStorage.setItem("age","20");
```

用json存储数据
```
localStorage.setItem("json",JSON.stringify({
    name : "刘谣",
    age : "20"
}));

//获取数据，获取到的就是JSON的字符串内容
localStorage.getItem("json");

//利用json的反序列化转成对象
console.log( JSON.parse(localStorage.getItem("json")) );

//删除某一个数据
localStorage.removeItem("json");

//删除所有数据
localStorage.clear("json");
```


---

## 字符串模板

```
var obj = {
    name : "刘谣",
    age : "20"
};
//反引号,所有内容都在 `` 里面写
//所有的换行都会保留
var str = `我是${obj.name}，几年${obj.age}岁`;
```


---

## ajax
asyncChronous javascript and XML
【同源策略，不可跨域】

> 在不刷新页面的前提下，更新当前这个页面或者局部的数据；
实现与后台的数据交互，同时在页面进行更新

ajax是一个`对象`，必须被new执行的对象
```
//创建一个ajax对象
var ajax = new XMLHttpRequest();
```

open( get/post , 接口地址 , 是否异步/同步true(异步)/false(同步) );
```
ajax.open("get","www.baidu.com/xxx",true);
```

send(); 发送到后台

监听状态，当与后台交互的状态发生变化的时候，就会触发一个函数
```
ajax.pnreadystatechange = function(){
    //当前的状态码ajax.readyState
    //当数据全部接收完成时
    if(ajax.readyState ==== 4){
        //判断服务器的好坏，服务器状态码，http状态码
        if(ajax.status >= 200 && ajax.status < 300 || ajax.status === 300){
            //获取的数据反映出来
            console.log(ajax.responseText);
        }
    }
}

```

与后台交互时当前的状态码ajax.readyState
    0 ：ajax已经创建，但是没有调用open方法
    1 ：open已经调用，没有send发法发送
    2 ：已经发送给后台，但是还没有得到数据
    3 ：正在接受数据
    4 ：数据全部接收完成
    【但是也存在有状态码为4的时候数据没有接收完成，这时可能是服务器出问题了】
    
服务器状态码/http状态码ajax.status
    大于200并且小于300，或者等于300表示服务器没有问题
    
当用户的网络很差或者其他情况，后台处理时间很长；后台应该达到一定时间自动关闭这个请求，让用户不需要继续等待了，无法访问
```
//一秒后关闭请求
setTimeout(function(){
    ajax.abort(); //关闭请求
},1000)
```


### get和post的区别
同：都是使用键值对格式，传输数据都是没有上限的
异：但是get一般只用来传输小数据，因为get的数据（传输）会直接显示在地址栏处，浏览器会对url地址栏的字符长度做限制

#### get
所有发送的数据都跟在 “？” 后面，在地址栏显示，保密性极差
数据：http:www.baidu.com/xxx?xxxxxx
ajax.open("get","http:www.baidu.com/xxx?xxxxxx",true);

#### post
可以在network中看到数据
数据前不带 “？” 问号，以字符串形式放在send里面，保密性和get差不多的，只是不像get一样直接在地址栏显示出来
数据：xxxxxx
ajax.open("get","http:www.baidu.com/xxx",true);
ajax.send("xxxxxx");
post必须设置请求头
ajax.setRequestHeader("Content-Type","xxxxx")



----

## jsonp
是一种非正式的传输`协议`
jsonp是利用了script的src属性的跨域漏洞，可以去其他不同的服务器拿数据

> 比如：img的src，能够跨域访问别的网页的图片，其他的底层定义的src的属性的一些标签也可以实现跨域访问，但是只能显示它本身标签的内容形式

### callback 
回调函数，是jsonp里比传的参数


---

## 面向对象

1、面向对象编程

2、面向过程编程
    以过程为中心得编程思想
    缺点：不利于扩展
    
### 面向对象三大特征：
封装、继承、多态

对象都有的属性：共性
特有的属性：特性

利用function创造一个工厂/流水线
```
function Person(name,age,sex){
    var obj = {};
    obj.name = name;
    obj.age = age;
    obj.sex = sex;
    return obj;
}
var p1 = Person("刘谣",20,"男");
```


### new
> 通过new关键字执行的函数，new后面的函数叫做构造函数

> `new的特性`：
    每次执行函数都会在函数内部创建一个对象，最终会把这个对象返回出来，对象是引用性数据类型，所以每次new执行调用函数时，返回的都是一个新的对象
    
```
var a = "字符串1", //字面量
    b = String("字符串2"), //String方法/内建方法
    c = new String(字符串"); //构造函数
```

> new执行构造函数的过程：叫做构造函数的实例化/类的实例化；
构造函数执行结束以后返回的对象：叫做实例/实例化对象


```
function Person(name,age,sex){
    this.name = name;
    this.age = age;
    this.sex = sex;
}
var p1 = new Person("刘谣",20,"男");
```
> 使用new会隐式创建一个对象并返回出来，并且构造函数中的this会指向new创建的那个对象
就不需要var一个对象并return

> 构造函数一般的函数名一般第一个字母大写

### 原型prototype
> 就是一个仓库，并且仓库里的东西都是共享的，里面存储的每个对象都可以共享方法/属性
本质上是一个对象

```
function Person(name,age,sex){
    //私有属性-->实例对象的属性
    this.name = name;
    this.age = age;
    this.sex = sex;
}
//原型方法
Person.prototype = {
    //共有属性
    say : function (say){
        console.log(say);
    },
    constructor : Person
};
var p1 = new Person("刘谣",20,"男");
p1.say("我是"+this.name);
```

### 原型链
所有的仓库
"1".\__proto__

`__proto__`： 原型链，就是一个引用
所有的对象都有的属性，除了null和undefined

> 原型链：一个对象的原型（\__proto__）指向它的构造函数那个仓库的原型对象（prototype）的原型（\__proto__）
在找原型时，只会在构造函数的原型里面找，不会构造函数的私有属性里面找


> 实例对象的`__proto__`指向生成这个实例对象的构造函数的原型对象，既是构造函数的prototype原型对象

prototype ： 原型对象
只有函数/方法才有的属性

> 原型（prototype）是一个对象，这个对象的\__proto__指向创建这个对象的构造函数的原型（prototype）

constructor：每个原型都有constructor属性，指向当前原型的构造函数

>【先创建构造函数，在创建实例化对象】

----

## 多态
> 多种状态，根据参数的不同，做出不同的反馈



---

## es6新增

### let const class import

es5 ：全局作用域、局部作用域
es6 ：全局作用域、函数作用域、块作用域


### const 声明常量
声明时必须赋值，后续不可以进行第二次等号操作，引用性数据类型是可以向变量里面添加内容的

### 解构赋值
本质上是一种模式，只要等号两边的结构值相同，那么等号左边的变量就会被赋予对应的值。

- 当右边的值比左边的变量少的时候，左边的变量会自动赋予undefined
- 左右值不对应时，左边多余的变量会赋予undefined值，右边多余的时候多余的不管
- 默认值：在左边给变量用=赋予默认值，默认值只有在变量匹配到undefined的时候才会生效，如果匹配到了值，则使用右边的值

#### 扩展运算符 “...”
将数组/类数组展开，将展开的东西变为数组
```
let [a , ...b] = [1,2,3,4,5];
//a = 1
//b = [2,3,4,5]
```

```
let a = 1,
    b = 2;
[a,b]=[b,a]
//a = 2 , b = 1
 
```

### includes()
查找xxx字符串，返回布尔值true/false

### starrsWith()
判断是否以xxx字符开头，返回布尔值true/false

### endsWith()
判断是否以xxx字符结尾，返回布尔值true/false

### repeat(n)
重复原字符串n次返回出一个新字符串，并且默认向下取整。
- -1到+1取0
- false为0
- true为1
- NaN为0
- 字符串会默认转化为数字，转化不了时为false，即为0


## padStart(n,str) padEnd(n,str)
es8的方法
"str"可以没有，默认补全空格
n小于等于原字符串的长度时，返回原字符串

### padStart()
往字符串前面补全到设置长度，返回新字符串
```
var str = "abc".padStart(5,"defg");
//str = "abcde"
```

### padEnd()
往后补全，与padStart()同理




---

isFinite() 检测是否为一个有限数值
Infinity 无穷大

## es6
Number.isFinite() 不会进行隐式类型转换

#### Number.isInteger() 判断整数
有精度问题

### Math函数


#### Math.trunc()
砍掉小数点，会隐式调用Number进行类型转换

#### Math.sign()
整数返回+1，负数返回-1，-0返回-0,0返回0


#### Math.cbrt() 计算一个立方根

#### Math.hypot() 勾股定理，求第三边


es7新增指数运算符 **
2**3 = 2*2*2 = 8



## 函数的扩展

- 当()里面没有参数默认值的时候，默认声明变量的方式是var
- 当参数有默认值的时候，为let声明

arguments实际获取的是实参


### 临时作用域
- 当函数的形参有默认值的时候，整个()内会形成一个作用域
- 当设置默认值时，会先在()内的作用域里面找，如果没有再在此函数上面的全局作用域中找
- 暂时性死区
```
function fn(x = x){}
```
> var没有暂时性死区


### rest参数 ...参数名


### 箭头函数 () => {}
箭头右边如果只有一个表达式或者一个变量的时候表示返回这个东西

- 通常箭头函数用在回调函数上
- 箭头函数，本质上是一个表达式，它没有this
- this固定为父作用域的this
- 不能使用arguments，要使用rest参数代替
- 不可以把箭头函数当做构造函数



---

## 数组的扩展

### 拷贝数组

#### arr.concat();

#### ...arr

#### 浅拷贝
- 复制数组时，如果原数组的成员里有一个引用性数据，那么复制原数组时，新数组的这个引用性数据和原数组中的是一样的，指向同一个内存地址



---

### Object.assgin() 合并对象

Object.assgin(obj1, obj2, obj3)
将obj2和obj3合并到obj1中，改变了obj1，obj2和obj3不变

### Object.keys() 键名

### Object.values() 键值

### Object.entries() 键值对
用一个数组存键[0]和值[1]

## 判断一个对象是否是数组

### Array.isArray(obj)

### obj instanceof Array

### 判断是否有length/join/constructor === Array



---

## jq操作

### 1、$().offset()
返回一个包含元素到文档顶部（包括未显示的top/left区域，包括margin值）的top/left值得对象

### 1.1、$().offset({top: num,left: num})
当传值的时候，会强制将元素的top/left值变更达到元素距离文档上左的距离只有num值

### 2、$().position()
返回一个包含元素到定位父级的top/left值的对象

### 3、$().srollTop()
返回当前元素滚动条的高度

### 3.1、$().srollTop(num)
当有传值的时候，触发一个事件时，回时元素立刻到达设置的nun滚动条的高度

### 4、获取宽度
#### <1> $().width()
元素设置的width为多少返回的就是多少

#### <2> $().innerWidth()
返回元素的width+内部的距离(padding)

#### <3> $().outerWidth()
返回元素的width+外部的距离(margin)

#### <4> 传值的时候
- \$().width(num)
会强行改掉元素的宽度width
- \$().innerWidth(num)
会强行改成元素的宽度width使得width+padding的值等于num
- \$().outerWidth(num)
会强行改成元素的宽度width使得width+margin的值等于num

### $().map(function(index,val){})
- index：下标
- val：dom元素节点
- return：写什么返回什么

### $().each(function(index,val){})
- index：同上
- val：同上
- return：管你写什么，老子就返回操作对象


---
## 获取地理位置
使用navigator下面的geolocation()方法获取用户位置

- 检测是否支持地理定位
- 如果支持，则运行getCurrentPositio()方法。如果不支持，则向用户显示一段消息。
- 如果getCurrentPosition()运行成功，则向参数showPosition中规定的函数返回一个coordinates对象
- 如果运行失败，则向参数showError中规定的函数返回错误信息
    - Permission denied---用户不允许地理定位
    - Position unavailable - 无法获取当前位置
    - Timeout - 操作超时
  
- showPosition()函数获得并显示经度和纬度



```
<script>
function getLocation(){
    if (navigator.geolocation){
        navigator.geolocation.getCurrentPosition(showPosition,showError);
    } else {
        alert("Geolocation is not supported by this browser.");
    }
}
// 获取成功
function showPosition(position)
  {
  let lat = position.coords.latitude; //经度
  let lon = position.coords.longitude; //纬度
  }
//获取失败运行
function showError(error)
  {
  switch(error.code)
    {
    case error.PERMISSION_DENIED:
      x.innerHTML="User denied the request for Geolocation."
      break;
    case error.POSITION_UNAVAILABLE:
      x.innerHTML="Location information is unavailable."
      break;
    case error.TIMEOUT:
      x.innerHTML="The request to get user location timed out."
      break;
    case error.UNKNOWN_ERROR:
      x.innerHTML="An unknown error occurred."
      break;
    }
  }
</script>
```
---