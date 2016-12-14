###本篇文章适合初学者，所有的内容都是在布局文件中使用的，并没有使用到任何代码。
###在android中，文本的基本控件就要数TextView了，在android中textView的作用无处不在，有很多效果，可能你还不会使用或者不知道，下面就让我以实例来看一下TextView到底做了什么？  

###现在我们就看一下，到底有哪些地方用到了TextView呢？

![](/TextViewForImage/1.png)

比如这个界面 ，可以使用TextView搭建嘛，有人说了这明显上面有个图片，应该选择一个布局，然后每个布局文件中使用一个ImageView和一个TextView吗？ 

这里我们可以用TextView的Drawable属性来做这一个效果：

![](/TextViewForImage/2.png) 

因为屏幕分辨率不太相同和图片不太一致会有视角上的偏差。 

	android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:gravity="center_horizontal"
    android:drawableTop="@drawable/ic_archive_black_24dp" 
    android:text="社区"
    android:layout_weight="1"

上述代码中的重点就是drawableTop，加入这个属性之后，图片会显示在文字的上方，还有drawableBottom，drawableEnd，drawableStart，其中drawableStart和drawableLeft都在在左侧显示，只不过Start是后来Api中显示左侧显示的属性，理所应当的有一个drawableRight，不管写哪一个效果都是一样的，而且不会报错呢。

如果产品设计的产品中有这样的效果，可以尝试下，要比你写一个ImageView在写一个TextView要快的多。

如果产品设计一个拨打电话或者打开网页的，应该怎么做？

一般通过Intent跳转过去，然后拨打电话，同理打开网页也是一样的，使用Intent调用系统。

现在有个简单的方式，比如我就一个网址，需要打开这个网页，但是用Intent你不觉的麻烦吗？如下图：如果你加权限就会提示你。

![](/TextViewForImage/3.png)

其实TextView也可以实现相同的效果，虽然没有使用Intent做的好，也可以实现相同的效果。这个属性就是autoLink，而这个参数有几个常用的：none，web，email，phone，all。
示例如下：

![](/TextViewForImage/1.gif)

在上述图片中我没有验证email的，因为我的模拟器上没有email软件，TextView属性会检测是的text文本输入的内容，与之匹配，autoLink的值是all的情况下，TextView检测输入的text。

在Textview文本中，小写自动转为大写，使用textAllCaps属性，首先上代码：

	<TextView
		android:layout_width="match_parent"
    	android:layout_height="wrap_content"
        android:text="www.baidu.com"
        android:textAllCaps="true"
        />

![](/TextViewForImage/4.png)

使用这个属性再也不用担心测试非得输入小写了。

有的文字需要加粗有的文字还要斜体，那怎么办呢？  
别担心，TextView中textStyle属性可以分分钟解决你的问题。  
这个属性的值可以设置粗体，斜体和不设置三种场景，分别是bold，italic，normal。同时你可以同时使用两个值，那恭喜你可以设置粗斜体了。  

![](/TextViewForImage/5.png)

如果设计出个问题：想让文字之间宽度一样你该怎么做？  
没关系，没有解决不了的问题：android:typeface="monospace"，这个属性使用了之后你字体间是等宽的。如果这样还不能解决问题，设计说要按照我设置的宽度来设置字之间的宽度，那么简单：letterSpacing，这个属性的值是float类型的，所以随便你写宽度多少。但是有个问题是这个属性要在API21以上才能支持，所以，祈祷你的设计是一个聪明人，不过话又说回来了，现在5.0以下的手机多吗？
下图是效果：

![](/TextViewForImage/6.png)

 

最后一个属性，这个属性是textIsSelectable，默认false，设置为true后，按住就可以选择复制了。
