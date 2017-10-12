# Android Fragment教程：介绍
---
#### [原文地址](https://www.raywenderlich.com/149112/android-fragments-tutorial-introduction) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志
            </em>
            ：本教程已由Joe Howard更新至使用Kotlin和Android Studio 3.0的版本。原教程由Namrata Bandekar撰写。
        </p>
    </div>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/07/Activities-feature.png"
        alt="Learn how to juggle like an Android!" width="250" height="250" class="alignright size-full bordered">
    </p>
    <p>
        当你创建一个Android app的时候，很可能你会做的第一件事就是规划和设计如何去接管世界~开玩笑了。实际上，你会做的第一件事就是创建一个
        <em>
            Activity
        </em>
        。Activity是所有动作发生的地方，因为它就是用户和你的app进行交互的那块屏幕。
    </p>
    <p>
        简单地说，activity就是Android app的一个基本构建模块之一。
    </p>
    <p>
        在本教程中，你将深入了解如何使用activity。你会创建一个名为
        <em>
            Forget Me Not
        </em>
        的to-do列表app，从中学习到：
    </p>
    <ul>
        <li>
            创建，启动和停止一个activity的过程，以及如何处理两个activity之间的导航。
        </li>
        <li>
            一个activity生命周期的各个阶段，以及如何优雅地处理各个阶段。
        </li>
        <li>
            管理配置的变化，以及在你的activity中持久化数据的方式。
        </li>
    </ul>
    <p>
        此外，你将使用（官方最新的）
        <em>
            Kotlin
        </em>
        编程语言以及Android Studio 3.0。你需要使用Kotlin 1.1.3及Android Studio 3.0 Canary或更高地版本来完成。
    </p>
    <p>
        本教程假定你已熟悉了基本的Android开发。如果你是Kotlin，XML或Android Studio的纯小白，你应当在开始前先学习一下
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Beginning%20Android%20Development%20Part%20One%20Installing%20Android%20Studio.md"
        target="_blank" title="Beginning Android Development Series" sl-processed="1">
            开始Android开发系列
        </a>
        和
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Kotlin%20For%20Android%20An%20Introduction.md"
        target="_blank" title="Kotlin For Android: An Introduction" sl-processed="1">
            用Kotlin编写Android：介绍
        </a>
        。
    </p>
    <h2>
        入门
    </h2>
    <p>
        打开并提取本教程的
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/07/ForgetMeNot-starter.zip"
        title="starter project" sl-processed="1">
            初始项目
        </a>
        。打开
        <em>
            Android Studio
        </em>
        3.0或更高的版本，并选择
        <em>
            Open an existing Android Studio project
        </em>
        。然后选取刚提取的项目。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM-650x403.png"
            alt="" width="650" height="403" class="aligncenter size-large wp-image-165861"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM-650x403.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM-480x298.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM.png 1554w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        本教程剩余的主题就是
        <em>
            Forget Me Not
        </em>
        了，这是一个简单的app，让你可以从列表中添加或删除任务。它还可以展示当前的日期和时间，便于你的查看。
    </p>
    <p>
        现在
        <em>
            运行
        </em>
        项目，你会看到一个非常基本的界面：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7-280x500.png"
            alt="" width="280" height="500" class="aligncenter size-large wp-image-165885"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7-280x500.png 280w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7-179x320.png 179w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7.png 799w"
            sizes="(max-width: 280px) 100vw, 280px">
        </a>
    </p>
    <p>
        现在，你可以做的事情还不多。你的to-do列表是空的，点击“ADD A TASK”按钮也不会有任何的反映。你的任务就是通过让to-do列表变得可以修改，来使整个屏幕活跃起来。
    </p>
    <h2>
        Activity声明周期
    </h2>
    <p>
        在启动你的手指之前，先来絮叨一些理论。
    </p>
    <p>
        就像前面所提到的，activity是构建你app的屏幕的基础。它包含了多种用户可以与之交互的组件，并且通常你的app都会有多个activity来处理你创建的各个屏幕。
    </p>
    <p>
        让所有的activity做不同的事，使得开发一个Android app听起来像是一个复杂的任务。
    </p>
    <p>
        幸运的是，Android使用了特定的
        <em>
            回调方法
        </em>
        来处理这些，其中的代码只有在需要时才会被启动。这个系统就被称为
        <em>
            activity的生命周期
        </em>
        。
    </p>
    <p>
        对于创建一个健壮和可靠的app来讲，处理你activity生命周期的各个阶段是至关重要的。activity的生命周期是activity阶段步骤金字塔的最好阐释，它会被连接到下列的核心回调方法：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid.png"
            alt="Adapted from developer.android.com" width="630" height="429" class="aligncenter size-large wp-image-116817"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid.png 630w, https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid-470x320.png 470w"
            sizes="(max-width: 630px) 100vw, 630px">
        </a>
    </p>
    <p>
        跟随上述的图表，你可以实际地设置生命周期，相关的方法会自动在你的代码中调用。仔细来看一下每个回调方法：
    </p>
    <ul>
        <li>
            <em>
                onCreate()
            </em>
            ：在activity第一次被创建的时候由操作系统调用。你可以在这里初始化UI元素或数据对象。你还有activity的
            <code>
                savedInstanceState
            </code>
            ，它包含了之前保存的状态，你可以用它来重新创建状态。
        </li>
        <li>
            <em>
                onStart()
            </em>
            ：在将activity展示给用户之前会调用该方法，其后常常跟随着
            <code>
                onResume()
            </code>
            。通常，你在这里启动UI动画，基于音频的内容，或其它需要呈现到屏幕上的activity中的内容。
        </li>
        <li>
            <em>
                onResume()
            </em>
            ：会在进入前台的时候被调用。这里是一个重启动画，更新UI元素，重启镜头预览，继续音频/视频的播放的很好的地方，还可以在这里初始化你在
            <code>
                onPause()
            </code>
            方法中释放的组件。
        </li>
        <li>
            <em>
                onPause()
            </em>
            ：这个方法会在activity被切到后台之前被调用。你应当在这里停止任何关联到这个activity上视觉的或音频的内容，诸如UI动画，音乐播放或相机镜头。之后如果activity回到前台，就会调用
            <code>
                onResume()
            </code>
            方法；如果activity之后被隐藏，则调用
            <code>
                onStop()
            </code>
            方法。
        </li>
        <li>
            <em>
                onStop()
            </em>
            ：这个方法会在
            <code>
                onPause()
            </code>
            之后被调用，这时activity就不会再展示给用户。你可以在这里将数据保存到磁盘上。之后如果activity回到前台，就会调用
            <code>
                onRestart()
            </code>
            方法；如果activity从内存中被释放，则会调用
            <code>
                onDestroy()
            </code>
            方法。
        </li>
        <li>
            <em>
                onRestart()
            </em>
            ：会在activity被终止后，再次启动之前被调用。其后总是跟随着
            <code>
                onStart()
            </code>
            方法。
        </li>
        <li>
            <em>
                onDestroy()
            </em>
            ：这是你从操作系统中接收到的最后一个回调方法，它会在activity被销毁前被调用。你可以通过调用activity的
            <code>
                finish()
            </code>
            方法来触发它；或是当系统需要回收内存的时候，也会自动地触发它。如果你的activity中包含任何的后台线程，或其它长期运行的资源没有被释放，这个销毁就会导致内存泄漏，因此你需要牢记在这里停止这些操作。
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：你不可以在自己的代码中直接调用上述任一的回调方法（除了父类的调用）- 你只可以在你的activity子类中，按照需要来重载它们。它们是在当用户打开，隐藏或退出这个activity时，由系统调用的。
        </p>
    </div>
    <p>
        好多的方法需要记！在下一部分，你会看到一些生命周期方法的操作，让你可以更容易地记住它们。
    </p>
    <h2>
        配置一个Activity
    </h2>
    <p>
        记住activity的生命周期，让我们来看一下示例项目中的activity。打开
        <em>
            MainActivity.kt
        </em>
        ，你会看到这个类，和其中的
        <code>
            onCreate()
        </code>
        方法被重写成了如下的样子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> : <span class="hljs-type">AppCompatActivity</span></span>() {
  <span class="hljs-comment">// 1</span>
  <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> taskList: MutableList&lt;String&gt; = mutableListOf()
  <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> adapter <span class="hljs-keyword">by</span> lazy { makeAdapter(taskList) }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(savedInstanceState: <span class="hljs-type">Bundle</span>?)</span></span> {
    <span class="hljs-comment">// 2</span>
    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState)
    <span class="hljs-comment">// 3</span>
    setContentView(R.layout.activity_main)
    <span class="hljs-comment">// 4</span>
    taskListView.adapter = adapter
    <span class="hljs-comment">// 5</span>
    taskListView.onItemClickListener = AdapterView.OnItemClickListener { parent, view, position, id -&gt; }
  }

  <span class="hljs-comment">// 6</span>
  <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">addTaskClicked</span><span class="hljs-params">(view: <span class="hljs-type">View</span>)</span></span> {

  }

  <span class="hljs-comment">// 7</span>
  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">makeAdapter</span><span class="hljs-params">(list: <span class="hljs-type">List</span>&lt;<span class="hljs-type">String</span>&gt;)</span></span>: ArrayAdapter&lt;String&gt; =
      ArrayAdapter(<span class="hljs-keyword">this</span>, android.R.layout.simple_list_item_1, list)
}
</pre>
    <p>
        以下是对于上述代码的详细讲解：
    </p>
    <ol>
        <li>
            初始化activity的property，包括一个空的可变列表，以及一个使用
            <code>
                by lazy
            </code>
            初始化的adapter。
        </li>
        <li>
            用父类调用
            You call
            <code>
                onCreate()
            </code>
            方法 - 记住通常这就是你应当在回调方法中做的第一件事。当然也有一些高级的情况，使得你需要在调用父类方法之前调用其它的代码。
        </li>
        <li>
            用相应的布局文件设置你activity的content view。
        </li>
        <li>
            为
            <code>
                taskListView
            </code>
            设置adapter。
            <code>
                taskListView
            </code>
            会使用
            <em>
                Kotlin Android Extensions
            </em>
            来进行初始化，你可以在
            <a href="https://kotlinlang.org/docs/tutorials/android-plugin.html" sl-processed="1">
                这里
            </a>
            找到更多相关的信息。以此取代了
            <code>
                findViewById()
            </code>
            的调用，以及对其它view-binding库的需要。
        </li>
        <li>
            添加了一个空的
            <code>
                OnItemClickListener()
            </code>
            到
            <code>
                ListView
            </code>
            上，来捕捉用户在每个条目上的点击事件。listener为一个Kotlin的lambda。
        </li>
        <li>
            一个为“ADD A TASK”按钮准备的空的点击事件方法，由
            <em>
                activity_main.xml
            </em>
            布局所指定。
        </li>
        <li>
            一个私有方法，为list view来初始化adapter。这里你使用了Kotlin的=语法来表示一个单行表达的方法。
        </li>
    </ol>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：想了解更多关于
            <code>
                ListViews
            </code>
            和
            <code>
                Adapters
            </code>
            的内容，可以参考
            <a href="http://developer.android.com/guide/topics/ui/layout/listview.html"
            target="_blank" title="Android Developer docs" sl-processed="1">
                Android开发者文档
            </a>
            。
        </p>
    </div>
    <p>
        你的实现遵循了在上一节中提到的理论 - 你在activity创建的期间，完成了布局，adapter和点击事件的监听器的初始化过程。
    </p>
    <h2>
        开始一个Activity
    </h2>
    <p>
        现在，这个app只是一个相当无用的0、1构成的块，因为你还不能添加任何内容到to-do列表中。你有改变这点的能力，这就是你接下来将做的事。
    </p>
    <p>
        在打开的
        <em>
            MainActivity.kt
        </em>
        文件中，添加下列的property到类的顶部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> ADD_TASK_REQUEST = <span class="hljs-number">1</span>
</pre>
    <p>
        你将使用这个不可变的值来引用你的请求，以便在后面添加新的任务。
    </p>
    <p>
        然后添加下列的import语句到文件的顶部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.content.Intent
</pre>
    <p>
        添加下列的实现到
        <code>
            addTaskClicked()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> intent = Intent(<span class="hljs-keyword">this</span>, TaskDescriptionActivity::<span class="hljs-class"><span class="hljs-keyword">class</span>.<span class="hljs-title">java</span>)</span>
startActivityForResult(intent, ADD_TASK_REQUEST)
</pre>
    <p>
        当用户点击“ADD A TASK”按钮的时候，Android系统就会调用
        <code>
            addTaskClicked()
        </code>
        方法。然后你就创建一个
        <code>
            Intent
        </code>
        来从
        <code>
            MainActivity
        </code>
        运行
        <code>
            TaskDescriptionActivity
        </code>
        。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：这里会出现一个编译错误，因为你还没有定义
            <code>
                TaskDescriptionActivity
            </code>
            。
        </p>
    </div>
    <p>
        你可以使用
        You can start an activity with either
        <code>
            startActivity()
        </code>
        或
        <code>
            startActivityForResult()
        </code>
        方法来启动activity。两个方法是类似的，除了
        <code>
            startActivityForResult()
        </code>
        会导致
        <code>
            TaskDescriptionActivity
        </code>
        在完成的时候调用
        <code>
            onActivityResult()
        </code>
        方法。你会在之后实现这个回调，以获知是否有一个新的任务要添加到你的列表中。
    </p>
    <p>
        但首先，你需要一个方法来进入Forget Me Not中的新任务 - 你可以通过创建
        <code>
            TaskDescriptionActivity
        </code>
        来实现它。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：
            <code>
                Intents
            </code>
            用来启动一个新的activity，并向它传递数据。有关更多的信息，可以访问
            <a href="https://www.raywenderlich.com/?p=160019" target="_blank" title="Android: Intents Tutorial"
            sl-processed="1">
                Android：Intents教程
            </a>
        </p>
    </div>
    <h2>
        创建一个Activity
    </h2>
    <p>
        在Android Studio中创建一个activity变得非常容易。只需右击你想要将activity添加到的包名 - 在本例中，就是
        <em>
            com.raywenderlich.android.forgetmenot
        </em>
        这里。然后找到
        <em>
            New/Activity
        </em>
        ，并选择
        <em>
            Empty Activity
        </em>
        ，它是一个activity的基本模板：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10-650x391.png"
            alt="" width="650" height="391" class="aligncenter size-large wp-image-165897"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10-650x391.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10-480x289.png 480w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        在下一页中，输入
        <em>
            TaskDescriptionActivity
        </em>
        作为
        <em>
            Activity Name
        </em>
        ，Android Studio会基于此自动填充其它的字段。
    </p>
    <p>
        点击
        <em>
            Finish
        </em>
        。抬起手来庆祝一下吧，你已创建了你的第一个activity！
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11-595x500.png"
            alt="" width="595" height="500" class="aligncenter size-large wp-image-165898"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11-595x500.png 595w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11-381x320.png 381w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11.png 1600w"
            sizes="(max-width: 595px) 100vw, 595px">
        </a>
    </p>
    <p>
        Android Studio会自动生成创建activity所需的相应资源。也就是：
    </p>
    <ul>
        <li>
            <em>
                Class
            </em>
            ：类文件名为
            <em>
                TaskDescriptionActivity.kt
            </em>
            ，你会在这里实现activity的行为。这个类必须继承自
            <a href="http://developer.android.com/reference/android/app/Activity.html"
            title="Activity" target="_blank" sl-processed="1">
                Activity
            </a>
            类或是已存在的它的子类，例如
            <a href="https://developer.android.com/reference/android/support/v7/app/AppCompatActivity.html"
            title="AppCompatActivity" target="_blank" sl-processed="1">
                AppCompatActivity
            </a>
            。
        </li>
        <li>
            <em>
                Layout
            </em>
            ：这个布局文件位于
            <code>
                res/layout/
            </code>
            下，名为
            <em>
                activity_task_description.xml
            </em>
            。它会在activity被创建的时候，确定不同UI元素在屏幕上的位置。
        </li>
    </ul>
    <p>
        在Android Studio 3.0中，布局文件是由
        <em>
            Empty Activity
        </em>
        模板所创建的，对于根view group默认会使用
        <em>
            ConstraintLayout
        </em>
        。关于ConstraintLayout的更多消息，可以参考
        <a href="https://developer.android.com/training/constraint-layout/index.html"
        title="here" target="_blank" sl-processed="1">
            这里
        </a>
        的android开发者文档。
    </p>
    <p>
        除此之外，你还会在
        <em>
            AndroidManifest.xml
        </em>
        文件中看到一行新的代码：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">activity</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">".TaskDescriptionActivity"</span>&gt;</span><span class="hljs-tag">&lt;/<span class="hljs-name">activity</span>&gt;</span>
</pre>
    <p>
        The
        <code>
            activity
        </code>
        元素声明了这个activity。Android app有很强的规则性，因此所有的activity必须被声明到manifest文件中，以确保app只会控制在这里声明的activity。你不会希望你的app意外地使用了错误的activity，甚至更糟的情况，使用了被其它app中没有明确许可被使用的activity。
    </p>
    <p>
        有一些你可以在这个元素中包含的attribute，可以用来设置activity的属性，诸如label，icon，或是用来装扮activity UI的主题。
    </p>
    <p>
        <code>
            android:name
        </code>
        是唯一必须的attribute。它指定了activity相应于app包的类名（因为位于开始的时间段）。
    </p>
    <p>
        现在运行app。当你点击
        <em>
            ADD A TASK
        </em>
        后，就会看到一个新的activity！
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4-282x500.png"
            alt="" width="282" height="500" class="aligncenter size-large wp-image-165882"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4-282x500.png 282w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4.png 802w"
            sizes="(max-width: 282px) 100vw, 282px">
        </a>
    </p>
    <p>
        看起来不错 - 除了缺乏实质的这个事实。现在来进行一个快速的补救吧！
    </p>
    <p>
        在新生成的
        <em>
            TaskDescriptionActivity
        </em>
        类中，粘贴下列的代码到你的类文件中，覆盖除了类声明和它的括号之外的所有内容。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">companion</span> <span class="hljs-keyword">object</span> {
  <span class="hljs-keyword">val</span> EXTRA_TASK_DESCRIPTION = <span class="hljs-string">"task"</span>
}

<span class="hljs-comment">// 2</span>
<span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(savedInstanceState: <span class="hljs-type">Bundle</span>?)</span></span> {
  <span class="hljs-keyword">super</span>.onCreate(savedInstanceState)
  setContentView(R.layout.activity_task_description)
}

<span class="hljs-comment">// 3</span>
<span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">doneClicked</span><span class="hljs-params">(view: <span class="hljs-type">View</span>)</span></span> {

}
</pre>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：你可以快速地修复任何Android Studio所抱怨的缺失的import，只需将光标放置到相应的项目上并按下Option-Enter键。
        </p>
    </div>
    <p>
        这里，你完成了如下的内容：
    </p>
    <ol>
        <li>
            使用了Kotlin的
            <a href="https://kotlinlang.org/docs/reference/object-declarations.html#companion-objects"
            sl-processed="1">
                companion object
            </a>
            来定义跨类之间的通用attribute，类似于Java中的
            <em>
                static
            </em>
            成员。
        </li>
        <li>
            重写
            <code>
                onCreate()
            </code>
            这个生命周期方法来设置activity的content view。
        </li>
        <li>
            添加了一个空的点击事件处理方法，用来完成这个activity。
        </li>
    </ol>
    <p>
        切到你相应的布局文件
        <em>
            res/layout/activity_task_description.xml
        </em>
        ，并将所有的内容替换为如下的代码：
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">android.support.constraint.ConstraintLayout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">xmlns:app</span>=<span class="hljs-string">"http://schemas.android.com/apk/res-auto"</span>
  <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:padding</span>=<span class="hljs-string">"@dimen/default_padding"</span>
  <span class="hljs-attr">tools:context</span>=<span class="hljs-string">"com.raywenderlich.android.forgetmenot.TaskDescriptionActivity"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/descriptionLabel"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:padding</span>=<span class="hljs-string">"@dimen/default_padding"</span>
    <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/description"</span>
    <span class="hljs-attr">app:layout_constraintLeft_toLeftOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintRight_toRightOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintTop_toTopOf</span>=<span class="hljs-string">"parent"</span> /&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">EditText</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/descriptionText"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"100dp"</span>
    <span class="hljs-attr">android:inputType</span>=<span class="hljs-string">"textMultiLine"</span>
    <span class="hljs-attr">android:padding</span>=<span class="hljs-string">"@dimen/default_padding"</span>
    <span class="hljs-attr">app:layout_constraintLeft_toLeftOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintRight_toRightOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintTop_toBottomOf</span>=<span class="hljs-string">"@+id/descriptionLabel"</span> /&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">Button</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/doneButton"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:onClick</span>=<span class="hljs-string">"doneClicked"</span>
    <span class="hljs-attr">android:padding</span>=<span class="hljs-string">"@dimen/default_padding"</span>
    <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/done"</span>
    <span class="hljs-attr">app:layout_constraintLeft_toLeftOf</span>=<span class="hljs-string">"parent"</span>
    <span class="hljs-attr">app:layout_constraintTop_toBottomOf</span>=<span class="hljs-string">"@+id/descriptionText"</span> /&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">android.support.constraint.ConstraintLayout</span>&gt;</span></pre>
    <p>
        你在这里修改了布局，用一个
        <code>
            TextView
        </code>
        来展示任务的描述，一个
        <code>
            EditText
        </code>
        来让用户输入描述，一个Done按钮来保存新任务。
    </p>
    <p>
        再次运行app，点击
        <em>
            ADD A TASK
        </em>
        ，你会在屏幕上看到有趣的事发生。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-165883"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5.png 801w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        停止Activity
    </h2>
    <p>
        和使用所有正确的方法启动一个activity同样重要的，是恰当地结束activity。
    </p>
    <p>
        在
        <em>
            TaskDescriptionActivity.kt
        </em>
        中，添加下列的import，其中包含一个Kotlin Android的Extension：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.app.Activity
<span class="hljs-keyword">import</span> android.content.Intent
<span class="hljs-keyword">import</span> kotlinx.android.synthetic.main.activity_task_description.*
</pre>
    <p>
        添加下列的代码到
        <code>
            doneClicked()
        </code>
        中，它会在
        <em>
            Done
        </em>
        按钮被点击的时候调用：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">val</span> taskDescription = descriptionText.text.toString()

<span class="hljs-keyword">if</span> (!taskDescription.isEmpty()) {
  <span class="hljs-comment">// 2</span>
  <span class="hljs-keyword">val</span> result = Intent()
  result.putExtra(EXTRA_TASK_DESCRIPTION, taskDescription)
  setResult(Activity.RESULT_OK, result)
} <span class="hljs-keyword">else</span> {
  <span class="hljs-comment">// 3</span>
  setResult(Activity.RESULT_CANCELED)
}

<span class="hljs-comment">// 4</span>
finish()
</pre>
    <p>
        上述的代码：
    </p>
    <ol>
        <li>
            从
            <code>
                descriptionText
            </code>
            <code>
                EditText
            </code>
            中获取到任务的描述，Kotlin Android的Extension再次被用来获取对view的域的引用。
        </li>
        <li>
            如果在第一步中获取到的任务描述不为空的话，就创建一个result
            <code>
                Intent
            </code>
            ，来返回给
            <code>
                MainActivity
            </code>
            。然后将任务描述绑定到intent上，并将activity的result设置为
            <code>
                RESULT_OK
            </code>
            ，表示用户成功地进入到了一个任务中。
        </li>
        <li>
            如果用户还未输入任务描述，就将activity result设置为
            <code>
                RESULT_CANCELED
            </code>
            。
        </li>
        <li>
            关闭activity.
        </li>
    </ol>
    <p>
        在第四步调用
        <code>
            finish()
        </code>
        之后，
        <code>
            MainActivity
        </code>
        中的
        <code>
            onActivityResult()
        </code>
        方法就会被调用 - 你就可以相应地将任务添加到to-do列表中。
    <p>
        添加下列的方法到
        <em>
            MainActivity.kt
        </em>
        中，就在
        <code>
            onCreate()
        </code>
        方法之后：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onActivityResult</span><span class="hljs-params">(requestCode: <span class="hljs-type">Int</span>, resultCode: <span class="hljs-type">Int</span>, <span class="hljs-keyword">data</span>: <span class="hljs-type">Intent</span>?)</span></span> {
  <span class="hljs-comment">// 1</span>
  <span class="hljs-keyword">if</span> (requestCode == ADD_TASK_REQUEST) {
    <span class="hljs-comment">// 2</span>
    <span class="hljs-keyword">if</span> (resultCode == Activity.RESULT_OK) {
      <span class="hljs-comment">// 3</span>
      <span class="hljs-keyword">val</span> task = <span class="hljs-keyword">data</span>?.getStringExtra(TaskDescriptionActivity.EXTRA_TASK_DESCRIPTION)
      task?.let {
        taskList.add(task)
        <span class="hljs-comment">// 4</span>
        adapter.notifyDataSetChanged()
      }
    }
  }
}
</pre>
    <p>
        一步一步来看：
    </p>
    <ol>
        <li>
            检查
            <code>
                requestCode
            </code>
            以确认activity的结果确实是你在
            <code>
                TaskDescriptionActivity
            </code>
            中添加的任务请求。
        </li>
        <li>
            确保
            <code>
                resultCode
            </code>
            为
            <code>
                RESULT_OK
            </code>
            - 它是标注activity中成功操作的结果。
        </li>
        <li>
            从result intent中提取任务的描述，然后使用
            <code>
                let
            </code>
            方法进行一下null检查，最后添加到你的列表中。
        </li>
        <li>
            最后，调用adapter的
            <code>
                notifyDataSetChanged()
            </code>
            方法。相应的就会通知
            <code>
                ListView
            </code>
            你的数据模型发生了变化，以此来触发它的刷新操作。
        </li>
    </ol>
    <p>
        运行项目来查看一下。在app启动之后，点击
        <em>
            ADD A TASK
        </em>
        按钮。现在就会弹出一个新的页面来让你输入任务。添加描述并点击
        <em>
            Done
        </em>
        键，这个页面就会关闭，并在你的列表中出现一个新的任务：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1-596x500.png"
            alt="" width="596" height="500" class="aligncenter size-large wp-image-165952"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1-596x500.png 596w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1-381x320.png 381w"
            sizes="(max-width: 596px) 100vw, 596px">
        </a>
    </p>
    <h2>
        注册Broadcast Receiver
    </h2>
    <p>
        每个to-do列表都需要很好地掌握日期和时间，因此接下来要做的事情，就是添加一个时间的展示到你的app上。打开
        <em>
            MainActivity.kt
        </em>
        并添加下列的代码，就在顶部已存在的property声明的后面：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> tickReceiver <span class="hljs-keyword">by</span> lazy { makeBroadcastReceiver() }
</pre>
    <p>
        然后在
        <code>
            MainActivity
        </code>
        的顶部添加一个
        <em>
            companion object
        </em>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">companion</span> <span class="hljs-keyword">object</span> {
  <span class="hljs-keyword">private</span> const <span class="hljs-keyword">val</span> LOG_TAG = <span class="hljs-string">"MainActivityLog"</span>

  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getCurrentTimeStamp</span><span class="hljs-params">()</span></span>: String {
    <span class="hljs-keyword">val</span> simpleDateFormat = SimpleDateFormat(<span class="hljs-string">"yyyy-MM-dd HH:mm"</span>, Locale.US)
    <span class="hljs-keyword">val</span> now = Date()
    <span class="hljs-keyword">return</span> simpleDateFormat.format(now)
  }
}
</pre>
    <p>
        添加下列的代码到
        <code>
            MainActivity
        </code>
        底部，来初始化
        <code>
            MainActivity
        </code>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">makeBroadcastReceiver</span><span class="hljs-params">()</span></span>: BroadcastReceiver {
  <span class="hljs-keyword">return</span> <span class="hljs-keyword">object</span> : BroadcastReceiver() {
    <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onReceive</span><span class="hljs-params">(context: <span class="hljs-type">Context</span>, intent: <span class="hljs-type">Intent</span>?)</span></span> {
      <span class="hljs-keyword">if</span> (intent?.action == Intent.ACTION_TIME_TICK) {
        dateTimeTextView.text = getCurrentTimeStamp()
      }
    }
  }
}
</pre>
    <p>
        这里创建了一个
        <em>
            BroadcastReceiver
        </em>
        ，以从系统接收到时间发生变化broadcast的时候，将日期和时间设置到屏幕上。这里使用的
        <code>
            getCurrentTimeStamp()
        </code>
        是activity中的一个工具方法，用来格式化日期和时间。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：如果你不熟悉
            <code>
                BroadcastReceivers
            </code>
            ，请查阅
            <a href="http://developer.android.com/reference/android/content/BroadcastReceiver.html"
            title="Android Developer documentation" target="_blank" sl-processed="1">
                Android开发者文档
            </a>
            。
        </p>
    </div>
    <p>
        接下来在
        <code>
            onCreate()
        </code>
        方法的下面添加下列代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onResume</span><span class="hljs-params">()</span></span> {
  <span class="hljs-comment">// 1</span>
  <span class="hljs-keyword">super</span>.onResume()
  <span class="hljs-comment">// 2</span>
  dateTimeTextView.text = getCurrentTimeStamp()
  <span class="hljs-comment">// 3</span>
  registerReceiver(tickReceiver, IntentFilter(Intent.ACTION_TIME_TICK))
}

<span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onPause</span><span class="hljs-params">()</span></span> {
  <span class="hljs-comment">// 4</span>
  <span class="hljs-keyword">super</span>.onPause()
  <span class="hljs-comment">// 5</span>
  <span class="hljs-keyword">try</span> {
    unregisterReceiver(tickReceiver)
  } <span class="hljs-keyword">catch</span> (e: IllegalArgumentException) {
    Log.e(MainActivity.LOG_TAG, <span class="hljs-string">"Time tick Receiver not registered"</span>, e)
  }
}
</pre>
    <p>
        上述代码：
    </p>
    <ol>
        <li>
            调用父类的
            <code>
                onResume()
            </code>
            方法。
        </li>
        <li>
            用当前的时间戳更新
            <code>
                TextView
            </code>
            中的日期和时间，因为broadcast receiver现在还未注册。
        </li>
        <li>
            然后在
            <code>
                onResume()
            </code>
            中注册broadcast receiver，以接收
            <a href="http://developer.android.com/reference/android/content/Intent.html#ACTION_TIME_TICK"
            title="ACTION_TIME_TICK" target="_blank" sl-processed="1">
                ACTION_TIME_TICK
            </a>
            的broadcast。这个broadcast每分钟都会发送一次。
        </li>
        <li>
            在
            <code>
                onPause()
            </code>
            中首先调用父类的
            <code>
                onPause()
            </code>
            方法。
        </li>
        <li>
            然后注销broadcast receiver，这样activity就不会在暂停的时候接收到这个broadcast了。这样可以减小系统不必要的开销。
        </li>
    </ol>
    <p>
        运行app，现在你就可以在屏幕的顶部看到日期和时间了。即使你切到添加任务这页再返回，时间也会继续更新。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-165879"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1.png 800w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        持久化状态
    </h2>
    <p>
        每个to-do列表都擅长于记忆你需要去做的事，除了你的朋友Forget Me Not。不幸的是，这个app现在还相当得健忘，不信请看： 
    </p>
    <p>
        打开app并执行下列的步骤。
    </p>
    <ol>
        <li>
            点击
            <em>
                ADD A TASK
            </em>
            。
        </li>
        <li>
            输入“Replace regular with decaf in the breakroom”作为任务的描述，并点击
            <em>
                Done
            </em>
            。你就会在列表中看到你的新任务。
        </li>
        <li>
            从最近的app中关闭这个app。
        </li>
        <li>
            再次打开这个app。
        </li>
    </ol>
    <p>
        你会看到它已忘记了你的邪恶计划。
    </p>
    <h3>
        在多次启动间持久化数据
    </h3>
    <p>
        打开
        <em>
            MainActivity.kt
        </em>
        ，并在类的顶部添加下列的property：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> PREFS_TASKS = <span class="hljs-string">"prefs_tasks"</span>
<span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> KEY_TASKS_LIST = <span class="hljs-string">"tasks_list"</span>
</pre>
    <p>
        在你activity所有的生命周期方法下面添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onStop</span><span class="hljs-params">()</span></span> {
  <span class="hljs-keyword">super</span>.onStop()

  <span class="hljs-comment">// Save all data which you want to persist.</span>
  <span class="hljs-keyword">val</span> savedList = StringBuilder()
  <span class="hljs-keyword">for</span> (task <span class="hljs-keyword">in</span> taskList) {
    savedList.append(task)
    savedList.append(<span class="hljs-string">","</span>)
  }

  getSharedPreferences(PREFS_TASKS, Context.MODE_PRIVATE).edit()
      .putString(KEY_TASKS_LIST, savedList.toString()).apply()
}
</pre>
    <p>
        这里用列表中所有任务的描述，构建了一个由逗号分隔的字符串，然后将它保存到了
        <a href="http://developer.android.com/reference/android/content/SharedPreferences.html"
        title="Shared Preferences" target="_blank" sl-processed="1">
            SharedPreferences
        </a>
        中。正如之前所提到的，
        <code>
            onStop()
        </code>
        是一个保存数据，以实现app持久化数据功能的好地方。
    </p>
    <p>
        现在在
        <code>
            onCreate()
        </code>
        中已存在的初始化代码下面，添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> savedList = getSharedPreferences(PREFS_TASKS, Context.MODE_PRIVATE).getString(KEY_TASKS_LIST, <span class="hljs-literal">null</span>)
<span class="hljs-keyword">if</span> (savedList != <span class="hljs-literal">null</span>) {
  <span class="hljs-keyword">val</span> items = savedList.split(<span class="hljs-string">","</span>.toRegex()).dropLastWhile { it.isEmpty() }.toTypedArray()
  taskList.addAll(items)
}
</pre>
    <p>
        这里从
        <code>
            SharedPreferences
        </code>
        中读取到了保存的列表，并将其用逗号拆分，然后初始化
        <code>
            taskList
        </code>
        。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：选择使用
            <code>
                SharedPreferences
            </code>
            是因为这里只保存了原始的数据类型。对于更复杂的数据，则需要选用Android上的
            <a href="http://developer.android.com/guide/topics/data/data-storage.html"
            sl-processed="1">
                储存选项
            </a>
            。
        </p>
    </div>
    <p>
        现在，运行app。添加一个任务，关闭并再次打开app。发现不同之处了么？列表现在已经可以保持住任务的存在了！
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-165880"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2.png 799w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        配置的更改
    </h2>
    <p>
        我们需要从Forget Me Not删除条目的能力。
    </p>
    <p>
        还是在
        <em>
            MainActivity.kt
        </em>
        中，类的底部添加如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">taskSelected</span><span class="hljs-params">(position: <span class="hljs-type">Int</span>)</span></span> {
  <span class="hljs-comment">// 1</span>
  AlertDialog.Builder(<span class="hljs-keyword">this</span>)
    <span class="hljs-comment">// 2</span>
    .setTitle(R.string.alert_title)
    <span class="hljs-comment">// 3</span>
    .setMessage(taskList[position])
    .setPositiveButton(R.string.delete, { _, _ -&gt;
      taskList.removeAt(position)
      adapter.notifyDataSetChanged()
    })
    .setNegativeButton(R.string.cancel, {
      dialog, _ -&gt; dialog.cancel()
    })
    <span class="hljs-comment">// 4</span>
    .create()
    <span class="hljs-comment">// 5</span>
    .show()
}
</pre>
    <p>
        简而言之，当你从列表中选择一个任务时，需要创建并展示一个警告的对话框。以下是一步一步的解释：
    </p>
    <ol>
        <li>
            创建一个
            <code>
                AlertDialog.Builder
            </code>
            以帮助创建
            <code>
                AlertDialog
            </code>
            。
        </li>
        <li>
            设置警告对话框的标题。
        </li>
        <li>
            设置警告对话框中的信息为选中任务的描述。然后实现
            <code>
                PositiveButton
            </code>
            来从列表中移除该项，并进行刷新；以及
            <code>
                NegativeButton
            </code>
            来使对话框直接消失。
        </li>
        <li>
            创建警告对话框。
        </li>
        <li>
            展示警告对话框给用户。
        </li>
    </ol>
    <p>
        在
        <code>
            onCreate()
        </code>
        中更新
        <code>
            onCreate()
        </code>
        的
        <code>
            OnItemClickListener
        </code>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">taskListView.onItemClickListener = AdapterView.OnItemClickListener { _, _, position, _ -&gt;
  taskSelected(position)
}
</pre>
    <p>
        你的app现在还无法编译通过，因为你缺少定义一些字符串。将需要展示的文案和代码进行分离是一个很好的实践，这样你就可以很方便的来修改它们，并且也可以方便你在多个地方去使用这些文案。在需要将你的app翻译成其它语言的时候也会非常得方便。                                    
    </p>
    <p>
        为了配置这些文案，打开
        <em>
            res/values/strings.xml
        </em>
        ，并在
        <code>
            resources
        </code>
        元素中添加：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">string</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"alert_title"</span>&gt;</span>Task<span class="hljs-tag">&lt;/<span class="hljs-name">string</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">string</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"delete"</span>&gt;</span>Delete<span class="hljs-tag">&lt;/<span class="hljs-name">string</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">string</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"cancel"</span>&gt;</span>Cancel<span class="hljs-tag">&lt;/<span class="hljs-name">string</span>&gt;</span>
</pre>
    <p>
        运行app，点击一个任务，就会弹出一个警告对话框，带有选项
        <em>
            CANCEL
        </em>
        和从你的列表中
        <em>
            DELETE
        </em>
        任务：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3-280x500.png"
            alt="" width="280" height="500" class="aligncenter size-large wp-image-165881"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3-280x500.png 280w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3.png 796w"
            sizes="(max-width: 280px) 100vw, 280px">
        </a>
    </p>
    <p>
        现在尝试旋转设备。（确保你的设备已设置了auto-rotate的选项。）
    </p>
    <p>
        结果你一旋转，警告框就消失了。这会造成非常糟糕的用户体验 - 用户不会喜欢事物毫无理由地从屏幕上消失。
    </p>
    <h3>
        处理配置的更改
    </h3>
    <p>
        配置的更改，诸如旋转，键盘的出现或消失等等，会造成activity的关闭和重启。你可以在
        <a href="http://developer.android.com/guide/topics/manifest/activity-element.html#config"
        title="here" target="_blank" sl-processed="1">
            这里
        </a>
        找到所有会导致activity被重建的系统事件。
    </p>
    <p>
        有这么几种方法可以处理配置的更改。
    </p>
    <p>
        一种方法如下。在
        <em>
            AndroidManifest.xml
        </em>
        中，找到起始的标签：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">activity</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">".MainActivity"</span>&gt;</span>
</pre>
    <p>
        并将其修改为：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">activity</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">".MainActivity"</span> <span class="hljs-attr">android:configChanges</span>=<span class="hljs-string">"orientation|screenSize"</span>&gt;</span>
</pre>
    <p>
        这里声明了你的
        <code>
            MainActivity
        </code>
        会处理任何因方向或屏幕尺寸变化，而引起的配置的更改。这行简单的代码就避免了由系统造成的你的activity的重启，并将处理的工作丢给了
        <code>
            MainActivity
        </code>
        。
    </p>
    <p>
        你可以通过实现
        <code>
            onConfigurationChanged()
        </code>
        方法来处理配置的更改。在
        <em>
            MainActivity.kt
        </em>
        中，添加下列的方法到
        <code>
            onStop()
        </code>
        之后：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onConfigurationChanged</span><span class="hljs-params">(newConfig: <span class="hljs-type">Configuration</span>?)</span></span> {
  <span class="hljs-keyword">super</span>.onConfigurationChanged(newConfig)
}
</pre>
    <p>
        这里你只是调用了父类的
        <code>
            onConfigurationChanged()
        </code>
        方法，因为你不需要基于屏幕方向或尺寸的变化，来更新或重置任何元素。
    </p>
    <p>
        <code>
            onConfigurationChanged()
        </code>
        会传递一个
        <code>
            Configuration
        </code>
        对象作为参数，它包含了已更新的设备的配置。
    </p>
    <p>
        通过读取
        <code>
            newConfig
        </code>
        参数中的字段，你可以确定新的配置，并作出恰当的修改，来更新你界面中用到的资源。
    </p>
    <p>
        现在，运行app并再次旋转设备。这次警告对话框就保留下了，除非你点击CANCEL按钮让它消失。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9-650x365.png"
            alt="" width="650" height="365" class="aligncenter size-large wp-image-165887"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9-650x365.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9-480x270.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9.png 1423w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        另一种方法，则是将状态性的对象保留到重新创建的activity实例上。你可以通过实现
        <code>
            onSaveInstanceState()
        </code>
        这个回调方法来完成。
    </p>
    <p>
        当配置发生更改时，系统就会将activity的状态保存到
        <code>
            Bundle
        </code>
        中，然后你就可以在相应的
        <code>
            onRestoreInstanceState()
        </code>
        回调方法中来恢复它。然而，
        <code>
            Bundle
        </code>
        并不适用于持有诸如bitmap这样巨大的数据，它仅仅可以储存
        <a href="http://developer.android.com/reference/java/io/Serializable.html"
        title=" serializable " target="_blank" sl-processed="1">
            serializable（可序列化）
        </a>
        的数据。
    </p>
    <p>
        状态性对象这种解决方案，缺点是序列化和反序列化数据的代价非常高。它会消耗大量的内存，并拖慢activity重启的过程。
    </p>
    <p>
        在这种情况下，实际上使用
        <code>
            Fragment
        </code>
        才是处理配置变化的最好方式。你可以在我们的
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Android%20Fragments%20Tutorial%20An%20Introduction.md"
        title="Android Fragments Tutorial" target="_blank" sl-processed="1">
            Android Fragment教程
        </a>
        中，activity被重启的时候，了解更多关于fragment及如何使用它来保存信息的相关内容。
    </p>
    <h2>
        从这儿去向哪里？
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
        祝贺！你已经了解了在Android中使用activity的基本方法，并很好地理解了重要的生命周期的概念。
    </p>
    <p>
        你明白了很多重要的概念，包括：
    </p>
    <ul>
        <li>
            如何创建activity
        </li>
        <li>
            如何停止activity
        </li>
        <li>
            如何当activity停止时持久化数据
        </li>
        <li>
            如何处理配置的更改
        </li>
    </ul>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/09/congratulations.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/09/congratulations-467x320.png"
            alt="congratulations" width="467" height="320" class="aligncenter size-medium wp-image-116870">
        </a>
    </p>
    <p>
        你可以从
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/07/ForgetMeNot-final.zip"
        title="here" sl-processed="1">
            这里
        </a>
        下载完整的项目。如果你想了解更多的内容，可以访问Google的
        <a href="http://developer.android.com/reference/android/app/Activity.html#ActivityLifecycle"
        title="documentation" target="_blank" sl-processed="1">
            官方文档
        </a>
        。
    </p>
</div>