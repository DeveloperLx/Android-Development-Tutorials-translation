# 中级Recyclerview教程 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/172711/intermediate-recyclerview) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/RecyclerViewIntermediate-feature.png"
        alt="Android RW" width="250" height="250" class="alignright size-full wp-image-87100">
    </p>
    <p>
        你有想过去趟火星，看一看它的地平线么？我们无法把你送到哪里，但可以送你一个很棒的东西：能够展示所有火星图片的app。
    </p>
    <p> 
        为了展示这些图片，我们将会使用Android最流行的控件之一：
        <em>
            RecyclerView
        </em>
        。
    </p>
    <p>
        <em>
            RecyclerView
        </em>
        布局是在Lollipop的支持库中被引入的，Android开发者已使用了它很长的时间。它是最流行的布局之一，可以给予你相对
        <em>
            ListView
        </em>
        更加灵活的方式。
    </p>
    <p>
        然而，你还尚未了解到它的全部。在本教程中，你会看到如何为它添加分组，动画，分割线和轻扫手势。
    </p>
    <p>
        你应当熟悉
        <em>
            ReyclerView
        </em>
        的基本使用。若非如此，可以阅读
        <em>
            RecyclerView
        </em>
        的
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Android%20RecyclerView%20Tutorial%20with%20Kotlin.md"
        target="_blank" sl-processed="1">
            这个教程
        </a>
        。
    </p>
    <p>
        下面是来自完成的app的一张截图：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png"
        alt="mars rover screenshot" width="281" height="500" class="aligncenter size-large wp-image-173107"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        感受这些令人惊奇的火星图片！:]
    </p>
    <p>
        你将继续使用在上一篇
        <em>
            RecyclerView
        </em>
        教程中用到的NASA网址，但要做一些不同的事情。你会使用一个能够返回火星照片列表的API。配套于照片的
        <em>
            RecyclerView
        </em>
        ，还有两个spinner可以用来更改照片列表：一个用于漫游者，另一个用于相机。
    </p>
    <h2>
        入门
    </h2>
    <p>
        在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/marsrovers-starter-1.zip"
        sl-processed="1">
            这里
        </a>
        下载初始项目。在Android Studio 3.0.1或更高的版本中打开它。
    </p>
    <p>
        接下来，找到NASA的网站（
        <a href="https://api.nasa.gov/index.html#apply-for-an-api-key" target="
        _blank"="" sl-processed="1">
            https://api.nasa.gov/index.html#apply-for-an-api-key
        </a>
        ），并获取一个可以使用rover照片的API key。
    </p>
    <p>
        在模拟器或设备上运行项目。你可以在屏幕的中央看到一个默认的“Hello World!”
        <em>
            TextView
        </em>
        。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953-281x500.png” alt="" width="281" height="500" class="aligncenter size-large wp-image-172715” srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953-281x500.png
        281w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953-180x320.png
        180w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953.png
        1440w" sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h3>
        Manifest
    </h3>
    <p>
        添加下列的代码到
        <em>
            AndroidManifest.xml
        </em>
        文件中，就在application的tag之前：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">uses-permission</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.permission.INTERNET"</span>/&gt;</span></pre>
    <p>
        这样你就可以从NASA网站上获取信息了。注意这并不是一个“危险”的许可，用户无需对它进行批准。
    </p>
    <h3>
        字符串数据
    </h3>
    <p>
        为了完成主页面上的两个spinner，你需要在
        <em>
            strings.xml
        </em>
        文件中添加一些字符串。打开
        <em>
            res/values
        </em>
        目录下的
        <em>
            strings.xml
        </em>
        文件，并在
        <em>
            app_name
        </em>
        字符串之后添加如下的内容：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">string</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"api_error"</span>&gt;</span>Problems getting Photos<span class="hljs-tag">&lt;/<span class="hljs-name">string</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">string</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"rovers"</span>&gt;</span>Rovers<span class="hljs-tag">&lt;/<span class="hljs-name">string</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">string</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"cameras"</span>&gt;</span>Cameras<span class="hljs-tag">&lt;/<span class="hljs-name">string</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">string-array</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"rovers"</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Curiosity<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Opportunity<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Spirit<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">string-array</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">string-array</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"camera_names"</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Front Hazard<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Rear Hazard<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Navigation<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Panoramic<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>Mast<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">string-array</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">string-array</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"camera_values"</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>FHAZ<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>RHAZ<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>NAVCAM<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>PANCAM<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
   <span class="hljs-tag">&lt;<span class="hljs-name">item</span>&gt;</span>MAST<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">string-array</span>&gt;</span></pre>
    <h2>
        Main Layout
    </h2>
    <p>
        你需要对主布局进行一些修改，并添加一些代码到
        <code>
            MainActivity
        </code>
        类中。首先是在
        <em>
            activity_main.xml
        </em>
        文件中的替换。
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">android.support.constraint.ConstraintLayout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">xmlns:app</span>=<span class="hljs-string">"http://schemas.android.com/apk/res-auto"</span>
  <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">tools:context</span>=<span class="hljs-string">"com.raywenderlich.marsrovers.MainActivity"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">android.support.constraint.ConstraintLayout</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/control_layout"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:padding</span>=<span class="hljs-string">"10dp"</span>
    <span class="hljs-attr">app:layout_constraintLeft_toLeftOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintTop_toTopOf</span>=<span class="hljs-string">"parent"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/roverLabel"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/rovers"</span>
      <span class="hljs-attr">app:layout_constraintTop_toTopOf</span>=<span class="hljs-string">"parent"</span> /&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.AppCompatSpinner</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/rovers"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">app:layout_constraintRight_toRightOf</span>=<span class="hljs-string">"parent"</span>
      <span class="hljs-attr">app:layout_constraintTop_toTopOf</span>=<span class="hljs-string">"parent"</span> /&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/cameraLabel"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"4dp"</span>
      <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/cameras"</span>
      <span class="hljs-attr">app:layout_constraintTop_toBottomOf</span>=<span class="hljs-string">"@+id/roverLabel"</span> /&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.AppCompatSpinner</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/cameras"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
      <span class="hljs-attr">app:layout_constraintRight_toRightOf</span>=<span class="hljs-string">"parent"</span>
      <span class="hljs-attr">app:layout_constraintTop_toBottomOf</span>=<span class="hljs-string">"@+id/rovers"</span> /&gt;</span>
  <span class="hljs-tag">&lt;/<span class="hljs-name">android.support.constraint.ConstraintLayout</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.RecyclerView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/recycler_view"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"0dp"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"0dp"</span>
    <span class="hljs-attr">android:visibility</span>=<span class="hljs-string">"gone"</span>
    <span class="hljs-attr">app:layout_constraintBottom_toBottomOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintLeft_toLeftOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintRight_toRightOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintTop_toBottomOf</span>=<span class="hljs-string">"@+id/control_layout"</span> /&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">ProgressBar</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/progress"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:indeterminate</span>=<span class="hljs-string">"true"</span>
    <span class="hljs-attr">app:layout_constraintBottom_toBottomOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintLeft_toLeftOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintRight_toRightOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintTop_toBottomOf</span>=<span class="hljs-string">"@+id/control_layout"</span> /&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">android.support.constraint.ConstraintLayout</span>&gt;</span>
</pre>
    <p>
        上述代码使用了Android新的
        <em>
            ConstraintLayout
        </em>
        来添加两行的spinner，一行是Rover的，另一行则是camera的。在spinner的下方则是一个
        <em>
            RecyclerView
        </em>
        。RecyclerView的下方还有一个
        <em>
            ProgressBar
        </em>
        ，它会在数据加载的时候旋转起来。
    </p>
    <p>
        接下来修改
        <em>
            MainActivity.kt
        </em>
        。在
        <code>
            onCreate()
        </code>
        方法中，调用
        <code>
            setContentView
        </code>
        之后，添加如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">recycler_view.visibility = View.GONE
recycler_view.layoutManager = LinearLayoutManager(<span class="hljs-keyword">this</span>)
</pre>
    <p>
        当Android Studio在
        <code>
            recycler_view
        </code>
        上给你提示了一个错误的时候，将光标移到
        <code>
            recycler_view
        </code>
        上并点击
        <em>
            option+return
        </em>
        （在PC上是
        <em>
            Alt+Enter
        </em>
        ）并选择“Import”。这就会使用Kotlin的Android插件来讲
        <code>
            R.id.recycler_view id
        </code>
        转换为
        <code>
            recycler_view
        </code>
        变量。
    </p>
    <p>
        现在，运行app，你会看到如下的内容：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951-281x500.png"
        alt="mars rover screenshot" width="281" height="500" 
        class="aligncenter size-large wp-image-173095" 
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951-281x500.png
        281w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951-180x320.png
        180w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951.png
        1080w" sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h2>
        ViewHolder
    </h2>
    <p>
        <em>
            ViewHolder
        </em>
        类会持有item中的view，它在
        <em>
            RecyclerView.Adapter
        </em>
        的
        <code>
            onCreateViewHolder
        </code>
        方法中被创建，并在
        <code>
            onBindViewHolder
        </code>
        方法中被绑定。
    </p>
    <p>
        在
        <em>
            RecyclerView
        </em>
        之前，Android的开发者会使用
        <em>
            ListView
        </em>
        来实现类型的功能。随着
        <em>
            ListView
        </em>
        用法的成熟，开发者开始使用“view holder”的模式。之后Google则把
        <em>
            ViewHolder
        </em>
        作为了
        <em>
            RecyclerView
        </em>
        API的一个关键的部分。
    </p>
    <p>
        你将创建一个特别的
        <code>
            ViewHolder
        </code>
        类，让你能够在无需使用
        <code>
            findViewById
        </code>
        的条件下处理文本和图片。在
        <code>
            DefaultViewHolder
        </code>
        类中，你将从遍历所有的子view开始，将它们放置到一个map中，这样你就可以在之后轻松地获取它们。请看初始项目中完整的
        <code>
            DefaultViewHolder
        </code>
        类。
    </p>
    <h2>
        Adapter Layouts
    </h2>
    <p>
        你需要创建两个用在adapter上的布局，一个用于section的header，另一个则为行本身。首先，添加header item布局所需的header风格。
    </p>
    <p>
        <em>
            Header风格
        </em>
    </p>
    <p>
        在value资源目录下打开
        <em>
            styles.xml
        </em>
        文件，并添加下列的风格，它们将会在
        <em>
            header_item.xml
        </em>
        文件中被使用到：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">style</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"header"</span>&gt;</span><span class="xml">
  <span class="hljs-tag">&lt;<span class="hljs-name">item</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"android:textSize"</span>&gt;</span>16sp<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">item</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"android:textColor"</span>&gt;</span>@android:color/holo_red_dark<span class="hljs-tag">&lt;/<span class="hljs-name">item</span>&gt;</span>
</span><span class="hljs-tag">&lt;/<span class="hljs-name">style</span>&gt;</span>
</pre>
    <p>
        你可以使用任何你喜欢的颜色。为创建header，找到
        <em>
            res/layout
        </em>
        目录。右击它并选择
        <em>
            New/Layout resource file
        </em>
        。将文件命名为
        <em>
            header_item.xml
        </em>
        。保留建议的根元素，然后将其替换为如下的内容：
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">LinearLayout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
  <span class="hljs-attr">android:orientation</span>=<span class="hljs-string">"vertical"</span>
  <span class="hljs-attr">android:padding</span>=<span class="hljs-string">"10dp"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/header_text"</span>
    <span class="hljs-attr">style</span>=<span class="hljs-string">"@style/header"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">tools:text</span>=<span class="hljs-string">"Front Hazard"</span> /&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">LinearLayout</span>&gt;</span>
</pre>
    <p>
        这就是一个用来容纳header文本的
        <em>
            TextView
        </em>
        。
    </p>
    <p>
        接下来，右击布局目录，并创建一个名为
        <em>
            row_item.xml
        </em>
        的新布局。然后，再次将根元素替换为：
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">LinearLayout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
  <span class="hljs-attr">android:orientation</span>=<span class="hljs-string">"vertical"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">ImageView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/camera_image"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"80dp"</span>
    <span class="hljs-attr">android:adjustViewBounds</span>=<span class="hljs-string">"true"</span>
    <span class="hljs-attr">android:scaleType</span>=<span class="hljs-string">"fitXY"</span> /&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/date"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">tools:text</span>=<span class="hljs-string">"10/07/2017"</span> /&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">LinearLayout</span>&gt;</span>
</pre>
    <p>
        包含一个用来展示火星照片的
        <em>
            ImageView
        </em>
        ，以及一个用来展示图片日期的
        <em>
            TextView
        </em>
        。
    </p>
    <h2>
        Data
    </h2>
    <p>
        你将使用来自NASA网站的
        <a href="https://api.nasa.gov/api.html#MarsPhotos" sl-processed="1">
            https://api.nasa.gov/api.html#MarsPhotos
        </a>
        来填充
        <em>
            RecyclerView.Adapter
        </em>
        。
    </p>
    <p>
        测试API的一个简单的方法是使用Chrome的Postman插件，或Postman app (
        <a href="https://www.getpostman.com/" sl-processed="1">
            https://www.getpostman.com/
        </a>
        )。安装完毕之后，请使用url
        <a href="https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&amp;api_key="
        sl-processed="
        1">
            https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&amp;api_key=
        </a>
        并将你的key添加到它的最后。
    </p>
    <p>
        点击Postman上的“Send”按钮，你就会在Response区域看到返回的JSON。注意它是如何返回带有一个名为photo的item的对象的，它是一个对象的数组。现在，你将创建model来持有返回的数据。
    </p>
    <p>
        在Android Studio中找到, navigate to the
        <code>
            com.raywenderlich.marsrovers
        </code>
        包，右击并选择
        <em>
            New/Package
        </em>
        来创建一个新包，名为
        <code>
            models
        </code>
        。
    </p>
    <p>
        接下来，右击
        <code>
            models
        </code>
        包并选择
        <em>
            New/Kotlin File/Class
        </em>
        。将文件命名为
        <code>
            Camera
        </code>
        ，选择
        <em>
            Class
        </em>
        作为“Kind”，并将默认生成的代码替换为如下内容：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">data</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Camera</span></span>(<span class="hljs-keyword">val</span> id: <span class="hljs-built_in">Int</span>, <span class="hljs-keyword">val</span> name: String, <span class="hljs-keyword">val</span> rover_id: <span class="hljs-built_in">Int</span>, <span class="hljs-keyword">val</span> full_name: String)
</pre>
    <p>
        注意你使用了
        <code>
            data
        </code>
        关键字来让Kotlin帮助你创建getter和setter，因此这个类无需大括号来容纳需要实现的方法。这些字段的名称和从NASA API返回的JSON中相应的字段是相同的。你当然可以使这些名称更加地可读，但需要添加一些额外的annotation来实现。现在我们只需使用这里给出的名称。
    </p>
    <p>
        接下来，右击
        <code>
            models
        </code>
        包并创建一个Kotlin类，名为
        <code>
            Photo
        </code>
        ，并将其中的内容替换为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">data</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Photo</span></span>(<span class="hljs-keyword">val</span> id : <span class="hljs-built_in">Int</span>, <span class="hljs-keyword">val</span> img_src : String, <span class="hljs-keyword">val</span> earth_date: String, <span class="hljs-keyword">val</span> camera: Camera)</pre>
    <p>
        创建另一个名为
        <code>
            PhotoList
        </code>
        的Kotlin类。它持有了一个照片的列表，且为JSON数据的根元素：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">data</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PhotoList</span></span>(<span class="hljs-keyword">val</span> photos: List&lt;Photo&gt;)</pre>
    <p>
        最后，创建一个
        <code>
            PhotoRow
        </code>
        类，用来指示某一行时照片还是header。这样，你就只需创建一个
        <code>
            PhotoRow
        </code>
        对象的列表，并基于
        <code>
            RowType
        </code>
        枚举值来确定展示何种类型。在
        <code>
            models
        </code>
        包下创建一个新的名为
        <code>
            PhotoRow
        </code>
        的Kotlin类，并添加如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">enum</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RowType</span> </span>{
   PHOTO,
   HEADER
}

<span class="hljs-keyword">data</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PhotoRow</span></span>(<span class="hljs-keyword">var</span> type: RowType, <span class="hljs-keyword">var</span> photo: Photo?, <span class="hljs-keyword">var</span> header: String?)</pre>
    <p>
        <code>
            type
        </code>
        property将用来区分照片和header。row必然是照片和header文本中的一种，且它们均可为空。
    </p>
    <h2>
        Adapter
    </h2>
    <p>
        你的adapter将继承自
        <em>
            RecyclerView.Adapter
        </em>
        类，并使用
        <em>
            DefaultViewHolder
        </em>
        。找到
        <em>
            com.raywenderlich.marsrovers.recyclerview
        </em>
        包，并添加一个新的名为
        <em>
            PhotoAdapter
        </em>
        的Kotlin类。
    </p>
    <p>
        这个类初始看起来就像下面这样：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PhotoAdapter</span></span>(<span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> photoList: ArrayList&lt;PhotoRow&gt;) : RecyclerView.Adapter&lt;DefaultViewHolder&gt;() {</pre>
    <p>
        为了传递照片列表，在这个类的开始创建两个变量：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> filteredPhotos = ArrayList&lt;PhotoRow&gt;()
<span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> filtering = <span class="hljs-literal">false</span>
</pre>
    <p>
        <code>
            filterPhotos
        </code>
        列表将用来持有一个特定相机的照片，而
        <code>
            filtering
        </code>
        标记将在用户正在过滤时为true。
    </p>
    <p>
        <em>
            RecyclerView.Adapter
        </em>
        中有三个抽象方法必须要实现：
        <code>
            getItemCount
        </code>
        ，
        <code>
            onCreateViewHolder
        </code>
        ，和
        <code>
            onBindViewHolder
        </code>
        。你还需要重写
        <code>
            getItemViewType
        </code>
        方法来针对header和照片返回不同的值。
    </p>
    <p>
        <code>
            getItemCount
        </code>
        返回了可用照片的数量。当过滤器被打开时，则返回被过滤后照片的数量：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getItemCount</span><span class="hljs-params">()</span></span>: <span class="hljs-built_in">Int</span> {
 <span class="hljs-keyword">if</span> (filtering) {
     <span class="hljs-keyword">return</span> filteredPhotos.size
 }
 <span class="hljs-keyword">return</span> photoList.size
}
</pre>
    <p>
        <code>
            onBindViewHolder
        </code>
        是你用来加载照片并设置header文案的地方。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onBindViewHolder</span><span class="hljs-params">(holder: <span class="hljs-type">DefaultViewHolder</span>, position: <span class="hljs-type">Int</span>)</span></span> {
  <span class="hljs-keyword">val</span> photoRow : PhotoRow = <span class="hljs-keyword">if</span> (filtering) {
    filteredPhotos[position]
  } <span class="hljs-keyword">else</span> {
    photoList[position]
  }
  <span class="hljs-keyword">if</span> (photoRow.type == RowType.PHOTO) {
    <span class="hljs-keyword">val</span> photo = photoRow.photo
    Glide.with(holder.itemView.context)
        .load(photo?.img_src)
        .into(holder.getImage(R.id.camera_image))
    photo?.earth_date?.let { holder.setText(R.id.date, it) }
  } <span class="hljs-keyword">else</span> {
    photoRow.header?.let { holder.setText(R.id.header_text, it) }
  }
}
</pre>
    <p>
        上述代码使用了
        <a href="https://github.com/bumptech/glide" sl-processed="1">
            Glide
        </a>
        来加载图片到
        <em>
            ImageView
        </em>
        中。对于所有的火星照片，Glide看起来比
        <a href="http://square.github.io/picasso/" sl-processed="1">
            Picasso
        </a>
        更加得好，后者只可以加载其中部分的图片。
    </p>
    <p>
        <code>
            onCreateViewHolder
        </code>
        则是你inflate布局并返回
        <em>
            ViewHolder
        </em>
        的方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateViewHolder</span><span class="hljs-params">(parent: <span class="hljs-type">ViewGroup</span>, viewType: <span class="hljs-type">Int</span>)</span></span>: DefaultViewHolder {
  <span class="hljs-keyword">val</span> layoutInflater = LayoutInflater.from(parent.context)

  <span class="hljs-keyword">val</span> inflatedView : View = <span class="hljs-keyword">when</span> (viewType) {
    RowType.PHOTO.ordinal -&gt; layoutInflater.inflate(R.layout.row_item, parent,<span class="hljs-literal">false</span>)
    <span class="hljs-keyword">else</span> -&gt; layoutInflater.inflate(R.layout.header_item, parent,<span class="hljs-literal">false</span>)
  }
  <span class="hljs-keyword">return</span> DefaultViewHolder(inflatedView)
}
</pre>
    <p>
        对于
        <code>
            onCreateViewHolder
        </code>
        和
        <code>
            onBindViewHolder
        </code>
        这两个方法，你需要区分是header还是照片。你可以通过检查
        <em>
            PhotoRow
        </em>
        的类型来进行区分，正如你在下一节所看到的一样。
    </p>
    <h2>
        节Header
    </h2>
    <p>
        为了给行提供header，你需要不同的行类型。这需要通过让
        <em>
            RecyclerView
        </em>
        了解每行使用什么类型来完成。
    </p>
    <p>
        重写
        <code>
            getItemViewType
        </code>
        方法，并为每种类型返回不同的整数。你将返回两种不同的类型相应的整数，一种用于header，另一种用于照片。在本例中使用枚举相应的整数即可（因此返回值必然为0或1中的一个）。添加下列的方法到
        <code>
            onCreateViewHolder
        </code>
        之后。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getItemViewType</span><span class="hljs-params">(position: <span class="hljs-type">Int</span>)</span></span> =
  <span class="hljs-keyword">if</span> (filtering) {
    filteredPhotos[position].type.ordinal
  } <span class="hljs-keyword">else</span> {
    photoList[position].type.ordinal
  }
</pre>
    <p>
        <code>
            getItemCount
        </code>
        和
        <code>
            getItemViewType
        </code>
        方法都需要基于过滤标记的不同而在
        <code>
            photoList
        </code>
        和
        <code>
            filteredPhotos
        </code>
        列表之间进行选择。
    </p>
    <p>
        在
        <code>
            onCreateViewHolder
        </code>
        方法中，你为照片加载了row\_item布局，为header加载了head\_item布局。而在
        <code>
            onBindViewHolder
        </code>
        方法中，检查类型并绑定相应的item到
        <em>
            ViewHolder
        </em>
        上。
    </p>
    <p>
        现在运行app来确认它可以构建成功。由于你还没有把adapter添加到
        <em>
            RecyclerView
        </em>
        上，你还看不到任何内容，只有旋转的ProgressBar。
    </p>
    <h2>
        DiffUtil
    </h2>
    <p>
        <em>
            DiffUtil
        </em>
        是一个来自于 
        <em>
            RecyclerView
        </em>
        支持库的工具类，用来计算两个列表之间的差异，并创建将一个列表变换成另一个的操作。它将被
        <em>
            RecyclerView.Adapter
        </em>
        用来触发最优的数据变化通知，为
        <em>
            RecyclerView
        </em>
        的行添加动画。
    </p>
    <p>
        为使用这个方法，你需要实现
        <em>
            DiffUtil.Callback
        </em>
        。将它添加到
        <em>
            PhotoAdapter
        </em>
        类的尾部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PhotoRowDiffCallback</span></span>(<span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> newRows : List&lt;PhotoRow&gt;, <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> oldRows : List&lt;PhotoRow&gt;) : DiffUtil.Callback() {
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">areItemsTheSame</span><span class="hljs-params">(oldItemPosition: <span class="hljs-type">Int</span>, newItemPosition: <span class="hljs-type">Int</span>)</span></span>: <span class="hljs-built_in">Boolean</span> {
    <span class="hljs-keyword">val</span> oldRow = oldRows[oldItemPosition]
    <span class="hljs-keyword">val</span> newRow = newRows[newItemPosition]
    <span class="hljs-keyword">return</span> oldRow.type == newRow.type
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getOldListSize</span><span class="hljs-params">()</span></span>: <span class="hljs-built_in">Int</span> = oldRows.size

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getNewListSize</span><span class="hljs-params">()</span></span>: <span class="hljs-built_in">Int</span> = newRows.size

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">areContentsTheSame</span><span class="hljs-params">(oldItemPosition: <span class="hljs-type">Int</span>, newItemPosition: <span class="hljs-type">Int</span>)</span></span>: <span class="hljs-built_in">Boolean</span> {
    <span class="hljs-keyword">val</span> oldRow = oldRows[oldItemPosition]
    <span class="hljs-keyword">val</span> newRow = newRows[newItemPosition]
    <span class="hljs-keyword">return</span> oldRow == newRow
  }
}
</pre>
    <p>
        这个类会检查item是否含有相同的类型或值。
        <code>
            areItemsTheSame
        </code>
        方法只会检查行的类型，而
        <code>
            areContentsTheSame
        </code>
        则会检查行是否完全相同。
    </p>
    <h3>
        额外的方法
    </h3>
    <p>
        为更新照片的列表，你需要传入一个新的列表，计算两个列表的不同之处，并清理过滤器。在
        <code>
            PhotoAdapter
        </code>
        中        
        <code>
            getItemViewType
        </code>
        之后添加下列的方法，来支持清理过滤列表，使用
        <em>
            DiffUtil
        </em>
        来告知
        <em>
            Adapter
        </em>
        如何更新照片视图，并移除行：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">clearFilter</span><span class="hljs-params">()</span></span> {
    filtering = <span class="hljs-literal">false</span>
    filteredPhotos.clear()
  }

<span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">updatePhotos</span><span class="hljs-params">(photos : <span class="hljs-type">ArrayList</span>&lt;<span class="hljs-type">PhotoRow</span>&gt;)</span></span> {
   DiffUtil.calculateDiff(PhotoRowDiffCallback(photos, photoList), <span class="hljs-literal">false</span>).dispatchUpdatesTo(<span class="hljs-keyword">this</span>)
   photoList = photos
   clearFilter()
}

<span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">removeRow</span><span class="hljs-params">(row : <span class="hljs-type">Int</span>)</span></span> {
   <span class="hljs-keyword">if</span> (filtering) {
       filteredPhotos.removeAt(row)
   } <span class="hljs-keyword">else</span> {
       photoList.removeAt(row)
   }
   notifyItemRemoved(row)
}
</pre>
    <p>
        注意
        <code>
            notifyItemRemoved
        </code>
        方法。这个方法将为被删除行及其附近的行上添加动画，因为它确切地告知了
        <em>
            RecyclerView
        </em>
        adapter是如何变化的。不使用
        <code>
            notifyDataSetChanged
        </code>
        是正确的，因为它无法准确地告知
        <em>
            RecyclerView
        </em>
        数据变化的细节。
    </p>
    <h2>
        Retrofit
    </h2>
    <p>
        为了从NASA获取数据，你需要使用
        <a href="http://square.github.io/retrofit/" sl-processed="1">
            Retrofit
        </a>
        和
        <a href="https://github.com/square/moshi" sl-processed="1">
            Moshi
        </a>
        库。你将使用Retrofit来下载数据，使用Moshi来将JSON转化为我们的model。
    </p>
    <p>
        首先，创建一个服务器接口。创建一个名为
        <em>
            service
        </em>
        的新包，右击它创建一个新的名为
        <em>
            NasaApi
        </em>
        的Kotlin interface。将其中的内容替换为如下代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">NasaApi</span> </span>{
   <span class="hljs-meta">@GET(<span class="hljs-meta-string">"mars-photos/api/v1/rovers/{rover}/photos?sol=1000&amp;api_key=&lt;key&gt;"</span>)</span>
   <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getPhotos</span><span class="hljs-params">(<span class="hljs-meta">@Path(<span class="hljs-meta-string">"rover"</span>)</span> rover: <span class="hljs-type">String</span>)</span></span> : Call&lt;PhotoList&gt;
}
</pre>
    <p>
        用你从NASA网站中获取的key来替换这里的
        <em>
            &lt;key&gt;
        </em>
        。这样就设置好了获取照片列表的方法。传递给rover字符串的值将替换到{rover}处。
    </p>
    <p>
        如果你需要为
        <em>
            Call
        </em>
        添加一个import，请确保使用来自
        <em>
            retrofit2
        </em>
        包中的。
    </p>
    <p>
        接下来，就该创建实际的service了。它应当是一个单例。在Kotlin中，创建单例超级容易。
    </p>
    <p>
        右击
        <em>
            service
        </em>
        包并选择
        <em>
            New/Kotlin File/Class
        </em>
        ，将其命名为
        <em>
            NasaPhotos
        </em>
        ，设置
        <em>
            Kind
        </em>
        为
        <em>
            Object
        </em>
        。OK了！你已创建好了Kotlin单例。
    </p>
    <p>
        创建一个名为
        <code>
            service
        </code>
        的变量，用于
        <code>
            getPhotos
        </code>
        方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">object</span> NasaPhotos {
  <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> service : NasaApi
</pre>
    <p>
        然后添加一个
        <code>
            init
        </code>
        方法。它将用来创建Retrofit的实例，设置Moshi为JSON转换器，最后创建
        <code>
            service
        </code>
        对象：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">init {
    <span class="hljs-keyword">val</span> retrofit = Retrofit.Builder()
       .baseUrl(<span class="hljs-string">"https://api.nasa.gov/"</span>)
       .addConverterFactory(MoshiConverterFactory.create())
       .build()
    service = retrofit.create(NasaApi::<span class="hljs-class"><span class="hljs-keyword">class</span>.<span class="hljs-title">java</span>)</span>
}
</pre>
    <p>
        然后，穿件一个新法法来调用照片：
        Then, create a new method to make the call for the photos:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getPhotos</span><span class="hljs-params">(rover: <span class="hljs-type">String</span>)</span></span> : Call&lt;PhotoList&gt; = service.getPhotos(rover)
</pre>
    <p>
        你几乎已经完成，只需设置spinner和
        <em>
            RecyclerView
        </em>
        的adapter，这些将在下一节中完成。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/showme-320x320.png” alt="" width="320" height="320" class="aligncenter size-medium wp-image-179016” srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/showme-320x320.png
        320w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-250x250.png
        250w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-500x500.png
        500w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-32x32.png
        32w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-50x50.png
        50w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-64x64.png
        64w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-96x96.png
        96w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-128x128.png
        128w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme.png
        1000w" sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <h2>
        更新主UI
    </h2>
    <p>
        现在是时候来更新
        <em>
            MainActivity
        </em>
        ，设置spinner并加载一些照片了！
    </p>
    <p>
        添加一些变量来持有当前的rover字符串，以及spinner的位置，就在
        <code>
            MainActivity
        </code>
        的顶部
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> currentRover = <span class="hljs-string">"curiosity"</span>
<span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> currentRoverPosition = <span class="hljs-number">0</span>
<span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> currentCameraPosition = <span class="hljs-number">0</span>
</pre>
    <p>
        在
        <em>
            MainActivity
        </em>
        类声明的上方添加：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> const <span class="hljs-keyword">val</span> TAG = <span class="hljs-string">"MarsRover"</span>
</pre>
    <p>
        <code>
            TAG
        </code>
        将被用于日志。
    </p>
    <p>
        在
        <code>
            onCreate
        </code>
        方法下添加如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setupSpinners</span><span class="hljs-params">()</span></span> {
   setupRoverSpinner()
   setupCameraSpinner()
}

<span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setupCameraSpinner</span><span class="hljs-params">()</span></span> {
   <span class="hljs-comment">// Camera spinner</span>
   <span class="hljs-keyword">val</span> cameraStrings = resources.getStringArray(R.array.camera_values)
   <span class="hljs-keyword">val</span> cameraAdapter = ArrayAdapter.createFromResource(<span class="hljs-keyword">this</span>, R.array.camera_names, android.R.layout.simple_spinner_item)
   cameraAdapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
   cameras.adapter = cameraAdapter
   cameras.onItemSelectedListener = <span class="hljs-keyword">object</span> : AdapterView.OnItemSelectedListener {
       <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onNothingSelected</span><span class="hljs-params">(parent: <span class="hljs-type">AdapterView</span>&lt;*&gt;)</span></span> {
       }
       <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onItemSelected</span><span class="hljs-params">(parent: <span class="hljs-type">AdapterView</span>&lt;*&gt;, view: <span class="hljs-type">View</span>, position: <span class="hljs-type">Int</span>, id: <span class="hljs-type">Long</span>)</span></span> {
           currentCameraPosition = position
       }
   }
}

<span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setupRoverSpinner</span><span class="hljs-params">()</span></span> {
   <span class="hljs-comment">// Setup the spinners for selecting different rovers and cameras</span>
   <span class="hljs-keyword">val</span> roverStrings = resources.getStringArray(R.array.rovers)
   <span class="hljs-keyword">val</span> adapter = ArrayAdapter.createFromResource(<span class="hljs-keyword">this</span>, R.array.rovers, android.R.layout.simple_spinner_item)
   adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
   rovers.adapter = adapter
   rovers.onItemSelectedListener = <span class="hljs-keyword">object</span> : AdapterView.OnItemSelectedListener {
       <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onNothingSelected</span><span class="hljs-params">(parent: <span class="hljs-type">AdapterView</span>&lt;*&gt;)</span></span> {
       }
       <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onItemSelected</span><span class="hljs-params">(parent: <span class="hljs-type">AdapterView</span>&lt;*&gt;, view: <span class="hljs-type">View</span>, position: <span class="hljs-type">Int</span>, id: <span class="hljs-type">Long</span>)</span></span> {
           <span class="hljs-keyword">if</span> (currentRoverPosition != position) {
               currentRover = roverStrings[position].toLowerCase()
               loadPhotos()
           }
           currentRoverPosition = position
       }
   }
}
</pre>
    <p>
        这样就设置了spinner去持有相应的字符串数组。
    </p>
    <p>
        在
        <code>
            onCreate
        </code>
        方法的尾部，添加下列两行代码来设置spinner并加载照片：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">setupSpinners()
loadPhotos()
</pre>
    <p>
        接下来，加载并排序我们的照片。在
        <code>
            MainActivity
        </code>
        中的
        <code>
            setupRoverSpinner
        </code>
        后添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">loadPhotos</span><span class="hljs-params">()</span></span> {
    progress.visibility = View.VISIBLE
    recycler_view.visibility = View.GONE
    NasaPhotos.getPhotos(currentRover).enqueue(<span class="hljs-keyword">object</span> : Callback&lt;PhotoList&gt; {
       <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onFailure</span><span class="hljs-params">(call: <span class="hljs-type">Call</span>&lt;<span class="hljs-type">PhotoList</span>&gt;?, t: <span class="hljs-type">Throwable</span>?)</span></span> {
           Snackbar.make(recycler_view, R.string.api_error, Snackbar.LENGTH_LONG)
           Log.e(TAG, <span class="hljs-string">"Problems getting Photos with error: <span class="hljs-variable">$t</span>.msg"</span>)
       }
       <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onResponse</span><span class="hljs-params">(call: <span class="hljs-type">Call</span>&lt;<span class="hljs-type">PhotoList</span>&gt;?, response: <span class="hljs-type">Response</span>&lt;<span class="hljs-type">PhotoList</span>&gt;?)</span></span> {
           response?.let { photoResponse -&gt;
               <span class="hljs-keyword">if</span> (photoResponse.isSuccessful) {
                  <span class="hljs-keyword">val</span> body = photoResponse.body()
                  body?.let {
                     Log.d(TAG, <span class="hljs-string">"Received <span class="hljs-subst">${body.photos.size}</span> photos"</span>)
                     <span class="hljs-keyword">if</span> (recycler_view.adapter == <span class="hljs-literal">null</span>) {
                        <span class="hljs-keyword">val</span> adapter = PhotoAdapter(sortPhotos(body))
                        recycler_view.adapter = adapter
                     } <span class="hljs-keyword">else</span> {
                        (recycler_view.adapter <span class="hljs-keyword">as</span> PhotoAdapter).updatePhotos(sortPhotos(body))
                     }
                   }
                   recycler_view.scrollToPosition(<span class="hljs-number">0</span>)
                   recycler_view.visibility = View.VISIBLE
                   progress.visibility = View.GONE
               }
           }
       }
   })
}

<span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">sortPhotos</span><span class="hljs-params">(photoList: <span class="hljs-type">PhotoList</span>)</span></span> : ArrayList&lt;PhotoRow&gt; {
   <span class="hljs-keyword">val</span> map = HashMap&lt;String, ArrayList&lt;Photo&gt;&gt;()
   <span class="hljs-keyword">for</span> (photo <span class="hljs-keyword">in</span> photoList.photos) {
       <span class="hljs-keyword">var</span> photos = map[photo.camera.full_name]
       <span class="hljs-keyword">if</span> (photos == <span class="hljs-literal">null</span>) {
           photos = ArrayList()
           map[photo.camera.full_name] = photos
       }
       photos.add(photo)
   }
   <span class="hljs-keyword">val</span> newPhotos = ArrayList&lt;PhotoRow&gt;()
   <span class="hljs-keyword">for</span> ((key, value) <span class="hljs-keyword">in</span> map) {
       newPhotos.add(PhotoRow(RowType.HEADER, <span class="hljs-literal">null</span>, key))
       value.mapTo(newPhotos) { PhotoRow(RowType.PHOTO, it, <span class="hljs-literal">null</span>) }
   }
   <span class="hljs-keyword">return</span> newPhotos
}
</pre>
    <p>
        你需要导入一些类来解决出现的错误。注意，对于提供了多个导入选项的，你应当选择在
        <em>
            retrofit2
        </em>
        包中的那个。
    </p>
    <p>
        在
        <code>
            sortPhotos
        </code>
        方法中，你将照片拆分到了不同相机的部分中。
    </p>
    <p>
        Now it’s time to try it out. Build and run the app, and within about 10
        or 20 seconds, you should see something like:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png"
        alt="mars rover screenshot" width="281" height="500" class="aligncenter size-large wp-image-173107"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        If you don’t see any images, make sure you have your personal key in the
        Retrofit @GET annotation.
    </p>
    <p>
        You can choose different rovers from the spinner in the top right and
        different cameras from the spinner below the rover spinner but they won’t
        do anything until they are hooked up. Note also that not all rovers have
        images from all cameras.
    </p>
    <h2>
        Filtering
    </h2>
    <p>
        In order to filter the list, add the
        <em>
            filterCamera
        </em>
        method to
        <em>
            PhotoAdapter
        </em>
        below
        <code>
            getItemViewType
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">filterCamera</span><span class="hljs-params">(camera: <span class="hljs-type">String</span>)</span></span> {
   filtering = <span class="hljs-literal">true</span>
   <span class="hljs-keyword">val</span> newPhotos = photoList.filter { photo -&gt; photo.type == RowType.PHOTO &amp;&amp; photo.photo?.camera?.name.equals(camera) } <span class="hljs-keyword">as</span> ArrayList&lt;PhotoRow&gt;
   DiffUtil.calculateDiff(PhotoRowDiffCallback(newPhotos, photoList), <span class="hljs-literal">false</span>).dispatchUpdatesTo(<span class="hljs-keyword">this</span>)
   filteredPhotos = newPhotos
}
</pre>
    <p>
        Now go back to your
        <em>
            MainActivity
        </em>
        and hook up the camera filtering. Add the following code to the beginning
        of the
        <code>
            OnItemSelectedListener.onItemSelected()
        </code>
        in the
        <code>
            setupCameraSpinner
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">if</span> (recycler_view.adapter != <span class="hljs-literal">null</span> &amp;&amp; currentCameraPosition != position) {
   (recycler_view.adapter <span class="hljs-keyword">as</span> PhotoAdapter).filterCamera(cameraStrings[position])
}
</pre>
    <p>
        You pass in the camera string to filter on and create a new list with
        just those photos. You use Kotlin’s
        <code>
            filter
        </code>
        function on the collection and return a list of photos and has the given
        camera value.
    </p>
    <p>
        Now run the app and choose Opportunity as the new rover and you should
        see something like:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-179008"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        ItemDecorators
    </h2>
    <p>
        Unlike
        <em>
            ListView
        </em>
        ,
        <em>
            RecyclerView
        </em>
        does not come with any built-in dividers. Instead,
        <em>
            RecyclerView
        </em>
        allows you to add your own decorators.
    </p>
    <p>
        The
        <em>
            RecyclerView
        </em>
        library comes with a
        <em>
            DividerItemDecoration
        </em>
        that can be used to put dividers between your rows. You can add a divider
        with this one line, which you should add to
        <code>
            onCreate()
        </code>
        in
        <code>
            MainActivity
        </code>
        after the line:
        <code>
            recycler_view.visibility = View.GONE
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">recycler_view.addItemDecoration(DividerItemDecoration(<span class="hljs-keyword">this</span>, DividerItemDecoration.VERTICAL))</pre>
    <p>
        You can see the divider after the photo date on the last photo in a section.
    </p>
    <p>
        To create your own decorator, just subclass
        <em>
            ItemDecoration
        </em>
        and implement the
        <code>
            onDraw
        </code>
        and/or the
        <code>
            onDrawOver
        </code>
        methods.
    </p>
    <h2>
        Animations
    </h2>
    <p>
        <em>
            RecyclerView
        </em>
        s allow animations for each row and provides built-in animations for adding
        and removing rows.
    </p>
    <p>
        To show an animation for adding a row, make sure you use
        <code>
            notifyItemAdded(position)
        </code>
        instead of calling
        <code>
            notifyDataChanged()
        </code>
        . This lets the view know that just one row has been added and can animate
        that addition.
    </p>
    <p>
        For deleting, call
        <code>
            notifyItemRemoved(position)
        </code>
        .
    </p>
    <p>
        To animate the addition of each item, add the following method to
        <em>
            PhotoAdapter
        </em>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setAnimation</span><span class="hljs-params">(viewToAnimate: <span class="hljs-type">View</span>)</span></span> {
  <span class="hljs-keyword">if</span> (viewToAnimate.animation == <span class="hljs-literal">null</span>) {
    <span class="hljs-keyword">val</span> animation = AnimationUtils.loadAnimation(viewToAnimate.context, android.R.anim.slide_in_left)
    viewToAnimate.animation = animation
  }
}
</pre>
    <p>
        This will provide an animation where the row slides in from the left.
    </p>
    <p>
        Then add:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">setAnimation(holder.itemView)
</pre>
    <p>
        as the last line in
        <code>
            onBindViewHolder
        </code>
        . Now try running again.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/mars4.gif"
        alt="mars rover screenshot" width="238" height="500" class="aligncenter size-large wp-image-173282">
    </p>
    <p>
        The animation adds a nice dynamic effect to the presentation of the photos.
    </p>
    <h2>
        Swiping
    </h2>
    <p>
        Swiping is great way to let your user delete rows. You’re going to implement
        swiping in both the left and right direction to delete a row.
    </p>
    <p>
        <em>
            RecyclerView
        </em>
        uses an
        <em>
            ItemTouchHelper
        </em>
        class along with a swipe callback to handle the movement. The callback
        is simple and you will just call your adapter’s
        <code>
            removeRow
        </code>
        method in the
        <code>
            onSwiped
        </code>
        callback.
    </p>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        and add the following at the bottom of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">SwipeHandler</span></span>(<span class="hljs-keyword">val</span> adapter: PhotoAdapter, dragDirs : <span class="hljs-built_in">Int</span>, swipeDirs : <span class="hljs-built_in">Int</span>) : ItemTouchHelper.SimpleCallback(dragDirs, swipeDirs) {
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onMove</span><span class="hljs-params">(recyclerView: <span class="hljs-type">RecyclerView</span>?, viewHolder: <span class="hljs-type">RecyclerView</span>.<span class="hljs-type">ViewHolder</span>?, target: <span class="hljs-type">RecyclerView</span>.<span class="hljs-type">ViewHolder</span>?)</span></span>: <span class="hljs-built_in">Boolean</span> {
    <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onSwiped</span><span class="hljs-params">(viewHolder: <span class="hljs-type">RecyclerView</span>.<span class="hljs-type">ViewHolder</span>, direction: <span class="hljs-type">Int</span>)</span></span> {
    adapter.removeRow(viewHolder.adapterPosition)
  }
}
</pre>
    <p>
        In
        <code>
            loadPhotos
        </code>
        you will find the following in the
        <code>
            onResponse
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">if</span> (recycler_view.adapter == <span class="hljs-literal">null</span>) {
  <span class="hljs-keyword">val</span> adapter = PhotoAdapter(sortPhotos(body))
  recycler_view.adapter = adapter
</pre>
    <p>
        Add the following after setting the
        <code>
            adapter
        </code>
        value:
    </p>
    <<pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> touchHandler = ItemTouchHelper(SwipeHandler(adapter, <span class="hljs-number">0</span>, (ItemTouchHelper.LEFT or ItemTouchHelper.RIGHT)))
touchHandler.attachToRecyclerView(recycler_view)
</pre>
    <p>
        Run the app and try swiping left or right to delete a row.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/mars5.gif"
        alt="mars rover final screenshot" width="238" height="500" class="aligncenter size-large wp-image-173286">
    </p>
    <p>
        Awesome! You’re just deleting the row from the display in the
        <em>
            RecyclerView
        </em>
        . In another app you would likely delete the item from a database and/or
        make an API call to delete the corresponding item on a server.
    </p>
    <h2>
        Where to go from here
    </h2>
    <div class="inline-video-ad" id="sub-banner-inline">
        <div class="inline-video-ad-wrapper">
            <a href="https://videos.raywenderlich.com/courses" sl-processed="1">
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
        You’ve done a lot of work and now you know how to add animations, provide
        a swipe handler, add section headers, and use the
        <em>
            DiffUtil
        </em>
        class. Well done!
    </p>
    <p>
        A great next step would be to eliminate the
        <em>
            PhotoRow
        </em>
        model class and
        <em>
            DefaultViewHolder
        </em>
        and get the project working with separate Header and Photo model objects and a dedicated
        <em>
            ViewHolder
        </em>
        for each.
    </p>
    <p>
        The final project for this tutorial is available
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/marsrovers-final-1.zip"
        sl-processed="1">
            here
        </a>
        . In the final project, be sure to remember to set the API key in
        <em>
            NasaApi.kt
        </em>
        .
    </p>
    <p>
        If you need more information on
        <em>
            RecyclerView
        </em>
        s, you can check out the following Android developer documentation:
    </p>
    <ul>
        <li>
            <a href="https://developer.android.com/guide/topics/ui/layout/recyclerview.html"
            sl-processed="1">
                Recyclerview Layouts
            </a>
        </li>
        <li>
            <a href="https://developer.android.com/reference/android/support/v7/widget/RecyclerView.html"
            sl-processed="1">
                RecyclerView Class
            </a>
        </li>
        <li>
            <a href="https://developer.android.com/reference/android/support/v7/util/DiffUtil.html"
            sl-processed="1">
                DiffUtil Class
            </a>
        </li>
    </ul>
    <p>
        Go forward and make great animated
        <em>
            RecyclerView
        </em>
        s!
    </p>
</div>

