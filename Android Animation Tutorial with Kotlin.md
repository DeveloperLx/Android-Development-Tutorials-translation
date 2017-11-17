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
        上述的代码：
    </p>
    <ol>
        <li>
            创建了一个新的
            <code>
                ValueAnimator
            </code>
            。
        </li>
        <li>
            为ValueAnimator添加一个
            <code>
                AnimatorUpdateListener
            </code>
            来更新火箭的位置。
        </li>
        <li>
            创建一个
            <code>
                ObjectAnimator
            </code>
            ，用来处理火箭的旋转。
        </li>
        <li>
            创建一个
            <code>
                AnimatorSet
            </code>
            的实例。
        </li>
        <li>
            指定同时执行
            <code>
                positionAnimator
            </code>
            和
            <code>
                rotationAnimator
            </code>
            。
        </li>
        <li>
            就像一般的动画一样，设置它的持续时间，并调用
            <code>
                start()
            </code>
            。
        </li>
    </ol>
    <p>
        再次运行项目。选择
        <em>
            Launch and spin (AnimatorSet)
        </em>
        。点击屏幕。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/launch-n-spin.gif"
        alt="launch-n-spin" width="272" height="484" class="aligncenter size-full wp-image-134377">
    </p>
    <p>
        Doge违背了物理学定理。
    </p>
    <p>
        有一个很棒的工具，可以简化给一个对象上多个属性添加动画的过程。它被称作...
    </p>
    <h3>
        ViewPropertyAnimator
    </h3>
    <p>
        使用
        <code>
            ViewPropertyAnimator
        </code>
        来编写动画相关代码的最重要的一件事，就是它易于去读写 - 你很快就会懂得。
    </p>
    <p>
        打开
        <em>
            LaunchAndSpinViewPropertyAnimatorAnimationActivity.kt
        </em>
        并添加下列的代码到
        <code>
            onStartAnimation()
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">rocket.animate()
    .translationY(-screenHeight)
    .rotationBy(<span class="hljs-number">360</span>f)
    .setDuration(BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION)
    .start()
</pre>
    <p>
        这里，
        <code>
            animate()
        </code>
        方法会返回一个
        <code>
            ViewPropertyAnimator
        </code>
        的实例，这样你就可以将方法的调用连接起来。
    </p>
    <p>
        运行项目，选择
        <em>
            Launch and spin (ViewPropertyAnimator)
        </em>
        ，你就会看到和上一节中相同的代码。
    </p>
    <p>
        将本节的代码和上一节中
        <code>
            AnimatorSet
        </code>
        相关的代码进行比较：
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
        在多个动画同步进行的时候，可以提供更好的性能。它将无效的调用进行优化，对于添加到多个属性上的动画，只会占用一次调用来进行调整。
    </p>
    <h3>
        为两个对象的同一属性添加动画
    </h3>
    <p>
        <code>
            ValueAnimator
        </code>
        的一个很棒的功能，就是你可以将动画值应用到多个对象上。
    </p>
    <p>
        打开
        <em>
            FlyWithDogeAnimationActivity.kt
        </em>
        并在
        <code>
            onStartAnimation()
        </code>
        中添加下列的代码：
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
        在上述的代码中，你创建了三个animator：
    </p>
    <ol>
        <li>
            <code>
                positionAnimator
            </code>
            - 用来改变
            <code>
                rocket
            </code>
            和
            <code>
                doge
            </code>
            的位置
        </li>
        <li>
            <code>
                rotationAnimator
            </code>
            - 用来旋转Doge
        </li>
        <li>
            <code>
                animatorSet
            </code>
            - 把前面的两个animator连接起来
        </li>
    </ol>
    <p>
        注意，你在第一个animator中，一次设置了
        <i>
            两个
        </i>
        对象的translation。
    </p>
    <p>
        运行app并选择
        <em>
            Don’t leave Doge behind (Animating two objects)
        </em>
        。你知道现在该做什么。去往月球！
    </p>
    <h2>
        动画Listeners
    </h2>
    <p>
        动画通常意味着一个动作已经发生或即将发生。
    </p>
    <p>
        你没有观察火箭，但知道当动画结束的时候，它会停下来并停留在屏幕上。如果你不打算把它留在这里或完成activity，就可以将其移除以节省资源。
    </p>
    <p>
        <code>
            AnimatorListener
        </code>
        - 会在发生下列时间时，都到来自animator的通知：
    </p>
    <ul>
        <li>
            <code>
                onAnimationStart()
            </code>
            — 在动画开始时调用
        </li>
        <li>
            <code>
                onAnimationEnd()
            </code>
            - 当动画结束时调用
        </li>
        <li>
            <code>
                onAnimationRepeat()
            </code>
            - 当动画重复播放时进行调用
        </li>
        <li>
            <code>
                onAnimationCancel()
            </code>
            - 当动画被取消时调用
        </li>
    </ul>
    <p>
        打开
        <em>
            WithListenerAnimationActivity.kt
        </em>
        并添加下列的代码到
        <code>
            onStartAnimation()
        </code>
        中：
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
        上述代码的结构，应该看起来和上一节中一样，除了listener这一部分。这里所完成的事有：
    </p>
    <ol>
        <li>
            创建并设置一个animator。你使用了
            <code>
                ValueAnimator
            </code>
            来同时改变两个对象的位置 - 
            <code>
                ObjectAnimator
            </code>
            无法做到这点。
        </li>
        <li>
            添加
            <code>
                AnimatorListener
            </code>
            。
        </li>
        <li>
            当动画开始时展示一条toast消息
        </li>
        <li>
            当动画结束时展示另一条toast消息
        </li>
        <li>
            像往常一样开始动画
        </li>
    </ol>
    <p>
        运行app。选择
        <em>
            Animation events
        </em>
        。点击屏幕。查看相关的信息！
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/events.gif"
        alt="events" width="272" height="484" class="aligncenter size-full wp-image-134384">
    </p>
    <div class="note">
        <em>
            注意
        </em>
        ：你还可以在
        <code>
            start()
        </code>
        前将一个
        <code>
            setListener
        </code>
        添加到调用链中，为
        <code>
            ViewPropertyAnimator
        </code>
        添加一个listener：
        <p>
        </p>
        <pre lang="kotlin" class="language-kotlin hljs">rocket.animate().setListener(<span class="hljs-keyword">object</span> : Animator.AnimatorListener {
  <span class="hljs-comment">// Your action</span>
})
</pre>
        <p>
            另一种办法，你可以通过在
            <code>
                animate()
            </code>
            后调用
            <code>
                withStartAction(Runnable)
            </code>
            和
            <code>
                withEndAction(Runnable)
            </code>
            来设置开始及结束时要执行的动作。这和使用
            <code>
                AnimatorListener
            </code>
            是完全等效的。
        </p>
    </div>
    <h2>
        Animation选项
    </h2>
    <p>
        动画不只有开始和停止这么简单的两招。还可以进行循环，反转，以指定的持续时间来运行，等等。
    </p>
    <p>
        在Android中，你可以使用下列的方法来调整动画：
    </p>
    <ul>
        <li>
            <code>
                repeatCount
            </code>
            - 指定动画重复的次数。
        </li>
        <li>
            <code>
                repeatMode
            </code>
            - 定义动画结束时要做的事
        </li>
        <li>
            <code>
                duration
            </code>
            - 指定动画总的持续时间
        </li>
    </ul>
    <p>
        打开
        <em>
            FlyThereAndBackAnimationActivity.kt
        </em>
        ，添加下列代码到
        <code>
            onStartAnimation()
        </code>
        中。
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
        这里：
    </p>
    <ol>
        <li>
            和往常一样，创建一个animator
        </li>
        <li>
            你可以将
            <code>
                repeatMode
            </code>
            设置为以下的一项：
            <ul>
                <li>
                    <code>
                        RESTART
                    </code>
                    - 从开头重新开始动画。
                </li>
                <li>
                    <code>
                        REVERSE
                    </code>
                    - 每次迭代的时候反转动画的方向。
                </li>
            </ul>
            <p>
                在本例中，你将它设置为
                <code>
                    REVERSE
                </code>
                ，因为你希望火箭发射后可以返回到它开始时的位置。就像SpaceX一样！:]
            </p>
        </li>
        <li>
            你还想再执行三次。
        </li>
        <li>
            像往常一样，设置持续的时间并启动动画。
        </li>
    </ol>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：为何将重复的次数设置为3？因为一次的上来下去将消耗两次的重复次数，因此你将这里设置成3，才能将Doge带回地球两次：一次让它返回地面，两次让它再让它重复执行。
        </p>
    </div>
    <p>
        运行app。选择列表中的
        <em>
            Fly there and back (Animation options)
        </em>
        。会打开一个新的新的页面。点击它。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/there-and-back.gif"
        alt="there-and-back" width="272" height="484" class="aligncenter size-full wp-image-134385">
    </p>
    <p>
        你会看到火箭就像是一个跳动的蚂蚱！
    </p>
    <h2>
        在XML中声明动画
    </h2>
    <p>
        你已完成了本教程中最棒的一部分。在最后一节，你将学习如何让动画一次声明，处处使用 - 是的，你将可以不受限制的重复使用一个动画。
    </p>
    <p>
        通过在XML中定义动画，你就可以在整个代码库中对它进行重用了。
    </p>
    <p>
        在XML中定义动画，与编写view的布局有一些近似之处。
    </p>
    <p>
        初始的项目在
        <em>
            res/animator
        </em>
        目录下有一个名为
        <em>
            jump_and_blink.xml
        </em>
        的动画xml文件。打开它，你会看到如下的内容：
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">set</span> <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
     <span class="hljs-attr">android:ordering</span>=<span class="hljs-string">"together"</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">set</span>&gt;</span>
</pre>
    <p>
        以下的XML可供使用：
    </p>
    <ul>
        <li>
            <code>
                set
            </code>
            - 等同于
            <code>
                AnimatorSet
            </code>
        </li>
        <li>
            <code>
                animator
            </code>
            - 等同于
            <code>
                ValueAnimator
            </code>
        </li>
        <li>
            <code>
                objectAnimator
            </code>
            - 猜对了；它相当于
            <code>
                ObjectAnimator
            </code>
        </li>
    </ul>
    <p>
        当在XML中使用
        <code>
            AnimatorSet
        </code>
        时，你可以把
        <code>
            ValueAnimator
        </code>
        和
        <code>
            ObjectAnimator
        </code>
        对象嵌入到它的内部。就类似于你在XML文件中，将
        <code>
            View
        </code>
        嵌入到
        <code>
            ViewGroup
        </code>
        （诸如
        <code>
            RelativeLayout
        </code>
        ，
        <code>
            LinearLayout
        </code>
        等）中。
    </p>
    <p>
        使用下列的代码替换
        <em>
            jump_and_blink.xml
        </em>
        的内容：
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
        这里你将根元素声明为
        <code>
            set
        </code>
        。它的
        <code>
            ordering
        </code>
        属性可以是
        <code>
            together
        </code>
        或
        <code>
            sequential
        </code>
        的一种。默认的即为
        <code>
            together
        </code>
        ，但你也可以显式地指定它。
        <code>
            set
        </code>
        有两个子标签，且都是
        <code>
            objectAnimator
        </code>
        。
    </p>
    <p>
        看一下
        <code>
            objectAnimator
        </code>
        中的属性：
    </p>
    <ul>
        <li>
            <code>
                android:valueFrom
            </code>
            和
            <code>
                android:valueTo
            </code>
            - 指定开始和结束时动画的值，就像你在创建
            <code>
                ObjectAnimator
            </code>
            时所做的一样
        </li>
        <li>
            <code>
                android:valueType
            </code>
            - 值类型；可以选择
            <code>
                floatType
            </code>
            或
            <code>
                intType
            </code>
        </li>
        <li>
            <code>
                android:propertyName
            </code>
            - 你想要添加动画的属性
        </li>
        <li>
            <code>
                android:duration
            </code>
            - 动画的持续时间
        </li>
        <li>
            <code>
                android:repeatCount
            </code>
            - 等同于
            <code>
                setRepeatCount
            </code>
        </li>
        <li>
            <code>
                android:repeatMode
            </code>
            - 等同于
            <code>
                setRepeatMode
            </code>
        </li>
        <li>
            <code>
                android:interpolator
            </code>
            - 指定插值器。它通常以
            <code>
                @android:interpolator/
            </code>
            开头，输入它，Android Studio就会自动把可用的插值器提示给你
        </li>
        <li>
            你无法在这里指定目标的对象，需要在后面的Kotlin代码中来完成
        </li>
    </ul>
    <p>
        你添加了两个
        <code>
            objectAnimator
        </code>
        的实例到
        <code>
            AnimatorSet
        </code>
        中，它们将同时被播放。现在，是时候来进行使用了。
    </p>
    <p>
        打开
        <em>
            XmlAnimationActivity.kt
        </em>
        并添加下列的代码到
        <code>
            onStartAnimation()
        </code>
        中：
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
        上述的代码中：
    </p>
    <ol>
        <li>
            首先，从
            <code>
                R.animator.jump\_and\_blink
            </code>
            文件中加载
            <code>
                AnimatorSet
            </code>
            ，就像你在inflate一个view layout时所作的一样
        </li>
        <li>
            然后设置
            <code>
                rocket
            </code>
            作为刚加载的animator的目标
        </li>
        <li>
            再次从相同的文件中加载一个animator
        </li>
        <li>
            设置它的目标为
            <code>
                doge
            </code>
            对象
        </li>
        <li>
            又创建了一个
            <code>
                AnimatorSet
            </code>
            ，并让它同时播放上面的两个动画
        </li>
        <li>
            设置根animator的持续时间并开始
        </li>
        <li>
            Whew! 稍微休息一下 :]
        </li>
    </ol>
    <p>
        运行项目。选择列表中的
        <em>
            Jump and blink (Animations in XML)
        </em>
        。点击查看你的作品。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/jump-n-blink.gif"
        alt="jump-n-blink" width="272" height="484" class="aligncenter size-full wp-image-134382">
    </p>
    <p>
        你会看到Doge在跳动，消失，然后安全地返回到了地面 :]
    </p>
    <h2>
        从这儿去向哪里
    </h2>
    <p>
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/10/rocket_launcher-final.zip">
            这里
        </a>
        获取最终的项目。
    </p>
    <p>
        在本教程中，你：
    </p>
    <ul>
        <li>
            用
            <code>
                ValueAnimator
            </code>
            和
            <code>
                ObjectAnimator
            </code>
            创建并使用属性动画
        </li>
        <li>
            为你的动画设置你选择的
            <em>
                时间插值器
            </em>
        </li>
        <li>
            给
            <code>
                View
            </code>
            的位置，选择和颜色属性添加动画
        </li>
        <li>
            把若干动画结合到一起
        </li>
        <li>
            在
            <code>
                animate()
            </code>
            的帮助下，使用超赞的
            <code>
                ViewPropertyAnimator
            </code>
        </li>
        <li>
            重复动画
        </li>
        <li>
            在XML中定义动画，并在项目中进行复用
        </li>
    </ul>
    <p>
        你已基本获得了Android动画的超能力。
    </p>
    <p>
        如果你还期望学到更多的内容，可以在
        <a href="https://developer.android.com/reference/android/animation/TimeInterpolator.html"
        target="_blank">
            Android’s documentation
        </a>
        中查看时间插值器。如果你对其中任何的一种都不满意，甚至还可以进行自定义。你还可以为动画设置
        <code>
            Keyframe
        </code>
        来使其变得非常复杂。
    </p>
    <p>
        Android中还有其它的动画系统，类型
        <em>
            View animations
        </em>
        和
        <em>
            Drawable Animations
        </em>
        。你还可以使用
        <em>
            Canvas
        </em>
        和
        <em>
            OpenGL ES
        </em>
        的API来创建动画。保持关注 :]
    </p>
</div>