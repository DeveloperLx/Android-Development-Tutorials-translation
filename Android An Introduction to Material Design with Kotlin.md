# Android：质感设计的介绍 - Kotlin
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
            质感设计 - Kotlin！
        </p>
    </div>
    <p>
        Google的质感设计可以帮助你带给用户精美的Android app。但稍等-神马是质感设计？
    </p>
    <p>
        Google将其描述为一个界面，结合 触觉的表面，粗体的图形设计和流畅的动作，创造出美丽，直观的体验。质感设计是Android app的“用户体验哲学”！
    </p>
    <p>
        在本教程中，你会将质感设计植入到一个叫做Travel Wishlist的app中。通过这个过程你会学习到：
    </p>
    <ul>
        <li>
            实现质感主题；
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
        现在一切都是空的！你会添加一些质感的组件到它上面，包括动态的view，颜色方案和动画，来真正地完善这些照片。
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
        依赖声明好之后，就该将质感设计迁移到你的app中了！
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
        发生了一些微妙的变化，但就像你的旅行愿望清单一样，提升设计始于此步！
    </p>
    <h2>
        使用RecyclerView和CardView
    </h2>
    <p>
        为了给你的用户一个窗口，以方便他们到每个想去的地方，你需要一个view。你可以使用
        <code>
            RecyclerView
        </code>
        来替换
        <code>
            ListView
        </code>
        ，它具有更加通用的特性。Google将
        <code>
            RecyclerView
        </code>
        描述为“为大型的数据集提供有限窗口的一个灵活的view”。在本节中，你将会看到，如何通过使用相同的数据源（包含的是用户的位置），将一个列表的view切换为自定义的网格的view。
    </p>
    <h3>
        在XML中实现Recycler View
    </h3>
    <p>
        首先，打开
        <em>
            activity_main.xml
        </em>
        并添加下列代码到
        <code>
            LinearLayout
        </code>
        标签中：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.RecyclerView</span>
  <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/list"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:background</span>=<span class="hljs-string">"@color/light_gray"</span>/&gt;</span>
</pre>
    <p>
        这里就添加了一个
        <code>
            RecyclerView
        </code>
        到activity的布局中，并将它指定为填满整个父view的尺寸。
    </p>
    <h3>
        初始化Recycler View并提供Layout Manager
    </h3>
    <p>
        在添加Kotlin代码之前，配置Android Studio，来让它可以自动地插入import语句，来节约你必须每次手动添加所耗费的时间。
    </p>
    <p>
        打开
        <em>
            Preferences/Editor/General/Auto Import
        </em>
        并选择
        <em>
            Add unambiguous imports on the fly
        </em>
        勾选框。在
        <em>
            MainActivity.kt
        </em>
        中，添加下列的代码到类的顶部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> staggeredLayoutManager: StaggeredGridLayoutManager
</pre>
    <p>
        这里你声明了一个property来持有对
        <code>
            LayoutManager
        </code>
        的引用。
    </p>
    <p>
        接下来，添加下列代码到
        <code>
            onCreate()
        </code>
        的底部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">staggeredLayoutManager = StaggeredGridLayoutManager(<span class="hljs-number">1</span>, StaggeredGridLayoutManager.VERTICAL)
list.layoutManager = staggeredLayoutManager
</pre>
    <p>
        在上述代码中，你将
        <code>
            RecyclerView
        </code>
        的layout manager设置为
        <code>
            StaggeredGridLayoutManager
        </code>
        ，用来创建两种类型的竖直交错的网格。这里我们从第一种类型开始，传参
        <code>
            1
        </code>
        作为span数，
        <code>
            StaggeredGridLayoutManager.VERTICAL
        </code>
        作为方向。将span数设置为1，即可将其设定为一个列表而不是网格，你很快就会看到。然后，你还会添加一个带有两列的紧凑型的网格。
    </p>
    <p>
        注意你使用了
        <em>
            Kotlin Android Extensions
        </em>
        来查找
        <code>
            list
        </code>
        ，因此无需再调用
        <code>
            findViewById()
        </code>
        。确认下面这行代码已添加到了你的import语句中，这样就可以在
        <code>
            list
        </code>
        输入的时候自动地添加它了：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> kotlinx.android.synthetic.main.activity_main.*
</pre>
    <h3>
        使用Card View来创建行和单元格
    </h3>
    <p>
        <code>
            CardView
        </code>
        为view提供了统一的背景，包括圆角和阴影。你将通过它来实现
        <code>
            RecyclerView
        </code>
        的行和单元格。默认情况下，
        <code>
            CardView
        </code>
        继承自
        <code>
            FrameLayout
        </code>
        ，因此包含了持有其子view的能力。
    </p>
    <p>
        在
        <em>
            res\layout
        </em>
        目录下，创建一个新的
        <em>
            Layout resource文件 file
        </em>
        并将其命名为
        <em>
            row_places.xml
        </em>
        。按下
        <em>
            OK
        </em>
        来完成创建。
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
        为创建期望中的布局，将该文件中的所有内容替换为如下代码：
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
        通过添加
        <code>
            xmlns:card_view="http://schemas.android.com/apk/res-auto"
        </code>
        ，你就可以定义类似
        <code>
            card_view:cardCornerRadius
        </code>
        的属性，及给质感设计
        <code>
            card_view:cardElevation
        </code>
        提供Android app中类似签名卡片般的效果。
    </p>
    <p>
        注意
        <code>
            mainHolder
        </code>
        ，你已添加了
        <code>
            ?android:selectableItemBackground
        </code>
        作为背景。这就打开了用户在点击单元格的时的
        <i>
            ripple
        </i>
        动画效果，就像现在很多Android app中看到的一样。你马上就会眼见为实地看到它了。
    </p>
    <h3>
        为Recycler View实现一个Adapter
    </h3>
    <p>
        你将为
        <code>
            RecyclerView
        </code>
        通过一个adapter将数据绑定到view上。在
        <em>
            main/java
        </em>
        目录下，右击
        <em>
            package com.raywenderlich.android.travelwishlist
        </em>
        这个包并选择
        <em>
            New/Kotline File/Class
        </em>
        。将类命名为
        <em>
            TravelListAdapter
        </em>
        。
    </p>
    <p>
        添加下列的代码到类中，注意保留文件顶部的package语句：
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
        上述代码执行了如下的动作：
    </p>
    <ol>
        <li>
            让
            <code>
                TravelListAdapter
            </code>
            继承自
            <code>
                Recycler.Adapter
            </code>
            ，以便在之后覆盖其方法来实现你自己的逻辑。并将构造器设置为带有一个
            <code>
                Context
            </code>
            参数，你会在
            <code>
                MainActivity
            </code>
            中创建
            <code>
                TravelListAdapter
            </code>
            实例时进行传参，以便在本教程之后的部分执行更多的操作。
        </li>
        <li>
            创建
            <code>
                ViewHolder
            </code>
            类。尽管在
            <code>
                ListView
            </code>
            中，
            <code>
                ViewHolder
            </code>
            模式是可选的，但在
            <code>
                RecyclerView
            </code>
            中却必须执行。这样可以通过避免对每一个单元格都调用
            <code>
                findViewById()
            </code>
            来提升滚动的性能。
        </li>
    </ol>
    <p>
        在
        <code>
            TravelListAdapter
        </code>
        中将
        <code>
            RecyclerView.Adapter
        </code>
        的方法更新为如下的样子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getItemCount</span><span class="hljs-params">()</span></span> = PlaceData.placeList().size

<span class="hljs-comment">// 2</span>
<span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateViewHolder</span><span class="hljs-params">(parent: <span class="hljs-type">ViewGroup</span>, viewType: <span class="hljs-type">Int</span>)</span></span>: ViewHolder {
  <span class="hljs-keyword">val</span> itemView = LayoutInflater.from(parent.context).inflate(R.layout.row_places, parent, <span class="hljs-literal">false</span>)
  <span class="hljs-keyword">return</span> ViewHolder(itemView)
}

<span class="hljs-comment">// 3</span>
<span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onBindViewHolder</span><span class="hljs-params">(holder: <span class="hljs-type">ViewHolder</span>, position: <span class="hljs-type">Int</span>)</span></span> {
  <span class="hljs-keyword">val</span> place = PlaceData.placeList()[position]
  holder.itemView.placeName.text = place.name
  Picasso.with(context).load(place.getImageResourceId(context)).into(holder.itemView.placeImage)
}
</pre>
    <p>
        上述代码：
    </p>
    <ol>
        <li>
            <code>
                getItemCount()
            </code>
            会基于你的数据数组返回item的数量。在本例中，你使用的就是
            <code>
                PlaceData.placeList()
            </code>
            的数量。
        </li>
        <li>
            <code>
                onCreateViewHolder(...)
            </code>
            通过传参一个
            <code>
                row_places
            </code>
            的inflated的view，来返回一个
            <code>
                ViewHolder
            </code>
            的新的实例。
        </li>
        <li>
            <code>
                onBindViewHolder(...)
            </code>
            在
            <code>
                ViewHolder
            </code>
            中绑定了
            <code>
                Place
            </code>
            对象到相应的UI元素上。你将使用Picasso来为列表缓存图片。            
        </li>
    </ol>
    <p>
        在
        <code>
            MainActivity
        </code>
        中添加一个字段来持有你的adapter的引用：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> adapter: TravelListAdapter
</pre>
    <p>
        然后在
        <code>
            onCreate()
        </code>
        的底部，配置layout manager的后边，创建这个adapter的实例，并将其传递给
        <code>
            RecyclerView
        </code>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">adapter = TravelListAdapter(<span class="hljs-keyword">this</span>)
list.adapter = adapter
</pre>
    <p>
        现在运行app，你就会看到一个由place填充的列表。
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
        哪个地方正在呼唤你的名字？我喜欢那汪蓝绿色的水。但无论想去哪里，你都可以在这里记录想要做的事以耕耘你的梦想。首先，你需要让这些单元格可以响应用户的点击事件。
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
        为每个单元格实现点击事件的接口
    </h3>
    <p>
        和
        <code>
            ListView
        </code>
        不同，
        <code>
            RecyclerView
        </code>
        并没有提供
        <code>
            onItemClick
        </code>
        的接口，因此你必须在adapter中来实现它。在
        <code>
            TravelListAdapter
        </code>
        中，创建一个property来持有
        <code>
            OnItemClickListener
        </code>
        的实例。添加下列的代码到
        <code>
            TravelListAdapter
        </code>
        的顶部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> itemClickListener: OnItemClickListener
</pre>
    <p>
        现在，通过添加interface到
        <code>
            ViewHolder
        </code>
        的内部类的声明中，来实现
        <code>
            View.OnClickListener
        </code>
        ，就像下面这样：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">inner <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ViewHolder</span></span>(itemView: View) : RecyclerView.ViewHolder(itemView), View.OnClickListener {
</pre>
    <p>
        然后添加下列的方法到
        <code>
            ViewHolder
        </code>
        的内部类中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onClick</span><span class="hljs-params">(view: <span class="hljs-type">View</span>)</span></span> {      

}
</pre>
    <p>
        添加下列的
        <code>
            init
        </code>
        块到
        <code>
            ViewHolder
        </code>
        的顶部来设置listener：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">init {
  itemView.placeHolder.setOnClickListener(<span class="hljs-keyword">this</span>)
}
</pre>
    <p>
        这样，你就为
        <code>
            placeHolder
        </code>
        初始化了
        <code>
            setOnClickListener
        </code>
        并实现
        <code>
            onClick
        </code>
        这个覆盖的方法。
    </p>
    <p>
        你还需要做几件事来为
        <code>
            RecyclerView
        </code>
        实现
        <code>
            onClick
        </code>
        接口。在内部类
        <code>
            ViewHolder
        </code>
        的声明之后添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">OnItemClickListener</span> </span>{
  <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onItemClick</span><span class="hljs-params">(view: <span class="hljs-type">View</span>, position: <span class="hljs-type">Int</span>)</span></span>
}
</pre>
    <p>
        然后，添加
        <code>
            onClickListener
        </code>
        的setter方法到
        <code>
            TravelListAdapter
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setOnItemClickListener</span><span class="hljs-params">(itemClickListener: <span class="hljs-type">OnItemClickListener</span>)</span></span> {
  <span class="hljs-keyword">this</span>.itemClickListener = itemClickListener
}
</pre>
    <p>
        现在，在
        <code>
            onClick()
        </code>
        方法中实现逻辑：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onClick</span><span class="hljs-params">(view: <span class="hljs-type">View</span>)</span></span> = itemClickListener.onItemClick(itemView, adapterPosition)
</pre>
    <p>
        在
        <code>
            MainActivity
        </code>
        中，
        <code>
            onCreate()
        </code>
        方法上方创建一个
        <code>
            OnItemClickListener
        </code>
        的实例：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> onItemClickListener = <span class="hljs-keyword">object</span> : TravelListAdapter.OnItemClickListener {
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onItemClick</span><span class="hljs-params">(view: <span class="hljs-type">View</span>, position: <span class="hljs-type">Int</span>)</span></span> {
    Toast.makeText(<span class="hljs-keyword">this</span><span class="hljs-symbol">@MainActivity</span>, <span class="hljs-string">"Clicked "</span> + position, Toast.LENGTH_SHORT).show()
  }
}
</pre>
    <p>
        最后，通过添加下列的代码到
        <code>
            onCreate()
        </code>
        的底部，来为adapter设置listener，就在你设置adapter之后的地方：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">adapter.setOnItemClickListener(onItemClickListener)
</pre>
    <p>
        运行项目。现在当你点击每行的时候，就会看到一个ripple的效果，以及一个Toast的通知来展示单元格在列表当中的位置。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-38-08.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-38-08.gif"
            alt="" width="280" height="500" class="aligncenter size-large wp-image-168940">
        </a>
    </p>
    <h3>
        从列表到网页，再回头
    </h3>
    <p>
        <code>
            StaggeredLayoutManager
        </code>
        可以丰富你的布局。要将这个列表修改为更加紧凑的两列网格的形式，只需修改
        <code>
            StaggeredLayoutManager
        </code>
        中的
        <code>
            spanCount
        </code>
        。
    </p>
    <p>
        在
        <code>
            toggle()
        </code>
        中，添加下列的代码到
        <code>
            showGridView()
        </code>
        顶部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">staggeredLayoutManager.spanCount = <span class="hljs-number">2</span>
</pre>
    <p>
        并添加下列的代码到
        <code>
            showListView()
        </code>
        的顶部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">staggeredLayoutManager.spanCount = <span class="hljs-number">1</span>
</pre>
    <p>
        这里仅仅是改变了span的数量，就相应地展示了单列和多列的内容。
    </p>
    <p>
        运行项目，并使用动作按钮来在列表和网格形式的视图之间进行切换。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-46-24-toggle.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-22-46-24-toggle.gif"
            alt="" width="282" height="500" class="aligncenter size-full wp-image-168943">
        </a>
    </p>
    <h2>
        使用列表中的Palette API
    </h2>
    <p>
        现在你可以添加一些有趣的材质设计特性到mix中，从Palette的API开始。返回到
        <code>
            TravelListAdapter
        </code>
        ，在这里为
        <code>
            placeNameHolder
        </code>
        定义一个背景颜色，它会基于图片中的颜色进行动态地确定。
    </p>
    <p>
        添加下列的代码到
        <code>
            onBindViewHolder(...)
        </code>
        底部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> photo = BitmapFactory.decodeResource(context.resources, place.getImageResourceId(context))
Palette.from(photo).generate { palette -&gt;
  <span class="hljs-keyword">val</span> bgColor = palette.getMutedColor(ContextCompat.getColor(context, android.R.color.black))
  holder.itemView.placeNameHolder.setBackgroundColor(bgColor)
}
</pre>
    <p>
        <code>
            generate(...)
        </code>
        方法会在后台创建一个调色板，并传入一个lambda，它会在palette生成的时候被调用。这里你可以访问生成的颜色palette，来设置
        <code>
            holder.itemView.placeNameHolder
        </code>
        的背景颜色。如果这个颜色不存在，这个方法就会采用一个兜底的颜色 - 本例中为
        <code>
            android.R.color.black
        </code>
        。
    </p>
    <p>
        运行项目来眼见为实地查看Palette API！
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
            注意：
        </em>
        <p>
            Palette API可以从图片中抽取下列的颜色配置：
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
            建议你对它们进行尝试，将
            <code>
                palette.getMutedColor(...)
            </code>
            替换为
            <code>
                palette.getVibrantColor(...)
            </code>
            ，
            <code>
                palette.getDarkVibrantColor(...)
            </code>
            等。
        </p>
    </div>
    <h2>
        使用新的质感API
    </h2>
    <p>
        在本节，你会在
        <code>
            DetailActivity
        </code>
        和它相应的
        <code>
            activity_detail
        </code>
        布局上，通过使用一些新的质感设计API来让它变得更酷。
    </p>
    <p>
        首先，你希望看到在起始项目中的详情视图的样子。添加下列的代码到
        <code>
            DetailActivity
        </code>
        的companion object中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">newIntent</span><span class="hljs-params">(context: <span class="hljs-type">Context</span>, position: <span class="hljs-type">Int</span>)</span></span>: Intent {
  <span class="hljs-keyword">val</span> intent = Intent(context, DetailActivity::<span class="hljs-class"><span class="hljs-keyword">class</span>.<span class="hljs-title">java</span>)</span>
  intent.putExtra(EXTRA_PARAM_ID, position)
  <span class="hljs-keyword">return</span> intent
}
</pre>
    <p>
        然后，切到
        <code>
            MainActivity
        </code>
        ，使用下列的代码替换
        <code>
            onItemClick(...)
        </code>
        方法中的
        <code>
            Toast
        </code>
        语句：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">startActivity(DetailActivity.newIntent(<span class="hljs-keyword">this</span><span class="hljs-symbol">@MainActivity</span>, position))
</pre>
    <p>
        你可以通过intent来传递place对象的位置，这样
        <code>
            DetailActivity
        </code>
        就可以检索相应的信息用来布局界面。这就是这里所做的事。
    </p>
    <p>
        运行项目。
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
        现在还没有什么令人激动的（
        <i>
            但是！
        </i>
        ），你为之后的工作打下了一个很好的基础，方便去添加那些令人期待的质感设计API。你还可以看到一个很酷的
        <code>
            FloatingActionButton
        </code>
        ，它是有质感设计所引入的组件之一。
    </p>
    <h3>
        添加展现动画
    </h3>
    <p>
        现在我们想让用户可以添加关于他们想在这些美好景点想做的事的笔记。这里
        <em>
            activity_detail.xml
        </em>
        已有了一个默认隐藏的
        <code>
            edittext
        </code>
        。当用户点击FAB的时候，它就可以通过下面这样的动画的形式来展现出来：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-23-38-19-reveal.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-19-2017-23-38-19-reveal.gif"
            alt="" width="412" height="248" class="aligncenter size-full wp-image-168954">
        </a>
    </p>
    <p>
        打开
        <code>
            DetailActivity
        </code>
        。你需要在这里实现两个方法：
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
        首先，添加下列的代码到
        <code>
            revealEditText()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> cx = view.right - <span class="hljs-number">30</span>
<span class="hljs-keyword">val</span> cy = view.bottom - <span class="hljs-number">60</span>
<span class="hljs-keyword">val</span> finalRadius = Math.max(view.width, view.height)
<span class="hljs-keyword">val</span> anim = ViewAnimationUtils.createCircularReveal(view, cx, cy, <span class="hljs-number">0</span>f, finalRadius.toFloat())
view.visibility = View.VISIBLE
isEditTextVisible = <span class="hljs-literal">true</span>
anim.start()
</pre>
    <p>
        通过两个
        <code>
            int
        </code>
        的值获取到view的
        <code>
            x
        </code>
        和
        <code>
            y
        </code>
        的位置，并带有些微的偏移。这个偏移就造就了展现效果是从你FAB按钮处发生的效果。
    </p>
    <p>
        接下来，radius则给出了展现圆形的轮廓，就像你在上面的GIF动画中看到的一样。所有的这些值 - x位置，y位置，半径 - 你都会传入到动画实例中。这个动画使用了
        <code>
            ViewAnimationUtils
        </code>
        ，它可以帮助你来创建圆形展现效果的动画。
    </p>
    <p>
        由于
        <code>
            EditText
        </code>
        view开始时是隐藏的，因此将它的visibility设置为
        <code>
            VISIBLE
        </code>
        比将
        <code>
            isEditTextVisible
        </code>
        设为
        <code>
            true
        </code>
        。最后，调用animation对象的
        <code>
            start()
        </code>
        方法。
    </p>
    <p>
        为了隐藏view，添加下列的代码到
        <code>
            hideEditText()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> cx = view.right - <span class="hljs-number">30</span>
<span class="hljs-keyword">val</span> cy = view.bottom - <span class="hljs-number">60</span>
<span class="hljs-keyword">val</span> initialRadius = view.width
<span class="hljs-keyword">val</span> anim = ViewAnimationUtils.createCircularReveal(view, cx, cy, initialRadius.toFloat(), <span class="hljs-number">0</span>f)
anim.addListener(<span class="hljs-keyword">object</span> : AnimatorListenerAdapter() {
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onAnimationEnd</span><span class="hljs-params">(animation: <span class="hljs-type">Animator</span>)</span></span> {
    <span class="hljs-keyword">super</span>.onAnimationEnd(animation)
    view.visibility = View.INVISIBLE
  }
})
isEditTextVisible = <span class="hljs-literal">false</span>
anim.start()
</pre>
    <p>
        这里你的目标是隐藏view，并以相反的方向来展现圆形动画。因此，你将初始的半径设置为view的宽度，截止的则为0，这样就可以将圆形缩小了。
    </p>
    <p>
        你想要首先展示动画，然后再将view因此。为了做到这点，需要实现一个动画监听器，在动画结束的时候隐藏view。
    </p>
    <p>
        现在运行项目实际地参看动画！
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
                注意
            </em>
            ：如果键盘自己弹出来了，你需要显式地将它隐藏以便无阻碍地查看效果。注释掉
            <code>
                DetailActivity
            </code>
            中的
            <code>
                inputManager.showSoftInput(...)
            </code>
            ，但不要忘记取消注释。哦，不必担心你的按钮现在还未出现加号，你很快就会修复它。
        </p>
    </div>
    <h3>
        为浮动的动作按钮创建变换的贝塞尔路径
    </h3>
    <p>
        现在你已有了展现的动画来隐藏和展示编辑edit text field，你可以协调FAB上的图标，就像下面这样：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-58-26-scuba.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-58-26-scuba.gif"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168973">
        </a>
    </p>
    <p>
        起始的项目已包含了加号和对勾图标的矢量路径。你将学习如何动画 - 变形 - 从加号到对勾，以及相反的方向。
    </p>
    <p>
        在
        <em>
            res/drawables
        </em>
        目录下，通过
        <em>
            New/Drawable resource file
        </em>
        创建一个新的资源文件。将它命名为
        <em>
            icn_morph
        </em>
        并声明
        <code>
            animated-vector
        </code>
        作为根元素：
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">animated-vector</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">android:drawable</span>=<span class="hljs-string">"@drawable/icn_add"</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">animated-vector</span>&gt;</span>
</pre>
    <p>
        <code>
            animated-vector
        </code>
        需要一个已存在的
        <code>
            android:drawable
        </code>
        。在本例中，动画向量会从一个加号开始，逐渐变形为一个对号，因此你将drawable设置为
        <code>
            icn_add
        </code>
        。
    </p>
    <p>
        现在为了实际的变形效果，添加下列的内容到
        <code>
            animated-vector
        </code>
        的tag中：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">target</span>
  <span class="hljs-attr">android:animation</span>=<span class="hljs-string">"@anim/path_morph"</span>
  <span class="hljs-attr">android:name</span>=<span class="hljs-string">"sm_vertical_line"</span> /&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">target</span>
  <span class="hljs-attr">android:animation</span>=<span class="hljs-string">"@anim/path_morph_lg"</span>
  <span class="hljs-attr">android:name</span>=<span class="hljs-string">"lg_vertical_line"</span> /&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">target</span>
  <span class="hljs-attr">android:animation</span>=<span class="hljs-string">"@anim/fade_out"</span>
  <span class="hljs-attr">android:name</span>=<span class="hljs-string">"horizontal_line"</span> /&gt;</span>
</pre>
    <p>
        通过以上的代码，你就可以将加号中垂直的线转化成一个对勾，并将水平的线消失掉，就像下面的这张图所表示的一样：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM.png">
            <img class="aligncenter size-large wp-image-104111" src="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM-700x444.png"
            alt="Screen Shot 2015-04-22 at 12.59.57 AM" width="700" height="444" srcset="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM-700x444.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM-480x305.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-12.59.57-AM.png 778w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        此外，垂直的这条线包含了两条路径，一条较短，一条较长：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM.png">
            <img class="aligncenter size-large wp-image-104116" src="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM-700x337.png"
            alt="Screen Shot 2015-04-22 at 1.11.49 AM" width="700" height="337" srcset="https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM-700x337.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM-480x231.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/04/Screen-Shot-2015-04-22-at-1.11.49-AM.png 778w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        从上面的图表中可以看到，我们可以将前两个target，
        <code>
            sm_vertical_line
        </code>
        和
        <code>
            lg_vertical_line
        </code>
        ，通过在不同的角度下绘制来转换一个对勾，也就是你在前一个代码块中所做的事。
    </p>
    <p>
        接下来，则需要做相反的动作，把对勾转换为一个加号。创建另一个drawable资源文件，名为
        <em>
            icn_morph_reverse
        </em>
        ，并将其内容替换为下列的代码：
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">animated-vector</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">android:drawable</span>=<span class="hljs-string">"@drawable/icn_add"</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">target</span>
    <span class="hljs-attr">android:animation</span>=<span class="hljs-string">"@anim/path_morph_reverse"</span>
    <span class="hljs-attr">android:name</span>=<span class="hljs-string">"sm_vertical_line"</span>/&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">target</span>
    <span class="hljs-attr">android:animation</span>=<span class="hljs-string">"@anim/path_morph_lg_reverse"</span>
    <span class="hljs-attr">android:name</span>=<span class="hljs-string">"lg_vertical_line"</span> /&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">target</span>
    <span class="hljs-attr">android:animation</span>=<span class="hljs-string">"@anim/fade_in"</span>
    <span class="hljs-attr">android:name</span>=<span class="hljs-string">"horizontal_line"</span> /&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">animated-vector</span>&gt;</span>
</pre>
    <p> 
        构成加号竖线的两条线现在将转化回它们原始的状态，水平的线则会逐渐出现在view中，以此来创建一个平滑的效果。
    </p>
    <p>
        现在，为了完成动画。打开
        <em>
            DetailActivity.kt
        </em>
        并添加下列的代码到
        <code>
            onClick()
        </code>
        中，就在
        <code>
            if
        </code>
        分支中，else之前：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">addButton.setImageResource(R.drawable.icn_morph)
<span class="hljs-keyword">val</span> animatable = addButton.drawable <span class="hljs-keyword">as</span> Animatable
animatable.start()
</pre>
    <p>
        这里将按钮的图片资源设置为你之前创建的
        <code>
            icn_morph
        </code>
        drawable文件，从中来提取并开始动画。
    </p>
    <p>
        最后，添加下列的代码到
        <code>
            else
        </code>
        分支的尾部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">addButton.setImageResource(R.drawable.icn_morph_reverse)
<span class="hljs-keyword">val</span> animatable = addButton.drawable <span class="hljs-keyword">as</span> Animatable
animatable.start()
</pre>
    <p>
        这里基本和之前的一步完全一致，除了将图片资源设置为
        <code>
            icn_morph_reverse
        </code>
        ，这样动画就会以相反的方向来进行播放。
    </p>
    <p>
        在变化图标的同时，用户的点击还会将
        <code>
            todoText
        </code>
        中的问题添加到
        <code>
            toDoAdapter
        </code>
        中，并刷新place活动列表。由于文本现在还是白色的，我们无法看到。在下一节中，你会添加生动的颜色到view上，这样文本就会展现出来了。
    </p>
    <p>
        运行项目，欣赏魔法般的展现效果！点击FAB按钮，就会让它在对勾和加号的图标之间进行变换。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-04-13-morph.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-04-13-morph.gif"
            alt="" width="283" height="500" class="aligncenter size-large wp-image-168957">
        </a>
    </p>
    <h3>
        使用Palette API添加动态的颜色到View上
    </h3>
    <p>
        现在该使用Palette API来添加颜色到这个view上了。和之前的颜色不同，这里将会是动态的颜色！
    </p>
    <p>
        在
        <code>
            DetailActivity
        </code>
        中，添加下列的代码来充实
        <code>
            colorize()
        </code>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> palette = Palette.from(photo).generate()
applyPalette(palette)
</pre>
    <p>
        就像你在之前所做的一样，从一张照片中来生成一个palette - 尽管这次你是同步地完成了它 - 然后将这个palette传递给
        <code>
            applyPalette()
        </code>
        。将已存在的方法
        <code>
            applyPalette()
        </code>
        替换为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">applyPalette</span><span class="hljs-params">(palette: <span class="hljs-type">Palette</span>)</span></span> {
    window.setBackgroundDrawable(ColorDrawable(palette.getDarkMutedColor(defaultColor)))
    placeNameHolder.setBackgroundColor(palette.getMutedColor(defaultColor))
    revealView.setBackgroundColor(palette.getLightVibrantColor(defaultColor))
  }
</pre>
    <p>
        这里你使用了暗柔色，柔色及明亮色分别作为了窗口，标题的背景色。
    </p>
    <p>
        最后，为启动这一连串的事件，添加下列的代码到
        <code>
            getPhoto()
        </code>
        底部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">colorize(photo)
</pre>
    <p>
        再次运行app！你可以看到这个详情activity现在已使用了从相关图片的palette导出的颜色方案。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-18-55-colorize.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-18-55-colorize.gif"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168959">
        </a>
    </p>
    <h3>
        含有共享元素的Activity切换
    </h3>
    <p>
        我们都见过，并好奇Google app中那些使用质感设计的超赞的图片和文本过渡效果。好吧，无需再等了 - 你马上就会学到实现这些平滑动画效果的方法。
    </p>
    <div class="note">
        <em>
            注意
        </em>
        ：带有共享元素的Activity切换，让你可以在两个共享相同的view的activity之间进行切换。例如，你可以将一个列表中的缩略图过渡到详情activity中的大图，从而带给内容以连续性。
    </div>
    <p>
        在place列表view
        <code>
            MainActivity
        </code>
        ，及place详情view
        <code>
            DetailActivity
        </code>
        之间，你将会为下列的元素添加过渡效果：
    </p>
    <ul>
        <li>
            place的图片；
        </li>
        <li>
            place的标题；
        </li>
        <li>
            title的背景；
        </li>
    </ul>
    <p>
        打开
        <em>
            row_places.xml
        </em>
        并添加下列的代码到带有id为
        <code>
            placeImage
        </code>
        的
        <code>
            ImageView
        </code>
        的标签的声明中：
    </p>
    <pre lang="xml" class="language-xml hljs">android:transitionName="tImage"
</pre>
    <p>
        然后添加下列的代码到带有id为
        <code>
            placeNameHolder
        </code>
        的
        <code>
            LinearLayout
        </code>
        标签中：
    </p>
    <pre lang="xml" class="language-xml hljs">android:transitionName="tNameHolder"
</pre>
    <p>
        注意
        <code>
            placeName
        </code>
        并不包含过渡的名称。这是因为它是
        <code>
            placeNameHolder
        </code>
        的子代，它会为其所有的子view添加过渡效果。
    </p>
    <p>
        在
        <em>
            activity_detail.xml
        </em>
        中，添加一个
        <code>
            transitionName
        </code>
        到id为
        <code>
            placeImage
        </code>
        的
        <code>
            ImageView
        </code>
        标签下：
    </p>
    <pre lang="xml" class="language-xml hljs">android:transitionName="tImage"
</pre>
    <p>
        然后，以类似的方式，添加一个
        <code>
            transitionName
        </code>
        到id为
        <code>
            placeNameHolder
        </code>
        的
        <code>
            LinearLayout
        </code>
        标签下：
    </p>
    <pre lang="xml" class="language-xml hljs">android:transitionName="tNameHolder"
</pre>
    <p>
        想要在activity之间共享的添加过渡效果的元素，应当包含有相同的
        <code>
            android:transitionName
        </code>
        ，就像你在这里设置的一样。以及，注意图片的尺寸，还有
        <code>
            placeNameHolder
        </code>
        的高度要比在这个activity大得多。我们要在activity过渡时，为所有的布局变化添加动画效果，以此来提供很棒的视觉持续性。
    </p>
    <p>
        在
        <code>
            MainActivity
        </code>
        中的
        <code>
            onItemClickListener()
        </code>
        ，更新下列的方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onItemClick</span><span class="hljs-params">(view: <span class="hljs-type">View</span>, position: <span class="hljs-type">Int</span>)</span></span> {
  <span class="hljs-keyword">val</span> intent = DetailActivity.newIntent(<span class="hljs-keyword">this</span><span class="hljs-symbol">@MainActivity</span>, position)

  <span class="hljs-comment">// 1</span>
  <span class="hljs-keyword">val</span> placeImage = view.findViewById&lt;ImageView&gt;(R.id.placeImage)
  <span class="hljs-keyword">val</span> placeNameHolder = view.findViewById&lt;LinearLayout&gt;(R.id.placeNameHolder)

  <span class="hljs-comment">// 2</span>
  <span class="hljs-keyword">val</span> imagePair = Pair.create(placeImage <span class="hljs-keyword">as</span> View, <span class="hljs-string">"tImage"</span>)
  <span class="hljs-keyword">val</span> holderPair = Pair.create(placeNameHolder <span class="hljs-keyword">as</span> View, <span class="hljs-string">"tNameHolder"</span>)

  <span class="hljs-comment">// 3</span>
  <span class="hljs-keyword">val</span> options = ActivityOptionsCompat.makeSceneTransitionAnimation(<span class="hljs-keyword">this</span><span class="hljs-symbol">@MainActivity</span>,
    imagePair, holderPair)
  ActivityCompat.startActivity(<span class="hljs-keyword">this</span><span class="hljs-symbol">@MainActivity</span>, intent, options.toBundle())
}
</pre>
    <p>
        添加上述代码之后，你需要
        <em>
            手动地添加
        </em>
        下列的import语句到文件顶部，因为Android Studio无法自动判断需要那个package。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v4.util.Pair
</pre>
    <p>
        这里有一些事值得特别关注：
    </p>
    <ol>
        <li>
            对
            <code>
                RecyclerView
            </code>
            的给定位置，获取
            <code>
                placeImage
            </code>
            和
            <code>
                placeNameHolder
            </code>
            的实例。不能依赖Kotlin Android Extensions，因为你需要来自特定的
            <code>
                view
            </code>
            的
            <code>
                placeImage
            </code>
            和
            <code>
                placeNameHolder
            </code>
            。
        </li>
        <li>
            创建了一个包含view和
            <code>
                transitionName
            </code>
            的
            <a href="http://developer.android.com/reference/android/util/Pair.html"
            target="">
                <code>
                    Pair
                </code>
            </a>
            ，包含了图片和容纳文本的view。注意你需要再次手动添加下列的import语句到文件顶部：
            <code>
                android.support.v4.util.Pair
            </code>
        </li>
        <li>
            为了通过共享的view创建activity的场景转换，传入你的
            <code>
                Pair
            </code>
            实例，并使用你的
            <code>
                options
            </code>
            bundle来启动activity。
        </li>
    </ol>
    <p>
        运行项目，来查看图片从主activity到详情activity的过渡效果：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-45-50-transition.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-45-50-transition.gif"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-168960">
        </a>
    </p>
    <p>
        然而，这个动画在两个地方都有一点跳跃：
    </p>
    <ul>
        <li>
            FAB按钮会突然出现在
            <code>
                DetailActivity
            </code>
            中。
        </li>
        <li>
            如果你点击动作栏或导航栏之下的一行，该行在转换之前就会出现一点跳跃。
        </li>
    </ul>
    <p>
        首先来解决FAB按钮的问题。打开
        <em>
            DetailActivity.kt
        </em>
        并添加下列的代码到
        <code>
            windowTransition()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">window.enterTransition.addListener(<span class="hljs-keyword">object</span> : Transition.TransitionListener {
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onTransitionEnd</span><span class="hljs-params">(transition: <span class="hljs-type">Transition</span>)</span></span> {
    addButton.animate().alpha(<span class="hljs-number">1.0</span>f)
    window.enterTransition.removeListener(<span class="hljs-keyword">this</span>)
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onTransitionResume</span><span class="hljs-params">(transition: <span class="hljs-type">Transition</span>)</span></span> { }
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onTransitionPause</span><span class="hljs-params">(transition: <span class="hljs-type">Transition</span>)</span></span> { }
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onTransitionCancel</span><span class="hljs-params">(transition: <span class="hljs-type">Transition</span>)</span></span> { }
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onTransitionStart</span><span class="hljs-params">(transition: <span class="hljs-type">Transition</span>)</span></span> { }
})
</pre>
    <p>
        添加到过渡效果的监听器中的方法，将会在窗口过渡结束的时候被调用，此处用来给FAB按钮渐入的效果。因此你还需要在
        <em>
            activity_detail.xml
        </em>
        中将FAB的
        <code>
            alpha
        </code>
        值设置为
        <code>
            0
        </code>
        ：
    </p>
    <pre lang="xml" class="language-xml hljs">android:alpha="0.0"
</pre>
    <p>
        运行项目！你会看到现在FAB的过渡效果已
        <i>
            更加地
        </i>
        顺滑!:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-54-17-transition2.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-00-54-17-transition2.gif"
            alt="" width="282" height="500" class="aligncenter size-large wp-image-168963">
        </a>
    </p>
    <p>
        对于动作栏和导航栏的问题，首先更新
        <em>
            styles.xml
        </em>
        ，首先将父主题设置为
        <code>
            Theme.AppCompat.Light.NoActionBar
        </code>
        ：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">style</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"AppTheme"</span> <span class="hljs-attr">parent</span>=<span class="hljs-string">"Theme.AppCompat.Light.NoActionBar"</span>&gt;</span><span class="undefined">
</span></pre>
    <p>
        由于在
        <em>
            styles.xml
        </em>
        中并未定义过动作栏，你不得不适用单独的XML view来添加它。
    </p>
    <p>
        打开
        <em>
            activity_main.xml
        </em>
        并在
        <code>
            LinearLayout
        </code>
        中添加下列的代码，就在
        <code>
            RecyclerView
        </code>
        这个标签之上：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">include</span> <span class="hljs-attr">layout</span>=<span class="hljs-string">"@layout/toolbar"</span> /&gt;</span>
</pre>
    <p>
        这只包含了一个工具栏的布局，作为起始项目的一部分来提供到当前的布局中。现在你需要对详情activity的布局作出类似的更改。
    </p>
    <p>
        打开
        <em>
            activity_detail.xml
        </em>
        并添加下列的代码到第一个
        <code>
            FrameLayout
        </code>
        标签的尾部：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">include</span> <span class="hljs-attr">layout</span>=<span class="hljs-string">"@layout/toolbar_detail"</span>/&gt;</span>
</pre>
    <p>
        然后你需要在
        <code>
            MainActivity
        </code>
        中初始化工具栏。并在
        <code>
            onCreate()
        </code>
        方法的底部添加如下代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">setUpActionBar()
</pre>
    <p>
        这里你将调用
        <code>
            findViewById
        </code>
        的结果赋值给了新字段，然后调用
        <code>
            setUpActionBar()
        </code>
        （现在还只是一个空方法）。添加下列的代码到
        <code>
            setUpActionBar()
        </code>
        方法中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">    setSupportActionBar(toolbar)
    supportActionBar?.setDisplayHomeAsUpEnabled(<span class="hljs-literal">false</span>)
    supportActionBar?.setDisplayShowTitleEnabled(<span class="hljs-literal">true</span>)
    supportActionBar?.elevation = <span class="hljs-number">7.0</span>f
</pre>
    <p>
        这里设置这个工具栏作为你自定义工具栏的实例，然后设置title的visibility，禁用home按钮，然后通过设置elevation来添加些许的阴影效果。
    </p>
    <p>
        运行项目。你发现并没有什么变化，但这些改动已为合理地转换工具栏奠定了基础。
    </p>
    <p>
        打开
        <code>
            MainActivity
        </code>
        并使用下列的代码替换之前的
        <code>
            onItemClickListener
        </code>
        ：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">private</span> val onItemClickListener = object : TravelListAdapter.OnItemClickListener {
  <span class="hljs-function">override fun <span class="hljs-title">onItemClick</span><span class="hljs-params">(view: View, position: Int)</span> </span>{
    <span class="hljs-comment">// 1</span>
    val transitionIntent = DetailActivity.newIntent(<span class="hljs-keyword">this</span><span class="hljs-meta">@MainActivity</span>, position)
    val placeImage = view.findViewById&lt;ImageView&gt;(R.id.placeImage)
    val placeNameHolder = view.findViewById&lt;LinearLayout&gt;(R.id.placeNameHolder)
    <span class="hljs-comment">// 2</span>
    val navigationBar = findViewById&lt;View&gt;(android.R.id.navigationBarBackground)
    val statusBar = findViewById&lt;View&gt;(android.R.id.statusBarBackground)
    val imagePair = Pair.create(placeImage as View, <span class="hljs-string">"tImage"</span>)
    val holderPair = Pair.create(placeNameHolder as View, <span class="hljs-string">"tNameHolder"</span>)
    <span class="hljs-comment">// 3</span>
    val navPair = Pair.create(navigationBar, Window.NAVIGATION_BAR_BACKGROUND_TRANSITION_NAME)
    val statusPair = Pair.create(statusBar, Window.STATUS_BAR_BACKGROUND_TRANSITION_NAME)
    val toolbarPair = Pair.create(toolbar as View, <span class="hljs-string">"tActionBar"</span>)
    <span class="hljs-comment">// 4</span>
    val pairs = mutableListOf(imagePair, holderPair, statusPair, toolbarPair)
    <span class="hljs-keyword">if</span> (navigationBar != <span class="hljs-keyword">null</span> &amp;&amp; navPair != <span class="hljs-keyword">null</span>) {
      pairs += navPair
    }
    <span class="hljs-comment">// 5</span>
    val options = ActivityOptionsCompat.makeSceneTransitionAnimation(<span class="hljs-keyword">this</span><span class="hljs-meta">@MainActivity</span>,
      *pairs.toTypedArray())
    ActivityCompat.startActivity(<span class="hljs-keyword">this</span><span class="hljs-meta">@MainActivity</span>, transitionIntent, options.toBundle())
  }
}
</pre>
    <p>
        原始的实现与现在这个的差别如下：
    </p>
    <ol>
        <li>
            重命名intent以提供更多的context；
        </li>
        <li>
            获取对导航栏和状态栏的引用；
        </li>
        <li>
            创建了三个
            <code>
                Pair
            </code>
            的实例 - 一个用于navigation bar，一个用于status bar，还有一个用于toolbar；
        </li>
        <li>
            避免在某些设备上会发生的IllegalArgumentException，诸如Galaxy Tab S2这样的设备，它们的
            <code>
                navPair
            </code>
            就为null。
        </li>
        <li>
            最后你更新了传递给新activity的options，来包含指向新view的引用。并在改变成typed array的 
            <code>
                pairs
            </code>
            上，使用Kotlin的spread操作符
            <code>
                *
            </code>
            。
        </li>
    </ol>
    <p>
        太棒了！运行项目，你将可以看到一个更加流畅的动画：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-37-20-transition3.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Aug-20-2017-01-37-20-transition3.gif"
            alt="" width="282" height="500" class="aligncenter size-large wp-image-168964">
        </a>
    </p>
    <p>
        现在如果你点击action/toolbar或navigation bar之下的一行，它就不会在过渡之前出现跳动的效果了；它会与剩余的共享元素一同完成过渡效果，让你感觉到更加的赏心悦目。切换到网格的view，你就会看到在该布局下同样非常棒的过渡效果。
    </p>
    <p>
        Ta-da！下面是最终app的视频演示：
    </p>
    <div style="width: 206px;" class="wp-video">
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
            </div>
        </div>
    </div>
    <h2>
        从这儿去向哪里？
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
                            想要学习得更快？通过我们的
                            <span>
                                视频课程
                            </span>
                            来节约时间吧
                        </span>
                    </div>
                </div>
            </a>
        </div>
    </div>
    <p>
        为自己感到自豪吧：你创建了一个成熟的Android质感app！挑战一下自己吧，尝试下列的操作：
    </p>
    <ul>
        <li>
            使用
            <code>
                StaggeredLayoutManager
            </code>
            来创建一个三列的网格而不是两列。
        </li>
        <li>
            在
            <code>
                MainActivity
            </code>
            和
            <code>
                DetailActivity
            </code>
            中使用不同的palette选项来使用
            <code>
                Palette
            </code>
            API。
        </li>
        <li>
            在place列表中添加一个按钮，并将其作为共享的元素过渡到详情view中 - 也许是一个favorite按钮。
        </li>
        <li>
            让这些转场动画更酷 - 参考Android的Newsstand app，查看它如何使用展现的动画，来完成从网格视图到详情视图的过渡效果。通过这里所有的代码，你就可以重现这个效果。
        </li>
        <li>
            使用
            <code>
                animated-vectors
            </code>
            ，去尝试创建你在本文中所见到的变形动画。
        </li>
    </ul>
    <p>
        当然了，可以将这些知识应用到你的app中，让它们想这里所显示的一样酷。:]
    </p>
    <p>
        了解更多关于质感设计的内容，请访问Google最近重新设计的
        <a href="https://design.google/" target="_blank">
            Google Design
        </a>
        网站。
    </p>
    <p>
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/travelwishlist-final-2.zip">
            这里
        </a>
        获取最终的项目。
    </p>
</div>