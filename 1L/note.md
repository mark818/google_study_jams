# 学习笔记：Building Layouts: Part 2


## 关键词

- ViewGroup
    >  A ViewGroup is a special view that can contain other views (called children.) The view group is the base class for layouts and views containers. This class also defines the ViewGroup.LayoutParams class which serves as the base class for layouts parameters.
    > 
    >  ViewGroup是一种包含其他View（成为子view）的特殊View。ViewGroup是layout和View容器的基类。该类同时定义了ViewGroup.LayoutParams类，作为layout参数的基类。

- LinearLayout

    >  A Layout that arranges its children in a single column or a single row. The default orientation is horizontal.
    > 
    >  一种将其子View排列为一单行或一单列的Layout。默认的排列方式为横向。
     
- RelativeLayout

    > A Layout where the positions of the children can be described in relation to each other or to the parent.
    >  
    > 一种子View位置可以由其与其他子View或基类的关系定义的Layout。
    
&nbsp;
## ViewGroup

![image](https://github.com/mark818/google_study_jams/raw/master/1L/1L-1.png)

ViewGroup本身不是一种新的View，而是提供了一种组合其他View的规范。如图所示，红色框定义了一个ViewGroup，圈定了屏幕上的一块区域。然后ViewGroup内可以包含ImageView和TextView等，按照XML中参数的设定有机地摆放在ViewGroup区域内。

本章介绍了两种ViewGroup：LinearLayout和RelativeLayout。下面介绍它们的用法。

### LinearLayout

LinearLayout是一种简单的排列规范，它将包含的子View依次横向排开或纵向排开。我们看下面的例子：

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@android:color/darker_gray">

    <TextView
        android:text="VIP List"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#4CAF50"
        android:textSize="24sp" />

    <TextView
        android:text="Kunal"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#4CAF50"
        android:textSize="24sp" />

    <TextView
        android:text="Kagure"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#4CAF50"
        android:textSize="24sp" />

    <TextView
        android:text="Lyla"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:background="#4CAF50"
        android:textSize="24sp" />

</LinearLayout>
```

![image](https://github.com/mark818/google_study_jams/raw/master/1L/1L-2.png)

- 最后一行有一个```</LinearLayout>```，如果感到陌生，请前往我的1A笔记，其中有解释XML的closing tag。ViewGroup因为包含内容，不能使用self-closing tag。

- 子View按照代码中出现的顺序依次向下/右排列。向下还是向右取决于ViewGroup中的```android:orientation```参数，代码中设为vertical。

- 除了常用的参数，TextView中的layout_width或/和layout_height使用match_parent时会**撑满**其所在的ViewGroup的layout_width或/和layout_height。在例子中，我们使layout_width使用match_parent，从而使该TextView横向撑满了ViewGroup，而纵向保持wrap_content，形成对比。

### layout_weight

在我们介绍RelativeLayout之前，教程提到了一个将View均匀分布屏幕的方法：layout_weight。使用layout_weight可以将根据LinearLayout的横/竖orientation忽视子View的layout_width/layout_height，而根据layout_weight来分配屏幕空间。

在应用到ImageView时，其空间将完全取决于layout_weight；而在TextView中，最小面积取决与TextSize，即每个TextSize给予不小于wrap_content的空间，然后根据其layout_weight给予额外的空间。需要注意的是，每个View的空间计算是按xml中出现的顺序计算的，因此如果先出现的View占有了过大的weight，后出现的TextView将无法保证最小的能够显示的TextSize，被直接冲出的屏幕，如下图。

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <ImageView
        android:src="@drawable/ocean"
        android:layout_width="wrap_content"
        android:layout_height="500dp"
        android:layout_weight="2"
        android:scaleType="centerCrop" />

    <TextView
        android:text="You're invited!"
        android:layout_width="wrap_content"
        android:layout_height="100dp"
        android:textColor="@android:color/white"
        android:textSize="54sp"
        android:layout_weight="1000"
        android:background="#009688" />

    <TextView
        android:text="Bonfire at the beach"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textColor="@android:color/white"
        android:textSize="34sp"
        android:layout_weight="1"
        android:background="#009688" />

</LinearLayout>
```

![image](https://github.com/mark818/google_study_jams/raw/master/1L/1L-3.png)

### RelativeLayout

RelativeLayout是一种更加灵活的排列规范，给予使用者在排版上更多的自由度，从而作出复杂的界面。RelativeLayout通过子View之间或子View与ViewGroup之间的相互关系定义它们的位置。

在看例子之前，我们先梳理一下RelativeLayout用到的主要属性：

- ```android:id="@+id/xxx``` 用于区别各个子View，在使用相对位置时使用该属性指代View

- ```android:layout_alignParentLeft="true"``` 将子View放在ViewGroup的左边，有上下的自由度

- ```android:layout_alignParentTop="true"``` 将子View放在ViewGroup的顶边，有左右的自由度

- ```android:layout_alignParenRight="true"``` 将子View放在ViewGroup的右边，有上下的自由度

- ```android:layout_alignParenBottom="true"``` 将子View放在ViewGroup的底边，有左右的自由度

- 将上下和左右搭配使用可以将子View定位在屏幕的四个角上之一

- ```android:layout_centerHorizontal="true"``` 在现有的纵向位置前提下将子View横向居中

- ```android:layout_centerVertical="true"``` 在现有的横向位置前提下将子View纵向居中

- ```android:layout_toLeftOf="@id/xxx``` 将子View的横向位置置于给定ID代表的View的左边

- ```android:layout_toRightOf="@id/xxx``` 将子View的横向位置置于给定ID代表的View的右边

- ```android:layout_above="@id/xxx``` 将子View的纵向位置置于给定ID代表的View的上边

- ```android:layout_below="@id/xxx``` 将子View的纵向位置置于给定ID代表的View的下边


上面列举了很多的属性，他们之间可以有机地结合使用来定位一个View。我们看下面的例子：


```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@+id/lyla_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentLeft="true"
        android:textSize="24sp"
        android:text="Lyla" />

    <TextView
        android:id="@+id/me_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_toRightOf="@id/lyla_text_view"
        android:layout_alignParentLeft="true"

        android:textSize="24sp"
        android:text="Me" />

    <TextView
        android:id="@+id/natalie_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:textSize="24sp"
        android:text="Natalie" />

    <TextView
        android:id="@+id/jennie_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_alignParentRight="true"
        android:textSize="24sp"
        android:text="Jennie" />

    <TextView
        android:id="@+id/omoju_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentRight="true"
        android:layout_above="@id/jennie_text_view"
        android:textSize="24sp"
        android:text="Omoju" />

    <TextView
        android:id="@+id/amy_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_toLeftOf="@id/jennie_text_view"
        android:textSize="24sp"
        android:text="Amy" />

    <TextView
        android:id="@+id/ben_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentTop="true"
        android:layout_centerHorizontal="true"
        android:textSize="24sp"
        android:text="Ben" />

    <TextView
        android:id="@+id/kunal_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:layout_toLeftOf="@id/ben_text_view"
        android:textSize="24sp"
        android:text="Kunal" />

    <TextView
        android:id="@+id/kagure_text_view"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_alignParentTop="true"
        android:layout_alignParentRight="true"
        android:textSize="24sp"
        android:text="Kagure" />

</RelativeLayout>
```

![image](https://github.com/mark818/google_study_jams/raw/master/1L/1L-4.png)

下面我们来跟着代码分析每一个View的定位：

- Lyla具有```android:layout_alignParentBottom="true"```以及```android:layout_alignParentLeft="true"```，因此被放在ViewGroup的左下角。

- Me具有```android:layout_alignParentBottom="true"```，```android:layout_toRightOf="@id/lyla_text_view"```，因此同样放在ViewGroup左下角，但是又因为```android:layout_alignParentLeft="true"```，所以放在Lyla的右边。

- Natalie没有任何定位的属性，按照默认值置于ViewGroup的左上角。

- Jennie具有```android:layout_alignParentBottom="true"```以及```android:layout_alignParentRight="true"```，因此被放在ViewGroup的右下角。

- Omoju具有```android:layout_alignParentRight="true"```因此置于ViewGroup的右边界，又因为```android:layout_above="@id/jennie_text_view"```因此置于Jennie的上方。

- Amy具有```android:layout_alignParentBottom="true"```因此置于ViewGroup的底部，又因为```android:layout_toLeftOf="@id/jennie_text_view"```因此置于Jennie的左边。

- Ben具有```android:layout_alignParentTop="true"```因此置于ViewGroup的顶部，又因为```android:layout_centerHorizontal="true"```因此居中于顶部。

- Kunal具有```android:layout_alignParentBottom="true"```因此置于ViewGroup底部，又因为```android:layout_toLeftOf="@id/ben_text_view"```所以**横向位置**在Ben的左边。这是个很好的横竖位置分开定位的例子。

- Kagure具有```android:layout_alignParentTop="true"```以及```android:layout_alignParentRight="true"```，因此被放在ViewGroup的右上角。
 
相信经过上面的详细解释，RelativeLayout的“位置学”一定不再神秘了。不过要注意的是，部分属性之间会相互冲突，比如一个View不能既alignParentTop又alignParentBottom，也不能toLeftOf和toRightOf同一个View，更不能将同一方向（横/竖）的相对位置与centerVertical/centerHoriontal共用。具体的冲突其实用简单推理就可发现。


## Kirill Grouchnikov的访谈

1B的最后，讲师再次采访了Google Play的负责人Kirill Grouchnikov，请他介绍Google Play的UI设计是如何应用两种ViewGroup的。值得记住的是Kirill Grouchnikov提到，不要因为功能简单而弃用LinearLayout，在合适的场景下LinearLayout足以完成任务。
