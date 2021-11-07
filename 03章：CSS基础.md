**目录：**

- [3. CSS 基础](#3-css-基础)
  - [3.1. 定义和应用样式](#31-定义和应用样式)
    - [3.1.1. CSS 声明](#311-css-声明)
    - [3.1.2. 行内样式](#312-行内样式)
    - [3.1.3. 内部样式表](#313-内部样式表)
    - [3.1.4. 外部样式表](#314-外部样式表)
  - [3.2. 层叠和继承](#32-层叠和继承)
    - [3.2.1. 用户代理样式](#321-用户代理样式)
    - [3.2.2. 样式的层叠](#322-样式的层叠)
    - [3.2.3. !important](#323-important)
    - [3.2.4. 样式冲突](#324-样式冲突)
    - [3.2.5. 继承](#325-继承)
  - [3.3. 颜色](#33-颜色)
  - [3.4. 长度](#34-长度)
    - [3.4.1. 绝对单位](#341-绝对单位)
    - [3.4.2. 相对单位](#342-相对单位)
  - [3.5. 其他单位](#35-其他单位)

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

要想掌握样式表，弄清样式层叠和继承这两个概念是关键。浏览器根据层叠和继承规则确定显示一个元素时各种样式属性采用的值。每个元素都有一套浏览器呈现页面时要用到的 CSS 属性。对于每一个这种属性，浏览器都需要查看一下其所有的样式来源。前面已经讲过三种定义样式的方式（行内样式、内部样式表和外部样式表），但是要知道，样式还有另外一种来源。

### 3.2.1. 用户代理样式

用户代理样式一般指元素尚未设置样式时浏览器应用在它身上的默认样式。这些样式因浏览器而略有差异，不过大体一致。以 a 元素（超链接）为例，想想没有特别为它定义样式时浏览器会怎样显示。下面代码所示为一个不含任何样式的简单 HTML 文档。

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
    <a href="http://www.google.com/">google</a>
  </body>
</html>
```

我们对浏览器应用千链接的样式早已习以为常，以至于不会留意到它的存在。用户代理样式可以通过浏览器的控制台查看。如下是 Chrome 浏览器中，上面超链接的用户代理样式：

```css
a:-webkit-any-link {
  color: -webkit-link;
  cursor: pointer;
  text-decoration: underline;
}
```

虽然不是每一个 HTML 元素都有默认的浏览器样式，但是多数元素都有。本书介绍 HTML 元素的各章都会介绍常见浏览器一般都会应用的典型默认样式。

### 3.2.2. 样式的层叠

明白了浏览器所要查看的所有样式来源之后， 现在可以看看浏览器要显示元素时求索一个 CSS 属性值的次序。这个次序很明确：

1. 行内样式（用元素的全局属性 style 定义的样式）；
2. 内部样式表（定义在 style 元素中的样式）；
3. 外部样式表（用 link 元素导入的样式）；
4. 浏览器样式（浏览器应用的默认样式）。

设想用户需要显示一个 a 元素。浏览器需要知道的一件事情是其文字应显示为哪种颜色。为了解决这个问题，它需要为 CSS 属性 color 找到一个值。首先它会查看所要呈现的那个元素是否具有一条设定了 color 值的行内样式。比如下面这种：

```html
<a style="color: blue;" href="http://www.google.com/">google</a>
```

如果不存在元素内嵌样式， 那么接下来浏览器会看看是否有一个 style 元素包含着作用于那个元素的样式。比如下面这种：

```html
<style>
  a {
  color: red;
  ｝
</style>
```

如果不存在这样的 style 元素，那么浏览器接下来会查看用 link 元素载入的样式表。依次类推，直到找到一个 color 属性值或查完用户定义样式。在后面一种情况下， 最终使用的将是浏览器默认样式中的值。

前述次序表中的前三个属性来源（行内样式、内部样式表和外部样式表）合称作者样式。定义在用户样式表中的样式称为用户样式。由浏览器的默认样式则称为用户代理样式（浏览器样式）。

### 3.2.3. !important

在样式属性值后用 !important 标记，可以改变正常的层叠次序。

例如：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <style>
      a {
        color: blue !important;
      }
    </style>
    <title>Document</title>
  </head>
  <body>
    <a style="color: red;" href="http://www.baidu.com/">baidu</a>
  </body>
</html>
```

这样浏览器在检查样式时，内部样式表的样式就会被首先查询。因此，这个例子中，超链接文字颜色是蓝色而不是红色。

### 3.2.4. 样式冲突

在使用内部或外部样式表时，有时可能发生 **样式冲突**。样式冲突是指定义在内部样式表或外部样式表中的多条样式规则可能作用于同一个元素。例如：

```css
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <style>
      a{
        color:blue;
      }

      a.myClass{
        color: green;
        background-color: yellow;
      }
    </style>
    <title>Document</title>
  </head>
  <body>
    <!--蓝色文字-->
    <a href="http://www.google.com/">google</a>

    <!--蓝色文字，黄色背景-->
    <a class="myClass" href="http://www.baidu.com/">baidu</a>
  </body>
</html>
```

在这些情况下，为了判断该用哪个值，浏览器会评估两条样式的具体程度，然后选中较为特殊的那条。样式的具体程度通过统计三类特征得出：

- a: 样式的选择器中 id 值的数目；
- b: 选择器中其他属性和伪类的数目；
- c: 选择器中元素名和伪元素的数目。

在评定具体程度时要按 a-b-c 的形式（其中每一个字母依次代表上述三类特征的统计结果）生成一个数字。它不是一个三位数。如果对某个样式算出的 a 值最大，那么它就是具体程度高的那个。只有 a 值相等时浏览器才会比较 b 值，此时 b 值较大的样式具体程度更高。只有 a 值和 b 值都分别相等时浏览器才会考虑 c 值。也就是说，1-0-0 这个得分比 0-5-5 这个得分代表的具体程度更高。

本例中 a.myclass 这个选择器含有一个 class 属性，于是该样式的值为 0-1-0 (0 个 id 值+1 个其他属性+0 个元素名）。另一条样式的具体程度值为 0-0-0（因为它不包含 id 值、其他属性或元素名）。因此浏览器在呈现被归入 myclass 类的 a 元素时将使用 a.myclass 样式中设定的 color 属性值。对于所有其他 a 元素，使用的则是另一条样式中设定的值。

如果同一个样式属性出现在具体程度相当的几条样式中，那么浏览器会根据其位置的先后选择所用的值，规则是后来者居上。

例如：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <style>
      a.myClass1 {
        color: blue;
      }

      a.myClass2 {
        color: red;
      }
    </style>
    <title>Document</title>
  </head>
  <body>
    <!--红色文字-->
    <a class="myClass1 myClass2" href="http://www.baidu.com/">baidu</a>
  </body>
</html>
```

此例 style 元素中定义的两条样式在具体程度上得分相同。因此，超链接应用了第 2 条样式。同样地，如果我们颠倒了这 2 条样式，那么超链接就会变为蓝色文字。读者不妨自行尝试。

根据样式的具体程度和定义次序确定选用的样式属性值，应该把各个属性分开考虑。本节的几个例子还定义了背景颜色属性的值。因为该值并非两个样式中都有，所以不会发生冲突，也就没有必要查找其他值。

### 3.2.5. 继承

如果浏览器在直接相关的样式中找不到某个属性的值，就会求助于继承机制，使用父元素的这个样式属性值。

例如：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <style>
      p {
        color: white;
        background-color: black;
        border: 1px solid yellow;
      }
    </style>
    <title>Document</title>
  </head>
  <body>
    <p>
      I like
      <!--继承父元素 p 的前景色-->
      <span>apples</span>
      and oranges.
    </p>
  </body>
</html>
```

本例关注的是浏览器应用于 span 元素（其父元素为 p) 的样式。这个文档并没有在针对 span 元素的样式中设定 color 属性值，但是浏览器显示该元素的文字内容时却使用了前景色 white。这个值系由父元素 p 继承而来。

令人挠头的是，并非所有 CSS 属性均可继承。这方面有条经验可供参考：与元素外观（文字颜色、字体等）相关的样式会被继承；与元素在页面上的布局相关的样式不会被继承。在样式中使用 inherit 这个特别设立的值可以强行实施继承，明确指示浏览器在该属性上使用父元素样式中的值。

例如：

```css
span {
  border: inherit;
}
```

此例定义了一条用于 span 元素的样式，其 border 属性值继承自父元素。因此 apples 就会出现黄色边框。

## 3.3. 颜色

颜色在网页中的作用非常重要。在 CSS 中设置颜色有好几种方法。最简单的办法是使用规定的颜色名称，或者设置红、绿、蓝三种颜色成分的值（十进制或十六进制）。设置颜色成分值时，十进制值以逗号分隔，十六进制值前面通常要加上一个`#`号（例如`#ffffff`，它代表白色）。你可以查看[MDN 参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/color_value)查看各种颜色代码。

**更复杂的颜色**

颜色名称和简单的十六进制数不是表示颜色的唯一方式。CSS 中还可以用一些函数选择颜色。下表逐一介绍了这些函数。

| 函数             | 说明示例                                                                              |
| ---------------- | ------------------------------------------------------------------------------------- | -------------------------------- |
| rgb(r, g, b)     | 用 RGB 模型表示颜色 color: rgb(112, 128,144)                                          |
| rgba(r, g, b, a) | 用 RGB 模型表示颜色，外加一个用于表示透明度的 a 值（0 代表全透明， 1 代表完全不透明） | color: rgba(112, 128, 144, 0.4)  |
| hsl(h, s, l)     | 用 HSL 模型（色相(hue)、饱和度(saturation)和明度(Lightness)）表示颜色                 | color: hsl(120, 100%, 22%)       |
| hsla(h, s, l, a) | 与 HSL 模式类似， 只不过增加了一个表示透明度的 a 值                                   | color: hsla(120, 100%, 22%, 0.4) |

## 3.4. 长度

许多CSS属性要求为其设置长度值。width属性和font-size属性就是这方面的例子。前者用于设置元素的宽度，后者用于设置元素内容的字号。

例如：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <style>
      body{
        margin: 0px;
        font-size: 20px;
      }
    </style>
    <title>Document</title>
  </head>
  <body>一段文本</body>
</html>
```

设置长度值时，应让数字和单位标识符连在一起，二者之间不加空格或其他字符。上面这个例子中将 body 的外边框（margin）的长度设为0px，将其内容的文字大小设置为 20px。CSS规定了两种类型的长度单位，一种是绝对单位，另一种是与其他属性挂钩的相对单位。下面介绍这两种单位。

### 3.4.1. 绝对单位



### 3.4.2. 相对单位

## 3.5. 其他单位
