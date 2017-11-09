# jQuery

标签： 复习

---

## 简介

### 什么是jQuery?

    jQuery是一个JavaScript函数库。
    jQuery是一个轻量级的"写的少，做的多"的JavaScript库。
    
* jQuery库包含以下功能：
    * HTML 元素选取
    * HTML 元素操作
    * CSS 操作
    * HTML 事件函数
    * JavaScript 特效和动画
    * HTML DOM 遍历和修改
    * AJAX
    * Utilities

## jQuery - 链

    通过 jQuery，可以把动作/方法链接在一起。
    Chaining 允许我们在一条语句中运行多个jQuery方法（在相同的元素上）。

* 把 `css()`、`slideUp()` 和 `slideDown()` 链接在一起。"p1" 元素首先会变为红色，然后向上滑动，再然后向下滑动：

```
$("#p1").css("color","red").slideUp(2000).slideDown(2000);
```

## 遍历

### 祖先 -- 遍历

* parent() 方法返回被选元素的直接父元素。
* parents() 方法返回被选元素的所有祖先元素，它一路向上直到文档的根元素 (<html>)。
* parentsUntil() 方法返回介于两个给定元素之间的所有祖先元素。

### 后代 -- 遍历

* children() 方法返回被选元素的所有直接子元素。
* find() 方法返回被选元素的后代元素，一路向下直到最后一个后代。

### 同胞 -- 遍历

* siblings() 方法返回被选元素的所有同胞元素。
* next() 方法返回被选元素的下一个同胞元素。
* nextAll() 方法返回被选元素的所有跟随的同胞元素。
* nextUntil() 方法返回介于两个给定参数之间的所有跟随的同胞元素。

## 添加元素

### 添加新的 HTML 内容

* append() - 在被选元素的结尾插入内容
* prepend() - 在被选元素的开头插入内容
* after() - 在被选元素之后插入内容
* before() - 在被选元素之前插入内容

### 删除元素

* remove() - 删除被选元素（及其子元素）
* empty() - 从被选元素中删除子元素

## 获取并设置 CSS 类

### 操作 CSS

* addClass() - 向被选元素添加一个或多个类
* removeClass() - 从被选元素删除一个或多个类
* toggleClass() - 对被选元素进行添加/删除类的切换操作
* css() - 设置或返回样式属性

#### toggleClass() 方法

    toggleClass() 方法是对被选元素进行添加/删除类的切换操作。

```
$("button").click(function(){
  $("h1,h2,p").toggleClass("blue");
});
```

#### css() 方法

    css() 方法设置或返回被选元素的一个或多个样式属性。
    
* 返回指定的 CSS 属性的值

```
$("p").css("background-color");
```

* 设置 CSS 属性

```
$("p").css("background-color","yellow");
```

## 遍历

* `.each()` 遍历数组

```
$(function () { 
    $.each([52, 97], function(index, value) {
        alert(index + ': ' + value);
    });
})
```

## Ajax

```
<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.js"></script>
<script type="text/javascript">
    $(function () {
        $.ajax({
            type:'get',
            url:'http://106.14.213.216:8080/positions',
            data:{},
            dataType:'json',
            contentType:'application/x-www-form-urlencoded',
            async:false, //true 异步;false 同步
            beforeSend:function () {
              alert("正在进行,请稍候...");
            },
            success:function (res) {
                document.write(JSON.stringify(res));
            },
            error:function () {
                alert('error');
            },
            complete:function () {
                alert('complete');
                // 请求完成!
            }
        });
        
//      $.get(url,function (res) {
//        console.log(res);
//      })
    })
</script>
```