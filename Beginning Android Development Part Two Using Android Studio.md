# 开始Android开发教程第二部分：使用Android Studio
---
#### [原文地址](https://www.raywenderlich.com/154676/android-studio-tutorial-introduction) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-250x250.png"
            alt="" width="250" height="250" class="alignright size-thumbnail wp-image-155957"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/02/AndroidStudio-Intro-feature-128x128.png 128w"
            sizes="(max-width: 250px) 100vw, 250px">
        </a>
    </p>
    <p>
        <em>
            更新于2017年3月8日
        </em>
        ：由Brian Voong更新至适配最新版本的Android Studio。原教材是由Megha Bambra编写的。
    </p>
    <p>
        Android Studio是基于
        <a href="https://www.jetbrains.com/idea/" target="_blank" title="IntelliJ IDEA"
        sl-processed="1">
            IntelliJ IDEA
        </a>
        的IDE，并由Google声明为Android app开发的
        <i>
            官方
        </i>
        IDE。
    </p>
    <p>
        在本教程中，你将学习如何使用每个Android开发者都会使用的工具，来创建一个简单的算命app。你会学到一些Android Studio的关键特性，诸如：
    </p>
    <ul>
        <li>
            使用项目浏览器在不同文件间进行切换
        </li>
        <li>
            设置
            <em>
                AndroidManifest.xml
            </em>
            文件
        </li>
        <li>
            了解
            <em>
                Gradle
            </em>
            build系统
        </li>
        <li>
            将文件导入到你的项目中
        </li>
        <li>
            了解丰富的布局编辑器及动态布局预览
        </li>
        <li>
            使用
            <em>
                Logcat
            </em>
            和
            <em>
                Android Monitor
            </em>
            来debug你的app
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                注意：
            </em>
            本教程假定你早已安装Android Studio，并设置好了用来测试的模拟器或真机。如果不是的话，请先访问我们的
            <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Beginning%20Android%20Development%20Part%20One%20Installing%20Android%20Studio.md"
            sl-processed="1">
                上一篇教程
            </a>
            以便快速地启动项目！
        </p>
    </div>
    <h2>
        入门Android Studio
    </h2>
    <p>
        你将首先创建一个新的Android app，用来探索Android Studio，并了解它的界面和功能。
    </p>
    <p>
        作为你奖励，你也可以成为一个算命先生到处走走 - 或是做其它有趣的事。你至少会有一个有趣的app可以玩耍！
    </p>
    <p>
        打开Android Studio，并在
        <em>
            Android Studio Setup Wizard
        </em>
        窗口中，选择
        <em>
            Start a new Android Studio project
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.47.20-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.47.20-AM.png"
            alt="Android Studio New Project" width="775" height="457" class="aligncenter size-large wp-image-154678"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.47.20-AM.png 775w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.47.20-AM-480x283.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.47.20-AM-650x383.png 650w"
            sizes="(max-width: 775px) 100vw, 775px">
        </a>
    </p>
    <p>
        在
        <em>
            Create New Project
        </em>
        窗口中，将
        <em>
            Application Name
        </em>
        设置为Fortune Ball，输入你选择的        
        <em>
            Company Domain
        </em>
        ，并在
        <em>
            Project location
        </em>
        域中输入一个方便的位置来保存你的app。点击
        <em>
            Next
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.55.46-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.55.46-AM.png"
            alt="Screen Shot 2015-11-15 at 11.55.05 PM" width="686" height="696" class="aligncenter">
        </a>
    </p>
    <p>
        现在你看到的会是
        <em>
            Target Android Devices
        </em>
        窗口。勾选
        <em>
            Phone and Tablet
        </em>
        并指定
        <em>
            API 15
        </em>
        作为
        <em>
            Minimum SDK
        </em>
        。点击
        <em>
            Next
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.00.39-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.00.39-AM.png"
            alt="Target Android Devices" width="607" height="678" class="aligncenter size-full wp-image-154687"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.00.39-AM.png 607w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.00.39-AM-286x320.png 286w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.00.39-AM-448x500.png 448w"
            sizes="(max-width: 607px) 100vw, 607px">
        </a>
    </p>
    <p>
        在
        <em>
            Add an activity to Mobile
        </em>
        窗口中，选择
        <em>
            Basic Activity
        </em>
        。花半分钟来查看一下你的所有选项；这个窗口给出了布局文件的概述。这种情况下，它会是一个空白的activity，顶部带有一个工具栏，底部则是一个
        <a href="https://www.google.com/design/spec/components/buttons-floating-action-button.html#buttons-floating-action-button-floating-action-button"
        target="_blank" title="Floating Action Button" sl-processed="1">
            浮动的动作按钮
        </a>
        。点击
        <em>
            Next
        </em>
        来继续。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM.png"
            alt="Screen Shot 2017-02-03 at 10.05.32 AM" width="675" height="678" class="aligncenter size-full wp-image-154691"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM.png 675w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-319x320.png 319w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-498x500.png 498w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.05.32-AM-128x128.png 128w"
            sizes="(max-width: 675px) 100vw, 675px">
        </a>
    </p>
    <p>
        在
        <em>
            Customize the Activity
        </em>
        窗口中，就像下面所展示的一样，你可以改变
        <em>
            Activity Name
        </em>
        ，
        <em>
            Layout Name
        </em>
        ，
        <em>
            Title
        </em>
        和
        <em>
            Menu Resource Name
        </em>
        。在本教程中，让一切保持简单，点击
        <em>
            Finish
        </em>
        以保持默认的值。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM.png"
            alt="Customize the Activity" width="664" height="678" class="aligncenter size-full wp-image-154693"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM.png 664w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM-313x320.png 313w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM-490x500.png 490w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.08.40-AM-64x64.png 64w"
            sizes="(max-width: 664px) 100vw, 664px">
        </a>
    </p>
    <p>
        稍等一会之后（希望是秒！）你会看到一个这样的界面：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.10.21-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.10.21-AM-650x419.png"
            alt="content_main" width="650" height="419" class="aligncenter size-large wp-image-154694"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.10.21-AM-650x419.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.10.21-AM-480x309.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.10.21-AM.png 1112w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        运行你的app，你会看到一个类似的屏幕出现在你的设备或模拟器上，注意模拟器的作用就像是一个设备，因此需要时间来引导和加载。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.30.07-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.30.07-AM-280x500.png"
            alt="Build and Run" width="280" height="500" class="aligncenter size-large wp-image-154700"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.30.07-AM-280x500.png 280w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.30.07-AM-179x320.png 179w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.30.07-AM.png 336w"
            sizes="(max-width: 280px) 100vw, 280px">
        </a>
    </p>
    <p>
        瞧。一个app已经出现了！没有太多的内容，但对于深入到下一部分已足够了。
    </p>
    <h2>
        项目和文件结构
    </h2>
    <p>
        在本教程的这一部分，你将聚焦于下面截图中被红框框起的部分。这个窗口展示了你的app中的项目文件。默认情况下，这些文本会被过滤到只显示
        <em>
            Android
        </em>
        项目文件的部分。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.19.58-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.19.58-AM-650x438.png"
            alt="Project tab" width="650" height="438" class="aligncenter size-large wp-image-154697"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.19.58-AM-650x438.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.19.58-AM-475x320.png 475w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.19.58-AM.png 1387w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        当你选择文件的下拉菜单时，就像下面截图中展示的一样，你会看到几个用来过滤文件的选项。这其中关键的过滤器是
        <em>
            Project
        </em>
        和
        <em>
            Android
        </em>
        。
    </p>
    <p>
        <em>
            Project
        </em>
        过滤器会展示给你所有的应用模块 - 这是在所有项目中的一个最小的应用模块。
    </p>
    <p>
        其它类型的模块还包括第三方库的模块，或Android的其它应用模块（如Android wear app，Android TV等等）。每个模块都有自己完整的源集合，包括gradle文件，资源和源文件，例如java文件。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-1.30.25-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-1.30.25-AM-397x320.png"
            alt="Screen Shot 2015-11-16 at 1.30.25 AM" width="397" height="320" class="aligncenter size-medium wp-image-120543"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-1.30.25-AM-397x320.png 397w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-1.30.25-AM-620x500.png 620w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-1.30.25-AM.png 682w"
            sizes="(max-width: 397px) 100vw, 397px">
        </a>
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：如果没有看到项目视图的打开，你可以点击左侧面板中的
            <em>
                Project
            </em>
            tab，就像上面截图中所展示的一样。
        </p>
    </div>
    <p>
        默认的过滤器就是
        <em>
            Android
        </em>
        它会依据特定的类型来对文件进行分组。你会在顶层看到如下的目录：
    </p>
    <li>
        <em>
            manifests
        </em>
    </li>
    <li>
        <em>
            java
        </em>
    </li>
    <li>
        <em>
            res
        </em>
    </li>
    <li>
        <em>
            Gradle Scripts
        </em>
    </li>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-10.37.04-PM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-10.37.04-PM-480x281.png"
            alt="Screen Shot 2015-11-16 at 10.37.04 PM" width="480" height="281" class="aligncenter size-medium wp-image-120584"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-10.37.04-PM-480x281.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-10.37.04-PM.png 672w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        你会深入地了解其中的每一个目录，从下一部分所提到的
        <em>
            manifests
        </em>
        开始。
    </p>
    <h2>
        AndroidManifest.xml的概述
    </h2>
    <p>
        每个Android的app都包含一个
        <em>
            AndroidManifest.xml
        </em>
        文件在
        <em>
            manifests
        </em>
        目录中。这个XML文件会告知系统你app的需要，并且它必须存在，Android系统才能构建你的app。
    </p>
    <p>
        打开app的
        <em>
            manifests
        </em>
        目录并选择
        <em>
            AndroidManifest.xml
        </em>
        。双击这个文件来将其打开。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-11.31.53-PM1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-11.31.53-PM1-700x312.png"
            alt="Screen Shot 2015-11-16 at 11.31.53 PM" width="700" height="312" class="aligncenter size-large wp-image-120589"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-11.31.53-PM1-700x312.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-16-at-11.31.53-PM1-480x214.png 480w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        <code>
            manifest
        </code>
        和
        <code>
            application
        </code>
        标签都必须出现在manifest文件中且只能出现一次。
    </p>
    <p>
        除了元素的名称，每个标签还会定义一组属性。例如，在
        <code>
            application
        </code>
        标签中的属性就有：
        <code>
            android:icon
        </code>
        ，
        <code>
            android:label
        </code>
        和
        <code>
            android:theme
        </code>
        。
    </p>
    <p>
        其它会出现在manifest中的常见元素还包括：
    </p>
    <li>
        <code>
            uses-permission
        </code>
        ：你的app需要请求系统某些特定的权限，才能正确地执行某项操作。例如，一个app必须向用户请求许可才能够访问因特网 - 因此你就要请求
        <code>
            android.permission.INTERNET
        </code>
        的许可。
    </li>
    <li>
        <code>
            activity
        </code>
        ：声明一个实现了部分用户界面和逻辑的activity。你的app用到的每个activity都必须出现在manifest中 - 未声明的activity是无法被系统看到的，更可悲的是它们永远都不会被运行。
    </li>
    <li>
        <code>
            service
        </code>
        ：声明一个service，用来实现你将要长期运行在后台的操作，或是可以被其它app调用的丰富的API。一个例子就是为你的app调用网络来获取数据。不像activity，service是没有用户界面的。
    </li>
    <li>
        <code>
            receiver
        </code>
        ：声明一个broadcast接收器，它可以让你的app接收来自系统或其它app的代表一定含义的broadcast，即使app的其它组件还未运行。一个例子就是，当电量低的时候，就会在app中获取到一个系统的通知，你就可以撰写逻辑来做出响应。
    </li>
    <p>
        你可以在Android开发者网站的
        <a href="http://developer.android.com/guide/topics/manifest/manifest-intro.html"
        target="_blank" title="" sl-processed="1">
            这里
        </a>
        ，找到manifest文件允许的标签的完整列表。
    </p>
    <h3>
        配置Manifest
    </h3>
    <p>
        你现在看到的已经是一个优秀的框架的例子，但它无法成为一个厉害的算命先生；你在这里是因为你想要了解如何玩转Android。这是非常方便的，因为manifest需要一些变化，你可以在将来进一步地看。
    </p>
    <p>
        在
        <code>
            activity
        </code>
        下，添加下列的属性：
        <code>
            android:screenOrientation="portrait"
        </code>
        ，来限制屏幕只可以是垂直的模式。如果没有这项的话，屏幕就会依赖设备的方向来确定它是横向还是纵向。在添加这个attribute后，你的manifest文件看起来应当就像下面这样：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/manifest-700x478.png"
        alt="manifest" width="700" height="478" class="aligncenter size-large wp-image-122951"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/manifest-700x478.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/manifest-469x320.png 469w, https://koenig-media.raywenderlich.com/uploads/2015/12/manifest.png 1273w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <p>
        运行app。旋转你的手机。注意，由于你在
        <em>
            AndroidManifest
        </em>
        文件中限制了这项能力，你的屏幕就不会再旋转至横向模式了。
    </p>
    <h3>
        Gradle的概览
    </h3>
    <p>
        让我们换挡到Gradle。它是Android Studio使用的构建系统。它将Android项目构建/编译为一个可以安装到设备上的APK文件。
    </p>
    <p>
        如下图所示，你可以在
        <em>
            Gradle scripts
        </em>
        下找到
        <em>
            build.gradle
        </em>
        文件，它分为两个级别：模块级别和项目级别。大多情况下，你会在模块级别下编辑这个文件。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/gradle.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/gradle-430x500.png"
            alt="gradle" width="430" height="500" class="aligncenter size-large wp-image-121777"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/gradle-430x500.png 430w, https://koenig-media.raywenderlich.com/uploads/2015/12/gradle-275x320.png 275w, https://koenig-media.raywenderlich.com/uploads/2015/12/gradle.png 659w"
            sizes="(max-width: 430px) 100vw, 430px">
        </a>
    </p>
    <p>
        打开
        <em>
            build.gradle (Module:app)
        </em>
        文件。你会看到默认的gradle配置：
    </p>
    <pre lang="java" class="language-java hljs">apply plugin: <span class="hljs-string">'com.android.application'</span>

android {
    compileSdkVersion <span class="hljs-number">25</span>
    buildToolsVersion <span class="hljs-string">"25.0.2"</span>
    defaultConfig {
        applicationId <span class="hljs-string">"com.raywenderlich.fortuneball"</span>
        minSdkVersion <span class="hljs-number">15</span>
        targetSdkVersion <span class="hljs-number">25</span>
        versionCode <span class="hljs-number">1</span>
        versionName <span class="hljs-string">"1.0"</span>
        testInstrumentationRunner <span class="hljs-string">"android.support.test.runner.AndroidJUnitRunner"</span>
    }
    buildTypes {
        release {
            <span class="hljs-function">minifyEnabled <span class="hljs-keyword">false</span>
            proguardFiles <span class="hljs-title">getDefaultProguardFile</span><span class="hljs-params">(<span class="hljs-string">'proguard-android.txt'</span>)</span>, 'proguard-rules.pro'
        }
    }
}

dependencies </span>{
    <span class="hljs-function">compile <span class="hljs-title">fileTree</span><span class="hljs-params">(dir: <span class="hljs-string">'libs'</span>, include: [<span class="hljs-string">'*.jar'</span>])</span>
    <span class="hljs-title">androidTestCompile</span><span class="hljs-params">(<span class="hljs-string">'com.android.support.test.espresso:espresso-core:2.2.2'</span>, {
        exclude group: <span class="hljs-string">'com.android.support'</span>, <span class="hljs-keyword">module</span>: <span class="hljs-string">'support-annotations'</span>
    })</span>
    compile 'com.android.support:appcompat-v7:25.1.0'
    compile 'com.android.support:design:25.1.0'
    testCompile 'junit:junit:4.12'
}
</span></pre>
    <p>
        一步一步来看下主要部分：
    </p>
    <li>
        <code>
            apply plugin: 'com.android.application'
        </code>
        在父层级应用Android plugin，并使构建一个Android app所需的顶级构建任务变得可用。
    </li>
    <li>
        下面在
        <code>
            android{...}
        </code>
        这一部分，你会获取诸如
        <code>
            targetSdkVersion
        </code>
        的配置选项。你app的target SDK应当保持在最新的API等级（如本教程发布时的
        <em>
            25
        </em>
        ）。另一个重要的部分就是
        <code>
            minSDKVersion
        </code>
        ，它声明了一台设备为了运行你的app，所应当拥有的最低SDK版本。例如，如果你设备的SDK版本是14，这个app就无法运行到这个设备上了。
    </li>
    <li>
        最后一部分就是
        <code>
            dependencies{...}
        </code>
        了。值得去注意的重要依赖就是
        <code>
            compile 'com.android.support:appcompat-v7:VERSION'
        </code>
        和
        <code>
            compile 'com.android.support:design:VERSION'
        </code>
        了。它们提供了从最新API到较旧API中功能的支持和兼容性。
    </li>
    <p>
        除了Android的兼容性库，你还可以在
        <code>
            dependencies{...}
        </code>
        的组件中添加其它的第三方库。你会添加一个动画的库，这样就可以在app的用户界面中添加一些很酷的效果。找到
        <code>
            dependencies
        </code>
        ，并添加下列代码到文件的底部：
    </p>
    <pre lang="java" class="language-java hljs">dependencies {
  
  ...

  compile <span class="hljs-string">'com.daimajia.easing:library:2.0@aar'</span>
  compile <span class="hljs-string">'com.daimajia.androidanimations:library:2.2@aar'</span>
}
</pre>
    <p>
        这里你添加了两个新的第三方依赖，它们将帮助你的FortuneBall闪耀起来。这些库会被Android Studio自动地下载并集成。
    </p>
    <p>
        事实上，一旦你添加了这些依赖，Android Studio就会意识到需要去下载它们并告知于你。如下面的截图所示，可以查看
        <em>
            build.gradle
        </em>
        文件顶部的一个栏。点击
        <em>
            Sync Now
        </em>
        来将这些依赖集成到你的app中。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/sync-700x92.png"
        alt="sync" width="700" height="92" class="aligncenter size-large wp-image-122953"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/sync-700x92.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/sync-480x63.png 480w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <p>
        同步需要花费几秒钟的时间。你可以在底部面板的
        <em>
            Messages
        </em>
        tab中监视Gradle文件的更新。在这个面板中查找成功的消息，就如下面的截图所示。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/success-700x251.png"
        alt="success" width="700" height="251" class="aligncenter size-large wp-image-122954"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/success-700x251.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/success-480x172.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/12/success.png 1247w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <p>
        好了，以上就是你需要为Gradle作出的所有配置。这些都是为了给你的app添加一些神奇的动画。
    </p>
    <h2>
        导入文件
    </h2>
    <p>
        创建Android app中的一个重要的事就是集成其它的资源，诸如图片，自定义的字体，声音，视频等等。这些资源必须被导入到Android Studio，并放置到合适的目录下，以便Android的操作系统正确地获取资源。
    </p>
    <p>
        对于风水球，你将导入图片资源并将它们放置到drawable目录下。Drawable目录下可以存放图片或自定义的可绘制XML文件（也是就说，你可以通过XML代码绘制图形，并将它们引用到你app的布局中）。
    </p>
    <p>
        在
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/drawable.zip"
        sl-processed="1">
            这里
        </a>
        下载图片资源，然后解压并将它们存放到易于获取的地方。
    </p>
    <p>
        回到Android Studio的项目中，将
        <em>
            Android
        </em>
        切换为
        <em>
            Project
        </em>
        。打开
        <em>
            app &gt; src &gt; main
        </em>
        下的
        <em>
            res
        </em>
        目录。鼠标右键点击
        <em>
            res
        </em>
        目录，选择
        <em>
            New &gt; Android resource directory
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-7.50.17-PM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-7.50.17-PM-700x294.png"
            alt="Screen Shot 2015-12-10 at 7.50.17 PM" width="700" height="294" class="aligncenter size-large wp-image-123000"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-7.50.17-PM-700x294.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-7.50.17-PM-480x202.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-7.50.17-PM.png 1476w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        你会看到一个标题为
        <em>
            New Resource Directory
        </em>
        的窗口。从
        <em>
            Resource type
        </em>
        的下拉菜单中选择
        <em>
            drawable
        </em>
        。在
        <em>
            Available qualifiers
        </em>
        列表中，选择
        <em>
            Density
        </em>
        并点击下面截图中高亮的按钮：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-10.33.43-PM1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-10.33.43-PM1-700x402.png"
            alt="Screen Shot 2015-11-20 at 10.33.43 PM" width="700" height="402" class="aligncenter size-large wp-image-120919"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-10.33.43-PM1-700x402.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-10.33.43-PM1-480x276.png 480w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        在后面的窗口中，从
        <em>
            Density
        </em>
        的下拉菜单中选择
        <em>
            XX-High Density
        </em>
        。点击
        <em>
            OK
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/create_drawable.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/create_drawable-700x356.png"
            alt="create_drawable" width="700" height="356" class="aligncenter size-large wp-image-121786"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/create_drawable-700x356.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/create_drawable-480x244.png 480w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        从
        <em>
            Density
        </em>
        的下拉菜单中分别选择X-High，high，和medium density，来重复相同的过程创建
        <em>
            drawable-xhdpi
        </em>
        ，
        <em>
            drawable-hdpi
        </em>
        和
        <em>
            drawable-mdpi
        </em>
        目录。
    </p>
    <p>
        每个drawable目录都有一个密度修饰符（也就是 xxhdpi，xhdpi，hdpi），存放着相应像素密度或分辨率的图片。例如，
        <em>
            drawable-xxhdpi
        </em>
        目录就存放着高像素密度的图片，这样一个带有高分辨率的Android设备就会从这个目录下获取图片。这你的app就可以在所有的Android的设备上看起来都不错，不论它的屏幕分辨率是怎样的。了解更多关于屏幕像素密度的信息，请访问
        <a href="https://developer.android.com/guide/practices/screens_support.html"
        target="_blank" sl-processed="1">
            Android文档
        </a>
        。
    </p>
    <p>
        创建完所有的drawable目录后，返回到在drawable目录下未解压的内容，然后从每个目录中copy（
        <em>
            cmd + C
        </em>
        ）图片然后粘贴（
        <em>
            cmd + V
        </em>
        ）到Android Studio中相应的目录下。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-11.26.23-PM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-11.26.23-PM-700x481.png"
            alt="Screen Shot 2015-11-20 at 11.26.23 PM" width="700" height="481" class="aligncenter size-large wp-image-120927"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-11.26.23-PM-700x481.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-20-at-11.26.23-PM-466x320.png 466w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        当你粘贴文件的时候，你会看到一个
        <em>
            Copy
        </em>
        窗口。选择
        <em>
            OK
        </em>
        。
        <br>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-8.23.16-PM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-8.23.16-PM-700x205.png"
            alt="Screen Shot 2015-12-10 at 8.23.16 PM" width="700" height="205" class="aligncenter size-large wp-image-123001"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-8.23.16-PM-700x205.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-8.23.16-PM-480x140.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-10-at-8.23.16-PM.png 1266w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        你刚刚已经把球放入到了Fortune Ball中，并了解了如何导入文件。看起来你已经搞定了你待学习列表中的另一个特性！
    </p>
    <h3>
        带有动态布局预览图的XML视图
    </h3>
    <p>
        构建Android app的一个非常重要的部分，就是创建一个和用户进行交互的界面。在Android Studio中，你会在布局编辑器中完成这个任务。在
        <em>
            res/layout
        </em>
        下打开
        <em>
            content_main.xml
        </em>
        。你开始会位于布局编辑器的
        <em>
            Design
        </em>
        这个tab上。在这个tab中，你可以在编辑器上拖拽诸如按钮，文本框等等的用户交互元素。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.45.44-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.45.44-AM-650x401.png"
            alt="XML Editor" width="650" height="401" class="aligncenter size-large wp-image-154703"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.45.44-AM-650x401.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.45.44-AM-480x296.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.45.44-AM.png 1046w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        在
        <em>
            Design
        </em>
        tab的右侧则是
        <em>
            Text
        </em>
        tab。切换到这个视图，就可以直接去编辑构成布局的XML文件了。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/text_tab-480x204.png"
        alt="text_tab" width="480" height="204" class="aligncenter size-medium wp-image-122960"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/text_tab-480x204.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/12/text_tab.png 696w"
        sizes="(max-width: 480px) 100vw, 480px">
    </p>
    <p>
        在两个tab中，你都可以在构建时预览设备中的布局。选择
        <em>
            Text
        </em>
        tab来开始构建Fortune Ball的布局。
    </p>
    <p>
        在你构架视图之前，你需要定义一些特定的值。打开
        <em>
            res/values
        </em>
        下的
        <em>
            strings.xml
        </em>
        文件，并添加下列的内容：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">string</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"fortune_description"</span>&gt;</span>Suggest the question, which you can answer “yes” or “no”, then click on the magic ball.<span class="hljs-tag">&lt;/<span class="hljs-name">string</span>&gt;</span>
</pre>
    <p>
        <em>
            strings.xml
        </em>
        文件包含了所有在你的app中将会看到的字符创。将字符串拆分到它们自己的文件中可以使国际化变得非常容易，只需为每种你想要支持的语言提供相应的字符串文件即可。尽管你还不想立刻就翻译你的app，使用一个字符串文件仍是最佳的实践。
    </p>
    <p>
        接下来，打开
        <em>
            res/values
        </em>
        下的
        <em>
            dimens.xml
        </em>
        文件并添加下列的代码：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">dimen</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"description_text_size"</span>&gt;</span>15sp<span class="hljs-tag">&lt;/<span class="hljs-name">dimen</span>&gt;</span>
<span class="hljs-tag">&lt;<span class="hljs-name">dimen</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"fortune_text_size"</span>&gt;</span>20sp<span class="hljs-tag">&lt;/<span class="hljs-name">dimen</span>&gt;</span>
</pre>
    <p>
        <em>
            dimens.xml
        </em>
        则包含了所有的大小位置等的几何值，注入你布局中的边距，文本的大小等等。同样的，将这些值存放到这个文件中是一种很好的实践，以便在构建布局的时候重新使用。
    </p>
    <p>
        找到
        <em>
            content_main.xml
        </em>
        文件，并使用下列的代码替换文件中的全部内容。
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">RelativeLayout</span>
  <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>
  <span class="hljs-attr">xmlns:tools</span>=<span class="hljs-string">"http://schemas.android.com/tools"</span>
  <span class="hljs-attr">xmlns:app</span>=<span class="hljs-string">"http://schemas.android.com/apk/res-auto"</span>
  <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
  <span class="hljs-attr">app:layout_behavior</span>=<span class="hljs-string">"@string/appbar_scrolling_view_behavior"</span>
  <span class="hljs-attr">tools:showIn</span>=<span class="hljs-string">"@layout/activity_main"</span>
  <span class="hljs-attr">tools:context</span>=<span class="hljs-string">".MainActivity"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/descriptionText"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:text</span>=<span class="hljs-string">"@string/fortune_description"</span>
    <span class="hljs-attr">android:gravity</span>=<span class="hljs-string">"center"</span>
    <span class="hljs-attr">android:textSize</span>=<span class="hljs-string">"@dimen/description_text_size"</span>/&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">ImageView</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/fortunateImage"</span>
    <span class="hljs-attr">android:src</span>=<span class="hljs-string">"@drawable/img_crystal"</span>
    <span class="hljs-attr">android:layout_centerHorizontal</span>=<span class="hljs-string">"true"</span>
    <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@id/descriptionText"</span>
    <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"10dp"</span>/&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">TextView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/fortuneText"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@id/fortunateImage"</span>
    <span class="hljs-attr">android:gravity</span>=<span class="hljs-string">"center"</span>
    <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"20dp"</span>
    <span class="hljs-attr">android:textSize</span>=<span class="hljs-string">"@dimen/fortune_text_size"</span>
    <span class="hljs-attr">android:textStyle</span>=<span class="hljs-string">"bold"</span>
    <span class="hljs-attr">android:textColor</span>=<span class="hljs-string">"@android:color/holo_red_dark"</span>/&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">Button</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/fortuneButton"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"50dp"</span>
    <span class="hljs-attr">android:layout_below</span>=<span class="hljs-string">"@id/fortuneText"</span>
    <span class="hljs-attr">android:text</span>=<span class="hljs-string">"What's my fortune?"</span>
    <span class="hljs-attr">android:layout_centerHorizontal</span>=<span class="hljs-string">"true"</span>
    <span class="hljs-attr">android:layout_marginTop</span>=<span class="hljs-string">"10dp"</span>/&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">RelativeLayout</span>&gt;</span>
</pre>
    <p>
        以上的大段XML代码构建了FortuneBall的布局。在最顶层你添加了一个
        This rather large chunk of XML creates the layout of FortuneBall. 
        At the top level you’ve added a
        <em>
            RelativeLayout
        </em>
        标签，它的工作是对内容进行布局。它会拉伸以匹配整个父视图的尺寸（也就是Activity）。
    </p>
    <p>
        在relative layout中你添加了两个text，一个image和一个button。它们将会以你添加的顺序展示在容器中，而它们的文本内容会从
        <em>
            strings.xml
        </em>
        中读取，图片内容则从drawable中读取。
    </p>
    <p>
        随着你更新
        <em>
            content_main.xml
        </em>
        ，
        <em>
            Preview
        </em>
        窗口就会发生相应的变化：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.50.48-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.50.48-AM-650x406.png"
            alt="content_main updates" width="650" height="406" class="aligncenter size-large wp-image-154705"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.50.48-AM-650x406.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.50.48-AM-480x299.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-10.50.48-AM.png 1263w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            ：如果你无法看到预览窗口，请在你位于
            <em>
                Text
            </em>
            tab的情况下，点击布局编辑器中，右侧面板中的
            <em>
                Preview
            </em>
            按钮。
        </p>
    </div>
    <p> 
        运行项目。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-22-213951.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-22-213951-180x320.png"
            alt="device-2015-11-22-213951" width="180" height="320" class="aligncenter size-medium wp-image-121052"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-22-213951-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-22-213951-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-22-213951.png 1080w"
            sizes="(max-width: 180px) 100vw, 180px">
        </a>
    </p>
    <p>
        祝贺！你已经完成了设计你app的布局。然而，它现在实际上只是一张不能进行交互的图 - 点击按钮不会有任何的反映。准备好玩转activity了么？
    </p>
    <h2>
        连接view和activity
    </h2>
    <p>
        你需要使用位于
        <em>
            app / src / main / java
        </em>
        中的java文件完成你app的逻辑。
    </p>
    <p>
        打开
        <em>
            MainActivity.java
        </em>
        并在已存在的import的下方添加下列的import
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">import</span> java.util.Random;
<span class="hljs-keyword">import</span> android.view.View;
<span class="hljs-keyword">import</span> android.widget.Button;
<span class="hljs-keyword">import</span> android.widget.ImageView;
<span class="hljs-keyword">import</span> android.widget.TextView;

<span class="hljs-keyword">import</span> com.daimajia.androidanimations.library.Techniques;
<span class="hljs-keyword">import</span> com.daimajia.androidanimations.library.YoYo;
</pre>
    <p>
        前五个import表示你将要在代码证引用Random，View，Button，ImageView和TextView的类。剩下的两个则表示
        <em>
            build.gradle
        </em>
        中包含的两个库中的两个类进行动画的处理。在
        <em>
            MainActivity.java
        </em>        
        <code>
            MainActivity
        </code>
        类中添加下列的代码：
    </p>
    <pre lang="java" class="language-java hljs">String fortuneList[] = {<span class="hljs-string">"Don’t count on it"</span>,<span class="hljs-string">"Ask again later"</span>,<span class="hljs-string">"You may rely on it"</span>,<span class="hljs-string">"Without a doubt"</span>,<span class="hljs-string">"Outlook not so good"</span>,<span class="hljs-string">"It's decidedly so"</span>,<span class="hljs-string">"Signs point to yes"</span>,<span class="hljs-string">"Yes definitely"</span>,<span class="hljs-string">"Yes"</span>,<span class="hljs-string">"My sources say NO"</span>};

TextView mFortuneText;
Button mGenerateFortuneButton;
ImageView mFortuneBallImage;
</pre>
    <p>
        在上述的小段代码中，你为activity声明了四个成员变量。第一个成员变量是字符串的的数组，代表可能的命运，剩余三个则代表了你刚在布局中创建的UI元素。
    </p>
    <p>
        接下来，将
        <code>
            onCreate()
        </code>
        方法的内容替换为下列的代码：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-comment">// 1:</span>
<span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
<span class="hljs-comment">// 2:</span>
setContentView(R.layout.activity_main);
Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
setSupportActionBar(toolbar);
<span class="hljs-comment">// 3:</span>
mFortuneText = (TextView) findViewById(R.id.fortuneText);
mFortuneBallImage = (ImageView) findViewById(R.id.fortunateImage);
mGenerateFortuneButton = (Button) findViewById(R.id.fortuneButton);

<span class="hljs-comment">// 4:</span>
mGenerateFortuneButton.setOnClickListener(<span class="hljs-keyword">new</span> View.OnClickListener() {
  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onClick</span><span class="hljs-params">(View view)</span> </span>{
    <span class="hljs-comment">// 5:</span>
    <span class="hljs-keyword">int</span> index = <span class="hljs-keyword">new</span> Random().nextInt(fortuneList.length);
    mFortuneText.setText(fortuneList[index]);
    <span class="hljs-comment">// 6:</span>
    YoYo.with(Techniques.Swing)
        .duration(<span class="hljs-number">500</span>)
        .playOn(mFortuneBallImage);
  }
});
</pre>
    <p>
        一步一步来看代码：
    </p>
    <ol>
        <li>
            调用父类的实现以确保activity准备就绪。
        </li>
        <li>
            指定activity的布局是由你之前所创建的提供的，并为toolbar执行一些准备的工作。
        </li>
        <li>
            使用
            <code>
                findViewById
            </code>
            方法为你刚创建的三个成员变量赋值。
            <code>
                id
            </code>
            值要和你在XML布局文件中所指定的一样。
        </li>
        <li>
            为按钮添加一个
            <code>
                OnClickListener
            </code>
            。它是一个简单的类，封装了当你点击按钮的时候需要执行的事。
        </li>
        <li>
            从
            <code>
                fortuneList
            </code>
            数组中随机选取一个命运，并更新以展示它。
        </li>
        <li>
            使用你添加的第三方动画库作为gradle文件的依赖，来为水晶球添加一些有趣的动画。
        </li>
    </ol>
    <p>
        OK - 还不算太糟对么？运行项目，点击按钮来测试你算命的能力。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/fortuneball.gif"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/fortuneball-281x500.gif"
            alt="fortuneball" width="281" height="500" class="aligncenter size-large wp-image-121060"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/fortuneball-281x500.gif 281w, https://koenig-media.raywenderlich.com/uploads/2015/11/fortuneball-180x320.gif 180w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        整理
    </h2>
    <p>
        你几乎全都完成了。但在开始筹划发布会之前，你必须先进行一下清理，例如移除浮动的按钮。找到
        <em>
            res / layout
        </em>
        并打开
        <em>
            activity_main.xml
        </em>
        文件。
    </p>
    <p>
        这个布局文件包含了你之前编辑的
        <em>
            content_main.xml
        </em>
        文件的引用。它封装了你默认工具栏中的内容和浮动的动作按钮。然而，Fortune Ball并不需要浮动的动作按钮，因此从文件中移除下面的代码：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.design.widget.FloatingActionButton</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/fab"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"bottom|end"</span>
    <span class="hljs-attr">android:layout_margin</span>=<span class="hljs-string">"@dimen/fab_margin"</span>
    <span class="hljs-attr">android:src</span>=<span class="hljs-string">"@android:drawable/ic_dialog_email"</span>/&gt;</span>
</pre>
    <p>
        运行项目。你将不会再看到右下角的浮动按钮：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-23-013050.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-23-013050-281x500.png"
            alt="device-2015-11-23-013050" width="281" height="500" class="aligncenter size-large wp-image-121063"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-23-013050-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-23-013050-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2015/11/device-2015-11-23-013050.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        问一个问题，点击
        <em>
            What’s my fortune?
        </em>
        ，让你的未来展现在眼前！
    </p>
    <h2>
        Android监视器
    </h2>
    <p>
        Android Studio提供了一大堆的工具，来帮助你查看app的内容。打开你Android Studio窗口的底部的
        <em>
            Android Monitor
        </em>
        tab，就可以看到它了。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/android_monitor_tab.png"
        alt="android monitor tab" width="470" height="17" class="aligncenter size-full wp-image-156539">
    </p>
    <p>
        这里你会看到大量有用的开发者选项。我们来看几个。不要担心，你并不需要记住它们，没有测验。:]
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/android_monitor.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/android_monitor.png"
            alt="android monitor" width="700" height="213" class="aligncenter size-full wp-image-156540"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/android_monitor.png 1218w, https://koenig-media.raywenderlich.com/uploads/2017/02/android_monitor-480x146.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/android_monitor-650x198.png 650w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        从顶部开始，你需要在这里指定你想要指定的设备或模拟器，以及你最感兴趣的“进程”（你应当选择app的包名，如果不是的话，请更正）。
    </p>
    <p>
        将鼠标悬停在左侧的按钮上，以展示相应的工具提示。
    </p>
    <ul>
        <li>
            在左上侧的相机和播放按钮，可以进行屏幕截图及
            <a href="https://developer.android.com/studio/debug/am-video.html" sl-processed="1">
                屏幕录像
            </a>
            。
        </li>
        <li>
            放大镜按钮可以展示更多的选项，如分析你app内存的使用情况。
        </li>
        <li>
            <em>
                Layout Inspector
            </em>
            可以给出一个非常酷的可视化界面，来帮助你了解app为什么看起来是这个样子。
        </li>
    </ul>
    <p>
        最后就是LogCat，它会展示给你详细的设备系统信息，以便深入了解特定的app，甚至使用搜索栏来过滤包含特定文本的信息。
    </p>
    <p>
        确保你在右上侧选择了
        <em>
            Show only selected application
        </em>
        ，就像上面截图中的一样。现在，你你只会看到来自你app的消息，包括你自己写的那些。噢，什么？你还没有自己添加过任何信息？
    </p>
    <p>
        找到
        <em>
            MainActivity.java
        </em>
        并添加下列的代码到import的列表中
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">import</span> android.util.Log;
</pre>
    <p>
        在
        <em>
            MainActivity.java
        </em>
        ，
        <code>
            onCreate()
        </code>
        方法中，添加下列的代码：
    </p>
    <pre lang="java" class="language-java hljs">Log.v(<span class="hljs-string">"FORTUNE APP TAG"</span>,<span class="hljs-string">"onCreateCalled"</span>);
</pre>
    <p>
        <code>
            Log.v
        </code>
        引用了两个参数 - 一个tag和一条信息。在本例中，你将tag设为
        <code>
            "FORTUNE APP TAG"
        </code>
        ，而message设为
        <code>
            "onCreateCalled"
        </code>
        。
    </p>
    <p>
        运行app，这样你就可以在
        <em>
            Logcat
        </em>
        面板中看到log信息了。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/full_logcat.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/full_logcat.png"
            alt="" width="700" height="184" class="aligncenter size-full wp-image-156541"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/full_logcat.png 1218w, https://koenig-media.raywenderlich.com/uploads/2017/02/full_logcat-480x126.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/full_logcat-650x171.png 650w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        要将LogCat中的内容过滤到只剩你自己的信息，请输入
        <em>
            onCreateCalled
        </em>
        到控制台上方的搜索框中，就像这样：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/on_create_called.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/on_create_called.png"
            alt="logcat" width="700" height="182" class="aligncenter size-full wp-image-156542"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/on_create_called.png 1217w, https://koenig-media.raywenderlich.com/uploads/2017/02/on_create_called-480x125.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/on_create_called-650x169.png 650w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        然后移除你搜索的文本，再次查看所有的信息。
    </p>
    <p>
        logcat的另一个非常有用的功能，就是从app的崩溃和异常中，查看堆栈或错误信息的能力。现在来添加一个bug到你完美工作的app中，来查看logcat如何工作。
    </p>
    <p>
        前往
        <em>
            MainActivity.java
        </em>
        ，并在中
        <code>
            onCreate()
        </code>
        注释掉下面这行：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-comment">//mFortuneText = (TextView) findViewById(R.id.fortuneText);</span>
</pre>
    <p>
        运行app。点击屏幕上的
        <em>
            What’s My Fortune?
        </em>
        按钮。Oh no！它崩溃了。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-23-at-11.45.20-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-23-at-11.45.20-AM-480x279.png"
            alt="Screen Shot 2015-11-23 at 11.45.20 AM" width="480" height="279" class="aligncenter size-medium wp-image-121155"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-23-at-11.45.20-AM-480x279.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-23-at-11.45.20-AM-700x407.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-23-at-11.45.20-AM.png 1480w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        如果不是故意把这个错误引进来的，你该怎么来解决这个问题？用Logcat来进行抢救！
    </p>
    <p>
        回到
        <em>
            Logcat
        </em>
        面板 - 它看起来就像是这样：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/crash_logcat-1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/crash_logcat-1.png"
            alt="crash logcat" width="700" height="131" class="aligncenter size-full wp-image-156545"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/02/crash_logcat-1.png 1086w, https://koenig-media.raywenderlich.com/uploads/2017/02/crash_logcat-1-480x90.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/02/crash_logcat-1-650x122.png 650w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        看到很多红色的文本了么，它们正是该到何处去查找问题的线索。你正在查找异常是从何处暴出的。在本例中，它就在
        <em>
            MainActivity.java
        </em>
        文件中的第50行。LogCat甚至很有帮助地将其转换成了蓝色的超链接，点击它就可以直接跳转到有问题的那行代码！
    </p>
    <p>
        由于注释掉了
        <code>
            mFortuneText = (TextView) findViewById(R.id.fortuneText)
        </code>
        这行代码，你创建了一个变量，但并没有对它进行赋值 - 因此就造成了空指针的异常。
    </p>
    <p>
        取消注释，并再次运行app。这次没有崩溃了！
    </p>
    <p>
        Logcat是一个强有力的工具，可以帮助你debug app的错误和异常。
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
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/FortuneBall-3.zip"
        target="_blank" title="final project" sl-processed="1">
            这里
        </a>
        下载最终的项目。
    </p>
    <p>
        完美的实践！你现在已学会了如何创建一个项目，玩转Gradle，导入assets，设置布局并进行一些测试。
    </p>
    <p>
        Android有很多很酷的工具值得去了解，建议你可以从下列的部分开始：
    </p>
    <ul>
        <li>
            熟悉Logcat和过滤机制。用不同过的条件进行过滤。
        </li>
        <li>
            There will be times where you’ll want to test your application’s robustness in different network environments. 
            See the
            <em>
                Android Emulator 2.0
            </em>
            section of our
            <a href="https://www.raywenderlich.com/124936/whats-new-android-studio-2-0"
            sl-processed="1">
                Android Studio 2 tour
            </a>
            for more details.
        </li>
        <li>
            This beginning Android development tutorial has just touched on some of the tools used to build out the layout and UI. 
            To learn more, pour over the official
            <a href="http://developer.android.com/guide/topics/ui/index.html" target="_blank"
            title="Android documentation for UI" sl-processed="1">
                Android documentation for UI
            </a>
            .
        </li>
        <li>
            Keep coming back to raywenderlich.com—- we’ve got some great Android content coming your way over the next days, weeks and months.
        </li>
        <li>
            Talk to other developers. Make use of the forums below and ask your questions,
            share your findings and pick up tips.
        </li>
    </ul>
    <div class="note">
        <em>
            注意：
        </em>
        
        Also, another great next step would be to check out our Android Core Concepts tutorials:
        <p>
        </p>
        <ul>
            <li>
                <a href="https://www.raywenderlich.com/165824/introduction-android-activities-kotlin"
                target="_blank" sl-processed="1">
                    Introduction to Android Activities with Kotlin
                </a>
            </li>
            <a href="https://www.raywenderlich.com/165824/introduction-android-activities-kotlin"
            target="_blank" sl-processed="1">
            </a>
            <li>
                <a href="https://www.raywenderlich.com/165824/introduction-android-activities-kotlin"
                target="_blank" sl-processed="1">
                </a>
                <a href="https://www.raywenderlich.com/160019/android-intents-tutorial-2"
                target="_blank" sl-processed="1">
                    Android: Intents Tutorial
                </a>
            </li>
            <li>
                <a href="https://www.raywenderlich.com/149112/android-fragments-tutorial-introduction"
                target="_blank" sl-processed="1">
                    Android Fragments Tutorial: An Introduction
                </a>
            </li>
            <li>
                <a href="https://www.raywenderlich.com/168038/common-design-patterns-android-kotlin"
                target="_blank" sl-processed="1">
                    Common Design Patterns for Android with Kotlin
                </a>
            </li>
        </ul>
    </div>
</div>