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
  - [13.5. 并集选择器](#135-并集选择器)

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

- **:root**

:root 选择器匹配文档中的根元素。它可能是用得最少的一个伪类选择器，因为总是返回 html 元素。

```css
:root {
  background: yellow;
}
```

- **子元素伪类**

使用子元素伪类匹配直接包含在其他元素中的单个元素。

1. **:first-child**

:first-child 伪类表示在一组兄弟元素中的第一个元素。

```html
<div>
  <p>This text is selected!</p>
  <p>This text isn't selected.</p>
</div>

<div>
  <h2>This text isn't selected: it's not a `p`.</h2>
  <p>This text isn't selected.</p>
</div>
```

```css
p:first-child {
  color: lime;
  background-color: black;
  padding: 5px;
}
```

这个例子中，只会选择第一个 p 元素。

2. **:last-child**

:lst-child 伪类表示在一组兄弟元素中的最后一个元素。

```html
<ul>
  <li>此元素背景色不是lime</li>
  <li>我的也不是lime。</li>
  <li>我的才是lime！ :)</li>
</ul>
```

```css
li:last-child {
  background-color: lime;
}
```

在这个例子中，只有最后一个 li 元素被选择。

4. **:nth-child(n)**

:nth-child(n) 伪类选择器选择一组兄弟元素中顺序地第 n 个。

```html
<ul>
  <li>此元素背景色不是lime</li>
  <li>我的也不是lime。</li>
  <li>我的才是lime！ :)</li>
</ul>
```

```css
li:nth-child(2) {
  background-color: blue;
}
```

这个例子中，只有第 2 个 li 元素会被选中。

5. **:nth-last-child(n)**

这个伪类选择器和 :nth-child(n) 非常类似，只不过这个选择器的顺序是逆序。

```html
<ul>
  <li>此元素背景色不是lime</li>
  <li>我的也不是lime。</li>
  <li>我的才是lime！ :)</li>
</ul>
```

```css
li:nth-last-child(1) {
  background-color: blue;
}
```

这个例子中，最后一个 li 元素被选中。

6. **:only-child**

:only-child 匹配没有任何兄弟元素的元素。

```html
<ol>
  <li>
    First
    <ul>
      <li>This list has just one element.</li>
    </ul>
  </li>
  <li>
    Second
    <ul>
      <li>This list has three elements.</li>
      <li>This list has three elements.</li>
      <li>This list has three elements.</li>
    </ul>
  </li>
</ol>
```

```css
li li {
  list-style-type: disc;
}
li:only-child {
  color: red;
  list-style-type: square;
}
```

这个例子中 "This list has just one element." 内容的 li 元素会被选中。

7. **:only-of-type**

:only-of-type 代表了任意一个元素，这个元素没有其他相同类型的兄弟元素。

<main>
  <div>I am `div` #1.</div>
  <p>I am the only `p` among my siblings.</p>
  <div>I am `div` #2.</div>
  <div>I am `div` #3.
    <i>I am the only `i` child.</i>
    <em>I am `em` #1.</em>
    <em>I am `em` #2.</em>
  </div>
</main>

```css
main :only-of-type {
  color: red;
}
```

上面的例子中只会选中 p 元素。

6. **:nth-of-type(n)**

:nth-of-type() 这个 CSS 伪类是针对具有一组兄弟节点的标签, 用 n 来筛选出在一组兄弟节点的位置。

```html
<div>
  <div>这段不参与计数。</div>
  <p>这是第一段。</p>
  <p>这是第二段。</p>
  <div>这段不参与计数。</div>
  <p>这是第三段。</p>
  <p>这是第四段。</p>
</div>
```

```css
/* 奇数段 */
p:nth-of-type(2n + 1) {
  color: red;
}

/* 偶数段 */
p:nth-of-type(2n) {
  color: blue;
}

/* 第一段 */
p:nth-of-type(1) {
  font-weight: bold;
}
```

7. **:nth-last-of-type(n)**

:nth-last-of-type(n) 和 :nth-of-type(n) 类型，不过顺序相反。

### 13.4.2. UI 伪类选择器

1. **:enabled 和 :disabled**

有些元素有启用或者禁用状态，这些元素一般是用来收集用户输入的。:enabled 和 :disabled 选择器不会匹配没有禁用状态的元素。

2. **:checked**

使用:checked 选择器可以选中由 checked 属性或者用户勾选的单选按钮或者复选框。

3. **:valid 和 :invalid**

:valid 和:invalid 选择器分别匹配符合和不符合它们的输入验证要求的 input 元素。

4. **:required 和 :optional**

:required 选择器匹配具有 required 属性的 input 元素，这能够确保用户必需输入与 input 元素相关的值才能提交表单。:optional 选择器匹配没有 required 属性的 input 元素。

5. **:in-range 和 :out-of-range**

关于输入验证的一种具体程度更高的变体是选择值限于指定范围的 input 元素。:in-range 选择器匹配位于指定范围内的 input 元素，:out-of-range 选择器匹配位千指定范围之外的 input 元素。

### 13.4.3. 动态伪类选择器

之所以称为动态伪类选择器，是因为它们根据条件的改变匹配元素，是相对于文档的固定状态来说的。随着 JavaScript 广泛用于修改文档内容和元素状态，动态选择器和静态选择器之间的界限线越来越模糊，不过，动态伪类选择器仍然是一类比较特别的选择器。

1. **:link**

:link 选择器匹配超级链接。

2. **:visited**

:visited 选择器匹配用户已访问的超级链接。

3. **:hover**

:hover 选择器匹配用户鼠标悬停在其上的任意元素。鼠标在 HTML 页面内移动时，选中的元素样式会发生改变。

4. **:active**

:active 选择器匹配当前被用户激活的元素。浏览器依然可以自行决定如何诠释激活，但多数浏览器会在鼠标点击（在触摸屏上是手指按压）的情况下使用这个选择器。

5. **:focus**

最后一个动态伪类选择器是 :focus 选择器，它匹配当前获得焦点的元素。

### 13.4.4. 其他伪类选择器

1. **:not()**

CSS 伪类 :not() 用来匹配不符合一组选择器的元素。由于它的作用是防止特定的元素被选中，它也被称为反选伪类。

```css
/* 选择所有不是段落（p）的元素 */
:not(p) {
  color: blue;
}
```

2. **:empty**

:empty 选择器匹配没有定义任何子元素的元素。

3. **:lang()**

:lang 选择器匹配基于 lang 全局属性值的元素。如：:lang(zh-CN)。

3. **:target**

:target CSS 伪类代表一个唯一的页面元素(目标元素)，其 id 与当前 URL 片段匹配。

```css
/* 选择一个ID与当前URL片段匹配的元素*/
:target {
  border: 2px solid black;
}
```

## 13.5. 并集选择器

创建由逗号分隔的多个选择器可以将样式应用到单个选择器匹配的所有元素。

如：

```css
h1,
h2,
h3 {
}
```
