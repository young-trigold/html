**目录：**

- [2. HTML 基础](#2-html-基础)
  - [2.1. 元素](#21-元素)
    - [2.1.1. 虚元素](#211-虚元素)
  - [2.2. 元素属性](#22-元素属性)
    - [2.2.1. 元素关系](#221-元素关系)
    - [2.2.2. 元素类型](#222-元素类型)
    - [2.2.3. 布尔属性](#223-布尔属性)
    - [2.2.4. 自定义属性](#224-自定义属性)
  - [2.3. HTML 文档](#23-html-文档)
    - [2.3.1. 外层结构](#231-外层结构)
    - [2.3.2. head](#232-head)
    - [2.3.3. body](#233-body)
  - [2.4. HTML 实体](#24-html-实体)
  - [2.5. 全局属性](#25-全局属性)
    - [2.5.1. 选择器属性](#251-选择器属性)
    - [2.5.2. 键盘快捷键属性](#252-键盘快捷键属性)
    - [2.5.3. contentEditable](#253-contenteditable)
    - [2.5.4. hidden](#254-hidden)
    - [2.5.5. lang](#255-lang)
    - [2.5.6. title](#256-title)
    - [2.5.7. draggable](#257-draggable)
    - [2.5.8. style](#258-style)

# 2. HTML 基础

开发人员多少都知道一点 HTML。近年来它的身影随处可见，即便是那些从不需要写 HTML 代码的人，也可能见过一些。为了让读者打好基础，本章将回头介绍 HTML 的基本知识：HTML 的目标和其工作原理。我会解释一些 HTML 中的基本术语，并且介绍一些几乎所有网页都要用到的核心元素。

顾名思义，HTML 是一种标记语言。其标记以应用于文档内容（例如文本）的元素为其存在的形式。在后面的各节中，我会解释各种 HTML 元素的区别，以及使用各种属性配置这些元素的方法，并且介绍一系列可用于所有 HTML 元素的属性，称为全局属性。

## 2.1. 元素

以下是一个文本内容使用了 HTML 元素的例子：

```html
我正在深入学习
<i>HTML</i>
。
```

这个例子中，我们使用`i`标记了 HTML，使它变为斜体显示。`<i>HTML</i>` 整体为一个 **HTML 元素(HTML Element)**。具体来讲，几乎每一个元素（不是所有的元素）都分为三部分：开始标签（`<i>`），结束标签（`</i>`），和 **元素内容(Element Content)**（HTML）。其中开始标签和结束标签称为 **标签(tag)**。

元素使得浏览器可以根据标签来具体显示被标签包裹起来的内容。不同的标签使得内容有不同的显示效果。例如，`<i>` 标签使得文本斜体显示。

HTML 规定标签名不分大小写，大写和小写标签，对内容的显示效果是相同的。例如：`<I>HTML</I>` 和 `<i>HTML</i>` 的显示效果是相同的。但是最为推荐的标记风格是全部使用小写，这样更为方便，也更加统一。

HTML 规定了各式各样的标签，它们在 HTML 文档中起着不同的作用。`<i>` 标签是文本标签的一个例子。

标签应用在内容上改变内容的显示方式，这种想法在如今受到强烈的反对。现在的观点是标签应用在内容上只可以说明内容的含义或者文档结构，然后使用 CSS 来控制内容的显示，这样便可以做到 HTML 和 CSS 的松散耦合。

基于这些反对，HTML5 引进了很多的 **语义元素(Semantic Element)**，语义元素就是只用来说明内容的含义或者文档结构的，它们不会对内容的显示产生影响。例如，`<nav>` 只用来说明所标记内容表示一个导航链接，不会对 `<nav>` 标签包含的内容的显示产生影响。

虽然 HTML5 引入了很多的语义元素，但大部分以前的那些影响内容显示的标签并没有被废弃，你依然可以使用那些标签。

### 2.1.1. 虚元素

我们刚才说过，并不是所有的元素都包含：开始标签，内容，以及结束标签，实际上，有一种元素只包含一个结束标签，这种元素被称为 **虚元素(Void Element)**。例如，`</hr>` 就是这样一个例子，使用这个元素，会显示一条横线，用来表示内容的分隔。

虚元素并不是一定要用结束标签表示，事实上，你还可以使用开始标签表示。但是为了规范起见，我们推荐使用结束标签。

## 2.2. 元素属性

HTML 元素内可以使用 **属性(Attributes)**。具体来说，你可以在一个元素的开始标签里，使用 `键=值` 来补充这个元素的信息。

来看下面一个例子：

```html
<button id="btn">点击我！</button>
```

这个例子中，button 元素的开始标签里多了一个 `id="btn"`，这相当于指定了这个 button 元素的 id 为值："btn"。

元素的属性只能用在开始标签内，不能用于结束标签。属性值必须使用双引号包含起来，你也可以使用单引号，不过并不推荐。

有些属性可用于所有的 HTML 元素，这些属性称为 **全局属性(Global Attributes)**。而有一些属性只能用于特定的元素，这些属性称为 **局部属性(Local Attributes)**。本书后面
的章节会具体讲解。

一个元素可以使用多个属性，这些属性用空格分开。来看下面一个例子：

```html
<input type="text" name="userName"></input>
```

这个例子中，input 元素使用了 2 个属性：type 和 name。type 用来指定 input 的类型，这里 `type="text"` 指定这个 input 元素为文本类型。name 属性用来指定 input 的名称，这个名称在用 JavaScript 获取这个 input 的时候会用到。

这个例子中，input 元素开始标签内的 autofocus 属性并没有值，我们只是简单地写上了 autofocus，这也当然是可以起到效果的。autofocus 可以自动将焦点转移到 input 元素上。

### 2.2.1. 元素关系

HTML 文档中的元素之间有着明确的关系。如果元素 a 包含了元素 b，那么 b 是 a 元素的 **子元素(child)**，或者说 a 是 b 元素的 **父元素(parent)**。如果元素 a1 和 a2 在并列位置，那么称 a1 和 a2 为 **兄弟元素(sibling)**。

不是任何元素都可以成为某一个元素的子元素，这是有限制的。这种限制取决于父子元素的类型。除此之外，CSS 和 DOM 都会用到元素关系。

### 2.2.2. 元素类型

HTML 规范将元素分为 3 大类：**元数据元素(Metadata Element)**，**流元素(Flow Element)** 和 **短语元素(Phrasing Element)**。

元数据元素描述了文档的元数据信息，向浏览器提供了如何处理文档。

另外两种类型的元素的主要用途就是确定一个元素的合法子元素。短语元素是 HTML 文档的基本组成。流元素是短语元素的超集。

有些元素无法归入上述三种类型，这些元素要么没有什么特别的含义，要么只能用在一些非常有限的情况下。li 元素就是受限元素的一个例子。它表示列表项，只能有三种父元素： ol（表示有序列表）、ul（表示无序列表） 和 menu（表示菜单）。

### 2.2.3. 布尔属性

有些属性不需要一个值，只需写上属性键即可。这种属性称为 **布尔属性(Boolean Attributes)**。

来看一个例子：

```html
<input type="text" name="userName" autofocus></input>
```

### 2.2.4. 自定义属性

除了 HTML 内置的元素属性外，开发者可以自定义属性，这些自定义属性的键必须以 `data-` 开头。

例如：

```html
<article
  id="electric-cars"
  data-columns="3"
  data-index-number="12314"
  data-parent="cars"
>
  ...
</article>
```

这个例子中，有 3 个自定义属性：data-columns，data-index-number，data-parent。它们可以指定这个 article 元素的所在列，索引号，以及父元素信息。

自定义属性配合 JavaScript 非常方便。

## 2.3. HTML 文档

HTML 元素是 HTML 文档的构成单位。通过各式各样的元素的重复，嵌套，最终形成了 HTML 文档，也就是网页。但 HTML 文档一般有约定俗称的结构。

下面展示了一个通用的 HTML 文档结构：

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <title>文档</title>
  </head>
  <body>
    一段文本。
  <body>
</html>
```

下面的章节我们会一步步介绍。

### 2.3.1. 外层结构

HTML 文档的第一行是文档类型声明：`<!DOCTYPE html>`。这个元素表示这个文档是 HTML5 的 HTML 文档。在历史上，具有同等地位的还有其他一些标记语言，文档中可能会混合使用多种标记语言。但如今 HTML5 已经成为占绝对优势的标记语言，即使在文档中省略 DOCTYPE，绝大多数浏览器仍然假定处理的是 HTML5 文档。但是写上总是保险的做法。

紧接着文档类型声明的是 html 元素，html 元素用于包含 head 和 body 元素，使得文档声明和文档分隔清楚。

### 2.3.2. head

**元数据元素(meta-data Element)** 用来描述文档的信息，并不是文档的内容。所有的元数据元素都被放在 head 元素内部。例如 `<meta charset="utf-8">` 指定文档的字符集为 utf-8。

head 内常用的还有 title 元素，用来指定网页标签页的标题。除此之外，link 元素用来指定文档需要的外部链接信息，如 `<link rel="stylesheet" href="main.css">` 指定了文档的外部样式表。style 和 script 元素用来指定内联的层叠样式表和脚本。

### 2.3.3. body

head 元素用来放置文档元信息元素，而 body 元素放置的元素就是文档实际的内容。

我们编写 HTML 文档实际上大部分都在编写 HTML 文档的内容。因此都是在 body 元素内部编写的。

## 2.4. HTML 实体

从本章的例子中可以看到，HTML 文档中有些字符具有特殊含义最明显的是<和>这两个字符。有时需要在文档内容中用到这些字符，但不想让它们被当做 HTML 处理。为此应该使用 **HTML 实体(HTML entity)**。实体是浏览器用来替代特殊字符的一种代码。下表列出了一些常用实体。

| Result       | Description | Entity Name | Entity Number |
| ------------ | ----------- | ----------- | ------------- |
| non-breaking | 空格        | &nbsp;      | &#160;        |
| <            | 小于        | &lt;        | &#60;         |
| >            | 大于        | &gt;        | &#62;         |
| &            | 和          | &amp;       | &#38;         |
| "            | 双引号      | &quot;      | &#34;         |
| '            | 单引号      | &apos;      | &#39;         |
| ©            | 版权        | &copy;      | &#169;        |
| ®            | 注册商标    | &reg;       | &#174;        |

每个特殊字符都有一个实体编号，可以用来在文档内容中代表该字符。例如，字符 & 的实体编号是&#38;。特别常用的特殊字符还有对应的实体名称。例如，对于浏览器来说，&#38 和 &amp 是相同的。

## 2.5. 全局属性

前面讲过全局属性可以用于所有的 HTML 元素，本节涉及了一些常用的全局属性。

### 2.5.1. 选择器属性

class 和 id 属性可以标记元素的类别和唯一标识符。这在 CSS 选择器以及 JavaScript 中获取和选择元素非常有用。

class 和 id 属性的唯一区别就是 class 属性可以标识一类元素，而 id 属性只可以标识一个元素。

### 2.5.2. 键盘快捷键属性

1. **tabIndx**

tabIndex 全局属性可以指定使用键盘上的 Tab 键转移焦点索引。例如：

```html
<body>
  <button tabindex="-1">点击我！</button>
  <label>
    User Name
    <input type="text" tabindex="1" />
  </label>

  <label>
    Password
    <input type="password" tabindex="2" />
  </label>
</body>
```

在这个例子中，我们为 button 设置了 tabIndex 为 -1，这就意味着 button 不能通过 tab 键转移到焦点。而其他两个 Input 分别设置了 tabIndex 为 1 和 2，这样在用 tab 切换焦点时，我们就可以先切换到用户名字段，再到密码字段。

2. **accessKey**

accessKey 为元素设置了焦点键盘快捷键。用户可以通过键盘快捷键将焦点方便地转到元素。不同地浏览器快捷键可能不同，详情参考[这篇文章](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/accesskey)。Chrome 浏览器可以使用 Alt + accessKet 的方式。

例如：

```html
<!DOCTYPE html>
<html lang="zh-CN">
  <head>
    <meta charset="utf-8">
    <title>Doc</title>
  </head>
  <body>
    <button accesskey="u">上传</button>
    <button accesskey="s">提交</button>
  <body>
</html>
```

这个 html 设计了两个按钮分别带有 accessKey 为 "u" 和 "s"。用户可以通过 Alt + U 将焦点快捷地转到上传按钮上。

### 2.5.3. contentEditable

contentEditable 是 HTML5 新增的属性，这个属性设计的目的是富文本编辑。这个属性可以将一个元素变为可编辑状态。
这个属性往往要配合 document.execCommand() 方法以实现富文本编辑。

MDN 的[这篇文章](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Editable_content) 中实现了一个复杂的富文本编辑器。效果如下：

![2-7-contentEditable](illustrations/2-7-contentEditable.png)

### 2.5.4. hidden

全局属性 hidden 是一个布尔属性，表示一个元素尚未或者不再相关。例如，它可以被用来隐藏一个页面元素直到登录完毕。如果一个元素设置了这个属性，它就不会被显示。

hidden 属性不能用于隐藏那些可以在其它板块中合理显示的内容。 例如，用 hidden 属性去隐藏一个选项卡对话框种的面板是不正确的，因为选项卡界面只不过是溢出显示的一种——一个可以等量于一个只显示所有 form 表单控件的拥有滚动条的大页面。类似地，用 hidden 属性在某个特定板块中隐藏一部分内容也是不正确的，——如果某些内容被标记为隐藏，它将从所有版块中隐藏,包括例如屏幕阅读器.

隐藏元素不应与非隐藏元素链接，作为隐藏元素的后代的元素仍然是活动的，这意味着脚本元素仍然可以执行，表单元素仍然可以提交。

比如说，用 href 标签链接到一个带有 hidden 标签的区块是不对的。 如果这个区块和这个页面不相干，或者这个区块不适用于这个页面，那没有任何理由需要链接到它。

不过，你还是可以使用 ARIA aria-describedby 标签去引用本身是隐藏的一些描述。

类似的，你也可以将一个带有 hidden 标签的 canvas 元素作为屏幕外的缓存区域，或者在表单控件中引用一个已经隐藏的表单。

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
    <div id="target">隐藏文字</div>
    <button id="btn">切换隐藏</button>
    <script>
      const target = document.querySelector('#target');
      const btn = document.querySelector('#btn');

      btn.addEventListener('click', () => {
        if (target.hasAttribute('hidden')) {
          target.removeAttribute('hidden');
        } else {
          target.setAttribute('hidden', 'hidden');
        }
      });
    </script>
  </body>
</html>
```

上面的代码中，通过切换隐藏按钮可以将 div 在隐藏和不隐藏之间切换。

### 2.5.5. lang

lang 全局属性参与了元素语言的定义。这个语言是不可编辑元素写入的语言，或者可编辑元素应该写入的语言。标签包含单个条目，值的格式由 用于定义语言的标签 (BCP47) IETF 文档定义。如果标签的内容是空字符串，语言就设为未知。如果标签内容是无效的，根据 BCP47，它就设为无效。

通常在 html 元素上添加 lang 属性可以为整个网页指定语言，你也可以在单独的块上添加 lang 属性，这样语言效果只局限于这个块。

```html
<html lang="zh-CN"></html>
```

### 2.5.6. title

title 全局属性 包含了表示咨询信息文本，和它属于的元素相关。这个信息通常存在，但绝不必要，作为提示信息展示给用户。一些典型用例：

链接：被链接文档的标题或描述
媒体元素，例如图像：描述或关联信息
段落：脚注或者相关的评论
引用：作者信息，以及其他
如果省略了这个属性，就意味着这个元素的最近祖先的标题仍然是相关的（并且可以用作元素的提示信息）。如果这个属性设为空字符串，它就明确意味着，它的最近祖先的标题是不相关的（并且不应用于这个元素的提示信息）。

### 2.5.7. draggable

全局属性 draggable 是一个枚举类型的属性，用于标识元素是否允许使用 拖放操作 API (en-US) 拖动。它的取值如下：

true，表示元素可以被拖动
false，表示元素不可以被拖动
如果该属性没有设值，则默认值 为 auto ，表示使用浏览器定义的默认行为。

这个属性是枚举类型，而不是 布尔类型 。这意味着必须显式指定值为 true 或者 false ，像 `<label draggable>Example Label</label>` 这样的简写是不允许的。正确的用法是 `<label draggable="true">Example Label</label>`。

默认情况下，只有已选中的文本、图片、链接可以拖动。对其它的元素来说，必须按拖动机制的顺序设置 ondragstart 事件才能正常工作。

```html
<p
  draggable="true"
  ondragstart="event.dataTransfer.setData('text/plain', 'This text may be dragged')"
>
  This text
  <strong>may</strong>
  be dragged.
</p>
```

属性 draggable 设置为 "true"，所以这个元素变成可拖拽的。如果该属性被省略或被设置为 "false"，则该元素将不可拖拽，此时拖拽只会选中文本。

draggable 属性可在任意元素上设置，包括图像和链接。然而，对于后两者，该属性的默认值是 true，所以你只会在禁用这二者的拖拽时使用到 draggable 属性，将其设置为 false。

### 2.5.8. style

style 全局属性可以为单个元素指定它的样式，这种指定样式的方式优先级更高。

例如：

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      #target {
        background-color: pink;
      }
    </style>
  </head>
  <body>
    <span id="target" style="background-color: skyblue;">一段文本</span>
  </body>
</html>
```

在这个例子中，div 的背景颜色为天蓝色而不是粉红色。
