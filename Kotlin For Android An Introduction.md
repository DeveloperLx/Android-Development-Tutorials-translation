# 用Kotlin编写Android：介绍
---
#### [原文地址](https://www.raywenderlich.com/132381/kotlin-for-android-an-introduction) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-250x250.png"
        alt="Kotlin-feature" width="250" height="250" class="alignright size-thumbnail wp-image-141925"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/07/Kotlin-feature-128x128.png 128w"
        sizes="(max-width: 250px) 100vw, 250px">
    </p>
    <p>
        当为Android创建本地app的时候，你一般都会使用Java作为编程语言来编写逻辑。尽管Java是一种久经考验的语言，但并非没有问题。
    </p>
    <p>
        当你运行Java app的时候，app会被编译成一系列称作
        <a href="https://en.wikipedia.org/wiki/Java_bytecode" target="_blank"
        sl-processed="1">
            Bytecode
        </a>
        的指令，并运行在虚拟机上。在过去的几年中，引入了大量可以运行在
        <a href="https://en.wikipedia.org/wiki/Java_virtual_machine" target="_blank"
        title="Java virtual machine" sl-processed="1">
            Java虚拟机
        </a>
        上新的编程语言。尽管结果的app看起来对虚拟机都是一样的，但新语言中的特性可以帮助开发者编写更简单的代码，并修复一些Java中的问题。
    </p>
    <p>
        <a href="https://www.jetbrains.com/" target="_blank" title="JetBrains"
        sl-processed="1">
            JetBrains
        </a>
        ，因IntelliJ IDEA（Android Studio就基于IntelliJ）而出名，引入了
        <a href="https://kotlinlang.org/" target="_blank" title="Kotlin" sl-processed="1">
            Kotlin
        </a>
        语言。
    </p>
    <p>
        Kotlin是运行在JVM上的静态类型的编程语言。它还可以被编译成JavaScript源码。Kotlin有一些令人惊奇的特性！
    </p>
    <p>
        在本教程中，你将学到：
    </p>
    <ul>
        <li>
            如何设置你的Kotlin环境。
        </li>
        <li>
            如何在一个工程中同时使用Java和Kotlin两种语言。
        </li>
        <li>
            Kotlin作为一个新语言，有什么令人激动的特性。
        </li>
    </ul>
    <div class="note">
        <em>
            注意：
        </em>
        本教程假定你有Java语言下Android开发相关的经验。如果你完全是新手，对起始项目有很大的疑问，或是不熟悉Android Studio，请访问我们的
        <a href="https://www.raywenderlich.com/android-tutorials" target="_blank"
        title="Android tutorials" sl-processed="1">
            Android教程
        </a>
        。
    </div>
    <h2>
        为什么要为Android选择Kotlin？
    </h2>
    <p>
        由于Android如风暴般地席卷了全球，开发者对其app的开发除Java外没有其它选择。尽管它因此被广泛地传播，Java还带来了非常多的历史包袱。
    </p>
    <p>
        Java 8解决了一些语言的问题，在Java 10则纠正了更多的问题。要从这两个版本中获益，你不得不将minimum SDK的版本设置为Android
        24，仅仅是为了使用Java 8，这样的选择是无法被大多数开发者接受的。对于更大多数的开发者，Java 10几乎都压根不在视线范围内。
    </p>
    <p>
        Kotlin旨在填补Android平台与现代语言之间的差距。它有一些核心的
        <a href="http://kotlinlang.org/" target="_blank" title="tenets" sl-processed="1">
            准则
        </a>
        ，使它尽可能地成为：
    </p>
    <ol>
        <li>
            简洁，减少你需要编写的样本代码。
        </li>
        <li>
            表现力，让你的代码更加地可读和易于理解。
        </li>
        <li>
            安全，避免整个类型的错误，比如空指针的异常。
        </li>
        <li>
            通用性，构建服务端的app，Android app，或在浏览器中运行的前端代码。
        </li>
        <li>
            可协作性，100%地利用已存在JVM的框架和库。
        </li>
    </ol>
    <p>
        最重要的是，它是一门全新的语言！有什么可以比这更加激动人心？iOS的开发者无法拥有所有的乐趣。:]
    </p>
    <h2>
        入门
    </h2>
    <p>
        下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/09/omg-android-starter-1.zip"
        sl-processed="1">
            起始项目
        </a>
        ，提取并在Android Studio中打开它。
    </p>
    <p>
        你将会加工这个简单的app，让用户可以搜索书籍，查看书籍的封面，与朋友分享书籍，在这个过程中探索Kotlin。
    </p>
    <p>
        它包含了三个源码文件；花点时间来熟悉一下：
    </p>
    <ul>
        <li>
            <em>
                MainActivity.java：
            </em>
            用来搜索并展示书籍列表的
            <code>
                Activity
            </code>
            。
        </li>
        <li>
            <em>
                DetailActivity.java:
            </em>
            根据传递过来的ID，来展示书籍的封面的
            <code>
                Activity
            </code>
            。
        </li>
        <li>
            <em>
                JSONAdapter.java:
            </em>
            一个自定义的
            <code>
                BaseAdapter
            </code>
            ，可以将一个JSON对象转换为一个列表视图的item。
        </li>
    </ul>
    <p>
        运行项目来查看这个app。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25.png"
        rel="attachment wp-att-131882" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25-572x500.png"
            alt="intro_to_kotlin_25" width="572" height="500" class="aligncenter size-large wp-image-139018"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25-572x500.png 572w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25-366x320.png 366w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25.png 1100w"
            sizes="(max-width: 572px) 100vw, 572px">
        </a>
    </p>
    <h2>
        设置你的环境
    </h2>
    <p>
        默认情况下，Android Studio是不知道如何处理Kotlin的，因此第一步是需要按照Kotlin插件，并在你的项目中配置Kotlin。
    </p>
    <h3>
        安装Kotlin插件
    </h3>
    <p>
        在
        <em>
            Android Studio/Preferences
        </em>
        下选择
        <em>
            Plugins
        </em>
        这项。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_3.png"
        rel="attachment wp-att-131888" sl-processed="1">
            <img class="aligncenter size-large wp-image-131888" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_3-700x435.png"
            alt="kotlin for android 3" width="700" height="435" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_3-700x435.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_3-480x298.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_3-768x477.png 768w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        在
        <em>
            Plugins
        </em>
        这一屏中，点击
        <em>
            Install JetBrains plugin…
        </em>
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_4.png"
        rel="attachment wp-att-131889" sl-processed="1">
            <img class="aligncenter size-large wp-image-131889" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_4-700x426.png"
            alt="intro_to_kotlin_4" width="700" height="426" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_4-700x426.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_4-480x292.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_4-768x467.png 768w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        搜索并从列表中选择
        <em>
            Kotlin
        </em>
        ，然后点击
        <em>
            Install
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_5.png"
        rel="attachment wp-att-131890" sl-processed="1">
            <img class="aligncenter size-large wp-image-131890" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_5-700x424.png"
            alt="intro_to_kotlin_5" width="700" height="424" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_5-700x424.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_5-480x291.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_5-768x466.png 768w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_6.png"
        rel="attachment wp-att-131891" sl-processed="1">
            <img class="aligncenter size-large wp-image-131891" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_6-700x425.png"
            alt="kotlin for android 6" width="700" height="425" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_6-700x425.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_6-480x292.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_6-768x467.png 768w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        完成下载和安装之后，接下来跟随提示重启IDE。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_28.png"
        rel="attachment wp-att-138898" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_28-650x399.png"
            alt="intro_to_kotlin_28" width="650" height="399" class="aligncenter size-large wp-image-139028"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_28-650x399.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_28-480x295.png 480w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <h3>
        在项目中配置Kotlin
    </h3>
    <p>
        现在IDE就知道如何处理Kotlin了，但你的项目app还不知道。因此下面的一步就是修改项目的构建配置。
    </p>
    <p>
        在项目中找到
        <em>
            Tools/Kotlin/Configure Kotlin
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_7.png"
        rel="attachment wp-att-131892" sl-processed="1">
            <img class="aligncenter size-large wp-image-131892" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_7-700x435.png"
            alt="intro_to_kotlin_7" width="700" height="435" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_7-700x435.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_7-480x298.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_7-768x477.png 768w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        从弹出的菜单
        <em>
            Choose Configurator
        </em>
        中选择
        <em>
            Android with Gradle
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_8.png"
        rel="attachment wp-att-131894" sl-processed="1">
            <img class="aligncenter size-full wp-image-131894" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_8.png"
            alt="intro_to_kotlin_8" width="290" height="122">
        </a>
    </p>
    <p>
        在弹出的窗口
        <em>
            Configure Kotlin in Project
        </em>
        中，选择你想要使用的插件版本（在编写本教程的时候，当前的版本应当是1.0.3），并点击
        <em>
            OK
        </em>
        。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/configure_kotlin_in_project-480x168.png"
        alt="Configure Kotlin in Project" width="480" height="168" class="aligncenter size-medium wp-image-143060"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/configure_kotlin_in_project-480x168.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/09/configure_kotlin_in_project.png 552w"
        sizes="(max-width: 480px) 100vw, 480px">
    </p>
    <p>
        这个操作将对你的
        <em>
            build.gradle
        </em>
        文件进行大量的修改。
    </p>
    <p>
        <em>
            build.gradle（Project: omg-android-starter）：
        </em>
    </p>
    <pre lang="groovy" class="language-groovy">buildscript {
  ext.kotlin_version = '1.0.3' // 1
  repositories {
    jcenter()
  }
  dependencies {
    classpath 'com.android.tools.build:gradle:2.1.3'
    classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version" // 2

    // NOTE: Do not place your application dependencies here; they belong
    // in the individual module build.gradle files
  }
}

allprojects {
  repositories {
    jcenter()
  }
}
</pre>
    <p>
        <em>
            build.gradle（Module: OMG Android）：
        </em>
    </p>
    <pre lang="groovy" class="language-groovy">    
apply plugin: 'com.android.application'
apply plugin: 'kotlin-android' // 3

android {
    compileSdkVersion 23
    buildToolsVersion "24.0.2"

    defaultConfig {
        minSdkVersion 14
        targetSdkVersion 23
    }
  sourceSets {
    main.java.srcDirs += 'src/main/kotlin' // 4
  }
}

dependencies {
  compile 'com.android.support:appcompat-v7:23.2.0'
  compile 'com.loopj.android:android-async-http:1.4.4'
  compile 'com.squareup.picasso:picasso:2.1.1'
  compile "org.jetbrains.kotlin:kotlin-stdlib:$kotlin_version" // 5
}
repositories {
  mavenCentral()
}
</pre>
    <p>
        一步一步来看：
    </p>
    <ol>
        <li>
            声明配置在项目中的Kotlin版本
        </li>
        <li>
            声明一个类路径依赖的工件，其中包含有之前声明的Kotlin Gradle的插件
        </li>
        <li>
            通过
            <code>
                apply plugin command
            </code>
            指定Kotlin Android插件的用途
        </li>
        <li>
            声明在
            <em>
                src/main/kotlin
            </em>
            中的源码文件将被编译。严格地说，gradle将会编译在
            <em>
                src/main/java
            </em>
            中的Kotlin源码文件，但将Kotlin文件都存放到一个Kotlin的目录下显然会更好一些。
        </li>
        <li>
            添加Kotlin的标准库，作为项目编译时的依赖
        </li>
    </ol>
    <p>
        点击
        <em>
            Sync Now
        </em>
        来构建项目，然后运行。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25.png"
        rel="attachment wp-att-131882" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25-572x500.png"
            alt="intro_to_kotlin_25" width="572" height="500" class="aligncenter size-large wp-image-139018"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25-572x500.png 572w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25-366x320.png 366w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_25.png 1100w"
            sizes="(max-width: 572px) 100vw, 572px">
        </a>
    </p>
    <p>
        看不出任何视觉上的变化，但你已在这个Android项目加入了对Kotlin语言的支持。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/can_we_start_already-1.png"
        rel="attachment wp-att-131914" sl-processed="1">
            <img class="aligncenter size-full wp-image-131914" src="https://koenig-media.raywenderlich.com/uploads/2016/04/can_we_start_already-1.png"
            alt="can_we_start_already" width="250" height="235">
        </a>
    </p>
    <h2>
        在一个项目中同时使用Java和Kotlin
    </h2>
    <p>
        Kotlin最令人惊奇的一个特性，就是它可以与Java在一个项目中共存。并且Java代码可以调用Kotlin，Kotlin代码也可调用Java。
    </p>
    <p>
        在本教程后面的部分，你将使用Kotlin来翻译
        <em>
            DetailActivity
        </em>
        这个类。
    </p>
    <p>
        在左侧的项目面板中单击
        <code>
            com.example.omgandroid
        </code>
        这个包。选中这个包后，点击
        <em>
            File/New/Kotlin File/Class
        </em>
        来创建一个新的Kotlin类。（未选择包的情况下，你无法看到Kotlin文件的选项）。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_15.png"
        sl-processed="1">
            <img class="aligncenter size-large wp-image-132397" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_15-550x500.png"
            alt="intro_to_kotlin_15" width="550" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_15-550x500.png 550w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_15-352x320.png 352w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_15-768x699.png 768w"
            sizes="(max-width: 550px) 100vw, 550px">
        </a>
    </p>
    <p>
        在弹出的
        <em>
            New Kotlin File/Class
        </em>
        对话框中，在
        <em>
            Kind
        </em>
        域中选择
        <em>
            Class
        </em>
        ，然后输入
        <em>
            DetailActivityKotlin
        </em>
        作为类名。点击
        <em>
            OK
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_17.png"
        sl-processed="1">
            <img class="aligncenter size-full wp-image-132400" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_17.png"
            alt="intro_to_kotlin_17" width="699" height="269" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_17.png 699w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_17-480x185.png 480w"
            sizes="(max-width: 699px) 100vw, 699px">
        </a>
    </p>
    <p>
        你新创建的类现在看起来应当是这样：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">    
    <span class="hljs-keyword">package</span> com.example.omgandroid
    <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">DetailActivityKotlin</span> </span>{
    }
</pre>
    <p>
        这里有几件事值得注意：
    </p>
    <ol>
        <li>
            就像你在上述代码中看的一样，Kotlin使用关键字
            <code>
                class
            </code>
            来声明类 - 就像在Java中一样。
        </li>
        <li>
            Kotlin的默认可见性修饰符是
            <code>
                public
            </code>
            。
        </li>
        <li>
            类和方法默认都是final的。如果你想进行扩展的话，可以将他们声明成
            <code>
                open
            </code>
            的。
        </li>
    </ol>
    <p>
        由于Kotlin可以和Java进行交互，你可以在Kotlin的源码文件中直接使用Java的框架和库。
    </p>
    <p>
        首先在文件的顶部添加如下的import语句
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
  <span class="hljs-keyword">import</span> android.app.Activity
  <span class="hljs-keyword">import</span> android.os.Bundle
</pre>
    <p>
        然后创建一个
        <em>
            Activity
        </em>
        的子类。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">Main2Activity</span> : <span class="hljs-type">Activity</span></span>() {

}
</pre>
    <p>
        注意这里和Java中有一点不同。在Kotlin中，你用
        <em>
            :NameOfParentClass()
        </em>
        来表示类的继承。
    </p>
    <p>
        现在重写
        <em>
            Activity
        </em>
        的
        <em>
            onCreate()
        </em>
        方法，就像下面这样。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
<span class="hljs-keyword">import</span> android.app.Activity
<span class="hljs-keyword">import</span> android.os.Bundle

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">DetailActivityKotlin</span>: <span class="hljs-type">Activity</span></span>() {

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(savedInstanceState: <span class="hljs-type">Bundle</span>?)</span></span> {
    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState)
  }
}
</pre>
    <div class="note">
        <em>
            注意：
        </em>
        你可以使用Android Studio的代码生成功能来创建
        <em>
            onCreate
        </em>
        方法，快捷键是
        <em>
            control + O
        </em>
        。按下
        <em>
            control + O
        </em>
        键可以查看你当前所在的类可重载的方法。
        <p>
        </p>
        <p>
            <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_18.png"
            sl-processed="1">
                <img class="aligncenter size-large wp-image-132422" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_18-463x500.png"
                alt="intro_to_kotlin_18" width="463" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_18-463x500.png 463w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_18-296x320.png 296w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_18-768x830.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_18.png 1024w"
                sizes="(max-width: 463px) 100vw, 463px">
            </a>
        </p>
    </div>
    <p>
        打开
        <em>
            MainActivity.java
        </em>
        ，并将
        <code>
            onItemClick()
        </code>
        中的
        <code>
            DetailActivity
        </code>
        替换为
        <code>
            DetailActivityKotlin
        </code>
        。
    </p>
    <p>
        将创建intent的这行代码： Your intent creation line should change from:
    </p>
    <pre lang="java" class="language-java hljs">  
Intent detailIntent = <span class="hljs-keyword">new</span> Intent(<span class="hljs-keyword">this</span>, DetailActivity.class);
</pre>
    <p>
        替换为：
    </p>
    <pre lang="java" class="language-java hljs">  
Intent detailIntent = <span class="hljs-keyword">new</span> Intent(<span class="hljs-keyword">this</span>, DetailActivityKotlin.class);
</pre>
    <p>
        就像你在Java中为Activity做的，你需要在
        <em>
            AndroidManifest.xml
        </em>
        中声明你的Kotlin Activity。在
        <em>
            DetailActivity
        </em>
        声明的下方添加如下代码：
    </p>
    <pre lang="xml" class="language-xml hljs">   <span class="hljs-tag">&lt;<span class="hljs-name">activity</span>
        <span class="hljs-attr">android:name</span>=<span class="hljs-string">".DetailActivityKotlin"</span>
        <span class="hljs-attr">android:label</span>=<span class="hljs-string">"@string/activity_details_kotlin"</span>
        <span class="hljs-attr">android:parentActivityName</span>=<span class="hljs-string">".MainActivity"</span>&gt;</span>
      <span class="hljs-tag">&lt;<span class="hljs-name">meta-data</span>
          <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.support.PARENT_ACTIVITY"</span>
          <span class="hljs-attr">android:value</span>=<span class="hljs-string">".MainActivity"</span>/&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">activity</span>&gt;</span>
</pre>
    <p>
        运行项目。从列表中选择一本书，你就会看到一个带有标题
        <i>
            Kotlin Book Details
        </i>
        的空空的屏幕。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_26.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_26-572x500.png"
            alt="intro_to_kotlin_26" width="572" height="500" class="aligncenter size-large wp-image-139019"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_26-572x500.png 572w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_26-366x320.png 366w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_26.png 1100w"
            sizes="(max-width: 572px) 100vw, 572px">
        </a>
    </p>
    <h2>
        Kotlin有多酷？
    </h2>
    <p>
        在你深入Kotlin的特性之前，回到
        <em>
            DetailActivityKotlin.kt
        </em>
        ，并将文件的全部内容替换为：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
<span class="hljs-keyword">package</span> com.example.omgandroid

<span class="hljs-keyword">import</span> android.app.Activity
<span class="hljs-keyword">import</span> android.content.Intent
<span class="hljs-keyword">import</span> android.os.Bundle
<span class="hljs-keyword">import</span> android.view.Menu
<span class="hljs-keyword">import</span> android.widget.ImageView
<span class="hljs-keyword">import</span> android.widget.ShareActionProvider
<span class="hljs-keyword">import</span> com.squareup.picasso.Picasso

<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">DetailActivityKotlin</span>: <span class="hljs-type">Activity</span></span>() {

  <span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> IMAGE_URL_BASE = <span class="hljs-string">"http://covers.openlibrary.org/b/id/"</span>
  <span class="hljs-keyword">internal</span> <span class="hljs-keyword">var</span> mImageURL = <span class="hljs-string">""</span>
  <span class="hljs-keyword">internal</span> <span class="hljs-keyword">var</span> mShareActionProvider: ShareActionProvider? = <span class="hljs-literal">null</span>

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(savedInstanceState: <span class="hljs-type">Bundle</span>?)</span></span> {
    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState)

    setContentView(R.layout.activity_detail)

    actionBar?.setDisplayHomeAsUpEnabled(<span class="hljs-literal">true</span>)

    <span class="hljs-keyword">val</span> imageView = findViewById(R.id.img_cover) <span class="hljs-keyword">as</span> ImageView

    <span class="hljs-keyword">val</span> coverId = <span class="hljs-keyword">this</span>.intent.extras.getString(<span class="hljs-string">"coverID"</span>)

    <span class="hljs-keyword">val</span> len = coverId?.length ?: <span class="hljs-number">0</span>

    <span class="hljs-keyword">if</span> (len &gt; <span class="hljs-number">0</span>) {
      mImageURL = IMAGE_URL_BASE + coverId + <span class="hljs-string">"-L.jpg"</span>
      Picasso.with(<span class="hljs-keyword">this</span>).load(mImageURL).placeholder(R.drawable.img_books_loading).into(imageView)
    }
  }

  <span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">setShareIntent</span><span class="hljs-params">()</span></span> {

    <span class="hljs-keyword">val</span> shareIntent = Intent(Intent.ACTION_SEND)
    shareIntent.type = <span class="hljs-string">"text/plain"</span>
    shareIntent.putExtra(Intent.EXTRA_SUBJECT, <span class="hljs-string">"Book Recommendation!"</span>)
    shareIntent.putExtra(Intent.EXTRA_TEXT, mImageURL)

    mShareActionProvider?.setShareIntent(shareIntent)
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateOptionsMenu</span><span class="hljs-params">(menu: <span class="hljs-type">Menu</span>)</span></span>: <span class="hljs-built_in">Boolean</span> {

    menuInflater.inflate(R.menu.main, menu)

    <span class="hljs-keyword">val</span> shareItem = menu.findItem(R.id.menu_item_share)

    mShareActionProvider = shareItem!!.actionProvider <span class="hljs-keyword">as</span> ShareActionProvider

    setShareIntent()

    <span class="hljs-keyword">return</span> <span class="hljs-literal">true</span>
  }
}
</pre>
    <p>
        表面上看，上述代码非常得像Java，但仍包含着一些Kotlin语言的特性，你将在下一部分进行深入。
    </p>
    <p>
        运行项目，选择一本书，检查你是否能看到封面。是的，你做到了！
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_27.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_27-572x500.png"
            alt="intro_to_kotlin_27" width="572" height="500" class="aligncenter size-large wp-image-139020"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_27-572x500.png 572w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_27-366x320.png 366w, https://koenig-media.raywenderlich.com/uploads/2016/07/intro_to_kotlin_27.png 1100w"
            sizes="(max-width: 572px) 100vw, 572px">
        </a>
    </p>
    <h3>
        空指针的安全性
    </h3>
    <p>
        包括Java在内的很多语言，一个最头疼的问题就是访问空引用的成员。空引用通常发生在，你声明了一个对象的变量，但却未给它赋值的时候。当程序运行起来，尝试访问这个变量的时候，就无法知道该去哪里来找到它，因为它实际上并不存在。
    </p>
    <p>
        最常见的结果就是你的app会直接奔溃！你可能熟悉Java的“almighty”
        <em>
            NullPointerException
        </em>
        。在任何突然闪现的情况前道歉！:]
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/null_pointer_exception.png"
        rel="attachment wp-att-131906" sl-processed="1">
            <img class="aligncenter size-large wp-image-131906" src="https://koenig-media.raywenderlich.com/uploads/2016/04/null_pointer_exception-334x500.png"
            alt="null_pointer_exception" width="334" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/null_pointer_exception-334x500.png 334w, https://koenig-media.raywenderlich.com/uploads/2016/04/null_pointer_exception-214x320.png 214w, https://koenig-media.raywenderlich.com/uploads/2016/04/null_pointer_exception-768x1149.png 768w"
            sizes="(max-width: 334px) 100vw, 334px">
        </a>
    </p>
    <p>
        Kotlin最棒的特性之一，就是它的类型系统旨在消除
        <em>
            NullPointerException
        </em>
        （参考
        <a href="https://en.wikipedia.org/wiki/Void_safety" target="_blank" title="void safety"
        sl-processed="1">
            void safety
        </a>
        ）。
    </p>
    <p>
        在Kotlin中，造成
        <em>
            NullPointerException
        </em>
        的原因只有：
    </p>
    <ul>
        <li>
            外部的Java代码所导致
        </li>
        <li>
            显式地抛出NullPointerException()
        </li>
        <li>
            使用了
            <code>
                !!
            </code>
            操作符（有短路的特性）
        </li>
        <li>
            一些数据相关于构造器的内容前后矛盾
        </li>
    </ul>
    <h3>
        可以为空的类型和禁止为空的类型
    </h3>
    <p>
        Kotlin含有
        <em>
            nullable
        </em>
        和
        <em>
            non-null
        </em>
        类型。如果你未将变量声明成nullable的，你就不能给它赋一个空值。这是由编译器所强制规定的，使得因粗心造成你app的崩溃变得更加困难。
    </p>
    <p>
        不同于Java，kotlin所有的变量都必须在它声明时被初始化。
    </p>
    <p>
        要将一个类型声明为nullable的，你就必须在他的类型后添加一个
        <em>
            ?
        </em>
        ，就像你在
        <em>
            mShareActionProvider
        </em>
        的声明中看到的一样：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
<span class="hljs-keyword">internal</span> <span class="hljs-keyword">var</span> mShareActionProvider: ShareActionProvider? = <span class="hljs-literal">null</span>
</pre>
    <h3>
        安全的调用
    </h3>
    <p>
        在Java中，要访问一个property或方法，你需要首先进行一个null的判断。如你在
        <code>
            DetailActivity.java
        </code>
        中看到的：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">if</span> (mShareActionProvider != <span class="hljs-keyword">null</span>) {
  mShareActionProvider.setShareIntent(shareIntent)
}
</pre>
    <p>
        而在Kotlin中，你可以使用一个安全的调用操作符（
        <em>
            ?.
        </em>
        ）来简化上述的表达式。其后的property或方法只有在这个nullable的变量
        <i>
            不为空时
        </i>
        才会被调用。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
mShareActionProvider?.setShareIntent(shareIntent)
</pre>
    <p>
        这里，
        <code>
            setShareIntent
        </code>
        只有当
        <code>
            mShareActionProvider
        </code>
        property不为空时才会被调用。
    </p>
    <h3>
        !! 操作符
    </h3>
    <p>
        就像前面所提到的，它是造成可怕的
        <em>
            NullPointerException
        </em>
        可能的原因之一。如果你可以百分之百地确认这个对象不为空，就可以使用（
        <em>
            !!
        </em>
        ）操作符来重新引用你的对象。
    </p>
    <p>
        你可以在
        <code>
            setShareIntent()
        </code>
        中看到它的一个例子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">mShareActionProvider = shareItem!!.actionProvider <span class="hljs-keyword">as</span> ShareActionProvider
</pre>
    <p>
        这里，如果
        <em>
            shareItem
        </em>
        变量不为空，
        <em>
            actionProvider
        </em>
        就会被取用，反之则会抛出一个
        <em>
            NullPointerException
        </em>
        的异常。
    </p>
    <h3>
        Elvis操作符
    </h3>
    <p>
        Elvis操作符
        <em>
            ?:
        </em>
        ）看起来就像Java中的三元
        <code>
            if
        </code>
        操作符，但工作方式完全不同。获取封面ID的长度这里可以作为一个例子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
<span class="hljs-keyword">val</span> len = coverId?.length ?: <span class="hljs-number">0</span>
</pre>
    <p>
        如果Elvis操作符左边的表达式不为空，就返回这个表达式的结果。否则，就返回右侧的表达式。
    </p>
    <p>
        就像
        <code>
            if-else
        </code>
        语句一样，Elvis运算符右边的表达式只会在左边表达式的值为null时，才会进行计算。
    </p>
    <h3>
        类型推断
    </h3>
    <p>
        Kotlin还支持类型推断，意味着编译器可以从它的初始化中猜测它的类型。例如，
        <code>
            IMAGE_URL_BASE
        </code>
        和
        <code>
            mImageURL
        </code>
        变量的类型就是从它们的初始化中推断出来的。
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">  
<span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> IMAGE_URL_BASE = <span class="hljs-string">"http://covers.openlibrary.org/b/id/"</span>
<span class="hljs-keyword">internal</span> <span class="hljs-keyword">var</span> mImageURL = <span class="hljs-string">""</span>
</pre>
    <p>
        编译器会追踪每个变量的推断类型（
        <code>
            String
        </code>
        ），这样随后被赋予到这些变量的值就必须也是那个类型（
        <code>
            String
        </code>
        ）的了。
    </p>
    <h3>
        最酷的一点
    </h3>
    <p>
        早已在考虑用户Kotlin重写你的Java项目了么？不必太有压力 — Kotlin的插件早就为你考虑好了。
    </p>
    <p>
        由于Kotlin是由开发者所发明的语言，且为开发者使用，它会尽可能地让你的生活变得轻松。Kotlin的插件中甚至还包含了一个便利的工具，直接将你的Java源码转化为Kotlin。
    </p>
    <p>
        来测试一下这个功能，把
        <em>
            DetailActivity.java
        </em>
        文件转换成Kotlin的吧。
    </p>
    <p>
        打开
        <em>
            DetailActivity.java
        </em>
        类并点击
        <em>
            Code/Convert Java File to Kotlin File
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_13.png"
        rel="attachment wp-att-131898" sl-processed="1">
            <img class="aligncenter size-large wp-image-131898" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_13-700x435.png"
            alt="intro_to_kotlin_13" width="700" height="435" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_13-700x435.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_13-480x298.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_13-768x477.png 768w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        在
        <em>
            Convert Java to Kotlin
        </em>
        这页上点击
        <em>
            OK
        </em>
        ，就会将这个Java文件替换为Kotlin的！
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_14.png"
        rel="attachment wp-att-131899" sl-processed="1">
            <img class="aligncenter size-large wp-image-131899" src="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_14-700x256.png"
            alt="intro_to_kotlin_14" width="700" height="256" srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_14-700x256.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_14-480x175.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_14-768x280.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/04/intro_to_kotlin_14.png 800w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        OK了。你已将一个Java的类替换成了Kotlin的。:]
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/not_bad-1.png"
        rel="attachment wp-att-131964" sl-processed="1">
            <img class="aligncenter size-full wp-image-131964" src="https://koenig-media.raywenderlich.com/uploads/2016/04/not_bad-1.png"
            alt="not_bad" width="296" height="262">
        </a>
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
        祝贺！你刚刚已经了解了一些Kotlin语言中令人惊奇的特性，用Kotlin重写了一个Java的Activity，并使用Kotlin的插件将一个Java的源文件转花成了Kotlin的源文件。
    </p>
    <p>
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/07/omg-android-final.zip"
        target="_blank" title="here" sl-processed="1">
            这里
        </a>
        下载最终完成的项目。
    </p>
    <p>
        建议对文档
        <a href="https://kotlinlang.org/docs/reference/null-safety.html" title="Null Safety in Kotlin"
        sl-processed="1">
            Null Safety in Kotlin
        </a>
        进行更深入的阅读。
    </p>
    <p>
        你还可以使用
        <a href="http://try.kotlinlang.org/" target="_blank" title="Kotlin online compiler"
        sl-processed="1">
            Kotlin在线编译器
        </a>
        来实验代码样本及提升知识技能。
    </p>
    <p>
        本文中你仅仅是触及到了Kotlin的皮毛。如果你渴望了解更多内容的话，还可以查阅这些话题：
        <a href="http://kotlinlang.org/docs/reference/data-classes.html" target="_blank"
        title="Data Classes" sl-processed="1">
            Data Classes
        </a>
        ，
        <a href="http://kotlinlang.org/docs/reference/extensions.html" target="_blank"
        title="Extensions" sl-processed="1">
            Extensions
        </a>
        ，
        <a href="http://kotlinlang.org/docs/reference/coding-conventions.html#lambdas"
        target="_blank" title="Lambdas" sl-processed="1">
            Lambdas
        </a>
        ，
        <a href="http://kotlinlang.org/docs/reference/basic-syntax.html#using-string-templates"
        target="_blank" title="String Templates" sl-processed="1">
            String Templates
        </a>
        等。
    </p>
</div>