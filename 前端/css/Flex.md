# Flex布局

> flex是Flexible Box缩写，意为“弹性布局”，为盒状布局提供最大的灵活性。

webkit内核的浏览器，必须加上**-webkit**前缀

```
 .box{
    display: -webkit-flex; /* Safari */
    display: flex;
 }
```

> 采用flex布局的元素，称为Flex容器（flex container）,简称“容器”，所有子元素自动成为容器的成员。容器默认存在两根轴，一根水平主轴（**main axis**）和垂直的交叉轴（**cross axis**）。主轴的开始位置（与边框的交叉点）叫做**main start** ,结束位置叫做**main end**,交叉轴的开始位置叫做**cross start**,结束位置叫做**cross end**,容器内元素默认沿主轴排列，单个元素占据的主轴空间叫做**mian size**,占据的交叉轴空间叫做**cross size**



> 容器的属性

------

- flex-direction  决定主轴的方向 

  `flex-direction:row | row-reverse | column | column-reverse;` 

  ![](E:\github\studyNotes\assets\img\css\0001.png)

  

-  flex-wrap 主轴铺满一行换行展示

  `flex-wrap: nowrap | wrap | wrap-reverse;`

  1.nowrap 不换行

  2.wrap 换行，由上至下加行

  3.wrap-reverse 换行，由下至上换行

-  flex-flow  flex-direction和flex-wrap属性的简写

  `flex-flow: <flex-direction> || <flex-wrap>;`

-  justify-content 主轴上对齐方式

  `justify-content: flex-start | flex-end | center | space-between | space-around;`

-  align-items 交叉轴对齐方式

  `align-items: flex-start | flex-end | center | baseline | stretch;`

-  align-content  定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用

  `align-content: flex-start | flex-end | center | space-between | space-around | stretch;`

> flex容器内元素的6个属性

- order  定义元素的排列顺序。数值越小，排列越靠前，默认为0
- flex-grow  定义元素的放大比例，默认为`0`，即如果存在剩余空间，也不放大。 
- flex-shrink  定义了元素的缩小比例，默认为1，即如果空间不足，该项目将缩小。 
- flex-basis  定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小。 
- flex  属性是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选。 
- align-self  允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性 