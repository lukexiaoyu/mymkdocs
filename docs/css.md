## 链接方式

### 外部链接

```html
<link rel="stylesheet" href="mystyle.css">
```

可以链接多个外部的样式

#### 内部链接

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

#### 行内样式

```html
<h1 style="color:blue;text-align:center;">This is a heading</h1>
<p style="color:red;">This is a paragraph.</p>
```



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

