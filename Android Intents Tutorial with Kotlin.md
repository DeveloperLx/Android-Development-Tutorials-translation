# Android Intent教程 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/171071/android-intents-tutorial-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志：
            </em>
            本教程已由Steven Smith更新至Kotlin，Android 26 (Oreo)，及Android Studio 3.0的版本。原教程是由Darryl Bayliss撰写的。之前已由Artem Kholodnyi进行过更新。
        </p>
    </div>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/05/Intents-feature.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/05/Intents-feature-1.png"
            alt="android_intents_title_image" width="250" height="384" class="alignright size-full wp-image-56698">
        </a>
    </p>
    <p>
        人们并不是漫无目的地游览世界，他们所做的大部分工作 - 从看电视，到购物，到编写下一个杀手级的app之后 - 都带有着某些目的，或是
        <i>
            意图
        </i>
        。
    </p>
    <p>
        Android的工作方式也大致如此。在app可以执行一个
        <em>
            动作
            action
        </em>
        之前，它需要知道该动作的目的，或是
        <em>
            intent
        </em>
        ，以正确地执行这个动作。
    </p>
    <p>
        事实证明Android和人类并没有太多的不同。:]
    </p>
    <p>
        在本教程中，你将利用
        <a href="http://developer.android.com/guide/components/intents-filters.html">
            Intent
        </a>
        的力量来创建自己的meme生成器。通过这个过程你会学到：
    </p>
    <ul>
        <li>
            什么是
            <code>
                Intent
            </code>
            ，以及它在Android中的广泛用途。
        </li>
        <li>
            如何使用
            <code>
                Intent
            </code>
            来创建并从其它app中检索内容供自己使用。
        </li>
        <li>
            如何接收或响应从其它app中发送来的
            <code>
                Intent
            </code>
            。
        </li>
    </ul>
    <p>
        如果你是一个Android开发的新手，强烈推荐你通过
        <a href="https://www.raywenderlich.com/161318/beginning-android-development-part-one-installing-android-studio"
        target="_blank">
            Beginning Android Development
        </a>
        和
        <a href="https://www.raywenderlich.com/174395/kotlin-for-android-an-introduction-2"
        target="_blank">
            Kotlin for Android
        </a>
        来掌握基本的工具和概念。你需要使用Android Studio 3.0或更高的版本。
    </p>
    <p>
        准备你最好的meme脸。本教程会增强你的Android开发水平超过9000点！！！ :]
    </p>
    <h2>
        入门
    </h2>
    <p>
        下载本教程的
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/memeify-starter.zip">
            初始项目
        </a>
        。
    </p>
    <p>
        你会在初始项目中找到一些XML的布局文件，以及相应的包含了一些模板代码的Activity，还有一些助手类，用来改变
        <code>
            Bitmap
        </code>
        的大小，一些资源诸如
        <code>
            Drawable
        </code>
        和
        <code>
            String
        </code>
        。你会在本教程中用到它们。
    </p>
    <p>
        如果你已打开了Android Studio，请点击
        <em>
            File/Import Project
        </em>
        并选择你刚下载后解压的初始项目的目录。如果尚未打开Android Studio，请打开它并在欢迎页上选择
        <em>
            Open an existing Android Studio project
        </em>
        ，然后同样地选择你刚下载后解压的初始项目的目录。如果弹出提示需要更新到最新的Gradle插件，请接收以进行更新。
    </p>
    <p>
        在继续后面的工作之前，花一些时间来熟悉项目吧。
        <code>
            TakePictureActivity
        </code>
        中包含一个
        <code>
            ImageView
        </code>
        ，你可以点击它来使用设备的相机拍一张照片。当点击
        <em>
            LETS MEMEIFY!
        </em>
        按钮后，你就会将
        <code>
            ImageView
        </code>
        中位图的文件路径传递给
        <code>
            EnterTextActivity
        </code>
        。这里是真正有趣的地方，你可以输入meme的文本，来把照片转入到下一个病毒式的meme！
    </p>
    <h2>
        创建你的第一个Intent
    </h2>
    <p>
        运行项目。你会看到如下的内容：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-180x320.png"
            alt="1. Starter Project Load App" width="281" height="500" class="aligncenter size-large wp-image-172114"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        目前还显得比较空，如果你遵循说明去点击ImageView，什么都不会发生。
    </p>
    <p>
        添加一些代码来让它变得更有趣一些。
    </p>
    <p>
        打开
        <code>
            TakePictureActivity.kt
        </code>
        ，并添加下列的代码到类底部的companion object中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">const <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> TAKE_PHOTO_REQUEST_CODE = <span class="hljs-number">1</span>
</pre>
    <p>
        这将用来在intent返回时对它进行识别 - 之后你将在本教程中了解更多关于它的内容。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：本教程假定你已熟悉了处理import警告的方法，因此不再明确地说明需要import某个包。如果想进行一下快速复习，当你看到import警告时，可以在Mac上按下
            <em>
                option + return
            </em>
            键或在PC上按
            <em>
                Alt + Enter
            </em>
            键来自动导入所需的包。
        </p>
    </div>
    <p>
        在
        <code>
            onClick()
        </code>
        方法下添加下列的代码，以及进行必要的import：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">takePictureWithCamera</span><span class="hljs-params">()</span></span> {
    <span class="hljs-comment">// 1</span>
    <span class="hljs-keyword">val</span> captureIntent = Intent(MediaStore.ACTION_IMAGE_CAPTURE)
    <span class="hljs-comment">// 2</span>
    <span class="hljs-keyword">val</span> imagePath = File(filesDir, <span class="hljs-string">"images"</span>)
    <span class="hljs-keyword">val</span> newFile = File(imagePath, <span class="hljs-string">"default_image.jpg"</span>)
    <span class="hljs-keyword">if</span> (newFile.exists()) {
      newFile.delete()
    } <span class="hljs-keyword">else</span> {
      newFile.parentFile.mkdirs()
    }
    selectedPhotoPath = getUriForFile(<span class="hljs-keyword">this</span>, BuildConfig.APPLICATION_ID + <span class="hljs-string">".fileprovider"</span>, newFile)
    <span class="hljs-comment">// 3</span>
    captureIntent.putExtra(android.provider.MediaStore.EXTRA_OUTPUT, selectedPhotoPath)
    <span class="hljs-keyword">if</span> (Build.VERSION.SDK_INT &gt;= Build.VERSION_CODES.LOLLIPOP) {
      captureIntent.addFlags(Intent.FLAG_GRANT_WRITE_URI_PERMISSION)
    } <span class="hljs-keyword">else</span> {
      <span class="hljs-keyword">val</span> clip = ClipData.newUri(contentResolver, <span class="hljs-string">"A photo"</span>, selectedPhotoPath)
      captureIntent.clipData = clip
      captureIntent.addFlags(Intent.FLAG_GRANT_WRITE_URI_PERMISSION)
    }

  }
</pre>
    <p>
        这个方法中有相当多的代码，我们一步一步来看。
    </p>
    <p>
        第一部分的代码声明了一个
        <code>
            Intent
        </code>
        对象。一切看起来都不错，但到底神马是intent？
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/05/Intents-thinking-1.png"
        alt="Intent" width="720" height="360" class="aligncenter size-medium wp-image-105587"
        style="margin-bottom:0">
    </p>
    <p>
        intent是关于工作或功能的抽象概念，可以在将来的某个时候被你的app执行。总之就是你的app在某个时候需要去做的事。最基本的intent是由下列的部分构成的：
    </p>
    <ul>
        <li>
            <em>
                Action
            </em>
            ：就是intent需要去完成的事，诸如拨打电话号码，打开一个URL地址，或是编辑一些数据。实际上它就是一个描述要完成什么事的字符串常量。
        </li>
        <li>
            <em>
                Data
            </em>
            ：它是支持intent执行操作的资源。在Android中，它是通过一个
            <em>
                Uniform Resource Identifier
            </em>
            或
            <code>
                Uri
            </code>
            对象来表示的 - 它是相应于一个特定资源的唯一标识符。intent所需的数据类型基于action的不同而不同。你不会去尝试一个拨打电话号码的intent 从图片中获取电话号码！:]
        </li>
    </ul>
    <p>
        这种将action和data结合起来的能力，就可以让Android准确地知道这个intent想要做什么，以及如何去做。就是这么得简单！
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/05/Intents-smile-1.png"
        alt="Smile" width="720" height="360" class="aligncenter size-medium wp-image-105589"
        style="margin-bottom:0">
    </p>
    <p>
        回到
        <code>
            takePictureWithCamera()
        </code>
        ，你会看到你刚创建的intent使用了
        <code>
            ACTION_IMAGE_CAPTURE
        </code>
        action。可能你早已猜到了它为为你拍拍一张照片，这这正是meme生成器所需要的！
    </p>
    <p>
        第二部分的代码，则为图片生成了一个临时的
        <code>
            文件
        </code>
        。初始项目中已为你做好了必要的处理，但如果想明白它是如何工作的话，可以查看一下activity中的代码。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：你可能注意到了，变量selectedPhotoPath被添加了一个.fileprovider的后缀。File Provider是一个为你的app提供文件的特别的方式，并确保这个过程以安全的方式完成。你可以查看Android的Manifest文件，你会发现Memeify就使用了它。你可以在
            <a href="https://developer.android.com/reference/android/support/v4/content/FileProvider.html">
                这里
            </a>
            阅读更多关于它的内容。
        </p>
    </div>
    <h3>
        探索额外的内容
    </h3>
    <p>
        代码的第三部分，则为新创建的intent添加了一个
        <em>
            Extra
        </em>
        。
    </p>
    <p>
        什么是extra？？
    </p>
    <p>
        Extra是一个key-value对的表单，用来给你的intent额外的信息以完成它的action。就像人类一样，如果做一件事之前把该准备的都准备好了，就容易把事情做好。Android中的intent也是这样，一个很好的intent应该把它所需的extra也同时准备好！
    </p>
    <p>
        一个intent能够接受的extra的类型，可以根据action的不同而不同。这非常类似于你提供给action的数据的类型。
    </p>
    <p>
        一个很好的例子，就是创建一个action为
        <code>
            ACTION_WEB_SEARCH
        </code>
        的intent。这个action可以接受一个叫做
        <code>
            QUERY
        </code>
        的extra，它就是你想要搜索的查询字符串。一个extra的key通常都是一个字符串的常量，因为他的名字不应该被改变。启动这个intent，就会展示Google的搜索页面和相应查询到的结果。
    </p>
    <p>
        再来看一下
        <code>
            captureIntent.putExtra()
        </code>
        这行，
        <code>
            EXTRA_OUTPUT
        </code>
        指定了用相机拍到的照片应当保存到的位置 - 在本例中，就是你之前创建的空文件的
        <code>
            Uri
        </code>
        位置。
    </p>
    <h3>
        将你的Intent付诸行动
    </h3>
    <p>
        现在你已经准备好了intent，以及一个典型intent的完整的心理模型，它看起来应该像是这样：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent-500x500.png"
            alt="Contents of a Intent" width="500" height="500" class="aligncenter size-large wp-image-103211"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent.png 500w, https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2015/04/Contents-of-a-Intent-128x128.png 128w"
            sizes="(max-width: 500px) 100vw, 500px">
        </a>
    </p>
    <p>
        这里没有剩余太多的事要做，除了添加最后一行代码
        <code>
            takePictureWithCamera()
        </code>
        来让intent付诸实现。添加下列的内容到该方法的底部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">startActivityForResult(captureIntent, TAKE_PHOTO_REQUEST_CODE)
</pre>
    <p>
        这行代码请求Android启动了一个由action指定
        <code>
            captureIntent
        </code>
        指定的activity：以捕捉照片并保存到文件中。当activity实现了intent的动作之后，你还想检索得到的图片。你之前指定的常量
        <code>
            TAKE_PHOTO_REQUEST_CODE
        </code>
        ，将用来识别它返回的intent。
    </p>
    <p>
        接下来，在
        <code>
            onClick()
        </code>
        方法中，将
        <code>
            R.id.picture_imageview
        </code>
        分支中，
        <code>
            when
        </code>
        语句中的空闭包替换为调用
        <code>
            takePictureWithCamera()
        </code>
        方法。最终的代码看起来应当是下面这个样子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">R.id.pictureImageview -&gt; takePictureWithCamera()
</pre>
    <p>
        当你点击
        <code>
            ImageView
        </code>
        时，就会调用
        <code>
            takePictureWithCamera()
        </code>
        方法。
    </p>
    <p>
        是时候来检验你的劳动果实了！运行项目。点击
        <code>
            ImageView
        </code>
        来调用相机：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/trampoline-camera-snap.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/trampoline-camera-snap-180x320.png"
            alt="5. Camera Intent Working" width="281" height="500" class="aligncenter size-large wp-image-172120"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/trampoline-camera-snap-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/trampoline-camera-snap-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/trampoline-camera-snap.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        现在可以来拍一张照片，但拍完后并没有做任何的事情！你将在下一节对它进行处理。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：如果你是在模拟器中运行的app，你可能需要在AVD上对相机进行设置。点击
            <em>
                Tools/Android/AVD Manager
            </em>
            ，接着点击你想要使用的虚拟设备右侧的
            <em>
                绿色铅笔
            </em>
            。然后点击窗口底部左侧的
            <em>
                Show Advanced Settings
            </em>
            。在
            <em>
                Camera
            </em>
            中，确保所有可用相机的下拉列表都被设置为
            <em>
                Emulated
            </em>
            或
            <em>
                Webcam0
            </em>
            。
        </p>
    </div>
    <h2>
        隐式意图
    </h2>
    <p>
        If you’re running the app on a physical device with a number of camera-centric
        apps, you might have noticed something unexpected:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/multipl-camera-select.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/multipl-camera-select-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-172117"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/multipl-camera-select-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/multipl-camera-select-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/multipl-camera-select.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        You get prompted to choose which app should handle the intent.
    </p>
    <p>
        When you create an intent, you can be as explicit or as implicit as you
        like with what the intent should use to complete its action.
        <em>
            ACTION_IMAGE_CAPTURE
        </em>
        is a perfect example of an
        <em>
            Implicit Intent
        </em>
        .
    </p>
    <p>
        Implicit intents let Android developers give users the power of choice.
        If they have a particular app they like to use to perform a certain task,
        would it be so wrong to use some of its features for your own benefit?
        At the very least, it definitely saves you from reinventing the wheel in
        your own app.
    </p>
    <p>
        An implicit Intent informs Android that it needs an app to handle the
        intent’s action when it starts. The Android system then compares the given
        intent against all apps installed on the device to see which ones can handle
        that action, and therefore process that intent. If more than one can handle
        the intent, the user is prompted to choose one:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-500x500.jpg"
        width="500" height="500" class="aligncenter size-large wp-image-105603"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-500x500.jpg 500w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-250x250.jpg 250w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-320x320.jpg 320w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-32x32.jpg 32w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-64x64.jpg 64w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-96x96.jpg 96w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-128x128.jpg 128w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera.jpg 800w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        If only one app responds, the intent automatically takes the user to that
        app to perform the action. If there are no apps to perform that action,
        then Android will return nothing, leaving you with a null value that will
        cause your app to crash! :[
    </p>
    <p>
        You can prevent this by checking the result to ensure that at least one
        app responded to the action before attempting to start it, or in this case
        you can also state the app can only be installed on devices that have a
        camera by declaring the necessary hardware requirements by adding the following
        line to
        <em>
            AndroidManifest.xml
        </em>
        :
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">uses-feature</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.hardware.camera"</span> /&gt;</span></pre>
    <p>
        The starter project opts for the device restriction method.
    </p>
    <p>
        So you have an implicit intent set up to take a photo, but you don’t yet
        have a way to access that photo in your app. Your meme generator isn’t
        going to get far without photos!
    </p>
    <p>
        Add the following new method just below
        <code>
            takePictureWithCamera()
        </code>
        in
        <code>
            TakePictureActivity
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onActivityResult</span><span class="hljs-params">(requestCode: <span class="hljs-type">Int</span>, resultCode: <span class="hljs-type">Int</span>, <span class="hljs-keyword">data</span>: <span class="hljs-type">Intent</span>?)</span></span> {
    <span class="hljs-keyword">super</span>.onActivityResult(requestCode, resultCode, <span class="hljs-keyword">data</span>)
    <span class="hljs-keyword">if</span> (requestCode == TAKE_PHOTO_REQUEST_CODE &amp;&amp; resultCode == Activity.RESULT_OK) {
      <span class="hljs-comment">//setImageViewWithImage()</span>
    }
  }
</pre>
    <p>
        The above method only executes when an activity started by
        <code>
            startActivityForResult()
        </code>
        in
        <code>
            takePictureWithCamera()
        </code>
        has finished and returns to your app.
    </p>
    <p>
        The
        <code>
            if
        </code>
        statement above matches the returned
        <code>
            requestCode
        </code>
        against the constant you passed in (
        <code>
            TAKE_PHOTO_REQUEST_CODE
        </code>
        ) to ensure this is your intent. You also check that the
        <code>
            resultCode
        </code>
        is
        <code>
            RESULT_OK
        </code>
        ; this is simply an Android constant that indicates successful execution.
    </p>
    <p>
        If everything does go well, then you can assume your image is ready for
        use, so you call
        <code>
            setImageViewWithImage()
        </code>
        .
    </p>
    <p>
        Time to define that method!
    </p>
    <p>
        First, at the top of
        <code>
            TakePictureActivity
        </code>
        , add the following
        <code>
            boolean
        </code>
        variable:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> pictureTaken: <span class="hljs-built_in">Boolean</span> = <span class="hljs-literal">false</span>
</pre>
    <p>
        This tracks whether you have taken a photo, which is useful in the event
        you take more than one photo. You’ll use this variable shortly.
    </p>
    <p>
        Next, add the following right after
        <code>
            onActivityResult()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setImageViewWithImage</span><span class="hljs-params">()</span></span> {
    <span class="hljs-keyword">val</span> photoPath: Uri = selectedPhotoPath ?: <span class="hljs-keyword">return</span>
    pictureImageview.post {
      <span class="hljs-keyword">val</span> pictureBitmap = BitmapResizer.shrinkBitmap(
          <span class="hljs-keyword">this</span><span class="hljs-symbol">@TakePictureActivity</span>,
          photoPath,
          pictureImageview.width,
          pictureImageview.height
      )
      pictureImageview.setImageBitmap(pictureBitmap)
    }
    lookingGoodTextView.visibility = View.VISIBLE
    pictureTaken = <span class="hljs-literal">true</span>
  }
</pre>
    <p>
        <code>
            BitmapResizer
        </code>
        is a helper class bundled with the starter project to make sure the
        <code>
            Bitmap
        </code>
        you retrieve from the camera is scaled to the correct size for your device’s
        screen. Although the device can scale the image for you, resizing it in
        this way is more memory efficient.
    </p>
    <p>
        With
        <code>
            setImageViewWithImage()
        </code>
        now ready, uncomment this line that calls it, within
        <code>
            onActivityResult()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// setImageViewWithImage()</span></pre>
    <p>
        Build and run. Select your favorite camera app – if prompted – and take
        another photo.
    </p>
    <p>
        This time, the photo should scale to the appropriate size given your display
        and show up in the
        <code>
            ImageView
        </code>
        :
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-with-pic-2.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-with-pic-2-281x500.png"
            alt="memefy screenshot" width="281" height="500" class="aligncenter size-large wp-image-172113"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-with-pic-2-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-with-pic-2-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-with-pic-2.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        You’ll also see a
        <code>
            TextView
        </code>
        underneath that compliments you on your excellent photography skills.
        It’s always nice to be polite. :]
    </p>
    <h2>
        Explicit Intents
    </h2>
    <p>
        It’s nearly time to build phase two of your meme generator, but first
        you need to get your picture over to the next activity since you’re a little
        strapped for screen real estate here.
    </p>
    <p>
        In the
        <em>
            Constants.kt
        </em>
        , add the following constants just below the comment line:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">const <span class="hljs-keyword">val</span> IMAGE_URI_KEY = <span class="hljs-string">"IMAGE_URI"</span>
const <span class="hljs-keyword">val</span> BITMAP_WIDTH = <span class="hljs-string">"BITMAP_WIDTH"</span>
const <span class="hljs-keyword">val</span> BITMAP_HEIGHT = <span class="hljs-string">"BITMAP_HEIGHT"</span>
</pre>
    <p>
        These will be used as keys for the extras you’ll pass to an intent on
        the next screen.
    </p>
    <p>
        Now, add the following method to the bottom of
        <code>
            TakePictureActivity
        </code>
        , adding any imports as necessary:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">moveToNextScreen</span><span class="hljs-params">()</span></span> {
    <span class="hljs-keyword">if</span> (pictureTaken) {
      <span class="hljs-keyword">val</span> nextScreenIntent = Intent(<span class="hljs-keyword">this</span>, EnterTextActivity::<span class="hljs-class"><span class="hljs-keyword">class</span>.<span class="hljs-title">java</span>).<span class="hljs-title">apply</span> </span>{
        putExtra(IMAGE_URI_KEY, selectedPhotoPath)
        putExtra(BITMAP_WIDTH, pictureImageview.width)
        putExtra(BITMAP_HEIGHT, pictureImageview.height)
      }

      startActivity(nextScreenIntent)
    } <span class="hljs-keyword">else</span> {
      Toaster.show(<span class="hljs-keyword">this</span>, R.string.select_a_picture)
    }
  }
</pre>
    <p>
        Here you check
        <code>
            pictureTaken
        </code>
        to see if it’s
        <code>
            true
        </code>
        , which indicates your
        <code>
            ImageView
        </code>
        has a
        <code>
            Bitmap
        </code>
        from the camera. If you don’t have a
        <code>
            Bitmap
        </code>
        , then your activity will briefly show a
        <code>
            Toast
        </code>
        message telling you to go take a photo – method
        <code>
            show
        </code>
        from the
        <code>
            Toaster
        </code>
        class makes showing toasts just a tiny bit easier. If
        <code>
            pictureTaken
        </code>
        is
        <code>
            true
        </code>
        then you create an intent for the next activity, and set up the necessary
        extras, using the constants you just defined as the keys.
    </p>
    <p>
        Next, in the
        <code>
            onClick()
        </code>
        function, replace the empty closure in the
        <code>
            when
        </code>
        statement for the
        <code>
            R.id.enter_text_button
        </code>
        branch condition with a call to the
        <code>
            moveToNextScreen()
        </code>
        function. The resulting line of code should look like the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">R.id.enterTextButton -&gt; moveToNextScreen()
</pre>
    <p>
        Build and run. Tap
        <em>
            LETS MEMEIFY!
        </em>
        without first taking a photo and you’ll see the toast appear:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-toast.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-toast-281x500.png"
            alt="Toast Message Appears" width="281" height="500" class="aligncenter size-large wp-image-172112"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-toast-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-toast-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage1-toast.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        If a photo
        <i>
            is
        </i>
        taken, then
        <code>
            moveToNextScreen()
        </code>
        proceeds to create an intent for the text entry activity. It also attaches
        some
        <code>
            Extra
        </code>
        s to the intent, such as the
        <code>
            Uri
        </code>
        path for the
        <code>
            Bitmap
        </code>
        and the height and width of the
        <code>
            Bitmap
        </code>
        as it’s displayed on the screen. These will come in useful in the next
        activity.
    </p>
    <p>
        You’ve just created your first
        <em>
            explicit Intent
        </em>
        . Compared to implicit intents, explicit intents are a lot more conservative;
        this is because they describe a specific component that will be created
        and used when the intent starts. This could be another activity that is
        a part of your app, or a specific
        <code>
            Service
        </code>
        in your app, such as one that starts to download a file in the background.
    </p>
    <p>
        This intent is constructed by providing the
        <code>
            Context
        </code>
        from which the intent was created (in this case,
        <code>
            this
        </code>
        ) along with the class the intent needs to run (
        <code>
            EnterTextActivity::class.java
        </code>
        ). Since you’ve explicitly stated how the intent gets from A to B, Android
        simply complies. The user has no control over how the intent is completed:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-500x500.jpg"
        alt="intent_activity" width="500" height="500" class="aligncenter size-large wp-image-105605"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-500x500.jpg 500w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-250x250.jpg 250w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-320x320.jpg 320w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-32x32.jpg 32w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-64x64.jpg 64w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-96x96.jpg 96w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-128x128.jpg 128w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity.jpg 800w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        Build and run. Repeat the process of taking a photo, but this time tap
        <em>
            LETS MEMEIFY!
        </em>
        . Your explicit intent will kick into action and take you to the next
        activity:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-no-pic.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-no-pic-281x500.png"
            alt="11. Enter Text Activity" width="281" height="500" class="aligncenter size-large wp-image-172116"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-no-pic-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-no-pic-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-no-pic.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        The starter project has already has this activity created and declared
        in
        <em>
            AndroidManifest.xml
        </em>
        , so you don’t have to create it yourself.
    </p>
    <h2>
        Handling Intents
    </h2>
    <p>
        Looks like that intent worked like a charm. But where are those
        <code>
            Extra
        </code>
        s you sent across? Did they take a wrong turn at the last memory buffer?
        Time to find them and put them to work.
    </p>
    <p>
        Add the following code at the end of
        <code>
            onCreate()
        </code>
        in the
        <em>
            EnterTextActivity
        </em>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">pictureUri = intent.getParcelableExtra&lt;Uri&gt;(IMAGE_URI_KEY)
<span class="hljs-keyword">val</span> bitmapWidth = intent.getIntExtra(BITMAP_WIDTH, <span class="hljs-number">100</span>)
<span class="hljs-keyword">val</span> bitmapHeight = intent.getIntExtra(BITMAP_HEIGHT, <span class="hljs-number">100</span>)

pictureUri?.let {
  <span class="hljs-keyword">val</span> selectedImageBitmap = BitmapResizer.shrinkBitmap(<span class="hljs-keyword">this</span>, it, bitmapWidth, bitmapHeight)
  selectedPictureImageview.setImageBitmap(selectedImageBitmap)
}
</pre>
    <p>
        When you create the activity, you assign the
        <code>
            Uri
        </code>
        passed from the previous activity to
        <code>
            pictureUri
        </code>
        by accessing the
        <code>
            Intent
        </code>
        via
        <code>
            intent
        </code>
        . Once you have access to the intent, you can access its
        <code>
            Extra
        </code>
        values.
    </p>
    <p>
        Since variables and objects come in various forms, you have multiple methods
        to access them from the intent. To access the
        <code>
            Uri
        </code>
        object above, for example, you need to use
        <code>
            getParcelableExtra
            <uri>
                ()
            </uri>
        </code>
        . Other
        <code>
            Extra
        </code>
        methods exist for other variables such as strings and primitive data types.
    </p>
    <p>
        <code>
            getIntExtra()
        </code>
        , similarly to other methods that return primitives, also allows you to
        define a default value. These are used when a value isn’t supplied, or
        when the key is missing from the provided
        <code>
            Extra
        </code>
        s.
    </p>
    <p>
        Once you’ve retrieved the necessary
        <code>
            Extra
        </code>
        s, create a
        <code>
            Bitmap
        </code>
        from the
        <code>
            Uri
        </code>
        sized by the
        <code>
            BITMAP_WIDTH
        </code>
        and
        <code>
            BITMAP_HEIGHT
        </code>
        values you passed. Finally, you set the
        <code>
            ImageView
        </code>
        image source to the bitmap to display the photo.
    </p>
    <p>
        In addition to displaying the
        <code>
            ImageView
        </code>
        , this screen also contains two
        <code>
            EditText
        </code>
        views where the user can enter their meme text. The starter project does
        the heavy lifting for you by taking the text from those views and compositing
        it onto the photo.
    </p>
    <p>
        The only thing you need to do is to flesh out
        <code>
            onClick()
        </code>
        . Update the line to the
        <code>
            R.id.write_text_to_image_button
        </code>
        branch condition:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">R.id.writeTextToImageButton -&gt; createMeme()
</pre>
    <p>
        Drumroll please. Build and Run. Repeat the usual steps to take a photo,
        and then enter your incredibly witty meme text on the second screen and
        tap
        <em>
            LETS MEMEIFY!
        </em>
        :
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-memed.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-memed-281x500.png"
            alt="Image Memeified" width="281" height="500" class="aligncenter size-large wp-image-172115"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-memed-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-memed-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/memify-stage2-memed.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        You’ve just created your own meme generator! Don’t celebrate too long,
        though — there are a few bits of polish that you need to add to the app.
    </p>
    <h2>
        Broadcast Intents
    </h2>
    <p>
        It would be nice to save your shiny new meme so you can share it with
        the world. It’s not going to go viral all on its own! :]
    </p>
    <p>
        Fortunately the starter project has got it covered for you — you only
        need to tie things together.
    </p>
    <p>
        Add the following code to
        <code>
            saveImageToGallery()
        </code>
        , just below the
        <code>
            try
        </code>
        block before the second
        <code>
            Toaster.show()
        </code>
        call:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> mediaScanIntent = Intent(Intent.ACTION_MEDIA_SCANNER_SCAN_FILE)
mediaScanIntent.<span class="hljs-keyword">data</span> = Uri.fromFile(imageFile)
sendBroadcast(mediaScanIntent)
</pre>
    <p>
        This intent uses the
        <code>
            ACTION_MEDIA_SCANNER_SCAN_FILE
        </code>
        action to ask the Android’s media database to add the image’s
        <code>
            Uri
        </code>
        . That way, any apps that access the media database can use the image
        via its Uri.
    </p>
    <p>
        The
        <code>
            ACTION_MEDIA_SCANNER_SCAN_FILE
        </code>
        action also requires the intent to have some attached data in the form
        of a
        <code>
            Uri
        </code>
        , which comes from the
        <code>
            File
        </code>
        object to which you save the
        <code>
            Bitmap
        </code>
        .
    </p>
    <p>
        Finally, you broadcast the intent across Android so that any interested
        parties — in this case, the media scanner — can act upon it. Since the
        media scanner doesn’t have a user interface, you can’t start an activity
        so you simply broadcast the intent instead.
    </p>
    <p>
        Now, update the
        <code>
            R.id.save_image_button
        </code>
        branch condition in the
        <code>
            onClick()
        </code>
        function to the following:
    </p>
    <pre lang="java" class="language-java hljs">R.id.saveImageButton -&gt; askForPermissions()
</pre>
    <p>
        When the user hits
        <em>
            SAVE IMAGE
        </em>
        the above code checks for
        <code>
            WRITE_EXTERNAL_STORAGE
        </code>
        permission. If it’s not granted on Android Marshmallow and above, the
        method politely asks the user to grant it. Otherwise, if you are allowed
        to write to the external storage, it simply passes control to
        <code>
            saveImageToGallery()
        </code>
        .
    </p>
    <p>
        The code in
        <code>
            saveImageToGallery()
        </code>
        performs some error handling and, if everything checks out, kicks off
        the intent.
    </p>
    <p>
        Build and run. Take a photo, add some stunningly brilliant meme text,
        tap
        <em>
            LETS MEMEIFY!
        </em>
        , and then tap
        <em>
            SAVE IMAGE
        </em>
        once your image is ready.
    </p>
    <p>
        Now close the app and open the
        <em>
            Photos
        </em>
        app. If you’re using the emulator then open the
        <em>
            Gallery
        </em>
        app. You should be able to see your new image in all its meme-ified glory:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/photos-snap.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/photos-snap-281x500.png"
            alt="image from photos" width="281" height="500" class="aligncenter size-large wp-image-172118"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/photos-snap-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/photos-snap-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/photos-snap.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        Your memes can now escape the confines of your app and are available for
        you to post to social media or share in any manner of your choosing. Your
        meme generator is complete!
    </p>
    <h2>
        Intent Filtering
    </h2>
    <p>
        By now you should have a good idea of how to use the right intent for
        the right job. However, there’s another side to the story of the faithful
        intent: how your app knows which intent requests to respond to when an
        implicit intent is sent.
    </p>
    <p>
        Open
        <em>
            AndroidManifest.xml
        </em>
        found in
        <em>
            app/manifests
        </em>
        , and in the first
        <code>
            activity
        </code>
        element you should see the following:
    </p>
    <pre code="xml" class="hljs xml"><span class="hljs-tag">&lt;<span class="hljs-name">activity</span>
    <span class="hljs-attr">android:name</span>=<span class="hljs-string">".TakePictureActivity"</span>
    <span class="hljs-attr">android:label</span>=<span class="hljs-string">"@string/app_name"</span>
    <span class="hljs-attr">android:screenOrientation</span>=<span class="hljs-string">"portrait"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">intent-filter</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">action</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.action.MAIN"</span> /&gt;</span>

        <span class="hljs-tag">&lt;<span class="hljs-name">category</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.category.LAUNCHER"</span> /&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">intent-filter</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">activity</span>&gt;</span>
</pre>
    <p>
        The key here is the
        <code>
            intent-filter
        </code>
        element. An
        <em>
            Intent Filter
        </em>
        enables parts of your app to respond to implicit intents.
    </p>
    <p>
        These behave like a banner when Android tries to satisfy an implicit intent
        sent by another app. An app can have multiple intent filters, which it
        waves about wildly, hoping its intent filter satisfies what Android is
        looking for:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/04/app_intent.jpg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/04/app_intent-302x320.jpg"
            alt="IntentFiltering" width="302" height="320" class="aligncenter size-medium wp-image-104897"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/04/app_intent-302x320.jpg 302w, https://koenig-media.raywenderlich.com/uploads/2015/04/app_intent.jpg 381w"
            sizes="(max-width: 302px) 100vw, 302px">
        </a>
    </p>
    <p>
        It’s kind of like online dating for intents and apps. :]
    </p>
    <p>
        To make sure it’s the right app for the intent, the intent filter provides
        three things:
    </p>
    <ol>
        <li>
            <em>
                Intent Action
            </em>
            : The action the app can fulfill; this is similar to the way the camera
            app fulfills the
            <code>
                ACTION_IMAGE_CAPTURE
            </code>
            action for your app.
        </li>
        <li>
            <em>
                Intent Data
            </em>
            : The type of data the intent can accept. This ranges from specific file
            paths, to ports, to MIME types such as images and video. You can set one
            or more attributes to control how strict or lenient you are with the data
            from an intent that your app can handle.
        </li>
        <li>
            <em>
                Intent Category
            </em>
            : The categories of intents that are accepted; this is an additional way
            to specify which Actions can respond to an implicit Intent.
        </li>
    </ol>
    <p>
        It would be AWESOME to offer Memeify as an implicit intent to interacting
        with images from other apps — and it’s surprisingly simple to do.
    </p>
    <p>
        Add the following code directly underneath the first intent filter in
        your
        <em>
            AndroidManifest.xml
        </em>
        file:
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">intent-filter</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">action</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.action.SEND"</span> /&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">category</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.category.DEFAULT"</span> /&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">data</span> <span class="hljs-attr">android:mimeType</span>=<span class="hljs-string">"@string/image_mime_type"</span> /&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">intent-filter</span>&gt;</span>
</pre>
    <p>
        Your new intent filter specifies that your app will look for
        <code>
            SEND
        </code>
        action from an implicit intent. You use the default category as you don’t
        have any special use cases, and you’re looking only for image MIME data
        types.
    </p>
    <p>
        Now open
        <em>
            TakePictureActivity.kt
        </em>
        and add the following to the end of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">checkReceivedIntent</span><span class="hljs-params">()</span></span> {
    <span class="hljs-keyword">val</span> imageReceivedIntent = intent
    <span class="hljs-keyword">val</span> intentAction = imageReceivedIntent.action
    <span class="hljs-keyword">val</span> intentType = imageReceivedIntent.type

    <span class="hljs-keyword">if</span> (Intent.ACTION_SEND == intentAction &amp;&amp; intentType != <span class="hljs-literal">null</span>) {
      <span class="hljs-keyword">if</span> (intentType.startsWith(MIME_TYPE_IMAGE)) {
        selectedPhotoPath = imageReceivedIntent.getParcelableExtra&lt;Uri&gt;(Intent.EXTRA_STREAM)
        setImageViewWithImage()
      }
    }
  }
</pre>
    <p>
        Here you get the
        <code>
            Intent
        </code>
        that started the activity and retrieve its action and type. Then you compare
        these to what you declared in your intent filter, which is a data source
        with the MIME type of an image.
    </p>
    <p>
        If it’s a match, then you get the image’s
        <code>
            Uri
        </code>
        , query the
        <code>
            Uri
        </code>
        for the
        <code>
            Bitmap
        </code>
        using a helper method included with the starter project, and the finally
        ask the
        <code>
            ImageView
        </code>
        to display the retrieved
        <code>
            Bitmap
        </code>
        .
    </p>
    <p>
        Next add the following line at the end of
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">checkReceivedIntent()
</pre>
    <p>
        The above code ensures that you will check if there is an intent every
        time the activity is created.
    </p>
    <p>
        Build and run. Then back out to the home screen, and go to the Photos
        app, or the Gallery app if you’re using the emulator. Choose any photo,
        and tap the share button. You should see
        <em>
            Memeify
        </em>
        among the presented options:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/share.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/share-281x500.png"
            alt="share image" width="281" height="500" class="aligncenter size-large wp-image-172124"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/share-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/share-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/share.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        Memeify is ready and waiting to receive your photo! Tap
        <em>
            Memeify
        </em>
        and see what happens – Memeify launches with the selected photo already
        displayed in the
        <code>
            ImageView
        </code>
        .
    </p>
    <p>
        Your app is now receiving intents like a boss!
    </p>
    <h2>
        Where to Go From Here?
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
        You can download the completed project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/memeify-final.zip">
            here
        </a>
        .
    </p>
    <p>
        Intents are one of the fundamental building blocks of Android. Much of
        the openness and intercommunication that Android takes pride in just wouldn’t
        be possible without them. Learn how to use intents well and you will have
        made a very powerful ally indeed.
    </p>
    <p>
        If you want to learn more about intents and intent filters then check
        out Google’s
        <a href="http://developer.android.com/guide/components/intents-filters.html"
        target="_blank">
            Intents
        </a>
        documentation.
    </p>
</div>