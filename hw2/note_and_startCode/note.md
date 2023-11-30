# CS571之JavaScrip2

### 扩展资料

MDN文档

### 如何与API和JSON数据工作

什么是json？

JSON（JavaScript Object Notation），实际上只是一个结构化字符串

`JSON.parse` JSON String ---> JS Object

`JSON.stringify` JS Object ---> JSON String

什么是API？

API（application programming interface）应用程序编程接口

与服务器的通信的一种方式，我们与数据库之间的中间人

如何进行一次API请求呢？

用链接打开

cURL，从url中得到数据

用postman（有用户界面的cURL）

请求JSON：

请求可以同步或者异步，异步最常用

我们

现在用 `fetch` 做异步请求（15年以前用XMLHttpRequest）

```javascript
fetch(url)
	.then((response)=>response.json())//head，得到返回值并把JSON留下来给后面用
	.then((data) => {})//body，进行操作
	.catch(error => console.error(error))
```

可以使用 `innerHTML` 等对返回的数据进行操作

回调函数把一个函数传递给一个函数

在JS中我们主要是声明式编程（指定what happen），而java和C sharp中主要是命令式编程（指定how）

