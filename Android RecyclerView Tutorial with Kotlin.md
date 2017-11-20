# Android RecyclerView教程 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/170075/android-recyclerview-tutorial-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志
            </em>
            ：本教程已由Rod Biresch更新至Kotlin，Android 26 (Oreo)及Android Studio 3.0的版本。原教材由Darryl Bayliss编写。
        </p>
    </div>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-320x320.png"
        alt="RecyclerView-feature" width="250" height="250" class="alignright size-medium wp-image-136529"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-128x128.png 128w"
        sizes="(max-width: 250px) 100vw, 250px">
        <br>
        循环利用是对地球最有益的事之一，这是确保我们不会被自己的垃圾埋埋没且将来不再有足够的资源的共识方法。
    </p>
    <p>
        一些Android工程师明白循环利用的益处，并想把它利用到我们的app上。这个灵感的最终结果，就是数百万的生态战士和循环利用狂热者高兴地发现，Android Lollipop引入了
        <code>
            RecyclerView
        </code>
        组件 - 或是类似的东西。:]
    </p>
    <p>
        还有一件更值得庆祝的事，Google还发布了一个支持库，使这个干净，绿色，可循环利用的机制向后兼容到了Android Eclair（2.2）版本。这个版本早在2010年就已发布！
    </p>
    <p>
        在本教程中，你会在实践中体验RecyclerView的强大，并学习：
    </p>
    <ul>
        <li>
            RecyclerView的目的
        </li>
        <li>
            构成RecyclerView的成分
        </li>
        <li>
            如何修改RecyclerView的布局
        </li>
        <li>
            如何为RecyclerView添加超赞的动画
        </li>
    </ul>
    <p>
        你还会构建一个示例app
        <em>
            Galacticon
        </em>
        来“冲向外太空”。你会使用RecyclerView，基于NASA的公开API，来构建一个日常天文学照片的信息流照片。
    </p>
    <div class="note">
        <p>
            <em>
                预备知识
            </em>
            ：在开始本教程之前，你应当对使用Kotlin开发Android有一定的基本了解。如果你需要温习一下，可以访问我们的
            <a title="Android Tutorials" href="http://www.raywenderlich.com/category/android"
            target="_blank">
                介绍性教程
            </a>
            ！同时，你需要Android Studio 3.0或更高版本的eta。
        </p>
    </div>
    <h2>
        前往Cape Canaveral：入门
    </h2>
    <p>
        下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/galacticon-starter-5.zip">
            初始项目
        </a>
        并在Android Studio中打开。没有太多的东西，包括RecyclerView也找不到。
    </p>
    <p>
        点击顶部的
        <em>
            Run app
        </em>
        按钮，你会看到一些类似所有错误方式外部空间似的东西：
        <br>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1-281x500.png"
        alt="" width="281" height="500" class="aligncenter size-large wp-image-170498"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        它是空的，但没有关系。如果所有的动作都完成了，你学不到什么东西！在添加漂亮的NASA太空图片之前，你需要做一些设置工作。
    </p>
    <h2>
        获取访问Shuttle的（API）Key
    </h2>
    <p>
        你将会使用
        <a href="http://apod.nasa.gov" target="_blank" title="Astronomy Picture of the Day API">
            Astronomy Picture of the Day API
        </a>
        ，它是由NASA提供的最流行的网络服务之一。为确保不被当成未经授权的流量，该服务要求你的app有一个API的key。
    </p>
    <p>
        幸运的是，要获取这个key非常容易，只需将你的名字和邮箱地址填到
        <a href="https://api.nasa.gov/index.html#apply-for-an-api-key" target="_blank"
        title="webpage">
            api.nasa.gov
        </a>
        上，然后把弹出的页面或邮箱地址中的API key粘贴过来即可。
    </p>
    <p>
        获取API key之后，复制它，并在你的项目中打开
        <em>
            strings.xml
        </em>
        文件。将该API key粘贴到
        <code>
            api_key
        </code>
        中，替换掉
        <code>
            INSERT API KEY HERE
        </code>
        ：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-700x296.png"
        alt="4. API_KEY paste" width="700" height="296" class="aligncenter size-large wp-image-126540"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-700x296.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-480x203.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-768x325.png 768w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <h2>
        Space Oddity：学习RecyclerView
    </h2>
    <p>
        你将很快进入到外部空间来探索广袤的RecyclerView，但没有一个能干的司令官，会在没有准备之前就进入未知的领域。在出发之前，你有一些问题。本部分将作为你的一个任务摘要。
    </p>
    <p>
        RecyclerView可以被当做是一个
        <em>
            ListView
        </em>
        和
        <em>
            GridView
        </em>
        的结合体。并且，除了高效的内存模式之外，还具有额外的特性，可以将代码分离成易于维护的组件。
    </p>
    <p>
        但为何它会比你习惯使用的ListView和GridView更好呢？难道采用了某种来自外星的技术？一如既往，答案都在细节当中。
    </p>
    <h3>
        为何需要RecyclerView
    </h3>
    <p>
        想象一下，你在创建一个ListView，但它的item相当得复杂。你需要花时间来为这些item创建行布局，然后在adapter中进行使用。
    </p>
    <p>
        在
        <code>
            getView()
        </code>
        方法中，你inflate了item的布局。然后，通过你在XML文件中提供的唯一id去引用每一个view，来添加一些view的逻辑。然后，再把这个view传递给ListView，这时就可以绘制到屏幕上了。一切看起来都不错...那么？
    </p>
    <p>
        事实是ListView和GridView只完成了正确使用内存的一半的工作。它们循环利用了item的
        <em>
            layout
        </em>
        ，但却并不保留对layout子控件的引用，而是在每次调用
        <code>
            getView()
        </code>
        时，都得为每个子控件重新调用
        <code>
            findViewById()
        </code> 
        。
    </p>
    <p>
        所有的这些调用都
        <i>
            大幅地
        </i>
        增加了处理器的计算量，尤其当item的布局比较复杂的时候。此外，这个情形还会造成ListView的卡顿甚至失去响应，因为它会疯狂地抓取你所需的view的引用。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/02/ListView--700x491.png"
        alt="ListView-" width="600" height="421" class="aligncenter size-large wp-image-126766"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/02/ListView-.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/02/ListView--456x320.png 456w"
        sizes="(max-width: 600px) 100vw, 600px">
    </p>
    <p>
        Android的工程师最初通过
        <code>
            View Holder
        </code>
        模式，提供了一个解决该问题的方法（参见Android开发者网站的
        <a href="http://developer.android.com/training/improving-layouts/smooth-scrolling.html#ViewHolder"
        title="smooth scrolling" target="_blank">
            平滑滚动
        </a>
        ）。
    </p>
    <p>
        当使用这个模式时，你会通过在内存上创建一个对所有所需view的引用来，对布局进行填充。这么做的益处就是只需设置一次引用，然后再复用它即可，有效地解决了因重复地调用
        <code>
            findViewById()
        </code>
        产生的性能问题。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/viewholder_new_larger.png"
        alt="viewholder_new_larger" width="594" height="455" class="aligncenter size-full wp-image-134106"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/05/viewholder_new_larger.png 594w, https://koenig-media.raywenderlich.com/uploads/2016/05/viewholder_new_larger-418x320.png 418w"
        sizes="(max-width: 594px) 100vw, 594px">
    </p>
    <p>
        问题是这只是ListView或GridView的一个可选的模式，如果不了解细节，你可能就会非常奇怪为何ListViews和GridViews如此得慢。
    </p>
    <h2>
        第一次接触：RecyclerView和布局
    </h2>
    <p>
        RecyclerView的到来改变了一切。它仍然使用
        <em>
            Adapter
        </em>
        来充当数据源，但你必须创建
        <em>
            ViewHolders
        </em>
        来在内存中进行持有。
    </p>
    <p>
        当你需要一个新的view时，它会在创建一个新的ViewHolder对象来持有引入并inflate布局，与在已存在对象的栈中复用之间进行选择。
    </p>
    <p>
        现在你就知道它为何被叫做RecyclerView了！
    </p>
    <p>
        使用RecyclerView的另一个好处，是它带有默认的动画，无需你自己去添加。
    </p>
    <p>
        由于对ViewHolder的使用，RecyclerView清楚地知道哪个动画应用于哪个item。最重要的是，它只会按照需求的来做。你甚至可以创建自己的动画，并根据需要来使用它们。
    </p>
    <p>
        RecyclerView的最后一个，也是最重要的一个组件，就是
        <em>
            LayoutManager
        </em>
        了。这个对象被用来确定RecyclerView item的位置，并告诉RecyclerView什么时候来回收移出屏幕外的item。
    </p>
    <p>
        LayoutManager有三种默认的口味：
    </p>
    <ul>
        <li>
            <em>
                LinearLayoutManager
            </em>
            像标准的ListView一样地布局你的item
        </li>
        <li>
            <em>
                GridLayoutManager
            </em>
            类似于GridView一样地布局你的item
        </li>
        <li>
            <em>
                StaggeredGridLayoutManager
            </em>
            会以交错的网格格式来布局你的item。
        </li>
    </ul>
    <p>
        如果想要创建自己的布局，你还可以创建自定义的
        <code>
            LayoutManagers
        </code>
        。
    </p>
    <p>
        希望能够回答你所有的问题，司令官。现在，执行任务！
    </p>
    <h2>
        准备发射：创建RecyclerView
    </h2>
    <p>
        要创建RecyclerView，你有四个部分的工作需要完成：
    </p>
    <ol>
        <li>
            在activity的布局文件中声明RecyclerView，并在相应activity的Kotlin文件中引用它。
        </li>
        <li>
            为你的RecyclerView创建自定义的item XML布局文件。
        </li>
        <li>
            为这个item创建view holder，并连接到RecyclerView的数据源上，然后创建RecyclerView的Adapter来处理view的逻辑。
        </li>
        <li>
            将adapter到RecyclerView上。
        </li>
    </ol>
    <p>
        第一步应当是非常熟悉的。打开
        <em>
            activity_main.xml
        </em>
        布局文件，添加下列的代码作为LinearLayout的子元素：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.RecyclerView</span>
  <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/recyclerView"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:scrollbars</span>=<span class="hljs-string">"vertical"</span>/&gt;</span>
</pre>
    <p>
        这样就设置了RecyclerView的布局，并告知RecyclerView填满它的父布局。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：你使用了v7支持库来向后兼容旧版的设备。初始项目已在app的
            <em>
                build.gradle
            </em>
            文件中添加了对RecyclerView支持库的依赖。如果你想了解更多关于它本身的内容，可以访问
            <a href="http://developer.android.com/tools/support-library/setup.html"
            target="_blank">
                Android开发者网站
            </a>
            。
        </p>
    </div>
    <p>
        打开
        <em>
            MainActivity.kt
        </em>
        ，并在类的顶部声明下列的property：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> linearLayoutManager: LinearLayoutManager
</pre>
    <p>
        在
        <code>
            onCreate()
        </code>
        中，
        <code>
            setContentView
        </code>
        之后添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">linearLayoutManager = LinearLayoutManager(<span class="hljs-keyword">this</span>)
recyclerView.layoutManager = linearLayoutManager
</pre>
    <p>
        Android Studio会提示你为
        <code>
            recyclerView
        </code>
        导入
        <code>
            kotlinx.android.synthetic.main.activity_main.*
        </code>
        。你也许会好奇，为何未首先使用
        <code>
            findViewById()
        </code>
        来获取对
        <code>
            recyclerView
        </code>
        的引用？因为该项目已被配置使用了
        <a href="https://kotlinlang.org/docs/tutorials/android-plugin.html" target="_blank">
            Kotlin Android Extensions
        </a>
        插件，它可以将布局文件中的view自动合成为property。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> kotlinx.android.synthetic.main.activity_main.*
</pre>
    <p>
        <code>
            recyclerView
        </code>
        现在就是
        <code>
            Activity
        </code>
        的一个扩展property了，拥有和在
        <code>
            activity_main.xml
        </code>
        声明的相同的类型。这个插件使得我们略去了很多样板式的代码，并减小了潜在bug的风险。
    </p>
    <p>
        点火的第一阶段已完成了！你已为RecyclerView正常工作所需的两个部分声明并分配了内存：RecyclerView和它的Layout Manager。
    </p>
    <h2>
        点火的第二阶段：布置RecyclerView的Item
    </h2>
    <p>
        点火的第二阶段，是为RecyclerView所使用的item创建自定义的布局。这个过程和你为ListView和Gridview创建自定义的布局是完全一致的。
    </p>
    <p>
        找到layout目录，并创建一个新的名为
        <code>
            recyclerview_item_row
        </code>
        的布局文件，并将根元素设置为
        <code>
            LinearLayout
        </code>
        ，然后添加下列的子元素到它的内部：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">ImageView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/itemImage"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"center"</span>
    <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"8dp"</span>
    <span class="hljs-attr">android:layout_weight</span>=<span class="hljs-string">"3"</span>
    <span class="hljs-attr">android:adjustViewBounds</span>=<span class="hljs-string">"true"</span> /&gt;</span>

<span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/itemDate"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"top|start"</span>
    <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"8dp"</span>
    <span class="hljs-attr">android:layout_weight</span>=<span class="hljs-string">"1"</span>
    <span class="hljs-attr">tools:text</span>=<span class="hljs-string">"Some date"</span> /&gt;</span>

<span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/itemDescription"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"center|start"</span>
    <span class="hljs-attr">android:layout_weight</span>=<span class="hljs-string">"1"</span>
    <span class="hljs-attr">android:ellipsize</span>=<span class="hljs-string">"end"</span>
    <span class="hljs-attr">android:maxLines</span>=<span class="hljs-string">"5"</span> /&gt;</span>
</pre>
    <p>
        这里没有火箭科学，只是在布局中声明了一系列的元素，以便在adapter中进行使用。
    </p>
    <h2>
        Adapter：你的RecyclerView的火箭燃料
    </h2>
    <p>
        右击
        <em>
            com.raywenderlich.galacticon
        </em>
        目录，选择
        <em>
            New / Kotlin File/Class
        </em>
        ，将其命名为
        <em>
            RecyclerAdapter
        </em>
        并选择
        <em>
            Class
        </em>
        作为类型。在文件的顶部，
        <code>
            package
        </code>
        声明的下面，导入支持库版本的RecyclerView：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v7.widget.RecyclerView
</pre>
    <p>
        让这个类继承自
        <em>
            RecyclerView.Adapter
        </em>
        ，就像下面这样：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RecyclerAdapter</span> : <span class="hljs-type">RecyclerView.Adapter</span>&lt;<span class="hljs-type">RecyclerAdapter.PhotoHolder</span>&gt;</span>()  {
}
</pre>
    <p>
        Android Studio会检测到你继承了一个含义必需方法的类，然后在你类声明的下方画出一条波浪线。
    </p>
    <p>
        点击波浪线上的代码，然后按
        <em>
            Option + Return
        </em>
        键（在PC上是
        <em>
            Alt + Enter
        </em>
        键）弹出一个上下文的菜单。选择
        <em>
            Implement Methods
        </em>
        ：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/5-Implements-RecyclerView-Adapter-Methods-650x382.png"
        alt="5" width="650" height="382" class="aligncenter size-large wp-image-170792"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/5-Implements-RecyclerView-Adapter-Methods-650x382.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/5-Implements-RecyclerView-Adapter-Methods-480x282.png 480w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        点击
        <em>
            OK
        </em>
        ，以确认你想要实现的方法：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/6-Confirm-RecyclerView-Implemention-Methods-650x381.png"
        alt="" width="650" height="381" class="aligncenter size-large wp-image-170793"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/6-Confirm-RecyclerView-Implemention-Methods-650x381.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/6-Confirm-RecyclerView-Implemention-Methods-480x282.png 480w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        这些方法是RecyclerView adapter背后的驱动力。注意，这里此刻仍然有一个编译错误 - 这是因为adapter和要求的方法实际使用的是你定义的ViewHolder类
        <code>
            PhotoHolder
        </code>
        ，但它现在还并不存在。赶快定义你的ViewHolder，查看每个必须的方法所负责的部分吧，司令！
    </p>
    <p>
        和每个adapter一样，你需要为相应的view提供填充item的方法，并确定item的个数。
    </p>
    <p>
        Item的点击事件之前是由ListView或GridView的
        <code>
            onItemClickListener
        </code>
        所管理的。但RecyclerView自己并未提供这样的方法，因为它把自身聚焦于正确地确定位置，及进行有效的管理。
    </p>
    <p>
        监听行为现在成了RecyclerView item及它的子元素的工作。这看起来似乎需要更多的精力，但作为回馈，你获得了对item子元素更好的控制。
    </p>
    <p>
        在RecyclerAdapter类的顶部，添加一个变量
        <code>
            photos
        </code>
        ，以在主构造器中持有你的照片：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RecyclerAdapter</span></span>(<span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> photos: ArrayList&lt;Photo&gt;) RecyclerView.Adapter&lt;RecyclerAdapter.PhotoHolder&gt;() {
</pre>
    <p>
        Nice job, 司令！你的adapter现在就知道去什么地方查找数据了。很快你就会有一个照片的ArrayList来填充超赞的天文摄影展！
    </p>
    <p>
        下面就来填充那些Android Studio自动生成的方法吧。
    </p>
    <p>
        第一个方法
        <code>
            getItemCount()
        </code>
        ，非常简单。你应当熟悉在ListView和GridView中的做法。
    </p>
    <p>
        adapter会计算出要展示多少个item。在本例中，你希望adapter展示出你从NASA的API中下载的每张照片。将
        <code>
            getItemCount()
        </code>
        方法更新为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getItemCount</span><span class="hljs-params">()</span></span> = photos.size
</pre>
    <p>
        接下来，你会利用
        <code>
            ViewHolder
        </code>
        模式来创建一个对象，以持有item中所有view的引用。
    </p>
    <h2>
        万能魔术贴：持有你的View
    </h2>
    <p>
        你将在adapter中创建一个内部类
        <strong>
            PhotoHolder
        </strong>
        来持有view的引用。把它创建到这里，而不是另外的单独的类，是因为它的行为是与adapter紧密集合的。首先，为RecyclerView的item导入synthetic器，这样就可以引用view的属性了：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> kotlinx.android.synthetic.main.recyclerview_item_row.view.*
</pre>
    <p>
        添加下列的代码到RecyclerAdapter类的底部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">//1</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">PhotoHolder</span></span>(v: View) : RecyclerView.ViewHolder(v), View.OnClickListener {
  <span class="hljs-comment">//2</span>
  <span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> view: View = v
  <span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> photo: Photo? = <span class="hljs-literal">null</span>

  <span class="hljs-comment">//3</span>
  init {
    v.setOnClickListener(<span class="hljs-keyword">this</span>)
  }

  <span class="hljs-comment">//4</span>
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onClick</span><span class="hljs-params">(v: <span class="hljs-type">View</span>)</span></span> {
    Log.d(<span class="hljs-string">"RecyclerView"</span>, <span class="hljs-string">"CLICK!"</span>)
  }

  <span class="hljs-keyword">companion</span> <span class="hljs-keyword">object</span> {
    <span class="hljs-comment">//5</span>
    <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> PHOTO_KEY = <span class="hljs-string">"PHOTO"</span>
  }
}
</pre>
    <p>
        这里都做了什么？
    </p>
    <ol>
        <li>
            让这个类继承自RecyclerView.ViewHolder，使它可以作为adapter的ViewHolder。
        </li>
        <li>
            为对象的声明周期添加一个引用，使ViewHolder持有你的View，这样它就可以通过扩展的property来访问ImageView和TextView了。Kotlin的Android扩展插件增加了隐藏的缓存功能和字段，以避免频繁地对view进行查询。
        </li>
        <li>
            初始化
            <code>
                View.OnClickListener
            </code>
            。
        </li>
        <li>
            实现
            <code>
                View.OnClickListener
            </code>
            中必须的方法，让ViewHolder负责它自己的时间处理。
        </li>
        <li>
            添加了一个key，便于引用用于启动你的RecyclerView的特定item。
        </li>
    </ol>
    <p>
        在
        <code>
            onBindViewHolder
        </code>
        和
        <code>
            onCreateViewHolder
        </code>
        方法中仍然存在着编译错误。将
        <code>
            onBindViewHolder
        </code>
        中的参数
        <code>
            holder: ?
        </code>
        修改为
        <code>
            RecyclerAdapter.PhotoHolder
        </code>
        。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onBindViewHolder</span><span class="hljs-params">(holder: <span class="hljs-type">RecyclerAdapter</span>.<span class="hljs-type">PhotoHolder</span>, position: <span class="hljs-type">Int</span>)</span></span> {
    TODO(<span class="hljs-string">"not implemented"</span>) <span class="hljs-comment">//To change body of created functions use File | Settings | File Templates.</span>
}
</pre>
    <p>
        然后将
        <code>
            onCreateViewHolder
        </code>
        方法的返回类型修改为
        <code>
            RecyclerAdapter.PhotoHolder
        </code>
        ，并移除参数
        <code>
            parent
        </code>
        的安全调用操作符（也就是
        <code>
            ?
        </code>
        ）。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateViewHolder</span><span class="hljs-params">(parent: <span class="hljs-type">ViewGroup</span>, viewType: <span class="hljs-type">Int</span>)</span></span>: RecyclerAdapter.PhotoHolder {
    TODO(<span class="hljs-string">"not implemented"</span>) <span class="hljs-comment">//To change body of created functions use File | Settings | File Templates.</span>
 }
</pre>
    <p>
        You should now be able to build and run the app again, 
        but it’ll look about the same 
        because you haven’t told the RecyclerView how to associate the PhotoHolder with a view.
    </p>
    <h2>
        Assembling The Pieces
    </h2>
    <p>
        Sometimes there are no ViewHolders available. In this scenario, RecylerView
        will ask
        <code>
            onCreateViewHolder()
        </code>
        from RecyclerAdapter to make a new one. You’ll use the item layout — PhotoHolder
        — to create a view for the ViewHolder.
    </p>
    <p>
        The inflate code could simply be added to
        <code>
            onCreateViewHolder()
        </code>
        . However, this is a nice opportunity to show a really cool Kotlin feature
        called
        <a href="https://kotlinlang.org/docs/reference/extensions.html" target="_blank">
            Extensions
        </a>
        .
    </p>
    <p>
        First, add a new Kotlin file named
        <em>
            Extensions.kt
        </em>
        to the project and then add the following new extension function to the
        new file:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            ViewGroup.
            <span class="hljs-title">
                inflate
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-meta">
                    @LayoutRes
                </span>
                layoutRes:
                <span class="hljs-type">
                    Int
                </span>
                , attachToRoot:
                <span class="hljs-type">
                    Boolean
                </span>
                =
                <span class="hljs-literal">
                    false
                </span>
                )
            </span>
        </span>
        : View {
        <span class="hljs-keyword">
            return
        </span>
        LayoutInflater.from(context).inflate(layoutRes,
        <span class="hljs-keyword">
            this
        </span>
        , attachToRoot) }
    </pre>
    <p>
        Replace the
        <code>
            TODO("not implemented")
        </code>
        line between the curly braces in
        <code>
            onCreateViewHolder()
        </code>
        with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        inflatedView = parent.inflate(R.layout.recyclerview_item_row,
        <span class="hljs-literal">
            false
        </span>
        )
        <span class="hljs-keyword">
            return
        </span>
        PhotoHolder(inflatedView)
    </pre>
    <p>
        Here you inflate the view from its layout and pass it in to a PhotoHolder.
        The
        <code>
            parent.inflate(R.layout.recyclerview_item_row, false)
        </code>
        method will execute the new
        <code>
            ViewGroup.inflate(...)
        </code>
        extension function to inflate the layout.
    </p>
    <p>
        And with that, you’ve made it so the object holds onto those references
        while it’s recycled, but there are still more pieces to put together before
        you can launch your rocketship.
    </p>
    <p>
        Start a new activity by replacing the log in ViewHolder’s
        <code>
            onClick
        </code>
        with this code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        context = itemView.context
        <span class="hljs-keyword">
            val
        </span>
        showPhotoIntent = Intent(context, PhotoActivity::
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
        showPhotoIntent.putExtra(PHOTO_KEY, photo) context.startActivity(showPhotoIntent)
    </pre>
    <p>
        This grabs the current context of your item view and creates an intent
        to show a new activity on the screen, passing the photo object you want
        to show. Passing the context object into the intent allows the app to know
        what activity it is leaving.
    </p>
    <p>
        Next thing to do is to add this method inside
        <code>
            PhotoHolder
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                bindPhoto
            </span>
            <span class="hljs-params">
                (photo:
                <span class="hljs-type">
                    Photo
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            this
        </span>
        .photo = photo Picasso.with(view.context).load(photo.url).into(view.itemImage)
        view.itemDate.text = photo.humanDate view.itemDescription.text = photo.explanation
        }
    </pre>
    <p>
        This binds the photo to the PhotoHolder, giving your item the data it
        needs to work out what it should show.
    </p>
    <p>
        It also adds the suggested
        <a href="http://square.github.io/picasso/" target="_blank" title="Picasso">
            Picasso
        </a>
        import, which is a library that makes it significantly simpler to get
        images from a given URL.
    </p>
    <p>
        The last piece of the PhotoHolder assembly will tell it how to show the
        right photo at the right moment. It’s the RecyclerAdapter’s
        <code>
            onBindViewHolder
        </code>
        , and it lets you know a new item will be available on screen and the
        holder needs some data.
    </p>
    <p>
        Add the following code inside the
        <code>
            onBindViewHolder()
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        itemPhoto = photos[position] holder.bindPhoto(itemPhoto)
    </pre>
    <p>
        Here you’re passing in a copy of your ViewHolder and the position where
        the item will show in your RecyclerView, and calling
        <code>
            bindPhoto(...)
        </code>
        .
    </p>
    <p>
        And that’s all you needed to do here on the assembly — just use the position
        where your ViewHolder will appear to grab the photo out of your list, and
        then pass it to your ViewHolder.
    </p>
    <p>
        Step three of your ignition check protocol is complete!
    </p>
    <h2>
        Countdown And Liftoff: Hooking up the Adapter And RecyclerView
    </h2>
    <p>
        This is the moment you’ve been waiting for, the final stage before blast
        off! All you need to do is hook your adapter up to your RecyclerView and
        make sure it retrieves photos when it’s created so you can explore space
        — in pictures.
    </p>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        , and add this property at the top:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            lateinit
        </span>
        <span class="hljs-keyword">
            var
        </span>
        adapter: RecyclerAdapter
    </pre>
    <p>
        Next, underneath the assignment of
        <code>
            recyclerView.layoutManager
        </code>
        , add the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        adapter = RecyclerAdapter(photosList) recyclerView.adapter = adapter
    </pre>
    <p>
        Here you’re creating the adapter, passing in the constructors it needs
        and setting it as the adapter for your RecyclerView.
    </p>
    <p>
        Although the adapter is connected, there’s one more thing to do to make
        sure you don’t have an empty screen.
    </p>
    <p>
        In
        <code>
            onStart()
        </code>
        , underneath the call to
        <code>
            super
        </code>
        , add this code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            if
        </span>
        (photosList.size ==
        <span class="hljs-number">
            0
        </span>
        ) { requestPhoto() }
    </pre>
    <p>
        This adds a check to see if your list is empty, and if yes, it requests
        a photo.
    </p>
    <p>
        Next, in
        <code>
            receivedNewPhoto()
        </code>
        , update the method so it looks like the following:
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
                receivedNewPhoto
            </span>
            <span class="hljs-params">
                (newPhoto:
                <span class="hljs-type">
                    Photo
                </span>
                )
            </span>
        </span>
        { runOnUiThread { photosList.add(newPhoto) adapter.notifyItemInserted(photosList.size)
        } }
    </pre>
    <p>
        Here you are informing the recycler adapter that an item was added after
        the list of photos was updated.
    </p>
    <p>
        Now you’re ready to commence the ignition sequence, er…I mean run the
        app.
    </p>
    <p>
        <em>
            Run the app
        </em>
        , load up the emulator and before long, Galacticon should look something
        like this:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-281x500.png"
        alt="7. RecyclerView Working" width="281" height="500" class="aligncenter size-large wp-image-171028"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        That’s not all. Tap on the photo, and you should be greeted with a new
        activity that brings that item into focus:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-281x500.png"
        alt="8. Focus Activity" width="281" height="500" class="aligncenter size-large wp-image-171029"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        But that’s still not all! Try
        <em>
            rotating your device or emulator
        </em>
        (function + control + F11/F12) and you’ll see the image in full screen
        glory!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-650x366.png"
        alt="9. Landscape focus" width="650" height="366" class="aligncenter size-large wp-image-171030"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-650x366.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-480x270.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-266x151.png 266w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        Depending on the size of the image and your device screen it may look
        a little distorted, but don’t worry about that.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-320x320.png"
        alt="" width="320" height="320" class="aligncenter size-medium wp-image-173047"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-128x128.png 128w"
        sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <p>
        Congratulations! You have a working RecyclerView and can take your journey
        amongst the stars.
    </p>
    <h2>
        Taking A Spacewalk: Adding Scrolling support
    </h2>
    <p>
        If you head back to
        <em>
            MainActivity
        </em>
        on your device and try to scroll down, you’ll notice something is amiss
        — your RecyclerView isn’t retrieving any new photos.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-281x500.png"
        alt="10. Scrolling Not Working" width="281" height="500" class="aligncenter size-large wp-image-171032"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        Your RecyclerView is doing exactly as it’s told by showing the contents
        of
        <code>
            photosList
        </code>
        . The problem is that the app will only retrieve one photo when you load
        the app. It has no idea when or how to grab more photos.
    </p>
    <p>
        So next, you’ll retrieve the number of the photos and the last visible
        photo index while scrolling. Then you’ll check to see if the last photo
        is visible and if there are no photos already on request. If these are
        both true, then your app goes and downloads more pretty photos!
    </p>
    <p>
        This patch will require a spacewalk, so break out your spacesuit and get
        ready for a zero gravity experience.
    </p>
    <p>
        In
        <em>
            MainActivity.kt
        </em>
        , add this property with custom accessor below to MainActivity:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        lastVisibleItemPosition:
        <span class="hljs-built_in">
            Int
        </span>
        <span class="hljs-keyword">
            get
        </span>
        () = linearLayoutManager.findLastVisibleItemPosition()
    </pre>
    <p>
        This uses your RecyclerView’s LinearLayoutManager to get the index of
        the last visible item on the screen.
    </p>
    <p>
        Next, you add a method that inserts an
        <code>
            onScrollListener
        </code>
        to your RecyclerView, so it can get a callback when the user scrolls:
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
                setRecyclerViewScrollListener
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        { recyclerView.addOnScrollListener(
        <span class="hljs-keyword">
            object
        </span>
        : RecyclerView.OnScrollListener() {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onScrollStateChanged
            </span>
            <span class="hljs-params">
                (recyclerView:
                <span class="hljs-type">
                    RecyclerView
                </span>
                ?, newState:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onScrollStateChanged(recyclerView, newState)
        <span class="hljs-keyword">
            val
        </span>
        totalItemCount = recyclerView!!.layoutManager.itemCount
        <span class="hljs-keyword">
            if
        </span>
        (!imageRequester.isLoadingData &amp;&amp; totalItemCount == lastVisibleItemPosition
        +
        <span class="hljs-number">
            1
        </span>
        ) { requestPhoto() } } }) }
    </pre>
    <p>
        This function gives the RecyclerView a scroll listener that is triggered
        by scrolling. During scrolling, the listener retrieves the count of the
        items in its LayoutManager and calculates the last visible photo index.
        Once done, it compares these numbers (incrementing the index by 1 because
        the index begins at 0 while the count begins at 1). If they match and there
        are no photos already on request, then you request a new photo.
    </p>
    <p>
        Finally, hook everything to the RecyclerView by calling this method from
        <code>
            onCreate
        </code>
        , just beneath where you set your RecyclerView Adapter:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setRecyclerViewScrollListener()
    </pre>
    <p>
        Hop back in the ship (build and run the app again). Scroll down and you
        should see quite an improvement!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-281x500.png"
        alt="11. Scrolling Update" width="281" height="500" class="aligncenter size-large wp-image-171033"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        Excellent work, your RecyclerView now updates to show the latest photo
        requested by your app. The great thing is that
        <code>
            receivedNewPhoto()
        </code>
        handles most of the work because you told it to notify your adapter about
        new items.
    </p>
    <p>
        That earns an intergalactic thumbs up for upcycling code!
    </p>
    <h2>
        Layout Changes
    </h2>
    <p>
        Now that your RecyclerView is up and running, it’s time to trick out your
        spaceship.
    </p>
    <p>
        Wouldn’t it be cool if your RecyclerView could change its layout? Good
        news: RecyclerView’s item positioning is separated into a layout manager.
    </p>
    <p>
        Add a property for a
        <em>
            GridLayoutManager
        </em>
        to the top of
        <em>
            MainActivity.kt
        </em>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            lateinit
        </span>
        <span class="hljs-keyword">
            var
        </span>
        gridLayoutManager: GridLayoutManager
    </pre>
    <p>
        Note that GridLayoutManager is a built-in layout manager, but it could
        just as easily be custom.
    </p>
    <p>
        In
        <code>
            onCreate()
        </code>
        , initialize the LayoutManager below the existing Linear Layout Manager:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        gridLayoutManager = GridLayoutManager(
        <span class="hljs-keyword">
            this
        </span>
        ,
        <span class="hljs-number">
            2
        </span>
        )
    </pre>
    <p>
        Just like you did with the previous LayoutManager, you pass in the context
        the manager will appear in, but unlike the former, it takes an integer
        parameter. In this case, you’re setting the number of columns the grid
        will have.
    </p>
    <p>
        Add this method to MainActivity:
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
                changeLayoutManager
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (recyclerView.layoutManager == linearLayoutManager) {
        <span class="hljs-comment">
            //1
        </span>
        recyclerView.layoutManager = gridLayoutManager
        <span class="hljs-comment">
            //2
        </span>
        <span class="hljs-keyword">
            if
        </span>
        (photosList.size ==
        <span class="hljs-number">
            1
        </span>
        ) { requestPhoto() } }
        <span class="hljs-keyword">
            else
        </span>
        {
        <span class="hljs-comment">
            //3
        </span>
        recyclerView.layoutManager = linearLayoutManager } }
    </pre>
    <p>
        This code checks to see what LayoutManager your RecyclerView is using,
        and then:
    </p>
    <ol>
        <li>
            If it’s using the LinearLayoutManager, it swaps in the GridLayoutManager
        </li>
        <li>
            It requests a new photo if your grid layout only has one photo to show
        </li>
        <li>
            If it’s using the GridLayoutManager, it swaps in the LinearLayoutManager
        </li>
    </ol>
    <p>
        Next, you need to make some changes to
        <code>
            lastVisibleItemPosition
        </code>
        to help it handle the new LayoutManager. Make it look like the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        lastVisibleItemPosition:
        <span class="hljs-built_in">
            Int
        </span>
        <span class="hljs-keyword">
            get
        </span>
        () =
        <span class="hljs-keyword">
            if
        </span>
        (recyclerView.layoutManager == linearLayoutManager) { linearLayoutManager.findLastVisibleItemPosition()
        }
        <span class="hljs-keyword">
            else
        </span>
        { gridLayoutManager.findLastVisibleItemPosition() }
    </pre>
    <p>
        Here you ask the RecyclerView to tell you what its LayoutManager is, then
        you ask that LayoutManager to tell you the position of the last visible
        item.
    </p>
    <p>
        To use the grid layout, make use of the Options menu button that is already
        available in the app. Add the following code underneath
        <code>
            onStart()
        </code>
        :
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
                onOptionsItemSelected
            </span>
            <span class="hljs-params">
                (item:
                <span class="hljs-type">
                    MenuItem
                </span>
                )
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Boolean
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (item.itemId == R.id.action_change_recycler_manager) { changeLayoutManager()
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-literal">
            true
        </span>
        }
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onOptionsItemSelected(item) }
    </pre>
    <p>
        This checks the ID of the item tapped in the menu, then works out what
        to do about it. In this case, there should only be one ID that will match
        up, effectively telling the app to go away and rearrange the RecyclerView’s
        LayoutManager.
    </p>
    <p>
        And just like that, you’re ready to go! Load up the app and tap the button
        at the top right of the screen, and you’ll begin to see the stars shift:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-281x500.png"
        alt="12. Grid Layout" width="281" height="500" class="aligncenter size-large wp-image-171037"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h2>
        Star Killer
    </h2>
    <p>
        Sometimes you’ll see things you just don’t like the look of, perhaps a
        galaxy far, far away that has fallen to the dark side or a planet that
        is prime for destruction. How could you go about killing it with a swipe?
    </p>
    <p>
        Luckily, Android engineers have provided a useful class named
        <code>
            ItemTouchHelper
        </code>
        that gives you easy swipe behavior. Creating and attaching this to a RecyclerView
        requires just a few lines of code.
    </p>
    <p>
        In
        <em>
            MainActivity.kt
        </em>
        , underneath
        <code>
            setRecyclerViewScrollListener()
        </code>
        add the following method:
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
                setRecyclerViewItemTouchListener
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            //1
        </span>
        <span class="hljs-keyword">
            val
        </span>
        itemTouchCallback =
        <span class="hljs-keyword">
            object
        </span>
        : ItemTouchHelper.SimpleCallback(
        <span class="hljs-number">
            0
        </span>
        , ItemTouchHelper.LEFT or ItemTouchHelper.RIGHT) {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onMove
            </span>
            <span class="hljs-params">
                (recyclerView:
                <span class="hljs-type">
                    RecyclerView
                </span>
                , viewHolder:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                , viewHolder1:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                )
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Boolean
        </span>
        {
        <span class="hljs-comment">
            //2
        </span>
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-literal">
            false
        </span>
        }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onSwiped
            </span>
            <span class="hljs-params">
                (viewHolder:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                , swipeDir:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-comment">
            //3
        </span>
        <span class="hljs-keyword">
            val
        </span>
        position = viewHolder.adapterPosition photosList.removeAt(position) recyclerView.adapter.notifyItemRemoved(position)
        } }
        <span class="hljs-comment">
            //4
        </span>
        <span class="hljs-keyword">
            val
        </span>
        itemTouchHelper = ItemTouchHelper(itemTouchCallback) itemTouchHelper.attachToRecyclerView(recyclerView)
        }
    </pre>
    <p>
        Let’s go through this step by step:
    </p>
    <ol>
        <li>
            You create the callback and tell it what events to listen for. It takes
            two parameters, one for drag directions and one for swipe directions, but
            you’re only interested in swipe, so you pass 0 to inform the callback not
            to respond to drag events.
        </li>
        <li>
            You return false in
            <code>
                onMove
            </code>
            because you don’t want to perform any special behavior here.
        </li>
        <li>
            <code>
                onSwiped
            </code>
            is called when you swipe an item in the direction specified in the
            <code>
                ItemTouchHelper
            </code>
            . Here, you request the
            <code>
                viewHolder
            </code>
            parameter passed for the position of the item view, then you remove that
            item from your list of photos. Finally, you inform the RecyclerView adapter
            that an item has been removed at a specific position.
        </li>
        <li>
            You initialize the
            <code>
                ItemTouchHelper
            </code>
            with the callback behavior you defined, and then attach it to the RecyclerView.
        </li>
    </ol>
    <p>
        Add the method to the activity’s
        <code>
            onCreate()
        </code>
        , underneath
        <code>
            setRecyclerViewScrollListener()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setRecyclerViewItemTouchListener()
    </pre>
    <p>
        This will attach the
        <code>
            ItemTouchListener
        </code>
        to the RecyclerView using the code you just wrote.
    </p>
    <p>
        <em>
            Run the app
        </em>
        once more and
        <em>
            swipe across
        </em>
        one of your items, you should see it begin to move. If you swipe the item
        far enough, you should see it animate and vanish. If other items are visible,
        then they will reorganize themselves to cover the hole. How cool is that?
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item-281x500.png"
        alt="13 Swipe Away Item" width="281" height="500" class="aligncenter size-large wp-image-171038"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h2>
        Where To Go From Here?
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
        Nice job! You’ve been on quite an adventure, but now it’s time to head
        back to Earth and think about what you’ve learned.
    </p>
    <ul>
        <li>
            You’ve created a RecyclerView and all the components it needs, such as
            a LayoutManager, an Adapter and a ViewHolder.
        </li>
        <li>
            You’ve updated and removed items from an Adapter.
        </li>
        <li>
            You’ve added some cool features like changing layouts and adding swipe
            functionality.
        </li>
    </ul>
    <p>
        Above all, you’ve experienced how separation of components — a key attribute
        of RecyclerViews — provides so much functionality with such ease. If you
        want your collections to be flexible and provide some excitement, then
        look no further than the all-powerful RecyclerView.
    </p>
    <p>
        The final project for this tutorial is available
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/galacticon-final.zip">
            here
        </a>
        .
    </p>
    <p>
        If you want to learn more about RecyclerViews then check out the
        <a href="http://developer.android.com/reference/android/support/v7/widget/RecyclerView.html"
        target="_blank" title="Android documentation">
            Android documentation
        </a>
        to see what it can do. Take a look at the
        <a href="http://developer.android.com/tools/support-library/features.html#v7-recyclerview"
        target="_blank" title="support library">
            support library
        </a>
        for RecyclerViews to learn how to use it on older devices. If you want
        to make them fit with the material design spec then check out the
        <a href="https://www.google.com/design/spec/components/lists.html" target="_blank"
        title="list component">
            list component
        </a>
        design specification.
    </p>
</div>