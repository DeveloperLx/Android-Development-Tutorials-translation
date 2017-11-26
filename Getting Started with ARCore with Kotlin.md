# 入门ARCore - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/170520/getting-started-arcore-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ARCore-feature.png"
        alt="Getting Started with ARCore with Kotlin" width="250" height="250"
        class="alignright size-thumbnail bordered">
    </p>
    <p>
        维京人有现实中的大炮么？我不完全确定。但没有道理维京人不可以在AR中有大炮！:]
    </p>
    <p>
        在WWDC 2017，苹果发布了
        <em>
            ARKit
        </em>
        ，进军了AR开发的领域。Google同样也不甘示弱，就在上周，它
        <a href="https://www.blog.google/products/google-vr/arcore-augmented-reality-android-scale/"
        target="_blank">
            发布了
        </a>
        <em>
            ARCore
        </em>
        ，它是从
        <a href="https://get.google.com/tango/" target="_blank">
            Tango
        </a>
        的室内地图项目中提取出来的。Tango需要使用带有深度传感器的特定设备，而ARCore最终将在大部分的Android设备上都可用。
    </p>
    <p>
        对AR领域的比赛依然开始，演示的项目来得快速且猛烈。你可以在
        <a href="https://experiments.withgoogle.com/ar" target="_blank">
            AR实验的网站
        </a>
        上进行查看。
    </p>
    <p>
        ARCore app可以使用 can be built using
        <em>
            OpenGL
        </em>
        ，
        <em>
            Unity
        </em>
        ，和进行构建。在本教程中，你将在被修改过的，由Google提供的OpenGL示例app之上进行入门，并全部使用
        <em>
            Kotlin
        </em>
        来进行编码！全部都在Android Studio的舒适环境中！:]
    </p>
    <p>
        如果你刚刚入门Kotlin，请学习
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Kotlin%20For%20Android%20An%20Introduction.md"
        target="_blank">
            用Kotlin编写Android：介绍
        </a>
        。
    </p>
    <p>
        ARCore不能在模拟器上使用。你可以选择
        <em>
            Samsung Galaxy S8
        </em>
        或
        <em>
            Google Pixel/Pixel XL
        </em>
        的设备，以及Android Nougat（7.0）或更高的系统版本。如果你没有这些设备，希望你仍然可以对使用ARCore SDK有所体验。
    </p>
    <p>
        准备好探索AR的世界了么？让我们开始吧！
    </p>
    <h2>
        入门
    </h2>
    <p>
        首先下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/targetpractice-starter-2.zip">
            初始项目
        </a>
        。并在Android Studio 3.0 Beta 5或更高的版本中打开它。
    </p>
    <p>
        幸运的是，如果使用带有Kotlin插件的Android Studio 2.3.3也是可以的。:]
    </p>
    <p>
        接下来，确保你的手机已打开了
        <a href="https://developer.android.com/studio/debug/dev-options.html#enable"
        target="_blank">
            开发者选项
        </a>
        以及
        <a href="https://developer.android.com/studio/debug/dev-options.html#debugging"
        target="_blank">
            USB调试
        </a>
        。在运行初始项目之前，你还需要下载并安装由Google提供的
        <a href="https://github.com/google-ar/arcore-android-sdk/releases/download/sdk-preview/arcore-preview.apk">
            ARCore Service
        </a>
        。
    </p>
    <p>
        ARCore Service可以使用下列的
        <em>
            adb
        </em>
        命令进行安装：
    </p>
    <pre lang="bash" class="language-bash hljs">$ adb install -r -d arcore-preview.apk
</pre>
    <p>
        如果你想了解更多的信息，请访问adb
        <a href="https://developer.android.com/studio/command-line/adb.html">
            文档
        </a>
        。
    </p>
    <p>
        现在，按
        <em>
            Run/Run ‘app’
        </em>
        或Ctrl-R键运行初始项目。 
    </p>
    <p>
        它会首先请求你给予相机权限，之后屏幕会出现一个选择器，你会用它来选择待插入到屏幕中的对象。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-170527"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        你还会在底部看到一个snackbar提示“Searching for surfaces…”。同时可能还会看到一些被跟踪的点。
    </p>
    <p>
        将设备瞄准一个平面，这个平面应当会被检测到：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-170528"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        当检测到第一个平面时，snackbar就会消失，这个平面则会被高亮展示。注意在检测浅色的平面时，可能会遇到问题。
    </p>
    <p>
        此刻，初始app还没有做很多的事，但是时候来熟悉一下它的代码！尤其是你设置维京人和大炮之前！
    </p>
    <h2>
        ARCode SDK
    </h2>
    <p>
        在初始项目中
        <em>
            Project
        </em>
        视图下的
        <em>
            main/assets
        </em>
        文件中，包含了你将要使用的3D模型，分别为维京人，大炮和标靶。他们都是由
        <em>
            Blender
        </em>
        创建，参考
        <a href="https://www.raywenderlich.com/48293/how-to-export-blender-models-to-opengl-es-part-1"
        target="_blank">
            How To Export Blender Models to OpenGL ES: Part 1/3
        </a>
        。
    </p>
    <p>
        在
        <em>
            res/raw
        </em>
        目录中，还有一些OpenGL的着色器，它们全都来自ARCore的示例app。
    </p>
    <p>
        你还会在初始项目中看到一个名叫
        <em>
            rendering
        </em>
        的包，它包含了一些OpenGL的渲染器和来自ARCore示例app中的工具。还有一个叫做
        <em>
            PlaneAttachment
        </em>
        的使用ARCore SDK的Kotlin类。
    </p>
    <h3>
        Plane，Anchor，和Pose
    </h3>
    <p>
        <em>
            PlaneAttachment
        </em>
        类是通过一个
        <em>
            Plane
        </em>
        和一个
        <em>
            Anchor
        </em>
        构成的，通过它们来生成一个
        <em>
            姿势
        </em>
        。这三样都来自于ARCore SDK。
    </p>
    <p>
        <em>
            Plane
        </em>
        描述了真实世界中的二维平面。 
        <em>
            Anchor
        </em>
        则描述了在控件中的一个固定的位置和方向。而
        <em>
            Pose
        </em>
        则描述了从一个坐标系到另一个的转变，将一个对象的本地frame转变成
        <em>
            世界的坐标frame
        </em>
        。
    </p>
    <p>
        你可以在
        <a href="https://developers.google.com/ar/reference/java/com/google/ar/core/package-summary"
        target="_blank">
            官方文档
        </a>
        中阅读更多相关的内容。
    </p>
    <p>
        因此，
        <em>
            PlaneAttachment
        </em>
        可以让你把锚点附加到一个平面上，然后得到生成的pose，它会在你更改锚点位置的时候被ARCore所使用。
    </p>
    <h3>
        ARCore Session
    </h3>
    <p>
        初始项目在
        <em>
            MainActivity
        </em>
        中已包含了一个
        <em>
            Session
        </em>
        对象。它描述了所有的AR状态，当用户点击屏幕的时候，就可以将锚点附加到平面上。
    </p>
    <p>
        在
        <code>
            onCreate(...)
        </code>
        中的
        <code>
            setupSession()
        </code>
        方法中，初始项目会检查这个设备是否支持ARCore。如果不支持的话，就会展示一个
        <em>
            Toast
        </em>
        并结束activity。
    </p>
    <p>
        假设你有一个支持ARCore的设备，现在就可以将一些对象渲染到场景中了！
    </p>
    <h2>   
        添加对象
    </h2>
    <p>
        打开
        <em>
            MainActivity
        </em>
        ，并添加下列property
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> vikingObject = ObjectRenderer()
<span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> cannonObject = ObjectRenderer()
<span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> targetObject = ObjectRenderer()
</pre>
    <p>
        分别定义了三个来自ARCore示例app的
        <em>
            ObjectRenderer
        </em>
        。
    </p>
    <p>
        然后，在它的下面添加三个
        <em>
            PlaneAttachment
        </em>
        property：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> vikingAttachment: PlaneAttachment? = <span class="hljs-literal">null</span>
<span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> cannonAttachment: PlaneAttachment? = <span class="hljs-literal">null</span>
<span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> targetAttachment: PlaneAttachment? = <span class="hljs-literal">null</span>
</pre>
    <p>
        它们均为Kotlin
        <em>
            nullables
        </em>
        类型，且被初始化为null。它们将在之后用户点击屏幕时被创建。
    </p>
    <p>
        你需要在
        <code>
            onSurfaceCreated(...)
        </code>
        中设置对象。找到其中已存在的
        <code>
            try-catch
        </code>
        代码块，并在它的上面添加如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// Prepare the other rendering objects.</span>
<span class="hljs-keyword">try</span> {
  vikingObject.createOnGlThread(<span class="hljs-keyword">this</span>, <span class="hljs-string">"viking.obj"</span>, <span class="hljs-string">"viking.png"</span>)
  vikingObject.setMaterialProperties(<span class="hljs-number">0.0</span>f, <span class="hljs-number">3.5</span>f, <span class="hljs-number">1.0</span>f, <span class="hljs-number">6.0</span>f)
  cannonObject.createOnGlThread(<span class="hljs-keyword">this</span>, <span class="hljs-string">"cannon.obj"</span>, <span class="hljs-string">"cannon.png"</span>)
  cannonObject.setMaterialProperties(<span class="hljs-number">0.0</span>f, <span class="hljs-number">3.5</span>f, <span class="hljs-number">1.0</span>f, <span class="hljs-number">6.0</span>f)
  targetObject.createOnGlThread(<span class="hljs-keyword">this</span>, <span class="hljs-string">"target.obj"</span>, <span class="hljs-string">"target.png"</span>)
  targetObject.setMaterialProperties(<span class="hljs-number">0.0</span>f, <span class="hljs-number">3.5</span>f, <span class="hljs-number">1.0</span>f, <span class="hljs-number">6.0</span>f)
} <span class="hljs-keyword">catch</span> (e: IOException) {
  Log.e(TAG, <span class="hljs-string">"Failed to read obj file"</span>)
}
</pre>
    <p>
        你将使用初始项目中提供的3D模型文件来设置这三个对象，并在这三个对象上添加一些material的property。
    </p>
    <h2>
        将锚点附加到这个Session上
    </h2>
    <p>
        在
        <em>
            MainActivity
        </em>
        中找到
        <code>
            handleTaps(...)
        </code>
        。添加下列的代码到最内部的
        <code>
            if
        </code>
        语句中，就在
        <code>
            break
        </code>
        语句前的注释之上：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">when</span> (mode) {
  Mode.VIKING -&gt; vikingAttachment = addSessionAnchorFromAttachment(vikingAttachment, hit)
  Mode.CANNON -&gt; cannonAttachment = addSessionAnchorFromAttachment(cannonAttachment, hit)
  Mode.TARGET -&gt; targetAttachment = addSessionAnchorFromAttachment(targetAttachment, hit)
}
</pre>
    <p>
        <code>
            mode
        </code>
        的值则是由屏幕顶部的radio按钮控制的。
        <code>
            Mode
        </code>
        是一个Kotlin的
        <em>
            枚举类
        </em>
        ，它的每个mode值中还包含了一个缩放系数的浮点值，用来调整相应的3D模型在场景中的大小。
    </p>
    <p>
        在
        <code>
            when
        </code>
        声明中，对每个mode，你都要使用旧的attachment和点击的hit值，来为相应的
        <em>
            PlaneAttachment
        </em>
        设置一个新值，它是一个ARCore的
        <em>
            PlaneHitResult
        </em>
        ，定义了点击和平面的3D的交点。
    </p>
    <p>
        现在，你需要添加一个
        <code>
            addSessionAnchorFromAttachment(...)
        </code>
        方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">addSessionAnchorFromAttachment</span><span class="hljs-params">(
  previousAttachment: <span class="hljs-type">PlaneAttachment</span>?, hit: <span class="hljs-type">PlaneHitResult</span>)</span></span>: PlaneAttachment {
  previousAttachment?.let {
    session.removeAnchors(Arrays.asList(previousAttachment.anchor))
  }
  <span class="hljs-keyword">return</span> PlaneAttachment(hit.plane, session.addAnchor(hit.hitPose))
}
</pre>
    <p>
        如果
        <code>
            previousAttachment
        </code>
        不为空，你需要首先将锚点从session中移除掉，然后再给session添加一个新锚点，并基于来自PlaneHitResult平面和锚点，返回
        <em>
            PlaneAttachment
        </em>
        的新值。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/vikingcannons.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/vikingcannons.png"
            alt="" width="372" height="281" class="aligncenter size-full wp-image-170603">
        </a>
    </p>
    <p>
        你几乎已经能够看到维京人做打靶练习了！:]
    </p>
    <h2>
        绘制对象
    </h2>
    <p>
        你需要完成的最后一步就是把对象绘制到屏幕上。你会在用户点击的时候创建平面，但现在你需要在这是完成对象的绘制。
    </p>
    <p>
        找到
        <code>
            onDrawFrame(...)
        </code>
        方法。添加下列的代码到
        <code>
            try
        </code>
        代码块的底部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">drawObject(vikingObject, vikingAttachment, Mode.VIKING.scaleFactor,
  projectionMatrix, viewMatrix, lightIntensity)
drawObject(cannonObject, cannonAttachment, Mode.CANNON.scaleFactor,
  projectionMatrix, viewMatrix, lightIntensity)
drawObject(targetObject, targetAttachment, Mode.TARGET.scaleFactor,
  projectionMatrix, viewMatrix, lightIntensity)
</pre>
    <p>
        你调用了已有的
        <code>
            drawObject(...)
        </code>
        助手方法，它需要传参对象，相应的attachment，以及相应的缩放系数，还有OpenGL所需的相关的值来绘制对象。它们是通过初试项目中的助手方法计算出来的：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">computeProjectionMatrix</span><span class="hljs-params">()</span></span>: FloatArray {
  <span class="hljs-keyword">val</span> projectionMatrix = FloatArray(<span class="hljs-number">16</span>)
  session.getProjectionMatrix(projectionMatrix, <span class="hljs-number">0</span>, <span class="hljs-number">0.1</span>f, <span class="hljs-number">100.0</span>f)
  <span class="hljs-keyword">return</span> projectionMatrix
}

<span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">computeViewMatrix</span><span class="hljs-params">(frame: <span class="hljs-type">Frame</span>)</span></span>: FloatArray {
  <span class="hljs-keyword">val</span> viewMatrix = FloatArray(<span class="hljs-number">16</span>)
  frame.getViewMatrix(viewMatrix, <span class="hljs-number">0</span>)
  <span class="hljs-keyword">return</span> viewMatrix
}

<span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">computeLightIntensity</span><span class="hljs-params">(frame: <span class="hljs-type">Frame</span>)</span></span> = frame.lightEstimate.pixelIntensity
</pre>
    <p>
        <code>
            projectionMatrix
        </code>
        是从ARCore的Session中计算出来的，而
        <code>
            viewMatrix
        </code>
        则是从ARCore的
        <em>
            Frame
        </em>
        中计算出来的，它们描述了AR在特定时间下的状态。而
        <code>
            lightIntensity
        </code>
        同样是有frame所决定的。
    </p>
    <p>
        运行app。在屏幕顶部选择一个对象mode，然后你会发现在镜头中出现了一个平面，点击它就可以在上面添加一个对象。当添加好所有的对象之后，旋转手机，你就会看到：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-650x366.png"
            alt="" width="650" height="366" class="aligncenter size-large wp-image-170529"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-650x366.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-480x270.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-266x151.png 266w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        你可以移动场景，观看维京人正准备开火。它不会被消失掉！:]
    </p>
    <h2>
        从这儿去向哪里？
    </h2>
    <p>
        你已经在Android Studio中初步地入门了ARCore和OpenGL。关于更多的内容，可以查看
        <a href="https://developers.google.com/ar/reference/java" target="_blank">
            ARCore API
        </a>
        和
        <a href="https://developers.google.com/ar/discover/" target="_blank">
            ARCore Overview
        </a>
        。
    </p>
    <p>
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/targetpractice-final-2.zip">
            这里
        </a>
        下载最终的项目。
    </p>
    <p>
        你还可以使用
        <a href="https://developers.google.com/ar/develop/unity/getting-started"
        target="_blank">
            ARCore with Unity
        </a>
        和
        <a href="https://developers.google.com/ar/develop/unreal/getting-started"
        target="_blank">
            ARCore with Unreal
        </a>
        。由于ARCore相当一大部分的开发都依赖于Unity，我强烈地建议你也看一看
        <a href="https://www.raywenderlich.com/category/unity" target="_blank">
            Unity相关的内容
        </a>
        。
    </p>
    <p>
        除了Android，ARCore还面向网络，你可以在
        <a href="https://developers.google.com/ar/develop/web/getting-started"
        target="_blank">
            这里
        </a>
        找到更多相关的信息。最后，你可以在
        <a href="https://experiments.withgoogle.com/ar" target="_blank">
            Google实验网站
        </a>
        上，找到一些使用ARCore完成的非常酷的演示。
    </p>
</div>