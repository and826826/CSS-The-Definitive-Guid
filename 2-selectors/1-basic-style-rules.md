# Basic Style Rules

As stated, a central feature of CSS is its ability to apply certain rules to an entire set of element types in a document. For example, let’s say that you want to make the text of all h2 elements appear gray. Using old-school HTML, you’d have to do this by inserting <font color="gray">…</font> tags inside all your h2 elements. Using the style attribute, which is also bad practice, would require you to include style="color: gray;" in all your h2 elements, like this:

如上所说，css的核心特性是它将各种规则应用到文档中的所有元素。例如，假设你想要让所有h2元素呈现灰色。使用旧html，你不得不在每个h2元素里面插入<font color="gray">…</font>。使用style属性，也是一个糟糕的体验，需要你在所有h2元素中加入style="color:gray",像下面：

<h2><font color="gray">This is h2 text</font></h2> 
<h2 style="color: gray;">This is h2 text</h2>

This will be a tedious process if your document contains a lot of h2 elements. Worse, if you later decide that you want all those h2s to be green instead of gray, you’d have to start the manual tagging all over again. (Yes, this is really how it used to be done!) CSS allows you to create rules that are simple to change, edit, and apply to all the text elements you define (the next section will explain how these rules work). For example, you can write this rule once to make all your h2 elements gray:

如果你的文档中包含很多个h2元素，这是一个非常枯燥的过程。更糟糕的是，如果以后你想让所有的h2元素是绿色而不是灰色，你不得不重新修改标签。（没错，过去就是这么做的）CSS允许你创建方便改变，修改，应用到所有的你定义的文本元素上（下一个章节会解释这些规则如何工作）。例如，你可以写一个规则让所有的h2元素变灰：

h2 {color: gray;}

If you want to change all h2 text to another color—say, silver—just alter the value:

如果你想要所有h2字体成另一种颜色，比如银色，只需要改变值：

h2 {color: silver;}

## Element Selectors

An element selector is most often an HTML element, but not always. For example, if a CSS file contains styles for an XML document, the element selectors might look something like this:

元素选择器通常是一个HTML元素，但不总是。例如，如果一个CSS文件包含了XML文档的样式，元素选择器可能看起来像下面一样：

quote {color: gray;} 
bib {color: red;} 
booktitle {color: purple;} 
myElement {color: red;}

In other words, the elements of the document serve as the most basic selectors. In XML, a selector could be anything, since XML allows for the creation of new markup languages that can have just about anything as an element name. If you’re styling an HTML document, on the other hand, the selector will generally be one of the many HTML elements such as p, h3, em, a, or even html itself. For example:

换句话说，文档的元素是最基本的选择器。在XML中，什么都可能使一个选择器，因为XML允许创建新的标记语言，它们可以任意取名。如果你给一个HTML文档添加样式，另一方面，选择器通常是众多HTML元素中的一个。比如p,h3,em或者html本身，例如：

html {color: black;} h1 {color: gray;} h2 {color: silver;}

Once you’ve globally applied styles directly to elements, you can shift those styles  from one element to another. Let’s say you decide that the paragraph text, not the h1 elements, in Figure 2-1 should be gray. No problem. Just change the h1 selector to p:

一旦你全局应用样式到元素上，你将可以这些样式从一个元素转移到另一个。假设你决定蚊子段落是灰色，而不是h1元素，没问题，只要改变h1为p:

html {color: black;} 
p {color: gray;} 
h2 {color: silver;}

## Declarations and Keywords

The declaration block contains one or more declarations. A declaration is always formatted as a property followed by a colon and then a value followed by a semicolon. The colon and semicolon can be followed by zero or more spaces. In nearly all cases, a value is either a single keyword or a space-separated list of one or more keywords that are permitted for that property. If you use an incorrect property or value in a declaration, the whole rule will be ignored. Thus, the following two declarations would fail:

声明块包含一个或多个声明。一个声明总是属性后面是冒号，接着是属性值和分号。冒号和分号后面可以是一个或多个空格。在大多数情况下，属性值要么单个关键字，要么是由空格分开的多个关键字。如果你在声明中使用你不恰当的值，整个声明都会被忽视。因此，下面两种声明会失效：

brain-size: 2cm; /* unknown property 'brain-size' */ 
color: ultraviolet; /* unknown value 'ultraviolet' */

In an instance where you can use more than one keyword for a property’s value, the keywords are usually separated by spaces, with some cases requiring slashes (/) or commas. Not every property can accept multiple keywords, but many, such as the font property, can. Let’s say you want to define medium-sized Helvetica for paragraph text。

在实例中你可以使用一个或多个关键字作为属性的值，关键字通常用空格分开，有些情况下需要使用反斜线或者逗号。不是所有的属性值都能有多个关键字，但是大多数都可以，比如font属性值。假设你想要为段落定义中等大小的Helvetica字体。

The rule would read as follows:

规则会像下面：

p {font: medium Helvetica;}

Note the space between medium and Helvetica, each of which is a keyword (the first is the font’s size and the second is the actual font name). The space allows the user agent to distinguish between the two keywords and apply them correctly. The semicolon indicates that the declaration has been concluded.

由于medium和Helvatica之间的空格，他们都是关键字（第一个指定了字体大小，第二个指定了字体名字）。这个空格让客户端能够辨别这个两个关键词并正确的应用它们。分号表明这个声明已经结束。

These space-separated words are referred to as keywords because, taken together, they form the value of the property in question. For instance, consider the following fictional rule:









