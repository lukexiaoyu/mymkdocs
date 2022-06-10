# css
## 链接方式

### 外部链接

```html
<link rel="stylesheet" href="mystyle.css">
```

可以链接多个外部的样式

### 内部链接

```html
<!DOCTYPE html>
<html>
<head>
<style>
body {
  background-color: linen;
}

h1 {
  color: maroon;
  margin-left: 40px;
}
</style>
</head>
<body>

<h1>This is a heading</h1>
<p>This is a paragraph.</p>

</body>
</html>
```

### 行内样式

```html
<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>
```

### 优先级

1. 行内样式
2. 外部和内部样式表（在头部）
3. 浏览器默认

因此，内联样式具有最高优先级，并将覆盖外部和内部样式以及浏览器默认值。

## 选择器

### 基本选择器

```css
.a{
	color:red;
}
p{
  color:red;
}
#one{
  color:red;
}
*{
  color:red;
}
```

### 分组选择器

```css
h1,h2,p{
  color:red;
}
```

意思就是一次选择多个选择器，中间用逗号隔开。

### 后代选择器

父元素下面的==所有指定的标签==

```css
<main>
    <div id="one">
        <div>
            <p>11</p>
        </div>
        <p>1</p>
        <p>2</p>
        <p>3</p>
        <p>4</p>
    </div>
</main>
<style>
    #one p{
        color: red;
    }
</style>
```

<main>
    <div id="one">
        <div>
            <p>11</p>
        </div>
        <p>1</p>
        <p>2</p>
        <p>3</p>
        <p>4</p>
    </div>
</main>
<style>
    #one p{
        color: red;
    }
</style>

<hr>



## color

### RGB

**rgb(red, *green***, blue)

每一个值都是0-255

### HEX

是16进制颜色表示方式

 (RR, GG, and BB)  =》#ff00ff

每一个的值是从00到ff

### HSL

hsl(hue,saturation,lightness)

hue色调是色轮上从 0 到 360 的度数。0 是红色，120 是绿色，240 是蓝色。

saturation饱和度是一个百分比值，0% 表示灰色阴影，100% 表示全色。

lightness明度也是一个百分比，0%是黑色，50%既不亮也不暗，100%是白色

### 透明度

RGB和HSL都可以添加透明度

```css
.a{
   color:rgba(200, 200, 200, 0.5);
	}
.b{
   color:hsla(30, 50%, 30%, 0.3);
}
```

其中参数a它的取值是0-1，1是正常，0就完全透明

### 透明transparent

这个属性就是直接透明了。

```css
div {
  background-color: transparent;
}
```

### currentcolor 

意思就是和当前元素的一些颜色相同

```css
div {
  color: blue;
  border: 10px solid currentcolor;
}
```

比如这里字体颜色是blue,所以border也就是blue了。

适合页面的整体调色。

### inherit 

继承父元素的颜色

```css
div {
  border: 2px solid red;
}

span {
  border: inherit;
}
```

div是red,span也就是red

### Gradients渐变



## 背景background

### background-color

没啥说的，就是正常的背景颜色

### background-image

```css
body {
  background-image: url("paper.gif");
}
```

OK，这里在body下加载了背景图片，默认图片不会有任何的拉升，而且会重复放置

### background-repeat

默认情况下， background-image 属性会在水平和垂直方向上重复图像。 有些图像只能水平或垂直重复，否则它们会看起来很奇怪

我们可以定义在x,y上重复，或者没有任何重复

```css
body {
  background-image: url("img_tree.png");
  background-repeat: no-repeat;
}
```

如果是在x,y重复，那么把值改成repeat-x  repeat-y

### background-position

在no-repeat的情况下，图片不会充满整个元素空间，我们可以定义它的位置

```css
 background-position: right top;
```

它由两个值组成，中间空格

第一个是水平，第2个是垂直

我们可以写方位，也可以写长度（px等），也可以写x%，这里相对本身做百分比

==这里我们要着重强调一个东西，那就是在Y方向有固定的尺寸这些才能生效，否则无法生效哦==

### background-attachment

属性指定背景图像应该滚动还是固定（不会随着页面的其余部分滚动）：

```css
body {
  background-image: url("img_tree.png");
  background-repeat: no-repeat;
  background-position: right top;
  background-attachment: fixed;
}
```

fixed就是背景永远都不会动了，scroll表示和页面一起滑动、

### 缩写

所有的都可以写在一条上面

==注意书写是有顺序的，没有的可以不写==

- `background-color`
- `background-image`
- `background-repeat`
- `background-attachment`
- `background-position`

按照这个顺序写

```css
body {
  background: #ffffff url("img_tree.png") no-repeat right top;
}
```

背景颜色在背景图片的下面，不用担心

### background-size

可以用长度单位，百分比，或者用关键字：contain cover

```css
#div1 {
  background: url(img_flower.jpg);
  background-size: 100px 80px;
  background-repeat: no-repeat;
}
```

很简单就是宽和高

如果使用百分比，这个百分比的意思是占父元素的width，height百分之多少。比如都是100%，那么就刚好拉升填充父元素

最后一个就是contain cover

contain ：让图片等比例拉伸，图片能够全部显示，且有一边和父元素完全重合之后停止缩放。

cover：让图片等比例拉伸，切充满整个父元素，且有一边和父元素完全重合之后停止缩放。

最常用的一般是width或者height 100%,然后另一边auto.

### background-origin

这是一个==背景image==范围的属性

1. border-box  会把边框的范围也算进去，是最大的
2. padding-box  默认值
3. content-box 只会在内容的范围，是最小的

```css
background-origin: content-box;

```

### background-clip

这个和上面的一样，只不过，这个属性==针对的是整个背景==，而不只是image

## border边框

### border-style

边框有很多样式

- `dotted` - Defines a dotted border
- `dashed` - Defines a dashed border
- `solid` - Defines a solid border
- `double` - Defines a double border
- `groove` - Defines a 3D grooved border. The effect depends on the border-color value
- `ridge` - Defines a 3D ridged border. The effect depends on the border-color value
- `inset` - Defines a 3D inset border. The effect depends on the border-color value
- `outset` - Defines a 3D outset border. The effect depends on the border-color value
- `none` - Defines no border
- `hidden` - Defines a hidden border

其实常用的就是solid了，其它看看好了

任意方向的style

```css
.one{
        width: 200px;
        height: 200px;
        border-style: outset;
        border-top-style: double;
    }
```



### Border Width

宽度 一般用长度表示

```css
p.three {
  border-style: dotted;
  border-width: 2px;
}
```

可以设置不同方向的宽度

```css
p.one {
  border-style: solid;
  border-width: 5px 20px; /* 5px top and bottom, 20px on the sides */
}

p.two {
  border-style: solid;
  border-width: 20px 5px; /* 20px top and bottom, 5px on the sides */
}

p.three {
  border-style: solid;
  border-width: 25px 10px 4px 35px; /* 25px top, 10px right, 4px bottom and 35px left */
}
```

### Border Color

遵循所有的颜色定律，方位自定义

除此之外还有一个透明的属性

```css
border-color: transparent;
```

只是透明宽度依然有的

### 缩写

```css
p {
  border-bottom: 6px solid red;
}
```

没有明确的顺序，没有的可以不写，写了整体之后，可以单独定义某一边的样式

### 圆形边框border-radius

可以用长度或者百分比来表示

当50%的时候刚好是圆形,超过50%就不会有再多的变化了。

```
border-radius:50%;
```

同时可以写四个方位不同的圆角程度,这样可以呈现更多的形状

```css
border-radius: 50% 20% 30% 10%;
```

## 外边距margin

这是一个用的超级多的属性。

所谓外边距就是在border外面再加一层透明的边框，这样和相邻的元素感觉就是有距离的了。

同样margin也可以定义4个方位的数值，用长度符号来表示即可。

这里要提一下auto的值如下：

```css
maring:auto 50px;
```

这句话的意思是水平外边距auto，那么其实就是让元素居中了。==而在垂直方向auto是不适用的==，因为其实当我们内容过多的时候，长度是不够的。所以····

## 文本Text

### color

文字颜色，适用于所有颜色的规则

### Text Alignment对齐方式

基本写法

```css
h1 {
  text-align: center;
}

h2 {
  text-align: left;
}

h3 {
  text-align: right;
}
```

### 文字方向Direction

direction 和 unicode-bidi 属性可用于更改元素的文本方向：

```css
p {
  direction: rtl;
  unicode-bidi: bidi-override;
}
```

下面一句固定，上面一句是right to left 的简写，所以反过来就是ltr，从左到右，或者从右到左

### 文字装饰Text Decoration

这边我们直接介绍简写

```css
h1 {
  text-decoration: underline;
}

h2 {
  text-decoration: underline red;
}

h3 {
  text-decoration: underline red double;
}

p {
  text-decoration: underline red double 5px;
}
```

是上面下滑线一定要写，其它随便

none是一个重要的值，可以把例如a这种变迁的下划线给去掉。

```css
a{
	text-decoration:none;
}
```

### 文字大小写

这个就是相对英文了

```css
p.uppercase {
  text-transform: uppercase;
}

p.lowercase {
  text-transform: lowercase;
}

p.capitalize {
  text-transform: capitalize;
}
```

第3个的意思是首字母大写，前面2个不用我说了。

### 首行缩进text-indent

```css
p {
  text-indent: 50px;
}
```

### 字符间距letter-spacing

```css
h1 {
  letter-spacing: 5px;
}

h2 {
  letter-spacing: -2px;
}
```

### 行高line-height

```css
p.small {
  line-height: 0.8;
}

p.big {
  line-height: 1.8;
}
```

因为文字没有垂直居中，所以可以利用line-height来左文章

```css
p{
	height:50px;
	line-height:50px;
}
```

让line-height=height那么就垂直居中了

### 单词间距word-spacing

```css
p.one {
  word-spacing: 10px;
}

p.two {
  word-spacing: -2px;
}
```

### 文字阴影text-shadow

```css
h1 {
  text-shadow: 0 0 3px #ff0000;
}
```

参数1-3：x阴影距离，y距离，阴影模糊距离 x,y可以负，就是反方向阴影

参数4：阴影距离

可以同时设置多个阴影，用逗号隔开

```css
h1 {
  text-shadow: 0 0 3px #ff0000, 0 0 5px #0000ff;
}
```

## 字体font

### font-family

我感觉自带的字体都是针对英文的，所以用默认的就好

### font-style

```css
p.normal {
  font-style: normal;
}

p.italic {
  font-style: italic;
}

p.oblique {
  font-style: oblique;
}
```

### font-weight

```css
p.normal {
  font-weight: normal;
}

p.thick {
  font-weight: bold;
}
```

### font-size

文字大小

```css
h1 {
  font-size: 40px;
}

h2 {
  font-size: 30px;
}

p {
  font-size: 14px;
}
```

```css
h1 {
  font-size: 2.5em; /* 40px/16=2.5em */
}

h2 {
  font-size: 1.875em; /* 30px/16=1.875em */
}

p {
  font-size: 0.875em; /* 14px/16=0.875em */
}
```

响应式font-size

```html
<h1 style="font-size:10vw">Hello World</h1>
```

视口是浏览器窗口的大小。 1vw = 视口宽度的 1%。如果视口为 50 厘米宽，则 1vw 为 0.5 厘米。

### 缩写

The `font` property is a shorthand property for:

- `font-style`
- `font-variant`
- `font-weight`
- `font-size/line-height`
- `font-family`

The `font-size` and `font-family` values are required

```css
p.a {
  font: 20px Arial, sans-serif;
}

p.b {
  font: italic small-caps bold 12px/30px Georgia, serif;
}
```

## 链接link

链接主要讲的是在它的4个状态下，给它定制样式

- `a:link` - a normal, unvisited link  正常状态，还没有访问的状态
- `a:visited` - a link the user has visited 已经访问过的
- `a:hover` - a link when the user mouses over it 鼠标经过的时候
- `a:active` - a link the moment it is clicked 链接被点击的那一刻

>在为多个链接状态设置样式时，有一些顺序规则： a:hover 必须在 a:link 和 a:visited 之后 a:active 必须在 a:hover 之后

### 去下划线

默认是有下划线的，可以用样式去掉

```css
a:link {
  text-decoration: none;
}

a:visited {
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

a:active {
  text-decoration: underline;
}
```

## List列表

列表有ul  and ol  

ul是无序列表

ol是有序列表，每一项前面都有序号

### list-style-type

可以更改前标样式

其实用ul>li就可以了，他们的样式通用

### list-style-image

对的，可以把前标换成图片

不过不太好用，因为你要准备足够小的图片，而且加载浪费时间，这个就算了吧，哈哈

### list-style-position

前标是占位置的，如果换行，第2行和一行对齐还是和前标对齐的样式

inside就是和前标对齐，outside就是和文字对齐

这个不需要刻意去记了

```css
ul.a {
  list-style-position: outside;
}

ul.b {
  list-style-position: inside;
}
```

### 移除默认样式

很多时候我们是不需要前标的，及时移除了，文字前面也有缩进，都可以取消的

```css
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
```

### 缩写

```css
ul {
  list-style: square inside url("sqpurple.gif");
}
```

## table表格

用到的很多

基本标签

```html
<table>
        <tr>
            <th></th>
        </tr>
        <tr>
            <td></td>
        </tr>
        
</table>
```

tr就是一行的意思，然后一行里有几个就写几个，th,td,th是第一行行头，所以单独区分

### Table Borders表格边框

OK，默认下表格是没有边框的

```css
table, th, td {
  border: 1px solid;
}
```

注意，我们这里写的3个元素加边框，因为每个元素只会给自己外围加边框，其实3个都加了是非常丑的，不会像excel那样平滑

### table width

这没啥讲的，里面的单元格会自动拉伸

```css
table {
  width: 100%;
}
```

### Collapse Table Borders表格边框去重

```css
table {
  border-collapse: collapse;
}
```

好了，现在就和excel一样看上去很平滑了

### table style

默认的表格很丑，我们可以自己修改样式，比如th,td不加边框，只加bottom

比如奇偶颜色不同

```css
tr:nth-child(even) {background-color: #f2f2f2;}
```

比如鼠标经过某一行，变色

```css
tr:hover {background-color: coral;}
```

### 响应式表格

如果屏幕太小而无法显示完整内容，响应式表格将显示水平滚动条：

```css
<div style="overflow-x:auto;">

<table>
... table content ...
</table>

</div>
```

## positon

元素的位置有很多调整的方法

默认的都是从上到下一个元素一行的排列，就像是写word一样

### static

是元素的默认属性

```css
div.static {
  position: static;
  border: 3px solid #73AD21;
}
```

### relative

相对定位，这是相对自己原来的位置的定位，==且原来的位置是保留的==

```css
div:nth-child(1){
        position: relative;
        left: 50px;
        background-color: red;
    }
```

### fixed

相对于视口，然后于自己的位置永远固定

原来的位置不再保留

```css
#one_1{
        background-color: green;
        position: fixed;
        bottom: 50px;
    }
```

### absolute

绝对定位，首先是相对于父元素，第2父元素要是相对定位relative才行，==口诀：子绝父相==

### sticky

在超过屏幕显示的内容的时候，从static=》fixed，一般比如头部导航可以设置。

## math function 数学运算

### calc

```css
#div1 {
  position: absolute;
  left: 50px;
  width: calc(100% - 100px);
  border: 1px solid black;
  background-color: yellow;
  padding: 5px;
}
```

要注意的是中间的符号==前后都要有空格==

### max,min

选择最大,最小的值进行style

```css
#div1 {
  background-color: yellow;
  height: 100px;
  width: max(50%, 300px);
}
```

## 2D转换

- `translate()` 
- `rotate()`
- `scaleX()`
- `scaleY()`
- `scale()`
- `skewX()`
- `skewY()`
- `skew()`
- `matrix()`

### translate位移

x,y移动,仍然保留原来的位置。挺方便的

```css
div {
  transform: translate(50px, 100px);
}
```

百分比=>是相对于自身的长度了。

```css
div {
  transform: translate(50%, 50%);
}
```

### rotate旋转

中心点就是元素的中心，单位deg就是度的意思咯。顺序是顺时针，可以负度数

```css
div {
  transform: rotate(-20deg);
}
```

### scale缩放

这个是针对x,y缩放的

基数是1，然后你自己写吧。

需要注意的是缩放的时候是以中心缩放的，不是以左上角

```css
div {
  transform: scale(2, 3);
}
div {
  transform: scale(0.5, 0.2);
}
```

