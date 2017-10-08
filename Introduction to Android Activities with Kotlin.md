# Android Activity的介绍 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/165824/introduction-android-activities-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

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
                Note
            </em>
            : You can quickly fix any missing imports that Android Studio complains
            about by placing your cursor on the item and pressing Option-Enter.
        </p>
    </div>
    <p>
        Here, you’ve accomplished the following:
    </p>
    <ol>
        <li>
            Used the Kotlin
            <a href="https://kotlinlang.org/docs/reference/object-declarations.html#companion-objects"
            sl-processed="1">
                companion object
            </a>
            for the class to define attributes common across the class, similar to
            <em>
                static
            </em>
            members in Java.
        </li>
        <li>
            Overriden the
            <code>
                onCreate()
            </code>
            lifecycle method to set the content view for the activity from the layout
            file.
        </li>
        <li>
            Added an empty click handler that will be used to finish the activity.
        </li>
    </ol>
    <p>
        Jump over to your associated layout in
        <em>
            res/layout/activity_task_description.xml
        </em>
        and replace everything with the following:
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
        Here you change the layout so there is a
        <code>
            TextView
        </code>
        prompting for a task description, an
        <code>
            EditText
        </code>
        for the user to input the description, and a Done button to save the new
        task.
    </p>
    <p>
        Run the app again, tap
        <em>
            ADD A TASK
        </em>
        and your new screen will look a lot more interesting.
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
        Stopping an Activity
    </h2>
    <p>
        Just as important as starting an activity with all the right methods is
        properly stopping it.
    </p>
    <p>
        In
        <em>
            TaskDescriptionActivity.kt
        </em>
        , add these imports, including one for Kotlin Android Extensions:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.app.Activity
<span class="hljs-keyword">import</span> android.content.Intent
<span class="hljs-keyword">import</span> kotlinx.android.synthetic.main.activity_task_description.*
</pre>
    <p>
        Then add the following to
        <code>
            doneClicked()
        </code>
        , which is called when the
        <em>
            Done
        </em>
        button is tapped in this activity:
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
        You can see a few things are happening here:
    </p>
    <ol>
        <li>
            You retrieve the task description from the
            <code>
                descriptionText
            </code>
            <code>
                EditText
            </code>
            , where Kotlin Android Extensions has again been used to get references
            to view fields.
        </li>
        <li>
            You create a result
            <code>
                Intent
            </code>
            to pass back to
            <code>
                MainActivity
            </code>
            if the task description retrieved in step one is not empty. Then you bundle
            the task description with the intent and set the activity result to
            <code>
                RESULT_OK
            </code>
            , indicating that the user successfully entered a task.
        </li>
        <li>
            If the user has not entered a task description, you set the activity result
            to
            <code>
                RESULT_CANCELED
            </code>
            .
        </li>
        <li>
            Here you close the activity.
        </li>
    </ol>
    <p>
        Once you call
        <code>
            finish()
        </code>
        in step four, the callback
        <code>
            onActivityResult()
        </code>
        will be called in
        <code>
            MainActivity
        </code>
        — in turn, you need to add the task to the to-do list.
    </p>
    <p>
        Add the following method to
        <em>
            MainActivity.kt
        </em>
        , right after
        <code>
            onCreate()
        </code>
        :
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
        Let’s take this step-by-step:
    </p>
    <ol>
        <li>
            You check the
            <code>
                requestCode
            </code>
            to ensure the activity result is indeed for your add task request you
            started with
            <code>
                TaskDescriptionActivity
            </code>
            .
        </li>
        <li>
            You make sure the
            <code>
                resultCode
            </code>
            is
            <code>
                RESULT_OK
            </code>
            — the standard activity result for a successful operation.
        </li>
        <li>
            Here you extract the task description from the result intent and, after
            a null check with the
            <code>
                let
            </code>
            function, add it to your list.
        </li>
        <li>
            Finally, you call
            <code>
                notifyDataSetChanged()
            </code>
            on your list adapter. In turn, it notifies the
            <code>
                ListView
            </code>
            about changes in your data model so it can trigger a refresh of its view.
        </li>
    </ol>
    <p>
        Build and run the project to see it in action. After the app starts, tap
        <em>
            ADD A TASK
        </em>
        . This will bring up a new screen that lets you enter a task. Now add
        a description and tap
        <em>
            Done
        </em>
        . The screen will close and the new task will be on your list:
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
        Registering Broadcast Receivers
    </h2>
    <p>
        Every to-do list needs to have a good grasp on date and time, so a time
        display should be the next thing you add to your app. Open
        <em>
            MainActivity.kt
        </em>
        and add the following after the existing property declarations at the
        top:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        tickReceiver
        <span class="hljs-keyword">
            by
        </span>
        lazy { makeBroadcastReceiver() }
    </pre>
    <p>
        Then add a
        <em>
            companion object
        </em>
        near the top of
        <code>
            MainActivity
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            companion
        </span>
        <span class="hljs-keyword">
            object
        </span>
        {
        <span class="hljs-keyword">
            private
        </span>
        const
        <span class="hljs-keyword">
            val
        </span>
        LOG_TAG =
        <span class="hljs-string">
            "MainActivityLog"
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                getCurrentTimeStamp
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        : String {
        <span class="hljs-keyword">
            val
        </span>
        simpleDateFormat = SimpleDateFormat(
        <span class="hljs-string">
            "yyyy-MM-dd HH:mm"
        </span>
        , Locale.US)
        <span class="hljs-keyword">
            val
        </span>
        now = Date()
        <span class="hljs-keyword">
            return
        </span>
        simpleDateFormat.format(now) } }
    </pre>
    <p>
        And initialize the
        <code>
            tickReceiver
        </code>
        by adding the following to the bottom of
        <code>
            MainActivity
        </code>
        :
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
                makeBroadcastReceiver
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        : BroadcastReceiver {
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-keyword">
            object
        </span>
        : BroadcastReceiver() {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onReceive
            </span>
            <span class="hljs-params">
                (context:
                <span class="hljs-type">
                    Context
                </span>
                , intent:
                <span class="hljs-type">
                    Intent
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (intent?.action == Intent.ACTION_TIME_TICK) { dateTimeTextView.text =
        getCurrentTimeStamp() } } } }
    </pre>
    <p>
        Here, you create a
        <em>
            BroadcastReceiver
        </em>
        that sets the date and time on the screen if it receives a time change
        broadcast from the system. You use
        <code>
            getCurrentTimeStamp()
        </code>
        , which is a utility method in your activity, to format the current date
        and time.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : If you’re not familiar with
            <code>
                BroadcastReceivers
            </code>
            , you should refer to the
            <a href="http://developer.android.com/reference/android/content/BroadcastReceiver.html"
            title="Android Developer documentation" target="_blank" sl-processed="1">
                Android Developer documentation
            </a>
            .
        </p>
    </div>
    <p>
        Next add the following methods to
        <code>
            MainActivity
        </code>
        underneath
        <code>
            onCreate()
        </code>
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
                onResume
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onResume()
        <span class="hljs-comment">
            // 2
        </span>
        dateTimeTextView.text = getCurrentTimeStamp()
        <span class="hljs-comment">
            // 3
        </span>
        registerReceiver(tickReceiver, IntentFilter(Intent.ACTION_TIME_TICK))
        }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onPause
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 4
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onPause()
        <span class="hljs-comment">
            // 5
        </span>
        <span class="hljs-keyword">
            try
        </span>
        { unregisterReceiver(tickReceiver) }
        <span class="hljs-keyword">
            catch
        </span>
        (e: IllegalArgumentException) { Log.e(MainActivity.LOG_TAG,
        <span class="hljs-string">
            "Time tick Receiver not registered"
        </span>
        , e) } }
    </pre>
    <p>
        Here you do a few things:
    </p>
    <ol>
        <li>
            You call
            <code>
                onResume()
            </code>
            on the superclass.
        </li>
        <li>
            You update the date and time
            <code>
                TextView
            </code>
            with the current time stamp, because the broadcast receiver is not currently
            registered.
        </li>
        <li>
            You then register the broadcast receiver in
            <code>
                onResume()
            </code>
            . This ensures it will receive the broadcasts for
            <a href="http://developer.android.com/reference/android/content/Intent.html#ACTION_TIME_TICK"
            title="ACTION_TIME_TICK" target="_blank" sl-processed="1">
                ACTION_TIME_TICK
            </a>
            . These are sent every minute after the time changes.
        </li>
        <li>
            In
            <code>
                onPause()
            </code>
            , you first call
            <code>
                onPause()
            </code>
            on the superclass.
        </li>
        <li>
            You then unregister the broadcast receiver in
            <code>
                onPause()
            </code>
            , so the activity no longer receives the time change broadcasts while
            paused. This cuts down unnecessary system overhead.
        </li>
    </ol>
    <p>
        Build and run the app. Now you should now see the current date and time
        at the top of the screen. Even if you navigate to the add task screen and
        come back, the time still gets updated.
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
        Persisting State
    </h2>
    <p>
        Every to-do list is good at remembering what you need to do, except for
        your friend Forget Me Not. Unfortunately, the app is quite forgetful at
        the moment. See it for yourself.
    </p>
    <p>
        Open the app and follow these steps.
    </p>
    <ol>
        <li>
            Tap
            <em>
                ADD A TASK
            </em>
            .
        </li>
        <li>
            Enter “Replace regular with decaf in the breakroom” as the task description
            and tap
            <em>
                Done
            </em>
            . You’ll see your new task in the list.
        </li>
        <li>
            Close the app from the recent apps.
        </li>
        <li>
            Open the app again.
        </li>
    </ol>
    <p>
        You can see that it forgot about your evil plans.
    </p>
    <h3>
        Persisting Data Between Launches
    </h3>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        , and add the following properties to the top of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        PREFS_TASKS =
        <span class="hljs-string">
            "prefs_tasks"
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        KEY_TASKS_LIST =
        <span class="hljs-string">
            "tasks_list"
        </span>
    </pre>
    <p>
        And add the following underneath the rest of your activity lifecycle methods.
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
                onStop
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onStop()
        <span class="hljs-comment">
            // Save all data which you want to persist.
        </span>
        <span class="hljs-keyword">
            val
        </span>
        savedList = StringBuilder()
        <span class="hljs-keyword">
            for
        </span>
        (task
        <span class="hljs-keyword">
            in
        </span>
        taskList) { savedList.append(task) savedList.append(
        <span class="hljs-string">
            ","
        </span>
        ) } getSharedPreferences(PREFS_TASKS, Context.MODE_PRIVATE).edit() .putString(KEY_TASKS_LIST,
        savedList.toString()).apply() }
    </pre>
    <p>
        Here you build a comma separated string with all the task descriptions
        in your list, and then you save the string to
        <a href="http://developer.android.com/reference/android/content/SharedPreferences.html"
        title="Shared Preferences" target="_blank" sl-processed="1">
            SharedPreferences
        </a>
        in the
        <code>
            onStop()
        </code>
        callback. As mentioned earlier,
        <code>
            onStop()
        </code>
        is a good place to save data that you want to persist across app uses.
    </p>
    <p>
        Next add the following to
        <code>
            onCreate()
        </code>
        below the existing initialization code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        savedList = getSharedPreferences(PREFS_TASKS, Context.MODE_PRIVATE).getString(KEY_TASKS_LIST,
        <span class="hljs-literal">
            null
        </span>
        )
        <span class="hljs-keyword">
            if
        </span>
        (savedList !=
        <span class="hljs-literal">
            null
        </span>
        ) {
        <span class="hljs-keyword">
            val
        </span>
        items = savedList.split(
        <span class="hljs-string">
            ","
        </span>
        .toRegex()).dropLastWhile { it.isEmpty() }.toTypedArray() taskList.addAll(items)
        }
    </pre>
    <p>
        Here you read the saved list from the
        <code>
            SharedPreferences
        </code>
        and initialize
        <code>
            taskList
        </code>
        by converting the retrieved comma separated string to a typed array.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : You used
            <code>
                SharedPreferences
            </code>
            since you were only saving primitive data types. For more complex data
            you can use a variety of
            <a href="http://developer.android.com/guide/topics/data/data-storage.html"
            sl-processed="1">
                storage options
            </a>
            available on Android.
        </p>
    </div>
    <p>
        Now, build and run the app. Add a task, close and reopen the app. Do you
        see a difference? You are now able to retain tasks in your list!
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
        Configuration Changes
    </h2>
    <p>
        You need the ability to delete entries from Forget Me Not.
    </p>
    <p>
        Still in
        <em>
            MainActivity.kt
        </em>
        , at the bottom of the class add:
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
                taskSelected
            </span>
            <span class="hljs-params">
                (position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        AlertDialog.Builder(
        <span class="hljs-keyword">
            this
        </span>
        )
        <span class="hljs-comment">
            // 2
        </span>
        .setTitle(R.string.alert_title)
        <span class="hljs-comment">
            // 3
        </span>
        .setMessage(taskList[position]) .setPositiveButton(R.string.delete, {
        _, _ -&gt; taskList.removeAt(position) adapter.notifyDataSetChanged() })
        .setNegativeButton(R.string.cancel, { dialog, _ -&gt; dialog.cancel() })
        <span class="hljs-comment">
            // 4
        </span>
        .create()
        <span class="hljs-comment">
            // 5
        </span>
        .show() }
    </pre>
    <p>
        In a nutshell, you’re creating and showing an alert dialog when you select
        a task from the list. Here is the step-by-step explanation:
    </p>
    <ol>
        <li>
            You create an
            <code>
                AlertDialog.Builder
            </code>
            which facilitates the creation of an
            <code>
                AlertDialog
            </code>
            .
        </li>
        <li>
            You set the alert dialog title.
        </li>
        <li>
            You set the alert dialog message to be the description of the selected
            task. Then you also implement the
            <code>
                PositiveButton
            </code>
            to remove the item from the list and refresh it, and the
            <code>
                NegativeButton
            </code>
            to dismiss the dialog.
        </li>
        <li>
            You create the alert dialog.
        </li>
        <li>
            You display the alert dialog to the user.
        </li>
    </ol>
    <p>
        Update the
        <code>
            OnItemClickListener
        </code>
        of the
        <code>
            taskListView
        </code>
        in
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        taskListView.onItemClickListener = AdapterView.OnItemClickListener { _,
        _, position, _ -&gt; taskSelected(position) }
    </pre>
    <p>
        Your app won’t compile though until you define some strings. It’s good
        practice to keep text you want in your app separate from the code. The
        reason is so that you can easily change it, which is especially useful
        for text that you use in multiple places. It’s also handy for those times
        you need to translate your app into another language.
    </p>
    <p>
        To configure the strings, open
        <em>
            res/values/strings.xml
        </em>
        and within the
        <code>
            resources
        </code>
        element add:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "alert_title"
            </span>
            &gt;
        </span>
        Task
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "delete"
            </span>
            &gt;
        </span>
        Delete
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "cancel"
            </span>
            &gt;
        </span>
        Cancel
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
    </pre>
    <p>
        Build and run the app. Tap on one of the tasks. You’ll see an alert dialog
        with options to
        <em>
            CANCEL
        </em>
        or
        <em>
            DELETE
        </em>
        the task from the list:
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
        Now try rotating the device. (Make sure you have rotation in the device
        settings set to auto-rotate.)
    </p>
    <p>
        As soon as you rotate the device, the alert dialog is dismissed. This
        makes for an unreliable, undesirable user experience — users don’t like
        it when things just vanish from their screen without reason.
    </p>
    <h3>
        Handling Configuration Changes
    </h3>
    <p>
        Configuration changes, such as rotation, keyboard visibility and so on,
        cause an activity to shut down and restart. You can find the full list
        of system events that cause an activity to be recreated
        <a href="http://developer.android.com/guide/topics/manifest/activity-element.html#config"
        title="here" target="_blank" sl-processed="1">
            here
        </a>
        .
    </p>
    <p>
        There are a couple of ways you can handle a configuration change.
    </p>
    <p>
        One way is as follows. In
        <em>
            AndroidManifest.xml
        </em>
        , find the start tag:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                activity
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                ".MainActivity"
            </span>
            &gt;
        </span>
    </pre>
    <p>
        And change it to:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                activity
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                ".MainActivity"
            </span>
            <span class="hljs-attr">
                android:configChanges
            </span>
            =
            <span class="hljs-string">
                "orientation|screenSize"
            </span>
            &gt;
        </span>
    </pre>
    <p>
        Here, you declare that your
        <code>
            MainActivity
        </code>
        will handle any configuration changes that arise from a change in orientation
        or screen size. This simple line prevents a restart of your activity by
        the system, and it passes the work to
        <code>
            MainActivity
        </code>
        .
    </p>
    <p>
        You can then handle these configuration changes by implementing
        <code>
            onConfigurationChanged()
        </code>
        . In
        <em>
            MainActivity.kt
        </em>
        , add the following method after
        <code>
            onStop()
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
                onConfigurationChanged
            </span>
            <span class="hljs-params">
                (newConfig:
                <span class="hljs-type">
                    Configuration
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onConfigurationChanged(newConfig) }
    </pre>
    <p>
        Here you’re just calling the superclass’s
        <code>
            onConfigurationChanged()
        </code>
        method since you’re not updating or resetting any elements based on screen
        rotation or size.
    </p>
    <p>
        <code>
            onConfigurationChanged()
        </code>
        is passed a
        <code>
            Configuration
        </code>
        object that contains the updated device configuration.
    </p>
    <p>
        By reading fields in this
        <code>
            newConfig
        </code>
        , you can determine the new configuration and make appropriate changes
        to update the resources used in your interface.
    </p>
    <p>
        Now, build and run the app and rotate the device again. This time, the
        dialog stays in place until you dismiss it.
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
        An alternative way to handle configuration changes is to retain a stateful
        object that’s carried forward to the recreated instance of your activity.
        You can accomplish this by implementing the
        <code>
            onSaveInstanceState()
        </code>
        callback.
    </p>
    <p>
        When you do this, the system saves your activity’s state in a
        <code>
            Bundle
        </code>
        , and you can restore it when you implement the corresponding
        <code>
            onRestoreInstanceState()
        </code>
        callback. However, the
        <code>
            Bundle
        </code>
        is not designed to hold large data sets such as bitmaps, and it can only
        store data that is
        <a href="http://developer.android.com/reference/java/io/Serializable.html"
        title=" serializable " target="_blank" sl-processed="1">
            serializable
        </a>
        .
    </p>
    <p>
        The downside of the stateful object solution is that serializing and deserializing
        the data during a configuration change can come at a high cost. It can
        consume a lot of memory and slow down the activity restart process.
    </p>
    <p>
        In such instances, retaining a
        <code>
            Fragment
        </code>
        is currently the most preferable way to handle a configuration change.
        You can learn more about fragments and how to use them to retain information
        when your activity is restarted in our
        <a href="https://www.raywenderlich.com/149112/android-fragments-tutorial-introduction"
        title="Android Fragments Tutorial" target="_blank" sl-processed="1">
            Android Fragments Tutorial
        </a>
        .
    </p>
    <h2>
        Where To Go From Here?
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
        Congratulations! You have just learned the basics of using activities
        in Android and now have an excellent understanding of the ever-important
        activity lifecycle.
    </p>
    <p>
        You covered quite a few concepts, including:
    </p>
    <ul>
        <li>
            How to create an activity
        </li>
        <li>
            How to stop an activity
        </li>
        <li>
            How to persist data when an activity stops
        </li>
        <li>
            How to work around a configuration change
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
        You can download the completed project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/07/ForgetMeNot-final.zip"
        title="here" sl-processed="1">
            here
        </a>
        . If you’re still hungry for more, check out Google’s
        <a href="http://developer.android.com/reference/android/app/Activity.html#ActivityLifecycle"
        title="documentation" target="_blank" sl-processed="1">
            documentation
        </a>
        .
    </p>
</div>