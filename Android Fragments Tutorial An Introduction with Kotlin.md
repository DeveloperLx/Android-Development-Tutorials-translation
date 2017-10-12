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
        在Android中，当使用fragment时，你可以使用两种fragment的实现。一种是由平台版本所提供的，也就是用户正在运行的Android的版本所提供。例如，一台运行Android 6.0（SDK版本23）的设备，就会运行库的平台版本23。
    </p>
    <p>
        第二种是支持库的fragment。导入一个支持库到你的项目中和导入其它的第三方库没有什么差别。它在开发支持多版本Android的app时，有两个好处。
    </p>
    <p>
        首先，它确保了你的代码在不同设备不同平台版本上的一致性。这就意味着bug的修复会在使用这些库的不同版本的Android上更加得一致。
    </p>
    <p>
        其次，当新的特性被添加到最新版本的Android上时，Android的团队通常就会通过支持库来将其进行向后兼容，以便开发者使用较旧版本的Android。
    </p>
    <h3>
        到底该使用哪个库？
    </h3>
    <p>
        如果你要编写支持多个版本Android和多个版本设备的app，你就应当为Fragment采取支持库的方案。你同样需要为其它的功能采用支持库的方案。这是大多数的高级Android开发者和Android核心团队所认为的最佳实践。唯有在你想为非常特定版本的Android做开发的时候，才会采用平台库的方案。
    </p>
    <p>
        换句话就是：如果可以的话，就尽量使用支持库的方案。对于fragment，就是使用
        <em>
            the v4 support library
        </em>
        了。
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
            RageComicDetailsFragment.kt
        </em>
        中，会看到类似如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.os.Bundle
<span class="hljs-keyword">import</span> android.support.v4.app.Fragment
<span class="hljs-keyword">import</span> android.view.LayoutInflater
<span class="hljs-keyword">import</span> android.view.View
<span class="hljs-keyword">import</span> android.view.ViewGroup

<span class="hljs-comment">//1</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">RageComicDetailsFragment</span> : <span class="hljs-type">Fragment</span></span>() {

  <span class="hljs-comment">//2</span>
  <span class="hljs-keyword">companion</span> <span class="hljs-keyword">object</span> {
    <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">newInstance</span><span class="hljs-params">()</span></span>: RageComicDetailsFragment {
      <span class="hljs-keyword">return</span> RageComicDetailsFragment()
    }
  }

  <span class="hljs-comment">//3</span>
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateView</span><span class="hljs-params">(inflater: <span class="hljs-type">LayoutInflater</span>?, container: <span class="hljs-type">ViewGroup</span>?,
                            savedInstanceState: <span class="hljs-type">Bundle</span>?)</span></span>: View? {
    <span class="hljs-keyword">return</span> inflater?.inflate(R.layout.fragment_rage_comic_details, container, <span class="hljs-literal">false</span>)
  }

}
</pre>
    <p>
        上述代码：
    </p>
    <ol>
        <li>
            声明
            <code>
                RageComicDetailsFragment
            </code>
            作为
            <code>
                Fragment
            </code>
            的子类。
        </li>
        <li>
            提供了一个方法用来创建这个fragment的实例，这是一个工厂方法。
        </li>
        <li>
            创建由fragment所控制的view的层级。
        </li>
    </ol>
    <p>
        Activity使用
        <code>
            setContentView()
        </code>
        来指定它相应的布局文件，而fragment则在
        <code>
            onCreateView()
        </code>
        中创建它们的view层级。这里你调用
        <code>
            LayoutInflater.inflate
        </code>
        来创建
        <code>
            RageComicDetailsFragment
        </code>
        的层级。
    </p>
    <p>
        <code>
            inflate
        </code>
        的第三个参数确定了是否要将其添加到
        <code>
            container
        </code>
        上。container就是将持有fragment的view层级的父view。你应当总是将其设置为
        <code>
            false
        </code>
        ：
        <code>
            FragmentManager
        </code>
        将负责将fragment添加到container上。
    </p>
    <p>
        这里有一个新的东东：
        <code>
            FragmentManager
        </code>
        。每个activity都会有一个
        <code>
            FragmentManager
        </code>
        来管理它的fragment。它还提供了一个供你访问，添加和移除的界面。
    </p>
    <p>
        你会注意到尽管
        <code>
            RageComicDetailsFragment
        </code>
        有一个工厂的实例方法
        <code>
            newInstance()
        </code>
        ，但却没有任何的构造器。
    </p>
    <p>
        为何要有一个工厂方法而不是构造器？
    </p>
    <p>
        首先，由于你并没有定义任何的构造器，编译器就会自动生成一个空的，无参的默认构造器。这就是你需要有的构造器了，无需其它。
    </p>
    <p>
        第二，你可能知道，当app进入后台的时候，Android会销毁并重新创建Activity及其所属的fragment。当activity再生的时候，它的
        <code>
            FragmentManager
        </code>
        就会使用默认的空构造器来重建fragment。如果无法找到，就会抛出一个异常。
    </p>
    <p>
        因此，最后的实践就是永远都不要指定非空的构造器，实际上，最简单的做法就是你刚刚做的这样，不要指定构造器。
    </p>
    <p>
        稍等，如果你需要将信息或数据传递给Fragment，该怎么做？跟上，你马上就将得到答案。
    </p>
    <h2>
        添加Fragment
    </h2>
    <p>
        添加你漂亮的fragment的最简单的办法，就是将它添加到XML的布局文件上。
    </p>
    <p>
        打开
        <em>
            activity_main.xml
        </em>
        ，选择Text tab，并添加下列的内容到根
        <em>
            FrameLayout
        </em>
        中：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">fragment</span>
  <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/details_fragment"</span>
  <span class="hljs-attr">class</span>=<span class="hljs-string">"com.raywenderlich.alltherages.RageComicDetailsFragment"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>/&gt;</span>
</pre>
    <p>
        这里在activity布局的内部放置了一个
        <code>
            &lt;fragment&gt;
        </code>
        ，并指定了fragment的类型。
        <code>
            class
        </code>
        这个属性需要完整。
        <code>
            &lt;fragment&gt;
        </code>
        的view ID是
        <code>
            FragmentManager
        </code>
        所需求的。
    </p>
    <p>
        运行项目，你就可以看到fragment了：
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
        动态地添加Fragment
    </h3>
    <p>
        首先，再次打开
        <em>
            activity_main.xml
        </em>
        并移除你刚放置的
        <code>
            &lt;fragment&gt;
        </code>
        。（是的，我知道你刚刚把它放到的这里 - 对不起。）你将使用暴走漫画的列表来替换它。
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
        打开
        <em>
            RageComicListFragment.java
        </em>
        ，它包含了所有可爱的列表代码。你可以看到
        <code>
            RageComicListFragment
        </code>
        没有显式的构造器，只有一个
        <code>
            newInstance()
        </code>
        。
    </p>
    <p>
        <code>
            RageComicListFragment
        </code>
        中的列表代码需要依赖于一些资源。你必须确保这个fragment对
        <code>
            Context
        </code>
        包含有效的引用。这就是
        <code>
            onAttach()
        </code>
        应该发挥作用的地方了。
    </p>
    <p>
        打开
        <em>
            RageComicListFragment.kt
        </em>
        ，并添加下列的import到已有import的下方：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.os.Bundle
<span class="hljs-keyword">import</span> android.support.v7.widget.GridLayoutManager
</pre>
    <p>
        <code>
            GridLayoutManager
        </code>
        ，用来在暴走漫画的列表中放置item。其它的import则是标准的fragment覆盖。
    </p>
    <p>
        在
        <em>
            RageComicListFragment.kt
        </em>
        中，添加下列的两个方法，就在
        <code>
            RageComicAdapter
        </code>
        定义的上方：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onAttach</span><span class="hljs-params">(context: <span class="hljs-type">Context</span>?)</span></span> {
    <span class="hljs-keyword">super</span>.onAttach(context)
    <span class="hljs-comment">// Get rage face names and descriptions.</span>
    <span class="hljs-keyword">val</span> resources = context!!.resources
    names = resources.getStringArray(R.array.names)
    descriptions = resources.getStringArray(R.array.descriptions)
    urls = resources.getStringArray(R.array.urls)
    <span class="hljs-comment">// Get rage face images.</span>
    <span class="hljs-keyword">val</span> typedArray = resources.obtainTypedArray(R.array.images)
    <span class="hljs-keyword">val</span> imageCount = names.size
    imageResIds = IntArray(imageCount)
    <span class="hljs-keyword">for</span> (i <span class="hljs-keyword">in</span> <span class="hljs-number">0.</span>.imageCount - <span class="hljs-number">1</span>) {
      imageResIds[i] = typedArray.getResourceId(i, <span class="hljs-number">0</span>)
    }
    typedArray.recycle()
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateView</span><span class="hljs-params">(inflater: <span class="hljs-type">LayoutInflater</span>?, container: <span class="hljs-type">ViewGroup</span>?,
                            savedInstanceState: <span class="hljs-type">Bundle</span>?)</span></span>: View? {
    <span class="hljs-keyword">val</span> view: View = inflater!!.inflate(R.layout.fragment_rage_comic_list, container,
        <span class="hljs-literal">false</span>)
    <span class="hljs-keyword">val</span> activity = activity
    <span class="hljs-keyword">val</span> recyclerView = view.findViewById&lt;RecyclerView&gt;(R.id.recycler_view) <span class="hljs-keyword">as</span> RecyclerView
    recyclerView.layoutManager = GridLayoutManager(activity, <span class="hljs-number">2</span>)
    recyclerView.adapter = RageComicAdapter(activity)
    <span class="hljs-keyword">return</span> view
  }
</pre>
    <p>
        <code>
            onAttach()
        </code>
        中，访问了你需要通过
        <code>
            Context
        </code>
        来访问的资源。由于代码位于
        <code>
            onAttach()
        </code>
        中，你无需判断fragment是否包含一个有效的
        <code>
            Context
        </code>
        。
    </p>
    <p>
        在
        <code>
            onCreateView()
        </code>
        中，你填充了
        <code>
            RageComicListFragment
        </code>
        的view的层级，它包含了一个
        <code>
            RecyclerView
        </code>
        ，并执行了一些设置。
    </p>
    <p>
        通常，如果你需要在fragment的view上进行一些处理，
        <code>
            onCreateView()
        </code>
        就是一个很好的地方，因为这里已经能确定你的view准备好了。
    </p>
    <p>
        接下来，打开
        <em>
            MainActivity.kt
        </em>
        并使用下列的代码替换
        <code>
            onCreate()
        </code>
        方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"> <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(savedInstanceState: <span class="hljs-type">Bundle</span>?)</span></span> {
    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState)
    setContentView(R.layout.activity_main)
    <span class="hljs-keyword">if</span> (savedInstanceState == <span class="hljs-literal">null</span>) {
      supportFragmentManager
              .beginTransaction()
              .add(R.id.root_layout, RageComicListFragment.newInstance(), <span class="hljs-string">"rageComicList"</span>)
              .commit()
    }
  }
</pre>
    <p>
        这里你将
        <code>
            RageComicListFragment
        </code>
        放置到
        <code>
            MainActivity
        </code>
        中。你会请求你的新朋友
        <code>
            FragmentManager
        </code>
        来添加它。
    </p>
    <p>
        首先，你通过
        <code>
            supportFragmentManager
        </code>
        而非
        <code>
            fragmentManager
        </code>
        得到了
        <code>
            FragmentManager
        </code>
        ，因为你使用的是支持框架。
    </p>
    <p>
        然后通过调用
        <code>
            beginTransaction()
        </code>
        来请求
        <code>
            FragmentManager
        </code>
        开启一个新的事务 - 你应该可以单靠自己搞懂了。然后调用
        <code>
            add
        </code>
        来指定你想要的添加操作，并传递参数：
    </p>
    <ul>
        <li>
            用来在activity的布局中，容纳fragment的view层级的container的view ID。如果你偷偷看一眼
            <code>
                activity_main.xml
            </code>
            ，你就会发现
            <code>
                @+id/root_layout
            </code>
            。
        </li>
        <li>
            待添加的fragment的实例。
        </li>
        <li>
            一个字符串，用来充当fragment实例的tag/identifier。这样便于
            <code>
                FragmentManager
            </code>
            在稍后检索fragment。
        </li>
    </ul>
    <p>
        最后，你通过调用
        <code>
            commit()
        </code>
        来请求
        <code>
            FragmentManager
        </code>
        执行事务。
    </p>
    <p>
        这样，fragment就被添加上了！
    </p>
    <p>
        运行项目，你就会看到充满暴走漫画的列表：
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
        通过
        <code>
            FragmentTransactions
        </code>
        实现功能，它们是fragment基本的操作，如添加，删除等等。
    </p>
    <p>
        在上述的代码中，
        <code>
            if
        </code>
        语句包含了展示fragment的代码，并判断activity尚无保存的状态。当activity被保存的时候，相应它所有fragment也会被保存。如果你不执行这这检查，就会发生这样的情况：
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
        你就会：
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
        课程：牢记保存的状态会如何影响你的fragment。
    </p>
    <h2>
        数据绑定
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
            <pre lang="groovy" class="language-groovy">dataBinding {
  enabled = true
}
</pre>
        </li>
        <li>
            A data section in the
            <code>
                recycler_item_rage_comic.xml
            </code>
            layout file.
            <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">layout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">data</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">variable</span>
      <span class="hljs-attr">name</span>=<span class="hljs-string">"comic"</span>
      <span class="hljs-attr">type</span>=<span class="hljs-string">"com.raywenderlich.alltherages.Comic"</span> /&gt;</span>
 <span class="hljs-tag">&lt;/<span class="hljs-name">data</span>&gt;</span>

  ...
<span class="hljs-tag">&lt;/<span class="hljs-name">layout</span>&gt;</span>
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
    <pre lang="kotlin" class="language-kotlin hljs">programmer.name = <span class="hljs-string">"a purr programmer"</span>
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
    <pre lang="xml" class="language-xml hljs">tools:text="@{comic.name}" 
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateViewHolder</span><span class="hljs-params">(viewGroup: <span class="hljs-type">ViewGroup</span>, viewType: <span class="hljs-type">Int</span>)</span></span>: ViewHolder {
  <span class="hljs-comment">//1</span>
  <span class="hljs-keyword">val</span> recyclerItemRageComicBinding = RecyclerItemRageComicBinding.inflate(layoutInflater,
    viewGroup, <span class="hljs-literal">false</span>)
  <span class="hljs-comment">//2</span>
  <span class="hljs-keyword">val</span> comic = Comic(imageRmesIds[position], names[position], descriptions[position],
    urls[position])
  recyclerItemRageComicBinding.comic = comic
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
        与Activity进行通信
    </h2>
    <p>
        即使fragment被附加到了一个activity上，如果没有进一步的“鼓励”，它们就不一定要彼此交流。
    </p>
    <p>
        对于所有的暴走漫画，你需要
        <code>
            RageComicListFragment
        </code>
        可以让
        <code>
            MainActivity
        </code>
        知道什么时候用户已作出了选择，这样
        <code>
            RageComicDetailsFragment
        </code>
        才可以将选择展示出来。
    </p>
    <p>
        开始，打开
        <em>
            RageComicListFragment.kt
        </em>
        并添加下列的Java interface到文件的底部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">OnRageComicSelected</span> </span>{
  <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onRageComicSelected</span><span class="hljs-params">(comic: <span class="hljs-type">Comic</span>)</span></span>
}
</pre>
    <p>
        这就为activity定义了一个监听者的interface来监听fragment。activity将实现这个interface，而fragment就会在一项被选中时，调用
        <code>
            onRageComicSelected()
        </code>
        ，将选择传递给activity。
    </p>
    <p>
        在
        <code>
            RageComicListFragment
        </code>
        中，现有的字段下添加一个新的字段：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> listener: OnRageComicSelected
</pre>
    <p>
        这个字段会引用fragment的监听者，也就是activity。
    </p>
    <p>
        在
        <code>
            onAttach()
        </code>
        方法中，
        <code>
            super.onAttach(context);
        </code>
        之下，添加下列代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">if</span> (context <span class="hljs-keyword">is</span> OnRageComicSelected) {
  listener = context
} <span class="hljs-keyword">else</span> {
  <span class="hljs-keyword">throw</span> ClassCastException(context.toString() + <span class="hljs-string">" must implement OnRageComicSelected."</span>)
}
</pre>
    <p>
        这里初始化了监听者的引用。在
        <code>
            onAttach()
        </code>
        中执行，可以确保fragment确实被附加到了activity上。然后你通过
        <code>
            instanceof
        </code>
        来验证相应的activity实现了
        <code>
            OnRageComicSelected
        </code>
        interface。
    </p>
    <p>
        如果判断失败，就抛出一个异常，因为你已无法继续下去了。反之，则将activity设置为
        <code>
            RageComicListFragment
        </code>
        的
        <code>
            listener
        </code>
        。
    </p>
    <p>
        在
        <code>
            onBindViewHolder()
        </code>
        方法中，添加下列的代码到它的底部 -- ok，我撒了一点小谎：
        <code>
            RageComicAdapter
        </code>
        并没有包含你所需的
        <i>
            所有内容
        </i>
        !)
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">viewHolder.itemView.setOnClickListener { listener.onRageComicSelected(comic) }
</pre>
    <p>
        这就添加了一个
        <code>
            View.OnClickListener
        </code>
        到每个暴走漫画上，以便它在listener（activity）上调用回调方法，来传递选择。
    </p>
    <p>
        打开
        <em>
            MainActivity.java
        </em>
        并将类定义更新为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> : <span class="hljs-type">AppCompatActivity</span></span>(), RageComicListFragment.OnRageComicSelected {
</pre>
    <p>
        这里会报出一个错误，让你将
        <code>
            MainActivity
        </code>
        设为abstract的，或实现abstract的方法
        <code>
            OnRageComicSelected(int, String, String, String)
        </code>
        。不要纠结这里，很快你就会解决它。
    </p>
    <p>
        此代码指定了
        <code>
            MainActivity
        </code>
        会作为
        <code>
            OnRageComicSelected
        </code>
        interface的一个实现。
    </p>
    <p>
        现在，你将展示一个toast来验证代码是否可以正常地工作。添加下列的import到已有的import下面：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.widget.Toast
</pre>
    <p>
        然后在
        <code>
            onCreate()
        </code>
        方法之后，添加下列的方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onRageComicSelected</span><span class="hljs-params">(comic: <span class="hljs-type">Comic</span>)</span></span> {
  Toast.makeText(<span class="hljs-keyword">this</span>, <span class="hljs-string">"Hey, you selected "</span> + comic.name + <span class="hljs-string">"!"</span>,
      Toast.LENGTH_SHORT).show()
}
</pre>
    <p>
        现在错误就消失了！运行项目，然后点击任一个暴走漫画，你就会看到一个被点击项目的toast消息：
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
        你已经让activity和它的fragment进行沟通了。你就像是一个数字外交官！
    </p>
    <h2>
        Fragment参数和事务
    </h2>
    <p>
        当前，
        <code>
            RageComicDetailsFragment
        </code>
        展示了一个静态的
        <code>
            Drawable
        </code>
        和
        <code>
            Strings
        </code>
        的集合，但你还想展示用户的选择。
    </p>
    <p>
        首先，将在
        <code>
            fragment_rage_comic_details.xml
        </code>
        中全部的view替换为：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">layout</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">data</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">variable</span>
            <span class="hljs-attr">name</span>=<span class="hljs-string">"comic"</span>
            <span class="hljs-attr">type</span>=<span class="hljs-string">"com.raywenderlich.alltherages.Comic"</span> /&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">data</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">ScrollView</span> <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
        <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
        <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
        <span class="hljs-attr">android:fillViewport</span>=<span class="hljs-string">"true"</span>
        <span class="hljs-attr">tools:ignore</span>=<span class="hljs-string">"RtlHardcoded"</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">LinearLayout</span>
            <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
            <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
            <span class="hljs-attr">android:gravity</span>=<span class="hljs-string">"center"</span>
            <span class="hljs-attr">android:orientation</span>=<span class="hljs-string">"vertical"</span>&gt;</span>
            <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
                <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/name"</span>
                <span class="hljs-attr">style</span>=<span class="hljs-string">"@style/TextAppearance.AppCompat.Title"</span>
                <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
                <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
                <span class="hljs-attr">android:layout_marginBottom</span>=<span class="hljs-string">"0dp"</span>
                <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"@dimen/rage_comic_name_margin_top"</span>
                <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@{comic.name}"</span> /&gt;</span>
            <span class="hljs-tag">&lt;<span class="hljs-name">ImageView</span>
                <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/comic_image"</span>
                <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
                <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"@dimen/rage_comic_image_size"</span>
                <span class="hljs-attr">android:layout_marginBottom</span>=<span class="hljs-string">"@dimen/rage_comic_image_margin_vertical"</span>
                <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"@dimen/rage_comic_image_margin_vertical"</span>
                <span class="hljs-attr">android:adjustViewBounds</span>=<span class="hljs-string">"true"</span>
                <span class="hljs-attr">android:contentDescription</span>=<span class="hljs-string">"@null"</span>
                <span class="hljs-attr">android:scaleType</span>=<span class="hljs-string">"centerCrop"</span>
                <span class="hljs-attr">imageResource</span>=<span class="hljs-string">"@{comic.imageResId}"</span> /&gt;</span>
            <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
                <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/description"</span>
                <span class="hljs-attr">style</span>=<span class="hljs-string">"@style/TextAppearance.AppCompat.Body1"</span>
                <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
                <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
                <span class="hljs-attr">android:layout_marginBottom</span>=<span class="hljs-string">"@dimen/rage_comic_description_margin_bottom"</span>
                <span class="hljs-attr">android:layout_marginLeft</span>=<span class="hljs-string">"@dimen/rage_comic_description_margin_left"</span>
                <span class="hljs-attr">android:layout_marginRight</span>=<span class="hljs-string">"@dimen/rage_comic_description_margin_right"</span>
                <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"0dp"</span>
                <span class="hljs-attr">android:autoLink</span>=<span class="hljs-string">"web"</span>
                <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@{comic.text}"</span> /&gt;</span>
        <span class="hljs-tag">&lt;/<span class="hljs-name">LinearLayout</span>&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">ScrollView</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">layout</span>&gt;</span>
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
    <pre lang="xml" class="language-xml hljs">imageResource="@{comic.imageResId}"
</pre>
    <p>
        This corresponds to a binding adapter that we’ve created in the
        <code>
            DataBindingAdapters.kt
        </code>
        file.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-meta">@BindingAdapter(<span class="hljs-meta-string">"android:src"</span>)</span>
  <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setImageResoruce</span><span class="hljs-params">(imageView: <span class="hljs-type">ImageView</span>, resource: <span class="hljs-type">Int</span>)</span></span> {
    imageView.setImageResource(resource)
  }
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> java.io.Serializable
</pre>
    <p>
        Replace
        <code>
            newInstance()
        </code>
        with the code shown below:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> const <span class="hljs-keyword">val</span> COMIC = <span class="hljs-string">"comic"</span>

<span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">newInstance</span><span class="hljs-params">(comic: <span class="hljs-type">Comic</span>)</span></span>: RageComicDetailsFragment {
  <span class="hljs-keyword">val</span> args = Bundle()
  args.putSerializable(COMIC, comic <span class="hljs-keyword">as</span> Serializable)
  <span class="hljs-keyword">val</span> fragment = RageComicDetailsFragment()
  fragment.arguments = args
  <span class="hljs-keyword">return</span> fragment
}
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> com.raywenderlich.alltherages.databinding.FragmentRageComicDetailsBinding
</pre>
    <p>
        Now, replace the contents of
        <em>
            onCreateView()
        </em>
        with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> fragmentRageComicDetailsBinding = FragmentRageComicDetailsBinding.inflate(inflater!!,
    container, <span class="hljs-literal">false</span>)

<span class="hljs-keyword">val</span> comic = arguments.getSerializable(COMIC) <span class="hljs-keyword">as</span> Comic
fragmentRageComicDetailsBinding.comic = comic
comic.text = String.format(getString(R.string.description_format), comic.description, comic.url)
<span class="hljs-keyword">return</span> fragmentRageComicDetailsBinding.root
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> detailsFragment =
    RageComicDetailsFragment.newInstance(comic)
supportFragmentManager.beginTransaction()
    .replace(R.id.root_layout, detailsFragment, <span class="hljs-string">"rageComicDetails"</span>)
    .addToBackStack(<span class="hljs-literal">null</span>)
    .commit()
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