**目录：**

- [13. CSS 选择器](#13-css-选择器)
  - [13.1. 基本选择器](#131-基本选择器)
    - [13.1.1. 通用选择器](#1311-通用选择器)
    - [13.1.2. 元素选择器](#1312-元素选择器)
    - [13.1.3. 类选择器](#1313-类选择器)
    - [13.1.4. id 选择器](#1314-id-选择器)
    - [13.1.5. 属性选择器](#1315-属性选择器)
  - [13.2. 组合选择器](#132-组合选择器)
    - [13.2.1. 后代选择器](#1321-后代选择器)
    - [13.2.2. 直接后代选择器](#1322-直接后代选择器)
    - [13.2.3. 兄弟选择器](#1323-兄弟选择器)
    - [13.2.4. 相邻兄弟选择器](#1324-相邻兄弟选择器)
  - [13.3. 伪元素选择器](#133-伪元素选择器)
    - [13.3.1. ::after](#1331-after)
    - [13.3.2. ::before](#1332-before)
    - [13.3.3. ::first-line](#1333-first-line)
    - [13.3.4. ::first-letter](#1334-first-letter)
    - [13.3.5. ::selection](#1335-selection)
  - [13.4. 伪类选择器](#134-伪类选择器)
    - [13.4.1. 结构性伪类选择器](#1341-结构性伪类选择器)
    - [13.4.2. UI 伪类选择器](#1342-ui-伪类选择器)
    - [13.4.3. 动态伪类选择器](#1343-动态伪类选择器)
    - [13.4.4. 其他伪类选择器](#1344-其他伪类选择器)
  - [13.5. 分组选择器](#135-分组选择器)

# 13. CSS 选择器

本章会详细地介绍 CSS 选择器。

## 13.1. 基本选择器

有些选择器使用起来非常简单，我们把这部分选择器称为 **基本选择器(basic selector)**。开发人员可使用这类选择器在文档中进行比较宽泛的选择，也可以将其看做结合多种选择器进行特殊选择的基础（本章后面会介绍复合选择器）。接下来每节介绍一种基本选择器的用法。

### 13.1.1. 通用选择器

通用选择器（\*）匹配文档中的所有元素。它是最基本的选择器，不过使用很少，因为匹配过于广泛。一般不推荐使用这个选择器，它性能很低。

### 13.1.2. 元素选择器

CSS 元素选择器(也称为类型选择器)通过 node 节点名称匹配元素. 因此,在单独使用时,寻找特定类型的元素时,元素选择器都会匹配该文档中所有此类型的元素。

下面的例子展示了元素选择器的用法。

```css
body {
  margin: 0px;
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
}
```

### 13.1.3. 类选择器

在一个 HTML 文档中，CSS 类选择器会根据元素的类属性中的内容匹配元素。类属性被定义为一个以空格分隔的列表项，在这组类名中，必须有一项与类选择器中的类名完全匹配，此条样式声明才会生效。

类选择器有 3 种基本用法：

1. **.className**

这种用法选择所有具有 className 的元素。

2. **tagName.className**

这种用法选择所有 tagName 类型的元素中含有 className 的元素。

3. **.className1.className2**

这种用法选择所有同时具有 className1 和 className2 的元素。

当然你也可以组合产生更多用法。

下面展示了了一些用例。

```css
p.center.bold {
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
}
```

### 13.1.4. id 选择器

在一个 HTML 文档中，CSS ID 选择器会根据该元素的 ID 属性中的内容匹配元素，元素 ID 属性名必须与选择器中的 ID 属性名完全匹配，此条样式声明才会生效。

id 选择器既可以单独使用也可以紧跟在一个元素选择器后面：

```css
#nav-bar {
  display: flex;
}
```

```css
div#nav-bar {
  display: flex;
}
```

### 13.1.5. 属性选择器

CSS 属性选择器通过已经存在的属性名或属性值匹配元素。

1. **[attr]**

选取有 attr 属性的元素。

```css
input[required] {
  /* 选择input中带有 required 的元素。 */
}
```

2. **[attr=value]**

选取属性为特定值的元素

```css
a[target='_blank'] {
  /* 选取 target 属性为 "_blank" 的 a 元素 */
  background-color: yellow;
}
```

3. **[attr~=value]**

[attr~=value] 选择器选取属性值包含指定词的元素。

```css
[title~='flower'] {
  border: 5px solid yellow;
}
```

上面的例子会匹配以下属性的元素：title="flower"、title="summer flower" 以及 title="flower new"，但不匹配：title="my-flower" 或 title="flowers"。

4. **[attr|=value]**

[attr|=value] 选择器用于选取指定属性以指定值开头的元素。

```css
[class|='top'] {
  background: yellow;
}
```

上例选取 class 属性以 "top" 开头的所有元素，而且值必须是完整或单独的单词，比如 class="top" 或者后跟连字符的，比如 class="top-text"。

5. **[attr^=value]**

[attr^=value] 选择器用于选取指定属性以指定值开头的元素。

```css
[class^='top'] {
  background: yellow;
}
```

上例选取 class 属性以 "top" 开头的所有元素，但值不必是完整单词！

6. **[attr$=value]**

[attre$=value] 选择器用于选取指定属性以指定值结尾的元素。

```css
[class$='wrapper'] {
  background-color: yellow;
}
```

上例选取 class 属性以 "test" 结尾的所有元素，但值不必是完整单词。

7. **[attr*=value]**

[attr*=value] 选择器选取属性值包含指定词的元素。

```css
[class*='te'] {
  background: yellow;
}
```

上例选取 class 属性包含 "te" 的所有元素，但值不必是完整单词！

## 13.2. 组合选择器

组合使用不同的选择器可以匹配更特定的元素。有的组合选择器能将目标样式应用到更多元素，有的组合选择器则会锁定更少元素，总之会让你的选择非常具体。在接下来的几节中，我会为你展示组合使用选择器的各种方法。

### 13.2.1. 后代选择器

后代组合器（通常用单个空格（ ）字符表示）组合了两个选择器，如果第二个选择器匹配的元素具有与第一个选择器匹配的祖先（父母，父母的父母，父母的父母的父母等）元素，则它们将被选择。利用后代组合器的选择器称为后代选择器。

从技术上讲，后代组合器是两个选择器之间的一个或多个 CSS 空格字符-空格字符和/或四个控制字符之一：回车，换页，换行和制表符在没有其他组合器的情况下。此外，组成组合器的空白字符可以包含任意数量的 CSS 注释。

```css
h1 em {
  color: red;
}
```

这个例子中，选择了 h1 元素中的所有 em 元素。

### 13.2.2. 直接后代选择器

如果您不希望选择任意的后代元素，而是希望缩小范围，只选择某个元素的子元素，请使用子元素选择器（Child selector）。例如，如果您希望选择只作为 h1 元素子元素的 strong 元素，可以这样写：

```css
h1 > strong {
  color: red;
}
```

这个规则会把第一个 h1 下面的两个 strong 元素变为红色，但是第二个 h1 中的 strong 不受影响：

```html
<h1>
  This is
  <strong>very</strong>
  <strong>very</strong>
  important.
</h1>
<h1>
  This is
  <em>
    really
    <strong>very</strong>
  </em>
  important.
</h1>
```

### 13.2.3. 兄弟选择器

兄弟选择符，位置无须紧邻，只须同层级，A~B 选择 A 元素之后所有同层级 B 元素。

```css
p ~ span {
  color: red;
}
```

```html
<span>This is not red.</span>
<p>Here is a paragraph.</p>
<code>Here is some code.</code>
<span>And here is a span.</span>
```

这样，只有最后一个 span 元素会被选中。

### 13.2.4. 相邻兄弟选择器

相邻兄弟选择器 (+) 介于两个选择器之间，当第二个元素紧跟在第一个元素之后，并且两个元素都是属于同一个父元素的子元素，则第二个元素将被选中。

```css
li + li {
  font-weight: bold;
}
```

```html
<div>
  <ul>
    <li>List item 1</li>
    <li>List item 2</li>
    <li>List item 3</li>
  </ul>
  <ol>
    <li>List item 1</li>
    <li>List item 2</li>
    <li>List item 3</li>
  </ol>
</div>
```

上面这个选择器只会把列表中的第二个和第三个列表项变为粗体。第一个列表项不受影响。

## 13.3. 伪元素选择器

目前为止， 我们已经学习了如何使用 HTML 文档中定义的元素选择文档内容。CSS 中还定义了伪选择器(pseudo-selector)， 它们提供了更复杂的功能，但并非直接对应 HTML 文档定义的元素。伪选择器分两种：伪元素和伪类。本节将介绍和演示伪元素选择器。顾名思义，伪元素实际上并不存在，它们是 CSS 提供的额外“福利”，为了方便你选中文档内容。

### 13.3.1. ::after

CSS 伪元素::after 用来创建一个伪元素，作为已选中元素的最后一个子元素。通常会配合 content 属性来为该元素添加装饰内容。这个虚拟元素默认是行内元素。

```css
/* Add an arrow after links */
a::after {
  content: '<-';
}
```

### 13.3.2. ::before

CSS 伪元素::before 用来创建一个伪元素，作为已选中元素的第一个一个子元素。通常会配合 content 属性来为该元素添加装饰内容。这个虚拟元素默认是行内元素。

```css
/* Add an arrow before links */
a::after {
  content: '->';
}
```

### 13.3.3. ::first-line

::first-line 选择器匹配文本块的首行。

```css
::first-line {
  background-color: grey;
  color: white;
}
```

### 13.3.4. ::first-letter

CSS 伪元素 ::first-letter 会选中某 block-level element（块级元素）第一行的第一个字母，并且文字所处的行之前没有其他内容（如图片和内联的表格） 。

```css
p::first-letter {
  font-weight: bold;
  color: red;
}
```

### 13.3.5. ::selection

::selection CSS 伪元素应用于文档中被用户高亮的部分（比如使用鼠标或其他选择设备选中的部分）。

```css
::selection {
  background-color: cyan;
}
```

只有一小部分 CSS 属性可以用于::selection 选择器：

color
background-color
cursor
caret-color
outline and its longhands
text-decoration and its associated properties
text-emphasis-color (en-US)
text-shadow

## 13.4. 伪类选择器

伪类跟伪元素一样，并不是直接针对文档元素的，而是为你基于某些共同特征选择元素提供方便。

### 13.4.1. 结构性伪类选择器

使用结构性伪类选择器能够根据元素在文档中的位置选择元素。这类选择器都有一个冒号字符前缀（:）， 例如： empty。它们可以单独使用，也可以跟其他选择器组合使用，如 p:empty。

1. **:root**

2. **子元素伪类**

### 13.4.2. UI 伪类选择器

1. **:enabled 和 :disabled**

2. **:checked**

3. **:valid 和 :invalid**

4. **:required 和 :optional**

5. **:in-range 和 :out-of-range**

### 13.4.3. 动态伪类选择器

1. **:link**

2. **:visited**

3. **:hover**

4. **:active**

5. **:focus**

### 13.4.4. 其他伪类选择器

1. **:not()**

2. **:empty**

3. **:lang**

4. **:target**

## 13.5. 分组选择器
