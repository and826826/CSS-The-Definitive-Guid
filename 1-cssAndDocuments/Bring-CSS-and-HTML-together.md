# Bringing CSS and HTML Together

I’ve mentioned that HTML documents have an inherent structure, and that’s a point worth repeating. In fact, that’s part of the problem with web pages of old: too many of us forgot that documents are supposed to have an internal structure, which is altogether different than a visual structure. In our rush to create the coolest-looking pages on the web, we bent, warped, and generally ignored the idea that pages should contain information with some structural meaning.

我已经提到过HTML有固有的结构,这是值得重复的点.实际上,有个由于旧网页的问题:我们大都忘记了文档应该有一个内部结构,它与视觉结构完全不同.在我们急于创建web上外观最酷的页面时，我们弯曲、扭曲，并且通常忽略了页面应该包含具有某种结构意义的信息.

That structure is an inherent part of the relationship between HTML and CSS; without it, there couldn’t be a relationship at all. To understand it better, let’s look at an example HTML document and break it down by pieces:

这种结构是HTML和css间的固有部分,没有它,两者根本没有联系.为了更好的理解它,让我们来看一个HTML文档示例,并把它分成几部分.

```
<html>
    <head>
        <title>Eric's World of Waffles</title>
        <meta http-equiv="content-type" content="text/html; charset=utf-8">
        <link rel="stylesheet" type="text/css" href="sheet1.css" media="all">
        <style type="text/css"> 
        /* These are my styles! Yay! */ 
        @import url(sheet2.css); 
        </style>
    </head> 
    <body> 
      <h1>Waffles!</h1> 
      <p style="color: gray;">The most wonderful of all breakfast foods is the waffle—a ridged and cratered slab of home-cooked, fluffy goodness that makes every child's heart soar with joy. And they're so easy to make! Just a simple waffle-maker and some batter, and you're ready for a morning of aromatic ecstasy!
       </p>
    </body>
</html>
```

The result of this markup and the applied styles is shown in Figure 1-4.

最后的结果如图1-4

