# 开始Android开发教程第一部分：安装Android Studio
---
#### [原文地址](https://www.raywenderlich.com/161318/beginning-android-development-part-one-installing-android-studio) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p><em>更新笔记</em>： 本教程已由Eunice Obugyei更新至适配最新版本的Android Studio。
            <a href="http://www.raywenderlich.com/56107/make-first-android-app-part-1" target="_blank"
                title="Original tutorial" sl-processed="1">原教程</a>是由Matt Luedke编写的。上次的更新是由Darryl Bayliss和Megha Bambra完成的。</p>
    </div>
    <p><img src="https://koenig-media.raywenderlich.com/uploads/2017/06/AndroidStudio-feature-1.png" alt="AndroidRW" width="250"
            height="250" class="alignright size-full wp-image-87100"></p>
    <p>人们对Android app的开发有着强劲的需求，因为全球每月有超过<i>20亿</i>的Android活跃用户。这是一个令人激动的平台，它为创建app提供了广阔的空间。</p>
    <h2>开始Android开发</h2>
    <p>本教程不需要任何的预备知识，除了你的意愿和一台Mac - 当然你也可以在PC上开发Android，但这些教程主要是提供给使用Mac的开发者的。</p>
    <p>你将要学到如何设置全部所需的工具，来开启你成为一名Android开发者的道路。下面是你将在本教程中所做的事情：</p>
    <ol>
        <li>下载并安装Android Studio.</li>
        <li>在模拟器和真机上测试你的app。</li>
        <li>创建一个简单的“Hello World!” Android app。把这句话展示到你设备或模拟器的屏幕上。</li>
        <li>导入一个样本工程到Android Studio中。</li>
    </ol>
    <h2>安装Android Studio</h2>
    <p>开始任何新平台，最重要的事就是配置你的环境了，Android也不例外。</p>
    <p>花一点时间，有条不紊地遵循每一步完成任务非常得重要。即使完全遵循了这些步骤，你也可能需要去解决一个或多个的问题。你的系统配置或是产品的版本都有可能导致意外结果的发生。</p>
    <h2>安装Java</h2>
    <p>记住刚提到的一切，让我们来快速检查一个你是否已安装了Java开发的工具包（JDK）。你最好使用值得信赖的老版<em>Terminal</em>来完成检查。</p>
    <div class="note">
        <p><em>注意</em>：你将在接下来的几段中了解到本教程的基本步骤，但如果你想要深入了解Terminal的知识，你可以在这篇博客<a href="http://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line" target="_blank" title=" teamtreehouse.com" sl-processed="1">teamtreehouse.com</a>中找到一个很好介绍性的教程。</p>
    </div>
    <h3>Terminal</h3>
    <p>简单地说，使用Terminal就像是你在车罩下面看。这时你是在真正面对面地了解机器，没有任何复杂的图形界面。</p>
    <p>你可以在Mac上轻松地找到Terminal：打开启动版并输入<em>terminal</em>到屏幕顶部的搜索框中，并当Terminal被展示出来的时候，选择它。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal-480x207.png" alt="Find Terminal in Launchpad" width="480" height="207" class="aligncenter size-medium wp-image-161322" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal-480x207.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal-650x280.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal.png 1004w" sizes="(max-width: 480px) 100vw, 480px"></a></p>
    <p>打开Terminal之后，输入<code>java -version</code>。你应该会看到一些带有版本号的输出，就像下面这样。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version-480x124.png" alt="Beginning Android development - Check Java version" width="480" height="124" class="aligncenter size-medium wp-image-161328" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version-480x124.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version-650x167.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version.png 1142w" sizes="(max-width: 480px) 100vw, 480px"></a></p>
    <p>如果你看到的不是这样，就说明你还没有安装JDK。Terminal可能会告诉你<code>-bash: java: command not found</code>，或是<code>No Java runtime present, requesting install.</code>并弹出一个窗口引导你前往Oracle的网站进行下载。<br>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-3.13.48-PM-e1449423724199.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-3.13.48-PM-e1449423724199.png" alt="Beginning Android development - Install Java" width="413" height="155" class="aligncenter size-full wp-image-122395"></a></p>
    <p>你可以点击<em>More Info…</em>或到<a href=" http://www.oracle.com/technetwork/java/javase/downloads/index.html" target="_blank" sl-processed="1">Oracle</a>上去下载JDK。</p>
    <p>安装完JDK之后，前往<a href="https://developer.android.com/sdk/installing/studio.html" target="_blank" title="Android Studio page" sl-processed="1">Android Studio页</a>，点击<em>Download Android Studio</em>按钮。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page-650x394.png" alt="Download Android Studio" width="650" height="394" class="aligncenter size-large wp-image-161331" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page-650x394.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page-480x291.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h2>获取Android Studio</h2>
    <p>Google会不断地更新这个页面，因此你看到的版本可能会比上面截图中的更新。点击<em>Download Android Studio</em>按钮，你会看到一个同意条款条件的请求。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions-650x427.png" alt="android-studio-terms-conditions" width="650" height="427" class="aligncenter size-large wp-image-161334" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions-650x427.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions-480x315.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>仔细阅读之后（每个人都会花时间进行完整的阅读，对么？）接受并点击下面蓝色的<em>Download Android Studio For Mac</em>按钮。下载完成后，你就可以像安装其它程序一样地安装Android Studio了。</p>
    <p>下载的链接将会重定向到包含OS X，Windows和Linux操作系统安装引导的页面中。如果这个引导没有出现的话，你可以直接访问
    <a href="https://developer.android.com/studio/install.html"
            target="_blank" title="here" sl-processed="1">这里</a>。</p>
    <p>安装完成之后，你就可以运行<em>Android Studio</em>了！</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2014/12/3.-Android-Studio-Loading.png" sl-processed="1"><img class="aligncenter size-medium wp-image-56524" src="https://koenig-media.raywenderlich.com/uploads/2014/12/3.-Android-Studio-Loading.png" alt="opening_studio_3" width="313" height="240"></a></p>
    <h2>设置Android Studio</h2>
    <p>第一次加载的时候，你会看到一个设置向导。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM.png" sl-processed="1"><img class="aligncenter size-medium wp-image-120269" src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM-426x320.png" alt="Screen Shot 2015-11-08 at 8.08.50 PM" width="426" height="320" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM-426x320.png 426w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM-666x500.png 666w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM.png 1598w" sizes="(max-width: 426px) 100vw, 426px"></a></p>
    <p>点击<em>Next</em>移动到<em>Install Type</em>页。整个过程可能需要花费几分钟的时间。
    </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM.png" sl-processed="1"><img class="aligncenter size-large wp-image-120356" src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM-664x500.png" alt="Screen Shot 2015-11-08 at 8.09.21 PM" width="664" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM-664x500.png 664w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM-425x320.png 425w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM.png 1598w" sizes="(max-width: 664px) 100vw, 664px"></a></p>
    <p>选择<em>Standard</em>并点击<em>Next</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings-650x487.png" alt="verify settings" width="650" height="487" class="aligncenter size-large wp-image-161668" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings-650x487.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings-427x320.png 427w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>在<em>Verify Settings</em>窗口中，你可以有机会来确认你的设置。点击<em>Finish</em>来开始下载SDK组件。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components-650x489.png" alt="downloading components" width="650" height="489" class="aligncenter size-large wp-image-161670" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components-650x489.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components-426x320.png 426w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>下载完成之后，点击<em>Finish</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete-650x490.png" alt="component download complete" width="650" height="490" class="aligncenter size-large wp-image-161671" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete-650x490.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete-424x320.png 424w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>Android Studio的欢迎屏幕</h3>
    <p>几分钟后，你会看到一个欢迎屏幕，它可以作为构建所有Android的大门口。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen-650x450.png" alt="welcome screen" width="650" height="450" class="aligncenter size-large wp-image-161672" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen-650x450.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen-462x320.png 462w, https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen.png 1334w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>即使你刚刚下载的Android Studio，它也有可能不是最新的版本。在欢迎窗口的屏幕底部，依次选择<em>Configure/Check for Update</em>来检查是否有更新的版本可用。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1-543x500.png" alt="check for updates" width="543" height="500" class="aligncenter size-large wp-image-161677" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1-543x500.png 543w, https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1-348x320.png 348w, https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1.png 1334w" sizes="(max-width: 543px) 100vw, 543px"></a></p>
    <p>如果有新的版本可用，就会弹出一个类似下面截图的窗口。点击<em>Update and Restart</em>按钮来让它完成更新的工作。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen-650x452.png" alt="update screen" width="650" height="452" class="aligncenter size-large wp-image-161678" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen-650x452.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen-460x320.png 460w, https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen.png 1332w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h2>Android SDK管理器</h2>
    <p>每个版本的Android都有它自己的<em>SDK</em>（Software Development Kit）来让你创建Android平台上的app。由于你刚刚已经过了安装向导，你就已经拥有了最新版本的SDK。</p>
    <h3>安装新的SDK</h3>
    <p>了解如何安装其它版本的SDK，对于你开发支持全部版本Android的app是非常有用的。</p>
    <p>SDK允许你根据个人的配置，创建<em>AVD</em>（Android虚拟设备）来测试你的app。</p>
    <p>在Android Studio的欢迎屏幕上，选择<em>Configure/SDK Manager</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager-545x500.png" alt="configure sdk manager" width="545" height="500" class="aligncenter size-large wp-image-161683" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager-545x500.png 545w, https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager-349x320.png 349w, https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager.png 1334w" sizes="(max-width: 545px) 100vw, 545px"></a></p>
    <p>启动之后，你会看到一个像下面这样的窗口：</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2-650x435.png" alt="Android Studio - SDK Platfors" width="650" height="435" class="aligncenter size-large wp-image-161692" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2-650x435.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2-478x320.png 478w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>SDK平台</h3>
    <p>该窗口的第一个tab<em>SDK Platforms</em>，列出了全部可供下载的Android SDK平台。</p>
    <p>打开<em>Show Package Details</em>选项可以展示各个SDK组件，例如其平台本身或和API级别相关的源，如系统映像。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1-650x381.png" alt="sdk platforms with details" width="650" height="381" class="aligncenter size-large wp-image-161695" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1-650x381.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1-480x281.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>注意SDK平台旁边的选框；如果有更新的话，它就会是可用的。</p>
    <p>默认情况下，SDK Manager会安装最新版本的包和工具。选择如上图所示的SDK。如果你希望安装其它的SDK，就选择它们安装即可。</p>
    <h3>SDK Tools</h3>
    <p><em>SDK Tools</em>这个tab列出了最新版本的开发者工具和文档。类似于第一个tab，点击<em>Show Package Details</em>可以展示可用的SDK工具的版本。</p>
    <p>例如，这个列表中选择的三个组件是<em>Android SDK Build-Tools</em>，<em>Android SDK Tools</em>和<em>Android SDK Platform-Tools</em>。每个包含的组件旨在协助Android的开发及跨多个SDK进行工作。使用此tab上的默认选择。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools-650x378.png" alt="sdk tools" width="650" height="378" class="aligncenter size-large wp-image-161700" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools-650x378.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools-480x279.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>SDK Update Sites</h3>
    <p><em>SDK Update Sites</em>tab展示了Android SDK工具和插件的更新地址。你并不限制于在这个tab下列出的地址。你还可以添加托管自己Android SDK插件的其它网站，然后从这些网站中进行下载。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites-650x378.png" alt="sdk update sites" width="650" height="378" class="aligncenter size-large wp-image-161704" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites-650x378.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites-480x279.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>为了正确地进行设置，请选择上面截图中的选项。点击屏幕底部的<em>Apply</em>。你会看到一个确认选择的包的对话框，接受并继续。点击<em>OK</em>来关闭窗口。</p>
    <p>确认对话框关闭后，会弹出一个许可协议。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement-594x500.png" alt="Beginning Android development - Android Studio license agreement" width="594" height="500" class="aligncenter size-large wp-image-161716" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement-594x500.png 594w, https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement-380x320.png 380w, https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement.png 1596w" sizes="(max-width: 594px) 100vw, 594px"></a></p>
    <p>阅读后，选择<em>Accept</em>并点击<em>Next</em>。SDK管理器就会下载并安装这些项目。完成之后，点击<em>Finish</em>。你就会返回到SDK管理器窗口。然后点击<em>OK</em>就会将你带回到<em>Welcome to Android Studio</em>页。</p>
    <p>现在就是有趣的事将要开始的地方了！</p>
    <h2>创建你的第一个项目</h2>
    <p>Android Studio有一个小工具可以帮助你一步一步来创建项目。在<em>Welcome to Android Studio</em>页中点击<em>Start a new Android Studio Project</em>：
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project-650x449.png" alt="Beginning Android development - Start new project" width="650" height="449" class="aligncenter size-large wp-image-161718" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project-650x449.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project-463x320.png 463w, https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project.png 1326w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <div class="note">
        <p><em>注意</em>：如果你当前已打开了一个Android Studio的项目，因而无法看到欢迎页。可以从菜单栏中选择<em>File/New Project</em>来创建新的项目。</p>
    </div>
    <h3>标识你的Project</h3>
    <p>Android Studio会弹出一个项目创建页：</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1-650x442.png" alt="configure project" width="650" height="442" class="aligncenter size-large wp-image-161721" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1-650x442.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1-471x320.png 471w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>像上面这样在<em>Application name</em>中输入<em>OMG Android</em>。并在<em>Company domain</em>文本框中输入你自己的名称。在你输入的过程中，你会注意到<em>Package name</em>自动地发生变化生成一个逆向风格的域名。</p>
    <p><em>Package name</em>用来唯一地标识你的app，以便在一台设备上的任何工作都能找到合适的源，避免app之间的冲突。</p>
    <p>你可以将<em>Project location</em>设置为硬盘上的任一位置 - 如果你没有特定偏好的话，保持默认即可。点击窗口底部的<em>Next</em>按钮。</p>
    <h3>选择SDK</h3>
    <p>接下来的一页是<em>Target Android Devices</em>窗口。这里是你选择设备类型的操作系统的地方。</p>
    <p><em>Minimum SDK</em>这个下拉菜单设置了运行你的app所要求的Android的最低版本。这个SDk越新，你就可以使用更多的特性；然而，这个SDk越新的话，就只能支持越少的设备。</p>
    <p>选择这个值是一个在你想要的功能和你想要支持的设备之间进行平衡的问题。这是开发Android的一个比较tricky的地方。</p>
    <p>如果想要了解，你的App选择什么最低版本的SDK最合适，Android Studio可以帮助你。</p>
    <p>随着你在下拉菜单中改变最低支持的SDK，在下面文本中就会反映运行这个Android版本所占的百分比。</p>
    <p>想要了解更多关于每个版本SDK中的特性，可以点击下拉菜单下方的<em>Help me choose</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution-650x441.png" alt="API Version Distribution" width="650" height="441" class="aligncenter size-large wp-image-161754" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution-650x441.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution-472x320.png 472w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>关于更多API版本统计的信息，可以访问定期更新的<a href="https://developer.android.com/about/dashboards/index.html" target="_blank" title="Android Dashboards" sl-processed="1">Android Dashboards</a>。</p>
    <p>现在，你只是想要一个运行在Android手机上的App，它将会是你在默认的<em>Minimum SDK</em>下，默认看到的内容。对于本项目，请选择<em>API 16: Android 4.1 (Jelly Bean)</em>并点击<em>Next</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices-650x440.png" alt="target android devices" width="650" height="440" class="aligncenter size-large wp-image-161755" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices-650x440.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices-472x320.png 472w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>设置默认的Activity</h3>
    <p>下面的一步是选择你默认的<a href="https://developer.android.com/reference/android/app/Activity.html" target="_blank" sl-processed="1">Activity</a>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity-650x442.png" alt="Beginning Android development - Add activity" width="650" height="442" class="aligncenter size-large wp-image-161756" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity-650x442.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity-470x320.png 470w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>可以把Activity看作一个你app中展示内容，且用户可以进行交互的窗口。Activity可以占据全部的屏幕，也可以只是一个简单的弹窗窗口。</p>
    <p>
        这个特定模板的选项范围，从一个基本的Activity开始，也就是一个带有<em>Action Bar</em>和<em>Floating Button</em>的黑色屏幕，直到一个嵌入了<em>MapView</em>的Activity。 
    </p>
    <p>随着你开发更多的app，你会创建更多的activity，因此必须进行很好的掌握。</p>
    <p>选择<em>Basic Activity</em>并点击<em>Next</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity-650x442.png" alt="Beginning Android development - Customize activity" width="650" height="442" class="aligncenter size-large wp-image-161758" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity-650x442.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity-471x320.png 471w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>为了加速完成这一部分的内容，你可以使用默认预填充的值，但这些值实际上做了什么？</p>
    <ul>
        <li><em>Activity Name</em>：为你的Activity起了一个名字，以便在代码中进行引用。系统将使用这个名称创建一个<code>.java</code>的类，它将最终成为你代码中用来引用此Activity的名称。</li>
        <li><em>Layout Name</em>：你要用Java来定义你的Activity，但展示给用户的布局是一个特别的<a href="https://developer.android.com/guide/topics/ui/overview.html" target="_blank" title="Android XML" sl-processed="1">Android XML</a>文件。你很快就会学习如何阅读和编辑这些文件。</li>
    </ul>
    <p>点击<em>Finish</em>。</p>
    <h3>运行项目</h3>
    <p>Android Studio在背后执行了一系列的操作，并创建你的项目。当Android Studio展示当前正在做什么的描述时，你可能会注意到如下的信息：</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/project-building.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/project-building-650x156.png" alt="project building" width="650" height="156" class="aligncenter size-large wp-image-161759" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/project-building-650x156.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/project-building-480x115.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/project-building.png 936w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>你发现了你熟悉的项目名称，但后面还有一个单词<em>Gradle</em>。</p>
    <p>有一个像Android Studio这样的现代IDE，好处就是它可以帮助你处理很多的事情。但是，当你学习如何使用该软件时，大致地了解一下它为你做了些<i>什么</i>会更加得好。</p>
    <h3>Gradle</h3>
    <p><a href="https://gradle.org/" target="_blank" title="Gradle" sl-processed="1">Gradle</a>是一个很容易使用的build工具，如果你进行更进一步的了解，就会发现它包含很多高级的选项。它会用你的Java代码，XML布局文件和最新的Android build工具构建成app的包文件，也就是被称为<em>APK</em>（Android Package Kit）的文件。</p>
    <p>你可以定制你自己的配置，来让开发和生产版本的表现有所不同。你也可以添加对第三方库的依赖。</p>
    <p>过了一会，Android Studio会完成构建你的项目。当然，当前的项目完全是空的，但它已经拥有了运行在Android设备或模拟器上所需的一切条件。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen-650x376.png" alt="android studio screen" width="650" height="376" class="aligncenter size-large wp-image-161820" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen-650x376.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen-480x277.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>简要地查看一下项目的各个部分吧。</p>
    <ul>
        <li>
            <em>manifests/AndroidManifest.xml</em>文件提供了运行你的app所需的Android系统的重要信息。
        </li>
        <li>
            <em>res</em>是你的资源目录。App诸如图片，xml布局，风格，颜色等资源文件，均被定义在这个目录中。
        </li>
        <li>
            你的所有UI都会被设计到<em>res/layout</em>目录下。你会使用Android XML来设计你的UI。
        </li>
        <li>
            <em>res/menu</em>是你定义app菜单内容的地方。
        </li>
        <li>
            <em>res/values</em>目录是你定义诸如位置尺寸（<em>res/values/dimens.xml</em>），颜色（<em>res/values/colors.xml</em>），字符串（<em>res/values/strings.xml</em>）等资源的地方。
        </li>
    </ul>
    <p>打开<em>res/layout/activity_main.xml</em>并点击屏幕底部的<em>Text</em>。</p>
    <p>这时就会展示出你main layout的xml代码。还会在屏幕的右边展示出它在设备上的预览图。</p>
    <div class="note">
        <p><em>注意</em>：如果默认没有打开预览图，你可以通过在菜单栏中选择<em>View/Tool Windows/Preview</em>来打开它。</p>
        <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1-437x500.png" alt="tool windows preview" width="437" height="500" class="aligncenter size-large wp-image-161923" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1-437x500.png 437w, https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1-280x320.png 280w, https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1.png 878w" sizes="(max-width: 437px) 100vw, 437px"></a>
        </p>
    </div>
    <h2>在模拟器上运行</h2>
    <p>你已经获得了Android Studio并创建了一个app。如何来运行它？</p>
    <p>Android Studio可以在计算机上模拟一个基于软件的Android设备，并在它的上面进行运行app，浏览网址，debug等一切你想做到的事情。这个功能就被称作<a href="https://developer.android.com/studio/run/emulator.html" target="_blank" title="Android Emulator" sl-processed="1">Android模拟器</a>。</p>
    <p>你可以配置多个模拟器，并为每个模拟器设置屏幕的尺寸和平台的版本。由于设备是如此得多，你可能需要一整个房间来进行储存 - ok，可能有一点夸张，但你会有这样的想法。:]</p>
    <p>如果你之前是通过标准的安装过程完成了设置向导，现在就已经有一个模拟器准备好了。</p>
    <p>目前为止，你的计算机不得不模拟你在Android设备上执行的所有事，直到使用基于ARM的硬件前为止。大多数的计算机使用的都是基于x86的处理器，这就意味着你的计算机不得不将每条指令翻译成基于ARM处理器可以理解的，这样就会占用不少的时间。为了降低这个开销，Android Studio最近采取了HAXM驱动，它可以加速这个过程。</p>
    <p>你仍然可以创建尽可能接近于实际设备的模拟器，但注意初始化加载的时间可能会久一些，这使得很多Android的开发者不愿使用模拟器。</p>
    <p>说了这么多之后...无论如何让我们来配置一个模拟器，因为你需要知道如何去做！</p>
    <h3>创建模拟器</h3>
    <p>点击<em>AVD Manager</em>。它是靠近工具栏右边的一个紫色的按钮，上面还有一个Android的小小的头像：</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-650x236.png" alt="avd manager" width="650" height="236" class="aligncenter size-large wp-image-162281" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-650x236.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-480x174.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager.png 1180w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>AVD Manager会打开一个页面，上面带有一个创新新设备的选项：:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2-650x327.png" alt="avd manager 2" width="650" height="327" class="aligncenter size-large wp-image-162282" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2-650x327.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2-480x242.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>Virtual Device</h3>
    <p>点击<em>Create Virtual Device…</em>按钮就可以去开始创建一个新的虚拟设备了。</p>
    <p>第一步是选择设备的类型。在左侧的<em>Category</em>中，展示了一个你能够模拟的（TV，Wear，Phone，Tablet）不同类型设备的列表。选中<em>Phone</em>这个选项。在这页的中部，有一个附带其屏幕尺寸的设备的列表，分辨率和像素密度。让我们花一点时间来探索吧。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware-640x500.png" alt="select hardware" width="640" height="500" class="aligncenter size-large wp-image-162444" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware-640x500.png 640w, https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware-410x320.png 410w" sizes="(max-width: 640px) 100vw, 640px"></a></p>
    <p>你现在需要的只是模拟手机大小的设备，但如果想要模拟Android Wear手表或Android TV的话，你也可以在这里选择。</p>
    <p>从phone的category，设备列表中选择对你可用的<em>Pixel</em>，并点击<em>Next</em>。</p>
    <h2>选择Android版本</h2>
    <p>在下一页中，你要选择Android设备将要运行的Android系统的版本。</p>
    <p>在本教程中，选择<em>Nougat</em>，并确保选中的值在<em>ABI</em>这列中的值为<em>x86</em>，这种模拟器就可以在你的x86计算机上尽可能地运行。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2-642x500.png" alt="system_image_2" width="642" height="500" class="aligncenter size-large wp-image-162428" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2-642x500.png 642w, https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2-411x320.png 411w" sizes="(max-width: 642px) 100vw, 642px"></a></p>
    <div class="note">
        <p><em>注意</em>：如果这个版本还未下载，请点击旁边的下载链接，待下载完成之后再继续后续的工作。</p>
    </div>
    <p>完成本页的配置后，点击<em>Next</em>前进到最后一页。</p>
    <h2>验证虚拟设备</h2>
    <p>最后一页用来确认你的选择，并给出了一些配置其它属性的选项，诸如设备名称和启动时的方向等。点击<em>Show Advanced Settings</em>按钮，还可以展示更多诸如相机、网络和内存的设置等的额外配置。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-confirm_pixel-1.gif" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-confirm_pixel-1.gif" alt="avd_confirm_pixel" width="642" height="500" class="aligncenter size-large wp-image-162443"></a></p>
    <p>使用默认的选项并点击<em>Finish</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel-642x500.png" alt="verify configuration pixel" width="642" height="500" class="aligncenter size-large wp-image-162447" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel-642x500.png 642w, https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel-411x320.png 411w" sizes="(max-width: 642px) 100vw, 642px"></a></p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel-650x327.png" alt="avd list" width="650" height="327" class="aligncenter size-large wp-image-162448" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel-650x327.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel-480x242.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>关闭AVD Manager并返回到Android Studio的主视图中。现在你已完成了所有的配置，点击<em>Run</em>按钮。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png" alt="run app" width="650" height="180" class="aligncenter size-large wp-image-162437" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-480x133.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png 1296w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>选择一个Device</h3>
    <p>这时会弹出一个新的窗口，要求你选择测试App所使用的设备。当前你还没有任何运行的设备，因此选择刚刚创建的Pixel并点击<em>OK</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel-650x376.png" alt="select deployment target" width="650" height="376" class="aligncenter size-large wp-image-162449" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel-650x376.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel-480x278.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <div class="note">
        <p><em>注意</em>：如果你遇到了一个错误<i>This AVD’s configuration is missing a kernel file!!</i>，请检查先前安装的Android SDK是否包含ANDROID_SDK_ROOT环境变量。可以在Stack Overflow查看<a href="http://stackoverflow.com/questions/9712605/emulator-error-this-avds-configuration-is-missing-a-kernel-file/10775330#10775330" sl-processed="1">此问题</a>的相关探讨。</p>
    </div>
    <p>不要担心，第一次不能正常地工作，或花费几分钟让模拟器正确地启动起来，都并非是意料之外。坚持下去，完成之后，你会看到如下的界面：</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2-315x500.png" alt="mobile app 2" width="315" height="500" class="aligncenter size-large wp-image-162456" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2-315x500.png 315w, https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2-202x320.png 202w, https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2.png 800w" sizes="(max-width: 315px) 100vw, 315px"></a></p>
    <p>哇。你刚刚已制作了你的第一个Android app。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-6.44.38-PM.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-6.44.38-PM.png" alt="So you're an Android developer now?" width="338" height="230" class="aligncenter size-full wp-image-122394"></a></p>
    <h3>模拟器工具栏</h3>
    <p>正如你所注意到的，模拟器的右边有一个面板。它就是模拟器的工具栏。你可以使用它执行各种<a href="https://developer.android.com/studio/run/emulator.html#tasks" target="_blank" sl-processed="1">任务</a>，诸如截图，屏幕旋转，音量控制和执行扩展的功能如模拟设备定位，来电，信息发送，指纹等等。</p>
    <p>要访问<a href="https://developer.android.com/studio/run/emulator.html#extended" target="_blank" sl-processed="1">扩展</a>的功能，请点击屏幕底部的更多（<em>…</em>）图标。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls-650x338.png" alt="extended controls" width="650" height="338" class="aligncenter size-large wp-image-162457" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls-650x338.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls-480x250.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h2>在设备上运行</h2>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/androiddevoptions.gif" sl-processed="1"><img class="alignright size-full wp-image-120237" src="https://koenig-media.raywenderlich.com/uploads/2015/11/androiddevoptions.gif" alt="androiddevoptions" width="259" height="463"></a></p>
    <p>如果你拥有Android的设备，并且你想要在上面运行你的app，请跟随上面的GIF动画。它演示了如何在你的设备上打开开发者模式。</p>
    <p>以下是在Android设备上打开<em>开发者模式</em>的分步骤介绍：</p>
    <ol>
        <li>打开你设备中的<em>Settings</em>。</li>
        <li>向下滚动，找到并选择<em>About phone</em>。</li>
        <li>滚动找到<em>Build number</em>并点击多次。你会看到一个toast提示到“You’re <i>n</i> steps away from becoming a developer”。继续点击，并当提示语改变为“You’re now a developer!”后，开发者模式就打开了。</li>
        <li>找到<em>Settings</em>页并滚动到页面底部。你现在会看到<em>Developer Options</em>已处于打开状态了。</li>
        <li>选择<em>Developer Options</em>。接下来，在<em>Debugging</em>部分中打开<em>USB debugging</em>开关。
        </li>
        <li>通过USB把你的设备连接到计算机上。</li>
        <li>你的手机会弹出一个对话框<em>Allow USB debugging?</em>来提示你确认这个选项 - 点击<em>OK</em>。</li>
        <li>接下来，你的手机会要求你注册计算机的RSA秘钥指纹。如果这是受信任的机器，请点击<em>Always allow from this computer</em>选项。</li>
    </ol>
    <p>现在你的设备已配置完毕，点击<em>Run</em>按钮。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png" alt="run app" width="650" height="180" class="aligncenter size-large wp-image-162437" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-480x133.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png 1296w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>就像之前一样，这里会弹出<em>Select Deployment Target</em>的对话框。你的设备现在应当出现在这个对话框中了。选择它并点击<em>OK</em>。</p>
    <p>嗯...在你的设备上看到自己的app是不件很有价值的事？把它向你的朋友们展示一下吧。:]</p>
    <div class="note">
        <p><em>注意</em>：如果你的app早已在运行，可能你就不会得到提示。这是因为Android Studio上有一个新的被称作<em>Instant Run</em>的功能。我们将在本教程的下一部分中进行讨论。关闭模拟器，再次点击<em>Run</em>按钮。</p>
    </div>
    <h2>Instant Run</h2>
    <p>Android Studio 2.0引入了被称作<em>Instant Run</em>的特性。Instant Run使得你可以将更新（代码和资源）推送到真机或是模拟器正在运行的app上，无需进行重新安装。这样，你就可以在较短的时间内看到你的更改了。</p>
    <p>你可以对代码进行三种方式的改变：a hot swap，warm swap，和cold swap。Instant Run会根据你所做的改变，通过下列的方式之一来推送更新：</p>
    <ol>
        <li><em>Hot Swap</em>：应用于方法的改变。应用于方法的改变。你的app会使用存根的方法继续运行，直到下次调用相关的方法时再进行更改。这是最快的交换。</li>
        <li><em>Warm Swap</em>：应用于资源的改变。他从重启你当期的activity以更新资源。</li>
        <li><em>Cold Swap</em>：即使没有执行重新安装，Instant run也会重启整个app。这主要用于结构性的代码更改</li>
    </ol>
    <h3>测试Instant Run</h3>
    <p>继续尝试Instant Run。</p>
    <p>点击<em>Android Studio/Preferences/Build, Execution, Deployment/Instant Run</em>以打开Instant Run。确定勾选了 <em>Enable Instant Run to hot swap code/resource changes on deploy</em>且不勾选<em>Restart activity on code changes</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-650x379.png" alt="" width="650" height="379" class="aligncenter size-large wp-image-162460" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-650x379.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-480x280.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>如果你的app还未运行，请点击<em>Run</em>按钮并等待它运行。</p>
    <p>当app运行起来后，右侧的<em>Apply Changes</em>按钮就会处于可用状态。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM-650x168.png" alt="" width="650" height="168" class="aligncenter size-large wp-image-162464" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM-650x168.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM-480x124.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM.png 1296w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>在你的app运行的时候，点击浮动的按钮，展示消息，在屏幕的底部<em>替换你自己的动作</em>。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1-281x500.png" alt="" width="281" height="500" class="aligncenter size-large wp-image-162465" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1.png 1080w" sizes="(max-width: 281px) 100vw, 281px"></a></p>
    <p>改变消息来测试Instant Run。</p>
    <p>打开<em>MainActivity</em>，在<em>onCreate()</em>方法中，将文本：<em>Replace with your own action</em>替换为：<em>Hello Instant Run</em>。</p>
    <p>然后点击<em>Apply Changes</em>。现在当你点击按钮的时候，就会看到新的消息。这就是一个hot swap的例子。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374-281x500.png" alt="" width="281" height="500" class="aligncenter size-large wp-image-162467" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374.png 1080w" sizes="(max-width: 281px) 100vw, 281px"></a></p>
    <p>Instant Run可以通过减少更新你代码和资源变化所需的时间，来帮助你快速地coding。</p>
    <h2>导入已存在的项目</h2>
    <p>在你开发Android的过程中，你会经常需要导入已存在的项目。以下是导入一个项目的具体步骤：</p>
    <ol>
        <li>下载 <a href="https://developer.android.com/downloads/samples/CardView.zip" title="this" sl-processed="1">这个项目</a>作为你的测试对象。</li>
        <li>下载完毕后，解压其内容，并将它存放到一个容易获取的地方。</li>
        <li>在Android Studio中，点击<em>File/New/Import Project…</em>。</li>
        <li>弹出了一个被标记为<em>Select Eclipse or Gradle Project to Import</em>的窗口。选择在第一步中解压出的项目并点击<em>OK</em>。</li>
        <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM.png" sl-processed="1"><img class="aligncenter size-large wp-image-120323" src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM-469x500.png" alt="Screen Shot 2015-11-09 at 2.42.57 PM" width="469" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM-469x500.png 469w https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM-300x320.png 300w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM.png 1176w" sizes="(max-width: 469px) 100vw, 469px"></a></p>
        <li>完成导入之后，你会看到如下面图片中的样子。选择左侧面板中的<em>Project</em>tab，就像下面截图中所示的一样。</li>
        <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM.png" sl-processed="1"><img class="aligncenter size-large wp-image-120324" src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM-581x500.png" alt="Screen Shot 2015-11-09 at 2.43.30 PM" width="581" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM-581x500.png 581w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM-372x320.png 372w" sizes="(max-width: 581px) 100vw, 581px"></a></p>
        <li>现在你就可以在项目浏览器中看到刚导入项目中所有的文件了。</li>
    </ol>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer-700x500.png" alt="import_explorer" width="700" height="500" class="aligncenter size-large wp-image-121000" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer-700x500.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer-448x320.png 448w" sizes="(max-width:700px) 100vw, 700px"></a></p>
    <p>运行项目吧！点击工具栏中的<em>Run</em>按钮，并选择你之前设置好的一个设备或模拟器即可。</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run-299x500.png" alt="card_view_run" width="299" height="500" class="aligncenter size-large wp-image-121001" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run-299x500.png 299w, https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run-192x320.png 192w, https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run.png 722w" sizes="(max-width: 299px) 100vw, 299px"></a></p>
    <h2>从这儿去向哪里？</h2>
    <div class="inline-video-ad" id="sub-banner-inline">
        <div class="inline-video-ad-wrapper">
            <a href="https://videos.raywenderlich.com/courses" sl-processed="1">
                <div class="col-wrapper">
                    <div class="col">
                        <img src="https://koenig-assets.raywenderlich.com/wp-content/themes/raywenderlich/images/global/video-yeti@2x.png">
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
    <p>你已在这篇教程中学到了很多基础的内容：从下载和安装Android Studio，到创建你的第一个“Hello World!” app，再到将它不熟到一个屋里的设备上！</p>
    <p>继续阅读本系列的<a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Beginning%20Android%20Development%20Part%20Two%20Using%20Android%20Studio.md" sl-processed="1">下一部分</a>，你将从中开启一段Android Studio的旅程。</p>
    <p>在此期间，就像其它的语言或框架一样，Android的开发者社区拥有大量优秀的资源和参考文档。记住，任何时候访问Google的<a href="https://events.google.com/io/" target="_blank" title="Google I/O" sl-processed="1">I/O conference</a>，<a href="http://android-developers.blogspot.com/" target="_blank" title="Android Developers blog" sl-processed="1">Android Developers blog</a>或<a href="https://www.youtube.com/user/androiddevelopers" target="_blank" title="Android Developer videos" sl-processed="1">Android Developer videos</a>都不会太晚。</p>
</div>