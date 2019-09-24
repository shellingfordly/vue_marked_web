# css

---

## 视口
> <meta name="viewport" content="width=device-width initial-scale=1 minimum-scale=1 aximum-scale=1 user-scalable=no">

- initial-scale 初始比列
- minimum-scale 允许缩放的最小比例
- maximum-scale 允许缩放的最大比例
- user-scalable 是否允许缩放(yes/no || 1/0)

> 兼容：<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">

## 自适应em/rem
当网页窗口小于500px时改变

```
@media screen and (min-width:500px){
    html { font-size: 100px; }
}
```

使用js获取窗口宽度

```
let html = document.querySelector("html");
changeRem();
window.addEventListener("resize",changeRem);
function changeRem(){
    //获取设备宽度
    let width = html.getBoundingClientRect().width;
    html.style.fontSize = width/10 + "px";
}
```

