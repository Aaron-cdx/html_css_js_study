# CSS3 学习

> CSS3 学习,直面恐惧,战胜自己！2021-11-28 深圳

## CSS 简介

网页分为三个部分：

- 结构(HTML)
- 表现(CSS)
- 行为(JavaScript)

层叠样式表: 网页实际上是一个多层的结构，可以通过 CSS 分别为网页的每一层设置样式，而最终我们能看到的只是网页的最上边的一层。

CSS 是用来设置网页中元素中的样式

内联样式，行内样式，在标签内通过 style 属性来设置元素的样式。
使用内联样式只能对一个标签生效，如果希望影响到多个元素，必须在每一个元素中都复制一遍。并且当样式发生变化时，我们必须要一个一个的修改，非常的不方便。**注意在开发中绝对不要使用内联样式！**

```html
<p style="color: red; font-size: 20px;">我们是新时代共产主义接班人！</p>
```

内部样式: 将样式写在 header 中的 style 标签中，然后通过 css 的选择器来选中元素并为其设置各种样式，可以同时为多个标签设置样式，并且修改时只需要修改移除即可。

内部样式表只能对一个网页起作用，但里面的样式不能够跨页面复用。

```html
<style>
  p {
    color: red;
    font-size: 60px;
  }
</style>
```

外部样式表，用一个 css 文件，然后在网页中通过 link 来引用当前 css 文件，即可生效。意味着需要使用当前样式的网页都可以对其进行引用，使样式可以在不通过的页面之间进行复用操作。将样式编写到外部的 CSS 文件中，可以使用浏览器的缓存机制，从而加快网页的加载速度，提高用户的体验。

```html
<link rel="stylesheet" href="./01_css.css" />
```

## CSS 基本语法

CSS 基本语法，CSS 的基本语法包括选择器和声明块。

- 选择器: 通过选择器可以选中页面中的指定元素，比如 p 元素，可以选择中页面中所有的 p 标签元素
- 声明块: 通过声明块来指定需要为元素设置的样式。声明块由一个一个的声明组成，声明是一个键值对结构，一个样式名对应一个样式值，名和值之间以:连接，以;结尾。

## 常用选择器

- 元素选择器: 根据标签名来选中指定的元素
  > 语法: 标签名{} 例如: p{}/h1{}
- id 选择器: 根据 id 属性值选定指定的元素
  > 语法: #id 属性值{}, 例如: #box{}/#red{}
- 类选择器: 根据 class 来选择一组元素，可以同时对一个元素指定多个 class 名称(使用空格隔开即可)
  > 语法: .class 属性值
- 通配选择器: 选择页面中的所有元素
  > 语法: \*

## 复合选择器

- 交集选择器: 选中同时复合多个条件的元素
  > 语法: 选择器 1 选择器 2 选择器 3 选择器 n{},注意交集选择器中如果有元素选择，必须使用元素选择器开头。
- 并集选择器: 同时选择多个选择器对应的元素
  > 语法: 选择器 1,选择器 2,选择器 3,...,选择器 n{}

## 关系选择器

- 父元素: 直接包含子元素的元素叫做父元素
- 子元素: 直接被父元素包含的元素是子元素
- 祖先元素: 直接或间接包含后代的元素叫做祖先元素
- 后代元素: 直接或间接被祖先元素包含的元素叫做后代元素
- 兄弟元素: 拥有相同父元素的元素叫做兄弟元素

* 子元素选择器: 选中指定元素的指定子元素
  > 语法: 父元素 \> 子元素

```css
div > span {
  color: green;
}
```

- 后代元素选择器: 选中指定元素内的指定后代元素
  > 语法: 祖先 后代

```css
div span {
  color: red;
}
```

- 兄弟选择器: 选择下一个兄弟选择器
  > 语法: 前一个+下一个; 如果是选择下边所有的元素: 前一个 ~ 下一个

```css
p + span {
  color: blue;
}

p ~ span {
  color: orange;
}
```

## 属性选择器

属性选择器旨在选择标签内属性
语法:

> \[属性名\] 选择含有属性的元素
> \[属性名=属性值\] 选择含有指定属性和属性值的元素
> \[属性名^=属性值\] 选择属性值以指定值开头的元素
> \[属性名$=属性值\] 选择属性值以指定值结尾的元素
> \[属性名\*=属性值\] 选择属性值中含有某值的元素的元素

## 伪类选择器

伪类: 不存在的类，特殊的类，比如第一个子元素、被点击的元素、鼠标移入的元素。

伪类一般情况下使用`:`开头

- `:first-child`: 表示第一个子元素
- `:last-child`: 表示最后一个子元素
- `:nth-child(1)`: 表示选中第 n 个子元素,如果直接写 n 的话，则会选中所有的子元素，2n 表示选中偶数位置的元素(even 也可)，2n+1 表示奇数位元素(odd 也可)

以上的伪类都是根据所有的子元素进行排序的。

- `:first-of-type`
- `:last-of-type`
- `:nth-of-type`
  这些伪类的功能和上述的类似，只是这些是在类型元素中进行排序

* `:not()`: 否定伪类，将符合条件的元素从选择器中去除

## 超链接的伪类

- 没有访问过的状态
- 访问过的链接状态

`:link`: 用来表示没有访问过的链接(正常的链接)

`:visited`: 用来表示访问过的链接

因为隐私的原因，所以 visited 的伪类只能修改链接的颜色。

`:hover`: 表示鼠标移入的状态

`:active`: 用来表示鼠标点击

```html
<style>
  a:link {
    color: brown;
  }
  a:visited {
    color: aqua;
  }
  a:hover {
    font-size: 40px;
    color: greenyellow;
  }
  a:active {
    font-size: large;
    color: blueviolet;
  }
</style>
```

## 伪元素选择器

伪元素: 表示页面中一些特殊的并不真实存在的元素(特殊的位置),伪元素使用`::`开头。

`::first-letter`: 表示第一个字母

`::first-line`: 表示第一行

`::selection`: 表示选中的内容

`::before`: 表示元素的开始

`::after`: 表示元素的最后

before 和 after 必须结合 content 属性来使用，而且 before 和 after 在开发中使用比较频繁。

```css
p::first-letter {
  font-size: larger;
}
p::selection {
  background-color: greenyellow;
}
span::before {
  content: "(";
}
span::after {
  content: ")";
}
```

## 继承

样式的继承，为一个元素设置样式的同时也会应用到它的后代元素上。继承是发生在祖先与后代之间的。

继承的设计是为了方便我们的开发，利用继承我们可以将一些通用的样式统一设置到共同的祖先元素上，这样我们只需要设置一次即可让所有的元素都具有该样式。

注: 并不是所有的样式都会被继承，比如背景相关的、布局相关等这些样式都不会被继承。

没有设置背景色的话，默认的背景色是 transparent(透明)。

文档中元素是否会被继承的话，有一个字段`inherited`会表示是否可以继承。

## 选择器的权重

样式的冲突，当我们使用不同的选择器，选中相同的元素，并且为相同的样式设置不同的值的时候，就会发生样式的冲突。

发生样式冲突的时候，应该使用哪个样式由选择器的权重(优先级)决定。

选择器的权重

- 内联样式 1000
- id 选择器 100
- 类和伪类选择器 10
- 元素选择器 1
- 通配选择器 0
- 继承的样式 无优先级

比较优先级的时候，需要将所有的选择器的优先级进行相加计算，最后优先级越高，则越优先显示。(分组选择器是单独计算的, `div,p,span{}`)，选择器的累加不会超过其最大的数量级，类选择器再高也不会超过 id 选择器(**相加是不可以跨数量级**)。

如果优先级计算后相等，则优先使用靠下的样式。

可以在某一个样式后边添加`!important`，此时此样式会获取到最高的优先级，甚至超过内联样式，但注意，在开发中，important 需要慎用，js 无法操作。

## 单位

长度单位

- 像素: 屏幕(显示器)实际上是由一个一个的小点构成的。不同的屏幕像素大小是不同的，像素越大的屏幕显示的效果越清晰，所以同样的 200px 在不同的设备下显示效果是不一样的。
- 百分比: 百分比可以设置属性相对父元素的属性的百分比，设置百分比可以使子元素跟随父元素的改变而改变。
- em: 相对于元素的字体大小来计算的。1em = 1font-size, em 会跟随字体大小的改变而变化。
- rem: rem 是相对于根元素的字体大小来计算的。

## 颜色单位

颜色单位，在 css 中可以直接使用颜色名字来设置各种颜色，比如: red/orange/yellow/blue/green，但直接使用颜色名字非常不方便。

主要使用颜色的方式是采用 RGB 值，主要是通过三种颜色的不同浓度来调配处不同的颜色。R red/G green/B blue。每一种颜色的范围在 0~255 之间(0%~100%之间)

用法: RGB(红色,绿色,蓝色)

RGBA 值，最后一个值表示透明度，1 表示完全不透明，0 表示完全透明，5 表示半透明。

十六进制 RGB 值，语法: #红色绿色蓝色，颜色浓度通过 00-ff，如果颜色两位重复，可以简写，例如: #aabbcc => #abc

HSL 值，HSLA 值

- H 表示色相: 取值大小 0-360
- S 表示饱和度: 表示颜色浓度，取值大小 0-100%
- L 表示亮度: 表示颜色亮度，取值大小 0-100%

## 布局(layout)-文档流

文档流(normal flow)
网页是一个多层的结构，一层累着一层，通过 CSS 可以为每一层来设置样式，作为用户来讲只能看到最顶上一层。这些曾中，最底下的一层是文档流，文档流是网页的基础，我们所创建的元素默认都是在文档流中进行排列。

对于我们来说，元素主要有两个状态

- 在文档流中
- 不在文档流(脱离文档流)

元素在文档流中的特点:

- 块元素(例如 div)
  - 块元素会在页面中独占一行
  - 默认宽度是父元素的全部(会把父元素撑满)
  - 默认高度是被内容撑开(子元素)
- 行内元素(例如 span)
  - 行内元素不会在页面中独占一行，只占自身的大小
  - 行内元素在页面中自左向右水平排列，如果一行之中不能容纳下所有的行内元素，则元素会换到第二行继续自左向右排列
  - 行内元素的默认高度和高度都是被内容撑开的(即样式可以改变具体的大小)

## 盒子模型

盒模型、盒子模型、框模型(box model)

CSS 将页面中的所有元素都设置为了一个矩形的盒子。将元素设置为矩形的盒子后，对页面的布局就变成了对不同的盒子摆放到不同的位置。

每一个盒子都由以下几个部分组成：

- 内容区(content)
- 内边距(padding)
- 边框(border)
- 外边距(margin)

width 和 height 是设置内容区的大小，元素中的所有的资源苏和文本内容都在内容区中排列，内容区的大小由 width 和 height 两个属性来设置。

边框 border，边框属于盒子边缘，边框里边属于盒子内部，除了边框都是盒子的外部，边框的大小也会影响到整个盒子的大小，要设置边框，至少需要设置三个样式：

- 边框的宽度: border-width
- 边框的颜色: border-color
- 边框的样式: borders-style

```css
.box1 {
  width: 200px;
  height: 200px;
  background-color: #bfa;
  /* border设置三要素，border-width/border-color/border-style */
  /* 
    border-width有默认值，一般是3个像素 
    border-width可以用来指定四个方向的边框的宽度，
      四个值: 上右下左
      三个值: 上 左右 下
      两个值: 上下 左右
      一个值: 上下左右
    border-width还可以使用border-xxx-width，xxx值表示top/right/bottom/left,可以实现精准指定各个方向的边框宽度
  */
  border-width: 20px;
  /* border-color也可以四个方向使用颜色，与width的方向一致，border-color可以省略不写，如果省略了则自动使用color的颜色值 */
  border-color: black;
  /* 
    border-style指定边框的样式 
    solid: 表示实线
    dotted: 点状虚线
    double: 双线
  */
  border-style: solid;
  /* 
    border简写属性，通过该属性可以同时设置边框所有相关样式，并且没有顺序要求
    除了border以外还有四个border-xxx
    border-top
    border-right
    border-bottom
    border-left
  */
}
```

### 盒子模型-内边距

内边距(padding)，内容区和边框之间的距离是内边距，一共有四个方向的内边距。

- padding-top
- padding-right
- padding-bottom
- padding-left

内边距的设置会影响到盒子的大小，背景颜色会延升到内边距上。

盒子的可见框的大小，由内容区、内边距和边框共同决定。所以在计算盒子大小的时候，需要将这三个区域加到一起进行计算。

padding 的内边距也可以实现简写属性，可以同时指定四个方向的内边距。规则和 border-width 一样。

### 盒子模型-外边距

外边距(margin)，外边距不会影响到盒子可见框的大小，但是外边距会影响盒子的位置，一共有四个方向的外边距：

- margin-top: 上外边距，设置一个正值，盒子会向下移动
- margin-right: 右边距，设置正值，盒子会向左移动
- margin-bottom:
- margin-left: 左外边距，设置一个正值，盒子会向右移动

元素在页面中是按照自左向右的顺序排列的，所以默认情况下如果我们设置的左和上外边距则会移动元素自身而设置下和右外边距则会移动其他元素。

margin 的接卸属性，可以设置四个方向的外边距，用法与 padding 相同。

margin 会影响到盒子实际的占用空间

### 盒子模型-水平方向的元素布局

元素在水平方向的布局，元素在其父元素中水平方向的位置由一下几个属性共同决定:

- margin-left
- border-left
- padding-left
- width
- padding-right
- border-right
- margin-right

margin-left+border-left+padding-left+width+padding-right+border-right+margin-right = 其父元素内容区的宽度(必须满足)

如果等式不满足，则称为过渡约束，则等式会自动调整，调整的情况，如果这七个值中没有 auto 的情况，**则浏览器会自动调整 margin-right 值使得等式满足**。

这七个值中有三个值可以设置为 auto

- width
- margin-left
- margin-right

如果某个值设置为 auto，则会自动调整为 auto 的那个值以使等式成立。

- 如果将一个宽度和一个外边距设置为 auto，则宽度会调整到最大，设置为 auto 的外边距会自动为 0.
- 如果将三个值都设置为 auto，则外边距都是 0，宽度最大
- 如果将两个外边距设置为 auto，宽度固定值，则会在外边距设置为相同的值。

所以我们经常使用这个特点来使得元素居中

```css
width: 20px
margin: 0 auto
```

### 盒子模型-垂直方向的布局

垂直布局往往比较简单，没有水平布局那么麻烦。

子元素在父元素的内容区中排列的，如果子元素超过了父元素，则子元素会从父元素中溢出，使用 overflow 属性来设置父元素处理溢出的子元素方式，可选值:

- visible: 默认值，子元素会从父元素中溢出，在父元素外部的位置展示
- hidden: 溢出内容会被裁剪不会展示
- scroll: 生成两个滚动条，通过滚动条来查看完整的内容
- auto: 根据需要生成滚动条

overflow-x 和 overflow-y 分别用来处理水平方向和垂直方向的移除的问题。

### 盒子模型-外边距的折叠

垂直外边距的折叠，相邻的垂直方向外边距会发生重叠现象，

- 兄弟元素间的相邻垂直外边距取两者之间较大值
- 特殊情况，如果相邻的外边距一正一负，则取两者的和
- 如果相邻的外边距都是负值，则取两者之间的绝对值较大的
- 兄弟元素之间的外边距的重叠，对于开发是有利的，所以不需要对其进行处理

父子元素

- 父子元素间的相邻外边距，子元素的会传递给父元素(上外边距)
- 父子外边距的折叠会影响到页面的布局，必须要进行处理
  - 解决方案要么不用外边距，可以使用 padding-top
  - 两者不相邻，可以使用 boder-top 来把父元素的外边距与子元素隔开

## 行内元素的盒子模型

行内元素的盒模型

- **<font color="red">行内元素不支持设置宽度和高度</font>**
- 行内元素可以设置 padding，但是垂直方向 padding 不会影响页面的布局
- 行内元素可以设置 border， 垂直方向的 border 不会影响页面的布局
- 行内元素可以设置 margin，垂直方向的 margin 不会影响布局

display 用来设置元素显示的类型

- inline: 将元素设置为行内元素
- block: 将元素设置为块元素
- inline-block: 将元素设置为行内块元素
  - 行内块元素的特点是既可以设置宽度和高度，又不会独占一行(即两个一样的元素不会分成两行，而是会并行显示)
- none: 元素不在页面中显示(隐藏元素)，隐藏之后不会有位置占据

visibility 用来设置元素的显示状态

- visible: 默认值，元素在元素中正常显示
- hidden: 元素在页面中隐藏，不显示，但是会占据页面的位置

## 浏览器的默认样式

默认样式，通常情况下， 浏览器都会为元素设置一些默认样式，默认样式的存在会影响到页面的布局。通常情况下编写网页时必须要去除浏览器的默认样式(PC 端的页面)。

去除 ul 的项目符号`list-style: none;`

```css
/* 去除所有的默认样式 */
* {
  margin: 0;
  padding: 0;
}
```

可以使用`reset.css`或者`normalize.css`来处理具体的样式，以达到去除浏览器默认样式的作用。

```css
/* 要想让一个元素在父元素中处置居中，只需要将父元素的line-height设置为高度相同即可 */
line-height: 25px;
```

## 盒子的大小

默认情况下，盒子可见框的大小由内容区、内边距和边框共同决定。
box-sizing 用来设置盒子尺寸的计算方式(设置 width 和 height 的作用)

可选值：

- context-box: 默认值，宽度和高度用来设置内容区的大小
- border-box: 宽度和高度用来设置整个盒子可见框的大小

width 和 height 指的是内容区和内边距和边框的总大小。

## 轮廓阴影和圆角

outline 用来设置元素的轮廓线，用法和 border 一样。

轮廓和边框的区别在于轮廓不会影响到可见框的大小

```css
outline: 10px red solid;
```

box-shadow: 用来设置元素的阴影效果，阴影不会影响页面布局。

```css
box-shadow: 10px 10px 10px orange;
```

- 第一个值: 水平偏移量，设置阴影的水平位置，正值向右移动，负值向左移动，类似 margin-left
- 第二个值: 垂直偏移量，设置阴影的垂直位置，正值向下移动，负值向上移动，类比 margin-top
- 第三个值: 阴影的模糊半径
- 第四个值: 阴影的颜色

border-radius 用来设置圆角，用来设置圆的半径大小。
有四个单独设置四个方向的圆角

- border-top-left-radius
- border-top-right-radius
- border-bottom-left-radius
- border-bottom-right-raius

border-radius 可以直接设置四个方向的圆角

- 四个值: 左上，右上，右下，左上
- 三个值: 左上，右上/左下，右下
- 两个值: 左上/右下，右上/左下

```css
/* 设置横向和纵向的圆角, 用/做具体的区分 */
border-radius: 20px / 40px;

/* 将元素设置为一个圆形 */
border-radius: 50%;
```

# 浮动

## 浮动的简介

通过浮动可以使一个元素向其父元素的左侧或者右侧移动，可以使用 float 属性来设置元素的浮动。

可选值：

- none: 默认值，元素不浮动
- left: 元素向左浮动
- right: 元素向右浮动

元素设置浮动以后，水平布局的等式便不需要强制成立。

元素设置浮动以后，会完全从文档流中脱离，不在占用文档流的位置，所以元素下边的还在文档流中的元素会自动向上移动。

浮动的特点

- 浮动的元素会完全脱离文档流，不再占据文档流中的位置
- 设置浮动以后元素会向父元素的左侧或者右侧移动
- 浮动元素默认不会从父元素中移出
- 浮动元素向左或者向右移动时，不会超过它前边的其他浮动元素
- 如果浮动元素的上面是一个没有浮动的块元素，则浮动元素无法上移
- 浮动元素不会越过自己前面浮动的兄弟元素，最多就是和他一样高

浮动主要的功能就是让页面中的元素水平布局

## 浮动的特点

浮动元素不会盖住文字，文字会自动环绕在浮动元素的周围，所以我们可以利用浮动来说设置文字环绕图片的效果。

元素设置浮动之后，会从文档流中脱离，从文档流中脱离以后，元素的一些特点也会发生变化。

脱离文档流以后的特点：

- 块元素不再独占一行
- 脱离文档流以后，块元素的宽度和高度默认被内容撑开

行内元素脱离文档流以后会变成块元素

脱离文档流以后，不需要再区分块和行内元素

## 高度塌陷和 BFC

高度塌陷的问题: 在浮动布局中，父元素的高度默认是被子元素撑开的，当子元素浮动后，其完全脱离文档流，子元素从文档流中脱离，将会无法撑起父元素的告诉，导致父元素的高度丢失。

父元素高度丢失以后，其下的元素会自动上移，导致页面的布局混乱，所以高度塌陷问题是浮动布局中比较常见的一个问题，这个问题我们必须要处理。

解决方案，通过 BFC(Block Formatting Context)块级格式化环境来解决。BFC 是一个 CSS 中的一个隐含的属性，可以为一个元素开启 BFC，开启 BFC 该元素会变成一个独立的布局环境。

开启 BFC 的特点：

- 开启 BFC 的元素不会被浮动元素所覆盖
- 开启 BFC 的元素子元素和父元素外边距不会重叠
- 开启 BFC 的元素可以包含浮动的子元素

可以通过一些特殊的方式来开启元素的 BFC:

- 设置元素的浮动(不推荐)
- 将元素设置为行内块元素展示(不推荐)
- 将元素的 overflow 设置为一个非 visible 的值即可

## clear

开启了 BFC 的元素会脱离文档流，会导致其他元素的位置上移动。

如果我们不希望某个元素因为其他元素的浮动的影响而改变位置，可以通过 clear 属性来清除浮动元素对当前元素所产生的影响。

clear:

- 作用: 清除浮动元素对当前元素所产生的影响
- 可选值:
  - left: 清除左侧浮动元素对当前元素的影响
  - right: 清除右侧浮动元素对当前元素的影响
  - both: 清除两侧中最大影响的那一侧

原理:设置清除浮动以后，浏览器会自动为元素添加一个上外边距，以使得其不受其他元素的影响。

## clearfix

外边距重叠问题，可以使用`display: table;`来隔开两个块元素，而不占用任何的空间。

clearfix 可以同时解决高度塌陷和外边距重叠问题，当遇到这些问题的时候，可以直接使用 clearfix 解决这些问题。

## position

定位是一种更加高级的布局手段，通过定位可以将元素摆放到页面的任意位置。使用 position 属性来设置定位。

可选值：

- static:默认值，元素是静止的，没有开启定位。
- relative:开启元素的相对定位
- absolute:开启元素的绝对定位
- fixed:开启元素的固定定位
- sticky:开启元素的粘滞定位

relative:当元素的 position 属性值设置为 relative 时则开启了元素的相对定位。

特点:

- 元素**开启相对定位**后，如果不设置偏移量元素不会发生任何的实质性变化。
  - 偏移量:offset
  - top:上下位置
  - bottom:上下位置
  - right/left:左右元素
- 相对定位是参照于元素在文档流中的位置进行定位的
- 相对定位会提升元素的层级
- 相对定位不会使元素脱离文档流，行内元素还是行内元素

absolute：当元素的 position 属性值设置了 absolute 时则开启了元素的绝对定位。

特点：

- 开启绝对定位后，如果不设置偏量元素的位置不会发生变化
- 开启绝对定位后，元素会从文档流中脱离
- 绝对定位会改变元素的性质，行内变成块，块的宽高会被内容撑开
- 绝对定位会使元素提升一个层级
- 绝对定位元素是相对其包含块进行定位的

包含块(containing block)，正常情况下，包含块就是离当前元素最近的祖先块元素。

绝对定位的包含块，就是离它最近的开启了定位的祖先元素。如果所有的祖先元素都没有开启定位则根元素就是它的包含块。根元素就是初始包含块。

fixed:当元素的 position 属性设置了 fixed 时则开启了元素的固定定位。固定定位的大部分特性都和绝对定位一样。

唯一不同的是，**固定定位永远参照浏览器的视口进行定位**。固定定位不会随着网页的滚动条进行滚动。

sticky:当元素的 positioin 属性设置了 sticky 时，表示开启了元素的粘滞定位。

特点:

- 粘滞定位和相对定位的特点基本一致，但粘滞定位可以在元素到达某个位置的时候将其固定

当我们开启了决定给定位以后，水平方向的布局等式就需要添加 left 和 right 两个值。此时规则和之前一样高，只是多了两个值。当发生过度约束，如果 9 个值中没有 auto，则自动调整 auto 的值以使得等式满足。

可设置 auto 的值，margin width left right.

因为 left 和 right 的值默认是 auto，所以如果不知道 left 和 right 则等式不满足时，会自动调整这两个值。

可以设置`margin-left:auto;margin-right:auto;margin-top:auto;margin-bottom:auto`这里的就是水平垂直双居中。

## 元素的层级

对于开启了定位元素，可以通过 z-index 属性来指定元素的层级，z-index 需要一个整数作为参数，值越大元素的层级越高，元素的层级越高则越优先显示。

如果元素的层级一样，则优先显示靠下的元素。

祖先元素的层级再高也不会盖住后代元素。
