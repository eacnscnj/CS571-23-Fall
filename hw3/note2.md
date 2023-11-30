# JavaScript3

### 回忆：

命令型语言与声明型的区别

```javascript
const things = ["dogs", 1.2 , 0, false, {name:"Alice"}, -7]

let newThings1 = [];
//命令型
for(let thing of things){
    if(typeof thing === 'number'){
        newThings1.push(thing)
    }
}
//解释型
let newThings2 = things.filter(thing => typeof thing === 'number')
```

### 回调函数

`then` 和 `catch` 把回调函数作为参量

**定义:** 一个 *回调函数* (有时也叫 *函数引用*)传给另外一个函数当参数,然后在外部函数内部调用，以完成例程或操作。

```javascript
const name = prompt('Please enter your name.');
function processUserInput(callback) {
  alert("Incoming message!")
  callback(name);
}
function greeting1(name) {
  alert('Hello ' + name);
}
const greeting2 = (name) => {
  alert('Whats up ' + name);
}
processUserInput(greeting1);
processUserInput(greeting2);
processUserInput((name) => alert("Welcome " + name));

```

### `fetch()`

记住这个是异步的

```javascript
fetch(url)
  .then((response) => response.json()) // implict return
  .then((data) => {
    // fetch has already parsed data from JSON to a JS object!
    // Do something with the data
  })
  .catch(error => console.error(error)) // Print errors
```

## today

当你要反复使用一个逻辑，用命名函数。想在某个地方用一次然后结束，用匿名函数

### `slice(begI, endI)` 和 `concat(arr)`

`slice` 返回一个浅拷贝的副本并且包含可选择的开始下标和结束下表

```javascript
["apple", "banana", "coconut", "dragonfruit"].slice(1, 3); // ["banana", "coconut"]
```

`concat` 链接两个数组.

```javascript
["apple"].concat(["banana", "coconut"]); // ["apple", "banana", "coconut"]
```



### `some(cb)` 和 `every(cb)`

`some(cb)` 如果回调函数有至少一次返回真，则返回 `true` 

```javascript
["sam", "jacob", "jess"].some(p => p === "jess"); // true!
```

`every(cb)` 回调函数一直返回真，则返回 `true` 

```javascript
["sam", "jacob", "jess"].every(p => p === "jess"); // false!
```



### `reduce(cb, start)`

`reduce` 获得两个函数的回调 (前值和当前值) 和 一个起始值

```javascript
[2, 4, -1.1, 7.2].reduce((prev, curr) => prev + curr, 1.2); // 13.3
```

### 新建对象 和 `reduce`

```javascript
const fruits = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple'];
const countObj = fruits.reduce((acc, curr) => {
  acc[curr] = (acc[curr] || 0) + 1;
  return acc;
}, {});
console.log(countObj); // Output: { apple: 3, banana: 2, orange: 1 }
```

### `...` 扩展对象

我们可以扩展一个数组...

```javascript
const cats = ["apricat", "barnaby", "bucky", "colby"];

const newCats = [...cats, "darcy"];
```

### `??` 

如果运算符左边是 `null` 或 `undefined`, 把右边的拿去用.

```javascript
const IS_ENABLED = env.IS_ENABLED ?? true;

const USERNAME = document.getElementById("username").value ?? "";
```



与三目运算符的不同

```javascript
const IS_ENABLED = env.IS_ENABLED ? env.IS_ENABLED : true; // always true!
```

[Try it on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing)

## 数据复制

### 数据复制

`json.parse` 和 `json.stringify` 对深度复制非常有用.

```javascript
let dog = ... // some complex data we wish to preserve
let newDog = JSON.parse(JSON.stringify(dog));

newDog.age = 2                // does not change dog's age!如果是引用拷贝就会改变
newDog.name.first = "Thomas"; // does not change dog's name!如果是浅层拷贝就会改变
```

[When is deep copying with JSON.parse and JSON.stringify an issue?](https://lodash.com/)

[lodash is the preferred way to copy](https://stackblitz.com/edit/js-yqe3zb?file=index.js)

1.引用复制
2.浅复制
3.深度复制
回顾一下：变量是容器 -- 它们包含原始值或指向对象的指针

## 使用CSS库

什么是 CSS 库？
定义：抽象出面向用户元素的底层 CSS 实现的软件库。

一些流行的库包括...

- [Bootstrap](https://getbootstrap.com/)（大部分网站看着相似就是因为都使用了这个库）

- [Foundation](https://foundation.zurb.com/)

- [Semantic UI](https://semantic-ui.com/)

- [Pure](https://purecss.io/)

- [UIkit](https://getuikit.com/v2/)

  ### Boostrap如何工作？

  Bootstrap 为我们提供了...

  ​	布局
  ​	内容
  ​	组件
  ​	实用工具
  等等

  ### Bootstrap 分类：布局

  容器是布局中最基本的元素。

  ```html
  <div class="container">
    ...
  </div>
  ```

  

  ```html
  <div class="container-fluid">
    ...
  </div>
  ```

### 网格

通常，容器用行和列形成网格

*为列跨度

```html
<div class="container">
  <div class="row">
    <div class="col-*"></div>
    <div class="col-*"></div>
  </div>
</div>
```

[StackBlitz](https://stackblitz.com/edit/js-2wv34r?file=index.html)

#### 响应式设计

根据终端的屏幕大小确定不同的布局

```html
<div class="container">
  <div class="row">
    <div class="col-12 col-md-6 col-lg-3"></div>
    <div class="col-12 col-md-6 col-lg-3"></div>
    <div class="col-12 col-md-6 col-lg-3"></div>
    <div class="col-12 col-md-6 col-lg-3"></div>
  </div>
</div>
```

### content

Content 样式包括基本 HTML 元素、排版、代码、图片、表格和数字。

基本 HTML 示例：

```html
<h1></h1>
<ul></ul>
<input/>
<button></button>
```

它们将获得默认的 Bootstrap 风格。

### 别的元素样式

```html
<img src="..." class="img-fluid">
```



```html
<table class="table">
  <thead class="thead-dark">
    <tr>
      <th scope="col">...</th>
      ...
```



```html
<div class="table-responsive-sm">
  <table class="table">
  ...
```

### 组件

组件包括构成设计的所有其他视觉/交互元素，如按钮、表单、导航栏、工具提示等。

```html
<button type="button" class="btn btn-primary">Fill button</button>

<button type="button" class="btn btn-outline-primary">Outline button</button>

<div class="btn-group-toggle" data-toggle="buttons">
  <label class="btn btn-secondary active">
    <input type="checkbox" checked autocomplete="off"> Switch
  </label>
</div>
```

### 实用工具

实用工具本身并不是元素，但它们可以修改/控制其他元素，例如为图片添加圆角。

```html
<div class="shadow p-3 mb-5 bg-white rounded">Shadow</div>
<img src="..." class="rounded">
```

 图标：[icon libraries](https://getbootstrap.com/docs/4.3/extend/icons/)

### 其他资源

- [Bootstrap Documentation](https://getbootstrap.com/docs/4.3/getting-started/introduction/)
- [Tutorial Republic](https://www.tutorialrepublic.com/twitter-bootstrap-tutorial/)
- [W3 Schools](https://www.w3schools.com/bootstrap/default.asp)