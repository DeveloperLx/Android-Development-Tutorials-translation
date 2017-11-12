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
        Android的SDK默认是向前支持的，但并不向后支持 - 这意味着一个构建于且支持最低SDK版本为3.0的app，同样可以安装并运行在高于3.0版本的设备上，但不能运行在低于3.0版本的设备上。
    </p>
    <p>
        因此，你应当慎重地选择最低的SDK版本。这意味这要在支持尽可能多的设备，与利用新版SDK功能之间进行利弊的权衡。
    </p>
    <p>
        例如，Android 3.0是在2011年发布的，同时在Android社区中则发布了Action Bar。由于Action Bar只支持Android 3.0及以上的版本，在app中使用它，就意味着要在较酷的用户界面，与支持SDK版本较老的设备之间进行选择。鱼和熊掌不可兼得 :[
    </p>
    <p>
        那该怎么办？为了解决这个问题，Android的v7-appcompat支持库中引入了一个向后兼容的版本。它能够让开发者即支持较老版本的SDK，又可以在app中使用最新的Action Bar API。是不是很棒！
    </p>
    <p>
        让我们来深入理解一下支持库的工作原理吧、
    </p>
    <div class="note">
        <em>
            注意如何挑选最低sdk版本：
        </em>
        Google提供了一个
        <a href="https://developer.android.com/about/dashboards/index.html" target="_blank">
            Dashboard
        </a>
        ，用来展示每个api级别用户所占的百分比。你可以参考它来确定最低sdk的版本。
    </div>
    <h2>
        Android支持库
    </h2>
    <p> 
        各种各样的组件构成了“支持库”，它们可以被分为两组：
    </p>
    <ul>
        <li>
            <em>
                AppCompat
            </em>
            库：用来确保所有的（或大多数的）最新的API级别，可以向后支持到早期的版本，并且可以在这个库中被找到。AppCompat的第一个版本是在Google I/O 2013时发布的。
            <p>
                这个版本的目标，是让开发者能够将ActionBar移植到运行IceScreamSandwich级别SDK的设备上，让其相关的API可以跨越尽可能多的API级别。从此之后，AppCompat持续地进行改进。现在Android L的相应支持库的API，已可以等价于这个框架的本身的 - 这是有史以来的第一次 :]
            </p>
        </li>
        <li>
            <em>
                Others
            </em>
            ：构成支持库的剩余部分，在考虑了向后兼容的情形下，提供了新的功能（palette，gridview，gridlayout，recycler view，material design widgets）。
        </li>
    </ul>
    <p>
        你可以将它们拆分成若干独立的库，而在项目中用到时选择相应的即可。注意，每个支持库只能向后兼容到一个特定的API级别。它们通常都以可以向后兼容到的API级别来进行命名。例如，
        <em>
            v7-appcompat
        </em>
        就提供了直到API级别为7的向后兼容。
    </p>
    <p>
        你可以在
        <a href="http://developer.android.com/tools/support-library/features.html"
        target="_blank">
            Android文档
        </a>
        中，找到各个组件对应的支持库的列表。
    </p>
    <div class="note">
        <em>
            注意：支持库最低sdk的变化：
        </em>
        从支持库的26.0.0版本开始，
        <a href="https://developer.android.com/topic/libraries/support-library/index.html#api-versions"
        target="_blank">
            Google已将最低的支持级别修改为Api 14
        </a>
        。这意味着你在使用了26.0.0+的支持库时，就不可以将最低sdk版本设置得低于Api级别14了。
    </div>
    <h2>
        如何使用Android支持库
    </h2>
    <p>
        该行动起来去添加Android支持库了！打开
        <em>
            MainActivity.kt
        </em>
        。就像你在
        <em>
            onCreate()
        </em>
        方法中所看到的，它使用一个
        <em>
            Toolbar
        </em>
        （它是质感设计的一部分）来替代
        <em>
            Action Bar
        </em>
        。
    </p>
    <p>
        <em>
            Toolbar
        </em>
        是在API 21(Android Lollipop)时被引入的，作为一个能够在布局中任意位置被使用的灵活的组件，可以对它的大小添加动画效果，这点于Action Bar是不同的。
    </p>
    <p>
        感谢AppCompat，它让这个功能向后支持到了API 14的版本（Ice Cream Sandwich）。因此你就可以使用v7的appcompat支持库，来将你的app兼容性扩展到minSdkVersion为15。
    </p>
    <h3>
        更新Build文件
    </h3>
    <p>
        首先，在你的项目级别
        <em>
            build.gradle
        </em>
        文件中添加
        <em>
            google()
        </em>
        （如果它还尚不存在）：
    </p>
    <pre lang="groovy" class="language-groovy">repositories {
    jcenter()
    google()
}
</pre>
    <p>
        现在，打开app模块的
        <em>
            build.gradle
        </em>
        ，并在dependencies中添加下列的代码：
    </p>
    <pre lang="groovy" class="language-groovy">implementation "com.android.support:appcompat-v7:26.0.1"</pre>
    <p>
        这样你就为此app声明了对appcompat-v7支持库的依赖。你可以忽略这里出现的警告。尽管可以进行更新，建议你在本教程中还是使用这个。
    </p>
    <p>
        接下来，将minSdkVersion修改为15。
    </p>
    <pre lang="groovy" class="language-groovy">minSdkVersion 15</pre>
    <p>
        这样你就声明了这个app可以运行在Android SDK为4.0.4版本的设备上。现在，尝试在API级别为15的模拟器上运行这个app。你会看到在logcat中，出现了下列的异常：
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
        关键的一行在这里：
    </p>
    <pre lang="java" class="language-java hljs">Caused by: java.lang.ClassNotFoundException: android.widget.Toolbar</pre>
    <p>
        <code>
            ClassNotFoundException
        </code>
        错误表示你运行app的SDK版本中没有这样的类。事实上，它只能在API级别21及以上的版本中运行，而你当前运行的API基本是15。
    </p>
    <h3>
        添加向后兼容
    </h3>
    <p>
        现在让我们来使用向后兼容版本的Toolbar。在
        <em>
            MainActivity.kt
        </em>
        中，将
        <code>
            android.widget.Toolbar
        </code>
        的import语句更新为下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v7.widget.Toolbar</pre>
    <p>
        这样就将SDK的import替换成了AppCompat的版本。
    </p>
    <p>
        接下来从AppCompat库中import
        <em>
            AppCompatActivity
        </em>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v7.app.AppCompatActivity</pre>
    <p>
        然后修改代码，使
        <em>
            MainActivity
        </em>
        类继承自
        <em>
            AppCompatActivity
        </em>
        ：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainActivity</span> : <span class="hljs-type">AppCompatActivity</span></span>(), ContinentSelectedListener</pre>
    <p>
        这样，你就将一个来自最新版本SDK中的类，替换成了在支持库中的类。
    </p>
    <p>
        现在你需要对这个类进行排查，将其中一些方法的调用，替换成支持库中的相应的版本：
    </p>
    <ul>
        <li>
            在
            <code>
                onCreate()
            </code>
            方法的底部，将
            <code>
                setActionBar(toolbar)
            </code>
            更新为
            <code>
                setSupportActionBar(toolbar)
            </code>
            。
        </li>
        <li>
            在
            <code>
                onContinentSelected()
            </code>
            ，
            <code>
                goToContinentList()
            </code>
            ，和
            <code>
                onBackPressed()
            </code>
            中，将
            <code>
                actionBar?
            </code>
            替换为
            <code>
                supportActionBar?
            </code>
            。
        </li>
        <li>
            在
            <code>
                onContinentSelected()
            </code>
            和
            <code>
                goToContinentList()
            </code>
            中，将
            <code>
                fragmentManager()
            </code>
            替换为
            <code>
                supportFragmentManager()
            </code>
            。
        </li>
    </ul>
    <h3>
        更新Fragment类
    </h3>
    <p>
        打开
        <em>
            DescriptionFragment.kt
        </em>
        和
        <em>
            MainFragment.kt
        </em>
        ，找到下面的这行代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.app.Fragment</pre>
    <p>
        将其更新为：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> android.support.v4.app.Fragment</pre>
    <p>
        这样你就使用了支持版本的
        <code>
            Fragment
        </code>
        替换了在主SDK中的。后者只可以在minSdkVersion为14及以上版本的app中进行使用。
    </p>
    <div class="note">
        <em>
            注意：
        </em>
        AppCompat v7依赖于v4的支持库。这就是你也能够使用所有
        <code>
            android.support.v4.app
        </code>
        包中的API的原因。
    </div>
    <p>
        你已将所有主API中的代码，替换成了在支持库中的版本。下面你需要用支持库去更新布局文件。
    </p>
    <p>
        在
        <em>
            res / layout
        </em>
        目录下，打开
        <em>
            toolbar_custom.xml
        </em>
        并添加下列的代码：
    </p>
    <ul>
        <li>
            将
            <code>
                android.widget.Toolbar
            </code>
            修改为
            <code>
                android.support.v7.widget.Toolbar
            </code>
        </li>
        <li>
            将
            <code>
                ?android:attr/actionBarSize
            </code>
            修改为
            <code>
                ?attr/actionBarSize
            </code>
        </li>
    </ul>
    <p>
        这样，就将所有的包名替换成了v7-appcompat的版本。
    </p>
    <p>
        现在，所有的编译时错误都被修复了，尝试再次运行app。你会发现下列的运行时错误：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">java.lang.RuntimeException: Unable to start activity ComponentInfo{com.raywenderlich.continents/com.raywenderlich.continents.MainActivity}: java.lang.IllegalStateException: You need to use a Theme.AppCompat theme (or descendant) with <span class="hljs-keyword">this</span> activity.
</pre>
    <h3>
        更新风格
    </h3>
    <p>
        错误的信息相当明了，但是，为何你需要使用AppCompat的主题？AppCompat的Lollipop版本中，有一个功能是有所不同的。
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
        在
        <em>
            res/values
        </em>
        目录下，打开
        <em>
            styles.xml
        </em>
        ，并将
        <code>
            android:Theme.Black.NoTitleBar
        </code>
        修改为
        <code>
            Theme.AppCompat.NoActionBar
        </code>
        。
    </p>
    <p>
        运行项目，现在它就可以运行在API级别为15的设备或模拟器上了。
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
        真棒！这个app现在已经可以向后兼容到
        <a href="https://source.android.com/source/build-numbers.html">
            Ice cream sandwich，lollipops和jelly beans
        </a>
        的版本了！
    </p>
    <p>
        我们来添加一些卡片，让这个详情页看起来更棒。
    </p>
    <h2>
        如何使用Card View支持库
    </h2>
    <p>
        打开app模块的
        <em>
            build.gradle
        </em>
        ，并添加下列的代码到dependencies中：
    </p>
    <pre lang="xml" class="language-xml hljs">implementation "com.android.support:cardview-v7:26.0.1"</pre>
    <p>
        这样就添加了v7-cardview支持库到app的依赖中。
    </p>
    <p>
        打开
        <em>
            fragment_description.xml
        </em>
        文件，并将ImageView放置到一个CardView中：
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
        注意，当使用支持库中的控件时，一些XML属性（CardView的
        <code>
            cardBackgroundColor
        </code>
        和
        <code>
            cardElevation
        </code>
        ）就不再以“android”为前缀了。这是因为他们是来自于支持库中的API，并非来自于Android的框架。如果你需要在xml文件中设置
        <code>
            card_view
        </code>
        这个命名空间，可以按下
        <em>
            option+return
        </em>
        （在PC中是
        <em>
            Alt+Enter
        </em>
        ）键。
    </p>
    <p>
        现在，运行项目：
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
        酷，你现在已使用兼容库添加了新风格的cardview到你的app上，使它能够兼容古老的API级别15。
    </p>
    <h2>
        关于质感设计
    </h2>
    <p>
        你已成功地使用AppCompat的主题，带给了app像Android Lollipop一样的外表和体验，并且能够运行在很多的SDK版本之上。除了这些元素外，
        <a href="https://www.google.com/design/spec/material-design/introduction.html"
        target="_blank">
            Material Design specification
        </a>
        还包含了很多AppCompat未包含的模式和组件。现在就是设计库该登场的时候了。它提供了很多的小控件，诸如navigation drawer，floating action button，snackbar和tab等等。让我们把它引入到工程中，并添加一个floating action button。
    </p>
    <p>
        在
        <em>
            build.gradle
        </em>
        中，添加下列的代码到
        <code>
            dependencies
        </code>
        中：
    </p>
    <pre lang="groovy" class="language-groovy">implementation "com.android.support:design:26.0.1"</pre>
    <p>
        然后在
        <em>
            fragment_description.xml
        </em>
        中，添加下列的XML元素到FrameLayout的关闭标签前：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">android.support.design.widget.FloatingActionButton</span>
    <span class="hljs-attr">android:id</span>=<span class="hljs-string">"@+id/search_button"</span>
    <span class="hljs-attr">android:layout_width</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_height</span>=<span class="hljs-string">"wrap_content"</span>
    <span class="hljs-attr">android:layout_gravity</span>=<span class="hljs-string">"bottom|end"</span>
    <span class="hljs-attr">android:layout_margin</span>=<span class="hljs-string">"16dp"</span>
    <span class="hljs-attr">android:src</span>=<span class="hljs-string">"@drawable/ic_search_white_18dp"</span> /&gt;</span></pre>
    <p>
        运行项目。你就能看到期望中的floating button了。
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
        向后兼容所有的内容？
    </h2>
    <p>
        一些最新版本SDK中的功能由于太过复杂，难以做到向后兼容。最终，你不得不对性能和可用性进行平衡。如果你想要在代码中使用不可用框架的API，就需要在运行时检查API级别。
    </p>
    <p>
        在
        <code>
            MainActivity
        </code>
        中，下列的代码片段，使用了基础的包，而非支持库的包来import类。然后在
        <code>
            onContinentSelected
        </code>
        中，description fragment被初始化之后，但开始它的事务之前，添加下列的代码：
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
        分别在两个模拟器上运行项目。你会发现在API级别为15的模拟器上无动画，但在API级别为25及以上的模拟器中会有淡入和滑出的动画效果：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/side-by-side.gif">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/11/side-by-side.gif"
            alt="side-by-side" width="600" height="338" class="aligncenter size-full wp-image-121856">
        </a>
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
        祝贺！你已了解了Android SDK的版本及其相应的代号。你使一个API级别为26的app向后兼容到了API级别15，并使用cardview和设计库来添加额外的组件。你可能还想了解更多 :]
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
            都是因为Android。
        </p>
    </div>
    <p>
        在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/11/continents-final.zip">
            这里
        </a>
        可以下载到本教程的最终项目。
    </p>
    <p>
        如果你对Android SDK的版本感兴趣，可以参考
        <a href="https://en.wikipedia.org/wiki/Android_version_history" target="_blank">
            this wikipedia page
        </a>
        或在Android开发者网站中的
        <a href="http://developer.android.com/about/versions" target="_blank">
            versions
        </a>
        页。你还可以在
        <a href="http://developer.android.com/guide/topics/manifest/uses-sdk-element.html"
        target="_blank">
            开发者网站
        </a>
        中阅读更多关于minSdkVersion和targetSdkVersion属性相关的内容。最后，你还可以访问
        <a href="https://developer.android.com/tools/support-library/index.html"
        target="_blank">
            Support libraries
        </a>
        和它的
        <a href="https://developer.android.com/tools/support-library/features.html"
        target="_blank">
            feature list
        </a>
        。
    </p>
</div>