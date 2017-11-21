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
        现在就可以运行app了，但看起来并没有发生过什么变化，因为你还未告诉RecyclerView如何把PhotoHolder和一个view关联起来。
    </p>
    <h2>
        组装碎片
    </h2>
    <p>
        当没有可用的ViewHolder时，RecylerView就会调用RecyclerAdapter的
        <code>
            onCreateViewHolder()
        </code>
        方法来创建一个新的ViewHolder。你将使用item的布局 - PhotoHolder - 来创建一个相应于ViewHolder的view。
    </p>
    <p>
        inflate的代码可以直接被添加到
        <code>
            onCreateViewHolder()
        </code>
        中。但实际上，这是一个很好的机会去展示一个叫做
        <a href="https://kotlinlang.org/docs/reference/extensions.html" target="_blank">
            Extensions
        </a>
        的很酷的Kotlin特性。
    </p>
    <p>
        首先，在项目中添加一个名为
        <em>
            Extensions.kt
        </em>
        的Kotlin文件，然后添加下列的代码到其中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> ViewGroup.<span class="hljs-title">inflate</span><span class="hljs-params">(<span class="hljs-meta">@LayoutRes</span> layoutRes: <span class="hljs-type">Int</span>, attachToRoot: <span class="hljs-type">Boolean</span> = <span class="hljs-literal">false</span>)</span></span>: View {
    <span class="hljs-keyword">return</span> LayoutInflater.from(context).inflate(layoutRes, <span class="hljs-keyword">this</span>, attachToRoot)
}
</pre>
    <p>
        在
        <code>
            onCreateViewHolder()
        </code>
        中，将花括号中的
        <code>
            TODO("not implemented")
        </code>
        替换为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> inflatedView = parent.inflate(R.layout.recyclerview_item_row, <span class="hljs-literal">false</span>)
<span class="hljs-keyword">return</span> PhotoHolder(inflatedView)
</pre>
    <p>
        这里你从item的布局中inflate了一个view，并把它传递给PhotoHolder。
        <code>
            parent.inflate(R.layout.recyclerview_item_row, false)
        </code>
        方法将会执行新的
        <code>
            ViewGroup.inflate(...)
        </code>
        扩展方法来inflate布局。
    </p>
    <p>
        这样你就办到了在回收的时候持有这些元素的引用，但在发射火箭飞船之前，还有一些碎片需要被拼凑起来。
    </p>
    <p>
        通过将ViewHolder
        <code>
            onClick
        </code>
        方法中的log语句替换为如下代码，启动一个新的activity：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> context = itemView.context
<span class="hljs-keyword">val</span> showPhotoIntent = Intent(context, PhotoActivity::<span class="hljs-class"><span class="hljs-keyword">class</span>.<span class="hljs-title">java</span>)</span>
showPhotoIntent.putExtra(PHOTO_KEY, photo)
context.startActivity(showPhotoIntent)
</pre>
    <p>
        上述代码，首先会获取到item view的context，然后创建用于在屏幕上展示新activity的intent，并传递你想要展示的照片对象。传递context对象给intent，能够让app知道是从哪个activity离开的。
    </p>
    <p>
        下一件事，是把这个方法添加到
        <code>
            PhotoHolder
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">bindPhoto</span><span class="hljs-params">(photo: <span class="hljs-type">Photo</span>)</span></span> {
  <span class="hljs-keyword">this</span>.photo = photo
  Picasso.with(view.context).load(photo.url).into(view.itemImage)
  view.itemDate.text = photo.humanDate
  view.itemDescription.text = photo.explanation
}
</pre>
    <p>
        这样就将photo绑定到了PhotoHolder上，提供给你item所需的数据，以便展示出来。
    </p>
    <p>
        它还会导入
        <a href="http://square.github.io/picasso/" target="_blank" title="Picasso">
            Picasso
        </a>
        ，这是一个用来大幅简化从URL中获取图片过程的库。
    </p>
    <p>
        PhotoHolder装配的最后一块拼图，将用来告知RecyclerView如何在正确的时间展示正确的照片，也就是RecyclerAdapter的
        <code>
            onBindViewHolder
        </code>
        方法。它会告知你，一个新的item将展示在屏幕上，相应的holder需要一些数据。
    </p>
    <p>
        在
        <code>
            onBindViewHolder()
        </code>
        方法中添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> itemPhoto = photos[position]
holder.bindPhoto(itemPhoto)
</pre>
    <p>
        这里你传递了ViewHolder的副本和item将展示到的位置，并调用
        <code>
            bindPhoto(...)
        </code>
        。
    </p>
    <p>
        以上就是所有你需要为装配完成的事 - 只需使用你的ViewHolder将出现的位置，将照片从列表中取出，然后再传递给ViewHolder。
    </p>
    <p>
        点火检查协议的第三个步骤完成了！
    </p>
    <h2>
        倒计时和起飞：连接Adapter和RecyclerView
    </h2>
    <p>
        这是你一直在等待的一刻，发射前的最后一个阶段！你需要做的所有事，就是将你的adapter连接到RecyclerView上，并确保它在创建的时候就检索图片，这样你就可以在图片中探索太空了。
    </p>
    <p>
        打开
        <em>
            MainActivity.kt
        </em>
        ，并在文件的顶部添加下列的property：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> adapter: RecyclerAdapter
</pre>
    <p>
        然后，在
        <code>
            recyclerView.layoutManager
        </code>
        之下，添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">adapter = RecyclerAdapter(photosList)
recyclerView.adapter = adapter
</pre>
    <p>
        这就创建了adapter，并传递给构造器它所需的参数，然后将它设置为RecyclerView的adapter。
    </p>
    <p>
        尽管adapter已连接，还有一件事需要做，以确保不会出现空白的屏幕。
    </p>
    <p>
        在
        <code>
            onStart()
        </code>
        中，
        <code>
            super
        </code>
        的调用之下，添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">if</span> (photosList.size == <span class="hljs-number">0</span>) {
  requestPhoto()
}
</pre>
    <p>
        这就添加了一个检查，在你的列表为空的情况下，就请求一张照片。
    </p>
    <p>
        接下来，在
        <code>
            receivedNewPhoto()
        </code>
        中，将该方法更新为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">receivedNewPhoto</span><span class="hljs-params">(newPhoto: <span class="hljs-type">Photo</span>)</span></span> {
  runOnUiThread {
    photosList.add(newPhoto)
    adapter.notifyItemInserted(photosList.size)
  }
}
</pre>
    <p>
        这样，在照片的列表被更新后，就会通知recycler的adapter添加了一个item。
    </p>
    <p>
        现在就已经准备好点火了，呃...我的意思就是运行这个app。
    </p>
    <p>
        <em>
            运行app
        </em>
        ，加载模拟器，稍后，Galacticon看起来应答像是这样：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-281x500.png"
        alt="7. RecyclerView Working" width="281" height="500" class="aligncenter size-large wp-image-171028"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        这还不是全部。点击一张照片，就会弹出一个新的activity，把这个item变为关注的重点：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-281x500.png"
        alt="8. Focus Activity" width="281" height="500" class="aligncenter size-large wp-image-171029"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        但这仍然不是全部！尝试
        <em>
            旋转你的设备或模拟器
        </em>
        （function + control + F11/F12）你就会看到全屏图像的壮观景象！
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-650x366.png"
        alt="9. Landscape focus" width="650" height="366" class="aligncenter size-large wp-image-171030"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-650x366.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-480x270.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-266x151.png 266w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        因为图片的大小和屏幕的尺寸，它看起来可能会有一点失真，但不必担心。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-320x320.png"
        alt="" width="320" height="320" class="aligncenter size-medium wp-image-173047"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-128x128.png 128w"
        sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <p>
        恭喜！你已经有了一个可用的RecyclerView，可以把你的旅程延展的星空中。
    </p>
    <h2>
        来一次太空漫步吧：添加滚动支持
    </h2>
    <p>
        如果回到
        <em>
            MainActivity
        </em>
        并尝试向下滚动，你会发现出了一个问题 - RecyclerView并不会检索任何新的照片。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-281x500.png"
        alt="10. Scrolling Not Working" width="281" height="500" class="aligncenter size-large wp-image-171032"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        这个RecyclerView是完全按照
        <code>
            photosList
        </code>
        的内容来进行检索和展示的。问题是，当你加载app的时候，它只会检索一张照片。它并不知道何时及如何获取更多的照片。
    </p>
    <p>
        因此，下面，你将检索照片的数量，以及在滚动时最后一张可见照片的索引。然后，检查最后一张照片是否可见，且如果没有照片的话，是否已发送了请求。如果是的话，就让app去下载更漂亮的照片！
    </p>
    <p>
        这个补丁需要进行太空漫步，因此打破你的太空服，准备一个零重力的实验。
    </p>
    <p>
        在
        <em>
            MainActivity.kt
        </em>
        中，添加下列的property及自定义的访问器：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> lastVisibleItemPosition: <span class="hljs-built_in">Int</span>
  <span class="hljs-keyword">get</span>() = linearLayoutManager.findLastVisibleItemPosition()
</pre>
    <p>
        这就通过RecyclerView的LinearLayoutManager获取了屏幕上最后一个可见item的索引。
    </p>
    <p>
        然后，添加一个用来插入
        <code>
            onScrollListener
        </code>
        到RecyclerView上的方法，以获取用户滚动时的回调：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setRecyclerViewScrollListener</span><span class="hljs-params">()</span></span> {
  recyclerView.addOnScrollListener(<span class="hljs-keyword">object</span> : RecyclerView.OnScrollListener() {
    <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onScrollStateChanged</span><span class="hljs-params">(recyclerView: <span class="hljs-type">RecyclerView</span>?, newState: <span class="hljs-type">Int</span>)</span></span> {
      <span class="hljs-keyword">super</span>.onScrollStateChanged(recyclerView, newState)
      <span class="hljs-keyword">val</span> totalItemCount = recyclerView!!.layoutManager.itemCount
      <span class="hljs-keyword">if</span> (!imageRequester.isLoadingData &amp;&amp; totalItemCount == lastVisibleItemPosition + <span class="hljs-number">1</span>) {
        requestPhoto()
      }
    }
  })
}
</pre>
    <p>
        这个方法给RecyclerView添加了一个滚动的listener，它会在RecyclerView被滚动时被触发。在滚动时，listener会在LayoutManager上检索item的数量，并计算最后一张可见照片的索引。然后，比较得到的两个数字（为索引加1是因为索引是从0开始计数，而数量是从1开始）。如果匹配的话，且没有照片正在请求，就请求一张新的照片。
    </p>
    <p>
        最后，通过在 
        <code>
            onCreate
        </code>
        中调用这个方法，把它附加到RecyclerView上。就在设置RecyclerView的Adapter那行代码之下：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">setRecyclerViewScrollListener()
</pre>
    <p>
        回到飞船上（再次构建并运行app）。向下滚动，你会看到改进后的效果！
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-281x500.png"
        alt="11. Scrolling Update" width="281" height="500" class="aligncenter size-large wp-image-171033"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        出色的工作，RecyclerView现已更新，以展示app请求到的最新照片。最棒的是，
        <code>
            receivedNewPhoto()
        </code>
        处理了大部分的工作，因为你让它通知adapter关于新item的事情。
    </p>
    <p>
        这个升级的代码，赢得了星际级大拇指的赞！
    </p>
    <h2>
        布局变化
    </h2>
    <p>
        既然RecyclerView已经可以运行起来了，现在是时候来装饰一下你的太空飞船了。
    </p>
    <p>
        如果RecyclerView可以改变它的布局，是不是会很酷？好消息是，RecyclerView item的定位工作已被分离到layoutManager中。
    </p>
    <p>
        添加一个
        <em>
            GridLayoutManager
        </em>
        的property到
        <em>
            MainActivity.kt
        </em>
        的顶部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> gridLayoutManager: GridLayoutManager
</pre>
    <p>
        注意GridLayoutManager是一个內建的layoutManager，但它很容易被定制。
    </p>
    <p>
        在
        <code>
            onCreate()
        </code>
        中，已存在的Linear Layout Manager下初始化LayoutManager：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">gridLayoutManager = GridLayoutManager(<span class="hljs-keyword">this</span>, <span class="hljs-number">2</span>)
</pre>
    <p>
        就像在之前的LayoutManager中所做的一样，你需要传递这个manager将出现在的上下文，但有所不同的是，它需要一个整型的参数。在本例中，它会指定网格所需的列数。
    </p>
    <p>
        添加下列的方法到MainActivity中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">changeLayoutManager</span><span class="hljs-params">()</span></span> {
  <span class="hljs-keyword">if</span> (recyclerView.layoutManager == linearLayoutManager) {
    <span class="hljs-comment">//1</span>
    recyclerView.layoutManager = gridLayoutManager
    <span class="hljs-comment">//2</span>
    <span class="hljs-keyword">if</span> (photosList.size == <span class="hljs-number">1</span>) {
      requestPhoto()
    }
  } <span class="hljs-keyword">else</span> {
    <span class="hljs-comment">//3</span>
    recyclerView.layoutManager = linearLayoutManager
  }
}
</pre>
    <p>
        上述代码会判断RecyclerView当前使用的是什么LayoutManager，然后：
    </p>
    <ol>
        <li>
            如果使用的是LinearLayoutManager，就更换为GridLayoutManager
        </li>
        <li>
            如果只有一张照片能展示，就再请求一张新的照片
        </li>
        <li>
            如果使用的是GridLayoutManager，就更换为LinearLayoutManager
        </li>
    </ol>
    <p>
        然后需要对
        <code>
            lastVisibleItemPosition
        </code>
        做出一些修改，以便处理新的LayoutManager。将其修改为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> lastVisibleItemPosition: <span class="hljs-built_in">Int</span>
  <span class="hljs-keyword">get</span>() = <span class="hljs-keyword">if</span> (recyclerView.layoutManager == linearLayoutManager) {
      linearLayoutManager.findLastVisibleItemPosition()
    } <span class="hljs-keyword">else</span> {
      gridLayoutManager.findLastVisibleItemPosition()
    }
</pre>
    <p>
        首先询问RecyclerView当前的LayoutManager是什么，然后再询问这个LayoutManager，最后一个可见item的位置。
    </p>
    <p>
        我们将使用这个app中已存在的选项菜单按钮以切换网格布局。在
        <code>
            onStart()
        </code>
        下添加如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onOptionsItemSelected</span><span class="hljs-params">(item: <span class="hljs-type">MenuItem</span>)</span></span>: <span class="hljs-built_in">Boolean</span> {
  <span class="hljs-keyword">if</span> (item.itemId == R.id.action_change_recycler_manager) {
    changeLayoutManager()
    <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>
  }
  <span class="hljs-keyword">return</span> <span class="hljs-keyword">super</span>.onOptionsItemSelected(item)
}
</pre>
    <p>
        首先会检查在菜单中被点击的item的ID，然后再执行相应的动作。在本例中，就会告诉app重新安排RecyclerView的LayoutManager。
    </p>
    <p>
        这样就全都准备好了！加载app，并点击屏幕右上角的按钮，你就会看到星星的转移：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-281x500.png"
        alt="12. Grid Layout" width="281" height="500" class="aligncenter size-large wp-image-171037"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h2>
        星星杀手
    </h2>
    <p>
        有时你会看到一些你不喜欢的东西，或是一个遥远的星系，它已掉落到了黑暗的边缘，或是一个已毁灭的星球。如何使用一个swipe的手势来将它杀死？
    </p>
    <p>
        幸运的是，Android的工程师提供了一个有用的名叫
        <code>
            ItemTouchHelper
        </code>
        的类，它可以帮你添加swipe的特性。创建它，并将它附加到RecyclerView上需要若干行的代码。
    </p>
    <p>
        在
        <em>
            MainActivity.kt
        </em>
        中，
        <code>
            setRecyclerViewScrollListener()
        </code>
        的下面添加下列的方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setRecyclerViewItemTouchListener</span><span class="hljs-params">()</span></span> {

  <span class="hljs-comment">//1</span>
  <span class="hljs-keyword">val</span> itemTouchCallback = <span class="hljs-keyword">object</span> : ItemTouchHelper.SimpleCallback(<span class="hljs-number">0</span>, ItemTouchHelper.LEFT or ItemTouchHelper.RIGHT) {
    <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onMove</span><span class="hljs-params">(recyclerView: <span class="hljs-type">RecyclerView</span>, viewHolder: <span class="hljs-type">RecyclerView</span>.<span class="hljs-type">ViewHolder</span>, viewHolder1: <span class="hljs-type">RecyclerView</span>.<span class="hljs-type">ViewHolder</span>)</span></span>: <span class="hljs-built_in">Boolean</span> {
      <span class="hljs-comment">//2</span>
      <span class="hljs-keyword">return</span> <span class="hljs-literal">false</span>
    }
    <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onSwiped</span><span class="hljs-params">(viewHolder: <span class="hljs-type">RecyclerView</span>.<span class="hljs-type">ViewHolder</span>, swipeDir: <span class="hljs-type">Int</span>)</span></span> {
      <span class="hljs-comment">//3</span>
      <span class="hljs-keyword">val</span> position = viewHolder.adapterPosition
      photosList.removeAt(position)
      recyclerView.adapter.notifyItemRemoved(position)
    }
  }

  <span class="hljs-comment">//4</span>
  <span class="hljs-keyword">val</span> itemTouchHelper = ItemTouchHelper(itemTouchCallback)
  itemTouchHelper.attachToRecyclerView(recyclerView)
}
</pre>
    <p>
        一步一步来看上述的代码：
    </p>
    <ol>
        <li>
            你创建了一个回调，并告诉它监听什么样的时间。它需要两个参数，一个是拖拽的方向，另一个则是swipe的方向。但你感兴趣的只有swipe，因此传递0来告知回调不要响应拖拽的事件。
        </li>
        <li>
            让
            <code>
                onMove
            </code>
            方法返回false，因为你不想在这里执行任何特殊的行为。
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
            parameter passed for the position of the item view, 
            then you remove that item from your list of photos. 
            Finally, you inform the RecyclerView adapter
            that an item has been removed at a specific position.
        </li>
        <li>
            You initialize the
            <code>
                ItemTouchHelper
            </code>
            with the callback behavior you defined, 
            and then attach it to the RecyclerView.
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
    <pre lang="kotlin" class="language-kotlin hljs">setRecyclerViewItemTouchListener()
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
        one of your items,
        you should see it begin to move. 
        If you swipe the item far enough, 
        you should see it animate and vanish. 
        If other items are visible,
        then they will reorganize themselves to cover the hole. 
        How cool is that?
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
        Nice job! You’ve been on quite an adventure, 
        but now it’s time to head back to Earth 
        and think about what you’ve learned.
    </p>
    <ul>
        <li>
            You’ve created a RecyclerView and all the components it needs, 
            such as a LayoutManager, 
            an Adapter and a ViewHolder.
        </li>
        <li>
            You’ve updated and removed items from an Adapter.
        </li>
        <li>
            You’ve added some cool features like changing layouts and adding swipe functionality.
        </li>
    </ul>
    <p>
        Above all, you’ve experienced how separation of components
         — a key attribute of RecyclerViews
         — provides so much functionality with such ease. 
         If you
        want your collections to be flexible and provide some excitement, 
        then look no further than the all
        -powerful RecyclerView.
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
        for RecyclerViews to learn how to use it on older devices. 
        If you want to make them fit with the material design spec then check out the
        <a href="https://www.google.com/design/spec/components/lists.html" target="_blank"
        title="list component">
            list component
        </a>
        design specification.
    </p>
</div>