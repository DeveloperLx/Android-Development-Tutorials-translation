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
        这里有两个类型的标准
        <code>
            PagerAdapters
        </code>
        来管理每个fragment的生命周期：
        <em>
            FragmentPagerAdapter
        </em>
        和
        <em>
            FragmentStatePagerAdapter
        </em>
        。他们每个都可以很好地处理fragment，但适宜的场景却有所不同：
    </p>
    <ul>
        <li>
            <em>
                FragmentPagerAdapter
            </em>
            会把需要进行切换的fragment储存到内存中。当fragment不在可见的时候，
            <code>
                PagerAdapter
            </code>
            会将其分离，而不是摧毁它，因此fragment仍然存活在
            <code>
                FragmentManager
            </code>
            中。fragment会在它所在的
            <code>
                Activity
            </code>
            被关闭的时候，才会关闭。这样可以使得页面之间的切换快速而平滑，且在fragment较多时不引起内存的问题。
        </li>
        <li>
            <em>
                FragmentStatePagerAdapter
            </em>
            会将所有用户无法看到的fragment进行销毁，只把它们的states保存到
            <code>
                FragmentManager
            </code>
            中，因此得到了这个名字。当用户再返回到这个fragment的时候，就会使用之前保存的state来恢复它。这个
            <code>
                PagerAdapter
            </code>
            所需的内存较少，但处理页面之间的切换过程也较慢。
        </li>
    </ul>
    <p>
        该做决定了。你的电影列表中只有5个项目，因此对于
        <code>
            FragmentPagerAdapter
        </code>
        来说一定是OK的。但如果在完成本教程后你感到无聊，想把所有哈利波特的电影都添加进来呢？你不得不再添加8个item到项目的JSON文件中。如果你又想把最喜爱的电视剧添加进来呢？这个数据就会变得相当得大。在本例中，使用
        <code>
            FragmentStatePagerAdapter
        </code>
        就会更棒一些。
    </p>
    <h3>
        创建一个自定义的FragmentStatePagerAdapter
    </h3>
    <p>
        在项目导航面板中，右击
        <em>
            com.raywenderlich.favoritemovies
        </em>
        并选择
        <em>
            New
        </em>
        - 
        <em>
            Kotlin File/Class
        </em>
        。将其命名为
        <em>
            MoviesPagerAdapter
        </em>
        ，并选择Kind为
        <em>
            Class
        </em>
        。点击
        <em>
            OK
        </em>
        。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/new-kotlin-file.png"
        alt="new Kotlin file" width="349" height="130" class="aligncenter size-full wp-image-169794">
    </p>
    <p>
        将文件的内容替换为下列的代码：
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
        一步一步地看：
    </p>
    <ol>
        <li>
            这个类继承自
            <code>
                FragmentStatePagerAdapter
            </code>
            。父类的构造器需要一个
            <code>
                FragmentManager
            </code>
            的参数，因此你自定义的
            <code>
                PagerAdapter
            </code>
            也继承了这点。你还需要提供一个电影的列表作为参数。
        </li>
        <li>
            返回关联到指定索引电影的fragment。
        </li>
        <li>
            返回数组中对象的数量。
        </li>
    </ol>
    <p>
        当
        <code>
            ViewPager
        </code>
        需要展示fragment的时候，它就会开启一个和
        <code>
            PagerAdapter
        </code>
        的对话。首先，
        <code>
            ViewPager
        </code>
        会通过调用
        <code>
            getCount()
        </code>
        来询问
        <code>
            PagerAdapter
        </code>
        数组中有多少部电影
        <code>
            getCount()
        </code>
        。然后当将要展示一个页的时候，就会调用它的
        <code>
            getItem(int position)
        </code>
        方法。在该方法中，
        <code>
            PagerAdapter
        </code>
        创建了一个新的fragment，用来展示数组中相应电影的信息。
    </p>
    <h3>
        连接PagerAdapter和ViewPager
    </h3>
    <p>
        打开
        <em>
            MainActivity.kt
        </em>
        ，并添加下列的代码到文件的顶部来声明你的
        <code>
            MoviesPagerAdapter
        </code>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> pagerAdapter: MoviesPagerAdapter</pre>
    <p>
        接下来添加下列的代码到
        <code>
            onCreate()
        </code>
        方法中，已存在代码的后面：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">pagerAdapter = MoviesPagerAdapter(supportFragmentManager, movies)
viewPager.adapter = pagerAdapter</pre>
    <p>
        这样就初始化了
        <code>
            MoviesPagerAdapter
        </code>
        ，并连接到
        <code>
            ViewPager
        </code>
        上。
    </p>
    <div class="note">
        <p>
            <em>
                注意：
            </em>
            这里的
            <code>
                supportFragmentManager
            </code>
            就等价于你在Java中使用的
            <code>
                getSupportFragmentManager()
            </code>
            方法，而
            <code>
                viewPager.adapter = pagerAdapter
            </code>
            则相对于
            <code>
                viewPager.setAdapter(pagerAdapter)
            </code>
            。你可以在
            <a href="https://kotlinlang.org/docs/reference/properties.html#getters-and-setters"
            target="_blank">
                这里
            </a>
            阅读更多关于Kotlin中
            <i>
                getters和setters
            </i>
            相关的内容。
        </p>
    </div>
    <p>
        运行项目。看起来和原始的版本一样，但是现在，你就可以通过swipe而不是按下按钮来切换电影了。:]
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
                注意：
            </em>
            使用
            <code>
                FragmentStatePagerAdapter
            </code>
            ，可以使你避免处理因运行时configuration发生变化，不得不保存当前页面的问题。比如旋转设备。
            <code>
                Activity
            </code>
            的state在这些情形下通常会丢失，因而你不得不将它保存到
            <code>
                onCreate(savedInstanceState: Bundle?)
            </code>
            的
            <code>
                Bundle
            </code>
            对象中。幸运的是，
            <code>
                PagerAdapter
            </code>
            为你做好了所有的工作。你可以在
            <a href="https://developer.android.com/guide/components/activities/activity-lifecycle.html"
            target="_blank">
                这里
            </a>
            阅读更多关于
            <code>
                savedInstanceState
            </code>
            对象和
            <code>
                Activity
            </code>
            生命周期的相关内容。
        </p>
    </div>
    <h3>
        无穷的滚动
    </h3>
    <p>
        你经常会看到的一个很棒的功能，就是在页面之间可以持续地循环进行swipe。你在第一页上向右swipe，就可以切到最后一页上。反之亦反。例如，在三个页面上进行swipe将会看到如下的内容：
    </p>
    <p>
        Page1 -&gt; Page2 -&gt; Page3 -&gt; Page1 -&gt; Page2
    </p>
    <p>
        Page2 &lt;- Page1 &lt;- Page3 &lt;- Page2 &lt;- Page1
    </p>
    <p>
        当当前的索引增长到等于由
        <code>
            getCount()
        </code>
        返回的对象的数量时，
        <code>
            FragmentStatePagerAdapter
        </code>
        就会停止创建新的fragment。因此，你要让这个方法返回一个相当大的数，使得用户即使以相同方向持续swipe，也难以到头。这样，
        <code>
            PagerAdapter
        </code>
        就会持续地创建页，直到页面的索引到达
        <code>
            getCount()
        </code>
        返回的值。
    </p>
    <p>
        打开
        <em>
            MoviesPagerAdapter.kt
        </em>
        并通过添加下列的代码，创建一个常量来代表这个大数：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> const <span class="hljs-keyword">val</span> MAX_VALUE = <span class="hljs-number">200</span></pre>
    <p>
        现在，将
        <code>
            getCount()
        </code>
        方法中的
        <code>
            return movies.size
        </code>
        这行替换为下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">return</span> movies.size * MAX_VALUE</pre>
    <p>
        通过和
        <code>
            MAX_VALUE
        </code>
        相乘，swipe的限制就可以正比例于电影的数量进行增长了。这样你就无需担心
        <code>
            getCount()
        </code>
        会返回一个比你电影的数量还小的值了。
    </p>
    <p>
        剩下的问题就在
        <code>
            getItem(position: Int)
        </code>
        方法中了。因为
        <code>
            getCount()
        </code>
        会返回一个比电影的数量还大的值，
        <code>
            ViewPager
        </code>
        在访问电影的时候就出出现数组越界的问题。
    </p>
    <p>
        将
        <code>
            getItem(position: Int)
        </code>
        的内容替换为下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">return</span> MovieFragment.newInstance(movies[position % movies.size])</pre>
    <p>
        这样就确保了
        <code>
            ViewPager
        </code>
        对数组的访问一定不会越界。
    </p>
    <p>
        现在只有当用户向前浏览数组（也就是向左swipe）的时候，无穷的滚动才能发挥作用。这是因为，当你启动app的时候，
        <code>
            ViewPager
        </code>
        只会展示索引为0的电影。为了修复这个问题，打开
        <em>
            MainActivity.kt
        </em>
        并添加下列的代码到
        <code>
            onCreate()
        </code>
        中，就在你连接
        <code>
            PageAdapter
        </code>
        到
        <code>
            ViewPager
        </code>
        的那行代码之下：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">viewPager.currentItem = pagerAdapter.count / <span class="hljs-number">2</span></pre>
    <p>
        这样就会让
        <code>
            ViewPager
        </code>
        展示数组中间的那部电影。现在用户就可以在两个方向上都有大量的swipe操作了，直到结束之前。为了确保在开始时展示的电影仍然是你列表中的第一项，必须将
        <code>
            MAX_VALUE
        </code>
        设置为一个偶数（例如本例中的200就可以）。
    </p>
    <p>
        运行项目，你现在就可以向左或向右swipe相当多的次数了，电影到达最后一部后，就会再从第一部开始，反之亦反。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/endless.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/endless.gif"
            alt="Endless scroll" width="282" height="500" class="aligncenter size-large wp-image-175296">
        </a>
    </p>
    <h3>
        添加Tab
    </h3>
    <p>
        <a href="https://developer.android.com/reference/android/support/design/widget/TabLayout.html"
        target="_blank">
            TabLayout
        </a>
        是一个非常棒的功能，可以让页面之间的切换变得非常容易。
        <code>
            TabLayout
        </code>
        对于每一页都会有一个tab，通常用来展示对应页的标题。用户既可以直接点击一个tab导航到期望的页，也可以swipe
        <code>
            TabLayout
        </code>
        来切换到那个页。
    </p>
    <p>
        如果你尝试添加
        <code>
            TabLayout
        </code>
        到
        <code>
            ViewPager
        </code>
        上，不会看到任何的tab。因为TabLayout会自动被大量的tab填充（tab的数量是由
        <code>
            FragmentStatePagerAdapter
        </code>
        的
        <code>
            getCount()
        </code>
        方法得到的，它给出了一个相当大的数字）。试图在屏幕上同时显示如此多的tab 会让它们变得相当狭小。
    </p>
    <p>
        幸运的是，有一个叫
        <a href="https://github.com/nshmura/RecyclerTabLayout" target="_blank">
            RecyclerTabLayout
        </a>
        的第三方库可以解决这个问题。它使用
        <code>
            RecyclerView
        </code>
        来进行实现。你可以在
        <a href="https://www.raywenderlich.com/126528/android-recyclerview-tutorial"
        target="_blank">
            这篇教程
        </a>
        中学习更多相关
        <code>
            RecyclerView
        </code>
        的知识。要安装这个库，打开
        <code>
            build.grade (Module: app)
        </code>
        并添加下列的代码到
        <code>
            dependencies
        </code>
        中：
    </p>
    <pre lang="groovy" class="language-groovy">implementation 'com.nshmura:recyclertablayout:1.5.0'
</pre>
    <p>
        RecyclerTabLayout使用了老版本的Android支持库，因此你需要添加以下的内容使Gradle的同步更加顺畅：
    </p>
    <pre lang="groovy" class="language-groovy">implementation 'com.android.support:recyclerview-v7:26.1.0'
</pre>
    <p>
        点击弹出的黄色窗口中的
        <em>
            Sync Now
        </em>
        ，并等待Android Studio进行安装。
    </p>
    <p>
        打开
        <em>
            activity_main.xml
        </em>
        ，并添加下列的代码片段到
        <code>
            ViewPager
        </code>
        上方：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">com.nshmura.recyclertablayout.RecyclerTabLayout</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/recyclerTabLayout"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"@dimen/tabs_height"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span> /&gt;</span></pre>
    <p>
        现在，添加下列的property到你的
        <code>
            ViewPager
        </code>
        上，让它对齐
        <code>
            RecyclerTabLayout
        </code>
        的底部：
    </p>
    <pre lang="xml" class="language-xml hljs">android:layout_below="@id/recyclerTabLayout"</pre>
    <p>
        现在你整个的布局文件看起来应当是这样：
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
        打开
        <em>
            MainActivity.kt
        </em>
        并import
        <code>
            RecyclerTabLayout
        </code>
        到文件的顶部，就像这样：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> com.nshmura.recyclertablayout.RecyclerTabLayout</pre>
    <p>
        现在添加下列的代码到类的顶部，来声明一个
        <code>
            RecyclerTabLayout
        </code>
        的实例：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> recyclerTabLayout: RecyclerTabLayout</pre>
    <p>
        添加下列的代码到
        <code>
            onCreate()
        </code>
        中，就在你设置
        <code>
            viewPager.currentItem
        </code>
        的上方：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">recyclerTabLayout = findViewById(R.id.recyclerTabLayout)
recyclerTabLayout.setUpWithViewPager(viewPager)</pre>
    <p>
        第一行代码将你的
        <code>
            RecyclerTabLayout
        </code>
        实例连接到xml view上，第二行代码则将
        <code>
            RecyclerTabLayout
        </code>
        连接到你的
        <code>
            ViewPager
        </code>
        上。
    </p>
    <p>
        你必须做的最后一件事，就是让
        <code>
            RecyclerTabLayout
        </code>
        知道每个tab上该展示什么标题。打开
        <em>
            MoviesPagerAdapter.kt
        </em>
        ，并添加下列的方法到这个类中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getPageTitle</span><span class="hljs-params">(position: <span class="hljs-type">Int</span>)</span></span>: CharSequence {
  <span class="hljs-keyword">return</span> movies[position % movies.size].title
}</pre>
    <p>
        这个方法就告知了
        <code>
            TabLayout
        </code>
        上的每个tab该展示什么样的内容。也就是对应那部电影的标题。
    </p>
    <p>
        运行app。你会看到当你改变当前页面的时候，tab也会发生相应的变化。尝试点击一个tab，
        <code>
            ViewPager
        </code>
        就会自动滚动到相应的电影上。:]
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/tabs.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/tabs.gif"
            alt="Tabs" width="281" height="500" class="aligncenter size-large wp-image-175301">
        </a>
    </p>
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
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/FavoriteMovies-final.zip">
            这里
        </a>
        下载本教程的最终项目。
    </p>
    <p>
        Nice job！你已在
        <code>
            ViewPager
        </code>
        的帮助下为这个app增加了更棒的UI。你还添加了超酷的
        <code>
            TabLayout
        </code>
        ，并实现了无穷的滚动。除此之外，你还学习了
        <code>
            PagerAdapter
        </code>
        及如何为你的app在
        <code>
            FragmentPagerAdapter
        </code>
        和
        <code>
            FragmentStatePagerAdapter
        </code>
        直接进行选择。
    </p>
    <p>
        如果你想了解更多关于
        <code>
            ViewPager
        </code>
        的内容，请访问
        <a href="https://developer.android.com/reference/android/support/v4/view/ViewPager.html"
        target="_blank">
            documentation
        </a>
        。你可以在
        <code>
            PageTransformer
        </code>
        的帮助下自定义过渡的动画。访问
        <a href="https://developer.android.com/training/animation/screen-slide.html#pagetransformer"
        target="_blank">
            这篇教程
        </a>
        以了解更多的内容。
    </p>
    <p>
        <em>
            额外的挑战：
        </em>
        你可以在很多流程指导页中看到点指示符。你可以在
        <a href="https://stackoverflow.com/questions/38459309/how-do-you-create-an-android-view-pager-with-a-dots-indicator"
        target="_blank">
            这里
        </a>
        找到一个创建点指示符的很好办法。注意这个解决方案并不适用于本教程中完成的
        <code>
            ViewPager
        </code>
        ，因为它需要
        <code>
            PagerAdapter
        </code>
        的
        <code>
            getCount()
        </code>
        方法来返回页面的确切个数。你可以尝试实现指示符以替代无穷滚动的效果。这次可以尝试使用默认的
        <a href="https://developer.android.com/reference/android/support/design/widget/TabLayout.html"
        target="_blank">
            TabLayout
        </a>
        来替代第三方库。你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/FavoriteMovies-challenge.zip">
            这里
        </a>
        下载解决方案。
    </p>
</div>