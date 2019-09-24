# DOM(document object model)文档对象模型
文档对象模型是表示和操作HTML、XML文档内容的基础API

当网页被加载时，浏览器会根据DOM模型将文档解析成一系列节点，构成了一个树状结构。

![image](https://7n.w3cschool.cn/attachments/image/20170619/t_document.png)

图中每一个方框都是一个节点，表示一个node对象，所有的node构成了DOM Tree

#### 节点有7个类型

- **Document：整个文档树的顶层节点**
- DocumentType：比如<!DOCTYPE html>
- **Element：网页的各种HTML标签**
- Attribute：网页元素的属性
- Text：标签之间或标签包含的文本
- Comment：注释
- DocumentFragment：文档片段

#### 通过CSS选择器选取元素

```
document.querySelectorAll('.div');   //选择所有class为div的元素
document.querySelectorAll('[data-tip="title"]');    //选择所有data-tip为title的元素
document.querySelectorAll('div:not(.ignore)');  //选择所有claa不为ignore的div元素
```
不支持伪元素的选择器，比如：first-line和first-letter；也不支持伪类的选择器，比如：link和：visited。

## 文档结构的遍历
> Document对象、它的Element对象和文档中表示文本的Text对象都是Node对象。

#### Node属性：

- parentNode

作为**元素树**遍历，只遍历Element对象，不包含Text和Comment对象
- children：返回NodeList对象，children列表只包含Element对象。（下同）
- nextElementChild、lastElementChild
- nextElementSibling、previousElementChild
- childElementCount：返回子元素数量，同children.length
- offsetParent：返回最靠近当前元素的父元素，且此父元素position不为static

作为**节点树**遍历，因此会有Text和Comment对象。@不推荐🤮
- childNodes：返回只读类数组对象(NodeList对象)，包含Text和Comment。
- firstChild、lastChild：分别返回第一个子节点、最后一个子节点，同样包含Text和Comment
- nextSibling、previousSibling：分别返回下一个兄弟节点、前一个兄弟节点，包含Text和Comment
- textContent：返回该节点和它所有后代节点的文本内容
- nodeType：返回该节点类型代号-number
- nodeName：返回该节点类型名称-string
- nodeValue：返回Text和Comment的文本内容，其他类型的节点将返回null
### NodeList和HTMLCollection
NodeList实例对象可能是动态集合也可能是静态集合。DOM Tree 每新增或删除一个节点，都可以反映在NodeList接口中。NodeList实例对象提供length属性和数字索引，但不能使用pop（）、push（）之类数组特有的方法。

HTMLCollection实例对象同NodeList实例对象，也是节点的集合，返回类数组对象。

HTMLDocument类中，有一些属性可以快捷访问节点。比如images、forms、links属性指向类数组<img>、<form>、<a>元素集合，返回的都是HTMLCollection实例对象。


```
graph LR
A(HTMLDocument类)-->B(.images)
B-->BB(<.img>元素集合)
A-->C(.links)
C-->CC(<.a href=''>元素集合)
A-->D(.forms)
D-->DD(<.form>元素集合)
A-->E(.scripts)
E-->EE(<.script>元素集合)
A-->F1(.embeds或.plugins)
F1-->FF(<.embed>元素集合)

BB-->Z(HTMLCollection对象)
CC-->Z
DD-->Z
EE-->Z
FF-->Z
```
**注**:HTMLDocument是类名，调用的是类的实例如document

```
document.forms.length   //返回document文档里<form>个数
document.doby   //返回<body>
document.head   //返回<html>
document.documentElement    //返回<html>
```
|| HTMLDocument | NodeList
---|---|---
节点类型|Element| Element、Text、Comment
实例对象|只能是动态集合 |可动态可静态
索引方式|可数字还可class、id|只能数字索引
## 文档的内容

innerHTML：返回当前元素包含的Element+Text，可读可写

outerHTML:返回当前元素及当前元素包含的Element+Text，可读可写

textContext：返回当前元素中所有后代节点的所有纯文本，可读可写。若写的内容包含Element，如<.span>，文档节点不会改动，因为此时<.span>被当作纯文本处理而不是标签。
```
<div id="div"><p>123</p></div>
var d = document.getElementById('div');
d.innerHTML  // "<p>123</p>"
d.outerHTML // "<div id="div"><p>123</p></div>"
/*写innerHTML*/
d.innerHTML = '<span>99</span>'
// <div id="div"><span>99</span></div>
//标签被换了
```
insertAdjacentHTML(beforebegin|afterbegin|beforeend|afterend,'tag')

此方法可将HTML标记符插入到指定元素的指定位置，第一个参数为插入的位置，第二个参数为要插入的标签名称
![image](https://7n.w3cschool.cn/attachments/image/20170619/t_insertAdjacentHTML.png)
document.createElement('tag')：创建一个标签

document.createTextNode('these are some text ~')：创建文本节点

createAttribute('attribute','value');   为一个标签创建属性

cloneNode('tag',true|false); 复制一个标签，第二个参数可选，默认false（不复制子标签）

||appendChild(new)|insertBefore(new,old)
---|---|---|
相同点|都是在子元素列表中插入元素
不同点|在子元素列表的最后插入|在old元素前面插入new
**注**：如果要插入的节点是已存在与文档中，那么将从原来的位置移除插到指定位置。

parentNode.removeChild(childnode)：父元素调用此方法删除一个子元素

parentNode.replaceChild(newNode,oldNode)：父元素调用此方法，替换掉一个不需要的子元素。
> DocumentFragment是一种特殊的Node，它作为其他节点的一个临时的容器。DocumentFragment是独立的，而不是任何其他文档的一部分。它的parentNode总是为null。但类似Element，它可以有任意多的子节点，也可以使用appendChild()等方法。

DocumentFragment的特殊之处在于它使得一组节点被当做一个节点看待。

```
var frag = docment.createDocumentFragment();
```
## 坐标、尺寸
getBoundingClienRect()：返回一个rectangle对象，此对象有width、height、left、right、top、bottom

由于元素的默认position为static，是相对于viewport的（视口：实际显示DOM文档的部分——不包括浏览器的标签栏、搜索栏等），因此会随着页面滚动变化。实现位置固定的一种方法：left+window.scollX, top+window.scollY

elementFromPoint(X,Y)：返回在指定位置的一个元素

Element.scrollLeft属性表示网页元素的水平滚动条向右侧滚动的像素数

Element.scoollTop属性表示网页元素的垂直滚动条向下滚动的像素数
```
//查看整张网页的水平的和垂直的滚动距离
document.body.scrollLeft 
document.body.scrollTop
//这两个属性都可读可写
```
还可以用scrollBy(X, Y )控制网页的滚动

所有元素都有clientWidth、clientHeight属性，值为width+padding，不包含border、margin、滚动条

```
//没有垂直滚动条时 
document.documentElement.clientHeight === window.innerHeight // true  
```
> 对于<.i>、<.code>和<.span>这些内联元素，clientWidth和clientHeight总是0

scollWidth、scollHeight属性，值也是width+padding，但包括溢出内容的width

offsetWidth为clientWidth+border

#### Document属性
- domain    当前文档的域名
- lastModified  文档修改时间的字符串
- location  与window对象的located属性引用同一个location对象
- referree  返回一个字符串，表示访问本文档的来源。如果无法获取来源或用户直接键入网址，则返回空字符串
- title title节点之间的内容可读写
- doctype   document两个子节点的第一个子节点<!DOCTYPE html>
- documentElement   document两个子节点的第二个子节点<.html>
- defaultview   返回window对象
- activeElement 返回文档中当前获得焦点的那个元素
- characterset  返回渲染当前文档的字符集
- readyState    返回当前文档状态1loading加载HTML2interactive加载外部资源3complete加载完成
#### Document方法
- write()   writerIn()

可为标签设置contenteditable属性为true使其可被编辑

#### execCommand（aCommandName, aShowDefaultUI, aValueArgument）
功能：插入元素、改变样式

## HTML属性
- getAttribute('attr')  返回属性值
- seAttribute('attr', 'value') 为元素新增/修改属性
- hasAttribute('attr')  判断某元素是否有某属性，返回布尔值
- removeAttribute('attr')   为元素移除属性

#### 数据集（dataset）属性
在HTML5文档中，任意以'data-'为前缀的小写属性都是合法的

Element有一个dataset属性，Element.dataset对应一个对象，这个对象的属性对应于'data-'后面的部分，如果有多个-则用驼峰命名。

```
<div id="top" data-tip="title"></div>

var t=document.getElementById('top');
t.dataset.tip  //title
t.dataset.tip = 'title2'//该属性是实时双向的，任何改变都会影响标签原属性
```
#### attribute属性是只读类数组对象，索引方式有多种

```
document.body.attributes[0]  //<body>元素的第一个属性
document.body.attributes.bgcolor // <body>元素的bgcolor属性
document.body.attributes['ONLOAD']  // <body>元素的onload属性。
//同时，属性节点又有name(nodeName)和value（nodeValue）的属性
<div id="top"></div>
var t = document.getElemntById('top');
t.attributes[0].name  // "id"
t.attributes[0].nodeName // "id"
t.attributes[0].value  // "top"
t.attributes[0].nodeValue // "top"
```
## CSS
Element.style返回的值是一个CSSStyleDeclaration

```
<div id="top"></div>
var t = document.getElementById('top');
t.style.color = 'red';
//或
t.setAttribute('style','background:red;');
```
style对象的cssText也可以用来读写或删除整个style属性。

```
t.style.cssText = 'background:red';
```
**写法注意** 

 1.float在JS中是关键字，因此要写  style.cssFloat
 
 2.border-left-width要写 borderLeftWidth
 
 三个方法的第一个参数，都是CSS属性名，且不用改写连词线。

```
t.style.setProperty('background-color','red');
t.style.getPropertyValue('background-color');
t.style.removeProperty('background-color');
```
#### window.getComputedStyle()

可以用来获取CSS伪对象伪元素的样式，第一个参数是元素，第二个参数通常为null或空字符串，但也可以是 :before :after :first-line first-letter

```
<style>
  #top{ line-height:30px;}
  #top:before{content:'before';color:red};
</style>
<div id="top" style="background:red"></div>
var t = document.getElementById('top');
window.getComputedStyle(t,null).lineHeight  //30px 去掉连字符
window.getComputedStyle(t,null).getPropertyValue('line-height');  //30px，无需去掉连字符
window.getComputedStyle(t,':before').content  // "before"
```
