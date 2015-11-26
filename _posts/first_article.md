title: Markdown用法说明
date: 2015-11-23 15:29:35
categories: IT
keywords: Markdown,计算机语言,语法
tags: [计算机语言,Markdown,语法]
----
## markdown介绍:

>Markdown是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法，它可以使普通文本内容具有一定的格式。


## markdown快速上手:

#### #一个可以用来调整字体大小的符号:
标题能显示出文章的结构。行首插入1-6个 # ，每增加一个 # 表示更深入层次的内容，对应到标题的深度由 1-6 阶。

<!--more-->


>例如:

>H1 :# Header 1

>H2 :## Header 2

>H3 :### Header 3

>H4 :#### Header 4

>H5 :##### Header 5

>H6 :###### Header 6

#### 显示效果如下:
* # Header1
* ## Header 2
* ### Header 3
* #### Header 4
* ##### Header 5
* ###### Header 6

文本样式:
----
    链接 :[Title](URL)

    加粗 :**Bold**

    斜体字 :*Italics*

    删除线 :~~text~~

    高亮 :==text==

    段落 : 段落之间空一行

    换行符 : 一行结束时输入两个空格

    列表 :* 添加星号成为一个新的列表项。

    引用 :> 引用内容

    内嵌代码 : `alert('Hello World');`

    画水平线 (HR) :--------


-----

图片:
---
    使用Markdown将图像插入文章，你需要在Markdown编辑器输入 ![]() 。 这时在预览面板中会自动创建一个图像上传框。你可以从电脑桌面拖放图片(.png, .gif, .jpg)到上传框, 或者点击图片上传框使用标准的图像上传方式。 如果你想通过链接插入网络上已
    经存在的图片，只要单击图片上传框的左下角的“链接”图标，这时就会呈现图像URL的输入框。想给图片添加一个标题, 你需要做的是将标题文本插图中的方括号。
    
示例使用网络图片:
----
[看原图请点击这里:](http://5.26923.com/download/pic/000/282/37a5d7166255a9d5e5b635573edaf266.jpg)
![](http://5.26923.com/download/pic/000/282/37a5d7166255a9d5e5b635573edaf266.jpg)

[看原图请点击这里:](http://img1.qunarzz.com/sight/p0/1507/34/99284125616a46680abef2ec0748b7bc.water.jpg_710x360_d3d20b76.jpg)
![](http://img1.qunarzz.com/sight/p0/1507/34/99284125616a46680abef2ec0748b7bc.water.jpg_710x360_d3d20b76.jpg)

脚注:
-----
    使用这样的占位符号可以将脚注添加到文本中:[^1]. 另外，你可以使用“n”而不是数字的[^n]所以你可以不必担心使用哪个号码。在您的文章的结尾，你可以如下图所示定义匹配的注脚，URL将变成链接:
	[^1]: This is my first page
	[^n]: Visit http://easytobegin.com
	[^n]: A final page

写代码:
------
>添加内嵌代码可以使用一对回勾号 `adlert('Hello World')`.对于插入代码, Ghost支持标准的Markdown代码和GitHub Flavored Markdown (GFM)[3]  。标准Markdown基于缩进代码行或者4个空格位:

#### 例子:
#### 嵌入链接:
>This is a paragraph that contains a [minisheep的主页](http://easytobegin.com)

#### 列表格式:
>This paragraph contains a list of items.

* Item 1

* Item 2

* Item three

#### 使用Markdown引用文本:

This paragraph has a quote

> That is pulled out like this from the text my post.

编辑器
--------

####常用的Markdown编辑器：

* OSX
* Byword
* Mou
* MacDown

* Linux
* ReText
* UberWriter

* Windows
* MarkdownPad
* Mou

* ios
* Byword

* 浏览器插件
* MaDO(Chrome)

* 高级应用
* Subline Text 2 + MarkdownEditing / 教程


