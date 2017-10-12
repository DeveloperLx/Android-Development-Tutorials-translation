# Android Fragment教程：介绍 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/169885/android-fragments-tutorial-introduction-2) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <em>
            更新日志
        </em>
        ：本教程已由Lance Gleason更新至支持Kotlin及Android Studio 3.0的版本。原教材是由Huyen Tue Dao编写的。
    </div>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/10/Fragments-feature.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/Fragments-feature.png"
            alt="Fragments-feature" width="250" height="250" class="alignright size-thumbnail wp-image-154115 bordered">
        </a>
        在现代的Android app开发中，fragment是构成UI布局非常的常用工具。在本教程中你会深入Android Fragment的基础概念，并创建一个app来展示暴走漫画。
    </p>
    <div class="note" style="width:50%">
        <em>
            fragment
        </em>
        |
        <i>
            noun
        </i>
        | /’frag-mənt/
        <br>
        孤立的或未完成的部分
    </div>
    <p>
        fragment是一个Android的组件，用来管理activity中的一部分UI。正如它的名字所体现的，fragment并非是一个独立的实体，而是寄存在某个activity下。
    </p>
    <p>
        在很多方面，fragment都有着类似于activity的特性。
    </p>
    <p>
        想象一下，你是一个activity，你有很多事需要做，于是就雇佣了很多迷你的自己来运行，用洗衣和交税来换取住宿和食物。这就很像是activity和fragment之间的关系。
    </p>
    <p>
        现在，可能就像实践上你并不需要几个听从命令的部下，你也并不一定需要使用fragment。然而，如果你可以很好地使用fragment，它就可以为你提供：
    </p>
    <ul>
        <li>
            模块性：将复杂的activity代码拆分为一个个的fragment，以获得更好的组织性和可维护性。
        </li>
        <li>
            可复用性：将行为或UI部分放置到多个fragment中，而fragment可以在多个activity之间进行共享。
        </li>
        <li>
            可适应性：将UI的部分表示为不同的fragment，并根据屏幕的方向和尺寸使用不同的布局。
        </li>
    </ul>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments.png"
            alt="android_fragments_d001_why_fragments" width="600" height="600" class="aligncenter size-full wp-image-117856"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments.png 600w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments-500x500.png 500w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d001_why_fragments-128x128.png 128w"
            sizes="(max-width: 600px) 100vw, 600px">
        </a>
    </p>
    <p>
        在本教程中，你将构建一个暴走漫画的迷你百科全书。app将展示一个由暴走漫画构成的格子视图。当选中一副暴走漫画的时候，app就会展示与它相关的信息。你会从中学到：
    </p>
    <ul>
        <li>
            如何创建并添加fragment到activity上。
        </li>
        <li>
            如何让fragment发送信息到activity上。
        </li>
        <li>
            如何使用事务来添加或交换fragment。
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：本教程假定你已熟悉了Android编程的基础，并理解activity的生命周期的含义。还有几点值得去注意：
        </p>
        <ul>
            <li>
                如果你是一个Android的纯小白，你应当首先参考
                <a href="http://www.raywenderlich.com/78574/android-tutorial-for-beginners-part-1"
                target="_blank" title=" Android Tutorial for Beginners " sl-processed="1">
                    Android Tutorial for Beginners
                </a>
                和
                <a href="https://www.raywenderlich.com/116580/introduction-to-android-activities-tutorial"
                target="_blank" title=" Introduction to Activities " sl-processed="1">
                    Activity介绍
                </a>
                。
            </li>
            <li>
                本教程还会用到Android的
                <code>
                    RecyclerView
                </code>
                。如果你还从未用过
                <code>
                    RecyclerView
                </code>
                ，你可以参考
                <a href="https://www.raywenderlich.com/126528/android-recyclerview-tutorial"
                target="_blank" title="Android RecyclerView Tutorial" sl-processed="1">
                    Android RecyclerView Tutorial
                </a>
                来进行学习。
            </li>
        </ul>
    </div>
    <p>
        接下来就开始学习fragments！
    </p>
    <h2>
        Android Fragment入门
    </h2>
    <p>
        下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/AllTheRages-Starter-1.zip"
        sl-processed="1">
            起始项目
        </a>
        ，解压并启动
        <em>
            Android Studio 3.0 Beta 2
        </em>
        或更高的版本。
    </p>
    <p>
        在
        <em>
            Welcome to Android Studio
        </em>
        对话框中，选择
        <em>
            Import project (Eclipse ADT, Gradle, etc.)
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/android_fragments_003_android_studio_welcome_screen.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/android_fragments_003_android_studio_welcome_screen-517x500.png"
            alt="Android Studio Welcome Screen" width="517" height="500" class="aligncenter size-large wp-image-169911"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/android_fragments_003_android_studio_welcome_screen-517x500.png 517w, https://koenig-media.raywenderlich.com/uploads/2017/08/android_fragments_003_android_studio_welcome_screen-331x320.png 331w, https://koenig-media.raywenderlich.com/uploads/2017/08/android_fragments_003_android_studio_welcome_screen-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/08/android_fragments_003_android_studio_welcome_screen.png 951w"
            sizes="(max-width: 517px) 100vw, 517px">
        </a>
    </p>
    <p>
        选择起始项目的根目录，并点击
        <em>
            OK
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_003_android_studio_select_project-1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_003_android_studio_select_project-1.png"
            alt="Select project to import" width="432" height="477" class="aligncenter size-full wp-image-148999"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_003_android_studio_select_project-1.png 432w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_003_android_studio_select_project-1-290x320.png 290w"
            sizes="(max-width: 432px) 100vw, 432px">
        </a>
    </p>
    <p>
        如果看到了一个更新项目Gradle插件的信息，那是因为你使用了更高版本的Android Studio，选择“update”并继续。
    </p>
    <p>
        查看项目，你会找到一些资源文件：
        <em>
            strings.xml
        </em>
        ，
        <em>
            activity_main.xml
        </em>
        ，
        <em>
            drawable
        </em>
        和
        <em>
            layout
        </em>
        。还有一些供你fragment使用的模板布局文件，非fragment的代码，以及一个fragment类，你可以在之后进行加工。
    </p>
    <p>
        <code>
            MainActivity
        </code>
        会持有你所有小小的fragment，而
        <code>
            RageComicListFragment
        </code>
        则包含了用来展示暴走漫画内容列表的代码，这样你就可以将注意力集中到fragment本身了。
    </p>
    <p>
        运行项目。你会看到其中一无所有。
        <br>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_004_app_first_build.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_004_app_first_build-281x500.png"
            alt="Running the starter app" width="281" height="500" class="aligncenter size-large wp-image-148991"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_004_app_first_build-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_004_app_first_build-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_004_app_first_build.png 1440w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        很快你就会修复...
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_005_app_soon.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_005_app_soon-448x320.png"
            alt="android_fragments_005_app_soon" width="448" height="320" class="aligncenter size-medium wp-image-117844"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_005_app_soon-448x320.png 448w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_005_app_soon.png 700w"
            sizes="(max-width: 448px) 100vw, 448px">
        </a>
    </p>
    <h2>
        Android Fragment的生命周期
    </h2>
    <p>
        和activity一样，fragment中也有着生命周期的概念，当fragment的状态发生变化的时候，就会触发相应的事件。例如，当fragment变为可见，活跃，无效，或被移除的状态时，一些事件就会发生。你可以在其中添加一些代码和行为来响应这些事件。
    </p>
    <p>
        下面是
        <a href="http://developer.android.com/guide/components/fragments.html#Creating"
        target="_blank" title=" Android Developer documentation " sl-processed="1">
            Android开发者文档
        </a>
        中，fragment生命周期的图表。
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d002_fragment_lifecycle.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d002_fragment_lifecycle.png"
            alt="android_fragments_d002_fragment_lifecycle" width="317" height="847"
            class="aligncenter size-full wp-image-117857" srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d002_fragment_lifecycle.png 317w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d002_fragment_lifecycle-120x320.png 120w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d002_fragment_lifecycle-187x500.png 187w"
            sizes="(max-width: 317px) 100vw, 317px">
        </a>
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_006_fragment_lifecycle_hmm.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_006_fragment_lifecycle_hmm.png"
            alt="android_fragments_006_fragment_lifecycle_hmm" width="336" height="392"
            class="aligncenter size-full wp-image-117845" srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_006_fragment_lifecycle_hmm.png 336w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_006_fragment_lifecycle_hmm-274x320.png 274w"
            sizes="(max-width: 336px) 100vw, 336px">
        </a>
    </p>
    <p>
        当你添加一个fragment时，就会触发下列的生命周期事件：
    </p>
    <ul>
        <li>
            <code>
                onAttach
            </code>
            ：当fragment被依附到相应的activity上时被调用。
        </li>
        <li>
            <code>
                onCreate
            </code>
            ：当一个新的fragment实例被初始化时调用，通常发生在它被附加到相应activity上后被调用 - fragment有一点像是病毒。
        </li>
        <li>
            <code>
                onCreateView
            </code>
            ：当fragment创建了view层级中它自己的部分时，也就是被添加到了activity的view层级的时候被调用。
        </li>
        <li>
            <code>
                onActivityCreated
            </code>
            ：当fragment的activity完成了它的
            <code>
                onCreate
            </code>
            事件之后调用。
        </li>
        <li>
            <code>
                onStart
            </code>
            ：当fragment变为可见状态后调用。fragment只会在它的activity启动之后才会启动，且通常都是activity一启动之后，它就启动。
        </li>
        <li>
            <code>
                onResume
            </code>
            ：当fragment变为可见且可交互的状态后调用。fragment resume只会在它的activity resume之后，且通常都是activity一resume之后，它就resume。
        </li>
    </ul>
    <p>
        但稍等，fragment还未完成。下列的生命周期的事件将在你移除一个fragment的时候发生：
    </p>
    <ul>
        <li>
            <code>
                onPause
            </code>
            ：当fragment变为不可交互的状态时触发。它仅会在一个fragment将被移除或替代的时候，或其activity被pause的时候发生。
        </li>
        <li>
            <code>
                onStop
            </code>
            ：当fragment变为不可见的状态时触发。它仅会在一个fragment将被移除或替代的时候，或其activity被停止的时候发生。
        </li>
        <li>
            <code>
                onDestroyView
            </code>
            ：当fragment的view和创建在
            <code>
                onCreateView
            </code>
            中的相关资源从activity的view层级中被移除并销毁的时候触发。
        </li>
        <li>
            <code>
                onDestroy
            </code>
            ：当fragment执行最后的清理时调用
        </li>
        <li>
            <code>
                onDetach
            </code>
            ：当fragment从所在的activity中移除的时候调用
        </li>
    </ul>
    <p>
        正如你所看到的，fragment的生命周期始终伴随着activity的生命周期。但它还有一些相应于view层级，状态，附加/分离于activity的额外的事件。
    </p>
    <h2>
        v4支持库
    </h2>
    <p>
        In Android, when using fragments, there are two alternative fragment implementations
        you can use. One type is the fragment that is provided by the platform
        version. A platform version corresponds to the version of Android that
        a user is running. For example, a device running Android 6.0 (SDK Version
        23) would be running platform version 23 of the library.
    </p>
    <p>
        The second type is a support library fragment. When you include a support
        library, it is added to your project in the same manner as any third-party
        library. This has two benefits when developing applications for multiple
        versions of Android.
    </p>
    <p>
        First, it ensures that you have consistency in your code and functionality
        across different devices and platform versions. This means that bugs, and
        fixes, will be more consistent across different versions of Android using
        these libraries.
    </p>
    <p>
        Second, when new features are added to the latest version of Android,
        the Android team will often back-port these features via the support library
        in order for developers to use on older versions of Android.
    </p>
    <h3>
        Which Library Should Be Used?
    </h3>
    <p>
        If you are writing an application that will be targeting multiple versions
        of Android on multiple devices, you should use support libraries for Fragments.
        You should also use the support library for any other functionality in
        your application when available. This is considered a best practice by
        most senior Android developers and the Core Android team. The only time
        you might want to use a platform library is if you are, in fact, doing
        very specialized development for an app that is only targeting one version
        of Android.
    </p>
    <p>
        To put it another way: odds are that you will want to use support libraries
        if and when they are available. With fragments, that means you’ll want
        to use
        <em>
            the v4 support library
        </em>
        .
    </p>
    <h2>
        Creating a Fragment
    </h2>
    <p>
        Eventually, All the Rages will show a list of Rage Comics on launch, and
        tapping on any of the items will display details about that particular
        comic. To start, you’ll work backwards and first create the detail page.
    </p>
    <p>
        Open the starter project in Android Studio and find
        <em>
            fragment_rage_comic_details.xml
        </em>
        under
        <em>
            app -&gt; res -&gt; layout
        </em>
        ; this XML file lays out the comic detail display. It also displays one
        of the drawable resources and the associated string resources.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_008_fragment_details_layout_preview.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_008_fragment_details_layout_preview-626x500.png"
            alt="Fragment details preview" width="626" height="500" class="aligncenter size-large wp-image-148992"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_008_fragment_details_layout_preview-626x500.png 626w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_008_fragment_details_layout_preview-401x320.png 401w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_008_fragment_details_layout_preview.png 696w"
            sizes="(max-width: 626px) 100vw, 626px">
        </a>
    </p>
    <p>
        Select Android Studio’s
        <em>
            Project tab
        </em>
        and locate the
        <em>
            RageComicDetailsFragment
        </em>
        file. This class will be responsible for displaying details for a selected
        comic.
    </p>
    <p>
        In
        <em>
            RageComicDetailsFragment.kt
        </em>
        , the code now looks like what is shown below:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.os.Bundle
        <span class="hljs-keyword">
            import
        </span>
        android.support.v4.app.Fragment
        <span class="hljs-keyword">
            import
        </span>
        android.view.LayoutInflater
        <span class="hljs-keyword">
            import
        </span>
        android.view.View
        <span class="hljs-keyword">
            import
        </span>
        android.view.ViewGroup
        <span class="hljs-comment">
            //1
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                RageComicDetailsFragment
            </span>
            :
            <span class="hljs-type">
                Fragment
            </span>
        </span>
        () {
        <span class="hljs-comment">
            //2
        </span>
        <span class="hljs-keyword">
            companion
        </span>
        <span class="hljs-keyword">
            object
        </span>
        {
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                newInstance
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        : RageComicDetailsFragment {
        <span class="hljs-keyword">
            return
        </span>
        RageComicDetailsFragment() } }
        <span class="hljs-comment">
            //3
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onCreateView
            </span>
            <span class="hljs-params">
                (inflater:
                <span class="hljs-type">
                    LayoutInflater
                </span>
                ?, container:
                <span class="hljs-type">
                    ViewGroup
                </span>
                ?, savedInstanceState:
                <span class="hljs-type">
                    Bundle
                </span>
                ?)
            </span>
        </span>
        : View? {
        <span class="hljs-keyword">
            return
        </span>
        inflater?.inflate(R.layout.fragment_rage_comic_details, container,
        <span class="hljs-literal">
            false
        </span>
        ) } }
    </pre>
    <p>
        This is what this code does:
    </p>
    <ol>
        <li>
            Declares
            <code>
                RageComicDetailsFragment
            </code>
            as a subclass of
            <code>
                Fragment
            </code>
            .
        </li>
        <li>
            Provides a method for creating new instances of the fragment, a factory
            method.
        </li>
        <li>
            Creates the view hierarchy controlled by the fragment.
        </li>
    </ol>
    <p>
        Activities use
        <code>
            setContentView()
        </code>
        to specify the XML file that defines their layouts, but fragments create
        their view hierarchy in
        <code>
            onCreateView()
        </code>
        . Here you called
        <code>
            LayoutInflater.inflate
        </code>
        to create the hierarchy of
        <code>
            RageComicDetailsFragment
        </code>
        .
    </p>
    <p>
        The third parameter of
        <code>
            inflate
        </code>
        specifies whether the inflated fragment should be added to the
        <code>
            container
        </code>
        . The container is the parent view that will hold the fragment’s view
        hierarchy. You should always set this to
        <code>
            false
        </code>
        : the
        <code>
            FragmentManager
        </code>
        will take care of adding the fragment to the container.
    </p>
    <p>
        There’s a new kid in town here:
        <code>
            FragmentManager
        </code>
        . Each activity has a
        <code>
            FragmentManager
        </code>
        that manages its fragments. It also provides an interface for you to access,
        add and remove those fragments.
    </p>
    <p>
        You’ll notice that while
        <code>
            RageComicDetailsFragment
        </code>
        has a factory instance method,
        <code>
            newInstance()
        </code>
        , it does not have any constructors.
    </p>
    <p>
        Wait, why do you need a factory method but not a constructor?
    </p>
    <p>
        First, because you did not define any constructors, the compiler automatically
        generates an empty, default constructor that takes no arguments. This is
        all that you should have for a fragment: no other constructors.
    </p>
    <p>
        Second, you probably know that Android may destroy and later re-create
        an activity and all its associated fragments when the app goes into the
        background. When the activity comes back, its
        <code>
            FragmentManager
        </code>
        starts re-creating fragments by using the empty default constructor. If
        it cannot find one, you get an exception.
    </p>
    <p>
        For this reason, it is best practice to never specify any non-empty constructors,
        and in fact, the easiest thing to do is to specify none as you just did.
    </p>
    <p>
        What if you need to pass information or data to a Fragment? Hang on, you’ll
        get the answer to that later!
    </p>
    <h2>
        Adding a Fragment
    </h2>
    <p>
        Here’s where you get to add a fragment using the simplest approach — adding
        it to the activity’s XML layout.
    </p>
    <p>
        To do this, open
        <em>
            activity_main.xml
        </em>
        , select the Text tab and add the following inside of the root
        <em>
            FrameLayout
        </em>
        :
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                fragment
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/details_fragment"
            </span>
            <span class="hljs-attr">
                class
            </span>
            =
            <span class="hljs-string">
                "com.raywenderlich.alltherages.RageComicDetailsFragment"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        In this step, you’re placing a
        <code>
            &lt;fragment&gt;
        </code>
        tag inside of the activity layout and specifying the type of fragment
        the
        <code>
            class
        </code>
        attribute should inflate. The view ID of the
        <code>
            &lt;fragment&gt;
        </code>
        is required by the
        <code>
            FragmentManager
        </code>
        .
    </p>
    <p>
        Build and run. You will see the fragment:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_012_app_details_fragment_test.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_012_app_details_fragment_test-281x500.png"
            alt="The details fragment in its full glory" width="281" height="500" class="aligncenter size-large wp-image-148995"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_012_app_details_fragment_test-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_012_app_details_fragment_test-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_012_app_details_fragment_test.png 1440w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h3>
        Adding a Fragment Dynamically
    </h3>
    <p>
        First, open
        <em>
            activity_main.xml
        </em>
        again and remove the
        <code>
            &lt;fragment&gt;
        </code>
        you just inserted. (Embrace the Zen of deleting code!) You’ll replace
        it with the list of Rage Comics.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_purr_programming-1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_purr_programming-1-452x500.png"
            alt="" width="452" height="500" class="aligncenter size-large wp-image-170083"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_purr_programming-1-452x500.png 452w, https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_purr_programming-1-289x320.png 289w"
            sizes="(max-width: 452px) 100vw, 452px">
        </a>
    </p>
    <p>
        Open
        <em>
            RageComicListFragment.kt
        </em>
        , which has all the list code. You can see that the
        <code>
            RageComicListFragment
        </code>
        has no explicit constructors and a
        <code>
            newInstance()
        </code>
        .
    </p>
    <p>
        The list code in
        <code>
            RageComicListFragment
        </code>
        depends on some resources. You have to ensure that the fragment has a
        valid reference to a
        <code>
            Context
        </code>
        for accessing those resources. That’s where
        <code>
            onAttach()
        </code>
        comes into play.
    </p>
    <p>
        Open
        <em>
            RageComicListFragment.kt
        </em>
        , and add these imports directly below the existing imports:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.os.Bundle
        <span class="hljs-keyword">
            import
        </span>
        android.support.v7.widget.GridLayoutManager
    </pre>
    <p>
        The
        <code>
            GridLayoutManager
        </code>
        , helps in positioning items in the Rage Comic list. The other import
        is for standard fragment overrides.
    </p>
    <p>
        Inside of
        <em>
            RageComicListFragment.kt
        </em>
        , add the following two methods
        <i>
            above
        </i>
        the definition of the
        <code>
            RageComicAdapter
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
                onAttach
            </span>
            <span class="hljs-params">
                (context:
                <span class="hljs-type">
                    Context
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onAttach(context)
        <span class="hljs-comment">
            // Get rage face names and descriptions.
        </span>
        <span class="hljs-keyword">
            val
        </span>
        resources = context!!.resources names = resources.getStringArray(R.array.names)
        descriptions = resources.getStringArray(R.array.descriptions) urls = resources.getStringArray(R.array.urls)
        <span class="hljs-comment">
            // Get rage face images.
        </span>
        <span class="hljs-keyword">
            val
        </span>
        typedArray = resources.obtainTypedArray(R.array.images)
        <span class="hljs-keyword">
            val
        </span>
        imageCount = names.size imageResIds = IntArray(imageCount)
        <span class="hljs-keyword">
            for
        </span>
        (i
        <span class="hljs-keyword">
            in
        </span>
        <span class="hljs-number">
            0.
        </span>
        .imageCount -
        <span class="hljs-number">
            1
        </span>
        ) { imageResIds[i] = typedArray.getResourceId(i,
        <span class="hljs-number">
            0
        </span>
        ) } typedArray.recycle() }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onCreateView
            </span>
            <span class="hljs-params">
                (inflater:
                <span class="hljs-type">
                    LayoutInflater
                </span>
                ?, container:
                <span class="hljs-type">
                    ViewGroup
                </span>
                ?, savedInstanceState:
                <span class="hljs-type">
                    Bundle
                </span>
                ?)
            </span>
        </span>
        : View? {
        <span class="hljs-keyword">
            val
        </span>
        view: View = inflater!!.inflate(R.layout.fragment_rage_comic_list, container,
        <span class="hljs-literal">
            false
        </span>
        )
        <span class="hljs-keyword">
            val
        </span>
        activity = activity
        <span class="hljs-keyword">
            val
        </span>
        recyclerView = view.findViewById&lt;RecyclerView&gt;(R.id.recycler_view)
        <span class="hljs-keyword">
            as
        </span>
        RecyclerView recyclerView.layoutManager = GridLayoutManager(activity,
        <span class="hljs-number">
            2
        </span>
        ) recyclerView.adapter = RageComicAdapter(activity)
        <span class="hljs-keyword">
            return
        </span>
        view }
    </pre>
    <p>
        <code>
            onAttach()
        </code>
        contains code that accesses the resources you need via the
        <code>
            Context
        </code>
        to which the fragment is attached. Because the code is in
        <code>
            onAttach()
        </code>
        , you can rest assured that the fragment has a valid
        <code>
            Context
        </code>
        .
    </p>
    <p>
        In
        <code>
            onCreateView()
        </code>
        , you inflate the view hierarchy of
        <code>
            RageComicListFragment
        </code>
        , which contains a
        <code>
            RecyclerView
        </code>
        , and perform some setup.
    </p>
    <p>
        If you have to inspect a fragment’s view,
        <code>
            onCreateView()
        </code>
        is a good place to start because it is where the view is generated.
    </p>
    <p>
        Next open
        <em>
            MainActivity.kt
        </em>
        and replace
        <code>
            onCreate()
        </code>
        with the following:
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
                onCreate
            </span>
            <span class="hljs-params">
                (savedInstanceState:
                <span class="hljs-type">
                    Bundle
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState) setContentView(R.layout.activity_main)
        <span class="hljs-keyword">
            if
        </span>
        (savedInstanceState ==
        <span class="hljs-literal">
            null
        </span>
        ) { supportFragmentManager .beginTransaction() .add(R.id.root_layout,
        RageComicListFragment.newInstance(),
        <span class="hljs-string">
            "rageComicList"
        </span>
        ) .commit() } }
    </pre>
    <p>
        At this point, you get
        <code>
            RageComicListFragment
        </code>
        into
        <code>
            MainActivity
        </code>
        . You ask your new friend,
        <code>
            FragmentManager
        </code>
        , to add it.
    </p>
    <p>
        First, you grab the
        <code>
            FragmentManager
        </code>
        by referencing
        <code>
            supportFragmentManager
        </code>
        , as opposed to
        <code>
            fragmentManager
        </code>
        since you are using support fragments.
    </p>
    <p>
        Then, you ask that
        <code>
            FragmentManager
        </code>
        to start a new transaction by calling
        <code>
            beginTransaction()
        </code>
        — you probably figured that out yourself. Next, you specify the add operation
        that you want by calling
        <code>
            add
        </code>
        and passing in:
    </p>
    <ul>
        <li>
            The view ID of a container for the fragment’s view hierarchy in the activity’s
            layout. If you take a look at
            <code>
                activity_main.xml
            </code>
            , you’ll find
            <code>
                @+id/root_layout
            </code>
            .
        </li>
        <li>
            The fragment instance to be added.
        </li>
        <li>
            A string that acts as a tag/identifier for the fragment instance. This
            allows the
            <code>
                FragmentManager
            </code>
            to later retrieve the fragment for you.
        </li>
    </ul>
    <p>
        Finally, you ask the
        <code>
            FragmentManager
        </code>
        to execute the transaction by calling
        <code>
            commit()
        </code>
        .
    </p>
    <p>
        And with that, the fragment is added!
    </p>
    <p>
        Build, run and you’ll see a Rage-filled list once the app launches:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_013_app_list_build.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_013_app_list_build-281x500.png"
            alt="The list of Rage Comics. Woo!" width="281" height="500" class="aligncenter size-large wp-image-148996"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_013_app_list_build-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_013_app_list_build-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_013_app_list_build.png 1440w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        <code>
            FragmentManager
        </code>
        helped achieve this awesomeness through
        <code>
            FragmentTransactions
        </code>
        , which are basically fragment operations such as add, remove, etc.
    </p>
    <p>
        In the code above, an
        <code>
            if
        </code>
        block contains the code that displays the fragment and checks that the
        activity doesn’t have saved state. When an activity is saved, all of its
        active fragments are also saved. If you don’t perform this check, this
        could happen:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d003_fragments_too_many.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d003_fragments_too_many-296x500.png"
            alt="android_fragments_d003_fragments_too_many" width="296" height="500"
            class="aligncenter size-large wp-image-117858" srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d003_fragments_too_many-296x500.png 296w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d003_fragments_too_many-189x320.png 189w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_d003_fragments_too_many.png 440w"
            sizes="(max-width: 296px) 100vw, 296px">
        </a>
    </p>
    <p>
        And you may feel like this:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-500x500.png"
            alt="android_fragments_014_y_u_no_have" width="500" height="500" class="aligncenter size-large wp-image-117853"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-500x500.png 500w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have-128x128.png 128w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_014_y_u_no_have.png 700w"
            sizes="(max-width: 500px) 100vw, 500px">
        </a>
    </p>
    <p>
        The lesson: Always keep in mind how the saved state affects your fragments.
    </p>
    <h2>
        Data Binding
    </h2>
    <p>
        While poking around the project you may have noticed a few things:
    </p>
    <ul>
        <li>
            A file called
            <code>
                DataBindingAdapters
            </code>
            .
        </li>
        <li>
            A reference to
            <code>
                dataBinding
            </code>
            in the app module
            <code>
                build.gradle
            </code>
            :
            <pre lang="groovy" class="language-groovy">
                dataBinding { enabled = true }
            </pre>
        </li>
        <li>
            A data section in the
            <code>
                recycler_item_rage_comic.xml
            </code>
            layout file.
            <pre lang="xml" class="language-xml hljs">
                <span class="hljs-tag">
                    &lt;
                    <span class="hljs-name">
                        layout
                    </span>
                    <span class="hljs-attr">
                        xmlns:android
                    </span>
                    =
                    <span class="hljs-string">
                        "http://schemas.android.com/apk/res/android"
                    </span>
                    &gt;
                </span>
                <span class="hljs-tag">
                    &lt;
                    <span class="hljs-name">
                        data
                    </span>
                    &gt;
                </span>
                <span class="hljs-tag">
                    &lt;
                    <span class="hljs-name">
                        variable
                    </span>
                    <span class="hljs-attr">
                        name
                    </span>
                    =
                    <span class="hljs-string">
                        "comic"
                    </span>
                    <span class="hljs-attr">
                        type
                    </span>
                    =
                    <span class="hljs-string">
                        "com.raywenderlich.alltherages.Comic"
                    </span>
                    /&gt;
                </span>
                <span class="hljs-tag">
                    &lt;/
                    <span class="hljs-name">
                        data
                    </span>
                    &gt;
                </span>
                ...
                <span class="hljs-tag">
                    &lt;/
                    <span class="hljs-name">
                        layout
                    </span>
                    &gt;
                </span>
            </pre>
        </li>
        <li>
            A
            <code>
                Comic
            </code>
            data class.
        </li>
    </ul>
    <p>
        If you haven’t used
        <em>
            data binding
        </em>
        before you may be like…
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_canine_coding.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_canine_coding-650x488.png"
            alt="" width="650" height="488" class="aligncenter size-large wp-image-170706"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_canine_coding-650x488.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/android_fragments_003_canine_coding-427x320.png 427w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        Let’s take a quick walkthrough.
    </p>
    <p>
        Normally, if you want to set the value of properties in your layout, you’d
        use something like the following in your fragments and activities:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        programmer.name =
        <span class="hljs-string">
            "a purr programmer"
        </span>
        view.findViewById&lt;TextView&gt;(R.id.name).setText(programmer.name)
    </pre>
    <p>
        The problem with that is that if you change the value of
        <code>
            name
        </code>
        for
        <code>
            programmer
        </code>
        , you would need to do a subsequent
        <code>
            setText
        </code>
        to the
        <code>
            TextView
        </code>
        in order to update the item. Imagine having a tool where you could bind
        a variable from your fragments and activities to your view and allow for
        changes to the variable to automatically update in the View. That is what
        <em>
            data binding
        </em>
        does for you.
    </p>
    <p>
        Looking at our
        <em>
            All The Rages
        </em>
        app, the
        <code>
            enabled=true
        </code>
        in the
        <code>
            build.gradle
        </code>
        enables
        <em>
            data binding
        </em>
        in the application. Your data class contains data that we want to use
        in our fragment and display in our view. The
        <em>
            data
        </em>
        field contains variables consisting of
        <em>
            name
        </em>
        and
        <em>
            type
        </em>
        options that specify the type and name of the variable being bound. This
        data is used in the view using
        <code>
            {@}
        </code>
        notation. For example, the following would set a text field to the value
        held by the
        <em>
            name
        </em>
        field of the
        <em>
            comic
        </em>
        variable:
    </p>
    <pre lang="xml" class="language-xml hljs">
        tools:text="@{comic.name}"
    </pre>
    <p>
        Now that you have your view set up, you need to access your view and
        <em>
            bind
        </em>
        the variables to it. This is where the
        <em>
            data binding
        </em>
        magic comes in! Whenever a view has a
        <code>
            data
        </code>
        field, the framework automatically generates a binding object. The name
        of the object is derived by converting the snake case name of the view
        into camel case and adding
        <em>
            binding
        </em>
        to the name. For example, a view called
        <code>
            recycler_item_rage_comic.xml
        </code>
        would have a corresponding binding called
        <code>
            RecyclerItemRageComicBinding
        </code>
        .
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
                onCreateViewHolder
            </span>
            <span class="hljs-params">
                (viewGroup:
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
        <span class="hljs-comment">
            //1
        </span>
        <span class="hljs-keyword">
            val
        </span>
        recyclerItemRageComicBinding = RecyclerItemRageComicBinding.inflate(layoutInflater,
        viewGroup,
        <span class="hljs-literal">
            false
        </span>
        )
        <span class="hljs-comment">
            //2
        </span>
        <span class="hljs-keyword">
            val
        </span>
        comic = Comic(imageRmesIds[position], names[position], descriptions[position],
        urls[position]) recyclerItemRageComicBinding.comic = comic
    </pre>
    <p>
        You can then inflate the view via the inflater method on the
        <em>
            binding
        </em>
        object and set properties via standard property access mechanisms.
    </p>
    <p>
        Data binding follows a Model-View-ViewModel (MVVM) pattern. MVVM consists
        of three components:
    </p>
    <ul>
        <li>
            <em>
                A View
            </em>
            : The layout file.
        </li>
        <li>
            <em>
                A Model
            </em>
            : The data class
        </li>
        <li>
            <em>
                A View Model/Binder
            </em>
            : The auto-generated binding files.
        </li>
    </ul>
    <p>
        For further reading on the MVVM, and other design patterns, refer to the
        tutorial:
        <a href="https://www.raywenderlich.com/168038/common-design-patterns-android-kotlin"
        target="_blank" title="Common Design Patterns for Android" sl-processed="1">
            Common Design Patterns for Android
        </a>
        . You’ll see more on data biding later on.
    </p>
    <h2>
        Communicating with the Activity
    </h2>
    <p>
        Even though fragments are attached to an activity, they don’t necessarily
        all talk to one another without some further “encouragement” from you.
    </p>
    <p>
        For All the Rages, you’ll need
        <code>
            RageComicListFragment
        </code>
        to let
        <code>
            MainActivity
        </code>
        know when the user has made a selection so that
        <code>
            RageComicDetailsFragment
        </code>
        can display the selection.
    </p>
    <p>
        To start, open
        <em>
            RageComicListFragment.kt
        </em>
        and add the following Kotlin interface at the bottom of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                interface
            </span>
            <span class="hljs-title">
                OnRageComicSelected
            </span>
        </span>
        {
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onRageComicSelected
            </span>
            <span class="hljs-params">
                (comic:
                <span class="hljs-type">
                    Comic
                </span>
                )
            </span>
        </span>
        }
    </pre>
    <p>
        This defines a listener interface for the activity to listen to the fragment.
        The activity will implement this interface, and the fragment will invoke
        the
        <code>
            onRageComicSelected()
        </code>
        when an item is selected, passing the selection to the activity.
    </p>
    <p>
        Add this new field below the existing ones in
        <code>
            RageComicListFragment
        </code>
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
        listener: OnRageComicSelected
    </pre>
    <p>
        This field is a reference to the fragment’s listener, which will be the
        activity.
    </p>
    <p>
        In
        <code>
            onAttach()
        </code>
        , add the following just below
        <code>
            super.onAttach(context)
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            if
        </span>
        (context
        <span class="hljs-keyword">
            is
        </span>
        OnRageComicSelected) { listener = context }
        <span class="hljs-keyword">
            else
        </span>
        {
        <span class="hljs-keyword">
            throw
        </span>
        ClassCastException(context.toString() +
        <span class="hljs-string">
            " must implement OnRageComicSelected."
        </span>
        ) }
    </pre>
    <p>
        This initializes the listener reference. You wait until
        <code>
            onAttach()
        </code>
        to ensure that the fragment actually attached itself. Then you verify
        that the activity implements the
        <code>
            OnRageComicSelected
        </code>
        interface via
        <code>
            instanceof
        </code>
        .
    </p>
    <p>
        If it doesn’t, it throws an exception, since you can’t proceed. If it
        does, you then set the activity as the
        <code>
            listener
        </code>
        for
        <code>
            RageComicListFragment
        </code>
        .
    </p>
    <p>
        In the
        <code>
            onBindViewHolder()
        </code>
        method in
        <code>
            RageComicAdapter
        </code>
        , add this code to the bottom. (Okay, I lied a little; the
        <code>
            RageComicAdapter
        </code>
        doesn’t have
        <i>
            everything
        </i>
        you need!)
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        viewHolder.itemView.setOnClickListener { listener.onRageComicSelected(comic)
        }
    </pre>
    <p>
        This adds a
        <code>
            View.OnClickListener
        </code>
        to each Rage Comic so that it invokes the callback on the listener (the
        activity) to pass along the selection.
    </p>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        and update the class definition to following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainActivity
            </span>
            :
            <span class="hljs-type">
                AppCompatActivity
            </span>
        </span>
        (), RageComicListFragment.OnRageComicSelected {
    </pre>
    <p>
        You will get an error asking you to make
        <code>
            MainActivity
        </code>
        abstract or implement the abstract method
        <code>
            OnRageComicSelected(comic: Comic)
        </code>
        . Don’t fret just yet, you’ll resolve it soon.
    </p>
    <p>
        This code specifies that
        <code>
            MainActivity
        </code>
        is an implementation of the
        <code>
            OnRageComicSelected
        </code>
        interface.
    </p>
    <p>
        For now, you’ll just show a toast to verify that the code works. Add the
        following import below the existing imports so that you can use toasts:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.widget.Toast
    </pre>
    <p>
        Then add the following method below
        <code>
            onCreate()
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
                onRageComicSelected
            </span>
            <span class="hljs-params">
                (comic:
                <span class="hljs-type">
                    Comic
                </span>
                )
            </span>
        </span>
        { Toast.makeText(
        <span class="hljs-keyword">
            this
        </span>
        ,
        <span class="hljs-string">
            "Hey, you selected "
        </span>
        + comic.name +
        <span class="hljs-string">
            "!"
        </span>
        , Toast.LENGTH_SHORT).show() }
    </pre>
    <p>
        The error is gone! Build and run. Once the app launches, click one of
        the Rage Comics. You should see a toast message naming the clicked item:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_015_app_selected_item.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_015_app_selected_item-281x500.png"
            alt="You selected Neil deGrasse Tyson!" width="281" height="500" class="aligncenter size-large wp-image-148997"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_015_app_selected_item-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_015_app_selected_item-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_015_app_selected_item.png 1440w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        Now you’ve got the activity and its fragments talking. You’re like a master
        digital diplomat!
    </p>
    <h2>
        Fragment Arguments and Transactions
    </h2>
    <p>
        Currently,
        <code>
            RageComicDetailsFragment
        </code>
        displays a static
        <code>
            Drawable
        </code>
        and set of
        <code>
            Strings
        </code>
        , but let’s say you want it to display the user’s selection.
    </p>
    <p>
        First, replace the entire view in
        <code>
            fragment_rage_comic_details.xml
        </code>
        with:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                layout
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                data
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                variable
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "comic"
            </span>
            <span class="hljs-attr">
                type
            </span>
            =
            <span class="hljs-string">
                "com.raywenderlich.alltherages.Comic"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                data
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                ScrollView
            </span>
            <span class="hljs-attr">
                xmlns:tools
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/tools"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:fillViewport
            </span>
            =
            <span class="hljs-string">
                "true"
            </span>
            <span class="hljs-attr">
                tools:ignore
            </span>
            =
            <span class="hljs-string">
                "RtlHardcoded"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                LinearLayout
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:gravity
            </span>
            =
            <span class="hljs-string">
                "center"
            </span>
            <span class="hljs-attr">
                android:orientation
            </span>
            =
            <span class="hljs-string">
                "vertical"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                TextView
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/name"
            </span>
            <span class="hljs-attr">
                style
            </span>
            =
            <span class="hljs-string">
                "@style/TextAppearance.AppCompat.Title"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:layout_marginBottom
            </span>
            =
            <span class="hljs-string">
                "0dp"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "@dimen/rage_comic_name_margin_top"
            </span>
            <span class="hljs-attr">
                android:text
            </span>
            =
            <span class="hljs-string">
                "@{comic.name}"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                ImageView
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/comic_image"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "@dimen/rage_comic_image_size"
            </span>
            <span class="hljs-attr">
                android:layout_marginBottom
            </span>
            =
            <span class="hljs-string">
                "@dimen/rage_comic_image_margin_vertical"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "@dimen/rage_comic_image_margin_vertical"
            </span>
            <span class="hljs-attr">
                android:adjustViewBounds
            </span>
            =
            <span class="hljs-string">
                "true"
            </span>
            <span class="hljs-attr">
                android:contentDescription
            </span>
            =
            <span class="hljs-string">
                "@null"
            </span>
            <span class="hljs-attr">
                android:scaleType
            </span>
            =
            <span class="hljs-string">
                "centerCrop"
            </span>
            <span class="hljs-attr">
                imageResource
            </span>
            =
            <span class="hljs-string">
                "@{comic.imageResId}"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                TextView
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/description"
            </span>
            <span class="hljs-attr">
                style
            </span>
            =
            <span class="hljs-string">
                "@style/TextAppearance.AppCompat.Body1"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_marginBottom
            </span>
            =
            <span class="hljs-string">
                "@dimen/rage_comic_description_margin_bottom"
            </span>
            <span class="hljs-attr">
                android:layout_marginLeft
            </span>
            =
            <span class="hljs-string">
                "@dimen/rage_comic_description_margin_left"
            </span>
            <span class="hljs-attr">
                android:layout_marginRight
            </span>
            =
            <span class="hljs-string">
                "@dimen/rage_comic_description_margin_right"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "0dp"
            </span>
            <span class="hljs-attr">
                android:autoLink
            </span>
            =
            <span class="hljs-string">
                "web"
            </span>
            <span class="hljs-attr">
                android:text
            </span>
            =
            <span class="hljs-string">
                "@{comic.text}"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                LinearLayout
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                ScrollView
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                layout
            </span>
            &gt;
        </span>
    </pre>
    <p>
        At the top you’ll see that we’ve added a variable for our
        <em>
            Comic
        </em>
        . The text for
        <em>
            name
        </em>
        and
        <em>
            description
        </em>
        is bound to the variables of the same name in the
        <em>
            Comic
        </em>
        object.
    </p>
    <h3>
        Binding Adapters
    </h3>
    <p>
        On the ImageView for the comic image you’ll notice the following tag:
    </p>
    <pre lang="xml" class="language-xml hljs">
        imageResource="@{comic.imageResId}"
    </pre>
    <p>
        This corresponds to a binding adapter that we’ve created in the
        <code>
            DataBindingAdapters.kt
        </code>
        file.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-meta">
            @BindingAdapter(
            <span class="hljs-meta-string">
                "android:src"
            </span>
            )
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                setImageResoruce
            </span>
            <span class="hljs-params">
                (imageView:
                <span class="hljs-type">
                    ImageView
                </span>
                , resource:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        { imageView.setImageResource(resource) }
    </pre>
    <p>
        A
        <em>
            binding adapter
        </em>
        allows us to perform actions on an element which are not supported by
        default
        <em>
            data binding
        </em>
        . In your case you are storing a resource integer for the image to be
        displayed, but data binding does not provide a default way to display an
        image from an ID. To fix that, you have a
        <em>
            BindingAdapter
        </em>
        that takes a reference to the object that it was invoked from, along with
        a parameter. It uses that to call
        <code>
            setImageResource
        </code>
        on the
        <code>
            imageView
        </code>
        that displays the image for the comic.
    </p>
    <p>
        Now that your view is set up, add the following import to the top of
        <em>
            RageComicDetailsFragment.kt
        </em>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        java.io.Serializable
    </pre>
    <p>
        Replace
        <code>
            newInstance()
        </code>
        with the code shown below:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        const
        <span class="hljs-keyword">
            val
        </span>
        COMIC =
        <span class="hljs-string">
            "comic"
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                newInstance
            </span>
            <span class="hljs-params">
                (comic:
                <span class="hljs-type">
                    Comic
                </span>
                )
            </span>
        </span>
        : RageComicDetailsFragment {
        <span class="hljs-keyword">
            val
        </span>
        args = Bundle() args.putSerializable(COMIC, comic
        <span class="hljs-keyword">
            as
        </span>
        Serializable)
        <span class="hljs-keyword">
            val
        </span>
        fragment = RageComicDetailsFragment() fragment.arguments = args
        <span class="hljs-keyword">
            return
        </span>
        fragment }
    </pre>
    <p>
        A fragment can take initialization parameters through its arguments, which
        you access via the
        <code>
            arguments
        </code>
        property. The arguments are actually a
        <code>
            Bundle
        </code>
        that stores them as key-value pairs, just like the
        <code>
            Bundle
        </code>
        in
        <code>
            Activity.onSaveInstanceState
        </code>
        .
    </p>
    <p>
        You create and populate the arguments’
        <code>
            Bundle
        </code>
        , set the
        <code>
            arguments
        </code>
        , and when you need the values later, you reference
        <code>
            arguments
        </code>
        property to retrieve them.
    </p>
    <p>
        As you learned earlier, when a fragment is re-created, the default empty
        constructor is used — no parameters for you.
    </p>
    <p>
        Because the fragment can recall initial parameters from its persisted
        arguments, you can utilize them in the re-creation. The above code also
        stores information about the selected Rage Comic in the
        <code>
            RageComicDetailsFragment
        </code>
        arguments.
    </p>
    <p>
        Add the following import to the top of
        <em>
            RageComicDetailsFragment.kt
        </em>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        com.raywenderlich.alltherages.databinding.FragmentRageComicDetailsBinding
    </pre>
    <p>
        Now, replace the contents of
        <em>
            onCreateView()
        </em>
        with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        fragmentRageComicDetailsBinding = FragmentRageComicDetailsBinding.inflate(inflater!!,
        container,
        <span class="hljs-literal">
            false
        </span>
        )
        <span class="hljs-keyword">
            val
        </span>
        comic = arguments.getSerializable(COMIC)
        <span class="hljs-keyword">
            as
        </span>
        Comic fragmentRageComicDetailsBinding.comic = comic comic.text = String.format(getString(R.string.description_format),
        comic.description, comic.url)
        <span class="hljs-keyword">
            return
        </span>
        fragmentRageComicDetailsBinding.root
    </pre>
    <p>
        Since you want to dynamically populate the UI of the
        <code>
            RageComicDetailsFragment
        </code>
        with the selection, you grab the reference to the
        <code>
            FragmentRageComicDetailsBinding
        </code>
        in the fragment view in
        <code>
            onCreateView
        </code>
        . Next, you bind the view comic with the Comic that you’ve passed to
        <code>
            RageComicDetailsFragment
        </code>
        .
    </p>
    <p>
        Finally, you need to create and display a
        <code>
            RageComicDetailsFragment
        </code>
        when a user clicks an item, instead of just showing a toast. Open
        <em>
            MainActivity
        </em>
        and replace the logic inside
        <code>
            onRageComicSelected
        </code>
        with:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        detailsFragment = RageComicDetailsFragment.newInstance(comic) supportFragmentManager.beginTransaction()
        .replace(R.id.root_layout, detailsFragment,
        <span class="hljs-string">
            "rageComicDetails"
        </span>
        ) .addToBackStack(
        <span class="hljs-literal">
            null
        </span>
        ) .commit()
    </pre>
    <p>
        You’ll find that this code is similar to your first transaction which
        added the list to
        <code>
            MainActivity
        </code>
        , but there are also some notable differences.
    </p>
    <ul>
        <li>
            You create a fragment instance that included some nifty parameters.
        </li>
        <li>
            You call
            <code>
                replace()
            </code>
            , instead of
            <code>
                add
            </code>
            , which removes the fragment currently in the container and then adds
            the new Fragment.
        </li>
        <li>
            You call another new friend: the
            <code>
                addToBackStack()
            </code>
            of
            <code>
                FragmentTransaction
            </code>
            . Fragments have a
            <em>
                back stack
            </em>
            , or history, just like Activities.
        </li>
    </ul>
    <p>
        The fragment back stack is not independent of the activity back stack.
        Think of it as an extra stack of history on top of that of the host activity.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_d004_fragments_backstack-1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_d004_fragments_backstack-1-650x381.png"
            alt="Fragments and back stack" width="650" height="381" class="aligncenter size-large wp-image-149114"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_d004_fragments_backstack-1-650x381.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_d004_fragments_backstack-1-480x281.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_d004_fragments_backstack-1.png 1024w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        When you navigate between activities, each one gets placed on the activity
        back stack. Whenever you commit a
        <code>
            FragmentTransaction
        </code>
        , you have the option to add that transaction to the back stack.
    </p>
    <p>
        So, what does
        <code>
            addToBackStack()
        </code>
        do? It adds the
        <code>
            replace()
        </code>
        to the back stack so that when the user hits the device’s back button
        it undoes the transaction. In this case, hitting the back button sends
        the user back to the full list.
    </p>
    <p>
        The
        <code>
            add()
        </code>
        transaction for the list omits calling
        <code>
            addToBackStack()
        </code>
        . This means that the transaction is part of the same history entry as
        the entire activity. If the user hits the back button from the list, it
        backs the user out of the app.
    </p>
    <p>
        Now, build and run and you should see details about each Rage when you
        tap on them:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_017_app_showing_details.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_017_app_showing_details-281x500.png"
            alt="Yay! Actual details on Neil deGrasse Tyson" width="281" height="500"
            class="aligncenter size-large wp-image-148998" srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_017_app_showing_details-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_017_app_showing_details-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_017_app_showing_details.png 1440w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        With that your done! You now have a
        <em>
            All The Rages
        </em>
        app that displays details about the comics.
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
        You can download the final project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/AllTheRages-Final.zip"
        sl-processed="1">
            here
        </a>
        .
    </p>
    <p>
        There is
        <i>
            a lot
        </i>
        more to learn and do with fragments. Like any kind of tool or feature,
        consider whether fragments fit your app’s needs, and if they do, try to
        follow best practices and conventions.
    </p>
    <p>
        To take your skills to the next level, here are some additional things
        to explore:
    </p>
    <ul>
        <li>
            Using fragments within a
            <code>
                ViewPager
            </code>
            . Many apps, including the Play Store, utilize a swipeable, tabbed content
            structure via
            <code>
                ViewPagers
            </code>
            .
        </li>
        <li>
            Using a more powerful, advantageous
            <code>
                DialogFragment
            </code>
            instead of a plain vanilla dialog or
            <code>
                AlertDialog
            </code>
            .
        </li>
        <li>
            Playing with how fragments interact with other parts of an Activity, like
            the app bar.
        </li>
        <li>
            Creating adaptive UIs with fragments. In fact, you should run through
            <a href="https://www.raywenderlich.com/114066/adaptive-ui-android-tutorial"
            target="_blank" title="Adaptive UI in Android Tutorial" sl-processed="1">
                Adaptive UI in Android Tutorial
            </a>
            .
        </li>
        <li>
            Using fragments as part of the implementation of a high-level behavioral
            architecture. You can take a look at
            <a href="https://www.raywenderlich.com/168038/common-design-patterns-android-kotlin"
            target="_blank" title="Common Design Patterns for Android" sl-processed="1">
                Common Design Patterns for Android
            </a>
            as a good starting point to get the architecture ball rolling.
        </li>
    </ul>
</div>