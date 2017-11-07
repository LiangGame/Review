# CSS & CSS3

标签： 模拟面试

---

## 1.如何实现垂直居中?

> 为实现良好的兼容性，PC端实现垂直居中的方法一般是通过绝对定位，`table-cell`，负边距等方法。

```
 // HTML结构：
<div class="box box1">
    <span>垂直居中</span>
</div>
```

* 方法1：table-cell

```
// CSS:
.box1{
    display: table-cell;
    vertical-align: middle;
    text-align: center;        
}
```
* 方法2：display:flex
```
.box2{
    display: flex;
    justify-content:center; // 主轴
    align-items:Center;  // 交叉轴
}
```
* 方法3：绝对定位和负边距
```
.box3{position:relative;}
.box3 span{
    position: absolute;
    width:100px;
    height: 50px;
    top:50%;
    left:50%;
    margin-left:-50px;
    margin-top:-25px;
    text-align: center;
}
```
* 方法4：绝对定位和0
```
.box4 span{
  width: 50%; 
  height: 50%; 
  background: #000;
  overflow: auto; 
  margin: auto; 
  position: absolute; 
  top: 0; left: 0; bottom: 0; right: 0; 
}
```
* 方法5：translate
```
.box6 span{
    position: absolute;
    top:50%;
    left:50%;
    width:100%;
    transform:translate(-50%,-50%);
    text-align: center;
}
```
* 方法6：display:inline-block
```
.box7{
  text-align:center;
  font-size:0;
}
.box7 span{
  vertical-align:middle;
  display:inline-block;
  font-size:16px;
}
.box7:after{
  content:'';
  width:0;
  height:100%;
  display:inline-block;
  vertical-align:middle;
}
```
* 方法7：display:flex和margin:auto
```
.box8{
    display: flex;
    text-align: center;
}
.box8 span{margin: auto;}
```
* 方法8：display:-webkit-box
```
.box9{
    display: -webkit-box;
    -webkit-box-pack:center;
    -webkit-box-align:center;
    -webkit-box-orient: vertical;
    text-align: center
}
```
* 方法9：display:-webkit-box
```
<div class="floater"></div>  
<div class="content"> Content here </div>  

// CSS
.floater {
    float:left; 
    height:50%; 
    margin-bottom:-120px;
}
.content {
    clear:both; 
    height:240px; 
    position:relative;
}
```
## 2. 什么是FOUC?如何解决？

> 如果使用import方法对CSS进行导入,会导致某些页面在Windows 下的Internet Explorer出现一些奇怪的现象:以无样式显示页面内容的瞬间闪烁,这种现象称之为文档样式短暂失效(Flash of Unstyled Content),简称为FOUC。

* 原因大致为：

> 1，使用import方法导入样式表。
2，将样式表放在页面底部
3，有几个样式表，放在html结构的不同位置。

其实原理很清楚：当样式表晚于结构性html加载，当加载到此样式表时，页面将停止之前的渲染。此样式表被下载和解析后，将重新渲染页面，也就出现了短暂的花屏现象。

* 解决方法：
> 使用LINK标签将样式表放在文档HEAD中;或将css文件放在CDN服务器上。

```
<link rel="stylesheet" href="style.css">
```

## 3. 什么是DIV高度塌陷？，如何解决？

* 如果父元素只包含浮动元素，且父元素未设置高度和宽度，那么它的高度就会塌缩为零，也就是所谓的“高度塌陷”。

> 解决“高度塌陷”问题的方法：

1.浮动父级元素，父级元素的高度就会扩大，直到完全包含它里面的浮动元素。如果使用这种方法，一定要在该元素的下个元素添加`clear:both`,确保浮动元素落到父级元素的下方。 

2.使用`overflow:hidden,zoom:1`,`overflow:hidden`属性会强制父级元素扩大到包含浮动元素，`zoom:1`只是触发IE6的`hasLayout`模式，不会对其他浏览器产生影响。
```
{ 
　　overflow:hidden; 
　　zoom:1; 
}
```

3.使用`:after`伪类清除，不会影响其他任何样式，通用性强。
```
.clearfix{ 
　　zoom:1; 
} 
.clearfix:after{ 
　　content:''; 
　　display:block; 
　　height:0; 
　　clear:both; 
　　overflow:hidden; 
}
```

## 4.如何实现中间div宽度固定，两端div自适应宽度？说出2种方法
* float法

> 通过使两边的div左右浮动，脱离文档流，再为中间的div设置margin-left,margin-right值为左右div的宽度即可.此处应该注意的是中间div在代码中的位置，应该放在最后。存在问题：在屏幕宽度减少至一定程度后，右边div会错位，另起一行。
```
/*float法*/
.float .left {
    float: left;
    height: 200px;
}
.float .center {
    margin: 0 400px;
    height: 200px;
}
.float .right {
    float: right;
    height: 200px;
}
```

* display:flex法

```
<style type="text/css">
    .container{
        width: 100%;
        height: 500px;
        display: flex;
    }
    .div01,.div03{
        background: black;
        flex: auto;
    }
    .div02{
        background: red;
        width: 220px;
    }
  </style>  

<div class="container">
    <div class="div01"></div>
    <div class="div02"></div>
    <div class="div03"></div>
</div>


// 使用"display: flex"声明使用弹性盒布局。
        
        
//  CSS 属性声明"flex-direction"用来确定主轴的方向:
// row（默认值）主轴为水平方向。排列顺序与页面的文档顺序相同。如果文档顺序是 ltr，则排列顺序是从左到右；如果文档顺序是rtl，则排列顺序是从右到左。
// row-reverse	主轴为水平方向。排列顺序与页面的文档顺序相反。
// column	主轴为垂直方向。排列顺序为从上到下。
// column-reverse	主轴为垂直方向。排列顺序为从下到上。

        
// CSS 属性"flex-wrap"用来声明当容器中条目的尺寸超过主轴尺寸时应采取的行为。
// nowrap（默认值）容器中的条目只占满容器在主轴方向上的一行，可能出现条目互相重叠或超出容器范围的现象。
// wrap	当容器中的条目超出容器在主轴方向上的一行时，会把条目排列到下一行。下一行的位置与交叉轴的方向一致。
// wrap-reverse	与wrap的含义类似，不同的是下一行的位置与交叉轴的方向相反。
```

## 5.描述css reset的作用和用途。

    Reset重置浏览器的css默认属性。浏览器的品种不同，样式不同;然后重置，让他们统一 。
    
## 6.解释css sprites，如何使用。 

    Css 精灵 把一堆小的图片整合到一张大的图片上，减轻服务器器对图片的请求数量;其实就是把网页中一些背景图片整合到一张图片文件中，再利用CSS的“background-image”，“background-repeat”，“background-position”的组合进行背景定位，background-position可以用数字精确的定位出背景图片的位置。 

## 7.清除浮动的几种方式，各自的优缺点 。

* 使用空标签清除浮动 clear:both（理论上能清楚任何标签，增加无意
义的标签） 
* 使用overflow:auto（空标签元素清除浮动而不得不增加无意代码的弊端,
使用zoom:1用于兼容IE） 
* 使用afert伪元素清除浮动(用于非IE浏览器) 

## 8.你能描述一下渐进增强和优雅降级之间的不同吗?

```
.transition{ 
    -webkit-transition: all .5s;  // 谷歌
    -ms-transition: all .5s;   // IE
    -moz-transition: all .5s;  // 火狐
    -o-transition: all .5s;    // 欧朋
    transition: all .5s;       // 统一标准
 } 
```
* 渐进增强 

        progressive enhancement：针对低版本浏览器进行构建页面，保证最基本的功能，然后再针对高级浏览器器进行效果、交互等改进和追加功能达到更好的用户体验。 
* 优雅降级  

        graceful degradation：一开始就构建完整的功能，然后再针对低版本浏览器器进行兼容。 
> 区别： 
优雅降级是从复杂的现状开始，并试图减少用户体验的供给，而渐进增强则是从一个非常基础的，能够起作用的版本开始，并不断扩充，以适应未来环境的需要。降级（功能衰减）意味着往回看；而渐进增强则意味着朝前看，同时保证其根基处于安全地带。

## 9.行内元素有哪些？块级元素有哪些？ 空(void)元素有那些？

    首先：CSS规范规定，每个元素都有display属性，确定该元素的类型，每个元素都有默认的display值，如div的display默认值为“block”，则为“块级”元素；span默认display属性值为“inline”，是“行内”元素。 
    
 （1）行内元素有：`a b span img input select strong（强调的语气）`
 （2）块级元素有： `div ul ol li dl dt dd h1 h2 h3 h4…p` 
 （3）常见的空元素：  `<br> <hr> <img> <input> <link> <meta>` 
 
 * 鲜为人知的是： 
 `<area> <base> <col> <command> <embed> <keygen> <param>
<source> <track> <wbr> `

## 10.页面导入样式时，使用link和@import有什么区别？

（1）link属于XHTML标签,除了加载CSS外,还能用于定义RSS,定义rel连接属性等作用;而@import是CSS提供的,只能用于加载CSS。
（2）页面被加载的时,link会同时被加载,而@import引用的CSS会等到页面被加载完再加载。
（3）import是CSS2.1提出的,只在IE5以上才能被识别,而link是XHTML标签,无兼容问题。

## 11.CSS选择符有哪些？哪些属性可以继承？

    1. id选择器   （ # myid） 
    2. 类选择器   （.myclassname） 
    3. 标签选择器 （div, h1, p） 
    4. 相邻选择器 （h1 + p） 
    5. 子选择器   （ul > li） 
    6. 后代选择器 （li a） 
    7. 通配符选择器   （ * ） 
    8. 属性选择器 （a[rel = "external"]） 
    9. 伪类选择器 （a:hover, li:nth-child） 
    
* 可继承的样式： `font-size font-family color, UL LI DL DD DT`; 
* 不可继承的样式：`border padding margin width height` ; 

## 12.CSS优先级算法如何计算？ 

 * 优先级就近原则，同权重情况下样式定义最近者为准; 
 * 载入样式以最后载入的定位为准; 

 > 优先级为: 
 !important > id > class > tag
 important 比内联优先级高
 
## 13.CSS3新增伪类有那些？ 

- p:first-of-type 选择属于其父元素的首个`<p>`元素的每个`<p>`元素。 
- p:last-of-type 选择属于其父元素的最后`<p>`元素的每个`<p>`元素。 
- p:only-of-type 选择属于其父元素唯一的`<p>`元素的每个`<p>`元素。 
- p:only-child 选择属于其父元素的唯一子元素的每个`<p>` 元素。 
- p:nth-child(2) 选择属于其父元素的第二个子元素的每个`<p>` 元素。 
- :after 在元素之前添加内容,也可以用来做清除浮动。 
- :before 在元素之后添加内容 。
- :enabled 。
- :disabled 控制表单控件的禁用状态。 
- :checked 单选框或复选框被选中。

## 14.CSS里的visibility属性有个collapse属性值是干嘛用的？在不同浏览器下以有什么区别？

    当一个元素的visibility属性被设置成collapse值后，对于一般的元素，它的表现跟hidden是一样的。但例外的是，如果这个元素是table相关的元素，例如table行，table group，table列，table column group，它的表现却跟display:none一样，也就是说，它们占用的空间也会释放。 
 
> 但遗憾的是，各种浏览器器对collapse值的处理方式不一样. 

## 15. 如何居中div？如何居中一个浮动元素？如何让绝对定位的div居中？

    给div设置一个宽度，然后添加margin:0 auto属性; 
    
    居中一个浮动元素 
    确定容器的宽高 宽500 高 300 的层 
    设置层的外边距 
```
.div { 
    width:500px ; 
    height:300px;//高度可以不设 
    margin: -150px 0 0 -250px; 
    position:relative; //相对定位 
    background-color:pink; //方便看效果 
    left:50%; 
    top:50%; 
} 
```
* 让绝对定位的div居中-水平居中 
```
position: absolute; 
width: 1200px; 
background: none; 
margin: 0 auto; 
right: 0; 
left: 0; 
```
* 让绝对定位的div居中-水平居中+垂直居中 
```
position: absolute; 
width: 1200px; 
background: none; 
margin: auto auto; 
top: 0; 
left: 0; 
bottom: 0; 
right: 0; 

.div_fixed { 
    position: fixed; 
    top: 50%; 
    left: 50%; 
    background-color: #000; 
    width:50%; 
    height: 50%; 
    -webkit-transform: translateX(-50%) translateY(-50%); 
} 
```

* 让div内部的块元素居中 

```
display: table-cell; 
vertical-align: middle; 

.div_fixed{ 
    position: fixed; 
    top: 50%; 
    left: 50%; 
    background-color: #000; 
    width:50%; 
    height: 50%; 
    -webkit-transform: translateX(-50%) translateY(-50%); 
} 
```