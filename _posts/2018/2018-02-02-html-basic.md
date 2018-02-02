---
layout: post
title:  HTML基础知识
categories: html
tags:  html
---

* content
{:toc}


# HTML入门
## 什么是 HTML?
HTML (HyperText Markup Language) 不是一种编程语言;它是一种标记语言，用于告诉您的浏览器如何构造您访问的网页。它可以像Web开发人员希望的那样复杂或简单。 HTML由一系列的 elements组成, 您可以使用它来封装，包装或标记内容的不同部分，使其以某种方式显示，或以某种方式执行。封闭tags 可以使一点内容成为超链接以链接到Web上的另一页面，斜体字等等。  
例如，采取以下行内容：  
```html
<p>My cat is very grumpy.</p>
```
我们的元素的主要部分是：
- 开始标签（Opening tag）：包括元素的名称（在本例中，p），包裹在开始和结束尖括号中。这表示元素开始或开始生效 - 在这种情况下，表示了一个段落的开头。
- 结束标签（Closing tag）：这与开始标记相同，除了它在元素名称之前包含正斜杠。这表示元素结束的位置 - 在这种情况下，表示了一个段落的结尾. 没有包含结束标记是一个常见的初学者错误，并可能导致奇怪的结果。
- 内容（Content）：这是元素的内容，在这种情况下只是文本。
- 元素（Element）：开始标记，加结束标记，加内容，等于元素。




## 嵌套元素
你也可以把元素放到其它元素之中——这被称作嵌套。如果我们想要表明我们的小猫脾气很暴躁，可以将very嵌套在`<strong>` 中，意味着这个单词被着重强调:  

```html
<p>My cat is <strong>very</strong> grumpy.</p>
```
你需要确保元素被正确的嵌套：在上面的例子中我们先打开`<p>`元素，然后才打开`<strong>`元素，因此必须先将`<strong>`元素关闭，然后再去关闭`<p>`元素。

下面的例子是错误的：  

```html
<p>My cat is <strong>very grumpy.</p></strong>
```
所有的元素都需要正确的打开和关闭，这样才能按你所想的方式展现。如果像上述的例子一样进行了错误的嵌套，那么浏览器会去猜测你想要表达的意思，但很有可能会得出错误的结果。所以永远不要这么做！

## 块级元素和内联元素
在HTML中有两种你需要知道的重要元素类别，块级元素和内联元素。
- 块级元素在页面中以块的形式展现 —— 相对与其前面的内容它会出现在新的一行，其后的内容也会被挤到下一行展现。块级元素通常用于展示页面上结构化的内容，例如段落、列表、导航菜单、页脚等等。一个以block形式展现的块级元素不会被嵌套进内联元素中，但可以嵌套在其它块级元素中。
- 内联元素通常出现在块级元素中并包裹文档内容的一小部分，而不是一整个段落或者一组内容。内联元素不会导致文本换行：它通常出现在一堆文字之间例如超链接元素`<a>`或者强调元素`<em>`和 `<strong>`。

看一看下面的例子：  

```html
<em>first</em><em>second</em><em>third</em>   
<p>fourth</p><p>fifth</p><p>sixth</p>
```

`<em>` 是一个内联元素，所以就像你在下方可以看到的，第一行代码中的三个元素都没有间隙的展示在了同一行。而`<p>`是一个块级元素，所以第二行代码中的每个元素分别都另起了新的一行展现，并且每个段落间都有一些间隔（这是因为默认的浏览器有着默认的展示`<p>`元素的 CSS styling ）。

## 空元素
不是所有元素都拥有开始标签，内容和结束标记. 一些元素只有一个标签，通常用来在此元素所在位置插入/嵌入一些东西 。例如：元素`<img>`是用来在元素`<img>`所在位置插入一张指定的图片。  
例子如下：  

```html
<img src="https://raw.githubusercontent.com/mdn/beginner-html-site/gh-pages/images/firefox-icon.png">
```

## 属性
元素也可以拥有属性，如下：  
```html
<p class="editor-note">My cat is very grumpy</p>
```
属性包含元素的额外信息，这些信息不会出现在实际的内容中。在上述例子中，这个class属性给元素赋了一个识别的名字（id），这个名字此后可以被用来识别此元素的样式信息和其他信息。
一个属性必须包含如下内容：
- 在元素和属性之间有个空格space (如果有一个或多个已存在的属性，就与前一个属性之间有一个空格.)
- 属性后面紧跟着一个“=”符号.
- 有一个属性值,由一对引号“ ”引起来.

## 布尔属性
有时你会看到没有值的属性，它是合法的。这些属性被称为布尔属性，他们只能有跟它的属性名一样的属性值。例如 disabled 属性，他们可以标记表单输入使之变为不可用(变灰色)，此时用户不能向他们输入任何数据。
```html
<input type="text" disabled="disabled">
```
采用如下简写更佳(下面一句为可用可输入数据的文本框，以作为对比)：
```html
<input type="text" disabled>
```

## 省略包围属性值的引号
当你浏览那些粗糙的web网站，你将会看见各种各样奇怪的标记风格，其中就有不给属性值添加引号。在某些情况下它是被允许的，但是其他情况下会破坏你的标记。例如，我们可以写一个只拥有一个href属性的链接，如下：  
```html
<a href=https://www.mozilla.org/>favourite website</a>
```
然而，当我们再添加一个title属性时就会出错，如下：
```html
<a href=https://www.mozilla.org/ title=The Mozilla homepage>favourite website</a>
```
此时浏览器会误解你的标记，它会把title属性理解为三个属性——title的属性值为"The“，另外还有两个布尔属性“Mozilla”和“homepage”。
我们建议始终添加引号——这样可以避免很多问题，并且使代码更易读。

## 单引号或者双引号？
在目前为止，本章内容所有的属性都是由双引号来包裹。也许在一些HTML中，你以前也见过单引号。这只是风格的问题，你可以从中选择一个你喜欢的。以下两种情况都可以：  
```html
<a href="http://www.example.com">A link to my example.</a>
<a href='http://www.example.com'>A link to my example.</a>
```
但你应该注意单引号和双引号不能再一个属性值里面混用。下面的语法是错误的：  

```html
<a href="http://www.example.com'>A link to my example.</a>
```

在一个HTML中已使用一种引号，你可以在此引号中嵌套另外一种引号：  

```html
<a href="http://www.example.com" title="Isn't this fun?">A link to my example.</a>
```
如果你想将引号当作文本显示在html中，你就必须使用 实体引用 。

## 分析HTML文档
学习了一些HTML元素的基础知识，这些元素单独一个是没有意义的。现在我们来学习这些特定元素是怎么被结合起来，从而形成一个完整的HTML页面的：  

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```
分析如下:

- `<!DOCTYPE html>`: 声明文档类型. 很久以前，早期的HTML(大约1991年2月)，文档类型声明类似于链接，规定了HTML页面必须遵从的良好规则，能自动检测错误和其他有用的东西。使用如下：  

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">`
```
然而现在没有人再这样写，需要保证每一个东西都正常工作已成为历史。你只需要知道`<!DOCTYPE html>`是最短的有效的文档声明。
- `<html></html>`: `<html>`元素。这个元素包裹了整个完整的页面，是一个根元素。
- `<head></head>`: `<head>`元素. 这个元素是一个容器，它包含了所有你想包含在HTML页面中但不想在HTML页面中显示的内容。这些内容包括你想在搜索结果中出现的关键字和页面描述，CSS样式，字符集声明等等。以后的章节能学到更多关于`<head>`元素的内容。
- `<meta charset="utf-8">`: 这个元素设置文档使用utf-8字符集编码，utf-8字符集包含了人类大部分的文字。基本上他能识别你放上去的所有文本内容。毫无疑问要使用它，并且它能在以后避免很多其他问题。
- `<title></title>`: 设置页面标题，出现在浏览器标签上，当你标记/收藏页面时它可用来描述页面。
- `<body></body>`: `<body>`元素。包含了你访问页面时所有显示在页面上的内容，文本，图片，音频，游戏等等。

## HTML中的空白
在上面的例子中，你可能已经注意到了在代码中包含了很多的空格——这是没有必要的；下面的两个代码片段是等价的：  

```html
<p>Dogs are silly.</p>
<p>Dogs        are
         silly.</p>
```
无论你用了多少空白(包括空白字符，包括换行), 当渲染这些代码的时候，HTML解释器会将连续出现的空白字符减少为一个单独的空格符。那么为什么我们会使用那么多的空白呢? 答案就是为了可读性 —— 如果你的代码被很好地进行格式化，那么就很容易理解你的代码是怎么回事, 反之就只有聚做一团的混乱. 在我们的HTML代码中，我们让每一个嵌套的元素以两个空格缩进。 你使用什么风格来格式化你的代码取决于你 (比如所对于每层缩进使用多少个空格),但是你应该坚持使用某种风格。

## 实体引用
在HTML中包含特殊字符
在HTML中，字符 <, >,",' 和 & 是特殊字符. 它们是HTML语法自身的一部分, 那么你如何将这些字符包含进你的文本中呢, 比如说如果你真的想要在文本中使用符号&或者小于号, 而不想让它们被浏览器视为代码并被解释?
我们必须使用字符引用 —— 表示字符的特殊编码, 它们可以在那些情况下使用. 每个字符引用以符号&开始, 以分号(;)结束.

| Literal character |	Character reference equivalent    |
| -------------- | ------------------------------------------- |
|     ` <	`       |        `&lt; `    |  
|      `>	`      |        `&gt;`           |  
|      `" `       |        `&quot;`       |  
|      `'`       |        `&apos;`       |  
|      `&	`       |        `&amp;`      |  
在下面的例子中你可以看到两个段落，它们在谈论web技术:  

```html
<p>In HTML, you define a paragraph using the <p> element.</p>
<p>In HTML, you define a paragraph using the &lt;p&gt; element.</p>
```
在上面的实时输出中，你会看到第一段是错误的，因为浏览器会认为第二个`<p>`是开始一个新的段落！  第二段是正确的，因为我们用字符引用来代替了角括号（'<'和'>'符号）.

## HTML注释
如同大部分的编程语言一样，在HTML中有一种可用的机制来在代码中书写注释 —— 注释是被浏览器忽略的，而且是对用户不可见的，它们的目的是允许你描述你的代码是如何工作的和不同部分的代码做了什么等等。 如果你在半年后重新返回你的代码库，而且不能记起你所做的事情 —— 或者当你处理别人的代码的时候， 那么注释是很有用的.
为了将一段HTML中的内容置为注释，你需要将其用特殊的记号`<!--和-->`包括起来， 比如：  

```html
<p>I'm not inside a comment</p>
<!-- <p>I am!</p> -->
```
正如你下面所见的那样，第一段出现在了实时输出中，但是第二段却没有。

## 总结
你已经来到了这篇文章的结尾 —— 希望你享受你的基础的HTML学习的旅程。 在这里你应该可以理解HTML语言的全貌， 它在基础的级别是如何工作，而且可以使用一些元素和属性。 在这个模块的后续文章中，我们会深入一些你已经见过的东西的细节，并且介绍一些新的HTML的特性。未完待续！

# HTML中的head   
在页面加载完成的时候，标签head里的内容，是不会在页面中显示出来的。它包含了像页面的`<title>`(标题) ,CSS(如果你想用CSS来美化页面内容)，图标和其他的元数据(比如 作者，关键词，摘要)。在本文中，我们将包含所有上述的事情，为您在脑海中营造一个很好的基础和代码印象。

## 什么是Head标签?
让我们简单的回顾下上一章提到的HTML 

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>My test page</title>
  </head>
  <body>
    <p>This is my page</p>
  </body>
</html>
```
head 标签是 `<head>` 元素的内容。不像 `<body>` 元素的内容可以显示在浏览器中，head 的内容不会在浏览器中显示，它的作用是包含一些页面的元数据。在下面的例子中，head 的内容很少。  

```html
<head>
  <meta charset="utf-8">
  <title>My test page</title>
</head>
```
当然，在大型的页面中，head 会包含很多的元数据。你可以用 developer tools 去查看你喜欢的网页的 head 的内容。 在这里，我们会告诉你怎么将必须的内容包含在 head 里，而不是将所有能够包含在 head 里的内容都告诉你。我们开始吧。

## 增加一个标题
我们之前已经看到了 `<title>`，它可以用来给 html 文档添加一个标题。你可能会将它和给 body 添加标题的 `<h1>` 元素混淆，有些时候 h1 也会被称作网页标题。但是它们是不同的。

- 当被加载到浏览器中的时候，元素 `<h1>`  会出现在页面中 —— 通常它应该在一个页面中只被使用一次, 它被用来标记你的页面内容的标题(故事的标题，新闻标题或者任何适当的方式）
- 元素 `<title>` 是用来表示整个HTML文档大致内容的元数据(不是文档的内容.)

元素 `<title>` 也被以其他的方式使用着. 比如说，如果你尝试为某个页面添加书签，(Bookmarks > Bookmark This Page, 在火狐浏览器中), 你会看到 `<title>` 的内容被作为建议的书签名.
元素 `<title>` 的内容也被用在搜索的结果中，正如你下面看到的那样。

## 元数据：`<meta>`元素
元数据就是描述数据的数据，而HTML有一个“官方的”方式来为一个文档添加元数据，——  `<meta>` 元素. 当然，其他在这篇文章中提到的东西也可以被当作元数据。 有很多不同种类的 `<meta>` 元素可以被包含进你的页面的`<head>`元素, 但是现在我们还不会尝试去解释所有类型, 这只会引起混乱。 我们会解释一些你常会看到的类型，先让你有个概念。
指定你的文档中字符的编码
在上面的例子中，这行是被包含的：  

```html
<meta charset="utf-8">
```
这个元素简单的指定了文档的字符编码 —— 在这个文档中被允许使用的字符集。 utf-8 是一个通用的字符集，它包含了任何人类语言中的大部分的字符。 这意味着你的web页面可以显示任意的语言; 所以对于你的每一个页面，使用这个设置是很好的! 比如说，你的页面可以很好的处理英语和日语:

## 添加作者和描述
许多`<meta>` 元素包含了name 和 content 特性:

- name 特性指定了meta 元素的类型; 说明该元素包含了什么类型的信息。

- content 指定了实际的元数据内容。
这两个meta 元素对于定义你的页面的作者和提供页面的内容描述是很有用的 。 让我们看一个例子：  

```html
<meta name="author" content="Chris Mills">
<meta name="description" content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications.">
```

指定作者在某些情况下是很有用的：如果你需要联系页面的作者，问一些关于页面内容的问题。 一些内容管理系统能够自动获取页面作者的信息，然后用于某种目的。

指定包含关于页面内容的关键字的页面内容的描述是很有用的，因为它可能或让你的页面在搜索引擎的相关的搜索出现得更多 (这些行为术语上被称为 Search Engine Optimization, or SEO.)

## 其他类型的 metadata
当你在网站上查看源码时，你也会发现其他类型的元数据。你在网站上看到的许多功能都是专有创作，旨在向某些网站(如社交网站)提供可使用的特定信息。

例如，Facebook 编写的元数据协议 Open Graph Data 为网站提供了更丰富的元数据。在 MDN 源代码中，你会发现：  

```html
<meta property="og:image" content="https://developer.cdn.mozilla.net/static/img/opengraph-logo.dc4e08e2f6af.png">
<meta property="og:description" content="The Mozilla Developer Network (MDN) provides
information about Open Web technologies including HTML, CSS, and APIs for both Web sites
and HTML5 Apps. It also documents Mozilla products, like Firefox OS.">
<meta property="og:title" content="Mozilla Developer Network">
```

上面代码展现的一个效果就是，当你在 Facebook 上链接到 MDN 时，该链接将显示一个图像和描述：这为用户提供更丰富的体验。

Twitter 还拥有自己的类型的专有元数据协议，当网站的 URL 显示在 twitter.com 上时，它具有相似的效果。例如下面：  

```html
<meta name="twitter:title" content="Mozilla Developer Network">
```

## 在你的站点增加自定义图标
为了进一步丰富你的网站设计，你可以在元数据中添加对自定义图标的引用，这些将在特定的场合中显示。

这个不起眼的图标已经存在很多很多年了，16 x 16 像素是这种图标的第一种类型。你可以看见这些图标出现在浏览器每一个打开的页面中的标签页中中以及在书签面板中的书签页面中。

页面添加图标的方式有：

- 将其保存在与网站的索引页面相同的目录中，以.ico格式保存（大多数浏览器将支持更通用的格式，如.gif或.png，但使用ICO格式将确保它能在如Internet Explorer 6一样久远的浏览器显示）
- 将以下行添加到HTML `<head>`中以引用它：  

```html
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
```
现代浏览器在各种场合使用favicons，如打开的页面标签页和书签面板中的书签页面。

如今还有很多其他的图标类型可以考虑。 例如，你可以在 MDN 主页的源代码中找到它：  

```html
<!-- third-generation iPad with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="144x144" href="https://developer.cdn.mozilla.net/static/img/favicon144.a6e4162070f4.png">
<!-- iPhone with high-resolution Retina display: -->
<link rel="apple-touch-icon-precomposed" sizes="114x114" href="https://developer.cdn.mozilla.net/static/img/favicon114.0e9fabd44f85.png">
<!-- first- and second-generation iPad: -->
<link rel="apple-touch-icon-precomposed" sizes="72x72" href="https://developer.cdn.mozilla.net/static/img/favicon72.8ff9d87c82a0.png">
<!-- non-Retina iPhone, iPod Touch, and Android 2.1+ devices: -->
<link rel="apple-touch-icon-precomposed" href="https://developer.cdn.mozilla.net/static/img/favicon57.a2490b9a2d76.png">
<!-- basic favicon -->
<link rel="shortcut icon" href="https://developer.cdn.mozilla.net/static/img/favicon32.e02854fdcf73.png">
```
这些注释解释了每个图标的用途 - 这些元素涵盖的东西提供一个高分辨率图标，这些高分辨率图标当网站保存到iPad的主屏幕时使用。

不用担心现在实现所有这些类型的图标 - 这是一个相当先进的功能，你将不会被要求在这个课堂上学习这个知识点。 这里的主要目的是让你提前了解有这一样东西以防当你浏览其他网站的源代码时不理解源代码的含义。

## 在HTML中应用CSS和JavaScript
如今，几乎你使用的所有网站都会使用 CSS 让网页更加炫酷, 使用JavaScript让网页有交互功能, 比如视频播放器，地图，游戏以及更多功能。这些应用在网页中很常见，它们分别使用 `<link>`元素以及 `<script>` 元素。

-  `<link>` 元素经常位于文档的头部，它有2个属性， rel="stylesheet"，表明这是文档的样式表，而 href,包含了样式表文件的路径：  
```html
<link rel="stylesheet" href="my-css-file.css">
```
- `<script>` 部分没必要非要放在文档头部; 实际上，把它放在文档的尾部（在 `</body>`标签之前）是一个更好的选择 ，这样可以确保在加载脚本之前浏览器已经解析了HTML内容（如果脚本加载某个不存在的元素，浏览器会报错）。  
```html
<script src="my-js-file.js"></script>
```
注意： `< script >`元素看起来像一个空元素，但它并不是，因此需要一个结束标记。您还可以选择将脚本放入`< script >`元素中，而不是指向外部脚本文件。

## 为文档设定主语言
最后，值得一提的是你可以（而且确实应该）为你的站点设定语言， 这个可以通过添加lang属性到HTML开始标签中来实现 (参考 meta-example.html)，如下所示：  

```html
<html lang="en-US">
```
这在很多方面都很有用。如果你的HTML文档的语言设置好了，那么你的HTML文档就会被搜索引擎更有效地索引 (例如，允许它在特定于语言的结果中正确显示),对于那些使用屏幕阅读器的视障人士也很有用(比如, 法语和英语中都有“six”这个单词，但是发音却完全不同)。

你还可以将文档的分段设置为不同的语言。例如， 我们可以把日语部分设置为日语， 如下所示：  

```html
<p>Japanese example: <span lang="jp">ご飯が熱い。</span>.</p>
```
这些codes根据 ISO 639-1 标准定义的. 你可以在Language tags in HTML and XML找到更多相关的。

总结
已经到了我们快速学习HTML head的尾声 — 你还能学到更多的相关的, 但是现阶段详尽的讲的太多会无聊且迷惑, 我们只希望你现在在这学到最基本的概念! 下一篇我们将要学习 HTML text 基础.
