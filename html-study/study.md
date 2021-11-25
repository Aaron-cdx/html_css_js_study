# html+css学习
> 直面自己最害怕的事情，将会促进自己不断成长！2021-11-23 深圳
## 文档的使用
doctype用于文档声明，声明当前网页的版本
```html
<!doctype html>
```

head是网页的头部，head中的内容不会在网页中直接出现，主要是用来帮助浏览器或者搜索引擎来解析网页。

mata标签用来设置网页的元数据，下面的html代码片段主要用来设置网页的字符集，避免出现乱码问题
```html
<meta charset="utf-8">
```

title中的内容会显示在浏览器的标题栏，搜索引擎主要根据title中的内容来判断网页的主要内容

body是html的子元素，表示网页的主体，网页中所有的可见内容都应该写在body中。

利用w3c school对html的相关标签tag和属性进行具体的熟悉

## 实体
如果需要在网页中展示一些特殊的符号，则需要使用html中的实体(转义字符)
实体的名字:
空格: `&nbsp;`
小于号: `&lt;`
大于号: `&gt;`

具体的话可以参考html文档获取想要插入的实体的具体的展示！

## meta标签
meta标签主要用于设置网页中的一些元数据，元数据不是给用户的
* charset用于指定网页的字符集
* name指示数据的名称
* content指定数据的内容

keywords表示网站的关键字，可以同时指定多个关键字，使用逗号分隔开
description表示网站的描述
title标签内容会作为搜索结果的超链接上的文字显示
以下实例是B站首页看到的一些meta元数据的信息
```html
<meta name="description" content="bilibili是国内知名的视频弹幕网站，这里有及时的动漫新番，活跃的ACG氛围，有创意的Up主。大家可以在这里找到许多欢乐。">
<meta name="keywords" content="Bilibili,哔哩哔哩,哔哩哔哩动画,哔哩哔哩弹幕网,弹幕视频,B站,弹幕,字幕,AMV,MAD,MTV,ANIME,动漫,动漫音乐,游戏,游戏解说,二次元,游戏视频,ACG,galgame,动画,番组,新番,初音,洛天依,vocaloid,日本动漫,国产动漫,手机游戏,网络游戏,电子竞技,ACG燃曲,ACG神曲,追新番,新番动漫,新番吐槽,巡音,镜音双子,千本樱,初音MIKU,舞蹈MMD,MIKUMIKUDANCE,洛天依原创曲,洛天依翻唱曲,洛天依投食歌,洛天依MMD,vocaloid家族,OST,BGM,动漫歌曲,日本动漫音乐,宫崎骏动漫音乐,动漫音乐推荐,燃系mad,治愈系mad,MAD MOVIE,MAD高燃">
<meta name="renderer" content="webkit">
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta name="spm_prefix" content="333.851">
```
下面的示例表示网页的定时跳转
```html
<meta http-euqiv="refresh" content="3,url=https://www.baidu.com/">
```
## 语义化标签
语义化标签是专门用来负责网页的结构，所以在使用html标签的时候，应该关注的是标签的语义，而不是标签的样式

标题标签h1~h6逐渐变得不重要，一般用h1~h3，h4~h6很少使用
可以使用hgroup把来为标签分组，可以将一组相关的标题同时放入到hgroup
```html
 <hgroup>
     <h1>h1标签</h1>
     <h2>h2标签</h2>
 </hgroup>
```
em标签表示语调的强调
strong标签表示强调，重要内容
blockquote表示一个长引用，q表示一个短引用，br表示标签页面的换行

## 块和行内元素
块元素(block element)在网页中一般通过块元素来对页面进行布局操作
行内元素(inline element)一般用来包裹文字

一般会在块元素中放行内元素，而不会在行内元素中放块元素
块元素中基本什么都可以放，**p元素中不能放任何的元素**

浏览器在解析网页的时候，会自动对网页中的不符合规范的内容进行修正操作
比如：
* 标签写在了根元素的外部
* p元素中嵌套了块元素
* 根元素中出现了除head和body以外的子元素

