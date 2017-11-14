# ViewPager教程：入门 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/169774/viewpager-tutorial-android-getting-started-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-250x250.png"
            alt="" width="250" height="250" class="alignright size-thumbnail wp-image-175579"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/11/Viewpager-feature-128x128.png 128w"
            sizes="(max-width: 250px) 100vw, 250px">
        </a>
        <code>
            ViewPager
        </code>
        是一个非常有用的布局管理器，可以帮你的app集成水平swipe的导航方式。它一种创建幻灯片，流程页和tab视图的常用方法。利用swipe手势在ViewPager的不同页面之间进行切换，可以让你节约屏幕的空间，以创建最紧凑的界面。
    </p>
    <p>
        在本教程中，你会将通过将一个已有的app优化成更棒的样子，来熟悉
        <code>
            ViewPager
        </code>
        。你将通过这个过程学到：
    </p>
    <ul>
        <li>
            <code>
                ViewPager
            </code>
            如何工作
        </li>
        <li>
            如何使它的内存使用更具效率
        </li>
        <li>
            如何向你的
            <code>
                ViewPager
            </code>
            添加一些超棒的功能
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                注意：
            </em>
            本教程假定你之前已有了一定使用
            <em>
                Kotlin
            </em>
            开发Android的经验。如果你还不熟悉这门语言，可以参考
            <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Kotlin%20For%20Android%20An%20Introduction.md"
            target="_blank">
                这篇教程
            </a>
            。如果你是一个Android的新手，请访问
            <a href="https://www.raywenderlich.com/category/android" target="_blank">
                入门
            </a>
            和其它的Android教程。
        </p>
    </div>
    <h2>
        入门
    </h2>
    <p>
        下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/FavoriteMovies-starter.zip">
            starter project
        </a>
        ，并使用
        <em>
            Android Studio
        </em>
        的
        <em>
            Open an existing Android Studio project
        </em>
        打开它：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/Screen-Shot-2017-10-30-at-1.54.21-PM.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/Screen-Shot-2017-10-30-at-1.54.21-PM-410x320.png"
            alt="Open an existing Android Studio project" width="410" height="320"
            class="aligncenter size-medium wp-image-175287" srcset="https://koenig-media.raywenderlich.com/uploads/2017/11/Screen-Shot-2017-10-30-at-1.54.21-PM-410x320.png 410w, https://koenig-media.raywenderlich.com/uploads/2017/11/Screen-Shot-2017-10-30-at-1.54.21-PM-641x500.png 641w, https://koenig-media.raywenderlich.com/uploads/2017/11/Screen-Shot-2017-10-30-at-1.54.21-PM.png 1054w"
            sizes="(max-width: 410px) 100vw, 410px">
        </a>
    </p>
    <p>
        找到项目目录，并点击
        <em>
            Open
        </em>
        。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/select-project.png"
        alt="select the project" width="547" height="372" class="aligncenter size-full wp-image-169789"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/select-project.png 547w, https://koenig-media.raywenderlich.com/uploads/2017/08/select-project-471x320.png 471w"
        sizes="(max-width: 547px) 100vw, 547px">
    </p>
    <p>
        在开始教程前，首先浏览一下已有的代码。在
        <em>
            assets
        </em>
        目录中，有一个JSON文件，包含了最受欢迎的5部Android相关的电影。:]
    </p>
    <p>
        你可以在
        <em>
            MovieHelper.kt
        </em>
        中找到用来读取JSON数据的助手方法。
        <a href="http://square.github.io/picasso/" target="_blank">
            The Picasso library
        </a>
        可以用来方便地下载图片，并将其展示到屏幕上。
    </p>
    <p>
        本教程会用到fragment。如果你还尚不熟悉它，可以参考
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Android%20Fragments%20Tutorial%20An%20Introduction%20with%20Kotlin.md"
        target="_blank">
            这篇教程
        </a>
        。
    </p>
    <p>
        运行项目。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/favoritemovies-starter.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/favoritemovies-starter.gif"
            alt="Running Starter Project" width="282" height="500" class="aligncenter size-large wp-image-175289">
        </a>
    </p>
    <p>
        这个app中包含了几个页面，每个页面都展示了关于一部电影的相关信息。我赌你想尝试的第一件事，就是向左swipe来查看下一部电影（好吧也许只有我是这样的）！可现在，你只能不怎么优雅地用屏幕底部的Previous和Next按钮来切换页面了。
    </p>
    <h2>
        介绍ViewPager
    </h2>
    <p>
        在UI上添加
        <code>
            ViewPager
        </code>
        ，就可以让用户通过左右swipe以在页面间进行切换。你无需特地去处理过渡的动画和检测swipe的手势，因为ViewPager的实现比你想象中的更加容易。
    </p>
    <p>
        我们把
        <code>
            ViewPager
        </code>
        的实现分为三个部分：
    </p>
    <ul>
        <li>
            添加
            <code>
                ViewPager
            </code>
        </li>
        <li>
            为
            <code>
                ViewPager
            </code>
            创建
            <code>
                Adapter
            </code>
        </li>
        <li>
            将
            <code>
                ViewPager
            </code>
            和
            <code>
                Adapter
            </code>
            连接到一起
        </li>
    </ul>
    <h3>
        准备ViewPager
    </h3>
    <p>
        第一步，打开
        <em>
            MainActivity.kt
        </em>
        ，删除
        <code>
            onCreate()
        </code>
        方法中，位于这行代码之后的所有代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> movies = MovieHelper.getMoviesFromJson(<span class="hljs-string">"movies.json"</span>, <span class="hljs-keyword">this</span>)</pre>
    <p>
        然后删除这个类尾部的
        <code>
            replaceFragment()
        </code>
        方法。
    </p>
    <p>
        现在，打开
        <em>
            activity_main.xml
        </em>
        并使用下列的代码替换
        <code>
            RelativeLayout
        </code>
        中所有的内容：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.v4.view.ViewPager</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/viewPager"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span> /&gt;</span>
</pre>
    <p>
        这样你就创建了一个
        <code>
            ViewPager
        </code>
        view，它是
        <code>
            RelativeLayout
        </code>
        的唯一子元素。这个xml文件现在应当是这个样子：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">RelativeLayout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
                <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
                <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
                <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
                <span class="hljs-attr">tools:context</span>=<span class="hljs-string">"com.raywenderlich.favoritemovies.MainActivity"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">android.support.v4.view.ViewPager</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/viewPager"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span> /&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">RelativeLayout</span>&gt;</span></pre>
    <p>
        <code>
            ViewPager
        </code>
        只可以通过Android的支持库来使用。
        <i>
            Android的支持库
        </i>
        是一系列小库的集合，它提供了一些控件的向后兼容能力和其它标准的Android功能。这些库提供了通用的API，使得在只能支持较低API级别的设备上，也可以使用新版本Android SDK中的功能。你可以通过访问
        <a href="https://developer.android.com/topic/libraries/support-library/index.html"
        target="_blank">
            Support Library
        </a>
        和
        <a href="https://developer.android.com/topic/libraries/support-library/packages.html"
        target="_blank">
            Support Library Packages
        </a>
        来熟悉它。
    </p>
    <p>
        回到
        <em>
            MainActivity.kt
        </em>
        ，并添加下列的代码来import
        <code>
            ViewPager
        </code>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v4.view.ViewPager</pre>
    <p>
        现在，添加下列的代码到类的顶部，来声明
        <code>
            ViewPager
        </code>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> viewPager: ViewPager</pre>
    <div class="note">
        <p>
            <em>
                注意：
            </em>
            使用关键字
            Use the keyword
            <code>
                lateinit
            </code>
            可以使viewPager惰性初始化，同时避免它会为空。你可以在
            <a href="https://kotlinlang.org/docs/reference/properties.html#late-initialized-properties"
            target="_blank">
                这里
            </a>
            阅读更多关于
            <code>
                lateinit
            </code>
            和其它Kotlin修饰符的相关知识。
        </p>
    </div>
    <p>
        添加下列的代码到
        <code>
            onCreate()
        </code>
        方法的底部，来连接你的
        <code>
            ViewPager
        </code>
        引用到你之前创建的xml视图上：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">viewPager = findViewById(R.id.viewPager)</pre>
    <h3>
        实现PagerAdapter
    </h3>
    <p>
        第一步完成了！你现在已有了一个
        <code>
            ViewPager
        </code>
        ，但必须借由
        <em>
            Adapter
        </em>
        来告诉它该展示什么，它才能做一些有趣的事情。如果现在运行app，你不会看到任何的movie：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509386896.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509386896-281x500.png"
            alt="Empty Screen" width="281" height="500" class="aligncenter size-large wp-image-175291"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509386896-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509386896-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509386896.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        <code>
            ViewPager
        </code>
        通常会使用fragment来展示它的“页”，但如果你想展示静态内容的话，它也可以使用类似
        <code>
            ImageView
        </code>
        这样简单的view来代表页。在本项目中，每页都会展示多项的内容。因此选用
        <code>
            Fragments
        </code>
        。
    </p>
    <p>
        你将使用一个
        <em>
            PagerAdapter
        </em>
        来将
        <code>
            Fragment
        </code>
        实例和
        <code>
            ViewPager
        </code>
        连接起来。PagerAdapter是一个可以将
        <code>
            ViewPager
        </code>
        和你想让它去展示的数据集（本例中就是电影的数组了）连接起来的对象。
        <code>
            PagerAdapter
        </code>
        会创建每个
        <code>
            Fragment
        </code>
        ，并为它添加相应的电影数据，并返回给
        <code>
            ViewPager
        </code>
        。
    </p>
    <p>
        <code>
            PagerAdapter
        </code>
        是一个抽象类，因此你只能实例化它的子类（
        <code>
            FragmentPagerAdapter
        </code>
        和
        <code>
            FragmentStatePagerAdapter
        </code>
        ）。
    </p>
    <h3>
        FragmentPagerAdapter或FragmentStatePagerAdapter？
    </h3>
    <p>
        There are two types of standard
        <code>
            PagerAdapters
        </code>
        that manage the lifecycle of each fragment:
        <em>
            FragmentPagerAdapter
        </em>
        and
        <em>
            FragmentStatePagerAdapter
        </em>
        . Both of them work well with fragments, but they are better suited for different scenarios:
    </p>
    <ul>
        <li>
            The
            <em>
                FragmentPagerAdapter
            </em>
            stores the fragments in memory as long as the user can navigate between them. 
            When a fragment is not visible, the
            <code>
                PagerAdapter
            </code>
            will detach it, but not destroy it, 
            so the fragment instance remains alive in the
            <code>
                FragmentManager
            </code>
            . It will release it from memory only when the
            <code>
                Activity
            </code>
            shuts down. 
            This can make the transition between pages fast and smooth,
            but it could cause memory issues in your app if you need many fragments.
        </li>
        <li>
            The
            <em>
                FragmentStatePagerAdapter
            </em>
            makes sure to destroy all the fragments the user does not see and only keep their saved states in the
            <code>
                FragmentManager
            </code>
            , hence the name. When the user navigates back to a fragment, 
            it will restore it using the saved state. This
            <code>
                PagerAdapter
            </code>
            requires much less memory, 
            but the process of switching between pages can be slower.
        </li>
    </ul>
    <p>
        It’s time to decide. Your list of movies has only five items, so the
        <code>
            FragmentPagerAdapter
        </code>
        might work after all. But what if you get bored after this tutorial and
        watch all Harry Potter movies? You’ll have to add 8 more items to the JSON
        file. What if you then decide to add your favorite TV series as well? That
        array can become pretty large. In this case, the
        <code>
            FragmentStatePagerAdapter
        </code>
        works better.
    </p>
    <h3>
        Creating a Custom FragmentStatePagerAdapter
    </h3>
    <p>
        In the project navigator pane, right-click on
        <em>
            com.raywenderlich.favoritemovies
        </em>
        and select
        <em>
            New
        </em>
        -&gt;
        <em>
            Kotlin File/Class
        </em>
        . Name it
        <em>
            MoviesPagerAdapter
        </em>
        and select
        <em>
            Class
        </em>
        for Kind. Hit
        <em>
            OK
        </em>
        .
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/new-kotlin-file.png"
        alt="new Kotlin file" width="349" height="130" class="aligncenter size-full wp-image-169794">
    </p>
    <p>
        Replace the contents of this file with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">package</span> com.raywenderlich.favoritemovies

<span class="hljs-keyword">import</span> android.support.v4.app.Fragment
<span class="hljs-keyword">import</span> android.support.v4.app.FragmentManager
<span class="hljs-keyword">import</span> android.support.v4.app.FragmentStatePagerAdapter

<span class="hljs-comment">// 1</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MoviesPagerAdapter</span></span>(fragmentManager: FragmentManager, <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> movies: ArrayList&lt;Movie&gt;) : 
    FragmentStatePagerAdapter(fragmentManager) {

  <span class="hljs-comment">// 2 &nbsp; </span>
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getItem</span><span class="hljs-params">(position: <span class="hljs-type">Int</span>)</span></span>: Fragment {
    <span class="hljs-keyword">return</span> MovieFragment.newInstance(movies[position])
  }

  <span class="hljs-comment">// 3 &nbsp;</span>
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getCount</span><span class="hljs-params">()</span></span>: <span class="hljs-built_in">Int</span> {
    <span class="hljs-keyword">return</span> movies.size
  }
}</pre>
    <p>
        Let’s go over this step-by-step.
    </p>
    <ol>
        <li>
            Your new class extends
            <code>
                FragmentStatePagerAdapter
            </code>
            . The constructor of the superclass requires a
            <code>
                FragmentManager
            </code>
            , thus your custom
            <code>
                PagerAdapter
            </code>
            needs it as well. You also need to provide the list of movies as a parameter.
        </li>
        <li>
            Return the fragment associated with the object located at the specified
            position.
        </li>
        <li>
            Return the number of objects in the array.
        </li>
    </ol>
    <p>
        When the
        <code>
            ViewPager
        </code>
        needs to display a fragment, it initiates a chat with the
        <code>
            PagerAdapter
        </code>
        . First, the
        <code>
            ViewPager
        </code>
        asks the
        <code>
            PagerAdapter
        </code>
        how many movies are in the array by calling
        <code>
            getCount()
        </code>
        . Then it will call
        <code>
            getItem(int position)
        </code>
        whenever a new page is about to be visible. Within this method, the
        <code>
            PagerAdapter
        </code>
        creates a new fragment that displays the information about the movie at
        the correct position in the array.&nbsp;
    </p>
    <h3>
        Connecting the PagerAdapter and the ViewPager
    </h3>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        and add the following line at the top to declare your
        <code>
            MoviesPagerAdapter
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> pagerAdapter: MoviesPagerAdapter</pre>
    <p>
        Next add the following inside
        <code>
            onCreate()
        </code>
        , beneath the existing code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">pagerAdapter = MoviesPagerAdapter(supportFragmentManager, movies)
viewPager.adapter = pagerAdapter</pre>
    <p>
        This initializes your
        <code>
            MoviesPagerAdapter
        </code>
        and connects it to the
        <code>
            ViewPager
        </code>
        .&nbsp;
    </p>
    <div class="note">
        <p>
            <em>
                Note:
            </em>
            <code>
                supportFragmentManager
            </code>
            is equivalent to the
            <code>
                getSupportFragmentManager()
            </code>
            method you would use in Java and
            <code>
                viewPager.adapter = pagerAdapter
            </code>
            is the same as
            <code>
                viewPager.setAdapter(pagerAdapter)
            </code>
            . Read more about
            <i>
                getters and setters
            </i>
            in Kotlin
            <a href="https://kotlinlang.org/docs/reference/properties.html#getters-and-setters"
            target="_blank">
                here
            </a>
            .
        </p>
    </div>
    <p>
        Build and run. The app should behave like the original version, but you
        can now navigate between movies by swiping rather than pressing buttons
        :].
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/swipe.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/swipe.gif"
            alt="Swiping ViewPager" width="282" height="500" class="aligncenter size-large wp-image-175295">
        </a>
    </p>
    <div class="note">
        <p>
            <em>
                Note:
            </em>
            Using the
            <code>
                FragmentStatePagerAdapter
            </code>
            saves you from having to deal with saving the current page across a runtime
            configuration change, like rotating the device. The state of the
            <code>
                Activity
            </code>
            is usually lost in those situations and you would have to save it in the
            <code>
                Bundle
            </code>
            object passed as a parameter in
            <code>
                onCreate(savedInstanceState: Bundle?)
            </code>
            . Luckily, the
            <code>
                PagerAdapter
            </code>
            you used does all the work for you. You can read more about the
            <code>
                savedInstanceState
            </code>
            object and the
            <code>
                Activity
            </code>
            lifecycle
            <a href="https://developer.android.com/guide/components/activities/activity-lifecycle.html"
            target="_blank">
                here
            </a>
            .
        </p>
    </div>
    <h3>
        Endless Scrolling
    </h3>
    <p>
        A nice feature you often see is being able to swipe continuously between
        pages in a circular manner. That is going to the last page when swiping
        right on the first one and going to the first one when swiping left on
        the last. For example, swiping between 3 pages would look like this:&nbsp;
    </p>
    <p>
        Page1 -&gt; Page2 -&gt; Page3 -&gt; Page1 -&gt; Page2
    </p>
    <p>
        Page2 &lt;- Page1 &lt;- Page3 &lt;- Page2 &lt;- Page1
    </p>
    <p>
        The
        <code>
            FragmentStatePagerAdapter
        </code>
        will stop creating new fragments when the current index reaches the number
        of objects returned by
        <code>
            getCount()
        </code>
        , so you need to change the method to return a fairly large number that
        the users are not very likely to reach by continuously swiping in the same
        direction. That way the
        <code>
            PagerAdapter
        </code>
        will keep creating pages until the page index reaches the value returned
        by
        <code>
            getCount()
        </code>
        .
    </p>
    <p>
        Open
        <em>
            MoviesPagerAdapter.kt
        </em>
        and create a new constant representing the large number by adding this
        line at the top of the file above the class definition:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> const <span class="hljs-keyword">val</span> MAX_VALUE = <span class="hljs-number">200</span></pre>
    <p>
        Now replace the
        <code>
            return movies.size
        </code>
        line inside
        <code>
            getCount()
        </code>
        with this:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">return</span> movies.size * MAX_VALUE</pre>
    <p>
        By multiplying the length of the array with
        <code>
            MAX_VALUE
        </code>
        , the swipe limit will grow proportionally to the number of movies in
        your list. This way you don’t have to worry about
        <code>
            getCount()
        </code>
        returning a number that is less than the number of movies as your movie
        list grows.
    </p>
    <p>
        The only problem you now have is inside the Adapter’s
        <code>
            getItem(position: Int)
        </code>
        method. Since
        <code>
            getCount()
        </code>
        now returns a number larger than the size of the list, the
        <code>
            ViewPager
        </code>
        will try to access the movie at an index greater than the array size when
        the user swipes past the last movie.
    </p>
    <p>
        Replace the code inside
        <code>
            getItem(position: Int)
        </code>
        with this line:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">return</span> MovieFragment.newInstance(movies[position % movies.size])</pre>
    <p>
        This will ensure that the
        <code>
            ViewPager
        </code>
        doesn’t request the element at an index larger than
        <code>
            movies.size
        </code>
        because the remainder after you divide the position by
        <code>
            movies.size
        </code>
        will always be greater than or equal to 0 and less than
        <code>
            movies.size
        </code>
        .
    </p>
    <p>
        Right now the infinite scrolling works only when the user navigates forward
        through the array (swipes left). That is because, when your app starts,
        the
        <code>
            ViewPager
        </code>
        displays the movie at index 0. To fix this issue, open
        <em>
            MainActivity.kt
        </em>
        and add the following line inside
        <code>
            onCreate()
        </code>
        below the line where you connect the
        <code>
            PageAdapter
        </code>
        to the
        <code>
            ViewPager
        </code>
        :&nbsp;
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">viewPager.currentItem = pagerAdapter.count / <span class="hljs-number">2</span></pre>
    <p>
        This tells the
        <code>
            ViewPager
        </code>
        to display the movie found in the middle of the array. The user has now
        plenty of swiping to do in either direction before they reach an end. To
        ensure that the movie displayed at the beginning will still be the first
        one in your list, set
        <code>
            MAX_VALUE
        </code>
        to be an even number (in this case 200 works fine). This way, after you
        divide
        <code>
            pagerAdapter.count
        </code>
        by 2,
        <code>
            pagerAdapter.count % movies.size = 0
        </code>
        (which is the first index that the
        <code>
            ViewPager
        </code>
        asks for when the app starts).
    </p>
    <p>
        Build and run. You should now be able to swipe left and right a decent
        amount of times and the movies will start again from the beginning after
        you reach the last one and from the end when you reach the first one.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/endless.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/endless.gif"
            alt="Endless scroll" width="282" height="500" class="aligncenter size-large wp-image-175296">
        </a>
    </p>
    <h3>
        Adding Tabs
    </h3>
    <p>
        A
        <a href="https://developer.android.com/reference/android/support/design/widget/TabLayout.html"
        target="_blank">
            TabLayout
        </a>
        is a nice feature that makes it easy to explore and switch between pages.
        The
        <code>
            TabLayout
        </code>
        contains a tab for each page, which usually displays the page title. The
        user can tap on a tab to navigate directly to the desired page or can use
        a swipe gesture over the
        <code>
            TabLayout
        </code>
        to switch between pages.
    </p>
    <p>
        If you try to add a
        <code>
            TabLayout
        </code>
        to your
        <code>
            ViewPager
        </code>
        you won’t be able to see any tabs because the layout will be automatically
        populated with as many tabs as the
        <code>
            FragmentStatePagerAdapter
        </code>
        tells it by calling the
        <code>
            getCount()
        </code>
        method, which now returns a pretty large number. Trying to fit that many
        tabs on your screen will make them really narrow.
    </p>
    <p>
        Luckily, there is a third party library called
        <a href="https://github.com/nshmura/RecyclerTabLayout" target="_blank">
            RecyclerTabLayout
        </a>
        that solves this problem. The library uses the
        <code>
            RecyclerView
        </code>
        in its implementation. You can learn more about the mysterious
        <code>
            RecyclerView
        </code>
        from
        <a href="https://www.raywenderlich.com/126528/android-recyclerview-tutorial"
        target="_blank">
            this tutorial
        </a>
        . To install the library, open up
        <code>
            build.grade (Module: app)
        </code>
        and add the following line inside
        <code>
            dependencies
        </code>
        :
    </p>
    <pre lang="groovy" class="language-groovy">implementation 'com.nshmura:recyclertablayout:1.5.0'
</pre>
    <p>
        The recyclertablayout library uses an old version of the Android Support
        Libraries, so you’ll need to add the following to make the Gradle sync
        happy:
    </p>
    <pre lang="groovy" class="language-groovy">implementation 'com.android.support:recyclerview-v7:26.1.0'
</pre>
    <p>
        Tap
        <em>
            Sync Now
        </em>
        on the yellow pop-up and wait until Android Studio installs the library.
    </p>
    <p>
        Open
        <em>
            activity_main.xml
        </em>
        and paste the following snippet above the
        <code>
            ViewPager
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">com.nshmura.recyclertablayout.RecyclerTabLayout</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/recyclerTabLayout"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"@dimen/tabs_height"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span> /&gt;</span></pre>
    <p>
        Now add the following property to your
        <code>
            ViewPager
        </code>
        to align it below the
        <code>
            RecyclerTabLayout
        </code>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">android:layout_below="@id/recyclerTabLayout"</pre>
    <p>
        Your whole layout file should now look like this:
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">RelativeLayout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
                <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
                <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
                <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
                <span class="hljs-attr">tools:context</span>=<span class="hljs-string">"com.raywenderlich.favoritemovies.MainActivity"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">com.nshmura.recyclertablayout.RecyclerTabLayout</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/recyclerTabLayout"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"@dimen/tabs_height"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span> /&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">android.support.v4.view.ViewPager</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/viewPager"</span>
      <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@id/recyclerTabLayout"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span> /&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">RelativeLayout</span>&gt;</span></pre>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        and import
        <code>
            RecyclerTabLayout
        </code>
        at the top of the file, like this:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> com.nshmura.recyclertablayout.RecyclerTabLayout</pre>
    <p>
        Now add the following at the top of the class to declare a
        <code>
            RecyclerTabLayout
        </code>
        instance:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> recyclerTabLayout: RecyclerTabLayout</pre>
    <p>
        Add this block of code inside
        <code>
            onCreate()
        </code>
        , above the line where you set
        <code>
            viewPager.currentItem
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">recyclerTabLayout = findViewById(R.id.recyclerTabLayout)
recyclerTabLayout.setUpWithViewPager(viewPager)</pre>
    <p>
        The first line connects your
        <code>
            RecyclerTabLayout
        </code>
        instance to the xml view and the second one links the
        <code>
            RecyclerTabLayout
        </code>
        to your
        <code>
            ViewPager
        </code>
        .
    </p>
    <p>
        The last thing you have to do is let the
        <code>
            RecyclerTabLayout
        </code>
        know what titles to display on the Tabs. Open
        <em>
            MoviesPagerAdapter.kt
        </em>
        and add the following method inside the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getPageTitle</span><span class="hljs-params">(position: <span class="hljs-type">Int</span>)</span></span>: CharSequence {
  <span class="hljs-keyword">return</span> movies[position % movies.size].title
}</pre>
    <p>
        This method tells the
        <code>
            TabLayout
        </code>
        what to write on the tab placed at a particular position. It returns the
        title of the movie that corresponds with the fragment created inside
        <code>
            getItem(position: Int)
        </code>
        .
    </p>
    <p>
        Run the app. You should be able to see the tabs changing as you swipe
        through the pages. Try tapping on a tab and see how the
        <code>
            ViewPager
        </code>
        will scroll automatically to the corresponding movie :].
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/tabs.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/tabs.gif"
            alt="Tabs" width="281" height="500" class="aligncenter size-large wp-image-175301">
        </a>
    </p>
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
        You can download the final project for this tutorial
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/FavoriteMovies-final.zip">
            here
        </a>
        .
    </p>
    <p>
        Nice job! You’ve modified an app and gave it a nicer UI with the help
        of
        <code>
            ViewPager
        </code>
        . You’ve also added a pretty cool
        <code>
            TabLayout
        </code>
        and implemented the endless scroll. In addition, you learned about the
        <code>
            PagerAdapter
        </code>
        and had to choose which of the
        <code>
            FragmentPagerAdapter
        </code>
        and
        <code>
            FragmentStatePagerAdapter
        </code>
        is best for you application.&nbsp;
    </p>
    <p>
        If you want to read more about the
        <code>
            ViewPager
        </code>
        have a look at the
        <a href="https://developer.android.com/reference/android/support/v4/view/ViewPager.html"
        target="_blank">
            documentation
        </a>
        . You can try and customize the transition animation with the help of
        <code>
            PageTransformer
        </code>
        . Check out
        <a href="https://developer.android.com/training/animation/screen-slide.html#pagetransformer"
        target="_blank">
            this tutorial
        </a>
        for that.
    </p>
    <p>
        <em>
            Bonus challenge:
        </em>
        You can implement dot indicators for your pages as seen in many onboarding
        flows.
        <a href="https://stackoverflow.com/questions/38459309/how-do-you-create-an-android-view-pager-with-a-dots-indicator"
        target="_blank">
            Here
        </a>
        you can find a nice way of creating dot indicators. Note that this solution
        won’t work with your final
        <code>
            ViewPager
        </code>
        from this tutorial as it needs
        <code>
            PagerAdapter
        </code>
        ‘s
        <code>
            getCount()
        </code>
        method to return the exact number of pages. You can try implementing the
        indicators instead of the endless scroll. This time try using the default
        <a href="https://developer.android.com/reference/android/support/design/widget/TabLayout.html"
        target="_blank">
            TabLayout
        </a>
        instead of the third party library. You can download the solution
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/FavoriteMovies-challenge.zip">
            here
        </a>
        .
    </p>
</div>