# Android Fragment教程：介绍
---
#### [原文地址](https://www.raywenderlich.com/149112/android-fragments-tutorial-introduction) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-250x250.png"
            alt="Fragments-feature" width="250" height="250" class="alignright size-thumbnail wp-image-154115"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2015/12/Fragments-feature-128x128.png 128w"
            sizes="(max-width: 250px) 100vw, 250px">
        </a>
        本教程将会介绍Android的Fragment。你将学习Android Fragment的基本概念，并创建一个可以展示暴走漫画的app。
    </p>
    <p>
        <em>
            更新日志：
        </em>
        本教程已由Huyen Tue Dao更新至适配API 25和Android Studio 2.2.2的版本。原教程亦由Huyen Tue Dao编写。
    </p>
    <div class="note">
        <em>
            fragment
        </em>
        |
        <i>
            noun
        </i>
        | /’frag-mənt/
        <br>
        某事物的孤立的或未完成的部分
    </div>
    <p>
        fragment是一个Android的组件，用来管理activity中的一部分UI。正如它的名字所暗示的，fragment并非是一个独立的实体，而是屈从于某个activity下。
    </p>
    <p>
        在很多方面上，它都模仿了activity中的某些特性。
    </p>
    <p>
        想象一下假如你是一个activity。你有很多的工作想做，因此你就雇佣了很多迷你的自己来运行，通过洗衣和交税来换取住宿和食物。这就非常像是activity和fragment之间的关系。
    </p>
    <p>
        现在，就像你实际上并不需要几个部下听从你的命令，你并不一定需要使用fragment。然而，如果你可以很好地使用fragment，它就可以提供：
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
        <br>
        在本教程中，你将构建一个暴走漫画的迷你百科全书。app将展示一个由暴走漫画构成的格子视图。当选中一副暴走漫画的时候，app就会展示与它相关的信息。在本教程中，你将学到：
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
            ：本教程假设你已熟悉Android编程的基础，理解activity的生命周期。如果你是一个Android的纯小白，你应当首先查阅
            <a href="http://www.raywenderlich.com/78574/android-tutorial-for-beginners-part-1"
            target="_blank" title=" Android Tutorial for Beginners " sl-processed="1">
                Android Tutorial for Beginners
            </a>
            和
            <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Introduction%20to%20Android%20Activities%20with%20Kotlin.md"
            target="_blank" title=" Introduction to Activities " sl-processed="1">
                Activity介绍
            </a>
            。本教程还会用到Android的
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
        </p>
    </div>
    <p>
        接下来就开始学习fragments！
    </p>
    <h2>
        Android Fragment入门
    </h2>
    <p>
        下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/AllTheRages-Starter-1.zip"
        target="_blank" title="starter project" sl-processed="1">
            起始项目
        </a>
        ，解压并启动
        <em>
            Android Studio
        </em>
        。
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
        <br>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_002_android_studio_welcome_screen.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_002_android_studio_welcome_screen.png"
            alt="Android Studio Welcome Screen" width="648" height="436" class="aligncenter size-full wp-image-148989"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_002_android_studio_welcome_screen.png 648w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_002_android_studio_welcome_screen-476x320.png 476w"
            sizes="(max-width: 648px) 100vw, 648px">
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
        。还有一些供你fragment使用的模板布局文件，非fragment的代码，以及一个fragment类。
    </p>
    <p>
        <code>
            MainActivity
        </code>
        会持有你所有小小的fragment，而
        <code>
            RageComicListFragment
        </code>
        则包含了用来展示暴走漫画内容列表的代码，这样你就可以将注意力集中到fragment上了。
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
        当你添加一个fragment的时候，下列的生命周期事件就会被触发：
    </p>
    <ul>
        <li>
            <code>
                onAttach
            </code>
            ：当fragment被依附到相应的activity上时被调用
        </li>
        <li>
            <code>
                onCreate
            </code>
            ：当一个新的fragment实例被初始化时调用，通常发生在它被附加到相应activity上后被调用 - fragment有一点像是病毒
        </li>
        <li>
            <code>
                onCreateView
            </code>
            : when a fragment creates its portion of the view hierarchy, which is
            added to its activity’s view hierarchy
        </li>
        <li>
            <code>
                onActivityCreated
            </code>
            ：当fragment的activity完成了它的
            <code>
                onCreate
            </code>
            事件之后调用
        </li>
        <li>
            <code>
                onStart
            </code>
            ：当fragment变为可见状态后调用。fragment只会在它的activity启动之后才会启动，且通常都是activity一启动之后，它就启动
        </li>
        <li>
            <code>
                onResume
            </code>
            ：当fragment变为可见且可交互的状态后调用。fragment resume只会在它的activity resume之后，且通常都是activity一resume之后，它就resume
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
            ：当fragment变为不可交互的状态时触发。它仅会在一个fragment将被移除或替代的时候，或其activity被pause的时候发生
        </li>
        <li>
            <code>
                onStop
            </code>
            ：当fragment变为不可见的状态时触发。它仅会在一个fragment将被移除或替代的时候，或其activity被停止的时候发生
        </li>
        <li>
            <code>
                onDestroyView
            </code>
            ：当fragment的view和创建在
            <code>
                onCreateView
            </code>
            中的相关资源从activity的view层级中被移除并销毁的时候触发
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
        Fragment是在定位于平板电脑，快要被遗忘的Honeycomb版本时被引入的。它用来为单个app创建特定于设备的布局。
    </p>
    <p>
        <em>
            v4支持库
        </em>
        提供了对小于Android 3.0版本的设备的fragment的实现，特别是
        <code>
            android.support.v4.app.Fragment
        </code>
        以下的包。
    </p>
    <p>
        即使你的app运行与4.0+的版本，你仍然可以使用支持fragment。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_007_support_fragment_why.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_007_support_fragment_why.png"
            alt="android_fragments_007_support_fragment_why" width="360" height="336"
            class="aligncenter size-full wp-image-117846" srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_007_support_fragment_why.png 360w, https://koenig-media.raywenderlich.com/uploads/2015/10/android_fragments_007_support_fragment_why-343x320.png 343w"
            sizes="(max-width: 360px) 100vw, 360px">
        </a>
    </p>
    <p>
        因为不仅仅是开发者会依赖支持库，其它的库也需要它，比如
        <em>
            v7 AppCompat Library
        </em>
        ，其中含有
        <code>
            AppCompatActivity
        </code>
        以及其它的对于API 21的向后支持的功能。事实上，
        <code>
            AppCompatActivity
        </code>
        就是v4的
        <code>
            FragmentActivity
        </code>
        的子类。
    </p>
    <p>
        所有，如果你想获得Lollipop及以上版本酷毙了的功能，你就需要走和v4一样的路子。
    </p>
    <h2>
        创建Fragment
    </h2>
    <p>
        最终，所有的暴走漫画会在启动的时候被展示位一个列表，点击其中的一项则会这幅漫画相应的详情。首先你将会创建详情页。
    </p>
    <p>
        在Android Studio中打开起始项目，并在
        <em>
            app -&gt; res -&gt; layout
        </em>
        下找到
        <em>
            fragment_rage_comic_details.xml
        </em>
        ，这个XML文件就指定了漫画详情展示的布局。它还展示了drawable资源和相关的string资源之一。
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
        选择Android Studio的
        <em>
            Project tab
        </em>
        并找到
        <em>
            RageComicDetailsFragment
        </em>
        文件。这个类用来负责展示被选择漫画的展示详情。
    </p>
    <p>
        在
        <em>
            RageComicDetailsFragment.java
        </em>
        中，会看到类似如下的代码：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">import</span> android.os.Bundle;
<span class="hljs-keyword">import</span> android.support.annotation.Nullable;
<span class="hljs-keyword">import</span> android.support.v4.app.Fragment;
<span class="hljs-keyword">import</span> android.view.LayoutInflater;
<span class="hljs-keyword">import</span> android.view.View;
<span class="hljs-keyword">import</span> android.view.ViewGroup;

<span class="hljs-comment">//1	</span>
<span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RageComicDetailsFragment</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Fragment</span> </span>{
  <span class="hljs-comment">//2	  </span>
  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">static</span> RageComicDetailsFragment <span class="hljs-title">newInstance</span><span class="hljs-params">()</span> </span>{
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">new</span> RageComicDetailsFragment();
  }

  <span class="hljs-comment">//3	</span>
  <span class="hljs-meta">@Nullable</span>
  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">public</span> View <span class="hljs-title">onCreateView</span><span class="hljs-params">(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)</span> </span>{
    <span class="hljs-keyword">return</span> inflater.inflate(R.layout.fragment_rage_comic_details, container, <span class="hljs-keyword">false</span>);
  }
}
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
        If you specify a non-empty constructor but not explicitly write an empty
        constructor, Lint will give you an error:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_010_fragment_details_no_default_constructor_warning.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_010_fragment_details_no_default_constructor_warning.png"
            alt="Lint warning for no default constructor" width="580" height="131"
            class="aligncenter size-full wp-image-148994" srcset="https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_010_fragment_details_no_default_constructor_warning.png 580w, https://koenig-media.raywenderlich.com/uploads/2016/12/android_fragments_010_fragment_details_no_default_constructor_warning-480x108.png 480w"
            sizes="(max-width: 580px) 100vw, 580px">
        </a>
    </p>
    <p>
        Now it will compile still, but when you run your application, you’ll get
        an even nastier exception.
    </p>
    <p>
        You probably know that Android may destroy and later re-create an activity
        and all its associated fragments when the app goes into the background.
        When the activity comes back, its
        <code>
            FragmentManager
        </code>
        starts re-creating fragments by using the empty default constructor. If
        it cannot find one, you get an exception.
    </p>
    <p>
        Because of this, it is best practice to never specify any non-empty constructors,
        and in fact, the easiest thing to do is to specify none as you just did.
    </p>
    <p>
        Wait, what if you need to pass information or data to a Fragment? Hold
        on tight: you’ll get the answer to that later.
    </p>
    <h2>
        Adding a Fragment
    </h2>
    <p>
        Here’s where you get to add your own shiny new fragment using the simplest
        approach: adding it to the activity’s XML layout.
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
        Here you’re placing a
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
        you just placed. (Yes, I know, you just put it there — sorry.) You’ll
        replace it with the list of Rage Comics.
    </p>
    <p>
        Open
        <em>
            RageComicListFragment.java
        </em>
        , which has all the lovely list code. You can see that the
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
            RageComicListFragment.java
        </em>
        , and add these imports directly below the existing imports:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.content.res.Resources;
        <span class="hljs-keyword">
            import
        </span>
        android.content.res.TypedArray;
        <span class="hljs-keyword">
            import
        </span>
        android.support.annotation.Nullable;
        <span class="hljs-keyword">
            import
        </span>
        android.os.Bundle;
        <span class="hljs-keyword">
            import
        </span>
        android.support.v7.widget.GridLayoutManager;
        <span class="hljs-keyword">
            import
        </span>
        android.app.Activity;
    </pre>
    <p>
        The first two imports allow you to access some string resources that you
        will use as data in the list. The fifth import, the
        <code>
            GridLayoutManager
        </code>
        , helps in positioning items in the Rage Comic list. The other imports
        are for standard fragment overrides.
    </p>
    <p>
        Inside of
        <em>
            RageComicListFragment.java
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
    <pre lang="java" class="language-java hljs">
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onAttach
            </span>
            <span class="hljs-params">
                (Context context)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onAttach(context);
        <span class="hljs-comment">
            // Get rage face names and descriptions.
        </span>
        <span class="hljs-keyword">
            final
        </span>
        Resources resources = context.getResources(); mNames = resources.getStringArray(R.array.names);
        mDescriptions = resources.getStringArray(R.array.descriptions); mUrls =
        resources.getStringArray(R.array.urls);
        <span class="hljs-comment">
            // Get rage face images.
        </span>
        <span class="hljs-keyword">
            final
        </span>
        TypedArray typedArray = resources.obtainTypedArray(R.array.images);
        <span class="hljs-keyword">
            final
        </span>
        <span class="hljs-keyword">
            int
        </span>
        imageCount = mNames.length; mImageResIds =
        <span class="hljs-keyword">
            new
        </span>
        <span class="hljs-keyword">
            int
        </span>
        [imageCount];
        <span class="hljs-keyword">
            for
        </span>
        (
        <span class="hljs-keyword">
            int
        </span>
        i =
        <span class="hljs-number">
            0
        </span>
        ; i &lt; imageCount; i++) { mImageResIds[i] = typedArray.getResourceId(i,
        <span class="hljs-number">
            0
        </span>
        ); } typedArray.recycle(); }
        <span class="hljs-meta">
            @Nullable
        </span>
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            View
            <span class="hljs-title">
                onCreateView
            </span>
            <span class="hljs-params">
                (LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            final
        </span>
        View view = inflater.inflate(R.layout.fragment_rage_comic_list, container,
        <span class="hljs-keyword">
            false
        </span>
        );
        <span class="hljs-keyword">
            final
        </span>
        Activity activity = getActivity();
        <span class="hljs-keyword">
            final
        </span>
        RecyclerView recyclerView = (RecyclerView) view.findViewById(R.id.recycler_view);
        recyclerView.setLayoutManager(
        <span class="hljs-keyword">
            new
        </span>
        GridLayoutManager(activity,
        <span class="hljs-number">
            2
        </span>
        )); recyclerView.setAdapter(
        <span class="hljs-keyword">
            new
        </span>
        RageComicAdapter(activity));
        <span class="hljs-keyword">
            return
        </span>
        view; }
    </pre>
    <p>
        <code>
            onAttach()
        </code>
        contains code that accesses the resources you need via the
        <code>
            Context
        </code>
        to which the fragment has attached. Because the code is in
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
        Generally, if you have to poke and prod at a fragment's view,
        <code>
            onCreateView()
        </code>
        is a good place to start because you have the view right there.
    </p>
    <p>
        Next open
        <em>
            MainActivity.java
        </em>
        and replace
        <code>
            onCreate()
        </code>
        with the following:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                protected
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onCreate
            </span>
            <span class="hljs-params">
                (Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState); setContentView(R.layout.activity_main);
        <span class="hljs-keyword">
            if
        </span>
        (savedInstanceState ==
        <span class="hljs-keyword">
            null
        </span>
        ) { getSupportFragmentManager() .beginTransaction() .add(R.id.root_layout,
        RageComicListFragment.newInstance(),
        <span class="hljs-string">
            "rageComicList"
        </span>
        ) .commit(); } }
    </pre>
    <p>
        Here you get
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
        Build, run and you'll see a Rage-filled list once the app launches:
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
        , which are basically fragment operations such as, add, remove, etc.
    </p>
    <p>
        First you grab the
        <code>
            FragmentManager
        </code>
        by calling
        <code>
            getSupportFragmentManager()
        </code>
        , as opposed to
        <code>
            getFragmentManager
        </code>
        since you are using support fragments.
    </p>
    <p>
        Then you ask that
        <code>
            FragmentManager
        </code>
        to start a new transaction by calling
        <code>
            beginTransaction()
        </code>
        -- you probably figured that out yourself. Next you specify the add operation
        that you want by calling
        <code>
            add
        </code>
        and passing in:
    </p>
    <ul>
        <li>
            The view ID of a container for the fragment's view hierarchy in the activity's
            layout. If you sneak a quick peek at
            <code>
                activity_main.xml
            </code>
            , you'll find
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
        An
        <code>
            if
        </code>
        block contains the code that displays the fragment and checks that the
        activity doesn't have saved state. When an activity is saved, all of its
        active fragments are also saved. If you don't perform this check, this
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
        And you would be like this:
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
        Communicating with the Activity
    </h2>
    <p>
        Even though fragments are attached to an activity, they don't necessarily
        all talk to one another without some further "encouragement" from you.
    </p>
    <p>
        For All the Rages, you'll need
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
            RageComicListFragment.java
        </em>
        and add the following Java interface at the bottom:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
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
                void
            </span>
            <span class="hljs-title">
                onRageComicSelected
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-keyword">
                    int
                </span>
                imageResId, String name, String description, String url)
            </span>
        </span>
        ; }
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
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            private
        </span>
        OnRageComicSelected mListener;
    </pre>
    <p>
        This field is a reference to the fragment's listener, which will be the
        activity.
    </p>
    <p>
        In
        <code>
            onAttach()
        </code>
        , add the following just below
        <code>
            super.onAttach(context);
        </code>
        :
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            if
        </span>
        (context
        <span class="hljs-keyword">
            instanceof
        </span>
        OnRageComicSelected) { mListener = (OnRageComicSelected) context; }
        <span class="hljs-keyword">
            else
        </span>
        {
        <span class="hljs-keyword">
            throw
        </span>
        <span class="hljs-keyword">
            new
        </span>
        ClassCastException(context.toString() +
        <span class="hljs-string">
            " must implement OnRageComicSelected."
        </span>
        ); }
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
        If it doesn't, it throws an exception since you can't proceed. If it does,
        then you set the activity as the
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
        method, add this code to the bottom -- okay, I fibbed a little; the
        <code>
            RageComicAdapter
        </code>
        doesn't have
        <i>
            everything
        </i>
        you need):
    </p>
    <pre lang="java" class="language-java hljs">
        viewHolder.itemView.setOnClickListener(
        <span class="hljs-keyword">
            new
        </span>
        View.OnClickListener() {
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onClick
            </span>
            <span class="hljs-params">
                (View v)
            </span>
        </span>
        { mListener.onRageComicSelected(imageResId, name, description, url); }
        });
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
            MainActivity.java
        </em>
        and update the class definition to following:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainActivity
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                AppCompatActivity
            </span>
            <span class="hljs-keyword">
                implements
            </span>
            <span class="hljs-title">
                RageComicListFragment
            </span>
            .
            <span class="hljs-title">
                OnRageComicSelected
            </span>
        </span>
        {
    </pre>
    <p>
        You will get an error asking you to make
        <code>
            MainActivity
        </code>
        abstract or implement abstract method
        <code>
            OnRageComicSelected(int, String, String, String)
        </code>
        . Don't fret just yet, you'll resolve it soon.
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
        For now, you'll just show a toast to verify that the code works. Add the
        following import below the existing imports so that you can use toasts:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.widget.Toast;
    </pre>
    <p>
        And then add the following method below
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onRageComicSelected
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-keyword">
                    int
                </span>
                imageResId, String name, String description, String url)
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
        + name +
        <span class="hljs-string">
            "!"
        </span>
        , Toast.LENGTH_SHORT).show(); }
    </pre>
    <p>
        There you go, the error is gone! Build and run. Once the app launches,
        click one of the Rage Comics. You should see a toast message naming the
        clicked item:
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
        You got the activity and its fragments talking. You're like a master digital
        diplomat.
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
        , but say you want it to display the user's selection.
    </p>
    <p>
        Open
        <em>
            RageComicDetailsFragment.java
        </em>
        and add the following constants at the top of the class definition:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            static
        </span>
        <span class="hljs-keyword">
            final
        </span>
        String ARGUMENT_IMAGE_RES_ID =
        <span class="hljs-string">
            "imageResId"
        </span>
        ;
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            static
        </span>
        <span class="hljs-keyword">
            final
        </span>
        String ARGUMENT_NAME =
        <span class="hljs-string">
            "name"
        </span>
        ;
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            static
        </span>
        <span class="hljs-keyword">
            final
        </span>
        String ARGUMENT_DESCRIPTION =
        <span class="hljs-string">
            "description"
        </span>
        ;
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            static
        </span>
        <span class="hljs-keyword">
            final
        </span>
        String ARGUMENT_URL =
        <span class="hljs-string">
            "url"
        </span>
        ;
    </pre>
    <p>
        These constants are keys you will use to save and restore the fragment's
        state.
    </p>
    <p>
        Replace
        <code>
            newInstance()
        </code>
        with the code shown below:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                static
            </span>
            RageComicDetailsFragment
            <span class="hljs-title">
                newInstance
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-keyword">
                    int
                </span>
                imageResId, String name, String description, String url)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            final
        </span>
        Bundle args =
        <span class="hljs-keyword">
            new
        </span>
        Bundle(); args.putInt(ARGUMENT_IMAGE_RES_ID, imageResId); args.putString(ARGUMENT_NAME,
        name); args.putString(ARGUMENT_DESCRIPTION, description); args.putString(ARGUMENT_URL,
        url);
        <span class="hljs-keyword">
            final
        </span>
        RageComicDetailsFragment fragment =
        <span class="hljs-keyword">
            new
        </span>
        RageComicDetailsFragment(); fragment.setArguments(args);
        <span class="hljs-keyword">
            return
        </span>
        fragment; }
    </pre>
    <p>
        A fragment can take initialization parameters through its arguments, which
        you access via
        <code>
            getArguments()
        </code>
        and
        <code>
            setArguments()
        </code>
        . The arguments are actually a
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
        You create and populate the arguments'
        <code>
            Bundle
        </code>
        , call
        <code>
            setArguments
        </code>
        , and when you need the values later, you call
        <code>
            getArguments
        </code>
        to retrieve them.
    </p>
    <p>
        As you learned earlier, when a fragment is re-created, the default empty
        constructor is used -- no parameters for you.
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
        Add the following imports to the top of
        <em>
            RageComicDetailsFragment.java
        </em>
        :
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.widget.ImageView;
        <span class="hljs-keyword">
            import
        </span>
        android.widget.TextView;
    </pre>
    <p>
        Now, replace
        <em>
            onCreateView()
        </em>
        with the following:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-meta">
            @Nullable
        </span>
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            View
            <span class="hljs-title">
                onCreateView
            </span>
            <span class="hljs-params">
                (LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            final
        </span>
        View view = inflater.inflate(R.layout.fragment_rage_comic_details, container,
        <span class="hljs-keyword">
            false
        </span>
        );
        <span class="hljs-keyword">
            final
        </span>
        ImageView imageView = (ImageView) view.findViewById(R.id.comic_image);
        <span class="hljs-keyword">
            final
        </span>
        TextView nameTextView = (TextView) view.findViewById(R.id.name);
        <span class="hljs-keyword">
            final
        </span>
        TextView descriptionTextView = (TextView) view.findViewById(R.id.description);
        <span class="hljs-keyword">
            final
        </span>
        Bundle args = getArguments(); imageView.setImageResource(args.getInt(ARGUMENT_IMAGE_RES_ID));
        nameTextView.setText(args.getString(ARGUMENT_NAME));
        <span class="hljs-keyword">
            final
        </span>
        String text = String.format(getString(R.string.description_format), args.getString
        (ARGUMENT_DESCRIPTION), args.getString(ARGUMENT_URL)); descriptionTextView.setText(text);
        <span class="hljs-keyword">
            return
        </span>
        view; }
    </pre>
    <p>
        Since you want to dynamically populate the UI of the
        <code>
            RageComicDetailsFragment
        </code>
        with the selection, you grab references to the
        <code>
            ImageView
        </code>
        and
        <code>
            TextViews
        </code>
        in the fragment view in
        <code>
            onCreateView
        </code>
        . Then you populate them with the image and text you passed to
        <code>
            RageComicDetailsFragment
        </code>
        , using them as arguments.
    </p>
    <p>
        Finally, you need to create and display a
        <code>
            RageComicDetailsFragment
        </code>
        when a user clicks an item, instead of just showing a dinky little toast.
        Open
        <em>
            MainActivity
        </em>
        and replace the logic inside
        <code>
            onRageComicSelected
        </code>
        with:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onRageComicSelected
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-keyword">
                    int
                </span>
                imageResId, String name, String description, String url)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            final
        </span>
        RageComicDetailsFragment detailsFragment = RageComicDetailsFragment.newInstance(imageResId,
        name, description, url); getSupportFragmentManager() .beginTransaction()
        .replace(R.id.root_layout, detailsFragment,
        <span class="hljs-string">
            "rageComicDetails"
        </span>
        ) .addToBackStack(
        <span class="hljs-keyword">
            null
        </span>
        ) .commit(); }
    </pre>
    <p>
        The code includes some classes you haven't used previously. So you need
        to fire off a couple of
        <em>
            option + enter
        </em>
        sequences to import the missing classes.
    </p>
    <p>
        You'll find that this code is similar to your first transaction that added
        the list to
        <code>
            MainActivity
        </code>
        , but there are some notable differences.
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
            , or history, just like activities.
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
        So what does
        <code>
            addToBackStack()
        </code>
        do? It adds the
        <code>
            replace()
        </code>
        to the back stack so that when the user hits the device's back button
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
        Guess what? That's all the code, so build and run.
    </p>
    <p>
        There won't be too much difference at first; it's still the same ol' list.
        This time, however, if you click on a Rage Comic, you should see the details
        for that comic instead of a dinky little toast:
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
        Woo hoo! Your app is now officially All the Rages, and you have a nice
        understanding of fragments.
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
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/12/AllTheRages.zip"
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
        consider whether fragments fit your app's needs and if they do, try to
        follow best practices and conventions.
    </p>
    <p>
        To take your skills to the next level, here are some things to explore:
    </p>
    <ul>
        <li>
            Using fragments within a
            <code>
                ViewPager
            </code>
            : many apps, including the Play Store, utilize a swipeable, tabbed content
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
            instead of a plain old dialog or
            <code>
                AlertDialog
            </code>
            .
        </li>
        <li>
            Playing with how fragments interact with other parts of the activity,
            like the app bar.
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
            <a href="https://www.raywenderlich.com/109843/common-design-patterns-for-android"
            target="_blank" title="Common Design Patterns for Android" sl-processed="1">
                Common Design Patterns for Android
            </a>
            and finding a good starting off point to get the architecture ball rolling.
        </li>
    </ul>
</div>