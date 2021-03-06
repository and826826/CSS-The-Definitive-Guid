# Elements 

Elements are the basis of document structure. In HTML, the most common elements are easily recognizable, such as p, table, span, a, and div. Every single element in a document plays a part in its presentation.

元素是文档结构的基础.在HTML中,最常见的元素很容易被认出,比如 p,table,span,a和div元素.一个文档中的每个元素都在页面显示中都扮演着自己的角色

## Replaced and Nonreplaced Elements

Although CSS depends on elements, not all elements are created equally. For example, images and paragraphs are not the same type of element, nor are span and div. In CSS, elements generally take two forms: replaced and nonreplaced.

尽管css依赖于元素,但不是所有元素都是一样的.比如,图片元素和段落元素不是同一种元素,span和div也不是.在CSS中 元素通常有两种形式:替换和非替换

### Replaced elements

Replaced elements are those where the element’s content is replaced by something that is not directly represented by document content. Probably the most familiar HTML example is the img element, which is replaced by an image file external to the document itself. In fact, img has no actual content, as you can see in this simple example:
`<img src="howdy.gif" >`

替换元素: 元素内容会被在文档外部内容所替代.可能最熟悉的例子是img元素,它会被文档外部的图片替换.实际上,imag没有实际的内容,你可以看看下面的例子:
`<img src="howdy.gif" >`

This markup fragment contains only an element name and an attribute. The element presents nothing unless you point it to some external content (in this case, an image specified by the src attribute). If you point to a valid image file, the image will be placed in the document. If not, it will either display nothing or the browser will show a “broken image” placeholder. 
Similarly, the input element is also replaced—by a radio button, checkbox, or text input box, depending on its type.

这个标记中只包含了一个元素名字和一个属性.元素不会显示任何内容除非你指向外部的内容(本例中通过src属性指定图片).如果你指向了一个有效的图片,他会被放在文档对应位置,如果指向一个无效的图片,页面什么也不会显示,游览器可能显示一个"broken image"符号.
同理,input元素也会被替换为单选框,复选框或者输入框,取决于input的type属性.

### Nonreplaced elements

The majority of HTML elements are nonreplaced elements. This means that their content is presented by the user agent (generally a browser) inside a box generated by the element itself. For example, <span>hi there</span> is a nonreplaced element, and the text “hi there” will be displayed by the user agent. This is true of paragraphs, headings, table cells, lists, and almost everything else in HTML.

大多数HTML元素都是非替换元素。这意味着他们的内容是由用户代理（通常是游览器）再元素自己的位置上显示的。例如 ，`<span> hi there<span>`是非替换元素，hi there 会被用户代理显示。段落，标题，表格单元，列表，几乎HTML中的所有元素都是这样的

## Element Display Roles

In addition to replaced and nonreplaced elements, CSS uses two other basic types of elements: block-level and inline-level. There are many more display types, but these are the most basic, and the types to which most if not all other display types refer. The block and inline types will be familiar to authors who have spent time with HTML markup and its display in web browsers. The elements are illustrated in Figure 1-1.

除了替换和非替换元素，CSS还有其他两种基本元素类型:块级元素和行内元素。由很多显示类型，但这是最基本的两种，也是大多数(如果不是所有)其他显示类型引用的类型。块级元素和行内元素对于那些在HTML标记和游览器显示上花了时间的作者是熟悉的。这些元素如图1-1所示。

### Block-level elements
Block-level elements generate an element box that (by default) fills its parent element’s content area and cannot have other elements at its sides. In other words, it generates “breaks” before and after the element box. The most familiar block elements from HTML are p and div. Replaced elements can be block-level elements, but usually they are not.

块级元素在父级元素的内容区域中生成了一个元素框（默认情况下），其他的元素不能在块级元素两边。换句话说，在元素框前面和后面生成了“break”。最熟悉的HTML块级元素是p和div。替换元素可以是块级元素，但通常他们不是。

List items are a special case of block-level elements. In addition to behaving in a manner consistent with other block elements, they generate a marker—typically a bullet for unordered lists and a number for ordered lists—that is “attached” to the element box. Except for the presence of this marker, list items are in all other ways identical to other block elements.

列表是一个特殊的块级元素。除了和其他块级元素一样外，他们还生成一个标记，通常是无序列表的符号和有序列表的数字，这个标记会被附加到元素框中。除了这个标记，列表的其他地方都与块级元素相同.

### Inline-level elements

Inline-level elements generate an element box within a line of text and do not break up the flow of that line. The best inline element example is the a element in HTML. Other candidates are strong and em. These elements do not generate a “break” before or after themselves, so they can appear within the content of another element without disrupting its display.

行内元素在一行文本中生成一个元素框,不会打乱这行的流.最好的行内元素例子是HTML中的 a 元素,其次是strong和em元素.这些元素不会在前后生成break,所以他们可以出现在另一个元素的内容中并且不会干扰它的显示.

Note that while the names “block” and “inline” share a great deal in common with block- and inline-level elements in HTML, there is an important difference. In HTML, block-level elements cannot descend from inline-level elements. In CSS, there is no restriction on how display roles can be nested within each other.

注意,虽然块级元素和行内元素有很多共同之处,但有一个很重要的不同点.在HTML中,块级元素不能从行内元素继承.在css中,对于角色之间如何嵌套没有限制.

To see how this works, let’s consider a CSS property, display.

为了了解这是怎么工作的,我们来看看css的display属性.

![!]("DISPLAY.png")
![!]("DISPLAY1.png")

You may have noticed that there are a lot of values, only three of which I’ve even come close to mentioning: block, inline, and list-item. Most of these values will be dealt with elsewhere in the book; for example, grid and inline-grid will be covered in a separate chapter about grid layout, and the table-related values are all covered in a chapter on CSS table layout.

 你已经注意到了这里有许多值,只有三种是我曾经提到过的:block,inline和list-item.大多数值会在本书的其他地方介绍.比如,grid和inline-grid会在网格布局中的单独章节介绍,表格相关的值会在css表格布局中有单独章节介绍.

 For now, let’s just concentrate on block and inline. Consider the following markup:
 现在,我们只关注block和inline,看看下面的标记

 `<body> <p>This is a paragraph with <em>an inline element</em> within it.</p> </body>`

 Here we have two block elements (body and p) and an inline element (em). According to the HTML specification, em can descend from p, but the reverse is not true. Typically, the HTML hierarchy works out so that inlines descend from blocks, but not the other way around.

 上面有两个块级元素(body,p)和一个行内元素(em).根据HTML规定,em可以是p的子元素,但是不能反过来.通常,HTML的层次结构是行内元素是块级元素的子元素,而不是反过来.

CSS, on the other hand, has no such restrictions. You can leave the markup as it is but change the display roles of the two elements like this:

css没有这样的限制,你可以让标记保持原样,然后这样改变两个元素的显示方式:

`p {display: inline;} `
`em {display: block;}`

This causes the elements to generate a block box inside an inline box. This is perfectly legal and violates no part of CSS. You would, however, have a problem if you tried to reverse the nesting of the elements in HTML:

这种方法在行内元素框中生成了块级元素框.这是合法的且没有违反css的任何部分.如果你试图在HTML中反转嵌套元素结构,你会遇到一个问题:

`<em><p>This is a paragraph improperly enclosed by an inline element.</p></em>`

No matter what you do to the display roles via CSS, this is not legal in HTML.

不论你通过css对元素显示做什么操作,这在HTML中都是不合法的.

While changing the display roles of elements can be useful in HTML documents, it becomes downright critical for XML documents. An XML document is unlikely to have any inherent display roles, so it’s up to the author to define them. For example, you might wonder how to lay out the following snippet of XML:
在HTML中修改元素的显示属性很有用,这对于xml文档也很重要.一个xml文档没有默认的显示角色,所以只能作者去定义他们.例如,你可能要想知道如何去对下面的xml文件布局:

```
<book>
 <maintitle>Cascading Style Sheets: The Definitive Guide</maintitle>
  <subtitle>Third Edition</subtitle>
   <author>Eric A. Meyer</author>
    <publisher>O'Reilly and Associates</publisher> 
    <pubdate>November 2006</pubdate> 
    <isbn type="print">978-0-596-52733-4</isbn>
     </book>
      <book>
       <maintitle>CSS Pocket Reference</maintitle> 
       <subtitle>Third Edition</subtitle>
        <author>Eric A. Meyer</author>
         <publisher>O'Reilly and Associates</publisher> 
         <pubdate>October 2007</pubdate>
          <isbn type="print">978-0-596-51505-8</isbn>
     </book>
```

Since the default value of display is inline, the content would be rendered as inline text by default, as illustrated in Figure 1-2. This isn’t a terribly useful display.

因为默认想显示属性时行内,所以默认会显示为内联文本.如图1-2中所示.这不是一个很有用的显示.

![]("DISPLAY.png")

You can define the basics of the layout with display:

你可以用display来定义基本的布局:

`book, maintitle, subtitle, author, isbn {display: block;}`
`publisher, pubdate {display: inline;}`

We’ve now set five of the seven elements to be block and two to be inline. This means each of the block elements will be treated much as div is treated in HTML, and the two inlines will be treated in a manner similar to span.

我们设置了五个元素为块级元素,两个为内联元素.这意味着每个块级元素会被当成HTML中的div一样对待,另外两个内联元素会像span一样被对待.

This fundamental ability to affect display roles makes CSS highly useful in a variety of situations. We could take the preceding rules as a starting point, add a few other styles for greater visual impact, and get the result shown in Figure 1-3.


改变显示角色的能力让css在很多场合都很有用.我们以前面的规则为起点,然后为了更好的视觉效果添加一点其他的样式,最后得到图1-3的显示结果

![!]("1-3.png")

Before learning how to write CSS in detail, we need to look at how one can associate CSS with a document. After all, without tying the two together, there’s no way for the CSS to affect the document. We’ll explore this in an HTML setting since it’s the most familiar.

在学习怎么写css之前,我们需要知道怎么将css和文档链接起来.毕竟,如果没有把两者结合,是没有办法通过css来影响文档.我们会在HTML设置中研究它,因为我们对HTML设置很熟悉.







