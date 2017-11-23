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
        正如你在很多相机相关的app上见到的一样，出现了一些意料之外的情况：
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
        系统会提示你选择用哪个app来处理这个intent。
    </p>
    <p>
        当你创建一个intent时，你可以在显式和隐式之间进行选择来完成这个action。
        <em>
            ACTION_IMAGE_CAPTURE
        </em>
        是一个
        <em>
            隐式Intent
        </em>
        的完美例子。
    </p>
    <p>
        隐式intent让Android开发者能够赋予用户进行选择的权力。他们希望使用特定的app来执行这个任务。为了自己的目的，去使用其它app的一些功能是错误的？至少，它绝对可以让你避免在自己的app中重新制造轮子。
    </p>
    <p>
        一个隐式意图会在它启动的时候，通知Android需要通过一个app来处理它的action。之后，Android系统就会将给它和所有设备上已安装的app进行比对，找出哪个可以处理这个action，并进行处理。如果有多个app可以处理，就提示用户从中选择一个：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-500x500.jpg"
        width="500" height="500" class="aligncenter size-large wp-image-105603"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-500x500.jpg 500w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-250x250.jpg 250w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-320x320.jpg 320w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-32x32.jpg 32w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-64x64.jpg 64w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-96x96.jpg 96w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera-128x128.jpg 128w, https://koenig-media.raywenderlich.com/uploads/2015/05/intents_needcamera.jpg 800w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        如果只有一个app能响应，intent就会把用户带到这个app上来执行它的action。如果没有任何app可以响应，Android就无法返回任何内容，造成你app的崩溃！:[
    </p>
    <p>
        你可以通过在尝试启动intent之前，检查至少有一个app可以响应这个action来避免崩溃的发生。或是通过在
        <em>
            AndroidManifest.xml
        </em>
        中添加下列的代码，来将app声明为只能安装在带有相机硬件的设备上：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">uses-feature</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.hardware.camera"</span> /&gt;</span></pre>
    <p>
        这样项目就选择了设备受限制的方法。
    </p>
    <p>
        现在你有了一个隐式的intent来拍摄照片，但还没有办法在你的app中访问这张照片。你的meme生成器不会这样一直没照片下去！
    </p>
    <p>
        在
        <code>
            TakePictureActivity
        </code>
        中
        <code>
            takePictureWithCamera()
        </code>
        之下，添加下列的方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onActivityResult</span><span class="hljs-params">(requestCode: <span class="hljs-type">Int</span>, resultCode: <span class="hljs-type">Int</span>, <span class="hljs-keyword">data</span>: <span class="hljs-type">Intent</span>?)</span></span> {
    <span class="hljs-keyword">super</span>.onActivityResult(requestCode, resultCode, <span class="hljs-keyword">data</span>)
    <span class="hljs-keyword">if</span> (requestCode == TAKE_PHOTO_REQUEST_CODE &amp;&amp; resultCode == Activity.RESULT_OK) {
      <span class="hljs-comment">//setImageViewWithImage()</span>
    }
  }
</pre>
    <p>
        当在
        <code>
            takePictureWithCamera()
        </code>
        中，通过调用
        <code>
            startActivityForResult()
        </code>
        执行任务，完成后回到你的app时，就会调用上面的方法。
    </p>
    <p>
        上述的
        <code>
            if
        </code>
        语句，会将返回的
        <code>
            requestCode
        </code>
        与你的常量（
        <code>
            TAKE_PHOTO_REQUEST_CODE
        </code>
        ）进行比较，以确保这是你的intent。你还检查了
        <code>
            resultCode
        </code>
        是否为
        <code>
            RESULT_OK
        </code>
        ，它是一个简单的Android常量，表示成功地执行了任务。
    </p>
    <p>
        如果一切顺利，就可以假定你的图片已准备好被使用了，因此调用
        <code>
            setImageViewWithImage()
        </code>
        。
    </p>
    <p>
        是时候来定义这个方法了！
    </p>
    <p>
        首先，在
        <code>
            TakePictureActivity
        </code>
        的顶部，添加下列的
        <code>
            boolean
        </code>
        变量：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">var</span> pictureTaken: <span class="hljs-built_in">Boolean</span> = <span class="hljs-literal">false</span>
</pre>
    <p>
        它会跟踪你是否拍摄了一张照片，在你拍摄超过了一张照片的时候，会非常得有用。你很快就会用到这个变量。
    </p>
    <p>
        接下来，在
        <code>
            onActivityResult()
        </code>
        之后，添加下列的内容：
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
        是一个由初始项目提供的助手类，用来确保从相机中获取的
        <code>
            Bitmap
        </code>
        ，尺寸符合你设备的屏幕。尽管设备可以为你缩放图片，但用这种方式来修饰图片可以更加节约内容。
    </p>
    <p>
        <code>
            setImageViewWithImage()
        </code>
        方法OK后，在 
        <code>
            onActivityResult()
        </code>
        中取消这行代码的注释来调用它：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// setImageViewWithImage()</span></pre>
    <p>
        运行项目。选在你最喜欢的相机app - 如果被提示的话 - 再拍一张照片。
    </p>
    <p>
        这次，照片会被缩放到合适的尺寸，并展示在
        <code>
            ImageView
        </code>
        上：
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
        你还会看到下面有一个
        <code>
            TextView
        </code>
        在称赞你杰出的摄影技巧。有礼貌总是很好的。:]
    </p>
    <h2>
        显式意图
    </h2>
    <p>
        现在基本已经到了构建meme生成器的第二阶段了，但首先你需要把照片传递给下一个activity，因为这里的屏幕空间有一定的限制。
    </p>
    <p>
        在
        <em>
            Constants.kt
        </em>
        中，注释的下方添加如下的常量：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">const <span class="hljs-keyword">val</span> IMAGE_URI_KEY = <span class="hljs-string">"IMAGE_URI"</span>
const <span class="hljs-keyword">val</span> BITMAP_WIDTH = <span class="hljs-string">"BITMAP_WIDTH"</span>
const <span class="hljs-keyword">val</span> BITMAP_HEIGHT = <span class="hljs-string">"BITMAP_HEIGHT"</span>
</pre>
    <p>
        这些将被当做你传递给下一页的intent的键。
    </p>
    <p>
        现在，添加下列的方法到
        <code>
            TakePictureActivity
        </code>
        底部，并添加相应的import：
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
        首先检查
        <code>
            pictureTaken
        </code>
        是否为
        <code>
            true
        </code>
        ，它表示你的
        <code>
            ImageView
        </code>
        是否含有来自相机的
        <code>
            Bitmap
        </code>
        。如果没有的话，就提示一个简短的
        <code>
            Toast
        </code>
        消息请求拍一张照片 - 来自
        <code>
            Toaster
        </code>
        类中的方法
        <code>
            show
        </code>
        可以方便地用来展示toast消息。
        如果
        <code>
            pictureTaken
        </code>
        为
        <code>
            true
        </code>
        的话，就为下个activity创建一个intent，并使用你刚设置的key来设置必要的extra。
    </p>
    <p>
        接下来，在
        <code>
            onClick()
        </code>
        方法中，将
        <code>
            R.id.enter_text_button
        </code>
        分支中的
        <code>
            when
        </code>
        语句替换为调用
        <code>
            moveToNextScreen()
        </code>
        方法。完成后的代码如下所示：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">R.id.enterTextButton -&gt; moveToNextScreen()
</pre>
    <p>
        运行项目。在没有拍照时点击
        <em>
            LETS MEMEIFY!
        </em>
        ，你会看到如下的toast提示：
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
        如果已获取到了照片，之后
        <code>
            moveToNextScreen()
        </code>
        就会创建一个新的intent，以进入用于文本输入的activity。同样它也附有一些
        <code>
            Extra
        </code>
        ，诸如
        <code>
            Bitmap
        </code>
        的
        <code>
            Uri
        </code>
        路径及它展示在屏幕上时的高和宽。这些信息对于下一个activity都非常得有用。
    </p>
    <p>
        你已创建了第一个
        <em>
            显式Intent
        </em>
        。相对于隐式intents，它更加得保守。这是因为它描述的是一个特定的组件，这个组件会在intent启动时被创建和使用。它可能是你app中的另一个activity或是
        <code>
            Service
        </code>
        ，诸如在后台启动下载一个文件。
    </p>
    <p>
        这种intent需要
        <code>
            Context
        </code>
        ，即你创建intent时所在的类（本例中即为
        <code>
            this
        </code>
        ），以及需要运行intent的类（本例中即为
        <code>
            EnterTextActivity::class.java
        </code>
        ）作为参数来创建。由于你已明确地说明了这个intent是从A到B，Android只需执行它即可。用户无法控制intent如何完成：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-500x500.jpg"
        alt="intent_activity" width="500" height="500" class="aligncenter size-large wp-image-105605"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-500x500.jpg 500w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-250x250.jpg 250w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-320x320.jpg 320w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-32x32.jpg 32w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-64x64.jpg 64w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-96x96.jpg 96w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity-128x128.jpg 128w, https://koenig-media.raywenderlich.com/uploads/2015/05/intent_activity.jpg 800w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        运行项目。再拍一张照片，但这次点击
        <em>
            LETS MEMEIFY!
        </em>
        。你的显式intent就会将你带到下一个activity上：
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
        初始项目中已创建过这个activity，并在
        <em>
            AndroidManifest.xml
        </em>
        中进行了声明，因此你无需自己创建。
    </p>
    <h2>
        处理Intent
    </h2>
    <p>
        看起来intent充满魅力。但这些
        <code>
            Extra
        </code>
        你送到了哪里？它是在最后一个内存缓存区中出错了么？是时候把它们找出来，并进行使用了。
    </p>
    <p>
        在
        <em>
            EnterTextActivity
        </em>
        中
        <code>
            onCreate()
        </code>
        方法的底部添加下列的代码：
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
        当你创建activity时，就将之前activity传递来的
        <code>
            intent
        </code>
        中的
        <code>
            pictureUri
        </code>
        传递给
        <code>
            Uri
        </code>
        。当你可以访问到intent的时候，就可以访问它的
        <code>
            Extra
        </code>
        值。
    </p>
    <p>
        由于变量和对象是以各种形式出现的，你会有各种各样的形式来从intent中访问到它们。例如，你要访问上面的
        <code>
            Uri
        </code>
        对象，就可以使用
        <code>
            getParcelableExtra
            <uri>
                ()
            </uri>
        </code>
        方法。
        <code>
            Extra
        </code>
        中还有着用于访问其它类型变量的方法，如字符串和其它的基本类型等。
    </p>
    <p>
        类似于其它返回基本类型的方法，
        <code>
            getIntExtra()
        </code>
        也允许你定义一个默认的值。当
        <code>
            Extra
        </code>
        中没有这个值，或缺少这个key的时候，就会使用默认的值。
    </p>
    <p>
        获取到必须的
        <code>
            Extra
        </code>
        后，就基于
        <code>
            Uri
        </code>
        创建一个
        <code>
            Bitmap
        </code>
        ，其长宽分别为你传递的
        <code>
            BITMAP_WIDTH
        </code>
        和
        <code>
            BITMAP_HEIGHT
        </code>
        。最后，将
        <code>
            ImageView
        </code>
        的图片资源设置为这个bitmap，就能把照片展示出来了。
    </p>
    <p>
        除了展示
        <code>
            ImageView
        </code>
        外，此页还包含两个
        <code>
            EditText
        </code>
        ，用来输入meme的文本。初始的项目承担了大量的工作，将其中的文本结合到你的照片上。
    </p>
    <p>
        现在你需要做的唯一一件事，就是完成
        <code>
            onClick()
        </code>
        了。将它更新到
        <code>
            R.id.write_text_to_image_button
        </code>
        分支中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">R.id.writeTextToImageButton -&gt; createMeme()
</pre>
    <p>
        运行项目。再次拍摄一张照片，然后在第二页输入你超赞的meme文本，并点击
        <em>
            LETS MEMEIFY!
        </em>
        ：
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
        你已创建了自己的meme生成器！不用庆祝太久，你还可以添加一些点缀到你的app上。
    </p>
    <h2>
        广播Intent
    </h2>
    <p>
        现在项目可以很好地保存你漂亮的新memen，可以将它共享到全世界。但它无法只靠自己来执行！:]
    </p>
    <p>
        幸运的是，初始项目中已覆盖了这些 - 你只需要将它们联系在一起。
    </p>
    <p>
        添加下列的代码到
        <code>
            saveImageToGallery()
        </code>
        中，就在
        <code>
            try
        </code>
        代码块之后，第二个
        <code>
            Toaster.show()
        </code>
        的调用之前：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> mediaScanIntent = Intent(Intent.ACTION_MEDIA_SCANNER_SCAN_FILE)
mediaScanIntent.<span class="hljs-keyword">data</span> = Uri.fromFile(imageFile)
sendBroadcast(mediaScanIntent)
</pre>
    <p>
        这个intent使用了
        <code>
            ACTION_MEDIA_SCANNER_SCAN_FILE
        </code>
        action来请求Android的媒体库添加图片的
        <code>
            Uri
        </code>
        。这样，任何访问媒体库的app都可以读取到这张图片了。
    </p>
    <p>
        这个
        <code>
            ACTION_MEDIA_SCANNER_SCAN_FILE
        </code>
        action还需要intent带有一些
        <code>
            Uri
        </code>
        形式的附加数据，代表你保存到文件中的
        <code>
            Bitmap
        </code>
        对象。
    </p>
    <p>
        最后，在Android上广播这个intent，这样任何对此感兴趣的部分 - 在本例中就是媒体扫描器 - 都可以执行相应的行动。由于媒体扫描器没有用户界面，因此你无需启动一个activity，只需广播这个intent即可。
    </p>
    <p>
        将在，将
        <code>
            onClick()
        </code>
        方法中的
        <code>
            R.id.save_image_button
        </code>
        分支更新为如下的代码：
    </p>
    <pre lang="java" class="language-java hljs">R.id.saveImageButton -&gt; askForPermissions()
</pre>
    <p>
        当用户点击
        <em>
            SAVE IMAGE
        </em>
        时，上述的代码就会检查
        <code>
            WRITE_EXTERNAL_STORAGE
        </code>
        权限。如果在Android Marshmallow及以上的系统上未得到授权，这个方法会有礼貌地请求用户来授予。否则，如果系统允许你写入到外部存储，只需将控制权传递给
        <code>
            saveImageToGallery()
        </code>
        。
    </p>
    <p>
        <code>
            saveImageToGallery()
        </code>
        中的代码会进行一些错误处理，如果没发现错误，就会启动intent。
    </p>
    <p>
        运行项目。拍一张照片，添加一些精美的meme文本，点击
        <em>
            LETS MEMEIFY!
        </em>
        ，然后在照片准备好之后，点击
        <em>
            SAVE IMAGE
        </em>
        。
    </p>
    <p>
        现在关闭app并打开
        <em>
            Photos
        </em>
        app。如果用的是模拟器，请打开
        <em>
            Gallery
        </em>
        app。你会看到刚保存的meme图片：
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
        现在你的meme就可以摆脱app的限制，并发布到社交媒体上，或是以任何你选择的方式进行分享。你的meme生成器已经完成了！
    </p>
    <h2>
        意图过滤器
    </h2>
    <p> 
        现在你应当对如何正确地使用intent有了自己的心得。然而，intent还有另一方面的内容：当隐式的intent被发送时，你的app如何知道是哪个intent请求相应。
    </p>
    <p>
        打开
        <em>
            AndroidManifest.xml
        </em>
        ，在第一个
        <code>
            activity
        </code>
        元素中，你会看到如下的代码：
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
        这里的关键就是
        <code>
            intent-filter
        </code>
        元素。
        <em>
            Intent Filter
        </em>
        可以让你app的一部分内容响应隐式intent。
    </p>
    <p>
        当Android尝试去满足从另一个app发送来的intent时，这些行为就像是一个条幅。一个app可以有多个intent过滤器，招揽着Android中其它的app正在寻找的意图实施者：
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
        有点像是intent和app的在线约会。:]
    </p>
    <p>
        为确保它是对intent正确的app，intent过滤器提供了三样东西：
    </p>
    <ol>
        <li>
            <em>
                Intent Action
            </em>
            ：app能够实现的action；类似于相机app可以为你的app实现
            <code>
                ACTION_IMAGE_CAPTURE
            </code>
            action。
        </li>
        <li>
            <em>
                Intent Data
            </em>
            ：intent可以接受数据的类型。诸如文件路径，端口，图像和视频这样的MIME类型。你可以设置一个或多个的属性，来控制你的app可以处理的intent的数据类型。
        </li>
        <li>
            <em>
                Intent Category
            </em>
            ：可以被接受的intent的类别。这是一个额外的方式来指定哪些Action可以响应隐式意图。
        </li>
    </ol>
    <p>
        把Memeify作为一个隐式intent，与来自其它app的图片进行交互是一件超棒的事 - 而且做起来超级简单。
    </p>
    <p>
        在
        <em>
            AndroidManifest.xml
        </em>
        文件中第一个intent下添加下列的代码：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">intent-filter</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">action</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.action.SEND"</span> /&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">category</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.category.DEFAULT"</span> /&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">data</span> <span class="hljs-attr">android:mimeType</span>=<span class="hljs-string">"@string/image_mime_type"</span> /&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">intent-filter</span>&gt;</span>
</pre>
    <p>
        新增的intent过滤器，指定了你的app将从隐式intent中查找
        <code>
            SEND
        </code>
        action。由于没有特殊的情况，这里使用默认的类别，也就是你只寻找图片这种数据类型。
    </p>
    <p>
        现在，打开
        <em>
            TakePictureActivity.kt
        </em>
        并添加下列的代码到类的底部：
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
        这里获取到了启动activity的
        <code>
            Intent
        </code>
        ，并检索它的action和类型。然后与你在intent过滤器中所声明的进行比较，它是一个图片类型的数据源。
    </p>
    <p>
        如果匹配的话，就获取图片的
        <code>
            Uri
        </code>
        ，然后使用在初始项目中包含的助手方法查询
        <code>
            Bitmap
        </code>
        的
        <code>
            Uri
        </code>
        ，最后请求
        <code>
            ImageView
        </code>
        展示检索到的
        <code>
            Bitmap
        </code>
        。
    </p>
    <p>
        接下来，添加下列的代码到
        <code>
            onCreate()
        </code>
        的尾部：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">checkReceivedIntent()
</pre>
    <p>
        上述的代码会确保每次创建这个activity时，这里是否有intent。
    </p>
    <p>
        运行项目。然后回到首页，再转到照片app（对于模拟器则是Gallery app）。选择任一照片，然后点击分享按钮。你应当会看到弹出的选项中已出现了
        <em>
            Memeify
        </em>
        ：
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
        Memeify已经准备好了，正等着接收你的照片！点击
        <em>
            Memeify
        </em>
        ，看看会发生什么 - Memeify会启动，刚选择的照片已显示在了
        <code>
            ImageView
        </code>
        中。
    </p>
    <p>
        你的app现在就像一个老板一样在接收intent！
    </p>
    <h2>
        从这儿去向哪里？
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
                            想要学得更快？通过我们的
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
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/memeify-final.zip">
            这里
        </a>
        下载最终的项目。
    </p>
    <p>
        Intent是Android最基本的构建模块之一。如果没有它们，Android自豪的开放性和互通性就不可能实现。学会如何使用intent，你就拥有了一个强有力的盟军。
    </p>
    <p>
        如果你想了解更多关于intent和intent过滤器的内容，请访问Google的
        <a href="http://developer.android.com/guide/components/intents-filters.html"
        target="_blank">
            Intent文档
        </a>
        。
    </p>
</div>