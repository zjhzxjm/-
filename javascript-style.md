# JavaScript 代码规范

> 参考Airbnb, AlibabaGroup

## 目录

1. [命名风格](#namingStyle)

1. [引用](#references)


<a name="namingStyle"></a>
## 命名风格

### 【强制】代码中的命名均不能以下划线或美元符号开始，也不能以下划线或美元符号结束

反例：
```js
_name / __name / $name / name_ / name$ / name__
```

### 【强制】代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式

> 正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式也要避免采用

正例：
```js
alibaba / taobao / hangzhou 等国际通用的名称，可视同英文
```
反例：
```js
DaZhePromotion [打折] / getPingfenByName() [评分] / int 某变量 = 3
```

### 【强制】方法名、参数名、成员变量、局部变量都统一使用 lowerCamelCase 风格，必须遵从驼峰形式

正例：
```js
localValue / getHttpMessage() / inputUserId
```

### 【强制】常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长

正例：
```js
MAX_STOCK_COUNT
```
反例：
```js
MAX_COUNT
```

### 【强制】杜绝完全不规范的缩写，避免望文不知义

反例：AbstractClass“缩写”命名成 AbsClass；condition“缩写”命名成 condi，此类随
意缩写严重降低了代码的可阅读性

<a name="references"></a>
## 引用

### 【强制】使用`const`，不要使用var

> 确保引用不会被修改，避免不必要的bugs

正例：
```js
const a = 1
const b = 2
```

反例：
```js
var a = 1
var b = 2
```

### 【强制】对于需要再次修改的变量，使用`let`代理`var`

> `let`是块级作用域，而`var`是函数作用域

正例：
```js
let count = 1
if(true) {
  count += 1
}

```
反例：
```js
var count = 1
if(true) {
  count += 1
}
```

