# JavaScript 代码规范

> 参考Airbnb, AlibabaGroup

## 目录
<a name="table-of-contents"></a>

1. [命名风格](#namingStyle)

1. [引用](#references)

1. [对象](#object)

1. [数组](#array)

1. [解构](#destructuring)


## 命名风格
<a name="namingStyle"></a>

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

**[⬆ 返回目录](#table-of-contents)**

## 引用
<a name="references"></a>
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

### 【强制】对于需要再次修改的变量，使用`let`代替`var`

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

**[⬆ 返回目录](#table-of-contents)**

## 对象
<a name="object"></a>

### 【强制】使用字面量创建对象
正例：
```js
const item = {};
```
反例：
```js
const item = new Object();
```

### 【强制】使用对象方法的简写
正例：
```js
const atom = {
  value: 1,
  
  addValue(value) {
    return atom.value + value
  }
}
```
反例：
```js
const atom = {
  value: 1,
  
  addValue: function(value) {
    return atom.value + value
  }
}
```

### 【强制】使用对象值的简写
> 这样写更具有描述性
```js
const lukeSkywalker = 'luke Skywalker'
```
正例：
```js
const obj = {
  lukeSkywalker
}
```
反例：
```js
const obj = {
  lukeSkywalker: lukeSkywalker
}
```

###【强制】在对象属性声明前
> 这样能清楚地看出哪些属性使用了简写
```js
const anakinSkywalker = 'Anakin Skywalker';
const lukeSkywalker = 'Luke Skywalker';
```
正例：
```js
const obj = {
  lukeSkywalker,
  anakinSkywalker,
  episodeOne: 1,
  twoJedisWalkIntoACantina: 2,
  episodeThree: 3,
  mayTheFourth: 4,
};
```
反例：
```js
const obj = {
  episodeOne: 1,
  twoJedisWalkIntoACantina: 2,
  lukeSkywalker,
  episodeThree: 3,
  mayTheFourth: 4,
  anakinSkywalker,
};
```
**[⬆ 返回目录](#table-of-contents)**

## 数组
<a name="array"></a>

### 【强制】使用字面量创建数组
正例：
```js
const items = []
```
反例：
```js
const items = new Array()
```

### 【强制】使用拓展运算符`...`复制数组
正例：
```js
const itemsCopy = [...items]
```
反例：
```js
const itemsCopy = []

for (let i = 0; i< items.length; i++) {
  itemsCopy[i] = items[i]
}
```
**[⬆ 返回目录](#table-of-contents)**

## 解构
<a name="destructuring"></a>

### 【强制】使用解构存取和使用多属性对象
> 能减少临时引用属性
正例：
```js
function getFullName(user) {
  const { firstName, lastName } = obj
  return `${firstName} ${lastName}`
}

// 最佳
function getFullName({ firstName, lastName }) {
  return `${firstName} ${lastName}`
}
```
反例：
```js
function getFullName(user) {
  const firstName = user.firstName
  const lastName = user.lastName
  
  return `${firstName} ${lastName}`
}
```

### 【强制】对数组使用解构赋值
```js
const arr = [1,2,3,4]
```
正例：
```js
const [first, second] = arr
```
反例：
```js
const first = arr[0]
const second = arr[1]
```

### 【强制】需要回传多个值时，使用对象解构，而不是数组解构
> 增加属性或者改变排序不会改变调用时的位置
正例：
```js
function processInput(input) {
  return { left, right, top, bottom }
}
// 调用时只需要选择需要的数据
const { left, right } = processInput(input)
```
反例：
```js
function processInput(input) {
  return [left, right, top, bottom]
}
// 调用时需要考虑回调数据的顺序
const [left, _, top] = processInput(input)
```

**[⬆ 返回目录](#table-of-contents)**