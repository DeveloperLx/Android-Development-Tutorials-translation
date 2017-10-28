# Android：材料设计的介绍 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/168916/android-an-introduction-to-material-design) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志
            </em>
            ：本教程已由Joe Howard更新至Kotlin版本。原教程由Megha Bambra撰写。
        </p>
    </div>
    <div id="attachment_119228" style="width: 260px" class="wp-caption alignright">
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/MaterialDesign-feature-250x250.png"
        alt="Material Design with Kotlin!" width="250" height="250" class="size-full wp-image-119228">
        <p class="wp-caption-text">
            材料设计 - Kotlin！
        </p>
    </div>
    <p>
        Google的材料设计可以帮助你带给用户精美的Android app。但稍等-神马是材料设计？
    </p>
    <p>
        Google将其描述为一个界面，结合 触觉的表面，粗体的图形设计和流畅的动作，创造出美丽，直观的体验。材料设计是Android app的“用户体验哲学”！
    </p>
    <p>
        在本教程中，你会将材料设计植入到一个叫做Travel Wishlist的app中。通过这个过程你会学习到：
    </p>
    <ul>
        <li>
            实现材料主题；
        </li>
        <li>
            使用类似
            <code>
                RecyclerView
            </code>
            和
            <code>
                CardView
            </code>
            的原件构建动态性的视图。
        </li>
        <li>
            使用Palette API来生成颜色主题，你可以将其用于文本或是背景view之上。
        </li>
        <li>
            使用Android的动画API创建超赞的交互。
        </li>
    </ul>
    <p>
        本教程假定你已熟悉了Android编程的基础，包括Kotlin，XML，Android Studio和Gradle。如果你是一个Android的纯小白，可以首先学习我们的
        <a title="Android Tutorials" href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Beginning%20Android%20Development%20Part%20One%20Installing%20Android%20Studio.md"
        target="_blank">
            Beginning Android Development
        </a>
        系列和
        <a title="Kotlin Introduction" href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Kotlin%20For%20Android%20An%20Introduction.md"
        target="_blank">
            Kotlin Introduction
        </a>
        。
        <br>
    </p>
    <p>
        为完成本教程，你需要使用Android Studio 3.0 Beta 2、Kotlin 1.1.4-2或更高的版本。
    </p>
    <p>
        让我们开始吧！
    </p>
    <h2>
        入门
    </h2>
    <p>
        下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/travelwishlist-starter-1.zip">
            初始项目
        </a>
        ，并打开
        <em>
            Android Studio
        </em>
        。
    </p>
    <p>
        要导入初始的项目，首先在
        <em>
            Welcome to Android Studio
        </em>
        窗口中选择
        <em>
            Open an existing Android Studio project
        </em>
        ：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-8.06.02-PM.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-8.06.02-PM-650x403.png"
            alt="" width="650" height="403" class="aligncenter size-large wp-image-168927"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-8.06.02-PM-650x403.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-8.06.02-PM-480x298.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-8.06.02-PM.png 777w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        然后选择下载的项目并点击
        <em>
            Open
        </em>
        ：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.05.24-PM.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.05.24-PM-650x445.png"
            alt="" width="650" height="445" class="aligncenter size-large wp-image-168929"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.05.24-PM-650x445.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.05.24-PM-467x320.png 467w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.05.24-PM.png 704w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        Travel Wishlist是一个非常简单的app。用户可以在上面看到一个来自全世界的图片的网格，并可以点击每个图片来添加相关的笔记。
    </p>
    <p>
        Build并运行起始项目，你会看到一个带有基本界面的页面：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503191407.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503191407-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168931"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503191407-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503191407-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503191407.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        现在一切都是空的！你会添加一些材料的组件到它上面，包括动态的view，颜色方案和动画，来真正地完善这些照片。
    </p>
    <p>
        打开app模块中的
        <em>
            build.gradle
        </em>
        ，并添加RecyclerView，CardView，Palette，和Picasso到你的依赖中：
    </p>
    <pre lang="groovy" class="language-groovy">dependencies {
    implementation fileTree(dir: 'libs', include: ['*.jar'])
    implementation "org.jetbrains.kotlin:kotlin-stdlib-jre7:$kotlin_version"
    implementation 'com.android.support:appcompat-v7:26.0.1'
    implementation 'com.android.support:recyclerview-v7:26.0.1'
    implementation 'com.android.support:cardview-v7:26.0.1'
    implementation 'com.android.support:palette-v7:26.0.1'
    implementation 'com.squareup.picasso:picasso:2.5.2'
    testImplementation 'junit:junit:4.12'
    androidTestImplementation 'com.android.support.test:runner:1.0.0'
    androidTestImplementation 'com.android.support.test.espresso:espresso-core:3.0.0'
}
</pre>
    <p>
        这里声明了你在本教程剩下的部分中需要使用到的依赖。前几个是Google提供的API的依赖，而最后的
        <a href="http://square.github.io/picasso/" target="_blank">
            Picasso
        </a>
        ，则是由
        <a href="https://squareup.com" target="_blank">
            Square
        </a>
        提供的一个神奇的图片下载和缓存库。
    </p>
    <p>
        依赖声明好之后，就该将材料设计迁移到你的app中了！
    </p>
    <h2>
        设置主题
    </h2>
    <p>
        在完成其它工作前，你需要更新主题。打开
        <em>
            res/values
        </em>
        目录下的
        <em>
            style.xml
        </em>
        。默认情况下选择的主题是
        <code>
            Theme.AppCompat.Light.DarkActionBar
        </code>
        。添加下列的item到主题tag中：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">item</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"android:navigationBarColor"</span>&gt;</span>@color/primary_dark<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">item</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"android:displayOptions"</span>&gt;</span>disableHome<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
</pre>
    <p>
        Android会自动地将
        <code>
            colorPrimary
        </code>
        应用到action bar上，将
        <code>
            colorPrimaryDark
        </code>
        应用到status bar上，将
        <code>
            colorAccent
        </code>
        应用到诸如文本输入框和勾选框的UI控件上。
    </p>
    <p>
        在上述代码中，你还改变了navigation bar的颜色。对于
        <code>
            android:displayOptions
        </code>
        ，则传参
        <code>
            disableHome
        </code>
        以在这个简单的app中适应屏幕的布局。
    </p>
    <p>
        运行项目，你就会在app中看到新的颜色方案。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503192155.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503192155-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168933"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503192155-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503192155-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503192155.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        发生了一些微妙的变化，但就像一个你旅行的愿望清单一样，升级设计始于此步！
    </p>
    <h2>
        使用RecyclerView和CardView
    </h2>
    <p>
        To give your users a window into all the cool places they might go,
        you need a view. You can use
        <code>
            RecyclerView
        </code>
        as a replacement for
        <code>
            ListView
        </code>
        , but it’s much more versatile than that. Google describes
        <code>
            RecyclerView
        </code>
        as “a flexible view for providing a limited window into a large data set.”
        In this section, you’re going to demonstrate this by switching the view
        from a list to a custom grid that uses the same data source which supplies
        the the users locations.
    </p>
    <h3>
        Implementing a Recycler View in XML
    </h3>
    <p>
        First, open
        <em>
            activity_main.xml
        </em>
        and add the following inside the
        <code>
            LinearLayout
        </code>
        tag:
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.RecyclerView</span>
  <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/list"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:background</span>=<span class="hljs-string">"@color/light_gray"</span>/&gt;</span>
</pre>
    <p>
        Here you’re adding a
        <code>
            RecyclerView
        </code>
        to the activity’s layout, and specifying it should match the entire size
        of the parent view.
    </p>
    <h3>
        Initializing a Recycler View and Applying a Layout Manager
    </h3>
    <p>
        Before adding Kotlin code, configure Android Studio so that it automatically
        inserts import statements to save you having to add each one manually.
    </p>
    <p>
        Go to
        <em>
            Preferences\Editor\General\Auto Import
        </em>
        and select the
        <em>
            Add unambiguous imports on the fly
        </em>
        checkbox. In
        <em>
            MainActivity.kt
        </em>
        , add the following to the top of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> staggeredLayoutManager: StaggeredGridLayoutManager
</pre>
    <p>
        Here you’re simply declaring a property to hold a reference to the
        <code>
            LayoutManager
        </code>
        .
    </p>
    <p>
        Next, add the following to the bottom of
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">staggeredLayoutManager = StaggeredGridLayoutManager(<span class="hljs-number">1</span>, StaggeredGridLayoutManager.VERTICAL)
list.layoutManager = staggeredLayoutManager
</pre>
    <p>
        In the code above, you set the layout manager of the
        <code>
            RecyclerView
        </code>
        to a
        <code>
            StaggeredGridLayoutManager
        </code>
        , which you’ll use to create two types of vertically staggered grids.
        Here you start with the first type, passing
        <code>
            1
        </code>
        for the span count and
        <code>
            StaggeredGridLayoutManager.VERTICAL
        </code>
        for the orientation. A span count of 1 makes this a list rather than a
        grid, as you’ll soon see. Later, you’ll add a compact grid formation with
        two columns.
    </p>
    <p>
        Note that you’re using
        <em>
            Kotlin Android Extensions
        </em>
        to find
        <code>
            list
        </code>
        , so there is no need for a call to
        <code>
            findViewById()
        </code>
        . Make sure that the following line is present in your import statements,
        as it should be automatically added when you type in
        <code>
            list
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> kotlinx.android.synthetic.main.activity_main.*
</pre>
    <h3>
        Creating Rows and Cells Using a Card View
    </h3>
    <p>
        <code>
            CardView
        </code>
        provides a consistent backdrop for your views, including rounded corners
        and a drop shadow. You’re going to implement it for the row/cell layout
        of your
        <code>
            RecyclerView
        </code>
        . By default,
        <code>
            CardView
        </code>
        extends
        <code>
            FrameLayout
        </code>
        and therefore includes the ability to host other child views.
    </p>
    <p>
        From the
        <em>
            res\layout
        </em>
        directory, create a new
        <em>
            Layout resource file
        </em>
        and call it
        <em>
            row_places.xml
        </em>
        . Press
        <em>
            OK
        </em>
        to create it.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.38.35-PM.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.38.35-PM-650x377.png"
            alt="" width="650" height="377" class="aligncenter size-large wp-image-168935"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.38.35-PM-650x377.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.38.35-PM-480x278.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-19-at-9.38.35-PM.png 824w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        To create your desired cell layout, replace all the contents of this file
        with the code below:
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.CardView</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">xmlns:card_view</span>=<span class="hljs-string">"http://schemas.android.com/apk/res-auto"</span>
  <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/placeCard"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
  <span class="hljs-attr">android:layout_margin</span>=<span class="hljs-string">"8dp"</span>
  <span class="hljs-attr">card_view:cardCornerRadius</span>=<span class="hljs-string">"@dimen/card_corner_radius"</span>
  <span class="hljs-attr">card_view:cardElevation</span>=<span class="hljs-string">"@dimen/card_elevation"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">ImageView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/placeImage"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"200dp"</span>
    <span class="hljs-attr">android:scaleType</span>=<span class="hljs-string">"centerCrop"</span> /&gt;</span>

  <span class="hljs-comment">&lt;!-- Used for the ripple effect on touch --&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">LinearLayout</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/placeHolder"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:background</span>=<span class="hljs-string">"?android:selectableItemBackground"</span>
    <span class="hljs-attr">android:orientation</span>=<span class="hljs-string">"horizontal"</span> /&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">LinearLayout</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/placeNameHolder"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"45dp"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"bottom"</span>
    <span class="hljs-attr">android:orientation</span>=<span class="hljs-string">"horizontal"</span>&gt;</span>

    <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/placeName"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"center_vertical"</span>
      <span class="hljs-attr">android:gravity</span>=<span class="hljs-string">"start"</span>
      <span class="hljs-attr">android:paddingStart</span>=<span class="hljs-string">"10dp"</span>
      <span class="hljs-attr">android:paddingEnd</span>=<span class="hljs-string">"10dp"</span>
      <span class="hljs-attr">android:textAppearance</span>=<span class="hljs-string">"?android:attr/textAppearanceLarge"</span>
      <span class="hljs-attr">android:textColor</span>=<span class="hljs-string">"@android:color/white"</span> /&gt;</span>

  <span class="hljs-tag">&lt;/<span class="hljs-name">LinearLayout</span>&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">android.support.v7.widget.CardView</span>&gt;</span>
</pre>
    <p>
        By adding
        <code>
            xmlns:card_view="http://schemas.android.com/apk/res-auto"
        </code>
        , you can define attributes like
        <code>
            card_view:cardCornerRadius
        </code>
        and
        <code>
            card_view:cardElevation
        </code>
        that are responsible for giving Material Design enabled Android apps their
        signature card-like look.
    </p>
    <p>
        Notice that for
        <code>
            mainHolder
        </code>
        , you’ve added
        <code>
            ?android:selectableItemBackground
        </code>
        as the background. This enables the
        <i>
            ripple
        </i>
        effect animation when the user touches a cell, as seen in many Android
        apps now. You’ll get to see it in action soon.
    </p>
    <h3>
        Implementing an Adapter for a Recycler View
    </h3>
    <p>
        You’re going to use an adapter for the
        <code>
            RecyclerView
        </code>
        to bind data to the view. In the
        <em>
            main/java
        </em>
        folder, right-click on the
        <em>
            package com.raywenderlich.android.travelwishlist
        </em>
        package and select
        <em>
            New\Kotline File/Class
        </em>
        . Call the class
        <em>
            TravelListAdapter
        </em>
        .
    </p>
    <p>
        Add the following code to the class, taking care to preserve the package
        statement at the top of the file:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">TravelListAdapter</span></span>(<span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> context: Context) : RecyclerView.Adapter&lt;TravelListAdapter.ViewHolder&gt;() {

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getItemCount</span><span class="hljs-params">()</span></span>: <span class="hljs-built_in">Int</span> {
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateViewHolder</span><span class="hljs-params">(parent: <span class="hljs-type">ViewGroup</span>?, viewType: <span class="hljs-type">Int</span>)</span></span>: ViewHolder {
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onBindViewHolder</span><span class="hljs-params">(holder: <span class="hljs-type">ViewHolder</span>?, position: <span class="hljs-type">Int</span>)</span></span> {
  }

  <span class="hljs-comment">// 2</span>
  inner <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ViewHolder</span></span>(itemView: View) : RecyclerView.ViewHolder(itemView) {    
  }
}
</pre>
    <p>
        A couple of things are happening above:
    </p>
    <ol>
        <li>
            You make
            <code>
                TravelListAdapter
            </code>
            extend
            <code>
                Recycler.Adapter
            </code>
            so that you can implement logic for the override methods you’ll add soon.
            You also setup the constructor with a
            <code>
                Context
            </code>
            that will be passed in when you create an instance of
            <code>
                TravelListAdapter
            </code>
            in
            <code>
                MainActivity
            </code>
            , which you’ll do a bit later in the tutorial.
        </li>
        <li>
            You create the
            <code>
                ViewHolder
            </code>
            class. Whereas the use of the
            <code>
                ViewHolder
            </code>
            pattern is optional in
            <code>
                ListView
            </code>
            ,
            <code>
                RecyclerView
            </code>
            enforces it. This improves scrolling and performance by avoiding
            <code>
                findViewById()
            </code>
            for each cell.
        </li>
    </ol>
    <p>
        Update the
        <code>
            RecyclerView.Adapter
        </code>
        methods in
        <code>
            TravelListAdapter
        </code>
        to the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                getItemCount
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        = PlaceData.placeList().size
        <span class="hljs-comment">
            // 2
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onCreateViewHolder
            </span>
            <span class="hljs-params">
                (parent:
                <span class="hljs-type">
                    ViewGroup
                </span>
                , viewType:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        : ViewHolder {
        <span class="hljs-keyword">
            val
        </span>
        itemView = LayoutInflater.from(parent.context).inflate(R.layout.row_places,
        parent,
        <span class="hljs-literal">
            false
        </span>
        )
        <span class="hljs-keyword">
            return
        </span>
        ViewHolder(itemView) }
        <span class="hljs-comment">
            // 3
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onBindViewHolder
            </span>
            <span class="hljs-params">
                (holder:
                <span class="hljs-type">
                    ViewHolder
                </span>
                , position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            val
        </span>
        place = PlaceData.placeList()[position] holder.itemView.placeName.text
        = place.name Picasso.with(context).load(place.getImageResourceId(context)).into(holder.itemView.placeImage)
        }
    </pre>
    <p>
        Here’s what’s happening:
    </p>
    <ol>
        <li>
            <code>
                getItemCount()
            </code>
            returns the number of items from your data array. In this case, you’re
            using the size of the
            <code>
                PlaceData.placeList()
            </code>
            .
        </li>
        <li>
            <code>
                onCreateViewHolder(...)
            </code>
            returns a new instance of your
            <code>
                ViewHolder
            </code>
            by passing an inflated view of
            <code>
                row_places
            </code>
            .
        </li>
        <li>
            <code>
                onBindViewHolder(...)
            </code>
            binds the
            <code>
                Place
            </code>
            object to the UI elements in
            <code>
                ViewHolder
            </code>
            . You’ll use Picasso to cache the images for the list.
        </li>
    </ol>
    <p>
        Add a field in
        <code>
            MainActivity
        </code>
        that will hold a reference to your adapter:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            lateinit
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        adapter: TravelListAdapter
    </pre>
    <p>
        And then create an instance of your adapter and pass it to the
        <code>
            RecyclerView
        </code>
        at the bottom of
        <code>
            onCreate()
        </code>
        , just after you configure the layout manager:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        adapter = TravelListAdapter(
        <span class="hljs-keyword">
            this
        </span>
        ) list.adapter = adapter
    </pre>
    <p>
        Now build and run the app, and you’ll see a populated list of places.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503194733.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503194733-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168938"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503194733-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503194733-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503194733.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        Which place is calling your name? I like the look of that turquoise water.
        But wherever you want to go, you’ll want to cultivate your dream by taking
        notes about what to do there. First, you need to make the cells respond
        to a user’s touch.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1.png"
            alt="alltheplaces" width="332" height="335" class="aligncenter size-large wp-image-106846"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1.png 332w, https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1-317x320.png 317w, https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2015/05/alltheplaces1-128x128.png 128w"
            sizes="(max-width: 332px) 100vw, 332px">
        </a>
    </p>
    <h3>
        Implementing a Click Interface for Each Cell
    </h3>
    <p>
        Unlike
        <code>
            ListView
        </code>
        ,
        <code>
            RecyclerView
        </code>
        doesn’t come with an
        <code>
            onItemClick
        </code>
        interface, so you have to implement one in the adapter. In
        <code>
            TravelListAdapter
        </code>
        , create a property to hold an instance of
        <code>
            OnItemClickListener
        </code>
        . Add the following to the top of
        <code>
            TravelListAdapter
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            lateinit
        </span>
        <span class="hljs-keyword">
            var
        </span>
        itemClickListener: OnItemClickListener
    </pre>
    <p>
        Now implement
        <code>
            View.OnClickListener
        </code>
        by adding the interface to the
        <code>
            ViewHolder
        </code>
        inner class definition like this:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        inner
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                ViewHolder
            </span>
        </span>
        (itemView: View) : RecyclerView.ViewHolder(itemView), View.OnClickListener
        {
    </pre>
    <p>
        Then add the following method stub to the inner
        <code>
            ViewHolder
        </code>
        class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onClick
            </span>
            <span class="hljs-params">
                (view:
                <span class="hljs-type">
                    View
                </span>
                )
            </span>
        </span>
        { }
    </pre>
    <p>
        Hook the two up by adding the following
        <code>
            init
        </code>
        block to the top of
        <code>
            ViewHolder
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        init { itemView.placeHolder.setOnClickListener(
        <span class="hljs-keyword">
            this
        </span>
        ) }
    </pre>
    <p>
        Above, you initiate
        <code>
            setOnClickListener
        </code>
        for
        <code>
            placeHolder
        </code>
        and implement the
        <code>
            onClick
        </code>
        override method.
    </p>
    <p>
        You need to do a few more things to implement the
        <code>
            onClick
        </code>
        interface for the
        <code>
            RecyclerView
        </code>
        . First, after the inner
        <code>
            ViewHolder
        </code>
        class definition add the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                interface
            </span>
            <span class="hljs-title">
                OnItemClickListener
            </span>
        </span>
        {
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onItemClick
            </span>
            <span class="hljs-params">
                (view:
                <span class="hljs-type">
                    View
                </span>
                , position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        }
    </pre>
    <p>
        Next, add the setter method of the
        <code>
            onClickListener
        </code>
        to
        <code>
            TravelListAdapter
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                setOnItemClickListener
            </span>
            <span class="hljs-params">
                (itemClickListener:
                <span class="hljs-type">
                    OnItemClickListener
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            this
        </span>
        .itemClickListener = itemClickListener }
    </pre>
    <p>
        Now implement the logic in the empty
        <code>
            onClick()
        </code>
        stub
        <em>
            within
        </em>
        the inner
        <code>
            ViewHolder
        </code>
        class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onClick
            </span>
            <span class="hljs-params">
                (view:
                <span class="hljs-type">
                    View
                </span>
                )
            </span>
        </span>
        = itemClickListener.onItemClick(itemView, adapterPosition)
    </pre>
    <p>
        In
        <code>
            MainActivity
        </code>
        , create an instance of
        <code>
            OnItemClickListener
        </code>
        above
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        onItemClickListener =
        <span class="hljs-keyword">
            object
        </span>
        : TravelListAdapter.OnItemClickListener {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onItemClick
            </span>
            <span class="hljs-params">
                (view:
                <span class="hljs-type">
                    View
                </span>
                , position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        { Toast.makeText(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-symbol">
            @MainActivity
        </span>
        ,
        <span class="hljs-string">
            "Clicked "
        </span>
        + position, Toast.LENGTH_SHORT).show() } }
    </pre>
    <p>
        Finally, set the listener to the adapter by adding the following code
        to the bottom of
        <code>
            onCreate()
        </code>
        , just after where you set the adapter:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        adapter.setOnItemClickListener(onItemClickListener)
    </pre>
    <p>
        Build and run. Now when you tap a cell you’ll see ripple effect every
        time you touch a row, and a Toast notification displaying the position
        of the cell in the list.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-38-08.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-38-08.gif"
            alt="" width="280" height="500" class="aligncenter size-large wp-image-168940">
        </a>
    </p>
    <h3>
        From List to Grid and Back
    </h3>
    <p>
        <code>
            StaggeredLayoutManager
        </code>
        lets you add versatility to your layouts. To change your existing list
        to a more compact two-column grid, you simply have to change the
        <code>
            spanCount
        </code>
        of the
        <code>
            StaggeredLayoutManager
        </code>
        in
        <code>
            MainActivity
        </code>
        .
    </p>
    <p>
        In
        <code>
            toggle()
        </code>
        , add the following to the top of the
        <code>
            showGridView()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        staggeredLayoutManager.spanCount =
        <span class="hljs-number">
            2
        </span>
    </pre>
    <p>
        And now add the following to the top of
        <code>
            showListView()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        staggeredLayoutManager.spanCount =
        <span class="hljs-number">
            1
        </span>
    </pre>
    <p>
        Here you’re simply switching between single and double span counts, which
        displays single and double columns respectively.
    </p>
    <p>
        Build and run and use the action bar button to toggle between list and
        grid views.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-46-24-toggle.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-46-24-toggle.gif"
            alt="" width="282" height="500" class="aligncenter size-full wp-image-168943">
        </a>
    </p>
    <h2>
        Using the Palette API in the List
    </h2>
    <p>
        Now you can add some interesting Material Design features into the mix,
        starting with the Palette API. Head back to
        <code>
            TravelListAdapter
        </code>
        , where you’ll define a background color for
        <code>
            placeNameHolder
        </code>
        that will be determined dynamically using the colors in the image.
    </p>
    <p>
        Add the following to the bottom of
        <code>
            onBindViewHolder(...)
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        photo = BitmapFactory.decodeResource(context.resources, place.getImageResourceId(context))
        Palette.from(photo).generate { palette -&gt;
        <span class="hljs-keyword">
            val
        </span>
        bgColor = palette.getMutedColor(ContextCompat.getColor(context, android.R.color.black))
        holder.itemView.placeNameHolder.setBackgroundColor(bgColor) }
    </pre>
    <p>
        The
        <code>
            generate(...)
        </code>
        method creates a color palette in the background, and is passed a lambda
        that is called when the palette has been generated. Here you can access
        the generated color palette and set the background color of
        <code>
            holder.itemView.placeNameHolder
        </code>
        . If the color doesn’t exist, the method will apply a fallback color —
        in this case,
        <code>
            android.R.color.black
        </code>
        .
    </p>
    <p>
        Build and run to see the Palette API in action!
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503197836.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503197836-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168946"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503197836-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503197836-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503197836.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <div class="note">
        <em>
            Note:
        </em>
        The Palette API can extract the following color profiles from an image:
        <p>
        </p>
        <ul>
            <li>
                Vibrant
            </li>
            <li>
                Dark Vibrant
            </li>
            <li>
                Light Vibrant
            </li>
            <li>
                Muted
            </li>
            <li>
                Dark Muted
            </li>
            <li>
                Light Muted
            </li>
        </ul>
        <p>
        </p>
        <p>
            I encourage you to experiment with these. Instead of
            <code>
                palette.getMutedColor(...)
            </code>
            , try
            <code>
                palette.getVibrantColor(...)
            </code>
            ,
            <code>
                palette.getDarkVibrantColor(...)
            </code>
            and so on.
        </p>
        <p>
        </p>
    </div>
    <h2>
        Using the New Material APIs
    </h2>
    <p>
        In this section, you’ll use
        <code>
            DetailActivity
        </code>
        and its corresponding
        <code>
            activity_detail
        </code>
        layout, and make them cooler by infusing some of the new Material Design
        APIs.
    </p>
    <p>
        First, you’ll want to see how the detail view currently looks in the starter
        project. To see this, first add the following to the companion object of
        <code>
            DetailActivity
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                newIntent
            </span>
            <span class="hljs-params">
                (context:
                <span class="hljs-type">
                    Context
                </span>
                , position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        : Intent {
        <span class="hljs-keyword">
            val
        </span>
        intent = Intent(context, DetailActivity::
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            .
            <span class="hljs-title">
                java
            </span>
            )
        </span>
        intent.putExtra(EXTRA_PARAM_ID, position)
        <span class="hljs-keyword">
            return
        </span>
        intent }
    </pre>
    <p>
        Then, go to
        <code>
            MainActivity
        </code>
        and replace the
        <code>
            Toast
        </code>
        in
        <code>
            onItemClick(...)
        </code>
        of onItemClickListener with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        startActivity(DetailActivity.newIntent(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-symbol">
            @MainActivity
        </span>
        , position))
    </pre>
    <p>
        You can pass the position of the place object via the intent so that
        <code>
            DetailActivity
        </code>
        can retrieve the information and use it to layout the interface. That’s
        what you’re doing here.
    </p>
    <p>
        Build and run.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503199820.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503199820-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168952"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503199820-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503199820-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screenshot_1503199820.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        There isn’t anything crazy going on here (
        <i>
            yet!
        </i>
        ), but you’ve got a nice foundation on which to start adding those highly
        anticipated Material Design APIs. You also see a cool
        <code>
            FloatingActionButton
        </code>
        , one of the widgets introduced by Material Design.
    </p>
    <h3>
        Adding a Reveal Animation
    </h3>
    <p>
        Now you want to give your users the ability to add notes about what they’d
        like to do in each of these stunning places. For this,
        <em>
            activity_detail.xml
        </em>
        already has an
        <code>
            edittext
        </code>
        that is hidden by default. When a user taps the FAB, it reveals itself
        with a cool animation like below:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-23-38-19-reveal.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-23-38-19-reveal.gif"
            alt="" width="412" height="248" class="aligncenter size-full wp-image-168954">
        </a>
    </p>
    <p>
        Open
        <code>
            DetailActivity
        </code>
        . There are two methods you have yet to implement:
    </p>
    <ul>
        <li>
            <code>
                revealEditText()
            </code>
        </li>
        <li>
            <code>
                hideEditText()
            </code>
        </li>
    </ul>
    <p>
        First, add the following lines inside
        <code>
            revealEditText()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        cx = view.right -
        <span class="hljs-number">
            30
        </span>
        <span class="hljs-keyword">
            val
        </span>
        cy = view.bottom -
        <span class="hljs-number">
            60
        </span>
        <span class="hljs-keyword">
            val
        </span>
        finalRadius = Math.max(view.width, view.height)
        <span class="hljs-keyword">
            val
        </span>
        anim = ViewAnimationUtils.createCircularReveal(view, cx, cy,
        <span class="hljs-number">
            0
        </span>
        f, finalRadius.toFloat()) view.visibility = View.VISIBLE isEditTextVisible
        =
        <span class="hljs-literal">
            true
        </span>
        anim.start()
    </pre>
    <p>
        The two
        <code>
            int
        </code>
        values are getting the
        <code>
            x
        </code>
        and
        <code>
            y
        </code>
        positions of the view with a slight offset. This offset gives the illusion
        that the reveal is happening from the direction of your FAB.
    </p>
    <p>
        Next, the radius gives the reveal the circular outline that you can see
        in the GIF above. All of these values — the x-position, y-position and
        the radius — you pass into the animation instance. This animation is using
        <code>
            ViewAnimationUtils
        </code>
        , which gives you the ability to create this circular reveal.
    </p>
    <p>
        Since the
        <code>
            EditText
        </code>
        view is initially hidden, you set the view’s visibility to
        <code>
            VISIBLE
        </code>
        and set your boolean check
        <code>
            isEditTextVisible
        </code>
        to
        <code>
            true
        </code>
        . Finally, you can call
        <code>
            start()
        </code>
        on the animation.
    </p>
    <p>
        To dismiss the view, add the following to
        <code>
            hideEditText()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        cx = view.right -
        <span class="hljs-number">
            30
        </span>
        <span class="hljs-keyword">
            val
        </span>
        cy = view.bottom -
        <span class="hljs-number">
            60
        </span>
        <span class="hljs-keyword">
            val
        </span>
        initialRadius = view.width
        <span class="hljs-keyword">
            val
        </span>
        anim = ViewAnimationUtils.createCircularReveal(view, cx, cy, initialRadius.toFloat(),
        <span class="hljs-number">
            0
        </span>
        f) anim.addListener(
        <span class="hljs-keyword">
            object
        </span>
        : AnimatorListenerAdapter() {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onAnimationEnd
            </span>
            <span class="hljs-params">
                (animation:
                <span class="hljs-type">
                    Animator
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onAnimationEnd(animation) view.visibility = View.INVISIBLE } }) isEditTextVisible
        =
        <span class="hljs-literal">
            false
        </span>
        anim.start()
    </pre>
    <p>
        Here your goal is to hide the view and show the circular animation in
        the opposite direction. Therefore, you make the initial radius the width
        of the view and the ending radius 0, which shrinks the circle.
    </p>
    <p>
        You want to show the animation first and then hide the view. To do this,
        you implement an animation listener and hide the view when the animation
        ends.
    </p>
    <p>
        Now build and run and see this animation in action!
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-23-46-35-reveal2.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-23-46-35-reveal2.gif"
            alt="" width="283" height="500" class="aligncenter size-large wp-image-168956">
        </a>
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : If the keyboard presents itself, you’ll need to dismiss it explicitly
            to see the effect without obstruction. Comment out the call to
            <code>
                inputManager.showSoftInput(...)
            </code>
            in
            <code>
                DetailActivity
            </code>
            , but don’t forget to uncomment it. Oh, and don’t worry that your button
            doesn’t show the plus icon yet, you’ll fix that soon.
        </p>
    </div>
    <h3>
        Morphing a Bezier Path for a Floating Action Button
    </h3>
    <p>
        Now that you have your reveal animation hiding and showing the edit text
        field, you can coordinate the icon on your FAB to look and respond just
        like the one shown below:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-58-26-scuba.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-58-26-scuba.gif"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168973">
        </a>
    </p>
    <p>
        The starter project includes the vector paths for the plus and checkmark
        icons. You’ll learn how to animate – or morph – the paths from the plus
        to the checkmark, and vice versa.
    </p>
    <p>
        Under the
        <em>
            res/drawables
        </em>
        directory, create a new resource file by going to
        <em>
            New\Drawable resource file
        </em>
        . Call it
        <em>
            icn_morph
        </em>
        and define
        <code>
            animated-vector
        </code>
        as the root element:
    </p>
    <pre lang="xml" class="language-xml hljs">
        &lt;?xml version="1.0" encoding="utf-8"?&gt;
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                animated-vector
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            <span class="hljs-attr">
                android:drawable
            </span>
            =
            <span class="hljs-string">
                "@drawable/icn_add"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                animated-vector
            </span>
            &gt;
        </span>
    </pre>
    <p>
        <code>
            animated-vector
        </code>
        requires an existing
        <code>
            android:drawable
        </code>
        . In this case, the animated vector will start with a plus sign and morph
        into a checkmark, so you’ll set the drawable to
        <code>
            icn_add
        </code>
        .
    </p>
    <p>
        Now for the actual morphing, add the following inside the
        <code>
            animated-vector
        </code>
        tag:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                target
            </span>
            <span class="hljs-attr">
                android:animation
            </span>
            =
            <span class="hljs-string">
                "@anim/path_morph"
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "sm_vertical_line"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                target
            </span>
            <span class="hljs-attr">
                android:animation
            </span>
            =
            <span class="hljs-string">
                "@anim/path_morph_lg"
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "lg_vertical_line"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                target
            </span>
            <span class="hljs-attr">
                android:animation
            </span>
            =
            <span class="hljs-string">
                "@anim/fade_out"
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "horizontal_line"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        With the code above, you are essentially transforming the vertical line
        of the plus icon into a checkmark while fading out the horizontal line,
        as the diagram below illustrates:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM.png">
            <img class="aligncenter size-large wp-image-104111" src="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM-700x444.png"
            alt="Screen Shot 2015-04-22 at 12.59.57 AM" width="700" height="444" srcset="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM-700x444.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM-480x305.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM.png 778w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        Furthermore, the vertical line is comprised of two paths, a smaller vertical
        line and a larger one:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM.png">
            <img class="aligncenter size-large wp-image-104116" src="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM-700x337.png"
            alt="Screen Shot 2015-04-22 at 1.11.49 AM" width="700" height="337" srcset="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM-700x337.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM-480x231.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM.png 778w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        You can see from the diagram above that you can transform the first two
        targets,
        <code>
            sm_vertical_line
        </code>
        and
        <code>
            lg_vertical_line
        </code>
        , into a checkmark by drawing their paths at different angles, which is
        exactly what you do in the previous code block, along with fading out
        <code>
            horizontal_line
        </code>
        .
    </p>
    <p>
        Next, you need to reverse this animation to transform the checkmark back
        into a plus sign. Create another drawable resource file, this time calling
        it
        <em>
            icn_morph_reverse
        </em>
        , and replace it’s contents with the following:
    </p>
    <pre lang="xml" class="language-xml hljs">
        &lt;?xml version="1.0" encoding="utf-8"?&gt;
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                animated-vector
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            <span class="hljs-attr">
                android:drawable
            </span>
            =
            <span class="hljs-string">
                "@drawable/icn_add"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                target
            </span>
            <span class="hljs-attr">
                android:animation
            </span>
            =
            <span class="hljs-string">
                "@anim/path_morph_reverse"
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "sm_vertical_line"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                target
            </span>
            <span class="hljs-attr">
                android:animation
            </span>
            =
            <span class="hljs-string">
                "@anim/path_morph_lg_reverse"
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "lg_vertical_line"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                target
            </span>
            <span class="hljs-attr">
                android:animation
            </span>
            =
            <span class="hljs-string">
                "@anim/fade_in"
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "horizontal_line"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                animated-vector
            </span>
            &gt;
        </span>
    </pre>
    <p>
        The two lines that make up the final vertical line in the plus icon will
        now morph back into their original states and the horizontal line will
        fade into view, creating a smooth effect.
    </p>
    <p>
        Now, to complete the animation. Open
        <em>
            DetailActivity.kt
        </em>
        and add the following to
        <code>
            onClick()
        </code>
        , at the end of the
        <code>
            if
        </code>
        branch before the else:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        addButton.setImageResource(R.drawable.icn_morph)
        <span class="hljs-keyword">
            val
        </span>
        animatable = addButton.drawable
        <span class="hljs-keyword">
            as
        </span>
        Animatable animatable.start()
    </pre>
    <p>
        Here you set the image resource of the button to the
        <code>
            icn_morph
        </code>
        drawable you created earlier, extract the animatable from it, and then
        kick-off the animation.
    </p>
    <p>
        Finally, add the following to the very bottom of the
        <code>
            else
        </code>
        branch:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        addButton.setImageResource(R.drawable.icn_morph_reverse)
        <span class="hljs-keyword">
            val
        </span>
        animatable = addButton.drawable
        <span class="hljs-keyword">
            as
        </span>
        Animatable animatable.start()
    </pre>
    <p>
        Here you’re doing almost exactly the same as the previous step, except
        you assign
        <code>
            icn_morph_reverse
        </code>
        as the image resource so the animation plays out in the opposite direction.
    </p>
    <p>
        Along with morphing the icon, the user’s click also adds the text from
        <code>
            todoText
        </code>
        to the
        <code>
            toDoAdapter
        </code>
        and refreshes the place activity list. This is not yet visible because
        of the white text, but in the next section, you’ll add vibrant color to
        your views so that the text stands out.
    </p>
    <p>
        Build and run, and watch the magic unfold before your eyes! The FAB icon
        now morphs between a checkmark and a plus sign when it’s tapped.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-04-13-morph.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-04-13-morph.gif"
            alt="" width="283" height="500" class="aligncenter size-large wp-image-168957">
        </a>
    </p>
    <h3>
        Adding Dynamic Colors to Views Using Palette API
    </h3>
    <p>
        It’s time to add colors to this view using the Palette API. And not just
        any colors—as before, they will be dynamic colors!
    </p>
    <p>
        In
        <code>
            DetailActivity
        </code>
        , flesh out
        <code>
            colorize()
        </code>
        by adding the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        palette = Palette.from(photo).generate() applyPalette(palette)
    </pre>
    <p>
        Just like you did previously, you generate a palette from a photo – although
        this time you do it synchronously – and then pass that palette onto
        <code>
            applyPalette()
        </code>
        . Replace the existing method stub for
        <code>
            applyPalette()
        </code>
        with this code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                applyPalette
            </span>
            <span class="hljs-params">
                (palette:
                <span class="hljs-type">
                    Palette
                </span>
                )
            </span>
        </span>
        { window.setBackgroundDrawable(ColorDrawable(palette.getDarkMutedColor(defaultColor)))
        placeNameHolder.setBackgroundColor(palette.getMutedColor(defaultColor))
        revealView.setBackgroundColor(palette.getLightVibrantColor(defaultColor))
        }
    </pre>
    <p>
        Here you’re you’re using the dark muted color, the muted color, and the
        light vibrant color as the background colors of the window, title holder,
        and reveal view respectively.
    </p>
    <p>
        Finally, to kick-off this chain of events add the following line to the
        bottom of
        <code>
            getPhoto()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        colorize(photo)
    </pre>
    <p>
        It’s that time again… build and run your app! You can see the detail activity
        is now using a color scheme derived from the palette of the associated
        image.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-18-55-colorize.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-18-55-colorize.gif"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168959">
        </a>
    </p>
    <h3>
        Activity Transitions With Shared Elements
    </h3>
    <p>
        We’ve all seen and wondered about those nice image and text transitions
        in Google’s app which have been updated to use Material Design. Well, wait
        no more—you’re about to learn the intricacies of achieving smooth animation.
    </p>
    <div class="note">
        <em>
            Note
        </em>
        : Activity transitions, together with shared elements, allow your app
        to transition between two activities that share common views. For example,
        you can transition a thumbnail on a list into a larger image on a detail
        activity, providing continuity of the content.
    </div>
    <p>
        Between the places list view,
        <code>
            MainActivity
        </code>
        , and the places detail view,
        <code>
            DetailActivity
        </code>
        , you’re going to transition the following elements:
    </p>
    <ul>
        <li>
            The image of the place;
        </li>
        <li>
            The title of the place;
        </li>
        <li>
            The background area of the title.
        </li>
    </ul>
    <p>
        Open
        <em>
            row_places.xml
        </em>
        and add the following to the declaration of the
        <code>
            ImageView
        </code>
        tag with an id of
        <code>
            placeImage
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        android:transitionName="tImage"
    </pre>
    <p>
        And then add this to the
        <code>
            LinearLayout
        </code>
        tag with an id of
        <code>
            placeNameHolder
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        android:transitionName="tNameHolder"
    </pre>
    <p>
        Notice that
        <code>
            placeName
        </code>
        doesn’t have a transition name. This is because it is the child of
        <code>
            placeNameHolder
        </code>
        , which will transition all of its child views.
    </p>
    <p>
        In
        <em>
            activity_detail.xml
        </em>
        , add a
        <code>
            transitionName
        </code>
        to the
        <code>
            ImageView
        </code>
        tag with the id
        <code>
            placeImage
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        android:transitionName="tImage"
    </pre>
    <p>
        And, in a similar fashion, add a
        <code>
            transitionName
        </code>
        to the
        <code>
            LinearLayout
        </code>
        tag that has an id of
        <code>
            placeNameHolder
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        android:transitionName="tNameHolder"
    </pre>
    <p>
        Shared elements between activities that you want to transition should
        have the same
        <code>
            android:transitionName
        </code>
        , which is what you’re setting up here. Also, notice that the size of
        the image, as well as the height of the
        <code>
            placeNameHolder
        </code>
        are much larger in this activity. You’re going to animate all of these
        layout changes during the activity transition to provide some nice visual
        continuity.
    </p>
    <p>
        In
        <code>
            onItemClickListener()
        </code>
        found in
        <code>
            MainActivity
        </code>
        , update the method to the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onItemClick
            </span>
            <span class="hljs-params">
                (view:
                <span class="hljs-type">
                    View
                </span>
                , position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            val
        </span>
        intent = DetailActivity.newIntent(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-symbol">
            @MainActivity
        </span>
        , position)
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            val
        </span>
        placeImage = view.findViewById&lt;ImageView&gt;(R.id.placeImage)
        <span class="hljs-keyword">
            val
        </span>
        placeNameHolder = view.findViewById&lt;LinearLayout&gt;(R.id.placeNameHolder)
        <span class="hljs-comment">
            // 2
        </span>
        <span class="hljs-keyword">
            val
        </span>
        imagePair = Pair.create(placeImage
        <span class="hljs-keyword">
            as
        </span>
        View,
        <span class="hljs-string">
            "tImage"
        </span>
        )
        <span class="hljs-keyword">
            val
        </span>
        holderPair = Pair.create(placeNameHolder
        <span class="hljs-keyword">
            as
        </span>
        View,
        <span class="hljs-string">
            "tNameHolder"
        </span>
        )
        <span class="hljs-comment">
            // 3
        </span>
        <span class="hljs-keyword">
            val
        </span>
        options = ActivityOptionsCompat.makeSceneTransitionAnimation(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-symbol">
            @MainActivity
        </span>
        , imagePair, holderPair) ActivityCompat.startActivity(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-symbol">
            @MainActivity
        </span>
        , intent, options.toBundle()) }
    </pre>
    <p>
        After adding this code, you will need to
        <em>
            manually add
        </em>
        the following import statement to the top of the file as Android Studio
        cannot automatically determine that this is the intended package.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.support.v4.util.Pair
    </pre>
    <p>
        There are a couple of things to highlight here:
    </p>
    <ol>
        <li>
            You get an instance of both
            <code>
                placeImage
            </code>
            and
            <code>
                placeNameHolder
            </code>
            for the given position of the
            <code>
                RecyclerView
            </code>
            . You’re not relying on Kotlin Android Extensions here since you need
            the
            <code>
                placeImage
            </code>
            and
            <code>
                placeNameHolder
            </code>
            from the specific
            <code>
                view
            </code>
            .
        </li>
        <li>
            You create a
            <a href="http://developer.android.com/reference/android/util/Pair.html"
            target="">
                <code>
                    Pair
                </code>
            </a>
            containing the view and the
            <code>
                transitionName
            </code>
            for both the image and the text holder view. Note that you will once again
            have to manually add the import statement to the top of the file:
            <code>
                android.support.v4.util.Pair
            </code>
            .
        </li>
        <li>
            To make the activity scene transition with shared views, you pass in your
            <code>
                Pair
            </code>
            instances and start the activity with your
            <code>
                options
            </code>
            bundle.
        </li>
    </ol>
    <p>
        Build and run to see the image transition from the main activity to the
        detail activity:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-45-50-transition.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-45-50-transition.gif"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168960">
        </a>
    </p>
    <p>
        However, the animation is a bit jumpy in two areas:
    </p>
    <ul>
        <li>
            The FAB button suddenly appears in
            <code>
                DetailActivity
            </code>
            .
        </li>
        <li>
            If you tap on a row under the action or navigation bar, that row appears
            to jump a bit before it transitions.
        </li>
    </ul>
    <p>
        You’ll solve the FAB button issue first. Open
        <em>
            DetailActivity.kt
        </em>
        and add the following to
        <code>
            windowTransition()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        window.enterTransition.addListener(
        <span class="hljs-keyword">
            object
        </span>
        : Transition.TransitionListener {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onTransitionEnd
            </span>
            <span class="hljs-params">
                (transition:
                <span class="hljs-type">
                    Transition
                </span>
                )
            </span>
        </span>
        { addButton.animate().alpha(
        <span class="hljs-number">
            1.0
        </span>
        f) window.enterTransition.removeListener(
        <span class="hljs-keyword">
            this
        </span>
        ) }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onTransitionResume
            </span>
            <span class="hljs-params">
                (transition:
                <span class="hljs-type">
                    Transition
                </span>
                )
            </span>
        </span>
        { }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onTransitionPause
            </span>
            <span class="hljs-params">
                (transition:
                <span class="hljs-type">
                    Transition
                </span>
                )
            </span>
        </span>
        { }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onTransitionCancel
            </span>
            <span class="hljs-params">
                (transition:
                <span class="hljs-type">
                    Transition
                </span>
                )
            </span>
        </span>
        { }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onTransitionStart
            </span>
            <span class="hljs-params">
                (transition:
                <span class="hljs-type">
                    Transition
                </span>
                )
            </span>
        </span>
        { } })
    </pre>
    <p>
        The listener you add to the enter transition is triggered when the window
        transition ends, which you use to fade in the FAB button. For this to be
        effective, set the
        <code>
            alpha
        </code>
        to
        <code>
            0
        </code>
        for the FAB in
        <em>
            activity_detail.xml
        </em>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        android:alpha="0.0"
    </pre>
    <p>
        Build and run! You’ll notice the FAB transition is
        <i>
            much
        </i>
        smoother!:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-54-17-transition2.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-54-17-transition2.gif"
            alt="" width="282" height="500" class="aligncenter size-large wp-image-168963">
        </a>
    </p>
    <p>
        As for the action bar and navigation bar issues, begin by updating
        <em>
            styles.xml
        </em>
        , to set the parent theme to
        <code>
            Theme.AppCompat.Light.NoActionBar
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                style
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "AppTheme"
            </span>
            <span class="hljs-attr">
                parent
            </span>
            =
            <span class="hljs-string">
                "Theme.AppCompat.Light.NoActionBar"
            </span>
            &gt;
        </span>
        <span class="undefined">
        </span>
    </pre>
    <p>
        Since there is no action bar defined in
        <em>
            styles.xml
        </em>
        , you’ll have to add it using individual XML views.
    </p>
    <p>
        Open
        <em>
            activity_main.xml
        </em>
        and add the following inside
        <code>
            LinearLayout
        </code>
        , just above the
        <code>
            RecyclerView
        </code>
        tag:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                include
            </span>
            <span class="hljs-attr">
                layout
            </span>
            =
            <span class="hljs-string">
                "@layout/toolbar"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        This simply includes a toolbar layout that's provided as part of the starter
        project into the current layout. Now you need to make a similar change
        to the detail activity's layout.
    </p>
    <p>
        Open
        <em>
            activity_detail.xml
        </em>
        and add the following at the very bottom of the first
        <code>
            FrameLayout
        </code>
        , just below the closing tag of the inner
        <code>
            LinearLayout
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                include
            </span>
            <span class="hljs-attr">
                layout
            </span>
            =
            <span class="hljs-string">
                "@layout/toolbar_detail"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        Next in
        <code>
            MainActivity
        </code>
        , you need to initialize the toolbar. Add the following to the bottom
        of the
        <code>
            onCreate()
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setUpActionBar()
    </pre>
    <p>
        Here you assign the result of the
        <code>
            findViewById
        </code>
        call to the new field, and then call
        <code>
            setUpActionBar()
        </code>
        . At the moment it's just an empty method stub. Fix that now by adding
        the following to
        <code>
            setUpActionBar()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setSupportActionBar(toolbar) supportActionBar?.setDisplayHomeAsUpEnabled(
        <span class="hljs-literal">
            false
        </span>
        ) supportActionBar?.setDisplayShowTitleEnabled(
        <span class="hljs-literal">
            true
        </span>
        ) supportActionBar?.elevation =
        <span class="hljs-number">
            7.0
        </span>
        f
    </pre>
    <p>
        Here you set the action bar to be an instance of your custom toolbar,
        set the visibility of the title, disable the home button, and add a subtle
        drop shadow by setting the elevation.
    </p>
    <p>
        Build and run. You'll notice that nothing much has changed, but these
        changes have laid the foundations of properly being able to transition
        the toolbar.
    </p>
    <p>
        Open
        <code>
            MainActivity
        </code>
        and replace the existing
        <code>
            onItemClickListener
        </code>
        with this one:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            private
        </span>
        val onItemClickListener = object : TravelListAdapter.OnItemClickListener
        {
        <span class="hljs-function">
            override fun
            <span class="hljs-title">
                onItemClick
            </span>
            <span class="hljs-params">
                (view: View, position: Int)
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        val transitionIntent = DetailActivity.newIntent(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-meta">
            @MainActivity
        </span>
        , position) val placeImage = view.findViewById&lt;ImageView&gt;(R.id.placeImage)
        val placeNameHolder = view.findViewById&lt;LinearLayout&gt;(R.id.placeNameHolder)
        <span class="hljs-comment">
            // 2
        </span>
        val navigationBar = findViewById&lt;View&gt;(android.R.id.navigationBarBackground)
        val statusBar = findViewById&lt;View&gt;(android.R.id.statusBarBackground)
        val imagePair = Pair.create(placeImage as View,
        <span class="hljs-string">
            "tImage"
        </span>
        ) val holderPair = Pair.create(placeNameHolder as View,
        <span class="hljs-string">
            "tNameHolder"
        </span>
        )
        <span class="hljs-comment">
            // 3
        </span>
        val navPair = Pair.create(navigationBar, Window.NAVIGATION_BAR_BACKGROUND_TRANSITION_NAME)
        val statusPair = Pair.create(statusBar, Window.STATUS_BAR_BACKGROUND_TRANSITION_NAME)
        val toolbarPair = Pair.create(toolbar as View,
        <span class="hljs-string">
            "tActionBar"
        </span>
        )
        <span class="hljs-comment">
            // 4
        </span>
        val pairs = mutableListOf(imagePair, holderPair, statusPair, toolbarPair)
        <span class="hljs-keyword">
            if
        </span>
        (navigationBar !=
        <span class="hljs-keyword">
            null
        </span>
        &amp;&amp; navPair !=
        <span class="hljs-keyword">
            null
        </span>
        ) { pairs += navPair }
        <span class="hljs-comment">
            // 5
        </span>
        val options = ActivityOptionsCompat.makeSceneTransitionAnimation(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-meta">
            @MainActivity
        </span>
        , *pairs.toTypedArray()) ActivityCompat.startActivity(
        <span class="hljs-keyword">
            this
        </span>
        <span class="hljs-meta">
            @MainActivity
        </span>
        , transitionIntent, options.toBundle()) } }
    </pre>
    <p>
        The differences between the original implementation and this one are thus:
    </p>
    <ol>
        <li>
            You've renamed the intent to provide more context;
        </li>
        <li>
            You get references to both the navigation bar and status bar;
        </li>
        <li>
            You've created three new instances of
            <code>
                Pair
            </code>
            - one for the navigation bar, one for the status bar, and one for the
            toolbar;
        </li>
        <li>
            You've protected against an IllegalArgumentException that occurs on certain
            devices, such as the Galaxy Tab S2, on which
            <code>
                navPair
            </code>
            is null.
        </li>
        <li>
            And finally you've updated the options that are passed to the new activity
            to include the references to the new views. You've used the Kotlin spread
            operator
            <code>
                *
            </code>
            on
            <code>
                pairs
            </code>
            , after changing it to a typed array.
        </li>
    </ol>
    <p>
        Great! Build and run, and you’ll see a much smoother animation:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-37-20-transition3.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-37-20-transition3.gif"
            alt="" width="282" height="500" class="aligncenter size-large wp-image-168964">
        </a>
    </p>
    <p>
        Now if you tap on a row under the action/toolbar or navigation bar, it
        doesn't jump before the transition; it transitions with the rest of the
        shared elements, which is much more pleasing to the eye. Switch to the
        grid view and you'll notice that the transitions work very nicely with
        that layout as well.
    </p>
    <p>
        Ta-da! Here is a video of the final app in action:
    </p>
    <div style="width: 206px;" class="wp-video">
        <!--[if lt IE 9]>
            <script>
                document.createElement('video');
            </script>
        <![endif]-->
        <span class="mejs-offscreen">
            Video Player
        </span>
        <div id="mep_0" class="mejs-container svg wp-video-shortcode mejs-video"
        tabindex="0" role="application" aria-label="Video Player" style="width: 206px; height: 367px;">
            <div class="mejs-inner">
                <div class="mejs-mediaelement">
                    <video class="wp-video-shortcode" id="video-168916-1" width="206" height="367"
                    preload="metadata" style="width: 100%; height: 100%;" src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-46-11-video.mp4?_=1">
                        <source type="video/mp4" src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-46-11-video.mp4?_=1">
                            <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-46-11-video.mp4">
                                https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-46-11-video.mp4
                            </a>
                    </video>
                </div>
                <div class="mejs-layers">
                    <div class="mejs-poster mejs-layer" style="display: none; width: 100%; height: 100%;">
                    </div>
                    <div class="mejs-overlay mejs-layer" style="display: none; width: 100%; height: 100%;">
                        <div class="mejs-overlay-loading">
                            <span>
                            </span>
                        </div>
                    </div>
                    <div class="mejs-overlay mejs-layer" style="display: none; width: 100%; height: 100%;">
                        <div class="mejs-overlay-error">
                        </div>
                    </div>
                    <div class="mejs-overlay mejs-layer mejs-overlay-play" style="width: 100%; height: 100%;">
                        <div class="mejs-overlay-button">
                        </div>
                    </div>
                </div>
                <div class="mejs-controls">
                    <div class="mejs-button mejs-playpause-button mejs-play">
                        <button type="button" aria-controls="mep_0" title="Play" aria-label="Play">
                        </button>
                    </div>
                    <div class="mejs-time mejs-currenttime-container" role="timer" aria-live="off">
                        <span class="mejs-currenttime">
                            00:00
                        </span>
                    </div>
                    <div class="mejs-time-rail" style="width: 55px;">
                        <span class="mejs-time-total mejs-time-slider" style="width: 45px;" aria-label="Time Slider"
                        aria-valuemin="0" aria-valuemax="NaN" aria-valuenow="0" aria-valuetext="00:00"
                        role="slider" tabindex="0">
                            <span class="mejs-time-buffering" style="display: none;">
                            </span>
                            <span class="mejs-time-loaded">
                            </span>
                            <span class="mejs-time-current">
                            </span>
                            <span class="mejs-time-handle">
                            </span>
                            <span class="mejs-time-float">
                                <span class="mejs-time-float-current">
                                    00:00
                                </span>
                                <span class="mejs-time-float-corner">
                                </span>
                            </span>
                        </span>
                    </div>
                    <div class="mejs-time mejs-duration-container">
                        <span class="mejs-duration">
                            00:00
                        </span>
                    </div>
                    <div class="mejs-button mejs-volume-button mejs-mute">
                        <button type="button" aria-controls="mep_0" title="Mute" aria-label="Mute">
                        </button>
                        <a href="javascript:void(0);" class="mejs-volume-slider" style="display: none;"
                        aria-label="Volume Slider" aria-valuemin="0" aria-valuemax="100" aria-valuenow="80"
                        aria-valuetext="80%" role="slider" tabindex="0">
                            <span class="mejs-offscreen">
                                Use Up/Down Arrow keys to increase or decrease volume.
                            </span>
                            <div class="mejs-volume-total">
                            </div>
                            <div class="mejs-volume-current" style="height: 80px; top: 28px;">
                            </div>
                            <div class="mejs-volume-handle" style="top: 25px;">
                            </div>
                        </a>
                    </div>
                    <div class="mejs-button mejs-fullscreen-button">
                        <button type="button" aria-controls="mep_0" title="Fullscreen" aria-label="Fullscreen">
                        </button>
                    </div>
                </div>
                <div class="mejs-clear">
                </div>
            </div>
        </div>
    </div>
    <h2>
        Where to Go From Here?
    </h2>
    <div class="inline-video-ad" id="sub-banner-inline">
        <div class="inline-video-ad-wrapper">
            <a href="https://videos.raywenderlich.com/courses">
                <div class="col-wrapper">
                    <div class="col">
                        <img src="https://koenig-assets.raywenderlich.com/wp-content/themes/raywenderlich/images/global/video-yeti@2x.png"
                        alt="yeti holding videos">
                    </div>
                    <div class="col large-col">
                        <span>
                            Want to learn even faster? Save time with our
                            <span>
                                video courses
                            </span>
                        </span>
                    </div>
                </div>
            </a>
        </div>
    </div>
    <p>
        Be proud of yourself: You’ve created a full-blown Android material app!
        To challenge yourself, try the following:
    </p>
    <ul>
        <li>
            Use
            <code>
                StaggeredLayoutManager
            </code>
            to make a grid with three columns instead of two.
        </li>
        <li>
            Experiment with the
            <code>
                Palette
            </code>
            API in both
            <code>
                MainActivity
            </code>
            and
            <code>
                DetailActivity
            </code>
            using different palette options.
        </li>
        <li>
            Add a button on the place list and transition it to the detail view as
            a shared element—perhaps a favorite button.
        </li>
        <li>
            Make those transitioning animations even cooler—check out Android's Newsstand
            app and see how it transitions from a grid to a detail view with the reveal
            animation. You have all the code here to replicate that.
        </li>
        <li>
            Try to create all the morphing animations you did here, but using
            <code>
                animated-vectors
            </code>
            .
        </li>
    </ul>
    <p>
        And of course, apply this knowledge to your apps so that they can be as
        cool as this one. :]
    </p>
    <p>
        To find out more about Material Design then be sure to check out Google's
        recently redesigned
        <a href="https://design.google/" target="_blank">
            Google Design
        </a>
        website.
    </p>
    <p>
        You can get the completed project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/travelwishlist-final-2.zip">
            here
        </a>
        .
    </p>
</div>