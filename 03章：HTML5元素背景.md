**目录：**

- [4. HTML5 元素背景](#4-html5-元素背景)
  - [4.1. 语义和呈现分离](#41-语义和呈现分离)
  - [4.2. 元素选用原则](#42-元素选用原则)
    - [4.2.1. 少亦可为多](#421-少亦可为多)
    - [4.2.2. 别误用元素](#422-别误用元素)
    - [4.2.3. 具体为佳，一以贯之](#423-具体为佳一以贯之)
    - [4.2.4. 对用户不要想当然](#424-对用户不要想当然)
  - [4.3. 元素说明体例](#43-元素说明体例)
  - [4.4. 元素速览](#44-元素速览)
    - [4.4.1. 文档和元数据元素](#441-文档和元数据元素)
    - [4.4.2. 内容分区](#442-内容分区)
    - [4.4.3. 内容分组](#443-内容分组)
    - [4.4.4. 文本元素](#444-文本元素)
    - [4.4.5. 表格](#445-表格)
    - [4.4.6. 表单](#446-表单)
    - [4.4.7. 嵌入内容](#447-嵌入内容)

# 4. HTML5 元素背景

HTML5 定义的各种元素将从下一章开始介绍。许多元素在 HTML4 中也存在，但是很多情况下元素的含义已经发生了变化，或者其使用方式已经有所不同。在介绍这些元素之前，我想先介绍一下它们的背景知识，为后续各章奠定基础。知道如何使用这些元素与理解其含义同等重要。

## 4.1. 语义和呈现分离

HTML5 中的一大主要变化是基本信念方面的：将元素的语义与元素对其内容呈现结果的影响分开。从原理上讲这的确合乎情理。HTML 元素负责文档内容的结构和含义，内容的呈现则由应用于元素上的 CSS 样式控制。HTML 文档的用户未必都需要显示它们，不掺合呈现方面的事有助于简化 HTML 的处理以及从中自动提炼含义。

HTML5 中新增的大多数元素都有具体的含义。例如，article 元素可以用来表示适于联合供稿的独立成篇的内容，而 figure 元素表示的自然是图片。

HTMIA 中的许多元素产生在呈现与含义分离观念形成之前。这造成了一种尴尬局面。以 b 元素为例，在 HTML5 之前的版本中，b 元素会指示浏览器以粗体显示其开始和结束标签之间的内容。而 HTML5 不再提倡纯属呈现因素的元素，所以给 b 元素下了个新定义（以下内容摘自 w3c.org 的"HTML: The Markup Language"):

b 元素表示一段文字（将这段文宇从周围文字中凸现出未并不表示特别的强调或重要性），习惯上使用粗体呈现，其使用场合包括文章提要中的关键宇或产品评论中的产品名称等。

这番裹脚布一般的辞令无非是说：b 元素告诉浏览器用粗体显示文字。b 元素没有任何语义，它只起呈现方面的作用。这个圆滑的定义透露了 HTML5 的一个重要信号：我们处在过渡时期。保留那些旧元素是因为它们用得实在太广泛了。让 HTML5 抛弃那些 HTMIA 元素是不切实际的，那样做无疑会减缓其被采用的进程。这样一来，HTML5 就成了一个“双速” 标准。一部分元素（特别是那些新元素）只有语义方面的作用；而另一部分元素（特别是那些名字只有一个字母的）因为招牌如此之老， 新标准在呈现与含义分离的原则上也只得向其屈服：尽管它不愿坦然承认这一点。

从下一章开始，在阅读元素说明的时候，对新思维和老路子之间的这种敏感关系最好要心里有数。它确实有助于解释读者碰到的一些琐碎的怪象。

我的建议是：在语义方面要求严格点不为过，只要有条件，尽量避用那些具有浓重呈现意味或纯粹起呈现作用的元素。定义一个自定义类然后借助它应用所需样式并不复杂。只要做到样式的采用是以内容类型为依据而不是随心所欲，你至少也保持了一颗向着语义的心。

## 4.2. 元素选用原则

就算撇开呈现方面的事不论，HTML5 规范仍然存在一些含混的地方。有些元素过于一般化，乍一看可能不招人喜欢。

那些元素固然一般化，但这是因为用 HTML 元素来标记的内容类型实在太多了。我写的大多数都是本书这样的东西，所以见到 section、article、heading 和 figure 这些术语的时候，想到的是 Apress 出版社在结构和样式方面对作者所提的要求。换了别的内容，同一批术语的含义却又不一样了。例如，技术规范、合同和博客文章都具有 section，但这个术语在三种情况下的含义截然不同。我们没有为书籍、技术规范、合同和博客文章中的 section 各自定义一个术语，而是使用一个通用的术语，附加一定的解释。在选择用来标记内容的元素方面我给读者总结了几条原则，接下来我们就来逐一说明。

### 4.2.1. 少亦可为多

开发者在使用元素的时候容易忘乎所以，把文档弄得标记密布。标记只应该应内容对语义的需要使用。不需要定义复杂标题也就不需要使用 hgroup 元素，只有那些引文比较重要的文档（如期刊文章）才需要用 cite 元素标记的详细引文。

判断该用多少标记需要经验。有条经验法则是：问问自己打算如何发挥一个元素的语义作用，如果不能马上答出就不用这个元素。

### 4.2.2. 别误用元素

每个元素针对的是一种特定类型的内容即便像 b 元素这类纯属呈现用途的元素也是如此。对内容进行标记时，只宜将元素用于它们原定的用途，不要创造自有的语义。如果找不到适合自己所要含义的元素，可以考虑使用通用元素（如 span 或 div)， 并且用全局属性 class 表明其含义。CSS 样式不是类属性唯一的用途。

### 4.2.3. 具体为佳，一以贯之

用来标记内容的元素应该选择最为具体的那个。如果已有元素能恰当表明内容的类型， 就不要使用通用元素。HTML4 中存在一种依赖 div 元素构建页面结构的倾向，其缺陷在于它们的语义并非显而易见。有些人或许会定义一个名为 article 的类，并且藉以应用各种样式，但是这样做所传达出的含义无法与使用 article 元素相提并论。

同样，同一个元素的使用在整个页面、网站或 Web 应用系统上要保持一致。对于作者来说，他们以后修改自己的 HTML 文档的工作可以因此更加轻松，对于要处理 HTML 文档的其他人亦然。

### 4.2.4. 对用户不要想当然

有人可能觉得 HTML 文档的用户关心的只是它在浏览器中的呈现结果，所以不用为标记的语义准确性劳神。呈现与语义分离原则的目的完全是为了让 HTML 文档更易千程序化处理，所以随着 HTML5 的采用和实现愈加广泛，HTML 内容的这种使用会日益增多。如果不关心标记的准确性和一致性，这样的 HTML 文档处理起来更为困难，用户能为其找到的用处也很有限。

## 4.3. 元素说明体例

本书在介绍每一个元素时，都会列出一个摘要表，表中襄括了与该元素相关的要点，读者在制作 HTML 文档时可以回头参考一下。下表是这种摘要表的一个例子。它介绍的是用来表示有序列表的 ol 元素。

| 元素              | ol                                                                                                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 元素类型          | 流元素                                                                                                                                                             |
| 允许具有的父元素  | 任何可以包含流元素的元素                                                                                                                                           |
| 局部属性          | start、reversed 和 type                                                                                                                                            |
| 内容              | 0、或多个 li 元素                                                                                                                                                  |
| 标签用法          | 开始和结束标签                                                                                                                                                     |
| 是否为 HTML5 新增 | 否                                                                                                                                                                 |
| 在 HTML5 中的变化 | reversed 属性是 HTML5 中新增的。在 HTM 区中已不赞成使用的 start 和 type 属性在 HTML5 中又得以恢复， 不过其含义变成了语义（而不是呈现）方面的。compact 属性不再使用 |
| 习惯样式          | ol { display: block; list-style-type: decimal;margin-before: 1em; margin-after: 1em; margin-start: 0; margin-end: 0;padding-start: 40px; }                         |

摘要表中的信息包括：哪些元素可成为该元素的父元素，该元素可以包含什么类型的内容，标签应该怎样使用，默认呈现样式，该元素是否为 HTML5 新增或在 HTML5 中发生了什么变化。关于允许具有什么父元素和内容的信息，其依据是介绍过的元素类型（主要是流元素和短语元素）。

## 4.4. 元素速览

接下来的表可让读者跑马观花地认识一下后面各章将要介绍的所有 HTML5 元素。

### 4.4.1. 文档和元数据元素

文档和元数据元素的用途包括创建 HTML 文档的上层建筑，向浏览器说明文档的情况，定义脚本程序和 CSS 样式，提供浏览器禁用脚本时要显示的内容。

| 元素     | 说明                                                                                                                                                   | 类型         | 新增或有无变化 |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ | -------------- |
| DOCTYPE  | 表示 HTML 文档的类型                                                                                                                                   | 无           | 有变化         |
| html     | 表示一个 HTML 文档的根（顶级元素），所以它也被称为根元素。所有其他元素必须是此元素的后代。                                                             | 无           | 有变化         |
| head     | 规定文档相关的配置信息（元数据），包括文档的标题，引用的文档样式和脚本等。                                                                             | 无           | 无变化         |
| body     | 表示文档的内容。document.body 属性提供了可以轻松访问文档的 body 元素的脚本。                                                                           | 无           | 有变化         |
| title    | 定义文档的标题，显示在 Browser 的标题栏或标签页上。它只应该包含文本，若是包含有标签，则它包含的任何标签都将被忽略。                                    | 元数据       | 无变化         |
| meta     | 表示那些不能由其它 HTML 元相关（meta-related）元素（(base、link, script、style 或 title）之一表示的任何 Metadata 信息。                                | 元数据       | 有变化         |
| link     | 规定了当前文档与外部资源的关系。该元素最常用于链接样式表，此外也可以被用来创建站点图标(比如 PC 端的“favicon”图标和移动设备上用以显示在主屏幕的图标) 。 | 元数据       | 有变化         |
| style    | 包含文档的样式信息或者文档的部分内容。默认情况下，该标签的样式信息通常是 CSS 的格式。                                                                  | 元数据       | 有变化         |
| script   | 定义内部脚本或外部脚本                                                                                                                                 | 元数据，短语 | 有变化         |
| noscript | 如果页面上的脚本类型不受支持或者当前在浏览器中关闭了脚本，则在 HTML `<noscript>` 元素中定义脚本未被执行时的替代内容。                                  | 元数据，短语 | 有变化         |
| base     | 指定用于一个文档中包含的所有相对 URL 的根 URL。一份中只能有一个 `<base>` 元素。                                                                        | 元数据       | 无变化         |

### 4.4.2. 内容分区

内容分区元素允许你将文档内容从逻辑上进行组织划分。使用包括页眉(header)、页脚(footer)、导航(nav)和标题(h1~h6)等分区元素，来为页面内容创建明确的大纲，以便区分各个章节的内容。

| 元素     | 说明                                                                                                                                                                                   | 类型 | 新增或有无变化 |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- | -------------- |
| header   | 用于展示介绍性内容，通常包含一组介绍性的或是辅助导航的实用元素。它可能包含一些标题元素，但也可能包含其他元素，比如 Logo、搜索框、作者名称，等等。                                      | 流   | 新增           |
| nav      | 表示页面的一部分，其目的是在当前文档或其他文档中提供导航链接。导航部分的常见示例是菜单，目录和索引。                                                                                   | 流   | 新增           |
| main     | 呈现了文档的 body 或应用的主体部分。主体部分由与文档直接相关，或者扩展于文档的中心主题、应用的主要功能部分的内容组成。                                                                 | 流   | 新增           |
| article  | 表示文档、页面、应用或网站中的独立结构，其意在成为可独立分配的或可复用的结构，如在发布中，它可能是论坛帖子、杂志或新闻文章、博客、用户提交的评论、交互式组件，或者其他独立的内容项目。 | 流   | 新增           |
| section  | 表示一个包含在 HTML 文档中的独立部分，它没有更具体的语义元素来表示，一般来说会有包含一个标题。                                                                                         | 流   | 新增           |
| h1 到 h6 | 呈现了六个不同的级别的标题，`<h1>` 级别最高，而 `<h6>` 级别最低。                                                                                                                      | 流   | 无变化         |
| details  | 可创建一个挂件，仅在被切换成展开状态时，它才会显示内含的信息。`<summary>` 元素可为该部件提供概要或者标签。                                                                             | 流   | 新增           |
| summary  | 用作 一个`<details>`元素的一个内容的摘要，标题或图例。                                                                                                                                 | 无   | 新增           |
| aside    | 表示一个和其余页面内容几乎无关的部分，被认为是独立于该内容的一部分并且可以被单独的拆分出来而不会使整体受影响。                                                                         | 流   | 新增           |
| footer   | 表示最近一个章节内容或者根节点（sectioning root ）元素的页脚。一个页脚通常包含该章节作者、版权数据或者与文档相关的链接等信息。                                                         | 流   | 新增           |
| address  | 表示其中的 HTML 提供了某个人或某个组织（等等）的联系信息。                                                                                                                             | 流   | 新增           |

### 4.4.3. 内容分组

| 元素       | 说明                                                                                                                                                                                                                                                         | 类型 | 新增或有无变化 |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---- | -------------- |
| div        | 一个通用型的流内容容器，在不使用 CSS 的情况下，其对内容或布局没有任何影响。                                                                                                                                                                                  | 流   | 无变化         |
| p          | 表示文本的一个段落。该元素通常表现为一整块与相邻文本分离的文本，或以垂直的空白隔离或以首行缩进。                                                                                                                                                             | 流   | 有变化         |
| ol         | 表示有序列表，通常渲染为一个带编号的列表。                                                                                                                                                                                                                   | 流   | 有变化         |
| ul         | 表示一个内可含多个元素的无序列表或项目符号列表。                                                                                                                                                                                                             | 流   | 有变化         |
| li         | 用于表示列表里的条目。它必须包含在一个父元素里：一个有序列表(ol)，一个无序列表(ul)，或者一个菜单 (menu)。在菜单或者无序列表里，列表条目通常用点排列显示；在有序列表里，列表条目通常在左边显示按升序排列的计数，例如数字或者字母。                            | 无   | 有变化         |
| dl         | 是一个包含术语定义以及描述的列表，通常用于展示词汇表或者元数据 (键-值对列表)。                                                                                                                                                                               | 流   | 无变化         |
| dd         | 用于在一个定义列表中声明一个术语。该元素仅能作为 dl 的子元素出现。通常在该元素后面会跟着 dd 元素， 然而，多个连续出现的 `<dt>` 元素都将由出现在它们后面的第一个 dd 元素定义。                                                                                | 无   | 无变化         |
| dd         | 用来指明一个描述列表 (dl) 元素中一个术语的描述。这个元素只能作为描述列表元素的子元素出现，并且必须跟着一个 dt 元素。                                                                                                                                         | 无   | 无变化         |
| pre        | 表示预定义格式文本。在该元素中的文本通常按照原文件中的编排，以等宽字体的形式展现出来，文本中的空白符（比如空格和换行符）都会显示出来。(紧跟在 `<pre>` 开始标签后的换行符也会被省略)                                                                          | 流   | 无变化         |
| blockquote | 代表其中的文字是引用内容。通常在渲染时，这部分的内容会有一定的缩进（注 中说明了如何更改）。若引文来源于网络，则可以将原内容的出处 URL 地址设置到 cite 特性上，若要以文本的形式告知读者引文的出处时，可以通过 cite 元素。                                     | 流   | 无变化         |
| hr         | 表示段落级元素之间的主题转换（例如，一个故事中的场景的改变，或一个章节的主题的改变）。                                                                                                                                                                       | 流   | 有变化         |
| figure     | 代表一段独立的内容, 经常与说明（caption） figcaption 配合使用, 并且作为一个独立的引用单元。当它属于主内容流（main flow）时，它的位置独立于主体。这个标签经常是在主文中引用的图片，插图，表格，代码段等等，当这部分转移到附录中或者其他页面时不会影响到主体。 | 流   | 新增           |
| figcaption | 是与其相关联的图片的说明/标题，用?于描述其父节点 figure 元素里的其他数据。这意味着 `<figcaption>` 在 figure 块里是第一个或最后一个。同时 HTML Figcaption 元素是可选的；如果没有该元素，这个父节点的图片只是会没有说明/标题。                                 | 无   | 新增           |

### 4.4.4. 文本元素

文本元素用来为内容提供基本的结构和含义。

| 元素   | 说明                                                                                                                                                                                                                                                                    | 类型     | 新增或有无变化 |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | -------------- |
| span   | 短语内容的通用行内容器，并没有任何特殊语义。可以使用它来编组元素以达到某种样式意图（通过使用类或者 Id 属性），或者这些元素有着共同的属性，比如 lang。应该在没有其他合适的语义元素时才使用它。`<span>` 与 div 元素很相似，但 div 是一个 块元素 而 `<span>` 则是 行内元素 | 短语     | 无变化         |
| a      | 生成超链接                                                                                                                                                                                                                                                              | 短语，流 | 有变化         |
| strong | 表示文本十分重要，一般用粗体显示。                                                                                                                                                                                                                                      | 短语     | 无变化         |
| em     | 标记出需要用户着重阅读的内容，`<em>` 元素是可以嵌套的，嵌套层次越深，则其包含的内容被认定为越需要着重阅读。                                                                                                                                                             | 短语     | 无变化         |
| b      | 用于吸引读者的注意到该元素的内容上（如果没有另加特别强调）。这个元素过去被认为是粗体（Boldface）元素，并且大多数浏览器仍然将文字显示为粗体。                                                                                                                            | 短语     | 有变化         |
| i      | 表现因某些原因需要区分普通文本的一系列文本。例如技术术语、外文短语或是小说中人物的思想活动等，它的内容通常以斜体显示。                                                                                                                                                  | 短语     | 有变化         |
| u      | 表示一个需要标注为非文本化（non-textual）的内联文本域。默认情况下渲染为一个实线下划线，可以用 CSS 替换。                                                                                                                                                                | 短语     | 有变化         |
| s      | 使用删除线来渲染文本。使用 `<s>`元素来表示不再相关，或者不再准确的事情。                                                                                                                                                                                                | 短语     | 有变化         |
| mark   | HTML 标记文本元素(< Mark >)表示为引用或符号目的而标记或突出显示的文本，这是由于标记的段落在封闭上下文中的相关性或重要性造成的。                                                                                                                                         | 短语     | 新增           |
| del    | 表示一些被从文档中删除的文字内容。                                                                                                                                                                                                                                      | 短语，流 | 新增           |
| ins    | 定义已经被插入文档中的文本。                                                                                                                                                                                                                                            | 短语，流 | 无变化         |
| small  | 表示边注释和附属细则，包括版权和法律文本。                                                                                                                                                                                                                              | 短语     | 有变化         |
| q      | 表示一个封闭的并且是短的行内引用的文本. 这个标签是用来引用短的文本，所以请不要引入换行符; 对于长的文本的引用请使用 blockquote 替代.                                                                                                                                     | 短语     | 无变化         |
| cite   | 表示一个作品的引用，且必须包含作品的标题。这个引用可能是一个根据适当的上下文约定关联引用的元数据的缩写。                                                                                                                                                                | 短语     | 有变化         |
| sub    | 表示下标                                                                                                                                                                                                                                                                | 短语     | 无变化         |
| sup    | 表示上标                                                                                                                                                                                                                                                                | 短语     | 无变化         |
| code   | 呈现一段计算机代码. 默认情况下, 它以浏览器的默认等宽字体显示.                                                                                                                                                                                                           | 短语     | 无变化         |
| var    | 表示变量的名称，或者由用户提供的值。                                                                                                                                                                                                                                    | 短语     | 无变化         |
| samp   | 用于标识计算机程序输出，通常使用浏览器缺省的 monotype 字体（例如 Lucida Console）。                                                                                                                                                                                     | 短语     | 无变化         |
| ruby   | 用来展示东亚文字注音或字符注释                                                                                                                                                                                                                                          | 短语     | 新增           |
| rp     | 用于为那些不能使用 ruby 元素展示 ruby 注解的浏览器，提供随后的圆括号。                                                                                                                                                                                                  | 短语     | 新增           |
| rt     | 包含字符的发音，字符在 ruby 注解中出现，它用于描述东亚字符的发音。这个元素始终在 ruby 元素中使用。                                                                                                                                                                      | 短语     | 新增           |
| abbr   | 用于代表缩写，并且可以通过可选的 title 属性提供完整的描述。                                                                                                                                                                                                             | 短语     | 无变化         |
| time   | 用来表示 24 小时制时间或者公历日期，若表示日期则也可包含时间和时区。                                                                                                                                                                                                    | 短语     | 新增           |
| br     | 在文本中生成一个换行（回车）符号。此元素在写诗和地址时很有用，这些地方的换行都非常重要。                                                                                                                                                                                | 短语     | 无变化         |
| wbr    | 一个文本中的位置，其中浏览器可以选择来换行，虽然它的换行规则可能不会在这里换行。                                                                                                                                                                                        | 短语     | 新增           |
| dfn    | 表示术语的一个定义。                                                                                                                                                                                                                                                    | 短语     | 无变化         |

### 4.4.5. 表格

表格在 HTML5 中的主要变化是不能再用来控制页面布局，这项工作交给了 CSS 布局特性。

| 元素     | 说明                                                                                                                                                                            | 类型 | 新增或有无变化 |
| -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- | -------------- |
| table    | 表示表格数据 — 即通过二维数据表表示的信息。                                                                                                                                     | 流   | 有变化         |
| caption  | 展示一个表格的标题， 它常常作为 table 的第一个子元素出现，同时显示在表格内容的最前面，但是，它同样可以被 CSS 样式化，所以，它同样可以出现在任何一个一个相对于表格的做任意位置。 | 无   | 有变化         |
| thead    | 定义了一组定义表格的列头的行。                                                                                                                                                  | 无   | 有变化         |
| tbody    | 表示表格主体                                                                                                                                                                    | 无   | 有变化         |
| tfoot    | 定义了一组表格中各列的汇总行。                                                                                                                                                  | 无   | 有变化         |
| td       | 定义了一个包含数据的表格单元格                                                                                                                                                  | 无   | 有变化         |
| th       | 表示标题行单元格                                                                                                                                                                | 无   | 有变化         |
| tr       | 表示一行单元格                                                                                                                                                                  | 无   | 有变化         |
| col      | 定义表格中的列，并用于定义所有公共单元格上的公共语义。它通常位于 colgroup 元素内。                                                                                              | 无   | 有变化         |
| colgroup | 用来定义表中的一组列表。                                                                                                                                                        | 无   | 有变化         |

### 4.4.6. 表单

表单元素用于创建 HTML 表单，以便获取用户的输入数据。HTML5 中对这方面关注较多，并且新增了不少元素和特性（包括在用户提交表单时在客户端验证输入数据的功能）。

| 元素     | 说明                                                                  | 类型 | 新增或有无变化 |
| -------- | --------------------------------------------------------------------- | ---- | -------------- |
| form     | 表示文档中的一个区域，此区域包含交互控件，用于向 Web 服务器提交信息。 | 流   | 有变化         |
| fieldset | 表示一组表单元素                                                      | 流   | 有变化         |
| legend   | 表示 fieldset 的说明性标签                                            | 无   | 无变化         |
| label    | 对表单元素的说明标签                                                  | 短语 | 有变化         |
| input    | 表示收集用户输入数据的控件                                            | 短语 | 有变化         |
| textarea | 表示收集用户输入多行文本的控件                                        | 短语 | 有变化         |
| output   | 表示计算结果                                                          | 短语 | 新增           |
| select   | 提供给用户一组的选项                                                  | 短语 | 有变化         |
| datalist | 提供一组建议值                                                        | 流   | 有变化         |
| option   | 表示供用户选择的一个选项                                              | 无   | 无变化         |
| optgroup | 表示一组相关的选项                                                    | 无   | 无变化         |
| button   | 表示提交或者一般的按钮                                                | 短语 | 有变化         |

### 4.4.7. 嵌入内容

嵌入元素用于在 HTML 文档中嵌入内容，例如图片，音频，视频或者画布。

| 元素     | 说明                                                                                                           | 类型     | 新增或有无变化 |
| -------- | -------------------------------------------------------------------------------------------------------------- | -------- | -------------- |
| img      | 嵌入图片                                                                                                       | 短语     | 有变化         |
| svg      | 嵌入可伸缩矢量图                                                                                               | 无       | 新增           |
| grogress | 表示一个进度条                                                                                                 | 流       | 新增           |
| meter    | 用来显示已知范围的标量值或者分数值。                                                                           | 短语     | 新增           |
| audio    | 嵌入音频                                                                                                       | 无       | 新增           |
| video    | 嵌入视频                                                                                                       | 无       | 新增           |
| track    | 被当作媒体元素—audio 和 video 的子元素来使用。它允许指定时序文本字幕（或者基于时间的数据），例如自动处理字幕。 | 无       | 新增           |
| map      | 与 area 属性一起使用来定义一个图像映射(一个可点击的链接区域).                                                  | 短语，流 | 有变化         |
| area     | 在 amp 内部使用，表示一个可点击的热区                                                                          | 短语     | 有变化         |
| embed    | 将外部内容嵌入文档中的指定位置。此内容由外部应用程序或其他交互式内容源（如浏览器插件）提供                     | 短语     | 新增           |
| iframe   | 通过创建一个浏览上下文，在一个文档内部嵌入文档                                                                 | 短语     | 有变化         |
| object   | 表示引入一个外部资源，这个资源可能是一张图片，一个嵌入的浏览上下文，亦或是一个插件所使用的资源。               | 短语，流 | 有变化         |
| param    | 为 object 元素定义参数                                                                                         | 无       | 无变化         |
| source   | 为 audio 或者 video 元素指定多个媒体资源。这是一个空元素。                                                     | 无       | 新增           |
| canvas   | 可被用来通过 JavaScript 绘制图形及图形动画。                                                                   | 短语，流 | 新增           |
