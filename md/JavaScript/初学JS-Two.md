# JavaScript


---

## 判断数据类型

### 1、if条件的数据类型

> true/false

> 为false的 : false  ''  0  null  underfined  NaN


* 三目运算（适合 if else）
> 表达式是否成立 ? 成立输出1 ： 不成立输出2 ;
> var a = 0 ;
> a == 0 ? a = 1 : a = -1 ;
> 等价于 a = a == 0 ? 1 : -1 ;

----------

### 2、switch语句

```
switch(){
    case 1:
        输出1；
        break；
    case 2：
        输出2；
        break；
    default：
        输出其他；
        break；
}
```
---

### 3、自增自减

后自增：先赋值后自增（自减同理）

```
var i = 20;
var a = i++;
a = 20;
i = 21;
```

前自增：先自增后赋值（自减同理）

```
var i = 20;
var a = ++i;
a = 21;
i = 21;
```

---

### 4、循环

    document.write('');//在网页中输出内容
    注：写在window.onload里面时会覆盖掉body里面的所有内容
    

---

### 5、函数自执行

定义就执行

```
    //<1>、
    (function (){
        函数内容;
    } ) ();
    //<2>、
    (function (){
        函数内容;
    } () );
    //<3>、+ - ~ !
    + function (){
        函数内容;
    } ();
    - function (){
        函数内容;
    } ();
    ~ function (){
        函数内容;
    } ();
    ! function (){
        函数内容;
    } ();
    
```

**注：函数外不可访问函数内的内荣**

---

### **6、函数传参**

> **<1>、对应传参**
传什么类型的东西形参都接收

```
var a;
function fn(x,y){ //形参
    a = x + y;
    alert(a);
}
fn( 1,1 );  //实参

function fn1(x,y){
    a = x + y;
}
fn(10,20);
alert(a); //a=30

```

> **<2>、任意传参**
<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">argunments</span>     类数组
<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">argunments.length</span>   参数个数
<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">argunments[index]</span>   访问每一个

```
var a;
function fn(a){
    alert(a);
}
fn(1,2,3,4);
// a 为1

function fn1(){
    alert( arguments.length );
}
fn1(1,2,3,4);
// 结果为4
```

---

> **<3>、函数中的return**
<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">undefined</span> 默认函数返回值

```
function fn(){
    return undefined;
    //默认返回undefined
}
//不需要定义 a = x + y;
function fn(x,y){
    return x+y;
}
alert( fn(1,1) ); //结果为2

```
---
<font style=" font-size: 30px;" color='red'>注意：</font>
> <font style=" font-size: 25px; line-height: 40px;" color='red'><1> alert( fn() ); alert某个函数时,弹窗显示的是函数的返回值，即return的值，简单的说就是return后面的全部内容；
<2> 而直接写 fn(); 是调用函数，得到的是函数里面的内容；
<3> 函数return之后的内容不会执行；</font>


```
function fn(){
    alert('ok');
    return ;
}
fn(); //此时弹窗显示 ok
alert( fn) ); //此时弹窗显示 ok，之后显示 undefined

```

---

<font style=" font-size: 30px;" color='blue'>例：</font>

```
function fn(){
    alert('ok');
    return function (){alert('return的返回值')};
}
fn();  //当直接执行函数 fn() 时，弹窗显示ok

var a = fn();   //将 fn() 付给a
a;      //因此执行 a; 与 fn(); 是一样的结果
fn();
alert( a );     // alert( a ); 和 alert( fn() ); 也是
alert( fn() );

/*  将 fn() 付给a，此时alert( a );时，和alert( fn() );是一样的结果，都是显示 ok 之后显示return后面的全部内容 function (){alert('return的返回值')}   */

/*  而当执行函数 a() 时，显示的是 ok，然后显示 return 的返回值，此时的 a() 和 a 是不同的，a 是函数 fn(); 而 a() 是函数 a();  */

a();


```

### 7、获取样式
<font style=" font-size: 30px;" color='red'>注意：</font>
> ① 不要获取没有定义的样式；
② 不要获取复合样式。

<1>、普通的 `.style.height` ,获取到的是行内样式（如果没有行内样式就获取不到）；
```
    var oDiv = document.getElementById('div');
    alert( oDiv.style.height );     //获取到的是行内样式
```

<2>、函数 `getComputedStyle()` ，获取到的是div最终的样式（不管样式写在哪，获取div的最终呈现的样式）；

```
    alert( getComputedStyle(oDiv).height );
```

<3>、兼容 IE
IE8以下不认识getComputedStyle函数

```
var h；
if( window.getComputedStyle ){
    h = getComputedStyle(oDiv).height;
}else{
    h = oDiv.currentStyle.height;
}
```

### 8、封装
例：用函数封装兼容IE8的getComputedStyle函数

```
// 获取某个对象（obj）的某个属性（attr）
function getStyle(obj,attr
attr
){
    if( window.getComputedStyle ){
        return getComputedStyle(obj).attr
attr
;
    }else{
      return obj.currentStyle.attr
;
    }
}
```

---

### 9、添加属性，移除属性

添加属性：setAttribute('','');
移除属性：removeAttribute('');

---

### 10、作用域
`作用范围，有效范围`

<1> 全局域
全局变量：直接在script下声明的变量
【即window的属性】

<2> 局部域
局部变量：在函数内部声明的变量
【任何一个函数在执行行就会开启一个局部域】

<3> 作用域链
#### <span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">内部变量会覆盖外部变量</span>
① 只要内部声明了和外部一样的`变量`，函数就不会到外部去找这个变量；

```
<script>
    var a = 'ok';
    function fn(){
        alert( a );
//这里不会弹‘ok’，而是undefined，因为在函数fn()内找不到a，但是它不会出去找
        var a = 123;
    }
</script>
```
#### <span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">就近原则</span>
②  只要是内部声明了和外部一样的`形参`或者`变量`，那么在函数内修改和访问的都是这个`形参`、或者`变量`。

```
var a = 'ok';
function fn(a){
    alert(a); //123
    a = '我是a';
    alert( a ); //我是a
}
fn( 123 );
alert( a ); //ok
```

### 11、js代码解析

#### <1> 预解析
先去找带 `var 等关键词` ，`变量声明`以及`函数声明`，然后将他们存在一个仓库中，会给每个变量都赋undefined，所以当在变量赋值前查看变量时都等于undefined；
var a = undefined ---- 变量提升
function (){} ---- 函数提升
<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">同名函数会被后面的覆盖</span>

#### <2> 解析

---

### 12、闭包
<1> 当函数执行完毕后，就把与解析、解析那个所谓的仓库直接丢掉， `释放内存`；

<2> 而如果`fn()函数`带有return的话，return的内容会被返回给fn()；return的内容（变量、函数）不会被丢掉，而是保存下来，而没有return的函数 fn() 中的内容会被丢掉；
<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">所以才会出现，当定义一个变量 f 去接收带有return的函数 fn() 时，执行变量函数 f() 时，会将return后面的函数内容执行，</span>

```
function fn(){
    alert("fn函数返回值");
    return function (){
        alert("return返回值");
    }
}
var fn1 = fn();
alert(fn1());
/*
这里的结果为：
    1、弹窗 fn函数返回值 ；
    //因为 var fn1 = fn(); 这里的 fn(); 所以执行了一次 fn();
    2、弹 return返回值 ；
    //alert(fn1());里面执行了fn1()；
    3、弹 undefined ；
    //alert(fn1());  难道是因为定义时var fn1 = fn();执行了一次fn();，然后fn()被释放了，所以fn1为undefined？我觉得不对，应该是这里alert(fn1());执行了fn1()；然后fn1()也被释放了；所以alert(fn1());为undefined

*/
```

#### <font color='red'><3> 需要注意的一点是：</font>
> fn()；执行完毕之后虽然说是将`解析的那个仓库`丢掉了，但是这里说的只是将`内存中执行的函数内容释放了`，函数fn()；依然存在的，后面依然可以调用；而 return 会使的 fn() 函数的内容【声明的变量】保存下来，（即return中内部函数使用了外部函数的变量被保存下来了）不会被js的垃圾回收机制给回收掉。

---

### 13、字符串

#### <1> 字符串定义

```
var str = 'helloWorld'; //① 直接量
var str = new String('helloWorle'); //②
var str = String('helloWorle'); // ③

var str1 = 'OK';
var new_str = str.concat( str1 );
alert(new_str); //helloWorleOK 拼接
```

#### <2> 查找字符串
① 通过指定字符查找位置
```
var str = 'helloWorld';
alert( str.indexOf('h') ); // 0
//第0个
```

② 指定索引返回字符串
```
alert( str.charAt(1) ); // e
```

③ 指定索引返回字符串的ASCII码
```
alert( str.charAt(1) ); // 101
// e的ASCII码
```

④ 指定索引返回字符串的ASCII码
```
alert( String.fromCharCode(80) ); // P
// P的ASCII码为80
```

⑤ 截取字符串
A. `substring`
_a. 截取索引为 （1，9） 的字符串，不包含第 9 位的字符_
_b. 会自动取从小到到的顺序，所以写反也没关系_
```
alert( str.substring(1,9) );
alert( str.substring(9,1) );
//结果为elloWorl
```

B. `slice`
_a. 正数同上，截取索引可以为负数，（-5，-1）截取倒数第5位到最后一位，不包含最后一位的字符_
_b. 返回来数时是从 1 开始数，即倒数第一个就是 -1_
```
alert( str.slice(-5,-1) );
//结果为Worl
```
⑥ 转换（不常用）
A. 转小写
```
var str = 'helloWORLD';
var new_str = str.LowerCase();
alert( new_str ); // helloworld
```
B. 转大写
```
var str = 'helloWORLD';
var new_str = str.toUpperCase();
alert( new_str ); // HELLOWORLD
```

⑦ 查找
A. match
【通过指定字符串查找，可以匹配一个或者多个字符，如果找到会直接返回查找的字符串，没有则返回 `null` 】
```
var str = 'helloworld';
alert（ str.match('hell') )；//hell
```
B. search
【匹配字符下标，找到返回下标值，找不到返回 `-1` 】
```
alert( str.search('m') ); //-1
```

⑧ 替换
replace( value, newval )
【查找第到第一个与 `value` 匹配的字符或者字符串，将它替换成 `newval` 】
```
alert( str.replace('o',123) );
// hell123world
alert( str.replace('ell',123) );
// h123oworld
```

⑨ 分割
split( val );
【以 `val` （val可以是字符串）将字符串分割，分别放入数组中】
```
console.log( str.split( 'o' ) );
// 返回为：hell,w,rld
var s = str.split( 'o' );
// 当我将它付给变量s时，返回s的类型为object
```
<font color='red'>注：上面的修改字符串的方法都是不会改变原数组的，只是改变了返回值</font>


---

### 14、数组

#### <1> 创建数组
① `var arr = [1,2,3];`
② `var arr = Array(1,2,3);`
③ `var arr = new Array(1,2,3);`
<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">区别：</span>
第①个内容有几个长度为几；
第②、③个，当数组中只有一个值时，长度为那个值。

#### <2> 改数组
① 修改长度：超出长度的内容就没有了
```
var arr = [1,5,3,6];
arr.length = 3;
alert( arr );   //结果为 1,5,3
```

② 修改内容：将数组中的某个内容替换掉
```
var arr = [1,5,3,6];
arr[0] = 'hello';
alert( arr );   //结果为 hello,5,3，6
```

③ 增加内容：再数组中的最后增加内容
```
var arr = [1,5,3,6];
arr[0] = 'OK';
alert( arr );   //结果为 1,5,3,6,OK
```

#### <2> 稀疏数组
```
var arr = [1,,3,,5];
alert( arr.length );    //5
```

#### <3> 方法 <font color='red'>【这些方法都会改变原数组】</font>

① 添加元素
<font color='red'>【返回新长度】</font>
A. 在数组开头
```
var arr = [1,2,3,4,5];
arr.unshift('hello');   // hello,1,2,3,4,5
```

B. 在数组末尾
```
var arr = [1,2,3,4,5];
arr.push('hello');   // 1,2,3,4,5,hello
```

② 删除元素
<font color='red'>【返回删除的元素】</font>

A. 删除首个元素
```
arr.shift();
alert( arr );   //结果为 2,3,4,5
alert( arr.shift() );   //结果为 1
```

B. 删除末尾元素
```
arr.pop();
alert( arr );   //结果为 1,2,3,4
alert( arr.pop() );   //结果为 5
```

③ 添加，删除，替换一体 `splice`
```
/*
第一位数：在第几个位置
第二个数：0 为不删除，1/2/3代表删几个
第三个数：添加或者替换的元素
*/
var arr = [1,2,3,4,5];
arr.splice(1,0,'hello');    //在第二个位置上添加hello
//返回结果 1,hello,2,3,4,5
arr.splice(1,2);    //删除第二个后面两个元素
//返回结果 1,4,5
arr.splice(1,1,'hello');    //将第二个元素换成hello
//返回结果 1,hello,3,4,5

arr.splice(1,1,'a','b','c','d');
//可以添加多个值，替换同理
```

#### <4> 排序

① sort()
默认排序，只笔每个元素的首位，没卵用

② 冒泡法
【当数组元素在10个以内时】【性能差】
> '>' 调换位置（返回值为正时）
'0' 不调换位置（相等）
'<' 不调换位置（返回值为负）

② 二分法
【当数组元素在10个以上时】

```
arr.sort( function (a,b){
    return a-b;
    return b-a;
} )
```

#### <5> 别的操作

① 颠倒 reverse() 
【将数组颠倒】

② 拼接 concat() 
【数组和数组拼接】
【不会改变原数组】

③ 截取 slice(1,3)
【从第二位到第三位，不包括第四位】

④ 拼接成字符串 join
【用某元素把数组拼接成字符串】

⑤ 判断数组
【返回值为 true/false 】
Array.isArray( arr );

---

### 15、ECMAscript5
【是javascript的执行标准】

value ：是数组的项
index ：当前项的下标
arr ：是数组本身

<1> forEach遍历数组
```
forEach( function (value,index,arr){
})
```

<2> map 计算
【有返回值，返回值是一个数组，retuern是什么就是什么】
```
map( function (val){
    return val * 2;
})
```

<3> filtre 过滤
【有返回值，返回值是一个数组，retuern为真（true）的value值会进入数组】
```
filter(function(value){
    return value > 5;
})
```

<3> every 有点判断的意思
【每一个为true，才返回true，否则为false】
```
every(function(val){
    return val != 'h'; //是否每个值都等于h
})
```

<3> some 也有判断的意思
【每一个为true，才返回true，否则为false】
```
some(function(val){
    return val == 'h'; //是否有一个值都等于h
})
```

---

<span style=" display: inline-block; background: yellow; border-radius: 5px; padding: 2px; margin: 5px 20px 0 0; ">随机数：
Math.random() 随机一个0~1之间的数，不包括1
</span>

---
