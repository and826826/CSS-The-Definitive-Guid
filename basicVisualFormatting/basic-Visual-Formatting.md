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

## A Quick Refresher
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




