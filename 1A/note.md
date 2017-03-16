# 学习笔记：Building Layouts: Part 1


## 关键词

- Layout

    >  "An Android layout defines everything the user can see and touch. A layout is made up of View (like buttons and text) and ViewGroup (like lists, tables, or more Views) objects, all combined to make a View Hierarchy" (http://stackoverflow.com/tags/android-layout/info)
    > 
    >   安卓Layout定义了用户（在屏幕上）可以看见和触摸的一切。layout由View（如button和text）和ViewGroup（list，table或更多的view）组成，共同合并成为一个视图层次结构。
     
- User Interface

    > "The user interface (UI), in the industrial design field of human–computer interaction, is the space where interactions between humans and machines occur."(https://en.wikipedia.org/wiki/User_interface)
    >  
    > 在人机交互的工业设计中，用户界面是产生人机互动的空间。
    
- TextView
    - 安卓Layout中的基本类型之一，提供在屏幕上渲染文本的功能
- ImageView
    - 安卓Layout中的基本类型之一，提供在屏幕上渲染图像的功能 
- Button
    - 安卓Layout中的基本类型之一，提供在屏幕上绘制按钮的功能
- Camel case

    > "Camel case (stylized as camelCase or CamelCase; also known as camel caps or more formally as medial capitals) is the practice of writing compound words or phrases such that each word or abbreviation in the middle of the phrase begins with a capital letter, with no intervening spaces or punctuation. (https://en.wikipedia.org/wiki/Camel_case)
    > 
    > 骆驼命名法是将复合词和短语中各单词或短语中的缩写大写首字母并不带空格或符号的做法。


&nbsp;
## View

![image](https://github.com/mark818/google_study_jams/raw/master/1A/1A-1.png)

安卓提供的内置View类型有很多，[速查表](https://static0.studyjamscn.com/content/Android%E5%B8%B8%E8%A7%81Views%E9%80%9F%E6%9F%A5%E8%A1%A8.pdf) 中列出了常用的View。

本章中详细描述了TextView和ImageView。在学习使用它们之前，首先需要了解xml的语法。

### XML

XML全称[Extensible Markup Language](https://en.wikipedia.org/wiki/XML)，由于其通用简单的语法，在网页、数据库和UI中广泛使用，作为对象描述和数据绑定的描述语言。

本章涉及的XML元素主要有**Tag**, **Element**, 以及**Attribute**。

- Tag是XML中的最小单位。 一个Tag包括opening tag和closing tag，他们的名字必须一致。如    ```<abc></abc>```。其中```abc```为Tag名，```<abc>```为opening tag，```</abc>```为closing tag。

- 一对opening tag和closing tag定义了一个Element。opening tag和closing tag之间可以加入内容，作为该element的数据，如
```<type>Some Content</type>```
 定义了type element，带有数据```Some Content```。值得注意的是element可以嵌套另一个element，如
```	
<parent>
	<child1></child1>
    <child2>
        <grandchild></grandchild>
    </child>
</parent>
```
上述代码中parent element嵌套了child1和child2 element，其中child2又嵌套了grandchild element。由于markdown不支持代码段缩进，看起来不够直观。通常每次嵌套会加入4个空格或一个tab作为缩进。如果一个Element没有数据，则称之为empty-element tag，同时可以简写为
```<type />```

- 每个Element都可以在opening tag中定义自己的Attribute，如
``` <type attr1="1" attr2="2"></type>```
中定义了type element的两个Attribute。每个Attribute的定义写为```属性名=“值”```。注意值需要包括在双引号里。

这里介绍了很多概念和细节，没有理解没关系，回到TextView和ImageView看看具体例子。

### TextView

```
<TextView
 android:id="@+id/title_text_view"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:text="@string/my_photos"
 android:textAppearance="?android:textAppearanceLarge"
 android:textColor="#4689C8"
 android:textStyle="bold" />
```

 这个是教程中TextView的定义。tag名字为TextView，定义了7种属性，其中id为View名，layout_width和layout_height定义了View在屏幕上的长宽，text定义在屏幕上显示的内容，textAppearance定义了字体的样式，textColor定义了字体的颜色，textStyle进一步定义字体的样式。

教程中着重介绍了如下几个属性：

- background
	- 这个属性定义了View的背景色。背景色通常用一个6个16进制数字表示一个RGB值，如```#000000```表示黑色，```#FFFFFF```表示白色。安卓提供了一些常用的颜色，我们可以方便地用单词引用它们，如```android:color/white```
- layout_width, layout_height
    - 这两个属性定义了这个View在安卓设备屏幕上所占的大小。定义的值可以使用数值和常数。数值可以使用百分比，px（pixel像素）和dp (density pixel)。由于不同设备屏幕大小和像素数都不同，教程推荐使用dp。dp总是假设一个160dpi (dots per inch每英寸像素点) 的屏幕，并在运行时将尺寸按比例缩放到具体屏幕上，达到在不同屏幕上实现同样比例的效果。常数包括```wrap_content```根据内容自动调整尺寸，```match_parent```匹配上层element的大小，等等。
- textSize
	- 这个属性和上述属性类似，不过定义的是View中显示的字体大小。在使用数值定义大小时，可以使用的单位除了px和dp外多出了sp，可以让用户通过更改系统字体大小来自动调整安卓应用字体大小，创造统一的视觉体验。
- textColor
	-  与background语法一致，用RGB来定义字体颜色。
- text
	-  TextView中最重要的属性，定义实际显示的内容。


### ImageView

```
<ImageView
 android:id="@+id/photo_image_view"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:scaleType="centerCrop"
 android:src="@drawable/beach" />
```
 
教程中另一个View就是ImageView。顾名思义，ImageView负责在屏幕上渲染图片。语法上和TextView有很多相同之处，具有id, layout_width, layout_height，同时也带来了自己独有的属性：

- scaleType
	- 和字体不同，图片几乎不会以固定的尺寸显示在各种各样的屏幕上，因此制定缩放的规则非常重要。scaleType定义了CENTER, CENTER_CROP, CENTER_INSIDE, FIT_CENTER, FIT_END, FIT_START, FIT_XY, SCALE_MATRIX。具体效果可以参考文档。
- src
  - 和字体不同，图片并不能轻易由用户打字来描述。图片通常存在本地或者来源与网络。src提供了两种引用图片的方式，  定义系统路径则表示图片在本地，定义url则表示图片在该网址处。
 
## 文档

其实上面描述的TextView和ImageView还有很多没有提到的属性，他们在XML不定义时采用自己的默认值。那到底有什么呢？

其实日常的开发中，开发者们经常会遇到不知道的特性/功能，或是无法解决的问题。此时除了到处google和搜索Q&A论坛外，Google提供了一套庞大而完善的[开发文档](https://developer.android.com/index.html)，详细描述了安卓开发的方方面面。看文档固然枯燥，但是关键时刻也许能剩下不少调试的时间。

## Kirill Grouchnikov的访谈

1A的最后，讲师采访了Google Play的负责人Kirill Grouchnikov， 请他描述在Google的工作和心路历程。Kirill Grouchnikov描述了Google Play如何使用TextView和ImageView做出精美而友好的界面，并且概括了Google Play的产品开发流程，非常值得一听。
