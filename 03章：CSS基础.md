**目录：**

- [3. CSS 基础](#3-css-基础)
  - [3.1. 定义和应用样式](#31-定义和应用样式)
    - [3.1.1. CSS 声明](#311-css-声明)
    - [3.1.2. 行内样式](#312-行内样式)
    - [3.1.3. 内部样式表](#313-内部样式表)
    - [3.1.4. 外部样式表](#314-外部样式表)
  - [3.2. 层叠和继承](#32-层叠和继承)

# 3. CSS 基础

CSS（层叠样式表）用来规定 HTML 文档的呈现形式（外观和格式编排）。本章将说明如何创建和应用 CSS 样式，解释层叠样式表这个名称的由来，为后续章节打下基础。

## 3.1. 定义和应用样式

### 3.1.1. CSS 声明

CSS 样式由一条或多条以分号隔开的样式声明组成。每条声明包含着一个 CSS 属性和该属性的值，二者以冒号分隔。

```css
background-color: yellow;
color: green;
```

在这个例子中，有 2 条 CSS 声明，第一条指定了背景色为 yellow，第 2 条指定了前景色为 green。

CSS 属性花样繁多，每种属性都控制着其应用元素某方面的外观。

### 3.1.2. 行内样式

样式不是定义了就了事，它还需要被应用，也即告诉浏览器它要影响哪些元素。把样式应用到元素身上的各种方式中，最直接的是使用全局属性 style。

你可以在一个元素的全局属性 style 中指定它的样式，例如：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
  </head>
  <body>
    <div
      style="width: 100px; height: 100px; border: 2px solid yellow; background-color: skyblue; display: flex; align-items: center; justify-content: center; color: white;"
    >
      一段文字
    </div>
  </body>
</html>
```

### 3.1.3. 内部样式表

直接对元素应用样式有它的用处，但是对于可能大量需要各种样式的复杂文档来说就显得缺乏效率。这样做不仅需要逐个元素设好样式，而且软件更新时还不得不逐个元素仔细搞好样式调整，很容易出错。我们可以换种方法，用 style 元素（而不是 style 属性）定义内部样式表，通过 CSS 选择器指示浏览器应用样式。

此时的 CSS 语法为选择器后跟花括号，花括号中写 CSS 声明。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <style>
      a {
        text-decoration: none;
      }
      a:active {
        color: purple;
      }
      a:visited {
        color: red;
      }
    </style>
    <title>Document</title>
  </head>
  <body>
    <a href="http://www.google.com/">去 google</a>
    <a href="http://www.baidu.com/">去 baidu</a>
  </body>
</html>
```

这个例子改写了超链接的默认样式。没有激活的链接没有下划线，为蓝色。激活的链接没有下划线，为紫色。访问过的连接没有下划线，为红色。

### 3.1.4. 外部样式表

如果有一套样式要用于多个 HTML 文档，那么与其在每一个文档中重复定义相同的样式，不如另外创建一个独立的样式表文件。这种文件按惯例以．css 为文件扩展名，其中包含着用户的样式定义。

样式表中用不着 style 元素，需要什么样式，只需要为其设计好选择器，后面再跟上一套样式声明即可。然后 HTML 文档就可以用 link 元素将这些样式导入其中。如下面是 style.css 的代码：

```css
a {
  text-decoration: none;
}
a:active {
  color: purple;
}
a:visited {
  color: red;
}
```

下面是对应 html 代码：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="style.css" />
    <title>Document</title>
  </head>
  <body>
    <a href="http://www.google.com/">去 google</a>
    <a href="http://www.baidu.com/">去 baidu</a>
  </body>
</html>
```

文档想要链接多少样式表都行，为每个样式表使用一个 link 元素即可。如果不同样式表中的样式使用了相同的选择器，那么这些样式表的导入顺序很重要，在此情况下得以应用的是后导入的样式。

1. **从其他样式表导入样式**

可以用＠import 语句将样式从一个样式表导入另一个样式表。

例如，你可以把一个基本的 base.css 导入一个另外样式表中：

base.css:

```css
body {
  width: 100vw;
  height: 100vh;
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

a {
  text-decoration: none;
}
a:active {
  color: purple;
}
a:visited {
  color: red;
}
```

style.css

```css
@import url(base.style);

#target {
  max-width: 100px;
}
```

2. **声明样式表的字符编码**

在 CSS 样式表中可以出现在@import 语句之前的只有@charset 语句。后者用于声明样式表使用的字符编码。下面示范了如何表示样式表使用的是 UTF-8 编码（这是最常见的编码）。

```css
@charset "utf-8";
@import url(base.style);

#target {
  max-width: 100px;
}
```

## 3.2. 层叠和继承
