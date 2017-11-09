# JavaScript

标签： 复习

---

### JavaScript的三大组成部分是：

1、ECMAScript：JavaScript的核心;
2、文档对象模型（DOM）：DOM（文档对象模型）是 HTML 和 XML 的应用程序接口（API）。
3、浏览器对象模型（BOM）对浏览器窗口进行访问和操作。

### 数据类型

* 五种基本数据类型
```
 undefined,null,boolean,number,string
```
* 一种复杂数据类型
```
 object
```
#### `typeof` 操作符
```
"undefined" —— 如果这个值未定义
"boolean" —— 如果这个值是布尔值 (true|false)
"string" —— 如果这个值是字符串
"number" —— 如果这个值是数值
"object" —— 如果这个值是对象或null
"function" —— 如果这个值是函数
```
* 检测类型
```
var s = "china";
var b = true;
var i = 22;
var u;
var n = null;
var o = new Object();
var f = function () {}
// 输出基本数据类型
console.log(typeof s); // string
console.log(typeof b); // boolean
console.log(typeof i); // number
console.log(typeof u); // undefined
console.log(typeof n); // object
console.log(typeof o); // object
console.log(typeof f); // function
// 输出变量是什么类型的对象
var s = new String("china");
var c = "china";
console.log(s instanceof String); // true 变量s是String吗？
console.log(c instanceof String); // false 变量c是String吗？
```

> 从技术角度上讲，函数在js中是对象，不是一种数据类型。然而，函数也确实有一些特殊的属性，因此通过`typeof`操作符来区分函数和其他对象是有必要的。

#### String 类型
* 去除两端空格

> `trim();` 这个方法会创建一个字符串的副本,删除前置及后缀的所有空格,然后返回结果

* 转换大小写

> `toLocaleLowerCase()` // 小写
`toLocaleLowerCase()` // 大写

<table class="reference">
<tbody><tr>
<th style="width:24%">方法</th>
    <th>描述</th>
  </tr>
<tr>
<td>charAt()</td>
    <td>返回指定索引位置的字符</td>
  </tr>
<tr>
<td>concat()</td>
    <td>连接两个或多个字符串，返回连接后的字符串</td>
  </tr>
<tr>
<td>indexOf()</td>
    <td>返回字符串中检索指定字符第一次出现的位置</td>
  </tr>
<tr>
<td>lastIndexOf()</td>
    <td>返回字符串中检索指定字符最后一次出现的位置</td>
  </tr>
<tr>
<td>match()</td>
    <td>找到一个或多个正则表达式的匹配</td>
  </tr>
<tr>
<td>replace()</td>
    <td>替换与正则表达式匹配的子串</td>
  </tr>
<tr>
<td>search()</td>
    <td>检索与正则表达式相匹配的值</td>
  </tr>
<tr>
<td>slice()</td>
    <td>提取字符串的片断，并在新的字符串中返回被提取的部分</td>
  </tr>
<tr>
<td>split()</td>
    <td>把字符串分割为子字符串数组</td>
  </tr>
<tr>
<td>substr()</td>
    <td>从起始索引号提取字符串中指定数目的字符</td>
  </tr>
<tr>
<td>substring()</td>
    <td>提取字符串中两个指定的索引号之间的字符</td>
  </tr>
<tr>
<td>toLowerCase()</td>
    <td>把字符串转换为小写</td>
  </tr>
<tr>
<td>toString()</td>
    <td>返回字符串对象值</td>
  </tr>
<tr>
<td>toUpperCase()</td>
    <td>把字符串转换为大写</td>
  </tr>
<tr>
<td>trim()</td>
    <td>移除字符串首尾空白</td>
  </tr>
<tr>
<td>valueOf()</td>
    <td>返回某个字符串对象的原始值</td>
  </tr>
</tbody>
</table>

#### Boolean 类型

<table>
<tr>
<td>数据类型</td>
<td>转换为true的值</td>
<td>转换为false的值</td>
</tr>
<tr>
<td>boolean</td>
<td>true</td>
<td>false</td>
</tr>
<tr>
<td>string</td>
<td>任何非空字符串</td>
<td>""(空字符串)</td>
</tr>
<tr>
<td>numberr</td>
<td>任何非零数字值(包括无穷大)</td>
<td>0和NaN</td>
</tr>
<tr>
<td>Object</td>
<td>任何对象</td>
<td>null</td>
</tr>
<tr>
<td>undefined</td>
<td>无</td>
<td>undefined</td>
</tr>
</table>

#### 数值转换

> 有三个函数可以把非数值转换为数值
```
number(), parseInt(),parseFloat()
// number()可以用于任何数据类型
// parseInt()和parseFloat()专门用于把字符串转换成数值,第二个参数可以选择进制[parseInt("ff",10)],默认为十进制。
```

#### 一元操作符

```
var a = 12;
a++; // a等于12;
++a; // a等于13;
```
#### 类型转换
```
var myVar = "3.14159";
string: ''+myVar;
Number: +myVar;
Inter: ~~myVar;
float: 1 * myVar;
```
> `num.toFixed(2)` // 保留两位小数。

#### Math 对象

##### 舍入方法

```
Math.ceil(25.9); // 执行向上舍入; 26
Math.ceil(25.1); // 26
Math.floor(25.9); // 执行向下舍入;25
Math.floor(25.1); // 25
Math.round(25.9); // 执行标准舍入;四舍五。// 26
Math.round(25.1); // 25
```
##### random() 取随机数

```
Math.random(); // 返回大于等于0小于1的随机数;
```

### 循环

#### while 循环
```
let i = 0;
while ( i < 10) {
    i += 2; // i = i + 2;
}
```
> 只要i小于10循环就不会结束。

#### for in 和 for of
```
var array = [1,2,3];

for(let item  in array){
    console.log(item); // item 数组下标;可以遍历到原型列！
}

for(let item  of array){
    console.log(item); // item 数组内容
}
```

#### break 和 continue
> `break` 会立即退出循环，强制继续执行循环后面的语句。
`continue` 会立即退出循环，但退出循环后会从循环的顶部继续执行。

#### switch

```
var i = 5;
switch (i) {
    case 2:
        console.log('2');
        break;
    case 3:
    /*合并两种条件*/
    case 4:
        console.log('4');
        break;
    case 5: // i = 5; 执行该语句
        console.log('5');
        break;
    default:
        console.log('7');
}

```
### Array 对象

> `forEach()`	数组每个元素都执行一次回调函数。
`indexOf()`	搜索数组中的元素，并返回它所在的位置。
`join()`	把数组的所有元素放入一个字符串。
`pop()`	删除数组的最后一个元素并返回删除的元素。
`push()`	向数组的末尾添加一个或更多元素，并返回新的长度。
`shift()`	删除并返回数组的第一个元素。
`unshift()`	向数组的开头添加一个或更多元素，并返回新的长度。
`slice()`	选取数组的的一部分，并返回一个新数组。
`sort()`	对数组的元素进行排序。
`splice()`	从数组中添加或删除元素。

### 日期格式化
```
var s = new Date(); // 获取当前时间

console.log(s.toDateString()); // Thu Oct 19 2017
console.log(s.toTimeString()); // 00:04:52 GMT+0800 (马来西亚半岛标准时间)
console.log(s.toLocaleDateString()); // 2017-10-19
console.log(s.toLocaleTimeString()); // 00:04:52
console.log(s.toUTCString()); // Wed, 18 Oct 2017 16:04:52 GMT
```
### 正则表达式(RegExp)
> `search`	检索与正则表达式相匹配的值。
`match`	找到一个或多个正则表达式的匹配。
`replace`	替换与正则表达式匹配的子串。
`split`	把字符串分割为字符串数组。

* **i 不区分大小写; g 全局匹配。**
```
var str = "welcome to China";
var m = str.match(/c/gi); // [ 'c', 'C' ]
var s = str.search(/c/gi); // 3
var r = str.replace(/c/gi, "a"); // welaome to ahina
var sp = str.split(/to/gi); // [ 'welcome ', ' China' ]
```

### BOM

> BOM的核心对象是window。

#### 窗口位置
> `screenLeft`和`screenTop`分别用于表示窗口相对于屏幕左边和上边的位置。

#### 窗口大小
> `innerWidth` 和 `innerHeight` 浏览器视图区大小（减去边框宽度）。

#### 打开窗口
> `window.open()` 

#### location 对象

```
location.host // 返回服务器名称和端口号（如果有）。
location.href // 返回当前页面的完整URL。
location.port // 返回URL中的端口号。

location.reload(); // 刷新当前页面
```

#### screen 对象

```
screen.height // 屏幕的像素高度
screen.width // 屏幕的像素高度
screen.left // 屏幕距左边的像素距离
screen.top // 屏幕距上边的像素距离
```

#### history 对象
> 保存用户上网的历史记录,从窗口被打开开始。
```
history.go(-1); // 后退一页
history.go(1); // 前进一页
history.go(2); // 前进两页

history.back(); // 后退一页
history.forward(); // 前进一页
```

### DOM

> DOM 可以将任何 HTML 或 XML 文档描绘成一个由多层节点构成的结构。

#### 查找 HTML 元素

```
document.getElementById("intro"); // 通过 id 查找 HTML 元素
getElementsByTagName("p"); // 通过标签名查找 HTML 元素
document.getElementsByClassName("intro"); // 通过类名找到 HTML 元素

```

#### 改变 HTML 内容

```
document.getElementById(id).innerHTML = "新的 HTML";
```

#### 改变 HTML 属性

```
document.getElementById(id).attribute = "新属性值"; //attribute 属性

// 例子
document.getElementById("image").src="landscape.jpg";
```

#### 改变 HTML 样式

```
document.getElementById(id).style.property = "新样式";

// 例子
document.getElementById("p2").style.color="blue";
document.getElementById("p2").style.fontFamily="Arial";
document.getElementById("p2").style.fontSize="larger";
```
#### addEventListener() 方法

> `addEventListener()` 方法用于向指定元素添加事件句柄。
`addEventListener()` 方法添加的事件句柄不会覆盖已存在的事件句柄。
`addEventListener()` 方法可以更简单的控制事件（冒泡与捕获）。

```
// 语法
element.addEventListener(event, function, useCapture);
```
> 第一个参数是事件的类型 (如 "click" 或 "mousedown").
第二个参数是事件触发后调用的函数。
第三个参数是个布尔值用于描述事件是冒泡还是捕获。该参数是可选的。

```
// 实例
document.getElementById("myBtn").addEventListener("click", displayDate);
```
#### 创建新的 HTML 元素
```
document.createElement('span'); // 创建节点

// 实例
<script>
    var para=document.createElement("p");
    var node=document.createTextNode("这是一个新段落。");
    para.appendChild(node);
    
    var element=document.getElementById("div1");
    element.appendChild(para);
    
    // 删除已有的HTML元素
    var parent=document.getElementById("div1");
    var child=document.getElementById("p1");
    parent.removeChild(child);
</script>

```

### DOM 扩展

#### querySelector() 方法

> `querySelector()` 方法返回文档中匹配指定 CSS 选择器的一个元素。

*  `querySelector()` 方法仅仅返回匹配指定选择器的第一个元素。如果需要返回所有的元素，使用 `querySelectorAll()` 方法替代。

```
// 实例
document.querySelector("#demo"); // 获取文档中 id="demo" 的元素。
document.querySelector(".demo"); // 获取文档中 class="demo" 的元素。
```