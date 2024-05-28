# 1.项目目录结构

<img src="\Snipaste_2023-11-06_17-03-39.png" style="zoom:50%;float:left" />java：我们写Java代码的地方，业务功能都在这里实现
res：存放我们各种资源文件的地方，有图片，字符串，动画，音频等，还有各种形式的XML文件

## res/assets

1.drawable：存放各种位图文件，(.png，.jpg，.9png，.gif等)除此之外可能是一些其他的drawable类型的XML文件
2.**layout**：该目录下存放的就是我们的**布局**文件，另外在一些特定的机型上，我们做屏幕适配，比如480*320这样的手机，我们会另外创建一套布局，就行：layout-480x320这样的文件夹！
3.menu：在以前有物理菜单按钮，即menu键的手机上，用的较多，现在用的并不多，菜单项相关的资源xml可在这里编写，不知道谷歌会不会出新的东西来替代菜单了~
4.mipmap-hdpi：高分辨率，一般我们把图片丢这里
5.mipmap-mdpi：中等分辨率，很少，除非兼容的的手机很旧<img src="\Snipaste_2023-11-06_17-14-38.png" style="zoom:100%;float:right" />
6.mipmap-xhdpi：超高分辨率，手机屏幕材质越来越好，以后估计会慢慢往这里过渡
7.mipmap-xxhdpi：超超高分辨率，这个在高端机上有所体现
8.values目录：
        demens.xml：定义尺寸资源
        string.xml：定义字符串资源
        styles.xml：定义样式资源
        colors.xml：定义颜色资源
        arrays.xml：定义数组资源
        attrs.xml：自定义控件时用的较多，自定义控件的属性！
        theme主题文件，和styles很相似，但是会对整个应用中的Actvitiy或指定Activity起作用，一般是改变窗口外观的！可在Java代码中通过setTheme使用，或者在Androidmanifest.xml中为<application...>添加theme的属性！											9.values-xxx目录：values-w820dp，values-v11等，前者w代表平板设备，820dp代表屏幕宽度；而v11这样代表在API(11)，即android 3.0后才会用到的！
10.raw目录： 用于存放各种原生资源(音频，视频，一些XML文件等)，我们可以通过openRawResource(int id)来获得资源的二进制流！其实和Assets差不多，不过这里面的资源会在R文件那里生成一个资源id而已
11.动画目录：
        animator：存放属性动画的XML文件
        anim：存放补间动画的XML文件

# 2.使用资源

所有的资源文件都会在R.java文件下生成一个资源id，可以通过这个资源id来完成资源的访问

## 1.java中

```java
//Java文字：
txtName.setText(getResources().getText(R.string.文件名)); 
//图片：
imgIcon.setBackgroundDrawableResource(R.drawable.文件名); 
//颜色：
txtName.setTextColor(getResouces().getColor(R.color.文件名)); 
//布局：
setContentView(R.layout.文件名);
//控件：
txtName = (TextView)findViewById(R.id.文件名);
```



## 2.xml中

```xml
<TextView android:text="@string/hello_world" android:layout_width="wrap_content" android:layout_height="wrap_content" android:background = "@drawable/img_back"/>
```

# 3.程序签名打包

build-generate signed Bundle/apk

# 4.反编译获取apk内资源

# 5.View/ViewGroup

在Android APP中，所有的用户界面元素都是由View和ViewGroup的对象构成的。

<img src="\Snipaste_2023-11-06_21-56-16.png" style="zoom:70%;float:left" />

最容易和最高效的方式来定义你的布局则是使用一个**XML文件**，使用XML元素的名称代表一个View

## 布局xml文件

```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:tools="http://schemas.android.com/tools"//语法判断器
android:id="@+id/LinearLayout1"//为布局设置id值为LinearLayout,并添加到R文件的id内部类中             android:layout_width="match_parent"
android:layout_height="match_parent"//控制组件的宽度和高度(warp_content/fill_parent/match_parent)
tools:context=".MainActivity"//不会进apk>

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/hello_world" //设置文本，引用string文件夹下的hello_world文件/>

</RelativeLayout>
```

