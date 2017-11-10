# Android SDK版本教程 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/171148/android-sdk-versions-tutorial-2) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <em>
            更新日志
        </em>
        ：本教程已由Eric Crawford更新至Kotlin版本。原教程是由Eunice Obugyei编写的。
    </div>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/AndroidSDKVersions-feature.png"
        alt="Android sdk versions" width="250" height="250" class="alignright size-thumbnail wp-image-124606">
    </p>
    <p>
        从Android的首次发布开始，它支持的设备已涵盖了各种各样的手机，智能手表等等。为这些设备开发Android app，最后实际都是归结到一个
        <em>
            Android SDK
        </em>
        （软件开发装备）上。新的SDK版本会跟随每个新版本的Android一起发布，这是我们这篇教程的重点。
    </p>
    <p>
        新的SDK版本会利用最新的设备上增强的处理能力，已提供非常棒的功能。很酷不是么？当然，另一方面Android开发者将会面对的挑战，就是确保app在运行不同版本Android SDK的设备上都能够正常地运行。
    </p>
    <p>
        幸运的是，有一些最佳实践的指南和工具可以帮助你去完成工作，而不必影响到用户体验和deadlines。
    </p>
    <p>
        在本教程中，你会学到：
    </p>
    <ul>
        <li>
            Android SDK版本和API级别
        </li>
        <li>
            Android的支持库及其重要性
        </li>
        <li>
            如何使用Android支持库来创建一个向后兼容的app
        </li>
        <li>
            如何使用CardView支持库
        </li>
    </ul>
    <p>
        为了将理论付诸实践，你将会玩转一个名为
        <em>
            Continents
        </em>
        的简单app。它给出了世界上各大洲的简介。
    </p>
    <div class="note">
        <em>
            注意：
        </em>
        本教程假定你已熟悉了Android开发和Kotlin的基础。如果你是一个Android开发的纯小白，请访问
        <a href="https://www.raywenderlich.com/161318/beginning-android-development-part-one-installing-android-studio"
        target="_blank">
            开始Android开发
        </a>
        和我们的
        <a href="https://www.raywenderlich.com/category/android" target="_blank">
            其它Android和Kotlin教程
        </a>
        学习相关的基础。
    </div>
    <div class="note">
        <em>
            注意：
        </em>
        本教程需要Android Studio 3.0 Beta 4及以上的版本。
    </div>
    <h2>
        入门
    </h2>
    <p>
        下载本教程的
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/continents-starter.zip">
            起始项目
        </a>
        ，并解压zip文件获取项目。
    </p>
    <p>
        从
        <em>
            Quick Start
        </em>
        菜单中选择
        <em>
            Open an existing Android Studio project
        </em>
        ，并打开起始项目：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASOpen.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASOpen-650x468.jpeg"
            alt="" width="650" height="468" class="aligncenter size-large wp-image-171193"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASOpen-650x468.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASOpen-444x320.jpeg 444w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASOpen.jpeg 662w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        如果你用的是windows系统，请选择
        <em>
            File / Open
        </em>
        以找到起始项目的目录。
    </p>
    <p>
        如果系统提示你安装（或更新到）新版本的Android构建工具，或提示更新Gradle插件的版本，请按照它的要求进行操作。
    </p>
    <p>
        在模拟器或真机上运行项目，确保它可以被正确地编译及运行。
    </p>
    <h2>
        模拟不同的SDK版本
    </h2>
    <p>
        我们想尝试在不同Android的版本上运行样本app，但基本上不可能有支持各个API级别SDK的Android设备。因此，首先我们需要学习如何设置不同SDK版本的模拟器。
    </p>
    <p>
        为设置模拟器，在
        <em>
            Android Studio的工具栏
        </em>
        上，找到
        <em>
            AVD (Android Virtual Device) Manager
        </em>
        。
    </p>
    <h3>
        创建一个虚拟设备
    </h3>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVD.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVD.jpeg"
            alt="" width="436" height="80" class="aligncenter size-full wp-image-171199">
        </a>
    </p>
    <p>
        如果看不到工具栏，请选择
        <em>
            View / Toolbar
        </em>
        来打开它。你还可以通过
        <em>
            Tools / Android / AVD Manager
        </em>
        来打开AVD管理器。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASCreateAVD.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASCreateAVD-650x345.jpeg"
            alt="" width="650" height="345" class="aligncenter size-large wp-image-171202"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASCreateAVD-650x345.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASCreateAVD-480x255.jpeg 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASCreateAVD.jpeg 1080w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        点击
        <em>
            Create a virtual device
        </em>
        按钮，就可以打开
        <em>
            Virtual Device Configuration
        </em>
        窗口中的
        <em>
            Select Hardware
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASPickDevice.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASPickDevice-650x437.jpeg"
            alt="" width="650" height="437" class="aligncenter size-large wp-image-171206"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASPickDevice-650x437.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASPickDevice-476x320.jpeg 476w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASPickDevice.jpeg 1000w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        选择你需要的设备，并点击
        <em>
            Next
        </em>
        。就会打开
        <em>
            System Image
        </em>
        ，展示出当前推荐的系统镜像。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage-650x437.jpeg"
            alt="" width="650" height="437" class="aligncenter size-large wp-image-171207"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage-650x437.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage-476x320.jpeg 476w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage.jpeg 1000w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        在
        <em>
            x86 Images
        </em>
        选项卡中会展示出所有x86模拟器的镜像。而在
        <em>
            Other Images
        </em>
        选项卡中，则会展示出ARM和x86的模拟器镜像。
    </p>
    <div class="note">
        <em>
            注意：
        </em>
        建议你始终都使用x86的镜像。这在大多数的PC和Mac的电脑上运行速度都是最快的
    </div>
    <h3>
        下载一个系统镜像
    </h3>
    <p>
        要下载尚未安装的系统镜像，请点击发版名称上的
        <em>
            Download
        </em>
        链接。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDImageDownload.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDImageDownload-650x437.jpeg"
            alt="" width="650" height="437" class="aligncenter size-large wp-image-171208"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDImageDownload-650x437.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDImageDownload-476x320.jpeg 476w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDImageDownload.jpeg 1000w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        注意Android平台现在有
        <a href="https://source.android.com/source/build-numbers.html">
            15个主要的SDK版本
        </a>
        。从Android 1.5开始，SDK的主要版本都是以一个糖果作为主题进行开发的。Google已设法按照字母的顺序去选择这些代号的名称。他们到现在还未用完糖果的名称 :]
    </p>
    <p>
        Android SDK的每个版本（主版本或是小版本）都有一个整数值来唯一地标识它。这个唯一的标识符被称为API级别。API级别越高，版本就越新。对于开发者来说，API级别是非常重要的，因为它决定了app可以运行在哪些设备上。
    </p>
    <p>
        一起来看一个Android 8.0的例子。我们知道：
    </p>
    <ul>
        <li>
            它是Android SDK的最新版本
        </li>
        <li>
            它的版本号是8.0
        </li>
        <li>
            代号是Oreo
        </li>
        <li>
            API级别是26
        </li>
    </ul>
    <p>
        在本教程中，我们至少需要两个模拟器，一个的API级别为15，另一个的API级别为26。
    </p>
    <p>
        回到Android Studio中的"System Image"界面，为每个本教程中你需要用到
        <em>
            （级别15和级别26）
        </em>
        ，但尚未下载的SDK版本上，点击
        <em>
            Download
        </em>
        按钮。然后选择级别为26的系统镜像，并点击
        <em>
            下一步
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage-650x437.jpeg"
            alt="" width="650" height="437" class="aligncenter size-large wp-image-171207"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage-650x437.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage-476x320.jpeg 476w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDSystemImage.jpeg 1000w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        在下一页点击
        <em>
            Finish
        </em>
        按钮。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDVerify.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDVerify-650x437.jpeg"
            alt="" width="650" height="437" class="aligncenter size-large wp-image-171215"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDVerify-650x437.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDVerify-476x320.jpeg 476w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASAVDVerify.jpeg 1000w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        重复相同的步骤来设置API级别为15的模拟器。如果你无法下载API级别15，也可以选择API级别16来代替。
    </p>
    <h3>
        首次运行
    </h3>
    <p>
        尝试在API级别为26的模拟器上运行实例app：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509473618.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509473618-281x500.png"
            alt="First Run" width="281" height="500" class="aligncenter size-large wp-image-175532"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509473618-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509473618-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/11/Screenshot_1509473618.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        看起来不错？但如果你尝试在API级别低于26的设备上运行，是无法成功的。这是因为这个app只能运行在API级别大于等于26的设备上，这对较旧的设备来说就是一个糟糕的消息了。下面，我们就会学习如何将这个app向下支持到API级别为14的设备。
    </p>
    <h2>
        SDK版本和API的级别
    </h2>
    <p>
        就像前面所提到的，API级别是用于标识Android SDK特定版本的一个唯一的整数。我们来看一下如何在Android Studio中指定API的级别，以编译和发布一个app。
    </p>
    <p>
        打开app模块中的
        <em>
            build.gradle
        </em>
        ：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASgradleInitial.jpeg"
        target="_blank">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASgradleInitial-650x350.jpeg"
            alt="build.gradle" width="650" height="350" class="aligncenter size-large wp-image-171217"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASgradleInitial-650x350.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASgradleInitial-480x258.jpeg 480w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        我们可以在这里看到三个重要的属性：
    </p>
    <ul>
        <li>
            <em>
                minSdkVersion
            </em>
            是app可以兼容最低的API级别。如果系统API的级别低于此属性中指定的值，Android就会阻止用户安装这个app。在Android中必须得设置这个属性。
        </li>
        <li>
            <em>
                targetSdkVersion
            </em>
            是app针对的API级别。这个属性会通知系统，你已针对目标版本进行了测试。如果未指定targetSdkVersion，它的值就默认等于minSdkVersion。
        </li>
        <li>
            <em>
                compileSdkVersion
            </em>
            指定了编译app的API级别。
        </li>
    </ul>
    <p>
        这些属性都可以在app模块的
        <em>
            build.gradle
        </em>
        文件中进行调整。
    </p>
    <div class="note">
        <em>
            注意SDK的预览版：
        </em>
        当你将
        <em>
            compileSdkVersion
        </em>
        设置为Android framework的
        <em>
            预览版本
        </em>
        时，清楚Android Studio将强使
        <em>
            minSdkVersion
        </em>
        和
        <em>
            targetSdkVersion
        </em>
        成为与
        <em>
            compileSdkVersion
        </em>
        相同的字符串是非常重要的。这是非常必要的，可以避免你把app上传到Google Play商店中。因此，如果
        <em>
            compileSdkVersion
        </em>
        被设置成预览版，你就只能在运行该
        <em>
            预览版
        </em>
        的模拟器上运行这个app，不可在较旧的设备上运行。
    </div>
    <h3>
        向后的兼容性
    </h3>
    <p>
        The Android SDK is by default forward compatible but not backward
        compatible — 
        this means that an application that is built with and supports
        a minimum SDK version of 3.0 can be installed on any device running
        Android versions 3.0 and upwards. 
        But not on devices running Android versions below 3.0.
    </p>
    <p>
        Since the Android SDK is not backward compatible, 
        you should choose the&nbsp;minimum SDK carefully. 
        This means striking a balance between supporting a wide
        range of devices and designing an app that implements&nbsp;useful features in later SDK versions.
    </p>
    <p>
        For example, when Android 3.0 was released in 2011,
        the Action Bar was unleashed on the Android Community. 
        Since the Action Bar was only supported in Android 3.0 and later, 
        using it in an app meant choosing either a cool user interface or supporting devices that ran older versions of the SDK.
        Sometimes you can’t have your&nbsp;honeycomb&nbsp;and eat it too :[
    </p>
    <p>
        Or can you? To help with the Action Bar issue, 
        the Android Support Library introduced a backward
        - compatible version in the v7-appcompat support library.
        So it would allow developers to support older versions of the SDK and still use the latest Action Bar APIs in their apps. 
        Sweet! Honeycomb for everyone!
    </p>
    <p>
        Let’s take a deeper look at what the Support Library does and how it works.
    </p>
    <div class="note">
        <em>
            Note on picking minimum sdk version:
        </em>
        Google provides a
        <a href="https://developer.android.com/about/dashboards/index.html" target="_blank">
            Dashboard
        </a>
        that breaks down the user
        <br>
        distribution percentage per api level. 
        You can use this to help target a good percentage of users.
    </div>
    <h2>
        Android Support Libraries
    </h2>
    <p>
        A wide range of components make up what is referred to as the “Support
        Library” or “Support Libraries,” and they can be categorized in two groups:
    </p>
    <ul>
        <li>
            The
            <em>
                AppCompat
            </em>
            library: The intention here is to make sure all (or most) of the framework APIs for the latest API Level have been backported to earlier versions and can be found in this single library. 
            The first version of AppCompat was released at Google I/O 2013.
            <p>
                The goal of this first release was to allow developers to backport the ActionBar to devices running IceScreamSandwich level. 
                This gave API parity to the framework across as many API Levels as possible. 
                Since then, the AppCompat library has continued to evolve. 
                And with Android L the support library is now at the point where the API is equivalent to the framework itself 
                — the first time that has ever happened :]
            </p>
        </li>
        <li>
            <em>
                Others
            </em>
            : The rest of the libraries that make up the Support Library essentially provide new functionality with the same consideration for backward compatibility 
            (palette, gridview, gridlayout, recycler view, material design widgets).
        </li>
    </ul>
    <p>
        When you break these up into independent libraries, 
        you can pick and choose the ones you need in your project. 
        It’s important to note that each support library is backward-compatible to a specific API Level. 
        And they are usually named based on which API Level they are backward-compatible to. 
        For example,
        <em>
            v7-appcompat
        </em>
        provides backward compatibility to API Level 7.
    </p>
    <p>
        You can find the full list of components that fall under the Support Library in the
        <a href="http://developer.android.com/tools/support-library/features.html"
        target="_blank">
            Android documentation
        </a>
        .
    </p>
    <div class="note">
        <em>
            Note: Support Library minimum sdk change:
        </em>
        Beginning with Support Library release 26.0.0,
        <a href="https://developer.android.com/topic/libraries/support-library/index.html#api-versions"
        target="_blank">
            Google has changed the minimum supported level to Api 14
        </a>
        . This means that your minimum sdk version cannot be set below Api level 14 when using version 26.0.0+ of the Support Library.
    </div>
    <h2>
        How to Use an Android Support Library
    </h2>
    <p>
        Time to see an Android support library in action! Open
        <em>
            MainActivity.kt
        </em>
        . As you may have noticed in the
        <em>
            onCreate()
        </em>
        method, the app uses a
        <em>
            Toolbar
        </em>
        (which is part of the material design patterns) instead of an
        <em>
            Action Bar
        </em>
        .
    </p>
    <p>
        The
        <em>
            Toolbar
        </em>
        was added in API 21 (Android Lollipop) as a flexible widget that
        can be used anywhere in layouts, 
        be animated and change in size, 
        unlike the Action Bar.
    </p>
    <p>
        Thanks to AppCompat, 
        that feature has been back-ported all the way to API 14, 
        which is code-named Ice Cream Sandwich (are you hungry yet?). 
        You’re going to use the v7-appcompat support library to extend your app’s compatibility to a minSdkVersion of 15.
    </p>
    <h3>
        Update Build File
    </h3>
    <p>
        First add
        <em>
            google()
        </em>
        to the Maven repositories in your project-level
        <em>
            build.gradle
        </em>
        file, if it’s not already there:
    </p>
    <pre lang="groovy" class="language-groovy">repositories {
    jcenter()
    google()
}
</pre>
    <p>
        Now, open
        <em>
            build.gradle
        </em>
        for the app module and add the following to the dependencies section:
    </p>
    <pre lang="groovy" class="language-groovy">implementation "com.android.support:appcompat-v7:26.0.1"</pre>
    <p>
        By adding this, you’re declaring the appcompat-v7 support library as a
        dependency for your application. 
        You can ignore the warning to use a newer version of the Support library. 
        Though you may update, 
        it’s recommended you stick to the one in this tutorial.
    </p>
    <p>
        Next, change the minSdkVersion attribute to 15.
    </p>
    <pre lang="groovy" class="language-groovy">minSdkVersion 15</pre>
    <p>
        Here you’re declaring that the app should be able to run on devices with Android SDK version 4.0.4. 
        Now try running your application on an emulator running API Level 15.
        You should see the following exceptions in the logcat:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/ASToolbarError.jpeg"
        target="_blank">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ASToolbarError-650x352.jpeg"
            alt="" width="650" height="352" class="aligncenter size-large wp-image-171357"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/ASToolbarError-650x352.jpeg 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASToolbarError-480x260.jpeg 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/ASToolbarError.jpeg 1317w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        The important line to look for is:
    </p>
    <pre lang="java" class="language-java hljs">Caused by: java.lang.ClassNotFoundException: android.widget.Toolbar</pre>
    <p>
        The
        <code>
            ClassNotFoundException
        </code>
        error indicates that there is no such class in the SDK version you’re running the app against. 
        Indeed, it’s only available in API Level 21, 
        while you’re currently running API Level 15.
    </p>
    <h3>
        Update For Backward Compatibility
    </h3>
    <p>
        You’re going to update the code to use the backward
        - compatible version of Toolbar. 
        In
        <em>
            MainActivity.kt
        </em>
        , and update the
        <code>
            android.widget.Toolbar
        </code>
        import statement to match the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v7.widget.Toolbar</pre>
    <p>
        This replaces the SDK import with one from the AppCompat library.
    </p>
    <p>
        Next import the
        <em>
            AppCompatActivity
        </em>
        from the AppCompat library:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v7.app.AppCompatActivity</pre>
    <p>
        Next update the&nbsp;
        <em>
            MainActivity
        </em>
        &nbsp;class definition line so that it inherits from
        <em>
            AppCompatActivity
        </em>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> : <span class="hljs-type">AppCompatActivity</span></span>(), ContinentSelectedListener</pre>
    <p>
        Once again, you’re replacing a class from the latest SDKs with one that exists in the support library.
    </p>
    <p>
        You now need to work through the class and replace some method calls with their support library equivalents:
    </p>
    <ul>
        <li>
            Find the call to
            <code>
                setActionBar(toolbar)
            </code>
            at the end of the
            <code>
                onCreate()
            </code>
            method body and update it to
            <code>
                setSupportActionBar(toolbar)
            </code>
            .
        </li>
        <li>
            Find the calls to
            <code>
                actionBar?
            </code>
            in
            <code>
                onContinentSelected()
            </code>
            ,
            <code>
                goToContinentList()
            </code>
            , and
            <code>
                onBackPressed()
            </code>
            and replace both of them with
            <code>
                supportActionBar?
            </code>
            .
        </li>
        <li>
            Replace the calls to
            <code>
                fragmentManager()
            </code>
            in
            <code>
                onContinentSelected()
            </code>
            and
            <code>
                goToContinentList()
            </code>
            with
            <code>
                supportFragmentManager()
            </code>
            .
        </li>
    </ul>
    <h3>
        Update Fragment Classes
    </h3>
    <p>
        Open
        <em>
            DescriptionFragment.kt
        </em>
        and
        <em>
            MainFragment.kt
        </em>
        , find the following line:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.app.Fragment</pre>
    <p>
        and update to match the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v4.app.Fragment</pre>
    <p>
        Here you’re using the support version of the
        <code>
            Fragment
        </code>
        class instead of the one in the main SDK. 
        The latter can only be used in apps with a minSdkVersion of 14 and above.
    </p>
    <div class="note">
        <em>
            Note:
        </em>
        AppCompat v7 depends on the v4 Support Library. 
        That’s why you can also use all the APIs in the
        <code>
            android.support.v4.app
        </code>
        package.
    </div>
    <p>
        So far you’ve replaced all the main API calls with corresponding methods from the support library. 
        Next you will need to update your layout files to use the Support Library.
    </p>
    <p>
        In the
        <em>
            res / layout
        </em>
        folder, open
        <em>
            toolbar_custom.xml
        </em>
        and do the following:
    </p>
    <ul>
        <li>
            Change
            <code>
                android.widget.Toolbar
            </code>
            to
            <code>
                android.support.v7.widget.Toolbar
            </code>
        </li>
        <li>
            Change
            <code>
                ?android:attr/actionBarSize
            </code>
            to
            <code>
                ?attr/actionBarSize
            </code>
        </li>
    </ul>
    <p>
        Again, all this does is change the package name from android to v7-appcompat.
    </p>
    <p>
        Now that all of the compile-time errors have been checked and fixed, try to run the app again. 
        You will now get the following run-time error:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">java.lang.RuntimeException: Unable to start activity ComponentInfo{com.raywenderlich.continents/com.raywenderlich.continents.MainActivity}: java.lang.IllegalStateException: You need to use a Theme.AppCompat theme (or descendant) with <span class="hljs-keyword">this</span> activity.
</pre>
    <h3>
        Update Styles
    </h3>
    <p>
        The error message is pretty self-explanatory, 
        but why do you need to use the AppCompat theme? 
        A feature from the Lollipop release of AppCompat is the different approach to theming. 
        One of the interesting things about this is the capability to get an L-friendly version of your app on prior versions. 
        If an app uses the framework version of everything (
        <em>
            Activity
        </em>
        instead of
        <em>
            AppCompatActivity
        </em>
        for example), it would only get the material theme on phones with the L release. 
        Devices with prior releases would get the default theme for those releases. 
        The goal of the AppCompat theming feature is to have a consistent experience across all devices.
    </p>
    <p>
        In the
        <em>
            res\values
        </em>
        folder, open
        <em>
            styles.xml
        </em>
        , and change
        <code>
            android:Theme.Black.NoTitleBar
        </code>
        to
        <code>
            Theme.AppCompat.NoActionBar
        </code>
        .
    </p>
    <p>
        Now build and run. 
        You can test the app on an API 15 device or emulator as well.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/61-e1444816686495.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/61-284x500.png"
            alt="" width="284" height="500" class="aligncenter size-large wp-image-118425">
        </a>
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/10/continent_view_2.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/10/continent_view_2-283x500.png"
            alt="" width="283" height="500" class="aligncenter size-large wp-image-119880"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/10/continent_view_2-283x500.png 283w, https://koenig-media.raywenderlich.com/uploads/2015/10/continent_view_2-181x320.png 181w, https://koenig-media.raywenderlich.com/uploads/2015/10/continent_view_2.png 774w"
            sizes="(max-width: 283px) 100vw, 283px">
        </a>
    </p>
    <p>
        Well done! The sample app is now backward compatible.
        <a href="https://source.android.com/source/build-numbers.html">
            Ice cream sandwich and lollipops and jelly beans
        </a>
        for everyone!
    </p>
    <p>
        Let’s throw in some cards to make the detail screen look nicer.
    </p>
    <h2>
        How to Use the Card View Support Library
    </h2>
    <p>
        Open
        <em>
            build.gradle
        </em>
        for the app module and add the following to the dependencies section:
    </p>
    <pre lang="xml" class="language-xml hljs">implementation "com.android.support:cardview-v7:26.0.1"</pre>
    <p>
        Adding this declares the v7-cardview support library as a dependency for the application.
    </p>
    <p>
        Open the
        <em>
            fragment_description.xml
        </em>
        file and place the ImageView in a CardView:
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.v7.widget.CardView</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/card_view"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"0dp"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"center"</span>
    <span class="hljs-attr">android:layout_weight</span>=<span class="hljs-string">"1"</span>
    <span class="hljs-attr">card_view:cardBackgroundColor</span>=<span class="hljs-string">"#316130"</span>
    <span class="hljs-attr">card_view:cardElevation</span>=<span class="hljs-string">"20dp"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">ImageView</span>
      <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/continentImage"</span>
      <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"match_parent"</span>
      <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"match_parent"</span>
      <span class="hljs-attr">android:contentDescription</span>=<span class="hljs-string">"@string/continent_image_description"</span>
      <span class="hljs-attr">android:paddingBottom</span>=<span class="hljs-string">"@dimen/activity_vertical_margin"</span>
      <span class="hljs-attr">android:src</span>=<span class="hljs-string">"@drawable/africa"</span> /&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">android.support.v7.widget.CardView</span>&gt;</span>
</pre>
    <p>
        Notice that when using widgets from the Support Library, some XML attributes
        (
        <code>
            cardBackgroundColor
        </code>
        and
        <code>
            cardElevation
        </code>
        for the CardView) are not prefixed with “android.” 
        That’s because they come from the Support Library API as opposed to the Android framework.
        Hit
        <em>
            option+return
        </em>
        (or
        <em>
            Alt+Enter
        </em>
        on PC) if you need to setup the
        <code>
            card_view
        </code>
        namespace in the xml file.
    </p>
    <p>
        Now, build and run the project:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/card_view.jpeg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/card_view-281x500.jpeg"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-171399"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/card_view-281x500.jpeg 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/card_view-180x320.jpeg 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/card_view.jpeg 322w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        Cool, you’ve added this new-style cardview to your app and using the compatibility library it works from modern versions of Android, 
        right back to ancient API-level 15.
    </p>
    <h2>
        Did You Say Material Design?
    </h2>
    <p>
        You’ve successfully used the AppCompat theming to give the app the Android Lollipop look and feel across a wide range of SDK versions. In addition to these elements, the
        <a href="https://www.google.com/design/spec/material-design/introduction.html"
        target="_blank">
            Material Design specification
        </a>
        includes many more patterns and widgets not contained in AppCompat. 
        This is where the Design Library comes into play. 
        It provides widgets such as navigation drawers, 
        floating action buttons, snackbars and tabs. 
        Let’s include it in the project and add a floating action button.
    </p>
    <p>
        In
        <em>
            build.gradle
        </em>
        add the following in the
        <code>
            dependencies
        </code>
        section:
    </p>
    <pre lang="groovy" class="language-groovy">implementation "com.android.support:design:26.0.1"</pre>
    <p>
        Next add the following XML element above the closing tag for FrameLayout in
        <em>
            fragment_description.xml
        </em>
        :
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.design.widget.FloatingActionButton</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/search_button"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"bottom|end"</span>
    <span class="hljs-attr">android:layout_margin</span>=<span class="hljs-string">"16dp"</span>
    <span class="hljs-attr">android:src</span>=<span class="hljs-string">"@drawable/ic_search_white_18dp"</span> /&gt;</span></pre>
    <p>
        Build and run. You will see the floating button as expected.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/fab-button.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/fab-button-281x500.png"
            alt="fab-button" width="281" height="500" class="aligncenter size-large wp-image-121869"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/fab-button-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2015/11/fab-button-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2015/11/fab-button.png 1440w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        Backport All the Things?
    </h2>
    <p>
        Some features in the latest releases of the SDK are just too complex to backport. 
        Ultimately, it’s your call to strike the right balance between performance and usability. 
        If you find yourself wanting to use an unavailable framework API, 
        you can check for the API Level at run-time.
    </p>
    <p>
        For the following snippet from
        <code>
            MainActivity
        </code>
        , import the classes from the base package instead of the Support Library package. Then in the
        <code>
            onContinentSelected
        </code>
        , add the following after the description fragment is instantiated but
        before the fragment transaction:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">if</span> (Build.VERSION.SDK_INT &gt;= Build.VERSION_CODES.N) {
  descriptionFragment.enterTransition = Fade()
  mainFragment?.exitTransition = Fade()
  descriptionFragment.exitTransition = Slide(Gravity.BOTTOM)
  mainFragment?.reenterTransition = Fade()
  descriptionFragment.allowReturnTransitionOverlap = <span class="hljs-literal">true</span>
}
</pre>
    <p>
        Build and run on both emulators. 
        You should see no animations on the emulator running API Level 15, 
        but notice the fade in and slide out on the emulators running API Level 25 and above:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/side-by-side.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/side-by-side.gif"
            alt="side-by-side" width="600" height="338" class="aligncenter size-full wp-image-121856">
        </a>
    </p>
    <h2>
        Where To Go From Here?
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
        Congratulations! 
        Finally you’ve learned about Android SDK versions and their sweet code names. 
        You made an API Level 26 application backward-compatible to API Level 15, 
        and used the cardview and design library to add additional components. 
        You might also have a sugar craving :]
    </p>
    <div id="attachment_123193" style="width: 371px" class="wp-caption aligncenter">
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/jelly-beans-939754_1280.jpg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/jelly-beans-939754_1280-361x320.jpg"
            alt="Blame Android." width="361" height="320" class="size-medium wp-image-123193"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/jelly-beans-939754_1280-361x320.jpg 361w, https://koenig-media.raywenderlich.com/uploads/2015/12/jelly-beans-939754_1280-564x500.jpg 564w, https://koenig-media.raywenderlich.com/uploads/2015/12/jelly-beans-939754_1280.jpg 1280w"
            sizes="(max-width: 361px) 100vw, 361px">
        </a>
        <p>
        </p>
        <p class="wp-caption-text">
            Blame Android.
        </p>
    </div>
    <p>
        The final project for this Android SDK Versions tutorial can be downloaded
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/continents-final.zip">
            here
        </a>
        .
    </p>
    <p>
        If you are interested in Android SDK version history, check out
        <a href="https://en.wikipedia.org/wiki/Android_version_history" target="_blank">
            this wikipedia page
        </a>
        or the
        <a href="http://developer.android.com/about/versions" target="_blank">
            versions
        </a>
        page on the Android developer site. 
        You can also read further about the minSdkVersion and targetSdkVersion attributes from the
        <a href="http://developer.android.com/guide/topics/manifest/uses-sdk-element.html"
        target="_blank">
            manifest
        </a>
        page on the developer site. 
        Finally, check out the developer pages on
        <a href="https://developer.android.com/tools/support-library/index.html"
        target="_blank">
            Support libraries
        </a>
        and its
        <a href="https://developer.android.com/tools/support-library/features.html"
        target="_blank">
            feature list
        </a>
        .
    </p>
</div>