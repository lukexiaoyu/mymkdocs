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
