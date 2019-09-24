# python学习


---

# 基础


---


## list
> 有序集合，类似数组

### len()
> 获取长度

```
names = ["ly","zf","cjq","yq"]
len(names) // 3
```

### 方法
- names.[i] 获取
- names.append("wzl") 在末尾添加
- names.insert(1, "dj") 在下标为1插入
- names.pop() 删除最后一个
- names.pop(i) 删除第i个


---


## tuple
> 与list类似，不能修改，元素必须被确定下来

- 被固定的只是指向
- 内容可以被修改，只要指向不变

### 定义
```
t = (1, 2, 3)
t = ()
// 定义一个元素时
t = (1, )
```

---


## if

```
if xxx:
    xxx
elif xxx:
    xxx
else:
    xxx
```

---


## input()
- input()返回的类型是string


---


## for
```
for x in [1,2,3]:
    xxx
```

### range()
> 生成一个整数序列

### list()
> 将一个序列转换成list(集合)

```
list(range(5))
[1,2,3,4,5]
```


---


## while
```
while xxx:
    xxx
```


---


## break
> 退出

## continue
> 跳过


---


## dict
> 字典：类似map，json之类的键值对的数据类型 { "key" : "value" }

- key值不存在则报错，不可对不存在的key赋值

```
d = {"数学": 20, "语文": 50, "英语": 60}
d["数学"] // 20
d["数学"] = 70
```

### in
> 判断key是否存在
```
"历史" in d // false
```

### get()
> 不存在返回None，或者自己指定返回值

- None在交互环境不显示结果
```
d.get("历史", -1) // 不存在返回-1
```

### pop(key)
> 删除key键值对
```
d.pop("英语") // 60
```


---


## set
> 一组key的集合，没value，key不能重复

- set会自动过滤重复元素
```
s = set([1,2,3])
// {1,2,3}
```

### add(key)
> 添加
```
s.add(4)
// {1,2,3,4}
```

### romeve(key)
> 删除
```
s.remeve(4)
{1,2,3s}
```

### & 交集 ，| 并集
```
s1 = set([1,2,3])
s2 = set([2,3,4])
s1 & s2 // {2,3}
s1 | s2 // {1,2,3,4}
```

## 不可变对象

### sort()
> 排序

### replace(x, x)
> 替换元素

- a没有改变
- replace返回新字符串
```
a = "abc"
a.replace("a", "A")
// "Abc"
a
??

```


---



# 函数


---


## 调用函数


### abs()
> 返回一个数的绝对值

- 只能传一个值
- 只能是数字

### max(1,2,3)
> 返回最大的一个数

### 类型转换函数
- int("123")
- float("12.123")
- str(111)
- bool(1)
- hex(1) 转换成十六进制


---


## 定义函数
```
def 函数名(变量):
    执行语句
    // 默认返回None
    return None
// 调用
函数名()

// 导入存在“函数文件”中的函数
from 函数文件 import 函数名
// 调用
函数名()
```

### pass
> 占位符，什么都不做，空函数
```
def nop():
    pass
```

### isinstance()
> 对数据类型检查
```
def my_abs(x):
    if not isintance(x, (int, float)):
        执行语句
```


---


## import
> 导入包

### math
> 一些数学公式的包

- math.sin()
- math.cos()
- math.pi
```
import math
```


---


## 函数传参

### 默认值
```
def cal(x, n = 2):
    xxx
```

### 可变参数
```
def clac(*numbers):
    xxx
```

```
nums = [1,2,3]
calc(*nums)
```

### **
