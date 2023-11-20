# CS571笔记：JavaScript 1

web programming

有用的文档

1.Mozilla's JS Docs

2.W3 Schools



Html Structure

CSS 设计

JS 行为

三大件基础

## 1.html

每个HTML元素有与之关联的属性，比如标识符。

img具有src的特殊属性，alt（替代文本）

名称介绍文本标识类似变量名，必须独一无二。

html是结构化的，非缩进敏感，但是最好好好缩进

服务器只是把你需要的HTML+CSS+JS传给你的电脑让你的电脑渲染他们

需要记住的tag：

html：封装头部和主体

h1~h6：标题级别

p：段落文本

strong，em：黑体和斜体（替代b和i）

a：超链接，anchor

img：图片

br：下一段（不用/br）

ul，ol，li：都是list，分别是无序，有序，普通

div：divisio，网站逻辑结构

推荐使用VS Code作为web的IDE，不过别的也行。vsc用ctrl+/快速注释

html的注释非常奇怪,尖括号+感叹号+横杠<!-- -->

一个table的组成：表头thead，表行tr，表头数据th，表体tbody，，表数据td。比如

```html
<table>
    <thead>
        <tr>
            <th>
            </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>
            </td>
        </tr>
    </tbody>
</table>
```

CSS中会有类（class）不要和Java的搞混

## 2.CSS

Cascading Style Sheets（级联样式表）

定义了我们如何涂抹我们的网站，设置它的风格

CSS前面的标签，（如：`#{ }`什么的）什么都没有，应用在html所有标签上，`#`：用于专门id，`.`：用于专门class

比如 `p {}`就是用于HTML中所有<p>上

可以混用，比如`p.intro`就是选择所有同时有<p>元素和class="intro"的

你可以在W3中找各种CSS颜色

如何使html与CSS协同？

内联：所有CSS与html一起定义

也可以搞嵌入CSS,在<style></style>里面定义，在html顶部定义，不过一般都是外部。

$会覆盖所有CSS默认值，！号是危险的，在不同浏览器或者不同版本上有细微区别

## 3.JS

历史：曾经人们只有静态网页，除了跳转做不了什么互动，Netscape开发了JS在10天内，现在我们仍旧遭受着这种折磨。JS有独特的历史，用起来也很奇怪。

JS是一种解释器语言，如果你熟悉Python就会比较熟悉这个。也就是没有编译步骤，在浏览器中作为JS工作而非字节码

JS是动态松散的语言，7种标准数据类型：

numbers，string，boolen，null，undefined，symbol，object。

用var（现在不使用了），let，const声明，const声明后不能再分配。可以使用typeof来知道目前该变量的数据类型。

三种语句：

​	1.if，else if 和 else

​	2.swtich

​	3.三目运算符 ？：

JS中的数据们具有真实性，只有null和undefined为假

符号：

​	===与！==（强比较）

​	==与！=(弱比较)   "0"==0 return ture

​	&&和||，也就是and和or

Object：

`let myTa = { name:"Hongtao",age:28}`用.访问，用类似`myTa['name']`也可以。非常像json

数组：

`let fruite = ["a","b"];`从0开始，可以push和pop。

for loop：

```javascript
for(let i = 0;i<10;i++){}
for(let attr in courser){}//in object
for(let item of arr){}//in array
```

后面两个是强loop，用的迭代器实现

也有while loop

函数

声明：

1.`function f(temp){ return temp+1; }`

2.`const fToC = function f(temp){ return temp+1; }`

3.`const fToC = (temp) => { return temp+1; }`

如何把JS与web连接起来呢？

三种方法，与CSS类似：

​	1.内联，如`<button onclick="console.log('hello word')">Click Me!</button>`

​	2.嵌入

​	3.脚本

操作文件

获得id来操作，如`let ttle = document.getElementbyId("articleTitle")`,之后就可以添加监听器，改变样式什么的

## 别的工具

TypeScript 相当于 JS + Type类型安全的

jQuery

Bootstrap