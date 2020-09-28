# chapter 7

This chapter is all about the theoretical side of visual rendering in CSS. Why is that necessary? The answer is that with a model as open and powerful as that contained within CSS, no book could hope to cover every possible way of combining properties and effects. You will undoubtedly go on to discover new ways of using CSS. In exploring CSS, you may encounter seemingly strange behaviors in user agents. With a thorough grasp of how the visual rendering model works, you’ll be better able to determine whether a behavior is a correct (if unexpected) consequence of the rendering engine CSS defines.

这个章节是关于css中视觉渲染理论的。为什么要有这个章节？因为css中包含了开放和强大的模型，没有一本书能够涵盖css中所有可能的性能和效果结合的方法。毫无疑问，你将发现很多使用css的新方法。在探索css时，你可能会在用户端土建一些看起来奇怪的行为，通过彻底掌握css模型视觉渲染的工作原理，你能够更好的判断渲染结果是不是css渲染引擎定义的正确结果。

## Basic Boxes

At its core, CSS assumes that every element generates one or more rectangular boxes, called element boxes. (Future versions of the specification may allow for nonrectangular boxes, and indeed there have been proposals to change this, but for now everything is rectangular.) Each element box has a content area at its center. This content area is surrounded by optional amounts of padding, borders, outlines, and margins. These areas are considered optional because they could all be set to a width of zero, effectively removing them from the element box. An example content area is shown in Figure 7-1, along with the surrounding regions of padding, borders, and margins. 

在css的核心中，它假设每个元素都会生成一个或者多个矩形框，名叫element box.(未来版本可能会允许非矩形的盒子，事实上现在已经有提案想要改变这个，但是现在所有的盒子都是矩形的)。每个元素盒子中心都是content area。这个内容区域被大小可选的padding,borders,outlines和margins包围着。这些区域被认为是可以选择的因为他们都可以被设置为0，相当于从元素盒子中移除了他们。图7-1中展示了一个content,padding,borders和margins的例子。

Each of the margins, borders, and the padding can be set using various side-specific properties, such as margin-left or border-bottom, as well as shorthand properties such as padding. The outline, if any, does not have side-specific properties. The content’s background—a color or tiled image, for example—is applied within the padding by default. The margins are always transparent, allowing the background(s) of any parent element(s) to be visible. Padding cannot have a negative length, but margins can. We’ll explore the effects of negative margins later on.

margins，borders和padding都能设置特定侧面的属性，比如margin-left，border-bottom,在padding中也有这种方便记忆的属性。在大纲中（如果有大纲的话）没有侧边属性。内容的背景可以是一种颜色或者是一个图片，它会默认应用于padding中。margins永远是透明的，这样使得父元素的背景能够被看见。padding不能有负值，但是margins可以。我们稍后会探索margins的负值效果。

![7-1]("7-1.png")

Borders are generated using defined styles, such as solid or inset, and their colors are set using the border-color property. If no color is set, then the border takes on the foreground color of the element’s content. For example, if the text of a paragraph is white, then any borders around that paragraph will be white, unless the author explicitly declares a different border color. If a border style has gaps of some type, then the element’s background is visible through those gaps by default. Finally, the
width of a border can never be negative.

border通过定义样式生成，比如solid和inset,他们的颜色由border-color属性设置。如果没有设置颜色，border会使用元素的颜色。例如，假设一个文本段落是白色，那它周围所有的border也是白色的，除非作者特地去声明一个不同的颜色。如果border样式是有空隙的，默认元素的背景能够在缝隙中显示。最后，border的宽度不能是负值。

The various components of an element box can be affected via a number of properties, such as width or border-right. Many of these properties will be used in this book, even though they aren’t defined here

元素框的各种组件能通过各种属性改变，例如width和border-right属性是修改宽度和右边框的。这本书中会用到其中的很多属性，尽管他们没有在这里提到过。

### A Quick Refresher
复习一下

Let’s quickly review the kinds of boxes we’ll be discussing, as well as some important terms that are needed to follow the explanations to come:

让我们快速的复习一下我们将要讨论的各种盒模型，以及在接下来将要用到的一些术语：

Normal flow
正常流

This is the left-to-right, top-to-bottom rendering of text in Western languages and the familiar text layout of traditional HTML documents. Note that the flow direction may be changed in non-Western languages. Most elements are in the normal flow, and the only way for an element to leave the normal flow is to be floated, positioned, or made into a flexible box or grid layout element. Remember, the discussions in this chapter cover only elements in the normal flow

在西方语言和传统文档中是从左到右，从上到下的渲染。注意，在非西方语言中流的方向可能会不同。大多数元素都是正常流，使元素脱离正常流的唯一方法是使用floate,positon属性，或者使用弹性盒子，网格布局。记住，这个章节讨论的都是正常流。

Nonreplaced element
非替代的元素

This is an element whose content is contained within the document. For example, a paragraph (p) is a nonreplaced element because its textual content is found within the element itself.

这是在文档内容中包含的元素，例如，一个段落p标签就是一个不会被替代的元素，因为他的文本内容能够在元素中找到

Replaced element
替代元素

This is an element that serves as a placeholder for something else. The classic example of a replaced element is the img element, which simply points to an image file that is inserted into the document’s flow at the point where the img element itself is found. Most form elements are also replaced (e.g., <input type="radio">).

这是一个为其他东西占位子的元素。最经典的替代元素是img
元素，它指向了要插入到文档中img位置的图片文件。大多数表单元素是替代元素。


Root element
根元素

This is the element at the top of the document tree. In HTML documents, this is the element html. In XML documents, it can be whatever the language permits; for example, the root element of RSS files is rss.

根元素是在文档树顶部的元素。在HTML中，根元素是html元素，在xml文档中，根元素可以是该语言允许的任何元素。例如，RSS文件中的根元素是rss.

Block box
块盒子

This is a box that an element such as a paragraph, heading, or div generates. These boxes generate “new lines” both before and after their boxes when in the normal flow so that block boxes in the normal flow stack vertically, one after another. Any element can be made to generate a block box by declaring display:block.

这是像段落，头部或者div标签生成的盒子。在正常流中，这些盒子在它们前后生成了新的一行，所以在正常流中块盒子是一个接一个垂直堆叠的。任何元素可以通过display:block声明生成一个块盒子。

Inline box
行内盒子

This is a box that an element such as strong or span generates. These boxes do not generate “line breaks” before or after themselves. Any element can be made to generate an inline box by declaring display: inline.

这是像strong或者span元素生成的盒子。这些盒子不会在前后生成break。任何元素都能够通过设置dispaly：inline的方式生成行内盒子。

Inline-block box
行内块盒子

This is a box that is like a block box internally, but acts like an inline box externally. It acts similar to, but not quite the same as, a replaced element. Imagine picking up a div and sticking it into a line of text as if it were an inline image, and you’ve got the idea.

这是一个内部表现像块级盒子但是外部行为像行内盒子。它表现的像一个代替元素，但又不完全相同。
想象你将一个div元素插入一行文本中，假想它就是一个行内图片，这样你就明白了。

There are several other types of boxes, such as table-cell boxes, but they won’t be covered in this book for a variety of reasons—not the least of which is that their complexity demands a book of its own, and very few authors will actually wrestle with them on a regular basis.

还有其他种类的盒子，比如表格单元盒子，但是出于各种原因它不会在这本书中涉及，他们的复杂性需要有专门的一本书，只有很少的作者会定期与它们的搏斗。

### The Containing Block
包含块

There is one more kind of box that we need to examine in detail, and in this case enough detail that it merits its own section: the containing block.

我们需要特别详细解释一种盒子，它有自己的部分:包含块。



Every element’s box is laid out with respect to its containing block; in a very real way, the containing block is the “layout context” for a box. CSS defines a series of rules for determining a box’s containing block. We’ll cover only those rules that pertain to the concepts covered in this book in order to keep our focus.

每个元素盒子相对于包含块进行定位。通常，包含块是一个盒子中的layout context.........


For an element in the normal, Western-style flow of text, the containing block forms from the content edge of the nearest ancestor that generated a list item or block box which includes all table-related boxes (e.g., those generated by table cells). Consider the following markup:

对于普通的西式文件流中的元素，包含的块形成于最近的祖先的内容边缘，它生成一个列表项或块框，其中包括所有与表相关的框(例如，由表单元格生成的框)。考虑以下标记:
```javascript
<body>
  <div>
    <p>This is a paragraph.</p>
  </div>
</body>
```

In this very simple markup, the containing block for the p element’s block box is the div element’s block box, as that is the closest ancestor element box that is a block or a list item (in this case, it’s a block box). Similarly, the div’s containing block is the body’s box. Thus, the layout of the p is dependent on the layout of the div, which is in turn dependent on the layout of the body element.

在这个非常简单的标记种，p的包含块是块级元素div,因为包含块是最邻近的块或者列表祖先元素（在这个例子中是块）。同样的，div的包含块是body盒子。因此，p的布局依赖于div的位置，div的布局依赖于body元素的位置。

And above that, the layout of the body element is dependent on the layout of the html element, whose box creates what is called the initial containing block. It’s unique in that the viewport—the browser window in screen media, or the printable area of the page in print media—determines its dimensions, not the size of the content of the root element. It’s a subtle distinction, and usually not a very important one, but it does exist.

在上面，body元素的布局依赖于html元素的布局，html盒子生成了初始包含块。他的独特之处在于，视图(屏幕媒体中的浏览器窗口或打印媒体中的页面的可打印区域)决定了它的尺寸，而不是根元素内容的大小。这是一个微妙的区别，通常不是很重要，但是它存在。

## Altering Element Display

You can affect the way a user agent displays by setting a value for the property display. Now that we’ve taken a close look at visual formatting, let’s consider the display property and discuss two more of its values using concepts from earlier in the book.

你可以通过给display属性设置值的方法来影响客户端的显示方式。现在我们已经仔细研究了可视化格式化，让我们考虑 display 属性，并使用本书前面的概念讨论它的另外两个值。

![7-2]("7-1.png")
![7-2-1]("7-1.png")

We’ll ignore the ruby- and table-related values, since they’re far too complex for this chapter, and we’ll also ignore the value list-item, since it’s very similar to block boxes. We’ve spent quite some time discussing block and inline boxes, but let’s spend a moment talking about how altering an element’s display role can alter layout before we look at inline-block.

我们将会忽略ruby- 和table- 相关的值，因为它们在这个章节中太复杂了，我们也会忽略list-item值，因为他与块盒子类似。我们已经花了不少事件来讨论块和行内盒子，在我们学习inline-block之前我们先花点时间讨论修改元素的display属性如何影响元素布局的。

### Changing Roles

When it comes to styling a document, it’s handy to be able to change the type of box an element generates. For example, suppose we have a series of links in a nav that we’d like to lay out as a vertical sidebar:

当涉及到文档样式时，改变一个元素生成的盒子类型时很方便的。例如，假设在nav中有很多个链接，我们希望布局成一个垂直侧边栏：
```javascript
<nav>
 <a href="index.html">WidgetCo Home</a> 
 <a href="products.html">Products</a>
 <a href="services.html">Services</a>
 <a href="fun.html">Widgety Fun!</a>
 <a href="support.html">Support</a> 
 <a href="about.html" id="current">About Us</a> 
 <a href="contact.html">Contact</a> 
</nav>
```

We could put all the links into table cells, or wrap each one in its own nav—or we could just make them all block-level elements, like this:

我们可以把所有的链接放到表格单元格中，或者把每个链接都包装在它自己的导航中，或者我们可以让它们都是块级元素，就像这样:

nav a {
  display: block;
}

This will make every a element within the navigation nav a block-level element. If we add on a few more styles, we could have a result like that shown in Figure 7-2.

这将会使nav中的每个a元素变成块级元素。如果你在a上再加一点样式，你可能会得到图7-2的结果：

![Figure7-2]("Figure7-2.png")

Changing display roles can be useful in cases where you want non-CSS browsers to get the navigation links as inline elements but to lay out the same links as block-level elements. With the links as blocks, you can style them as you would div or p elements, with the advantage that the entire element box becomes part of the link. Thus, if a user’s mouse pointer hovers anywhere in the element box, she can then click the link.

当你想让非css游览器将导航链接当成块级元素布局，而不是将导航链接当成行内元素时，修改display属性时有用的。使用作为块的链接，可以像div或p元素那样对它们进行样式设置，这样做的好处是整个元素框成为链接的一部分。因此，如果用户的鼠标指针在元素框中的任何位置停留，她都可以单击该链接。

You may also want to take elements and make them inline. Suppose we have an unordered list of names:













