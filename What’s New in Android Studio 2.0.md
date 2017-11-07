# Android Studio 2.0的新特性
---
#### [原文地址](https://www.raywenderlich.com/124936/whats-new-android-studio-2-0) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature.png"
        rel="attachment wp-att-131354" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature-250x250.png"
            alt="AndroidStudio2-feature" width="250" height="250" class="alignright size-thumbnail wp-image-131354 bordered"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/04/AndroidStudio2-feature-128x128.png 128w"
            sizes="(max-width: 250px) 100vw, 250px">
        </a>
    </p>
    <p>
        在2015的上一季度，Google宣布了一个全新的，Android为中心的叫做
        <a href="https://plus.google.com/+AndroidDevelopers/posts/dc8nMz7gpRQ"
        sl-processed="1">
            Android Dev Summit
        </a>
        的会议。Google将会议的内容高度保密，并宣称是“深度的技术会议”，但对Android Studio的新特性做出了
        <a href="https://www.youtube.com/watch?v=BKU-wmTAPdc" sl-processed="1">
            巨大的暗示
        </a>
        。
    </p>
    <p>
        毫无疑问，Android Dev Summit中最大的明星就是Android Studio 2.0（而不是平台和工具工程师）。Android的团队精心地打造了它的界面。更重要的是，Android Tools团队显然关注到了速度的需求，他们增强了build及Android模拟器的速度和性能，因此也获得了一个闪亮的“2.0”徽章。
    </p>
    <p>
        4月7日，Google在它们的“稳定”频道中发布了Android Studio 2.0，它不在是一个预览版了，而是Android开发的新标准！在本文中，你会了解到Android Studio 2.0中的提示点，并对其进行一些常识。
    </p>
    <p>
        如果你是一个Android开发的纯小白，你应当首先学习
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Beginning%20Android%20Development%20Part%20One%20Installing%20Android%20Studio.md"
        sl-processed="1">
            Android初学者教程
        </a>
        。尤其是，你应当可以设置并运行Android Studio和Android模拟器。如果你需要帮助，请查看
        <a href="http://www.raywenderlich.com/120177/beginning-android-development-tutorial-installing-android-studio"
        sl-processed="1">
            Android开发者教程：安装Android Studio
        </a>
        .
    </p>
    <p>
        好的，让我们来看一下测试版的Android Studio 2.0吧！
    </p>
    <h2>
        入门
    </h2>
    <p>
        首先，下载本文的
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/04/AS2.zip"
        sl-processed="1">
            配套项目
        </a>
        。这是一个完整的Android项目，供你在测试驱动上使用。其中有几处代码你会进行修改，但仅仅作为演示新版Android Studio特性的一部分。
    </p>
    <p>
        启动Android Studio，在
        <em>
            Welcome to Android Studio
        </em>
        对话框中，选择
        <em>
            导入项目（Eclipse ADT, Gradle, etc.）
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/02_android_studio_welcome_screen.png"
        rel="attachment wp-att-124938" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/02_android_studio_welcome_screen-480x269.png"
            alt="Android Studio: Welcome to Android Studio" width="480" height="269"
            class="aligncenter size-medium wp-image-124938" srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/02_android_studio_welcome_screen-480x269.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/02_android_studio_welcome_screen.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        选择配套项目的顶层目录，并点击
        <em>
            OK
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/03_android_studio_select_project.png"
        rel="attachment wp-att-124939" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/03_android_studio_select_project-334x320.png"
            alt="Select companion project" width="334" height="320" class="aligncenter size-medium wp-image-124939"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/03_android_studio_select_project-334x320.png 334w, https://koenig-media.raywenderlich.com/uploads/2016/01/03_android_studio_select_project-522x500.png 522w, https://koenig-media.raywenderlich.com/uploads/2016/01/03_android_studio_select_project-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/01/03_android_studio_select_project.png 700w"
            sizes="(max-width: 334px) 100vw, 334px">
        </a>
    </p>
    <p>
        浏览这个项目，你应当看到两个activity和两个
        <code>
            RecyclerView
        </code>
        的view holder类，以及相应的资源和布局文件。不必担心其中的细节，你不会大量地编辑这些文件。
    </p>
    <p>
        运行项目。你会看到如下的界面：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/04_app_first_build.png"
        rel="attachment wp-att-124940" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/04_app_first_build-317x500.png"
            alt="First build of companion app" width="317" height="500" class="aligncenter size-large wp-image-124940"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/04_app_first_build-317x500.png 317w, https://koenig-media.raywenderlich.com/uploads/2016/01/04_app_first_build-203x320.png 203w, https://koenig-media.raywenderlich.com/uploads/2016/01/04_app_first_build-768x1210.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/04_app_first_build.png 958w"
            sizes="(max-width: 317px) 100vw, 317px">
        </a>
    </p>
    <p>
        顶部的卡片中有几个小部件 - 你会在之后玩转它们。在widgets的下面，你应当可以看到有用的链接，以便更进一步地阅读本文中涉及到一些材料。
    </p>
    <h2>
        改进的IDE
    </h2>
    <p>
        虽然你只是一个完成UI的Android开发者，但这并不意味着你不渴望
        <em>
            更加
        </em>
        梦幻的UI。Android Studio 2.0可以满足你的渴望，包括几个UI的提升和新的工具，供你体验。
    </p>
    <h3>
        IntelliJ功能
    </h3>
    <p>
        Google的Android Studio基于Jetbrains的
        <a href="https://www.jetbrains.com/idea/" sl-processed="1">
            IntelliJ IDEA
        </a>
        。尽管这两个IDE拥有不同的公司和开发团队，但它们相互导入了功能，这是一个好消息，因为IntelliJ中含有用于代码导航、检查和重构的有用工具。事实上，Android Studio 2.0早已包含了来自最新版本（本文发布时）的IntelliJ（15）中的功能。
    </p>
    <p>
        一个功能就是在
        <i>
            Find in Path
        </i>
        中的即时结果。让我们试一下吧！
    </p>
    <p>
        在Android Studio中，选择
        <em>
            Edit / Find / Find in Path
        </em>
        (或使用键盘快捷键
        <em>
            CMD+Shift+F
        </em>
        ）。在弹出的
        <em>
            Find in Path
        </em>
        窗口中，选择
        <em>
            Preview
        </em>
        选项卡。在
        <em>
            Text to find
        </em>
        处输入要搜索的文本。为了确保在Preview选项卡中可以看到搜索的结果，请确保Options tab中的
        <em>
            Regular expressions
        </em>
        未被选中。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/05_intellij_find_in_path_preview.png"
        rel="attachment wp-att-124941" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/05_intellij_find_in_path_preview-468x500.png"
            alt="Live Preview of Text Search" width="468" height="500" class="aligncenter size-large wp-image-124941"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/05_intellij_find_in_path_preview-468x500.png 468w, https://koenig-media.raywenderlich.com/uploads/2016/01/05_intellij_find_in_path_preview-300x320.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/01/05_intellij_find_in_path_preview-768x820.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/05_intellij_find_in_path_preview.png 980w"
            sizes="(max-width: 468px) 100vw, 468px">
        </a>
    </p>
    <p>
        搜索结果会在你输入搜索文本的时候实时地更新。这些结果还会利用你在
        <i>
            Options
        </i>
        tab中设置的选项，给急躁的你以全面的搜索能力。
    </p>
    <p>
        IntelliJ 15中还有一个方便的新代码检查工具，
        <i>
            Expression Type
        </i>
        ，会在你不清楚一个表达式结果的类型时提供帮助。
    </p>
    <p>
        要实际地看到它，选中你代码中的表达式，并按下
        <em>
            CTRL+Shift+P
        </em>
        键。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/06_intellij_expression_type.png"
        rel="attachment wp-att-124942" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/06_intellij_expression_type-480x74.png"
            alt="Using Expression Type" width="480" height="74" class="aligncenter size-medium wp-image-124942"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/06_intellij_expression_type-480x74.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/06_intellij_expression_type.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        这样就可以确定表达式值的类型了，并将其展示到提示框中。Sweet！
    </p>
    <p>
        你可以从
        <a href="https://www.jetbrains.com/idea/whatsnew/" sl-processed="1">
            Jetbrains
        </a>
        中了解更多关于最新的IntelliJ 15的功能（也可以在Android Studio中使用。
    </p>
    <h3>
        Deep Links整合
    </h3>
    <p>
        可以在app中打开
        <em>
            deep links
        </em>
        ，使你的app出现在相应的Google搜索结果中。你可以通过
        <em>
            intent filters
        </em>
        来创建deep links，去处理相应的URLs。如果你尚未熟悉intent filters，可以访问我们的
        <a href="http://www.raywenderlich.com/103044/android-intents-tutorial"
        sl-processed="1">
            Android: Intents Tutorial
        </a>
        。
    </p>
    <p>
        Android Studio 1.5早已提供了一个简单的方法来在你的Android Manifest中生成这些intent filters，而在Android Studio 2.0中则添加了静态分析，来验证你的app是否已准备好app索引。
    </p>
    <p>
        试验一下吧，在Android Studio中打开
        <em>
            AndroidManifest.xml
        </em>
        。
    </p>
    <p>
        你应当会看到下列的内容：
    </p>
    <pre lang="xml" class="language-xml hljs">&lt;?xml version="1.0" encoding="utf-8"?&gt;
<span class="hljs-tag">&lt;<span class="hljs-name">manifest</span> <span class="hljs-attr">package</span>=<span class="hljs-string">"com.raywenderlich.as20allthethings"</span>
          <span class="hljs-attr">xmlns:android</span>=<span class="hljs-string">"http://schemas.android.com/apk/res/android"</span>&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">uses-permission</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.permission.ACCESS_FINE_LOCATION"</span>/&gt;</span>

  <span class="hljs-tag">&lt;<span class="hljs-name">application</span>
      <span class="hljs-attr">android:allowBackup</span>=<span class="hljs-string">"true"</span>
      <span class="hljs-attr">android:icon</span>=<span class="hljs-string">"@mipmap/ic_launcher"</span>
      <span class="hljs-attr">android:label</span>=<span class="hljs-string">"@string/app_name"</span>
      <span class="hljs-attr">android:supportsRtl</span>=<span class="hljs-string">"true"</span>
      <span class="hljs-attr">android:theme</span>=<span class="hljs-string">"@style/AppTheme"</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">activity</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">".MainActivity"</span>&gt;</span>
      <span class="hljs-tag">&lt;<span class="hljs-name">intent-filter</span>&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">action</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.action.MAIN"</span>/&gt;</span>
        <span class="hljs-tag">&lt;<span class="hljs-name">category</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.category.LAUNCHER"</span>/&gt;</span>
      <span class="hljs-tag">&lt;/<span class="hljs-name">intent-filter</span>&gt;</span>
    <span class="hljs-tag">&lt;/<span class="hljs-name">activity</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">activity</span>
        <span class="hljs-attr">android:name</span>=<span class="hljs-string">".DeepLinkActivity"</span>
        <span class="hljs-attr">android:theme</span>=<span class="hljs-string">"@style/AppTheme.Green"</span>/&gt;</span>

  <span class="hljs-tag">&lt;/<span class="hljs-name">application</span>&gt;</span>

<span class="hljs-tag">&lt;/<span class="hljs-name">manifest</span>&gt;</span>
</pre>
    <p>
        右击
        <code>
            activity android:name=".DeepLinkActivity"
        </code>
        标签，在弹出的菜单中，选择
        <em>
            Generate \ URL
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/07_deep_link_add_context_menu.png"
        rel="attachment wp-att-124943" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/07_deep_link_add_context_menu-480x117.png"
            alt="Add a Deep Link Intent Filter: Context Menu" width="480" height="117"
            class="aligncenter size-medium wp-image-124943" srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/07_deep_link_add_context_menu-480x117.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/07_deep_link_add_context_menu-700x171.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/07_deep_link_add_context_menu.png 720w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        或者，点击这个tag并按下
        <em>
            Option+Enter
        </em>
        键；在弹出的菜单中，选择
        <em>
            Add URL
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/08_deep_link_add_keyboard_shortcut.png"
        rel="attachment wp-att-124944" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/08_deep_link_add_keyboard_shortcut-480x85.png"
            alt="Add a Deep Link Intent Filter:  Generate" width="480" height="85"
            class="aligncenter size-medium wp-image-124944" srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/08_deep_link_add_keyboard_shortcut-480x85.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/08_deep_link_add_keyboard_shortcut-700x124.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/08_deep_link_add_keyboard_shortcut.png 720w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        通过上述的任一方法来生成必须的intent filter。
        <code>
            activity
        </code>
        现在看起来应当像是这样：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">activity</span>
    <span class="hljs-attr">android:name</span>=<span class="hljs-string">".DeepLinkActivity"</span>
    <span class="hljs-attr">android:theme</span>=<span class="hljs-string">"@style/AppTheme.Green"</span>&gt;</span>
  <span class="hljs-comment">&lt;!-- ATTENTION: This intent was auto-generated. Follow instructions at
https://g.co/AppIndexing/AndroidStudio to publish your URLs. --&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">intent-filter</span>&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">action</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.action.VIEW"</span>/&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">category</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.category.DEFAULT"</span>/&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">category</span> <span class="hljs-attr">android:name</span>=<span class="hljs-string">"android.intent.category.BROWSABLE"</span>/&gt;</span>
    <span class="hljs-comment">&lt;!-- ATTENTION: This data URL was auto-generated. We recommend that you use the HTTP scheme.
      <span class="hljs-doctag">TODO:</span> Change the host or pathPrefix as necessary. --&gt;</span>
    <span class="hljs-tag">&lt;<span class="hljs-name">data</span>
        <span class="hljs-attr">android:host</span>=<span class="hljs-string">"as20allthethings.raywenderlich.com"</span>
        <span class="hljs-attr">android:pathPrefix</span>=<span class="hljs-string">"/deeplink"</span>
        <span class="hljs-attr">android:scheme</span>=<span class="hljs-string">"http"</span>/&gt;</span>
  <span class="hljs-tag">&lt;/<span class="hljs-name">intent-filter</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">activity</span>&gt;</span>
</pre>
    <p>
        正如你所看到的，Android Studio完成了设置intent filter的大部分工作，这样任何匹配于“http://as20allthethings.raywenderlich.com/deeplink”的URL就可以被这个app处理了。
    </p>
    <p>
        为了实际地看到Android Studio 2.0的静态分析，将
        <code>
            data
        </code>
        修改为如下的样子：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">data</span>
    <span class="hljs-attr">android:host</span>=<span class="hljs-string">"as20allthethings.raywenderlich.com"</span>/&gt;</span>
</pre>
    <p>
        现在Android Studio 2.0会抱怨你做了一些不好的事情。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/09_deep_link_error_explanation.png"
        rel="attachment wp-att-124945" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/09_deep_link_error_explanation-480x117.png"
            alt="Deep Link Lint error" width="480" height="117" class="aligncenter size-medium wp-image-124945"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/09_deep_link_error_explanation-480x117.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/09_deep_link_error_explanation-768x187.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/09_deep_link_error_explanation-700x171.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/09_deep_link_error_explanation.png 1229w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        这里，Android Studio会特意提示你，Google搜索无法很好地处理这些无效的URL。撤销这些操作，让Android Studio和你的app愉快地在一起。
    </p>
    <p>
        你可能会觉得这个改进很小，但app索引也是一个强有力的工具，与Google搜索的集成可以提升app的可见性和实用性。有关app索引的更多内容，请访问
        <a href="https://developers.google.com/app-indexing/" sl-processed="1">
            this overview from Google Developers
        </a>
        。
    </p>
    <h3>    
        统一的单元测试和Android Instrumentation测试
    </h3>
    <p>
        如果熟悉Android中的单元测试，你就会知道在Android Studio中有两种类型的单元测试：
    </p>
    <ul>
        <li>
            <em>
                本地单元测试
            </em>
            是不依赖Android framework的单元测试，只需运行在本地的机器上。
        </li>
        <li>
            <em>
                装备化的单元测试
            </em>
            是必须运行在一个设备或是模拟器上的单元测试。
        </li>
    </ul>
    <p>
        在之前的版本中，你必须在
        <i>
            Build Variants
        </i>
        窗口中的
        <i>
            Test Artifacts
        </i>
        设置中，选择需要的类型。这样你就只能运行这种类型的测试，且只能在project概览中看到这种类型的测试。
    </p>
    <div id="attachment_124946" style="width: 490px" class="wp-caption aligncenter">
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/10_android_studio_test_artifact_unit.png"
        rel="attachment wp-att-124946" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/10_android_studio_test_artifact_unit-480x315.png"
            alt="Unit Tests Artifact" width="480" height="315" class="size-medium wp-image-124946"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/10_android_studio_test_artifact_unit-480x315.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/10_android_studio_test_artifact_unit.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
        <p class="wp-caption-text">
            Android Studio 2.0版本前的单元测试选择
        </p>
    </div>
    <div id="attachment_124947" style="width: 490px" class="wp-caption aligncenter">
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/11_android_studio_test_artifact_instrumentation.png"
        rel="attachment wp-att-124947" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/11_android_studio_test_artifact_instrumentation-480x316.png"
            alt="Android Instrumentation Tests Artifact" width="480" height="316" class="size-medium wp-image-124947"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/11_android_studio_test_artifact_instrumentation-480x316.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/11_android_studio_test_artifact_instrumentation.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
        <p class="wp-caption-text">
            Android Studio 2.0前的Instrumentation测试选择
        </p>
    </div>
    <p>
        而在Android Studio 2.0中有一个统一的测试视图。现在你可以同时运行两种测试，免除对测试类型的选择。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/13_android_studio_all_test_artifacts.png"
        rel="attachment wp-att-124949" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/13_android_studio_all_test_artifacts-399x320.png"
            alt="Project View: All Test Artifacts Enabled" width="399" height="320"
            class="aligncenter size-medium wp-image-124949" srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/13_android_studio_all_test_artifacts-399x320.png 399w, https://koenig-media.raywenderlich.com/uploads/2016/01/13_android_studio_all_test_artifacts-624x500.png 624w, https://koenig-media.raywenderlich.com/uploads/2016/01/13_android_studio_all_test_artifacts.png 700w"
            sizes="(max-width: 399px) 100vw, 399px">
        </a>
    </p>
    <p>
        有关Android单元测试的更多信息，请访问
        <a href="http://developer.android.com/tools/testing/testing_android.html"
        sl-processed="1">
            developer.android.com
        </a>
        。
    </p>
    <h3>
        GPU分析器
    </h3>
    <p>
        新的GPU分析器是为GL图形开发者准备的一个超帮的功能。定位于节约图形debug过程中所花费的大量时间，GPU分析器提供了细致检查GPU状态的能力。开发者可以记录并逐帧地重播场景，以及查看创建状态和场景的GPU命令序列。
    </p>
    <p>
        本文并非着眼于GPU分析器的细节，你可以在
        <a href="http://tools.android.com/tech-docs/gpu-profiler" sl-processed="1">
            Android Tools Project Site
        </a>
        中查看更多的信息。
    </p>
    <div id="attachment_124950" style="width: 490px" class="wp-caption aligncenter">
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/14_android_studio_gpu_profiler.png"
        rel="attachment wp-att-124950" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/14_android_studio_gpu_profiler-480x300.png"
            alt="Android Studio: GPU Profiler" width="480" height="300" class="size-medium wp-image-124950"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/14_android_studio_gpu_profiler-480x300.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/14_android_studio_gpu_profiler-768x480.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/14_android_studio_gpu_profiler-700x438.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
        <p class="wp-caption-text">
            来自Android Dev Summit的主题演讲：https://youtu.be/xdItHEVfQ4U?t=15m57s
        </p>
    </div>
    <p>
        由于你所写app的不同，GPU分析器可能并非是一个常用的工具。但下一节就会介绍一个你经常使用，且经过了多次改进的工具：Android模拟器。
    </p>
    <h2>
        Android模拟器2.0
    </h2>
    <p> 
        坦白来说，并没有太多开发者喜欢Android自带的模拟器，很多人都在诟病它超慢的启动速度及糟糕的性能。在一个很长的时期内，Android Studio自带的模拟器都缺乏很多第三方模拟器所带有的功能和UI遍历。
    </p>
    <p>
        幸运的是，Android模拟器2.0的出现完全改变了这个局面，大幅地改进了其UI和运行速度。
    </p>
    <h3>
        新节目
    </h3>
    <p>
        关于Android模拟器2.0的第一件事，是屏幕的渲染区域看起来和之前是相同的，带有手机的边框及灰色的窗口边框，且模拟器还有一个新的工具栏。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/15_android_emulator_2_0.png"
        rel="attachment wp-att-124951" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/15_android_emulator_2_0-336x500.png"
            alt="Android Emulator 2.0" width="336" height="500" class="aligncenter size-large wp-image-124951"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/15_android_emulator_2_0-336x500.png 336w, https://koenig-media.raywenderlich.com/uploads/2016/01/15_android_emulator_2_0-215x320.png 215w, https://koenig-media.raywenderlich.com/uploads/2016/01/15_android_emulator_2_0.png 700w"
            sizes="(max-width: 336px) 100vw, 336px">
        </a>
    </p>
    <p>
        Android团队还添加了一个听起来很简单的功能，就像他们所说的，这是一个经常被希望得到改进的功能：通过拖动窗口来改变模拟器的大小（不过有时会得到可笑的结果）。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/16_android_emulator_resize.png"
        rel="attachment wp-att-124968" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/16_android_emulator_resize-592x500.png"
            alt="Android Emulator 2.0: Resizing" width="592" height="500" class="aligncenter size-large wp-image-124968"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/16_android_emulator_resize-592x500.png 592w, https://koenig-media.raywenderlich.com/uploads/2016/01/16_android_emulator_resize-379x320.png 379w, https://koenig-media.raywenderlich.com/uploads/2016/01/16_android_emulator_resize.png 700w"
            sizes="(max-width: 592px) 100vw, 592px">
        </a>
    </p>
    <p>
        说的拖动，你现在还可以将文件拖到这个模拟器上。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/17_android_apk_drag_and_drop.png"
        rel="attachment wp-att-124953" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/17_android_apk_drag_and_drop-700x311.png"
            alt="Android Emulator 2.0: Drag and Drop APKs" width="700" height="311"
            class="aligncenter size-large wp-image-124953" srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/17_android_apk_drag_and_drop-700x311.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/17_android_apk_drag_and_drop-480x213.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/17_android_apk_drag_and_drop-768x341.png 768w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        新的模拟器工具栏，提供了对模拟器方便的控制途径，如音量，返回键，Home键，电源键等。它还提供了屏幕旋转按钮（旧版模拟器需要通过键盘快捷键或一个难记的ADB命令来旋转屏幕）以及一个截图按钮。
    </p>
    <p>
        点击工具栏底部的按钮，你会看到一个
        <em>
            Extended controls
        </em>
        窗口。选择
        <em>
            Settings
        </em>
        。你可以在这里设置保存截图的目录。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/18_android_emulator_2_0_extended_controls.png"
        rel="attachment wp-att-124954" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/18_android_emulator_2_0_extended_controls-586x500.png"
            alt="Extended controls: Settings" width="586" height="500" class="aligncenter size-large wp-image-124954"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/18_android_emulator_2_0_extended_controls-586x500.png 586w, https://koenig-media.raywenderlich.com/uploads/2016/01/18_android_emulator_2_0_extended_controls-375x320.png 375w, https://koenig-media.raywenderlich.com/uploads/2016/01/18_android_emulator_2_0_extended_controls-768x656.png 768w"
            sizes="(max-width: 586px) 100vw, 586px">
        </a>
    </p>
    <p>
        <em>
            Extended controls
        </em>
        窗口还展示了Android Studio 2.0中很多方便测试你app的超棒的功能。你可以模拟设备的环境并验证其行为，比如你的app如何处理不同类型的网络，网速，电量状态变化，定位更新等等。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/19_android_emulator_2_0_extended_controls_cellular.png"
        rel="attachment wp-att-124955" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/19_android_emulator_2_0_extended_controls_cellular-480x211.png"
            alt="Extended controls: Cellular" width="480" height="211" class="aligncenter size-medium wp-image-124955"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/19_android_emulator_2_0_extended_controls_cellular-480x211.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/19_android_emulator_2_0_extended_controls_cellular-768x337.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/19_android_emulator_2_0_extended_controls_cellular-700x308.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        甚至，还有一个模拟指纹输入的控件。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/20_android_extended_controls_fingerprint.png"
        rel="attachment wp-att-124956" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/20_android_extended_controls_fingerprint-480x254.png"
            alt="Extended controls: Fingerprint" width="480" height="254" class="aligncenter size-medium wp-image-124956"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/20_android_extended_controls_fingerprint-480x254.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/20_android_extended_controls_fingerprint-768x407.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/20_android_extended_controls_fingerprint-700x371.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/20_android_extended_controls_fingerprint.png 1020w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        让我们来尝试一下上述工具在配套app中的实践吧。
    </p>
    <h3>
        电话/短信
    </h3>
    <p>
        在
        <em>
            Extended controls
        </em>
        窗口中选择
        <em>
            Phone
        </em>
        。你应当会看到一个包含手机号码和文本信息输入框的表单：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/21_android_extended_controls_phone_01.png"
        rel="attachment wp-att-124957" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/21_android_extended_controls_phone_01-474x320.png"
            alt="Extended controls: Phone" width="474" height="320" class="aligncenter size-medium wp-image-124957"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/21_android_extended_controls_phone_01-474x320.png 474w, https://koenig-media.raywenderlich.com/uploads/2016/01/21_android_extended_controls_phone_01-768x519.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/21_android_extended_controls_phone_01-700x473.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/21_android_extended_controls_phone_01.png 1072w"
            sizes="(max-width: 474px) 100vw, 474px">
        </a>
    </p>
    <p>
        在
        <em>
            SMS text
        </em>
        中，输入
        <i>
            Check this out! http://as20allthethings.raywenderlich.com/deeplink
        </i>
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/04/deeplink_sms.png"
        alt="Extended controls: Sending a SMS" width="319" height="344" class="aligncenter size-full wp-image-130929"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/04/deeplink_sms.png 319w, https://koenig-media.raywenderlich.com/uploads/2016/04/deeplink_sms-297x320.png 297w"
        sizes="(max-width: 319px) 100vw, 319px">
    </p>
    <p>
        点击
        <em>
            SEND MESSAGE
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/23_android_extended_controls_phone_03.png"
        rel="attachment wp-att-124959" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/23_android_extended_controls_phone_03-246x500.png"
            alt="Extended controls: SMS received" width="246" height="500" class="aligncenter size-large wp-image-124959"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/23_android_extended_controls_phone_03-246x500.png 246w, https://koenig-media.raywenderlich.com/uploads/2016/01/23_android_extended_controls_phone_03-157x320.png 157w, https://koenig-media.raywenderlich.com/uploads/2016/01/23_android_extended_controls_phone_03.png 700w"
            sizes="(max-width: 246px) 100vw, 246px">
        </a>
    </p>
    <p>
        哈哈！你只是把短信发给了模拟器，不必紧张得冒汗。
    </p>
    <div class="note">
        <p>
            <em>
                注意：
            </em>
            正如在deep link整合中所讨论的，这个app现在就有了一个intent过滤器来处理文本信息中的URL。
        </p>
        <p>
            想要实际查看deep link，只需在模拟器中打开短信app，并点击链接即可。
        </p>
    </div>
    <h3>
        电池和充电状态
    </h3>
    <p>
        在2.0版本中，你可以直接操作的另一个设备状态，就是电池和充电状态了。
    </p>
    <p>
        运行这个app。顶部卡片中的一部分区域，就展示了该设备当前的电池状态。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/24_android_extended_controls_battery_01.png"
        rel="attachment wp-att-124960" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/24_android_extended_controls_battery_01-360x320.png"
            alt="Companion App: Battery Status" width="360" height="320" class="aligncenter size-medium wp-image-124960"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/24_android_extended_controls_battery_01-360x320.png 360w, https://koenig-media.raywenderlich.com/uploads/2016/01/24_android_extended_controls_battery_01-563x500.png 563w, https://koenig-media.raywenderlich.com/uploads/2016/01/24_android_extended_controls_battery_01.png 678w"
            sizes="(max-width: 360px) 100vw, 360px">
        </a>
    </p>
    <p>
        要进行更改，打开
        <em>
            Extended controls
        </em>
        窗口并选择
        <em>
            Battery
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/25_android_extended_controls_battery_02.png"
        rel="attachment wp-att-124961" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/25_android_extended_controls_battery_02-480x203.png"
            alt="Extended controls: Battery" width="480" height="203" class="aligncenter size-medium wp-image-124961"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/25_android_extended_controls_battery_02-480x203.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/25_android_extended_controls_battery_02-768x325.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/25_android_extended_controls_battery_02-700x296.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        这里有几个可以用来操作电池状态的控件。使用
        <em>
            Charge level滑动条
        </em>
        来改变电量，并观察模拟器中状态栏上即时的更新。选择
        <em>
            Battery status
        </em>
        下拉菜单中的
        <em>
            Full
        </em>
        以明确电池的状态。顶部的卡片就会检测到变化的发生，并即刻将新的状态展示出来。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/battery-status-dropdown.png"
        rel="attachment wp-att-126842" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/battery-status-dropdown-550x500.png"
            alt="battery-status-dropdown" width="550" height="500" class="aligncenter size-large wp-image-126842"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/battery-status-dropdown.png 550w, https://koenig-media.raywenderlich.com/uploads/2016/01/battery-status-dropdown-352x320.png 352w"
            sizes="(max-width: 550px) 100vw, 550px">
        </a>
    </p>
    <h3>
        位置更新
    </h3>
    <p>
        在extended control的最后一步，我们将会实践推送位置更新到模拟器上。
    </p>
    <p>
        现在查看顶部的卡片，你会看到文本“No location yet”。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/27_android_extended_controls_location_01.png"
        rel="attachment wp-att-124963" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/27_android_extended_controls_location_01-388x320.png"
            alt="No location yet" width="388" height="320" class="aligncenter size-medium wp-image-124963"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/27_android_extended_controls_location_01-388x320.png 388w, https://koenig-media.raywenderlich.com/uploads/2016/01/27_android_extended_controls_location_01-606x500.png 606w, https://koenig-media.raywenderlich.com/uploads/2016/01/27_android_extended_controls_location_01.png 674w"
            sizes="(max-width: 388px) 100vw, 388px">
        </a>
    </p>
    <p>
        顶部的卡片会监听位置的更新，并将收到的位置展示出来。现在就等着你来推送了！
    </p>
    <p>
        在这个app中，点击
        <em>
            Start
        </em>
        按钮。你会被请求允许app访问设备的位置。点击
        <em>
            ALLOW
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/28_android_extended_controls_location_02.png"
        rel="attachment wp-att-124964" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/28_android_extended_controls_location_02-311x320.png"
            alt="Location permissions" width="311" height="320" class="aligncenter size-medium wp-image-124964"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/28_android_extended_controls_location_02-311x320.png 311w, https://koenig-media.raywenderlich.com/uploads/2016/01/28_android_extended_controls_location_02-486x500.png 486w, https://koenig-media.raywenderlich.com/uploads/2016/01/28_android_extended_controls_location_02-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/01/28_android_extended_controls_location_02.png 676w"
            sizes="(max-width: 311px) 100vw, 311px">
        </a>
    </p>
    <p>
        现在，这个app就会开始等待位置的更新了。
    </p>
    <p>
        要传递一个更新，再次打开
        <em>
            Extended controls
        </em>
        窗口，并选择
        <em>
            Location
        </em>
        。选中
        <em>
            Decimal
        </em>
        ，输入
        <i>
            37.4226
        </i>
        到
        <em>
            Latitude
        </em>
        及
        <i>
            -122.084
        </i>
        到
        <em>
            Longitude
        </em>
        中。点击
        <em>
            SEND
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/29_android_extended_controls_location_03.png"
        rel="attachment wp-att-124965" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/29_android_extended_controls_location_03-480x150.png"
            alt="Location Coordinates Input" width="480" height="150" class="aligncenter size-medium wp-image-124965"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/29_android_extended_controls_location_03-480x150.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/29_android_extended_controls_location_03-768x240.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/29_android_extended_controls_location_03-700x219.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        顶部的卡片现在就会立刻更新，以展示新的位置。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/30_android_extended_controls_location_04.png"
        rel="attachment wp-att-124966" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/30_android_extended_controls_location_04-382x320.png"
            alt="Location update" width="382" height="320" class="aligncenter size-medium wp-image-124966"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/30_android_extended_controls_location_04-382x320.png 382w, https://koenig-media.raywenderlich.com/uploads/2016/01/30_android_extended_controls_location_04-597x500.png 597w, https://koenig-media.raywenderlich.com/uploads/2016/01/30_android_extended_controls_location_04.png 676w"
            sizes="(max-width: 382px) 100vw, 382px">
        </a>
    </p>
    <p>
        如果不想一个一个地输入位置的更新，你甚至可以将一系列的坐标加载到窗口中，并“播放”这个列表。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/31_android_extended_controls_location_05.png"
        rel="attachment wp-att-124967" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/31_android_extended_controls_location_05-480x274.png"
            alt="Location Coordinates List" width="480" height="274" class="aligncenter size-medium wp-image-124967"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/31_android_extended_controls_location_05-480x274.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/31_android_extended_controls_location_05-768x438.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/31_android_extended_controls_location_05-700x399.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/31_android_extended_controls_location_05-266x151.png 266w, https://koenig-media.raywenderlich.com/uploads/2016/01/31_android_extended_controls_location_05.png 1248w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        因为这些工具，Android模拟器2.0中已充满了令人兴奋的功能和超赞的界面，绝对值得去进行尝试。
    </p>
    <h2>
        更好的构建
    </h2>
    <p>
        你可能会和自己说，“Okey，一个快速的模拟器非常得棒，但我仍然会花费大量的时间在构建app上。我该怎么办？”
    </p>
    <p>
        好的，你可以考虑优化代码。如果没有别的，这会带给你一些YouTube的声誉 :]
    </p>
    <p>
        但更好的解决方案 - 你可能已经猜到了 - 就是Android Studio 2.0！
    </p>
    <p>
        Android的工具团队已尝试了提高构建和部署的速度。他们还添加了一项新的功能：Instant Run。你将会在下一节探索这些改进。
    </p>
    <h3>
        更快的构建速度
    </h3>
    <p>
        Android开发工具团队在若干构建系统上进行了巨大的改进，并称将整个构建时间提升了2~2.5倍。要对其进行充分的讨论需要一个相当深入的过程，但通常来说包括以下几点：
    </p>
    <ul>
        <li>
            改进
            <code>
                dx
            </code>
            合并。
            <code>
                dx
            </code>
            是可以将Java类转换为Dalvik可执行格式（.dex）文件的构建工具。
        </li>
        <li>
            调试模式的“收缩机”。
        </li>
        <li>
            针对连接到的特定的设备的构建。
        </li>
    </ul>
    <p>
        有关一般构建和构建系统的信息，请访问
        <a href="http://developer.android.com/sdk/installing/studio-build.html"
        sl-processed="1">
            android.developer.com.
        </a>
        上的
        <a href="http://developer.android.com/tools/help/index.html" sl-processed="1">
            文档
        </a>
        。
    </p>
    <p>
        有关这些构建系统改进的更多信息，请参阅Android Dev Summit上的
        <a href="https://www.youtube.com/watch?v=fs0eira2pRY" sl-processed="1">
            这个会议
        </a>
        。
    </p>
    <h3>
        更快的ADB
    </h3>
    <p>
        模拟器上的Android Debug桥接器（ADB）已收到了push/pull协议的更新。在将APK部署到新的模拟器上的时候，你会发现速度提升了5倍。
    </p>
    <div id="attachment_124977" style="width: 490px" class="wp-caption aligncenter">
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/32_adb_push_speeds.png"
        rel="attachment wp-att-124977" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/32_adb_push_speeds-480x244.png"
            alt="ADB Push Speeds" width="480" height="244" class="size-medium wp-image-124977"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/32_adb_push_speeds-480x244.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/32_adb_push_speeds.png 700w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
        <p class="wp-caption-text">
            来自Android Dev Summit的主题演讲：https://youtu.be/xdItHEVfQ4U?t=13m17s
        </p>
    </div>
    <h3>
        Instant Run
    </h3>
    <p>
        神奇的是，Android Studio 2.0全部是有关速度的需要。Android工具团队不仅提升了构建和部署的速度，他们还尝试了减少了部署的次数。
    </p>
    <p>
        为此，他们推出了
        <em>
            Instant Run
        </em>
        ，它可以将代码和资源推送到你正在运行的app上，
        <i>
            无需
        </i>
        重新进行安装。显然，这将节省大量的时间。
    </p>
    <p>
        对于不同类型的更改，Instant Run会有不同的处理方式。目前，Instant Run有三种方式来实现更新：
    </p>
    <ol>
        <li>
            <em>
                热交换
            </em>
            ：你的app会继续运行，并在下次执行相关方法的时候使用这些改变。该方式适用于方法的更改。
        </li>
        <li>
            <em>
                温交换
            </em>
            ：你的app会继续运行，但会重启当前的activity。这适用于资源的改变。
        </li>
        <li>
            <em>
                冷交换
            </em>
            ：你的app会进行重启，但不会重新安装。这适用于代码结构的改变。
        </li>
    </ol>
    <p>
        你可以在配套app上试用Instant Run。
    </p>
    <p>
        要启用Instant Run，请选择
        <em>
            Preferences / Build, Execution, Deployment / Instant Run
        </em>
        。确认勾选
        <em>
            Enable Instant Run to hot swap code/resource changes on deploy
        </em>
        且取消勾选
        <em>
            Restart activity on code changes
        </em>
        。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/instant-run.png"
        rel="attachment wp-att-126843" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/instant-run-700x277.png"
            alt="instant-run" width="700" height="277" class="aligncenter size-large wp-image-126843"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/instant-run-700x277.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/01/instant-run-480x190.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/instant-run-768x304.png 768w, https://koenig-media.raywenderlich.com/uploads/2016/01/instant-run.png 1000w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        如果配套app尚未运行，现在运行它。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/33_instant_run_01.png"
        rel="attachment wp-att-124987" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/33_instant_run_01-480x45.png"
            alt="Initial app run" width="480" height="45" class="aligncenter size-medium wp-image-124987"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/33_instant_run_01-480x45.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/33_instant_run_01.png 556w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        当app正在运行时，你会看到运行按钮旁边的闪电标记。该标记即表示Instant Run当前是可用的。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/34_instant_run_02.png"
        rel="attachment wp-att-124988" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/34_instant_run_02-480x50.png"
            alt="Instant Run Ready" width="480" height="50" class="aligncenter size-medium wp-image-124988"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/34_instant_run_02-480x50.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/01/34_instant_run_02.png 560w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        为进行测试，打开
        <em>
            colors.xml
        </em>
        并对颜色进行如下的更改：
    </p>
    <pre lang="xml" class="language-xml hljs"><span class="hljs-tag">&lt;<span class="hljs-name">resources</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">color</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"colorPrimary"</span>&gt;</span>#455A64<span class="hljs-tag">&lt;/<span class="hljs-name">color</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">color</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"colorPrimaryDark"</span>&gt;</span>#263238<span class="hljs-tag">&lt;/<span class="hljs-name">color</span>&gt;</span>
  <span class="hljs-tag">&lt;<span class="hljs-name">color</span> <span class="hljs-attr">name</span>=<span class="hljs-string">"colorAccent"</span>&gt;</span>#2196F3<span class="hljs-tag">&lt;/<span class="hljs-name">color</span>&gt;</span>
<span class="hljs-tag">&lt;/<span class="hljs-name">resources</span>&gt;</span>
</pre>
    <p>
        这里只是改变了
        <code>
            colorPrimary
        </code>
        和
        <code>
            colorPrimaryDark
        </code>
        的值，它们确定了状态栏和操作栏的颜色。
    </p>
    <p>
        点击
        <em>
            Run
        </em>
        按钮。屏幕会发生闪烁，并会出现一个toast通知你activity重启了。你会看到app在没有进行全构建和安装的情况下，就使颜色发生了变化。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/35_instant_run_03.png"
        rel="attachment wp-att-124989" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/35_instant_run_03-194x320.png"
            alt="Instant Run: Warm Swap" width="194" height="320" class="aligncenter size-medium wp-image-124989"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/35_instant_run_03-194x320.png 194w, https://koenig-media.raywenderlich.com/uploads/2016/01/35_instant_run_03-303x500.png 303w, https://koenig-media.raywenderlich.com/uploads/2016/01/35_instant_run_03.png 337w"
            sizes="(max-width: 194px) 100vw, 194px">
        </a>
    </p>
    <p>
        由于activity发生了重启，你可能会猜到这是一个温交换。
    </p>
    <p>
        现在打开
        <em>
            CardViewHolder.java
        </em>
        并对
        <code>
            onClick
        </code>
        方法做出如下的修改：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-meta">@Override</span>
<span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onClick</span><span class="hljs-params">(View v)</span> </span>{
  <span class="hljs-keyword">if</span> (mListener == <span class="hljs-keyword">null</span>) {
    <span class="hljs-keyword">return</span>;
  }

  Snackbar.make(itemView, R.string.instant_run, Snackbar.LENGTH_SHORT).show();

  mListener.onToggleLocationUpdates();
}
</pre>
    <p>
        上面添加代码，会在用户点击顶部卡片上的START/STOP按钮时，展示一个snackbar。
    </p>
    <p>
        点击
        <em>
            Run
        </em>
        按钮。这时会弹出一个toast，通知你“应用代码发生变化，无需重新启动。”
        <br>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/36_instant_run_04.png"
        rel="attachment wp-att-124990" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/36_instant_run_04-193x320.png"
            alt="Instant Run: Hot swap" width="193" height="320" class="aligncenter size-medium wp-image-124990"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/36_instant_run_04-193x320.png 193w, https://koenig-media.raywenderlich.com/uploads/2016/01/36_instant_run_04-301x500.png 301w, https://koenig-media.raywenderlich.com/uploads/2016/01/36_instant_run_04.png 337w"
            sizes="(max-width: 193px) 100vw, 193px">
        </a>
    </p>
    <p>
        能猜到这是哪种交换么？
    </p>
    <p>
        如果猜的是热插拔，奖励自己一块饼干吧！:] Instant Run可以在不重启activity的情况下就将这个改变推送给app。点击START/STOP按钮来验证一下吧：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/01/37_instant_run_05.png"
        rel="attachment wp-att-124991" sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/01/37_instant_run_05-194x320.png"
            alt="Instant Run!" width="194" height="320" class="aligncenter size-medium wp-image-124991"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/01/37_instant_run_05-194x320.png 194w, https://koenig-media.raywenderlich.com/uploads/2016/01/37_instant_run_05-303x500.png 303w, https://koenig-media.raywenderlich.com/uploads/2016/01/37_instant_run_05.png 337w"
            sizes="(max-width: 194px) 100vw, 194px">
        </a>
    </p>
    <p>
        Instant Run可以显著地提升生产效率，并大大地减少你为等待构建和部署去上网的时间。除此之外，Instant Run可以使你完成布局和样式更加得高效，因为你可以即使地看到UI变化的效果。
    </p>
    <h2>
        从这儿去向哪里
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
        There certainly is a lot to learn and try out in Android Studio 2.0 and
        Android Emulator 2.0! Much of the information about the two comes from
        the Android Dev Summit presentations, so check out those and other great
        sessions via the
        <a href="https://www.youtube.com/playlist?list=PLWz5rJ2EKKc_Tt7q77qwyKRgytF1RzRx8"
        sl-processed="1">
            recordings posted on YouTube.
        </a>
    </p>
    <p>
        Many of the cool new things in Android Studio 2.0 are works in progress.
        A great way to keep up with updates, bug fixes and new features is to regularly
        check the
        <a href="http://tools.android.com/recent" sl-processed="1">
            Recent Changes
        </a>
        page over at the
        <a href="http://tools.android.com/" sl-processed="1">
            Android Tools Project Site
        </a>
        .
    </p>
    <p>
        The Android Tools Project Site also contains
        <a href="http://tools.android.com/tech-docs" sl-processed="1">
            technical docs
        </a>
        on many of the Android Studio features.
    </p>
</div>