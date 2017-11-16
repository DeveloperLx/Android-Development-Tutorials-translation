# Android动画教程 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/173345/android-animation-tutorial-with-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <em>
            更新日志
        </em>
        ：本教程已由Rod Biresch更新至Kotlin及Android Studio 3.0的版本。原教材由Artem Kholodnyi编写。
    </div>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-250x250.png"
        alt="Android animation" width="250" height="250" class="alignright size-thumbnail wp-image-141919"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-128x128.png 128w"
        sizes="(max-width: 250px) 100vw, 250px">
    </p>
    <p>
        很难想象没有动画元素的移动体验 - 它们漂亮，有趣，不仅可以引导用户优雅地使用app，还可以让屏幕变得生动起来。
    </p>
    <p>
        构建动画使屏幕生动起来，开始听着像是一个航天工程，但是不要害怕！Android中有很多工具可以帮助你相对容易地创建动画。
    </p>
    <p>
        你将在本教程中学习如何使用一些基本的动画工具，来将一个火箭中的Doge发射到太空中（甚至是月球上），然后安全返回到地面上:]
    </p>
    <p>
        通过创建这些Doge的动画，你会学到如何：
    </p>
    <ul>
        <li>
            创建
            <em>
                property animations
            </em>
            — 它是最常用最简单的Android动画
        </li>
        <li>
            移动和隐藏Android的View
        </li>
        <li>
            把动画连接成一个序列，或同时启动它们
        </li>
        <li>
            重复和倒转动画
        </li>
        <li>
            调整动画的时间效果
        </li>
        <li>
            变成一个火箭科学家。:]
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                预备知识：
            </em>
            ：本教程是完全关于动画的，因此你需要Android编程的基本知识，并且熟悉Kotlin，Android Studio和XML layouts。
        </p>
        <p>
            如果你是一个Android的纯小白，请首先阅读
            <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Beginning%20Android%20Development%20Part%20One%20Installing%20Android%20Studio.md"
            target="_blank" title="Android Tutorial for Beginners: Part 1">
                开始Android开发 第一部分
            </a>
            .
        </p>
    </div>
    <p>
        很多的动画。这样的代码。快速的火箭。
    </p>
    <h2>
        入门
    </h2>
    <p>
        动画是非常有趣的话题！掌握构建动画的最佳方式就是在实践中进行探索。:]
    </p>
    <p>
        首先，下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/10/rocket_launcher-starter-1.zip">
            初始项目
        </a>
        。将它导入到Android Studio 3.0 Beta 7或更高的版本上，然后在你的设备上运行。它已经为你的开发准备好了必要的资源。
    </p>
    <p>
        你的设备上会展示出一个你将要实现的动画的列表。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/list.png"
        alt="list" width="300" height="500" class="aligncenter size-full wp-image-128166"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/03/list.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/03/list-192x320.png 192w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <p>
        点击列表中的任意一项。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket-281x500.png"
        alt="doge_rocket" width="281" height="500" class="aligncenter size-large wp-image-136020"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        你会看到两张静态的图片：Doge和火箭，Doge已准备好搭乘。当期所有的页面都是相同的，没有任何动画。
    </p>
    <h2>
        如何让属性动画work起来？
    </h2>
    <p>
        在开始处理第一个动画之前，让我们先走一轮理论，了解一下动画魔法背后的逻辑。:]
    </p>
    <p>
        想象一下，把一个火箭从屏幕的底部发射到顶部，在50毫秒的时间内完成这个过程。
    </p>
    <p>
        下面的图展示了火箭的位置如何跟随时间进行变化：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/linear-interpolator.gif"
        alt="linear-interpolator" width="272" height="400" class="aligncenter size-full wp-image-128117">
    </p>
    <p>
        上面的动画是平滑且连续的，然而，智能手机是数字的，只能处理离散的值，时间对它来说并不是连续地变化，而是分散成了微小的步。
    </p>
    <p>
        动画是由很多静止的图片构成的，它们被称作
        <em>
            帧
        </em>
        ，在指定的时间段内逐一进行展示，就构成了动画。这个概念和最原始的动漫是一致的，但是渲染有一定的不同。
    </p>
    <p>
        帧之间经过的时间被称作
        <em>
            帧刷新延迟
        </em>
        - 对于属性动画，它的默认值就是10毫秒。
    </p>
    <p>
        这里的动画和早先电影的不同之处在于：当你知道火箭在以一个固定的速度移动时，你可以在任何时刻计算火箭的位置。
    </p>
    <p>
        你可以在下面看到6个动画的帧。注意：
    </p>
    <ul>
        <li>
            在动画开始时，火箭位于屏幕的底部。
        </li>
        <li>
            之间的每一帧火箭都向上移动了相同的距离。
        </li>
        <li>
            在动画结束时，火箭位于屏幕的顶部。
        </li>
    </ul>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/frames.png"
        alt="frames" width="405" height="405" class="aligncenter size-full wp-image-134485"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/05/frames.png 405w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-128x128.png 128w"
        sizes="(max-width: 405px) 100vw, 405px">
    </p>
    <p>
        TL/DR：当需要绘制一个帧的时候，会基于相应的时间和帧刷新率来计算火箭的位置。
    </p>
    <p>
        幸运的是，你无需手动进行所有的计算，因为
        <code>
            ValueAnimator
        </code>
        将乐于为你完成所有的工作。:]
    </p>
    <p>
        要设置一个动画，你只需指定需添加动画的属性的起始值和结束值。你还可以添加一个listener来进行监听，它可以在每一帧为你的火箭设置一个新的位置。
    </p>
    <h3>
        时间插值器
    </h3>
    <p>
        你可能已注意到了，火箭在整个的动画过程中，都是以一个固定的速度进行移动的 - 这是非常不现实的。
        <a href="https://material.io/">
            Material Design
        </a>
        鼓励你创建生动的动画，以更自然的方式来吸引用户的注意力。
    </p>
    <p>
        Android的动画框架充分地利用了
        <em>
            时间插值器
        </em>
        。
        <code>
            ValueAnimator
        </code>
        合并了一个时间插值器 - 它是一个实现了
        <code>
            TimeInterpolator
        </code>
        interface的对象。时间插值器确定了动画的值如何跟随时间进行变化。
    </p>
    <p>
        再看一下这个最简单的情形，图形的位置跟随时间发生变化 - 这是一个
        <em>
            线性插值器
        </em>
        ：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/linear-interpolator.gif"
        alt="linear-interpolator" width="272" height="400" class="aligncenter size-full wp-image-128117">
    </p>
    <p>
        <code>
            LinearInterpolator
        </code>
        会这样地相应时间的变化：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/table_linear.png"
        alt="table_linear" width="175" height="250" class="aligncenter size-full wp-image-134326">
    </p>
    <p>
        基于时间，火箭的位置会以固定的速度或
        <i>
            线性地
        </i>
        发生变化。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/accelerate-interpolator.gif"
        alt="AccelerateInterpolator" width="273" height="400" class="aligncenter size-full wp-image-128128">
    </p>
    <p>
        Android同样拥有非线性的插值器。
        <code>
            AccelerateInterpolator
        </code>
        就是一个例子，它看起来更加得有趣：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/table_acc.png"
        alt="table_acc" width="175" height="316" class="aligncenter size-full wp-image-134327">
    </p>
    <p>
        它将输入的值进行平方，使火箭缓慢地开始并逐渐加速 - 就像真正的火箭一样！
    </p>
    <p>
        这基本就是你入门所需要知道的全部理论了，现在是时候开始实践操作了...
    </p>
    <h2>
        你的第一个动画
    </h2>
    <p>
        在继续下一步之前，花一些时间来熟悉项目。
        <code>
            com.raywenderlich.rocketlauncher.animationactivities
        </code>
        这个包包含了
        <em>
            BaseAnimationActivity
        </em>
        和其它继承自这个类的activity。
    </p>
    <p>
        在
        <em>
            res/layout
        </em>
        目录中打开
        <em>
            activity_base_animation.xml
        </em>
        这个文件。
    </p>
    <p>
        在根元素中，你会发现一个
        <code>
            FrameLayout
        </code>
        ，带有两个含有图片的
        <code>
            ImageView
        </code>
        的实例：一个图片为
        <em>
            rocket.png
        </em>
        ，另一个则为
        <em>
            doge.png
        </em>
        。两个ImageView的
        <code>
            android:layout_gravity
        </code>
        的值均被设置为
        <code>
            bottom|center_horizontal
        </code>
        ，以便将图片绘制在屏幕底部的中央。
    </p>
    <div class="note">
        <p>
            <em>
                注意
                Note
            </em>
            ：在本教程中，你会经常进行文件之间的切换。在Android Studio中使用下列的快捷键可以让这项工作变得更轻松：
        </p>
        <ul>
            <li>
                <p>
                    在Mac上使用
                    <em>
                        command + shift + O
                    </em>
                    ，或在Linux和Windows上使用
                    <em>
                        Ctrl + Shift + N
                    </em>
                    快捷键可以切换到任一文件中
                </p>
            </li>
            <li>
                <p>
                    在Mac上使用
                    <em>
                        command + O
                    </em>
                    ，或在Linux和Windows上使用
                    <em>
                        Ctrl + N
                    </em>
                    快捷键可以切换Kotlin的类中
                </p>
            </li>
        </ul>
    </div>
    <p>
        在本app中，
        <code>
            BaseAnimationActivity
        </code>
        是其它所有动画activity的超类。
    </p>
    <p>
        打开
        <em>
            BaseAnimationActivity.kt
        </em>
        并查看其中的代码。顶部是
        <code>
            View
        </code>
        成员变量，可以被所有的动画activity访问：
    </p>
    <ul>
        <li>
            <code>
                rocket
            </code>
            是带有火箭的图片的view
        </li>
        <li>
            <code>
                doge
            </code>
            是带有Doge的图片的view
        </li>
        <li>
            <code>
                frameLayout
            </code>
            是包含
            <code>
                rocket
            </code>
            和
            <code>
                doge
            </code>
            的FrameLayout
        </li>
        <li>
            <code>
                screenHeight
            </code>
            等于屏幕的高度，为方便使用而设立
        </li>
    </ul>
    <p>
        注意
        <code>
            rocket
        </code>
        和
        <code>
            doge
        </code>
        都是同一类型的
        <code>
            ImageView
        </code>
        ，但将它们都声明为
        <code>
            View
        </code>
        是因为属性动画可以用在所有的Android View上。这些view还被声明成了
        <code>
            lateinit
        </code>
        的值，因为它们开始都是空的，直到在合适的生命周期方法（如Activity的
        <code>
            onCreate()
        </code>
        中）被添加和绑定后，才会得到值。
    </p>
    <p>
        观察
        <code>
            onCreate()
        </code>
        的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">super</span>.onCreate(savedInstanceState)
setContentView(R.layout.activity_base_animation)

<span class="hljs-comment">// 2</span>
rocket = findViewById(R.id.rocket)
doge = findViewById(R.id.doge)
frameLayout = findViewById(R.id.container)

<span class="hljs-comment">// 3</span>
frameLayout.setOnClickListener { onStartAnimation() }
</pre>
    <p>
        上述代码：
    </p>
    <ol>
        <li>
            调用父类的
            <code>
                onCreate()
            </code>
            ，然后用布局文件调用
            <code>
                setContentView(...)
            </code>
            进行绘制。
        </li>
        <li>
            请求XML布局并绑定
            <code>
                FrameLayout
            </code>
            ，
            <code>
                rocket
            </code>
            和
            <code>
                doge
            </code>
            到它们相应的view上
        </li>
        <li>
            为
            <code>
                FrameLayout
            </code>
            设置
            <code>
                onClickListener
            </code>
            。
        </li>
        <li>
            每次点击屏幕的时候，就调用
            <code>
                onStartAnimation()
            </code>
            。它是一个抽象方法，需要在每个继承自
            <code>
                BaseAnimationActivity
            </code>
            的activity中实现。
        </li>
    </ol>
    <p>
        这些代码将被本教程中所有你需要编辑的Activity共享。熟悉之后，就开始进行定制吧！
    </p>
    <h3>
        发射火箭
    </h3>
    <p>
        不发射火箭，Doge哪里都去不了。这是一个入门最好的动画，因为它相当得容易。谁能想到火箭科学如此得简单？
    </p>
    <p>
        打开
        <em>
            LaunchRocketValueAnimatorAnimationActivity.kt
        </em>
        ，并添加下列的代码到
        <code>
            onStartAnimation()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">//1</span>
<span class="hljs-keyword">val</span> valueAnimator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, -screenHeight)

<span class="hljs-comment">//2</span>
valueAnimator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  rocket.translationY = value
}

<span class="hljs-comment">//5</span>
valueAnimator.interpolator = LinearInterpolator()
valueAnimator.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION

<span class="hljs-comment">//6</span>
valueAnimator.start()
</pre>
    <ol>
        <li>
            通过调用静态方法
            <code>
                ofFloat
            </code>
            ，来创建一个
            <code>
                ValueAnimator
            </code>
            的实例，需要被添加动画属性的起始值作为它的参数。在本例中，分别为
            <code>
                0f
            </code>
            和
            <code>
                -screenHeight
            </code>
            。Android屏幕坐标系的原点位于屏幕的左上角，因此火箭的Y坐标是从0变化到负的屏幕的高度 - 这样她就会从底部移动到顶部。
        </li>
        <li>
            调用
            <code>
                addUpdateListener()
            </code>
            方法，并传递一个listener。
            <code>
                ValueAnimator
            </code>
            在更新动画值时，都会调用这个listener - 记住默认的延迟为10毫秒。
        </li>
        <li>
            获取当前的动画值，并将其转化为float类型的值 - 因为你是用
            <code>
                ofFloat
            </code>
            方法创建的
            <code>
                ValueAnimator
            </code>
            。
        </li>
        <li>
            通过设置
            <code>
                translationY
            </code>
            值来改变火箭的位置
        </li>
        <li>
            设置动画的持续时间和插值器。
        </li>
        <li>
            开始动画。
        </li>
    </ol>
    <p>
        运行项目。选择列表中的
        <em>
            Launch a Rocket
        </em>
        。你会进入一个新的页面。点击它！
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/linear-launch.gif"
        alt="linear-launch" width="272" height="484" class="aligncenter size-full wp-image-134552">
    </p>
    <p>
        是不是很有趣？:] 不要担心Doge被丢在了后面 - 稍候它就会赶上飞船。
    </p>
    <h3>
        旋转
    </h3>
    <p>
        如何为火箭添加一个旋转的动作？打开
        <em>
            RotateRocketAnimationActivity.kt
        </em>
        并添加下列的代码到
        <code>
            onStartAnimation()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">val</span> valueAnimator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, <span class="hljs-number">360</span>f)

valueAnimator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  <span class="hljs-comment">// 2</span>
  rocket.rotation = value
}

valueAnimator.interpolator = LinearInterpolator()
valueAnimator.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
valueAnimator.start()
</pre>
    <p>
        发现区别了么？
    </p>
    <ol>
        <li>
            将
            <code>
                valueAnimator
            </code>
            的值修改为从
            <code>
                0f
            </code>
            到
            <code>
                360f
            </code>
            ，使火箭旋转一周。注意你还可以将值改为从
            <code>
                0f
            </code>
            到
            <code>
                180f
            </code>
            来创建一个U型旋转的效果。
        </li>
        <li>
            将设置
            <code>
                translationY
            </code>
            修改为设置
            <code>
                rotation
            </code>
            ，它是需要进行改变的属性。
        </li>
    </ol>
    <p>
        运行项目，选择
        <em>
            Spin a rocket
        </em>
        。点击新出现的页面：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/spin.gif"
        alt="" width="283" height="500" class="aligncenter size-large wp-image-173336">
    </p>
    <h3>
        加速启动
    </h3>
    <p>
        打开
        <em>
            AccelerateRocketAnimationActivity.kt
        </em>
        ，并添加下列的代码到你的老朋友
        <code>
            onStartAnimation()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">val</span> valueAnimator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, -screenHeight)
valueAnimator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  rocket.translationY = value
}

<span class="hljs-comment">// 2 - Here set your favorite interpolator</span>
valueAnimator.interpolator = AccelerateInterpolator(<span class="hljs-number">1.5</span>f)
valueAnimator.duration = BaseAnimationActivity.DEFAULT_ANIMATION_DURATION

<span class="hljs-comment">// 3</span>
valueAnimator.start()
</pre>
    <p>
        上述代码和
        <em>
            LaunchRocketValueAnimationActivity.kt
        </em>
        中的
        <code>
            onStartAnimation()
        </code>
        只有一行不同：插值器发生了变化。
    </p>
    <p>
        运行项目，选择列表中的
        <em>
            Accelerate a rocket
        </em>
        。点击出现的页面，观察火箭的变化。
    </p>
    <p>
        同样，可怜的Doge还是没有赶上火箭...可怜的家伙。先搁置一下吧！
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/accelerate.gif"
        alt="accelerate" width="272" height="484" class="aligncenter size-full wp-image-134549">
    </p>
    <p>
        由于使用了
        <code>
            AccelerateInterpolator
        </code>
        ，你可以看到火箭在发射后进行了加速。你可以自己先把玩一下插值器，我承诺会停下来等你 :]
    </p>
    <h2>
        哪些属性可以添加动画？
    </h2>
    <p>
        到目前为止，你只为
        <code>
            View
        </code>
        的位置和旋转添加过动画，但
        <code>
            ValueAnimator
        </code>
        并不关心你对提供的值所进行的操作。
    </p>
    <p>
        你可以为
        <code>
            ValueAnimator
        </code>
        传递下列类型的值来构建动画：
    </p>
    <ul>
        <li>
            <code>
                float
            </code>
            使用
            <code>
                ofFloat
            </code>
            来创建
            <code>
                ValueAnimator
            </code>
            的实例
        </li>
        <li>
            <code>
                int
            </code>
            使用
            <code>
                ofInt
            </code>
            来创建
            <code>
                ValueAnimator
            </code>
            的实例
        </li>
        <li>
            <code>
                ofObject
            </code>
            在
            <code>
                float
            </code>
            和
            <code>
                int
            </code>
            还不够的情况下使用 - 通常用来给颜色添加动画
        </li>
    </ul>
    <p>
        你可以为
        <code>
            View
        </code>
        的任何属性添加动画。例如：
    </p>
    <ul>
        <li>
            <code>
                scaleX
            </code>
            和
            <code>
                scaleY
            </code>
            - 分别在x轴和y轴上对view进行缩放，或同时对两者进行缩放。
        </li>
        <li>
            <code>
                translationX
            </code>
            和
            <code>
                translationY
            </code>
            - 改变view在屏幕上的位置。
        </li>
        <li>
            <code>
                alpha
            </code>
            - 对view的透明度添加动画；
            <code>
                0
            </code>
            代表完全透明，
            <code>
                1
            </code>
            代表完全不透明。
        </li>
        <li>
            <code>
                rotation
            </code>
            - 使view在屏幕上进行旋转；参数使用角度来表示，因此
            <code>
                360
            </code>
            就代表一个完整的顺时针方向旋转。你还可以指定负数的值，例如，
            <code>
                -90
            </code>
            代表了一个反方向直角角度的旋转。
        </li>
        <li>
            <code>
                rotationX
            </code>
            和
            <code>
                rotationY
            </code>
            - 类似于
            <code>
                rotation
            </code>
            ，但却是基于x轴和y轴进行旋转的。这样就实现了3D的旋转。
        </li>
        <li>
            <code>
                backgroundColor
            </code>
            - 让你可以设置颜色。如果是整型的参数，必须设置为
            <code>
                Color.YELLOW
            </code>
            ，
            <code>
                Color.BLUE
            </code>
            这样的Android常量。
        </li>
    </ul>
    <h3>
        ObjectAnimator
    </h3>
    <p>
        <code>
            ObjectAnimator
        </code>
        是
        <code>
            ValueAnimator
        </code>
        的子类。如果你只想对单个对象的单个属性添加动画，
        <code>
            ObjectAnimator
        </code>
        就是你最棒的新朋友。
    </p>
    <p>
        在
        <code>
            ValueAnimator
        </code>
        中，你必须设置listener，并对动画的值做出处理。而
        <code>
            ObjectAnimator
        </code>
        则可以为你自动进行这些处理。:]
    </p>
    <p>
        打开
        <em>
            LaunchRocketObjectAnimatorAnimationActivity.kt
        </em>
        类，并输入下列代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">val</span> objectAnimator = ObjectAnimator.ofFloat(rocket, <span class="hljs-string">"translationY"</span>, <span class="hljs-number">0</span>f, -screenHeight)

<span class="hljs-comment">// 2</span>
objectAnimator.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
objectAnimator.start()
</pre>
    <p>
        上述代码：
    </p>
    <ol>
        <li>
            创建一个
            <code>
                ObjectAnimator
            </code>
            的实例（就像你在
            <code>
                ValueAnimator
            </code>
            中做的一样，除了新增的两个参数）：
            <ul>
                <li>
                    <code>
                        rocket
                    </code>
                    是要进行动画的对象
                </li>
                <li>
                    这个对象必须包含你希望添加动画的属性，也就是这里的
                    <code>
                        “translationY”
                    </code>
                    了。你能够这么做的原因，是
                    <code>
                        rocket
                    </code>
                    是一个
                    <code>
                        View
                    </code>
                    类的实例，它基于Java的类，并带有一个
                    <code>
                        setTranslationY()
                    </code>
                    的setter方法。
                </li>
            </ul>
        </li>
        <li>
            设置动画的持续时间，并开始动画。
        </li>
    </ol>
    <p>
        运行项目。选择列表中的
        <em>
            Launch a rocket (ObjectAnimator)
        </em>
        。点击屏幕。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/linear-launch.gif"
        alt="linear-launch" width="272" height="484" class="aligncenter size-full wp-image-134552">
    </p>
    <p>
        这里火箭的行为和使用
        <code>
            ValueAnimator
        </code>
        的完全一致的，但使用了更少的代码。:]
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：
            <code>
                ObjectAnimator
            </code>
            是带有一定限制的 - 它不可以同时对两个对象添加动画。要实现的话，你必须添加两个
            <code>
                ObjectAnimator
            </code>
            的实例。
        </p>
        <p>
            考虑你的实际需求和代码量，来确定使用
            <code>
                ObjectAnimator
            </code>
            还是
            <code>
                ValueAnimator
            </code>
            。
        </p>
    </div>
    <h3>
        颜色动画
    </h3>
    <p>
        谈到具体的case，还有颜色动画需要去考虑。通过
        <code>
            ofFloat()
        </code>
        和
        <code>
            ofInt()
        </code>
        都无法构建颜色动画的效果。你最好还要使用
        <code>
            ArgbEvaluator
        </code>
        。
    </p>
    <p>
        打开
        <em>
            ColorAnimationActivity.kt
        </em>
        并在
        <code>
            onStartAnimation()
        </code>
        中添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">//1</span>
<span class="hljs-keyword">val</span> objectAnimator = ObjectAnimator.ofObject(
  frameLayout,
  <span class="hljs-string">"backgroundColor"</span>,
  ArgbEvaluator(),
  ContextCompat.getColor(<span class="hljs-keyword">this</span>, R.color.background_from),
  ContextCompat.getColor(<span class="hljs-keyword">this</span>, R.color.background_to)
)

<span class="hljs-comment">// 2</span>
objectAnimator.repeatCount = <span class="hljs-number">1</span>
objectAnimator.repeatMode = ValueAnimator.REVERSE

<span class="hljs-comment">// 3</span>
objectAnimator.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
objectAnimator.start()
</pre>
    <p>
        上述的代码：
    </p>
    <ol>
        <li>
            调用
            <code>
                ObjectAnimator.ofObject()
            </code>
            并传递下列的参数：
            <ul>
                <li>
                    <code>
                        frameLayout
                    </code>
                    - 含有待添加动画的属性的对象
                </li>
                <li>
                    <code>
                        "backgroundColor"
                    </code>
                    - 待添加动画的属性
                </li>
                <li>
                    <code>
                        ArgbEvaluator()
                    </code>
                    - 一个额外的参数，指定如何在两个不同的
                    <em>
                        ARGB
                    </em>
                    （alpha，red，green，blue）颜色值之间进行插值
                </li>
                <li>
                    开始时和结束时的颜色值 - 这里你使用了
                    <code>
                        ComtextCompat.getColor()
                    </code>
                    ，根据在
                    <code>
                        colors.xml
                    </code>
                    中获取的资源id，来生成相应的颜色值
                </li>
            </ul>
        </li>
        <li>
            通过设置objectAnimator
            <code>
                repeatCount
            </code>
            的值指定动画重复的次数，然后设置
            <code>
                repeatMode
            </code>
            来指定动画结束时的行为。后续会有更多关于这方面的内容！
        </li>
        <li>
            设置持续的时间，并启动动画。
        </li>
    </ol>
    <p>
        运行项目。选择
        <em>
            Background color
        </em>
        这个item，并点击屏幕。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/bg-color.gif"
        alt="bg-color" width="272" height="484" class="aligncenter size-full wp-image-134368">
    </p>
    <p>
        太赞了！你已逐渐熟悉了其中的套路。这是一个平滑的背景颜色变化动画 :]
    </p>
    <h2>
        连接动画
    </h2>
    <p>
        为一个view添加动画非常得棒，但到目前为止，你每次只能在一个对象的一个属性上添加动画。动画不应该受到这样的限制。
    </p>
    <p>
        现在是时候把Doge发送到月球上了！:]
    </p>
    <p>
        <code>
            AnimatorSet
        </code>
        让你可以同时或按顺序地播放多个动画。把第一个动画animator传递给
        <code>
            play()
        </code>
        ，它就会返回一个builder。
    </p>
    <p>
        接下来你就可以让这个builder调用下列的方法，它们都是以
        <code>
            Animator
        </code>
        作为参数：
    </p>
    <ul>
        <li>
            <code>
                with()
            </code>
            - 会将传递给它的
            <code>
                Animator
            </code>
            与你在
            <code>
                play()
            </code>
            中指定的动画同时进行播放
        </li>
        <li>
            <code>
                before()
            </code>
            - 在上一动画之前播放
        </li>
        <li>
            <code>
                after()
            </code>
            - 在上一动画之后播放
        </li>
    </ul>
    <p>
        You can create chains of calls such as these.
    </p>
    <p>
        在编辑器中打开
        <em>
            LaunchAndSpinAnimatorSetAnimatorActivity.kt
        </em>
        ，并在
        <code>
            onStartAnimation()
        </code>
        中添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">val</span> positionAnimator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, -screenHeight)

<span class="hljs-comment">// 2</span>
positionAnimator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  rocket.translationY = value
}

<span class="hljs-comment">// 3</span>
<span class="hljs-keyword">val</span> rotationAnimator = ObjectAnimator.ofFloat(rocket, <span class="hljs-string">"rotation"</span>, <span class="hljs-number">0</span>f, <span class="hljs-number">180</span>f)
<span class="hljs-comment">// 4</span>
<span class="hljs-keyword">val</span> animatorSet = AnimatorSet()
<span class="hljs-comment">// 5</span>
animatorSet.play(positionAnimator).with(rotationAnimator)
<span class="hljs-comment">// 6</span>
animatorSet.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
animatorSet.start()
</pre>
    <p>
        Here’s what you’re doing in this block:
    </p>
    <ol>
        <li>
            Create a new
            <code>
                ValueAnimator
            </code>
            .
        </li>
        <li>
            Attach an
            <code>
                AnimatorUpdateListener
            </code>
            to the ValueAnimator that updates the rocket’s position.
        </li>
        <li>
            Create an
            <code>
                ObjectAnimator
            </code>
            , a second animator that updates the rocket’s rotation.
        </li>
        <li>
            Create a new instance of
            <code>
                AnimatorSet
            </code>
            .
        </li>
        <li>
            Specify that you’d like to execute
            <code>
                positionAnimator
            </code>
            together with
            <code>
                rotationAnimator
            </code>
            .
        </li>
        <li>
            Just as with a typical animator, you set a duration and call
            <code>
                start()
            </code>
            .
        </li>
    </ol>
    <p>
        Build and run again. Select the
        <em>
            Launch and spin (AnimatorSet)
        </em>
        . Tap the screen.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/launch-n-spin.gif"
        alt="launch-n-spin" width="272" height="484" class="aligncenter size-full wp-image-134377">
    </p>
    <p>
        Doge defies the laws of physics with this one.
    </p>
    <p>
        There’s a nifty tool to simplify animating several properties of the same
        object. The tool is called…
    </p>
    <h3>
        ViewPropertyAnimator
    </h3>
    <p>
        One of the greatest things about animation code that uses
        <code>
            ViewPropertyAnimator
        </code>
        is that it’s easy to write and read — you’ll see.
    </p>
    <p>
        Open
        <em>
            LaunchAndSpinViewPropertyAnimatorAnimationActivity.kt
        </em>
        and add the following call to
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">rocket.animate()
    .translationY(-screenHeight)
    .rotationBy(<span class="hljs-number">360</span>f)
    .setDuration(BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION)
    .start()
</pre>
    <p>
        In here,
        <code>
            animate()
        </code>
        returns an instance of
        <code>
            ViewPropertyAnimator
        </code>
        so you can chain the calls.
    </p>
    <p>
        Build and run, select
        <em>
            Launch and spin (ViewPropertyAnimator)
        </em>
        , and you’ll see the same animation as in the previous section.
    </p>
    <p>
        Compare your code for this section to the
        <code>
            AnimatorSet
        </code>
        code snippet that you implemented in the previous section:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> positionAnimator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, -screenHeight)

positionAnimator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  rocket?.translationY = value
}

<span class="hljs-keyword">val</span> rotationAnimator = ObjectAnimator.ofFloat(rocket, <span class="hljs-string">"rotation"</span>, <span class="hljs-number">0</span>f, <span class="hljs-number">180</span>f)

<span class="hljs-keyword">val</span> animatorSet = AnimatorSet()
animatorSet.play(positionAnimator).with(rotationAnimator)
animatorSet.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
animatorSet.start()
</pre>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate.png"
        alt="" width="320" height="320" class="aligncenter size-medium wp-image-173339"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-128x128.png 128w"
        sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <p>
        <code>
            ViewPropertyAnimator
        </code>
        may provide better performance for multiple simultaneous animations. It
        optimizes invalidated calls, so they only take place once for several properties
        — in contrast to each animated property causing its own invalidation independently.
    </p>
    <h3>
        Animating the Same Property of Two Objects
    </h3>
    <p>
        A nice feature of
        <code>
            ValueAnimator
        </code>
        is that you can reuse its animated value and apply it to as many objects
        as you like.
    </p>
    <p>
        Test it out by opening
        <em>
            FlyWithDogeAnimationActivity.kt
        </em>
        and putting the following code in
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">//1</span>
<span class="hljs-keyword">val</span> positionAnimator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, -screenHeight)
positionAnimator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  rocket.translationY = value
  doge.translationY = value
}

<span class="hljs-comment">//2</span>
<span class="hljs-keyword">val</span> rotationAnimator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, <span class="hljs-number">360</span>f)
rotationAnimator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  doge.rotation = value
}

<span class="hljs-comment">//3</span>
<span class="hljs-keyword">val</span> animatorSet = AnimatorSet()
animatorSet.play(positionAnimator).with(rotationAnimator)
animatorSet.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
animatorSet.start()
</pre>
    <p>
        In the above code you just created three animators:
    </p>
    <ol>
        <li>
            <code>
                positionAnimator
            </code>
            — for changing positions of both
            <code>
                rocket
            </code>
            and
            <code>
                doge
            </code>
        </li>
        <li>
            <code>
                rotationAnimator
            </code>
            — for rotating Doge
        </li>
        <li>
            <code>
                animatorSet
            </code>
            — to combine the first two animators
        </li>
    </ol>
    <p>
        Notice that you set translation for
        <i>
            two
        </i>
        objects at once in the first animator.
    </p>
    <p>
        Run the app and select
        <em>
            Don’t leave Doge behind (Animating two objects)
        </em>
        . You know what to do now. To the moon!
    </p>
    <h2>
        Animation Listeners
    </h2>
    <p>
        Animation typically implies that a certain action has occurred or will
        take place. Typically, whatever happens usually comes at the end of your
        fancy animation.
    </p>
    <p>
        You don’t get to observe it, but know that the rocket stops and stays
        off screen when the animation ends. If you don’t plan to land it or finish
        the activity, you could remove this particular view to conserve resources.
    </p>
    <p>
        <code>
            AnimatorListener
        </code>
        — receives a notification from the animator when the following events
        occur:
    </p>
    <ul>
        <li>
            <code>
                onAnimationStart()
            </code>
            — called when the animation starts
        </li>
        <li>
            <code>
                onAnimationEnd()
            </code>
            — called when the animation ends
        </li>
        <li>
            <code>
                onAnimationRepeat()
            </code>
            — called if the animation repeats
        </li>
        <li>
            <code>
                onAnimationCancel()
            </code>
            — called if the animation is canceled
        </li>
    </ul>
    <p>
        Open
        <em>
            WithListenerAnimationActivity.kt
        </em>
        and add the following code to
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">//1</span>
<span class="hljs-keyword">val</span> animator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, -screenHeight)

animator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  rocket.translationY = value
  doge.translationY = value
}

<span class="hljs-comment">// 2</span>
animator.addListener(<span class="hljs-keyword">object</span> : Animator.AnimatorListener {
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onAnimationStart</span><span class="hljs-params">(animation: <span class="hljs-type">Animator</span>)</span></span> {
    <span class="hljs-comment">// 3</span>
    Toast.makeText(applicationContext, <span class="hljs-string">"Doge took off"</span>, Toast.LENGTH_SHORT)
        .show()
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onAnimationEnd</span><span class="hljs-params">(animation: <span class="hljs-type">Animator</span>)</span></span> {
    <span class="hljs-comment">// 4</span>
    Toast.makeText(applicationContext, <span class="hljs-string">"Doge is on the moon"</span>, Toast.LENGTH_SHORT)
        .show()
    finish()
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onAnimationCancel</span><span class="hljs-params">(animation: <span class="hljs-type">Animator</span>)</span></span> {}

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onAnimationRepeat</span><span class="hljs-params">(animation: <span class="hljs-type">Animator</span>)</span></span> {}
})

<span class="hljs-comment">// 5</span>
animator.duration = <span class="hljs-number">5000</span>L
animator.start()
</pre>
    <p>
        The structure of the code above, with the exception of the listener part,
        should look the same as the previous section. Here’s what you’re doing
        in there:
    </p>
    <ol>
        <li>
            Create and set up an animator. You use
            <code>
                ValueAnimator
            </code>
            to change the position of two objects simultaneously — you can’t do the
            same thing with a single
            <code>
                ObjectAnimator
            </code>
            .
        </li>
        <li>
            Add the
            <code>
                AnimatorListener
            </code>
            .
        </li>
        <li>
            Show a toast message when the animation starts
        </li>
        <li>
            And another toast when it ends
        </li>
        <li>
            Start the animation as usual
        </li>
    </ol>
    <p>
        Run the app. Select
        <em>
            Animation events
        </em>
        . Tap on the screen. Look at the messages!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/events.gif"
        alt="events" width="272" height="484" class="aligncenter size-full wp-image-134384">
    </p>
    <div class="note">
        <em>
            Note
        </em>
        : You also can add a listener to
        <code>
            ViewPropertyAnimator
        </code>
        by adding a
        <code>
            setListener
        </code>
        to a call chain before calling
        <code>
            start()
        </code>
        :
        <p>
        </p>
        <pre lang="kotlin" class="language-kotlin hljs">rocket.animate().setListener(<span class="hljs-keyword">object</span> : Animator.AnimatorListener {
  <span class="hljs-comment">// Your action</span>
})
</pre>
        <p>
            Alternatively, you can set start and end actions on your View by calling
            <code>
                withStartAction(Runnable)
            </code>
            and
            <code>
                withEndAction(Runnable)
            </code>
            after
            <code>
                animate()
            </code>
            . It’s the equivalent to an
            <code>
                AnimatorListener
            </code>
            with these actions.
        </p>
    </div>
    <h2>
        Animation Options
    </h2>
    <p>
        Animations are not one-trick ponies that simply stop and go. They can
        loop, reverse, run for a specific duration, etc.
    </p>
    <p>
        In Android, you can use the following methods to adjust an animation:
    </p>
    <ul>
        <li>
            <code>
                repeatCount
            </code>
            — specifies the number of times the animation should repeat
            <i>
                after
            </i>
            the initial run.
        </li>
        <li>
            <code>
                repeatMode
            </code>
            — defines what this animation should do when it reaches the end
        </li>
        <li>
            <code>
                duration
            </code>
            — specifies the animation’s total duration
        </li>
    </ul>
    <p>
        Open up
        <em>
            FlyThereAndBackAnimationActivity.kt
        </em>
        , and add the following to
        <code>
            onStartAnimation()
        </code>
        .
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">val</span> animator = ValueAnimator.ofFloat(<span class="hljs-number">0</span>f, -screenHeight)

animator.addUpdateListener {
  <span class="hljs-keyword">val</span> value = it.animatedValue <span class="hljs-keyword">as</span> <span class="hljs-built_in">Float</span>
  rocket.translationY = value
  doge.translationY = value
}

<span class="hljs-comment">// 2</span>
animator.repeatMode = ValueAnimator.REVERSE
<span class="hljs-comment">// 3</span>
animator.repeatCount = <span class="hljs-number">3</span>

<span class="hljs-comment">// 4</span>
animator.duration = <span class="hljs-number">500</span>L
animator.start()
</pre>
    <p>
        In here, you:
    </p>
    <ol>
        <li>
            Create an animator, as usual
        </li>
        <li>
            You can set the
            <code>
                repeatMode
            </code>
            to either of the following:
            <ul>
                <li>
                    <code>
                        RESTART
                    </code>
                    — restarts the animation from the beginning.
                </li>
                <li>
                    <code>
                        REVERSE
                    </code>
                    — reverses the animation’s direction with every iteration.
                </li>
            </ul>
            <p>
                In this case, you set it to
                <code>
                    REVERSE
                </code>
                because you want the rocket to take off and then go back to the same position
                where it started. Just like SpaceX! :]
            </p>
        </li>
        <li>
            …Except you’ll do it twice.
        </li>
        <li>
            Set a duration and start the animation, as usual.
        </li>
    </ol>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : So why does the third section specify the repeat count at three? Each
            up-and-down motion consumes two repetitions, so you need three to bring
            Doge back to earth twice: one to land the first time, and two to launch
            and land again. How many times would you like to see Doge bounce? Play
            around with it!
        </p>
    </div>
    <p>
        Run the app. Select
        <em>
            Fly there and back (Animation options)
        </em>
        in the list. A new screen is opened. Tap on the screen.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/there-and-back.gif"
        alt="there-and-back" width="272" height="484" class="aligncenter size-full wp-image-134385">
    </p>
    <p>
        You should see your rocket jumping like a grasshopper! Take that, Elon
        Musk. :]
    </p>
    <h2>
        Declaring Animations in XML
    </h2>
    <p>
        You’ve made it to the best part of this tutorial. In this final section,
        you’ll learn how to declare once and use everywhere — yes, that’s right,
        you’ll be able to reuse your animations with impunity.
    </p>
    <p>
        By defining animations in XML, you allow reuse of animations throughout
        your code base.
    </p>
    <p>
        Defining animations in XML bears some resemblance to composing view layouts.
    </p>
    <p>
        The starter project has an animation XML in
        <em>
            res/animator
        </em>
        named
        <em>
            jump_and_blink.xml
        </em>
        . Open the file in the editor, you should see this:
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">set</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
     <span class="hljs-attr">android:ordering</span>=<span class="hljs-string">"together"</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">set</span>&gt;</span>
</pre>
    <p>
        The following XML tags are available to you:
    </p>
    <ul>
        <li>
            <code>
                set
            </code>
            — the same as
            <code>
                AnimatorSet
            </code>
        </li>
        <li>
            <code>
                animator
            </code>
            — the same as
            <code>
                ValueAnimator
            </code>
        </li>
        <li>
            <code>
                objectAnimator
            </code>
            — you guessed correctly; it stands for
            <code>
                ObjectAnimator
            </code>
        </li>
    </ul>
    <p>
        When using an
        <code>
            AnimatorSet
        </code>
        in XML, you nest the
        <code>
            ValueAnimator
        </code>
        and
        <code>
            ObjectAnimator
        </code>
        objects inside it, similar to how you nest
        <code>
            View
        </code>
        objects inside
        <code>
            ViewGroup
        </code>
        objects (
        <code>
            RelativeLayout
        </code>
        ,
        <code>
            LinearLayout
        </code>
        , etc.) in layout XML files.
    </p>
    <p>
        Replace the contents of
        <em>
            jump_and_blink.xml
        </em>
        with the following code:
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">set</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">android:ordering</span>=<span class="hljs-string">"together"</span>&gt;</span>
    
  <span class="hljs-tag">&lt;<span class="hljs-name">objectAnimator</span>
    <span class="hljs-attr">android:propertyName</span>=<span class="hljs-string">"alpha"</span>
    <span class="hljs-attr">android:duration</span>=<span class="hljs-string">"1000"</span>
    <span class="hljs-attr">android:repeatCount</span>=<span class="hljs-string">"1"</span>
    <span class="hljs-attr">android:repeatMode</span>=<span class="hljs-string">"reverse"</span>
    <span class="hljs-attr">android:interpolator</span>=<span class="hljs-string">"@android:interpolator/linear"</span>
    <span class="hljs-attr">android:valueFrom</span>=<span class="hljs-string">"1.0"</span>
    <span class="hljs-attr">android:valueTo</span>=<span class="hljs-string">"0.0"</span>
    <span class="hljs-attr">android:valueType</span>=<span class="hljs-string">"floatType"</span>/&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">objectAnimator</span>
    <span class="hljs-attr">android:propertyName</span>=<span class="hljs-string">"translationY"</span>
    <span class="hljs-attr">android:duration</span>=<span class="hljs-string">"1000"</span>
    <span class="hljs-attr">android:repeatCount</span>=<span class="hljs-string">"1"</span>
    <span class="hljs-attr">android:repeatMode</span>=<span class="hljs-string">"reverse"</span>
    <span class="hljs-attr">android:interpolator</span>=<span class="hljs-string">"@android:interpolator/bounce"</span>
    <span class="hljs-attr">android:valueFrom</span>=<span class="hljs-string">"0"</span>
    <span class="hljs-attr">android:valueTo</span>=<span class="hljs-string">"-500"</span>
    <span class="hljs-attr">android:valueType</span>=<span class="hljs-string">"floatType"</span>/&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">set</span>&gt;</span>
</pre>
    <p>
        Here you declare a root element,
        <code>
            set
        </code>
        tag. Its
        <code>
            ordering
        </code>
        attribute can be either
        <code>
            together
        </code>
        or
        <code>
            sequential
        </code>
        . It’s
        <code>
            together
        </code>
        by default, but you may prefer to specify it for clarity. The
        <code>
            set
        </code>
        tag has two child XML tags, each of which is an
        <code>
            objectAnimator
        </code>
        .
    </p>
    <p>
        Take a look at the following attributes of
        <code>
            objectAnimator
        </code>
        :
    </p>
    <ul>
        <li>
            <code>
                android:valueFrom
            </code>
            and
            <code>
                android:valueTo
            </code>
            — specify start and end values like you did when you created an instance
            of
            <code>
                ObjectAnimator
            </code>
        </li>
        <li>
            <code>
                android:valueType
            </code>
            — value type; either
            <code>
                floatType
            </code>
            or
            <code>
                intType
            </code>
        </li>
        <li>
            <code>
                android:propertyName
            </code>
            — the property you want to animate without the
            <code>
                set
            </code>
            part
        </li>
        <li>
            <code>
                android:duration
            </code>
            — duration of the animation
        </li>
        <li>
            <code>
                android:repeatCount
            </code>
            — the same as with
            <code>
                setRepeatCount
            </code>
        </li>
        <li>
            <code>
                android:repeatMode
            </code>
            — the same as with
            <code>
                setRepeatMode
            </code>
        </li>
        <li>
            <code>
                android:interpolator
            </code>
            — specify interpolator; it usually starts with
            <code>
                @android:interpolator/
            </code>
            . Start typing this and Android Studio will show all available interpolators
            under autocomplete options
        </li>
        <li>
            You can’t specify your target object here, but you can do it later in
            Kotlin
        </li>
    </ul>
    <p>
        In the last block, you added two instances of
        <code>
            objectAnimator
        </code>
        to the
        <code>
            AnimatorSet
        </code>
        , and they will play together. Now, it’s time to use them.
    </p>
    <p>
        Go to
        <em>
            XmlAnimationActivity.kt
        </em>
        and add the following code to
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-comment">// 1</span>
  <span class="hljs-keyword">val</span> rocketAnimatorSet = AnimatorInflater.loadAnimator(<span class="hljs-keyword">this</span>, R.animator.jump_and_blink) <span class="hljs-keyword">as</span> AnimatorSet
  <span class="hljs-comment">// 2</span>
  rocketAnimatorSet.setTarget(rocket)
  
  <span class="hljs-comment">// 3</span>
  <span class="hljs-keyword">val</span> dogeAnimatorSet = AnimatorInflater.loadAnimator(<span class="hljs-keyword">this</span>, R.animator.jump_and_blink) <span class="hljs-keyword">as</span> AnimatorSet
  <span class="hljs-comment">// 4</span>
  dogeAnimatorSet.setTarget(doge)

  <span class="hljs-comment">// 5</span>
  <span class="hljs-keyword">val</span> bothAnimatorSet = AnimatorSet()
  bothAnimatorSet.playTogether(rocketAnimatorSet, dogeAnimatorSet)
  <span class="hljs-comment">// 6</span>
  bothAnimatorSet.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
  bothAnimatorSet.start()
</pre>
    <p>
        In the above code, you’re doing a few things:
    </p>
    <ol>
        <li>
            First, you load
            <code>
                AnimatorSet
            </code>
            from
            <code>
                R.animator.jump_and_blink
            </code>
            file, just like you normally would to inflate a view layout
        </li>
        <li>
            Then you set
            <code>
                rocket
            </code>
            as the target for just-loaded animator
        </li>
        <li>
            Load the animator from the same file once again
        </li>
        <li>
            Rinse and repeat for
            <code>
                doge
            </code>
            object
        </li>
        <li>
            Now you create a third
            <code>
                AnimatorSet
            </code>
            and set it up to play the first two simultaneously
        </li>
        <li>
            Set the duration for the root animator and start
        </li>
        <li>
            Whew! Rest just a little bit :]
        </li>
    </ol>
    <p>
        Build and run. Select
        <em>
            Jump and blink (Animations in XML)
        </em>
        in the list. Tap to see your handiwork.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/jump-n-blink.gif"
        alt="jump-n-blink" width="272" height="484" class="aligncenter size-full wp-image-134382">
    </p>
    <p>
        You should see Doge jumping, disappearing and then returning back to the
        ground safely :]
    </p>
    <h2>
        Where To Go From Here
    </h2>
    <p>
        You can grab the final project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/10/rocket_launcher-final.zip">
            here
        </a>
        .
    </p>
    <p>
        During this tutorial you:
    </p>
    <ul>
        <li>
            Created and used property animations with
            <code>
                ValueAnimator
            </code>
            and
            <code>
                ObjectAnimator
            </code>
        </li>
        <li>
            Set up
            <em>
                time interpolator
            </em>
            of your choice for your animation
        </li>
        <li>
            Animated position, rotation and color for
            <code>
                View
            </code>
        </li>
        <li>
            Combined animations together
        </li>
        <li>
            Used the spectacular
            <code>
                ViewPropertyAnimator
            </code>
            with the help of
            <code>
                animate()
            </code>
        </li>
        <li>
            Repeated your animation
        </li>
        <li>
            Defined the animation in XML for reuse across the project
        </li>
    </ul>
    <p>
        Basically, you just gained Android animation super-powers.
    </p>
    <p>
        If you’re hungry for more, check out the available time interpolators
        in
        <a href="https://developer.android.com/reference/android/animation/TimeInterpolator.html"
        target="_blank">
            Android’s documentation
        </a>
        (see Known Indirect Subclasses). If you’re not happy with either of them,
        you can create your own. You can also set
        <code>
            Keyframe
        </code>
        s for your animation to make them very sophisticated.
    </p>
    <p>
        Android has other animations systems like
        <em>
            View animations
        </em>
        and
        <em>
            Drawable Animations
        </em>
        . You can also make use of
        <em>
            Canvas
        </em>
        and
        <em>
            OpenGL ES
        </em>
        APIs to create animations. Stay tuned :]
    </p>
</div>