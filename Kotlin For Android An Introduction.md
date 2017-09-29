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
        Java 8解决了一些语言的问题，在Java 10则纠正了更多的问题。要从这两个版本中获益，你不得不将minimum SDK的版本设置为Android 24，仅仅是为了使用Java 8，这样的选择是无法被大多数开发者接受的。对于更大多数的开发者，Java 10几乎都压根不在视线范围内。
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
        One of the most amazing qualities of Kotlin is how it can coexist with
        Java on a project. Java code can be called from Kotlin and vice versa.
    </p>
    <p>
        From this point of the tutorial forward, you’ll be translating the
        <em>
            DetailActivity
        </em>
        class in Kotlin.
    </p>
    <p>
        Single click the
        <code>
            com.example.omgandroid
        </code>
        package in the Project panel on the left-hand side. With the package selected,
        go to
        <em>
            File\New\Kotlin File/Class
        </em>
        to create a new Kotlin class. (Without the package selected, you won’t
        see the Kotlin file option).
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
        On the
        <em>
            New Kotlin File/Class
        </em>
        popup, select
        <em>
            Class
        </em>
        in the
        <em>
            Kind
        </em>
        field and enter
        <em>
            DetailActivityKotlin
        </em>
        as the class name. Click
        <em>
            OK
        </em>
        .
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
        Your new class should look like this:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            package
        </span>
        com.example.omgandroid
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                DetailActivityKotlin
            </span>
        </span>
        { }
    </pre>
    <p>
        A few things to note here:
    </p>
    <ol>
        <li>
            As you may have noticed in the above code, classes in Kotlin are declared
            using the keyword
            <code>
                class
            </code>
            — just like in Java.
        </li>
        <li>
            The default visibility modifier in Kotlin is
            <code>
                public
            </code>
            .
        </li>
        <li>
            Classes and methods are final by default. You can declare them
            <code>
                open
            </code>
            if you want extensibility.
        </li>
    </ol>
    <p>
        Since Kotlin is Java interoperable, you can use existing Java frameworks
        and libraries in your Kotlin code files.
    </p>
    <p>
        First place the following import statements at the top of the file:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.app.Activity
        <span class="hljs-keyword">
            import
        </span>
        android.os.Bundle
    </pre>
    <p>
        Then make the class a subclass of
        <em>
            Activity
        </em>
        .
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                Main2Activity
            </span>
            :
            <span class="hljs-type">
                Activity
            </span>
        </span>
        () { }
    </pre>
    <p>
        Note that you do this in Kotlin a little differently from how you do it
        in Java. In Kotlin, you append
        <em>
            :NameOfParentClass()
        </em>
        to the subclass declaration.
    </p>
    <p>
        Now override
        <em>
            Activity
        </em>
        ‘s
        <em>
            onCreate()
        </em>
        method. It will look something like this.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.app.Activity
        <span class="hljs-keyword">
            import
        </span>
        android.os.Bundle
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                DetailActivityKotlin
            </span>
            :
            <span class="hljs-type">
                Activity
            </span>
        </span>
        () {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onCreate
            </span>
            <span class="hljs-params">
                (savedInstanceState:
                <span class="hljs-type">
                    Bundle
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState) } }
    </pre>
    <div class="note">
        <em>
            Note:
        </em>
        You can use Android Studio’s code generation functionality to generate
        the
        <em>
            onCreate
        </em>
        method signature with
        <em>
            control + O
        </em>
        . Press
        <em>
            control + O
        </em>
        to see a popup with all overridable methods for the class you’re in.
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
        Open
        <em>
            MainActivity.java
        </em>
        and replace the
        <code>
            DetailActivity
        </code>
        reference in
        <code>
            onItemClick()
        </code>
        with
        <code>
            DetailActivityKotlin
        </code>
        .
    </p>
    <p>
        Your intent creation line should change from:
    </p>
    <pre lang="java" class="language-java hljs">
        Intent detailIntent =
        <span class="hljs-keyword">
            new
        </span>
        Intent(
        <span class="hljs-keyword">
            this
        </span>
        , DetailActivity.class);
    </pre>
    <p>
        To this:
    </p>
    <pre lang="java" class="language-java hljs">
        Intent detailIntent =
        <span class="hljs-keyword">
            new
        </span>
        Intent(
        <span class="hljs-keyword">
            this
        </span>
        , DetailActivityKotlin.class);
    </pre>
    <p>
        Just like you would do for a Java Activity, you need to declare your Kotlin
        Activity in
        <em>
            AndroidManifest.xml
        </em>
        . Add the following code under the
        <em>
            DetailActivity
        </em>
        declaration:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                activity
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                ".DetailActivityKotlin"
            </span>
            <span class="hljs-attr">
                android:label
            </span>
            =
            <span class="hljs-string">
                "@string/activity_details_kotlin"
            </span>
            <span class="hljs-attr">
                android:parentActivityName
            </span>
            =
            <span class="hljs-string">
                ".MainActivity"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                meta-data
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "android.support.PARENT_ACTIVITY"
            </span>
            <span class="hljs-attr">
                android:value
            </span>
            =
            <span class="hljs-string">
                ".MainActivity"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                activity
            </span>
            &gt;
        </span>
    </pre>
    <p>
        Build and run. Select a book from the list so you can see that empty screen
        with the title
        <i>
            Kotlin Book Details
        </i>
        .
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
        How Cool is Kotlin?
    </h2>
    <p>
        Before you dive deeper into Kotlin’s features, go back to
        <em>
            DetailActivityKotlin.kt
        </em>
        and replace the contents of the file with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            package
        </span>
        com.example.omgandroid
        <span class="hljs-keyword">
            import
        </span>
        android.app.Activity
        <span class="hljs-keyword">
            import
        </span>
        android.content.Intent
        <span class="hljs-keyword">
            import
        </span>
        android.os.Bundle
        <span class="hljs-keyword">
            import
        </span>
        android.view.Menu
        <span class="hljs-keyword">
            import
        </span>
        android.widget.ImageView
        <span class="hljs-keyword">
            import
        </span>
        android.widget.ShareActionProvider
        <span class="hljs-keyword">
            import
        </span>
        com.squareup.picasso.Picasso
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                DetailActivityKotlin
            </span>
            :
            <span class="hljs-type">
                Activity
            </span>
        </span>
        () {
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        IMAGE_URL_BASE =
        <span class="hljs-string">
            "http://covers.openlibrary.org/b/id/"
        </span>
        <span class="hljs-keyword">
            internal
        </span>
        <span class="hljs-keyword">
            var
        </span>
        mImageURL =
        <span class="hljs-string">
            ""
        </span>
        <span class="hljs-keyword">
            internal
        </span>
        <span class="hljs-keyword">
            var
        </span>
        mShareActionProvider: ShareActionProvider? =
        <span class="hljs-literal">
            null
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onCreate
            </span>
            <span class="hljs-params">
                (savedInstanceState:
                <span class="hljs-type">
                    Bundle
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState) setContentView(R.layout.activity_detail)
        actionBar?.setDisplayHomeAsUpEnabled(
        <span class="hljs-literal">
            true
        </span>
        )
        <span class="hljs-keyword">
            val
        </span>
        imageView = findViewById(R.id.img_cover)
        <span class="hljs-keyword">
            as
        </span>
        ImageView
        <span class="hljs-keyword">
            val
        </span>
        coverId =
        <span class="hljs-keyword">
            this
        </span>
        .intent.extras.getString(
        <span class="hljs-string">
            "coverID"
        </span>
        )
        <span class="hljs-keyword">
            val
        </span>
        len = coverId?.length ?:
        <span class="hljs-number">
            0
        </span>
        <span class="hljs-keyword">
            if
        </span>
        (len &gt;
        <span class="hljs-number">
            0
        </span>
        ) { mImageURL = IMAGE_URL_BASE + coverId +
        <span class="hljs-string">
            "-L.jpg"
        </span>
        Picasso.with(
        <span class="hljs-keyword">
            this
        </span>
        ).load(mImageURL).placeholder(R.drawable.img_books_loading).into(imageView)
        } }
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                setShareIntent
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            val
        </span>
        shareIntent = Intent(Intent.ACTION_SEND) shareIntent.type =
        <span class="hljs-string">
            "text/plain"
        </span>
        shareIntent.putExtra(Intent.EXTRA_SUBJECT,
        <span class="hljs-string">
            "Book Recommendation!"
        </span>
        ) shareIntent.putExtra(Intent.EXTRA_TEXT, mImageURL) mShareActionProvider?.setShareIntent(shareIntent)
        }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onCreateOptionsMenu
            </span>
            <span class="hljs-params">
                (menu:
                <span class="hljs-type">
                    Menu
                </span>
                )
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Boolean
        </span>
        { menuInflater.inflate(R.menu.main, menu)
        <span class="hljs-keyword">
            val
        </span>
        shareItem = menu.findItem(R.id.menu_item_share) mShareActionProvider =
        shareItem!!.actionProvider
        <span class="hljs-keyword">
            as
        </span>
        ShareActionProvider setShareIntent()
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-literal">
            true
        </span>
        } }
    </pre>
    <p>
        On the surface, the code resembles Java, but there are some Kotlin language
        specifics that you’ll get into in the next section.
    </p>
    <p>
        Build and run, select a book and see if you get a cover this time. Oh,
        look, you do!
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
        Null Safety
    </h3>
    <p>
        One of the leading points of frustration with most programming languages,
        including Java, is accessing a member of a null reference. A null reference
        occurs when you declare an object variable but haven’t given it a value.
        When the program runs and tries to access that variable it doesn’t know
        where to look for it memory because it doesn’t exist.
    </p>
    <p>
        The most common result of this is your application come to an abrupt halt
        and crashes! You might be familiar with Java’s “almighty”
        <em>
            NullPointerException
        </em>
        . Apologies in advance for any flashbacks! :]
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
        One of Kotlin’s greatest features is that its type system aims to eliminate
        the
        <em>
            NullPointerException
        </em>
        (a goal known as
        <a href="https://en.wikipedia.org/wiki/Void_safety" target="_blank" title="void safety"
        sl-processed="1">
            void safety
        </a>
        ).
    </p>
    <p>
        In Kotlin, the only possible causes of a
        <em>
            NullPointerException
        </em>
        are:
    </p>
    <ul>
        <li>
            External Java code did it
        </li>
        <li>
            An explicit call to throw NullPointerException()
        </li>
        <li>
            Usage of the
            <code>
                !!
            </code>
            operator (which will be explained shortly)
        </li>
        <li>
            Some data inconsistency in regards to initialization
        </li>
    </ul>
    <h3>
        Nullable Types and Non-Null Types
    </h3>
    <p>
        Kotlin has
        <em>
            nullable
        </em>
        and
        <em>
            non-null
        </em>
        types. If you don’t declare a variable as nullable, then you cannot assign
        it a null value. This is enforced by the compiler meaning it’s much harder
        to unintentionally crash your app.
    </p>
    <p>
        In contrast to Java, all variables must be initialized at the point of
        declaration.
    </p>
    <p>
        To declare a variable as nullable, you have to append a
        <em>
            ?
        </em>
        to its type at the point of declaration as you see in this
        <em>
            mShareActionProvider
        </em>
        declaration:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            internal
        </span>
        <span class="hljs-keyword">
            var
        </span>
        mShareActionProvider: ShareActionProvider? =
        <span class="hljs-literal">
            null
        </span>
    </pre>
    <h3>
        Safe Calls
    </h3>
    <p>
        To access a property or method on a nullable variable in Java, you would
        first do a null check. You can see this in
        <code>
            DetailActivity.java
        </code>
        :
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            if
        </span>
        (mShareActionProvider !=
        <span class="hljs-keyword">
            null
        </span>
        ) { mShareActionProvider.setShareIntent(shareIntent) }
    </pre>
    <p>
        With Kotlin, you can simplify the above expression with the use of a safe
        call operator (
        <em>
            ?.
        </em>
        ). The property or method is only called when the nullable variable is
        <i>
            not null
        </i>
        .
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        mShareActionProvider?.setShareIntent(shareIntent)
    </pre>
    <p>
        Here,
        <code>
            setShareIntent
        </code>
        is only called when the
        <code>
            mShareActionProvider
        </code>
        property is not null.
    </p>
    <h3>
        The !! Operator
    </h3>
    <p>
        As stated earlier, this is one of possible causes of the dreaded
        <em>
            NullPointerException
        </em>
        . If you’re absolutely sure the object is not null, feel free to use the
        (
        <em>
            !!
        </em>
        ) operator to dereference your object.
    </p>
    <p>
        You can see an example of this in
        <code>
            setShareIntent()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        mShareActionProvider = shareItem!!.actionProvider
        <span class="hljs-keyword">
            as
        </span>
        ShareActionProvider
    </pre>
    <p>
        In here, the
        <em>
            actionProvider
        </em>
        is retrieved if the
        <em>
            shareItem
        </em>
        variable is not null, but a
        <em>
            NullPointerException
        </em>
        is thrown when the
        <em>
            shareItem
        </em>
        variable is null.
    </p>
    <h3>
        The Elvis Operator
    </h3>
    <p>
        The Elvis Operator (
        <em>
            ?:
        </em>
        ) looks like the ternary
        <code>
            if
        </code>
        operator in Java but works differently. You can see an example of this
        when trying to get the length of the cover ID:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        len = coverId?.length ?:
        <span class="hljs-number">
            0
        </span>
    </pre>
    <p>
        If the expression to the left of the Elvis operator is not null, the results
        of the expression are returned. Otherwise, the it returns the expression
        to the right.
    </p>
    <p>
        Just like an
        <code>
            if-else
        </code>
        statement, Elvis only evaluates the expression on the right if the one
        on the left side is null.
    </p>
    <h3>
        Type Inference
    </h3>
    <p>
        Kotlin also supports type inference, meaning the compiler can assume its
        type from the initializer when a variable is declared and initialized.
        For example, the types of the
        <code>
            IMAGE_URL_BASE
        </code>
        and
        <code>
            mImageURL
        </code>
        variables are inferred from their initializers.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        IMAGE_URL_BASE =
        <span class="hljs-string">
            "http://covers.openlibrary.org/b/id/"
        </span>
        <span class="hljs-keyword">
            internal
        </span>
        <span class="hljs-keyword">
            var
        </span>
        mImageURL =
        <span class="hljs-string">
            ""
        </span>
    </pre>
    <p>
        The compiler tracks the inferred type of each variable (each is a
        <code>
            String
        </code>
        ), and any subsequent values assigned to the variable must also be of
        that type (
        <code>
            String
        </code>
        ).
    </p>
    <h3>
        The Coolest of Them All
    </h3>
    <p>
        Already thinking of rewriting your Java project in Kotlin? Don’t stress
        — the Kotlin plugin has you covered.
    </p>
    <p>
        Since Kotlin is a programming language made by developers for developers,
        it’s designed to make your life as easy as possible. The Kotlin plugin
        even has a handy tool that allows you to convert a Java source file to
        Kotlin.
    </p>
    <p>
        Take this sanity-saving feature for a test drive by converting the
        <em>
            DetailActivity.java
        </em>
        file to Kolin.
    </p>
    <p>
        Open the
        <em>
            DetailActivity.java
        </em>
        class and go to
        <em>
            Code\Convert Java File to Kotlin File
        </em>
        .
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
        Click
        <em>
            OK
        </em>
        on the
        <em>
            Convert Java to Kotlin
        </em>
        screen. This will replace the Java file with a Kotlin one!
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
        That’s it. You’ve converted a Java class into a Kotlin class. :]
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/not_bad-1.png"
        rel="attachment wp-att-131964" sl-processed="1">
            <img class="aligncenter size-full wp-image-131964" src="https://koenig-media.raywenderlich.com/uploads/2016/04/not_bad-1.png"
            alt="not_bad" width="296" height="262">
        </a>
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
        Congratulations! You just learned about the Kotlin programming language
        and some of it’s amazing features, re-coded a Java Activity in Kotlin,
        and used the Kotlin plugin to convert a Java source file into a Kotlin
        source file.
    </p>
    <p>
        Download the final project for this tutorial
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/07/omg-android-final.zip"
        target="_blank" title="here" sl-processed="1">
            here
        </a>
        .
    </p>
    <p>
        I suggest reading up further on
        <a href="https://kotlinlang.org/docs/reference/null-safety.html" title="Null Safety in Kotlin"
        sl-processed="1">
            Null Safety in Kotlin
        </a>
        in the documentation.
    </p>
    <p>
        You can also use the
        <a href="http://try.kotlinlang.org/" target="_blank" title="Kotlin online compiler"
        sl-processed="1">
            Kotlin online compiler
        </a>
        to try out code samples and improve your knowledge of the language.
    </p>
    <p>
        You’ve only scratched the surface of the amazing possibilities with Kotlin.
        If you’re excited by what you’ve read here, you can checkout topics such
        as
        <a href="http://kotlinlang.org/docs/reference/data-classes.html" target="_blank"
        title="Data Classes" sl-processed="1">
            Data Classes
        </a>
        ,
        <a href="http://kotlinlang.org/docs/reference/extensions.html" target="_blank"
        title="Extensions" sl-processed="1">
            Extensions
        </a>
        ,
        <a href="http://kotlinlang.org/docs/reference/coding-conventions.html#lambdas"
        target="_blank" title="Lambdas" sl-processed="1">
            Lambdas
        </a>
        , or
        <a href="http://kotlinlang.org/docs/reference/basic-syntax.html#using-string-templates"
        target="_blank" title="String Templates" sl-processed="1">
            String Templates
        </a>
        if you need to satisfy your appetite for knowledge.
    </p>
</div>