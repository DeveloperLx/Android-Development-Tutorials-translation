# 开始Android开发教程第一部分：安装Android Studio
---
#### [原文地址](https://www.raywenderlich.com/161318/beginning-android-development-part-one-installing-android-studio) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p><em>Update Note</em>: This Beginning android development is now up to date with the latest version of Android Studio.
            Update by Eunice Obugyei. <a href="http://www.raywenderlich.com/56107/make-first-android-app-part-1" target="_blank"
                title="Original tutorial" sl-processed="1">Original tutorial</a> by Matt Luedke. Previous updates by Darryl Bayliss
            and Megha Bambra.</p>
    </div>
    <p><img src="https://koenig-media.raywenderlich.com/uploads/2017/06/AndroidStudio-feature-1.png" alt="AndroidRW" width="250"
            height="250" class="alignright size-full wp-image-87100"></p>
    <p>Clearly there’s a demand for Android app development since there are over <i>two billion</i> monthly active users around
        the globe. To say that it’s an exciting platform and space to make apps for is an understatement.</p>
    <h2>Beginning Android Development</h2>
    <p>There aren’t any prerequisites for this tutorial, other than a willing mind and a Mac — you can certainly develop for
        Android on PC, but these instructions are tooled for Mac-based developers. </p>
    <p>You’ll learn how to set up all the tools needed to start you on your way to becoming an Android developer. Here’s what
        you’ll do in this beginning Android development tutorial:</p>
    <ol>
        <li>Download and install Android Studio.</li>
        <li>Set up testing for your app on devices and emulators.</li>
        <li>Create a simple “Hello World!” Android app that prints to your device’s or emulator’s screen.</li>
        <li>Import a sample project into Android Studio.</li>
    </ol>
    <h2>Installing Android Studio</h2>
    <p>One of the most important parts of getting started with any new platform is setting up your environment, and this is
        no different with Android.</p>
    <p>It’s important to take your time and follow each step methodically. Even if you follow the steps perfectly, you may have
        to troubleshoot a small issue or few. Your system configuration or product versions can make for unexpected results.</p>
    <h2>Installing Java</h2>
    <p>With all of this in mind, let’s quickly check that you have the Java Development Kit (JDK) installed. To check, you’ll
        use trusty old <em>Terminal</em>. </p>
    <div class="note">
        <p><em>Note</em>: You’ll learn the essential steps for this tutorial in the next few paragraphs, but if you’d like to
            deepen your knowledge of the Terminal, you’ll find a good introductory tutorial about it in this blog from
            <a href="http://blog.teamtreehouse.com/introduction-to-the-mac-os-x-command-line" target="_blank" title=" teamtreehouse.com "
                sl-processed="1">teamtreehouse.com</a>.</p>
    </div>
    <h3>The Terminal</h3>
    <p>In a nutshell, using Terminal is kind of like looking under your car’s hood. It’s how you really get to know the machine
        face-to-face, without any complex graphical interface to interfere.</p>
    <p>You can find the Terminal app quite easily on a Mac: open Launchpad and type <em>terminal</em> into the search at the
        top of the screen and select Terminal when it shows up. </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal-480x207.png" alt="Find Terminal in Launchpad" width="480" height="207" class="aligncenter size-medium wp-image-161322" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal-480x207.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal-650x280.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/launchpad-terminal.png 1004w" sizes="(max-width: 480px) 100vw, 480px"></a></p>
    <p>Once you have Terminal open, type in <code>java -version</code>. You should see some output that mentions a version number,
        like below.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version-480x124.png" alt="Beginning Android development - Check Java version" width="480" height="124" class="aligncenter size-medium wp-image-161328" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version-480x124.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version-650x167.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/terminal-java-version.png 1142w" sizes="(max-width: 480px) 100vw, 480px"></a></p>
    <p>If that’s not what you see, then you don’t have the JDK installed. Terminal might tell you <code>-bash: java: command not found</code>,
        or it could say <code>No Java runtime present, requesting install.</code> and trigger a pop up that will lead you
        down the yellow brick road…to Oracle’s website.<br>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-3.13.48-PM-e1449423724199.png"
            sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-3.13.48-PM-e1449423724199.png" alt="Beginning Android development - Install Java" width="413" height="155" class="aligncenter size-full wp-image-122395"></a></p>
    <p>You can either click <em>More Info…</em> or head over to Oracle to <a href=" http://www.oracle.com/technetwork/java/javase/downloads/index.html"
            target="_blank" sl-processed="1">download the JDK</a> from Oracle.</p>
    <p>Install the JDK if needed, and once you’re done, head over to the <a href="https://developer.android.com/sdk/installing/studio.html"
            target="_blank" title="Android Studio page" sl-processed="1">Android Studio page</a> and click the <em>Download Android Studio</em>        button.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page-650x394.png" alt="Download Android Studio" width="650" height="394" class="aligncenter size-large wp-image-161331" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page-650x394.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-download-page-480x291.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h2>Getting Android Studio</h2>
    <p>Google constantly updates this page, so the version you see may very well be newer than the screenshot above. Once you
        click the <em>Download Android Studio</em> button, you’ll see a request to agree to the terms and conditions.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions-650x427.png" alt="android-studio-terms-conditions" width="650" height="427" class="aligncenter size-large wp-image-161334" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions-650x427.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-terms-conditions-480x315.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>After reading these carefully (everybody takes the time to fully read these, right?) accept and click the blue button
        underneath titled <em>Download Android Studio For Mac</em>. Once the download is complete, you can install Android
        Studio just like how you install any other program.</p>
    <p>The download link will redirect to a page that contains installation instructions for OS X, Windows and Linux Operating
        Systems. If the instructions don’t appear, then you can view them <a href="https://developer.android.com/studio/install.html"
            target="_blank" title="here" sl-processed="1">here</a>.</p>
    <p>Once installation wraps itself up, go ahead and launch <em>Android Studio</em>!</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2014/12/3.-Android-Studio-Loading.png" sl-processed="1"><img class="aligncenter size-medium wp-image-56524" src="https://koenig-media.raywenderlich.com/uploads/2014/12/3.-Android-Studio-Loading.png" alt="opening_studio_3" width="313" height="240"></a></p>
    <h2>Setting up Android Studio</h2>
    <p>The setup wizard will greet you the first time it loads.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM.png" sl-processed="1"><img class="aligncenter size-medium wp-image-120269" src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM-426x320.png" alt="Screen Shot 2015-11-08 at 8.08.50 PM" width="426" height="320" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM-426x320.png 426w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM-666x500.png 666w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.08.50-PM.png 1598w" sizes="(max-width: 426px) 100vw, 426px"></a></p>
    <p>Click <em>Next</em> to move to the <em>Install Type</em> screen. This whole process will probably take several minutes.
    </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM.png" sl-processed="1"><img class="aligncenter size-large wp-image-120356" src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM-664x500.png" alt="Screen Shot 2015-11-08 at 8.09.21 PM" width="664" height="500" srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM-664x500.png 664w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM-425x320.png 425w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-08-at-8.09.21-PM.png 1598w" sizes="(max-width: 664px) 100vw, 664px"></a></p>
    <p>Check the box for <em>Standard</em> and click <em>Next</em>. </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings-650x487.png" alt="verify settings" width="650" height="487" class="aligncenter size-large wp-image-161668" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings-650x487.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/verify-settings-427x320.png 427w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>On the <em>Verify Settings</em> window, you’ll have an opportunity to confirm your setup. Click <em>Finish</em> to start
        downloading the SDK components. </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components-650x489.png" alt="downloading components" width="650" height="489" class="aligncenter size-large wp-image-161670" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components-650x489.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/downloading-components-426x320.png 426w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>When the download is complete, click <em>Finish</em>.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete-650x490.png" alt="component download complete" width="650" height="490" class="aligncenter size-large wp-image-161671" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete-650x490.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/component-download-complete-424x320.png 424w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>Android Studio Welcome Screen</h3>
    <p>After a few minutes, you’ll have the welcome screen, which serves as your gateway to building all things Android.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen-650x450.png" alt="welcome screen" width="650" height="450" class="aligncenter size-large wp-image-161672" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen-650x450.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen-462x320.png 462w, https://koenig-media.raywenderlich.com/uploads/2017/05/welcome-screen.png 1334w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Even though you just downloaded Android Studio, it’s possible that it’s not the latest version. Select <em>Configure/Check for Update</em>        at the bottom of the welcome screen to check whether any updates are available.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1-543x500.png" alt="check for updates" width="543" height="500" class="aligncenter size-large wp-image-161677" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1-543x500.png 543w, https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1-348x320.png 348w, https://koenig-media.raywenderlich.com/uploads/2017/05/check-for-updates-1.png 1334w" sizes="(max-width: 543px) 100vw, 543px"></a></p>
    <p>If an update is available, a window like the screenshot below will appear. Click the <em>Update and Restart</em> button
        and let it do its thing.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen-650x452.png" alt="update screen" width="650" height="452" class="aligncenter size-large wp-image-161678" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen-650x452.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen-460x320.png 460w, https://koenig-media.raywenderlich.com/uploads/2017/05/update-screen.png 1332w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h2>The Android SDK Manager</h2>
    <p>Each version of Android has its own <em>SDK </em> (Software Development Kit) that enables you to create applications
        for the Android platform. Since you just went through the setup wizard, you’ll already have the latest version of
        the SDK available to you. </p>
    <h3>Installing a New SDK</h3>
    <p>It’s useful to know how to install additional versions of the SDK to help you develop for all supported versions of Android.</p>
    <p>SDKs allow you to create <em> AVDs </em> (Android Virtual Devices) according to your personal configuration for the purpose
        of testing your app.</p>
    <p>From the Android Studio welcome screen, select <em>Configure/SDK Manager</em>.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager-545x500.png" alt="configure sdk manager" width="545" height="500" class="aligncenter size-large wp-image-161683" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager-545x500.png 545w, https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager-349x320.png 349w, https://koenig-media.raywenderlich.com/uploads/2017/05/configure-sdk-manager.png 1334w" sizes="(max-width: 545px) 100vw, 545px"></a></p>
    <p>Once it launches, you’ll see a window like the one below:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2-650x435.png" alt="Android Studio - SDK Platfors" width="650" height="435" class="aligncenter size-large wp-image-161692" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2-650x435.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-2-478x320.png 478w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>SDK Platforms</h3>
    <p>The first tab of this window, <em>SDK Platforms</em>, lists the Android SDK platforms available for download. </p>
    <p>Enabling the <em>Show Package Details</em> option displays the individual SDK components, such as the platform itself
        and the sources pertaining to the API level like system image.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1-650x381.png" alt="sdk platforms with details" width="650" height="381" class="aligncenter size-large wp-image-161695" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1-650x381.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-platforms-expanded-1-480x281.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Take note of the checkbox next to the SDK platform; it will be pre-selected if an update is available.</p>
    <p>By default, the SDK Manager installs the latest packages and tools. Select the SDKs as shown in the screenshot above.
        If you wish to install other SDKs, just select them for installation.</p>
    <h3>SDK Tools</h3>
    <p>The <em>SDK Tools</em> tab lists developer tools and documentation along with the latest versions. Similar to the first
        tab, checking the <em>Show Package Details</em> will display available version of SDK tools. </p>
    <p>Three of the selected components in this list, for example, are <em>Android SDK Build-Tools</em>, <em>Android SDK Tools</em>        and <em>Android SDK Platform-Tools</em>. Each contains components that are designed to assist in the development
        of Android and work across multiple SDKs. Go with the default selection on this tab.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools-650x378.png" alt="sdk tools" width="650" height="378" class="aligncenter size-large wp-image-161700" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools-650x378.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-tools-480x279.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>SDK Update Sites</h3>
    <p>The <em>SDK Update Sites</em> tab displays the update sites for Android SDK tools and add-ons. You’re not limited to
        what’s listed under that tab. You can add other sites that host their own Android SDK add-ons, and then download
        them from those sites. </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites-650x378.png" alt="sdk update sites" width="650" height="378" class="aligncenter size-large wp-image-161704" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites-650x378.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/sdk-update-sites-480x279.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>For the purpose of setting up correctly, select the options that are checked in the screenshot above. Click <em>Apply</em>        at the bottom if it’s active. You’ll see a confirmation dialog for the chosen packages; accept and continue. Click
        <em>OK</em> to close the window.</p>
    <p>The confirmation dialog will disappear and a license agreement will popup. </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement-594x500.png" alt="Beginning Android development - Android Studio license agreement" width="594" height="500" class="aligncenter size-large wp-image-161716" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement-594x500.png 594w, https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement-380x320.png 380w, https://koenig-media.raywenderlich.com/uploads/2017/05/license-agreement.png 1596w" sizes="(max-width: 594px) 100vw, 594px"></a></p>
    <p>Read through it, select the <em>Accept</em> checkbox and click <em>Next</em>. The SDK Manager will download and install
        the selected items. Once it’s done, click <em>Finish</em>. You’ll be directed back to the SDK Manager window where
        clicking <em>OK</em> will take you back to the <em>Welcome to Android Studio</em> screen. </p>
    <p>This is where the fun begins!</p>
    <h2>Creating Your First Project</h2>
    <p>Android Studio has a nice little step-by-step tool to help you create your project. Click <em>Start a new Android Studio Project</em>        from the <em>Welcome to Android Studio</em> screen:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project-650x449.png" alt="Beginning Android development - Start new project" width="650" height="449" class="aligncenter size-large wp-image-161718" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project-650x449.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project-463x320.png 463w, https://koenig-media.raywenderlich.com/uploads/2017/05/start-new-project.png 1326w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <div class="note">
        <p><em>Note</em>: If you currently have an Android Studio project open and can’t see the welcome screen, select <em>File\New Project</em>            from the menu to create a new project.</p>
    </div>
    <h3>Identify Your Project</h3>
    <p>Android Studio will present you with a project creation screen:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1-650x442.png" alt="configure project" width="650" height="442" class="aligncenter size-large wp-image-161721" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1-650x442.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/new-project-1-471x320.png 471w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Enter <em>OMG Android</em> in <em>Application name</em> as shown above. Feel free to put your own name in the <em>Company domain</em>        text field. As you type, you’ll notice the <em>Package name</em> automatically changes to create a reverse domain
        style name per your entries.</p>
    <p>The <em>Package name</em> is used to uniquely identify your app so that any work done on a device is always properly
        attributed to the source, thus preventing confusion between apps.</p>
    <p>You can set the <em>Project location</em> to any location on your hard drive — keep the default if you don’t have a preference.
        Click <em>Next</em> at the bottom of the window.</p>
    <h3>Choose an SDK</h3>
    <p>The next screen is the <em>Target Android Devices</em> window. This is where you select device types and operating systems
        to target. </p>
    <p>The <em>Minimum SDK</em> drop-down menu sets the minimum version of Android requires to run your app. The newer the SDK,
        the more features you’ll have at your disposal; however, newer SDKs support fewer devices. </p>
    <p>Selecting this value is simply a matter of balancing the capabilities you want and the devices you want to support. This
        is where developing for Android can get a little tricky.</p>
    <p>If you really want to get into the details of what Minimum SDK version is best for your App, let Android Studio help
        you out. </p>
    <p>As you change the Minimum SDK in the drop down menu, the percentage in the text underneath reflects what percentage of
        devices currently run that version of Android. </p>
    <p>Click <em>Help me choose</em> underneath the drop down list to learn more about each SDK’s set of features.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution-650x441.png" alt="API Version Distribution" width="650" height="441" class="aligncenter size-large wp-image-161754" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution-650x441.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/API-Version-Distribution-472x320.png 472w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>For more on API versions statistics, check out the <a href="https://developer.android.com/about/dashboards/index.html"
            target="_blank" title="Android Dashboards" sl-processed="1">Android Dashboards</a>, which are updated periodically.</p>
    <p>For now, you just want an App that works on an Android Phone, and that is what you’ll see by default, alongside the default<em> Minimum SDK</em>.
        For this project, select SDK of <em>API 16: Android 4.1 (Jelly Bean)</em> and click <em>Next</em>.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices-650x440.png" alt="target android devices" width="650" height="440" class="aligncenter size-large wp-image-161755" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices-650x440.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/target-android-devices-472x320.png 472w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>Set the Default Activity</h3>
    <p>The next step is to select your default <a href="https://developer.android.com/reference/android/app/Activity.html" target="_blank"
            sl-processed="1">Activity</a>.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity-650x442.png" alt="Beginning Android development - Add activity" width="650" height="442" class="aligncenter size-large wp-image-161756" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity-650x442.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/add-activity-470x320.png 470w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Think of an Activity as a window within your app that displays content with which the user can interact. An Activity
        can take up the entire screen or it could be a simple pop-up.</p>
    <p>Your options on this particular template range from a Basic Activity, which is a blank screen with an <em>Action Bar</em>        and a <em>Floating Button</em> right up to an Activity with an embedded <em>MapView</em>. </p>
    <p>You’ll make a lot of activities as you develop more apps, so get to know them and know them well.</p>
    <p>Select the <em>Basic Activity</em> and click <em>Next</em>.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity-650x442.png" alt="Beginning Android development - Customize activity" width="650" height="442" class="aligncenter size-large wp-image-161758" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity-650x442.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/customize-activity-471x320.png 471w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>To speed this part up a little bit you’ll use the pre-populated default values, but what is actually done with these
        values?
    </p>
    <ul>
        <li><em>Activity Name</em>: This gives your Activity a name to refer to in code. A <code>.java</code> class will be created
            and will use the contents of this text field to give the class a name, which will ultimately be the name you
            use to refer to this Activity in your code.</li>
        <li><em>Layout Name</em>: You’re going to define your Activity in Java, but the layout it shows to the user is defined
            in a special sort of <a href="https://developer.android.com/guide/topics/ui/overview.html" target="_blank" title="Android XML"
                sl-processed="1">Android XML</a>. You’ll learn how to read and edit those files shortly.</li>
    </ul>
    <p>Click <em>Finish</em>. </p>
    <h3>Building the Project</h3>
    <p>Android Studio takes this as a cue to go do a bunch of behind-the-scenes operations and create your project. As it shoots
        out descriptions of what it’s doing, you may notice it says something like this:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/project-building.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/project-building-650x156.png" alt="project building" width="650" height="156" class="aligncenter size-large wp-image-161759" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/project-building-650x156.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/project-building-480x115.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/project-building.png 936w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Here, you see your project name, which is familiar. But then there is this <em>Gradle</em> word as well.</p>
    <p>The benefit of having a modern IDE like Android Studio is that it handles a lot for you. But, as you’re learning how
        to use the software, it’s good to have a general sense of <i>what</i> it does for you.</p>
    <h3>Gradle</h3>
    <p><a href="https://gradle.org/" target="_blank" title="Gradle" sl-processed="1">Gradle</a> is a build tool that’s easy
        to use, and if you investigate further, you’ll find it contains advanced options. It takes your Java code, XML layouts
        and the latest Android build tools to create the app package file, also known as an <em>APK</em> (Android Package
        Kit) file. </p>
    <p>You can customize your configurations to have development or production versions of the app that behave differently.
        You can also add dependencies for third-party libraries.</p>
    <p>After a brief moment, Android Studio will finish building your project. The project is pretty empty, of course, but it
        has everything it needs set up so that it can be launched on an Android device or emulator.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen-650x376.png" alt="android studio screen" width="650" height="376" class="aligncenter size-large wp-image-161820" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen-650x376.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/android-studio-screen-480x277.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Let’s take a brief look at the different parts of the project.</p>
    <ul>
        <li>
            The <em>manifests/AndroidManifest.xml</em> file provides to the Android system important information required
            to run your app.
        </li>
        <li>
            The <em>res</em> directory is your resource directory. Application resources such as images, xml layouts, styles,
            colors etc. are defined in this directory.
        </li>
        <li>
            The <em>res/layout</em> directory is where all your UI (User Interface) will be designed. You will use Android
            XML to design your UI.
        </li>
        <li>
            The <em>res/menu</em> directory is where you define the contents of your application’s menus.
        </li>
        <li>
            The <em>res/values</em> directory is where you define the resources such as dimensions (<em>res/values/dimens.xml</em>),
            colors (<em>res/values/colors.xml</em>), strings (<em>res/values/strings.xml</em>), etc.
        </li>
    </ul>
    <p>Open <em>res/layout/activity_main.xml</em> and click <em>Text</em> at the bottom of the screen.</p>
    <p>This shows you the xml code for your main layout. It also shows a preview of how it will look like on a device on the
        right side of the screen. </p>
    <div class="note">
        <p><em>Note</em>: If the Preview screen is not shown by default for you, open it by selecting <em>View\Tool Windows\Preview</em>            from the menu</p>
        <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1-437x500.png" alt="tool windows preview" width="437" height="500" class="aligncenter size-large wp-image-161923" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1-437x500.png 437w, https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1-280x320.png 280w, https://koenig-media.raywenderlich.com/uploads/2017/05/tool-windows-preview-1.png 878w" sizes="(max-width: 437px) 100vw, 437px"></a>
        </p>
    </div>
    <h2>Running on an Emulator</h2>
    <p>You’ve got Android Studio and you’ve created an app. So how do you run it?</p>
    <p>Android Studio comes with the ability to set up a software-based Android device on your computer and run apps on it,
        browse websites, debug and everything you would expect from a simulator. This capability is known as the <a href="https://developer.android.com/studio/run/emulator.html"
            target="_blank" title="Android Emulator" sl-processed="1">Android Emulator</a>.</p>
    <p>You can set up multiple emulators and set the screen size and platform version for each to whatever you like. Good thing,
        too. You’d need a whole room dedicated to storing devices for testing because there are so many out there — okay,
        maybe that’s an exaggeration, but you get the idea. :] </p>
    <p>If you ran through the setup wizard earlier using the standard installation, then you’ll already have an emulator set
        up and ready for you. </p>
    <p>Up until recently, your computer would have to emulate everything an Android device would try to do, right down to its
        hardware, which runs an ARM-based processor. Most computers make use of x86-based processors, meaning your computer
        has to translate each instruction to one that an ARM-based processor would understand and this takes a significant
        amount of time. To reduce this overhead, Android Studio has recently adopted the HAXM driver which is able to speed
        things up a bit.</p>
    <p>You still have the option to create an emulator that is as close to an actual device as you can, but be aware that the
        initial load times can drag a bit and have put off many an Android developer from using emulators at all.</p>
    <p>With all that being said…let’s set up an emulator anyway, because you do need to know how!</p>
    <h3>Creating an Emulator</h3>
    <p>Click the <em>AVD Manager</em>. It’s a button near the right side of the toolbar that shows an Android popping its head
        up next to a device with a purple display:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-650x236.png" alt="avd manager" width="650" height="236" class="aligncenter size-large wp-image-162281" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-650x236.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-480x174.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager.png 1180w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>The AVD Manager will open to a screen with an option to create a new device:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2-650x327.png" alt="avd manager 2" width="650" height="327" class="aligncenter size-large wp-image-162282" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2-650x327.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-manager-2-480x242.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>Virtual Device</h3>
    <p>Click the <em>Create Virtual Device…</em> button to start the process of creating a new virtual device. </p>
    <p>The first step is to select the type of device. The <em>Category</em> section, on the left side of the screen, shows
        a list of the different device types you can emulate(TV, Wear, Phone, Tablet). Make sure the <em>Phone</em> option
        is selected. In the middle of the screen, there is a list of specific devices with their screen size, resolution
        and density. Take a moment to explore them. </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware-640x500.png" alt="select hardware" width="640" height="500" class="aligncenter size-large wp-image-162444" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware-640x500.png 640w, https://koenig-media.raywenderlich.com/uploads/2017/05/select-hardware-410x320.png 410w" sizes="(max-width: 640px) 100vw, 640px"></a></p>
    <p>What you need now is just to emulate a phone-sized device, but if you wanted to emulate an Android Wear watch or an Android
        TV then you have options to do so here. </p>
    <p>Select <em>Pixel</em> in the list of devices available to you from the phone category and click <em>Next</em>.</p>
    <h2>Select Android Version</h2>
    <p>On the next screen, you have to select the version of Android the virtual device will run.</p>
    <p>For this tutorial, select <em>Nougat</em> and make sure the one selected has the value <em>x86</em> in the <em>ABI</em>        column so the emulator runs as fast as possible on your x86 computer.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2-642x500.png" alt="system_image_2" width="642" height="500" class="aligncenter size-large wp-image-162428" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2-642x500.png 642w, https://koenig-media.raywenderlich.com/uploads/2017/05/system_image_2-411x320.png 411w" sizes="(max-width: 642px) 100vw, 642px"></a></p>
    <div class="note">
        <p><em>Note</em>: If that version is not already downloaded, click on the Download link beside the release name to download
            before you continue.</p>
    </div>
    <p>Click <em>Next</em> once you’re done to advance to the final screen.</p>
    <h2>Verify Virtual Device</h2>
    <p>The last screen lets you confirm your choices and gives options to configure some other properties such as device name
        and startup orientation. Clicking the <em>Show Advanced Settings</em> button, shows you extra configurations you
        can change such as Camera, Network and Memory settings.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-confirm_pixel-1.gif" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-confirm_pixel-1.gif" alt="avd_confirm_pixel" width="642" height="500" class="aligncenter size-large wp-image-162443"></a></p>
    <p>Use the defaults and click <em>Finish</em>.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel-642x500.png" alt="verify configuration pixel" width="642" height="500" class="aligncenter size-large wp-image-162447" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel-642x500.png 642w, https://koenig-media.raywenderlich.com/uploads/2017/05/verify-configuration-pixel-411x320.png 411w" sizes="(max-width: 642px) 100vw, 642px"></a></p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel-650x327.png" alt="avd list" width="650" height="327" class="aligncenter size-large wp-image-162448" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel-650x327.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/avd-list-pixel-480x242.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Close the AVD Manager to go back to Android Studio’s main view. Now that you’ve configured everything, click the <em>Run</em>        button.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png" alt="run app" width="650" height="180" class="aligncenter size-large wp-image-162437" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-480x133.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png 1296w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h3>Selecting a Device</h3>
    <p>A new window will appear, asking you to choose the device you wish to test your App on. You currently have no devices
        running, so select the Pixel you just created and click <em>OK</em>. </p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel-650x376.png" alt="select deployment target" width="650" height="376" class="aligncenter size-large wp-image-162449" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel-650x376.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/select-deployment-target-pixel-480x278.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <div class="note">
        <p><em>Note</em>: If you get an error that says <i>This AVD’s configuration is missing a kernel file!!</i>, check to
            make sure that you don’t have the ANDROID_SDK_ROOT environment variable set from a previous installation of the
            Android SDK. See <a href="http://stackoverflow.com/questions/9712605/emulator-error-this-avds-configuration-is-missing-a-kernel-file/10775330#10775330"
                sl-processed="1">this thread</a> on Stack Overflow for more troubleshooting tips.</p>
    </div>
    <p>In the event that it doesn’t work the first time or takes several minutes for the emulator to fire up correctly, don’t
        worry, that’s not entirely unexpected. Stick with it. Once it’s ready, you should see something like this:</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2-315x500.png" alt="mobile app 2" width="315" height="500" class="aligncenter size-large wp-image-162456" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2-315x500.png 315w, https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2-202x320.png 202w, https://koenig-media.raywenderlich.com/uploads/2017/05/mobile-app-2.png 800w" sizes="(max-width: 315px) 100vw, 315px"></a></p>
    <p>Whoa. You just made your first Android app.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-6.44.38-PM.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2015/12/Screen-Shot-2015-12-05-at-6.44.38-PM.png" alt="So you're an Android developer now?" width="338" height="230" class="aligncenter size-full wp-image-122394"></a></p>
    <h3>The Emulator Toolbar</h3>
    <p>As you may have noticed, there’s a panel on the right side of the emulator. That is the emulator toolbar. The toolbar
        lets you perform various <a href="https://developer.android.com/studio/run/emulator.html#tasks" target="_blank" sl-processed="1">tasks</a>        such as Taking screenshots, Screen rotation, Volume control and perform extended functionalities such as simulating
        device location, phone calls, message sending, finger print etc. </p>
    <p>To access the <a href="https://developer.android.com/studio/run/emulator.html#extended" target="_blank" sl-processed="1">extended</a>        functionalities, click the More (<em>…</em>) icon at the bottom of the toolbar.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls-650x338.png" alt="extended controls" width="650" height="338" class="aligncenter size-large wp-image-162457" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls-650x338.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/extended-controls-480x250.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <h2>Running on a Device</h2>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/androiddevoptions.gif" sl-processed="1"><img class="alignright size-full wp-image-120237" src="https://koenig-media.raywenderlich.com/uploads/2015/11/androiddevoptions.gif" alt="androiddevoptions" width="259" height="463"></a></p>
    <p>If you have an Android device you want to run your app on, follow the animated GIF on the right. It demonstrates how
        to enable developer mode on your device.</p>
    <p>Here are the step-by-step instructions to enable <em>Developer Mode</em> on an Android device:</p>
    <ol>
        <li>Go to <em>Settings</em> on your device. </li>
        <li>Scroll all the way down and select <em>About phone.</em></li>
        <li>Scroll to <em>Build number</em> and tap in multiple times. You’ll see a toast come up that states “You’re <i>n</i>            steps away from becoming a developer”. Keep tapping and it will change to “You’re now a developer!” once it’s
            enabled. </li>
        <li>Go back to <em>Settings</em> screen and scroll all the way to the bottom. You’ll now see <em>Developer Options</em>            enabled. </li>
        <li>Select <em>Developer Options</em>. Next, turn on the <em>USB debugging</em> switch under the <em>Debugging</em> section.
        </li>
        <li>Connect your device to your computer via USB.</li>
        <li>Your phone will prompt you to confirm this option via a dialog that states <em>Allow USB debugging?</em> — click
            <em>OK</em>.</li>
        <li>Next, the phone will ask you to register your computer’s RSA key fingerprint. If this is a trusted machine, then
            check the <em>Always allow from this computer</em> option. </li>
    </ol>
    <p>Now that you’ve configured your device, click the <em>Run</em> button.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png" alt="run app" width="650" height="180" class="aligncenter size-large wp-image-162437" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-650x180.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app-480x133.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/run-app.png 1296w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>Just like before, you’ll get a prompt from the <em>Select Deployment Target</em> dialog. The device should now appear
        in this dialog. Select it and click <em>OK</em>.</p>
    <p>Ahh…isn’t it rewarding to see the app on your device? Go ahead and show it off to your friends. :]</p>
    <div class="note">
        <p><em>Note</em>: If the app is already running, you might not get the prompt. This is because of a new functionality
            in Android Studio know as <em>Instant Run</em>. We’ll talk about it in the next section of this tutorial. Close
            the emulator, go back and click the <em>Run</em> button again.</p>
    </div>
    <h2>Instant Run</h2>
    <p>From version 2.0 of Android Studio, a new functionality was introduced called <em>Instant Run</em>. Instant Run allows
        you to push updates (code and resources) to a running app on a device or emulator without performing a full reinstall.
        By doing this, you are able to view your changes in a shorter time.</p>
    <p>There are three kinds of changes you can make to your code: a hot swap, warm swap, or cold swap. Instant Run pushes updates
        by performing one of the following, depending on the kind of change you made: </p>
    <ol>
        <li><em>Hot Swap</em>: This applies to method changes. Your app continues to run but uses a stub method with the changes
            performed the next time the relevant method is called. This is the fastest swap.</li>
        <li><em>Warm Swap</em>: This swap applies to resource changes. With this, your the current activity will restart to update
            the changed resources.</li>
        <li><em>Cold Swap</em>: With this, Instant run restarts the whole app even though it does not perform a re-install. This
            swap applies to structural code changes</li>
    </ol>
    <h3>Testing Instant Run</h3>
    <p>Go ahead and try out Instant Run.</p>
    <p>To enable Instant Run, select <em>Android Studio \ Preferences \ Build, Execution, Deployment \ Instant Run</em>. Ensure
        that <em>Enable Instant Run to hot swap code/resource changes on deploy</em> is checked and that <em>Restart activity on code changes</em>        is unchecked.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-650x379.png" alt="" width="650" height="379" class="aligncenter size-large wp-image-162460" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-650x379.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-480x280.png 480w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>If your app is not yet running, launch it by clicking the <em>Run</em> button, and wait for it to launch.</p>
    <p>When the app is running, the <em>Apply Changes</em> button on the right side of the <em>Run</em> becomes enabled.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM-650x168.png" alt="" width="650" height="168" class="aligncenter size-large wp-image-162464" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM-650x168.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM-480x124.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screen-Shot-2017-05-20-at-7.52.44-PM.png 1296w" sizes="(max-width: 650px) 100vw, 650px"></a></p>
    <p>As your app is now running, clicking on the floating button, shows the message, <em>Replace with your own action</em>        at the bottom of the screen.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1-281x500.png" alt="" width="281" height="500" class="aligncenter size-large wp-image-162465" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/05/instant-run-screenshot-1.png 1080w" sizes="(max-width: 281px) 100vw, 281px"></a></p>
    <p>Change that message to test out Instant Run.</p>
    <p>Open <em>MainActivity</em>, in the <em>onCreate()</em> method, replace the text: <em>Replace with your own action</em>        with <em>Hello Instant Run</em>. </p>
    <p>Then click the <em>Apply Changes</em>. Now when you click the button, you will see the new message. This is an example
        of a hot swap.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374.png" sl-processed="1"><img src="https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374-281x500.png" alt="" width="281" height="500" class="aligncenter size-large wp-image-162467" srcset="https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/05/Screenshot_1495312374.png 1080w" sizes="(max-width: 281px) 100vw, 281px"></a></p>
    <p>Instant Run helps you code faster by significantly reducing the time it takes to update your app with code and resource
        changes. </p>
    <h2>Importing an Existing Project</h2>
    <p>During your Android app-making journey, you’ll find times where you need to import existing projects. The steps below
        will guide you through how to import a project:</p>
    <ol>
        <li>Download
            <a href="https://developer.android.com/downloads/samples/CardView.zip" title="this " sl-processed="1 ">this</a>            project to use as your test subject. </li>
        <li>Once downloaded, unzip the contents and place them somewhere easy to get to. </li>
        <li>In Android Studio, go to <em>File/New/Import Project…</em>.</li>
        <li>A window labeled <em>Select Eclipse or Gradle Project to Import</em> will appear. Select the unzipped project from
            Step 1 and click <em>OK</em>.</li>
        <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM.png
                " sl-processed="1 "><img class="aligncenter size-large wp-image-120323 " src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM-469x500.png
                " alt="Screen Shot 2015-11-09 at 2.42.57 PM " width="469 " height="500 " srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM-469x500.png
                469w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM-300x320.png
                300w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.42.57-PM.png 1176w
                " sizes="(max-width: 469px) 100vw, 469px "></a></p>
        <li>After Android Studio finishes importing, you’ll be dropped off on the screen below. Select the <em>Project</em> tab
            on the left panel as shown in the screenshot below. </li>
        <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM.png
                " sl-processed="1 "><img class="aligncenter size-large wp-image-120324 " src="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM-581x500.png
                " alt="Screen Shot 2015-11-09 at 2.43.30 PM " width="581 " height="500 " srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM-581x500.png
                581w, https://koenig-media.raywenderlich.com/uploads/2015/11/Screen-Shot-2015-11-09-at-2.43.30-PM-372x320.png
                372w " sizes="(max-width: 581px) 100vw, 581px "></a></p>
        <li>You’ll now see all the necessary files of the imported project in the project explorer. </li>
    </ol>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer.png " sl-processed="1 "><img src="https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer-700x500.png
                " alt="import_explorer " width="700 " height="500 " class="aligncenter size-large wp-image-121000 " srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer-700x500.png
                700w, https://koenig-media.raywenderlich.com/uploads/2015/11/import_explorer-448x320.png 448w " sizes="(max-width:
                700px) 100vw, 700px "></a></p>
    <p>It’s build and run time! Click the <em>Run</em> button in the toolbar and select either the emulator or device you’ve
        already set up.</p>
    <p><a href="https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run.png " sl-processed="1 "><img src="https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run-299x500.png
                " alt="card_view_run " width="299 " height="500 " class="aligncenter size-large wp-image-121001 " srcset="https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run-299x500.png
                299w, https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run-192x320.png 192w, https://koenig-media.raywenderlich.com/uploads/2015/11/card_view_run.png
                722w " sizes="(max-width: 299px) 100vw, 299px "></a></p>
    <h2>Where To Go From Here?</h2>
    <div class="inline-video-ad " id="sub-banner-inline ">
        <div class="inline-video-ad-wrapper ">
            <a href="https://videos.raywenderlich.com/courses " sl-processed="1 ">
                <div class="col-wrapper ">
                    <div class="col ">
                        <img src="https://koenig-assets.raywenderlich.com/wp-content/themes/raywenderlich/images/global/video-yeti@2x.png
                " alt="yeti holding videos ">
                    </div>
                    <div class="col large-col ">
                        <span>Want to learn even faster? Save time with our <span>video courses</span></span>
                    </div>
                </div>
            </a>
        </div>
    </div>
    <p>You’ve covered a lot of ground in this beginning Android development tutorial: from downloading and installing Android
        Studio, through creating your first “Hello World!” app, to deploying it on a physical device!</p>
    <p>Keep reading for the <a href="http://www.raywenderlich.com/120508/beginning-android-development-tutorial-android-studio
                " sl-processed="1
                ">next part of the series</a>, where you’ll take a tour of Android Studio.</p>
    <p>In the meantime, you can follow Android — like any language or framework, Android’s development community is a strong
        asset and supplier of endless reference. It’s never too soon or too late to start checking out Google’s <a href="https://events.google.com/io/ "
            target="_blank " title="Google I/O " sl-processed="1
                ">I/O conference</a>, <a href="http://android-developers.blogspot.com/ " target="_blank " title="Android Developers blog "
            sl-processed="1
                ">Android Developers blog</a> or <a href="https://www.youtube.com/user/androiddevelopers " target="_blank "
            title="Android Developer videos
                " sl-processed="1 ">Android Developer videos</a>.</p>
    <p><i>The Android robot is reproduced or modified from work created and shared by Google and used according to terms described in the Creative Commons 3.0 Attribution License.</i></p>
    <p>I hope you enjoyed this beginning Android development tutorial — you’ve successfully installed Android Studio and are
        now ready to take on the world of Android development. If you have any questions or comments, please join the discussion
        in the comments below.</p>
</div>