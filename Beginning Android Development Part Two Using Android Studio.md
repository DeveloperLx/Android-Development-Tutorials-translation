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
            Navigating through different files in your project using the project explorer
        </li>
        <li>
            Setting up the
            <em>
                AndroidManifest.xml
            </em>
            file
        </li>
        <li>
            Learning about the
            <em>
                Gradle
            </em>
            build system
        </li>
        <li>
            Importing files into your project
        </li>
        <li>
            Learning about the rich layout editor with dynamic layout previews
        </li>
        <li>
            Using
            <em>
                Logcat
            </em>
            and the
            <em>
                Android Monitor
            </em>
            to debug your app
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                Note:
            </em>
            This tutorial assumes that you’ve already installed Android Studio and
            have set up an emulator or a device configured for testing. If you haven’t,
            please refer to our previous tutorial about
            <a href="http://www.raywenderlich.com/120177/beginning-android-development-tutorial-installing-android-studio"
            sl-processed="1">
                installing Android Studio
            </a>
            to get up and running in no time!
        </p>
    </div>
    <h2>
        Getting Started with Android Studio
    </h2>
    <p>
        You’ll start by creating a brand new Android app that you’ll use to explore
        Android Studio and learn about its capabilities and interface.
    </p>
    <p>
        For bonus points, you’ll also walk away as a bonafide fortune teller —
        or something to that effect. At least you’ll have a fun app to play around
        with!
    </p>
    <p>
        Fire up Android Studio and in the
        <em>
            Android Studio Setup Wizard
        </em>
        window, select
        <em>
            Start a new Android Studio project
        </em>
        .
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
        In the
        <em>
            Create New Project
        </em>
        window, set the
        <em>
            Application Name
        </em>
        as Fortune Ball, enter a
        <em>
            Company Domain
        </em>
        of your choosing, and select a convenient location to host your application
        in the
        <em>
            Project location
        </em>
        field. Click
        <em>
            Next
        </em>
        .
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.55.46-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/Screen-Shot-2017-02-03-at-9.55.46-AM.png"
            alt="Screen Shot 2015-11-15 at 11.55.05 PM" width="686" height="696" class="aligncenter">
        </a>
    </p>
    <p>
        Now you’re looking at the
        <em>
            Target Android Devices
        </em>
        window. Check the
        <em>
            Phone and Tablet
        </em>
        box and specify
        <em>
            API 15
        </em>
        as the
        <em>
            Minimum SDK
        </em>
        . Click
        <em>
            Next
        </em>
        .
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
        From the
        <em>
            Add an activity to Mobile
        </em>
        window, select
        <em>
            Basic Activity
        </em>
        . Take a half minute here to look at all your options; this window gives
        you an overview of the layout template. In this case, it’ll be a blank
        activity with a toolbar at the top and a
        <a href="https://www.google.com/design/spec/components/buttons-floating-action-button.html#buttons-floating-action-button-floating-action-button"
        target="_blank" title="Floating Action Button" sl-processed="1">
            floating action button
        </a>
        at the bottom. Click
        <em>
            Next
        </em>
        to proceed.
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
        In the
        <em>
            Customize the Activity
        </em>
        window, which is shown in the screenshot below, you’ll have the option
        to change
        <em>
            Activity Name
        </em>
        ,
        <em>
            Layout Name
        </em>
        ,
        <em>
            Title
        </em>
        and
        <em>
            Menu Resource Name
        </em>
        . For the purposes of this tutorial, keep it simple and accept the default
        values by clicking
        <em>
            Finish
        </em>
        .
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
        Within a short amount of time (hopefully seconds!), you’ll land on a screen
        that looks similar to this:
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
        Build and run your application and you should see a similar screen on
        your device or emulator. Note that the emulator acts like a device, so
        it will need time to boot and load.
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
        Voila. That’s an app! There’s not much to it, but it’s enough to dive
        into the next section.
    </p>
    <h2>
        Project and File Structure
    </h2>
    <p>
        For this portion of the tutorial, your focus will be on the highlighted
        section of the screenshot below. This window shows the project files of
        your application. By default, the files are filtered to show
        <em>
            Android
        </em>
        project files.
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
        When you select the file dropdown menu as illustrated in the screenshot
        below, you’ll see several options to filter the files. The key filters
        here are
        <em>
            Project
        </em>
        and
        <em>
            Android
        </em>
        .
    </p>
    <p>
        The
        <em>
            Project
        </em>
        filter will show you all the application modules — there is a minimum
        of one application module in every project.
    </p>
    <p>
        Other types of modules include third-party library modules or other Android
        application modules (such as Android wear apps, Android TV, etc…). Each
        module has its own complete source sets, including a gradle file, resources
        and source files, e.g. java files.
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
                Note
            </em>
            : If you don’t see the project view open, you can click on the
            <em>
                Project
            </em>
            tab on the left side panel as indicated in the screenshot above.
        </p>
    </div>
    <p>
        The default filter is
        <em>
            Android
        </em>
        which groups files by specific types. You’ll see the following folders
        at the very top level:
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
        You’ll take a deeper dive into each of these folders, starting with the
        <em>
            manifests
        </em>
        in the next section.
    </p>
    <h2>
        Overview of the AndroidManifest.xml
    </h2>
    <p>
        Every Android application contains the
        <em>
            AndroidManifest.xml
        </em>
        file found in the
        <em>
            manifests
        </em>
        folder. This XML file informs your system of the app’s requirements and
        must be present in order for the Android system to build your app.
    </p>
    <p>
        Go to the app’s
        <em>
            manifests
        </em>
        folder and expand to select
        <em>
            AndroidManifest.xml
        </em>
        . Double click on the file to open.
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
        The
        <code>
            manifest
        </code>
        and
        <code>
            application
        </code>
        tags are required in the manifest file and must only appear once.
    </p>
    <p>
        In addition to the element name, each tag also defines a set of attributes.
        For example, some of the many attributes in the
        <code>
            application
        </code>
        tag are:
        <code>
            android:icon
        </code>
        ,
        <code>
            android:label
        </code>
        and
        <code>
            android:theme
        </code>
        .
    </p>
    <p>
        Other common elements that can appear in the manifest include:
    </p>
    <li>
        <code>
            uses-permission
        </code>
        : requests a special permission that must be granted to the application
        in order for it to operate correctly. For example, an app must request
        permission from the user in order to access the Internet—in this case you
        must specify the
        <code>
            android.permission.INTERNET
        </code>
        permission.
    </li>
    <li>
        <code>
            activity
        </code>
        : declares an activity that implements part of the application’s visual
        user interface and logic. Every activity that your app uses must appear
        in the manifest—undeclared activities won’t be seen by the system and sadly,
        they’ll never run.
    </li>
    <li>
        <code>
            service
        </code>
        : declares a service that you’re going to use to implement long-running
        background operations or a rich communications API that can be called by
        other applications. An example includes a network call to fetch data for
        your application. Unlike activities, services have no user interface.
    </li>
    <li>
        <code>
            receiver
        </code>
        : declares a broadcast receiver that enables applications to receive intents
        broadcast by the system or by other applications, even when other components
        of the application are not running. One example of a broadcast receiver
        would be when the battery is low and you get a system notification within
        your app, allowing you to write logic to respond.
    </li>
    <p>
        You can find a full list of tags allowed in the manifest file
        <a href="http://developer.android.com/guide/topics/manifest/manifest-intro.html"
        target="_blank" title="" sl-processed="1">
            here
        </a>
        on the Android Developer site.
    </p>
    <h3>
        Configuring the Manifest
    </h3>
    <p>
        You’re currently looking at an excellent example of a framework, but a
        terrible fortune teller; you’re here because you want to learn how to play
        around on Android. That’s rather convenient because the manifest needs
        some changes so you can look into the future.
    </p>
    <p>
        Under
        <code>
            activity
        </code>
        , add the following attribute:
        <code>
            android:screenOrientation="portrait"
        </code>
        . to restrict the screen to portrait mode only. If it’s absent, the screen
        will transform to landscape or portrait mode depending on the device’s
        orientation. After adding this attribute, your manifest file should look
        like the screenshot below:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/manifest-700x478.png"
        alt="manifest" width="700" height="478" class="aligncenter size-large wp-image-122951"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/manifest-700x478.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/manifest-469x320.png 469w, https://koenig-media.raywenderlich.com/uploads/2015/12/manifest.png 1273w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <p>
        Build and run the app. If you’re testing on your device, rotate your phone.
        Notice that the screen doesn’t transform into landscape mode as you have
        restricted this capability in the
        <em>
            AndroidManifest
        </em>
        file.
    </p>
    <h3>
        Overview of Gradle
    </h3>
    <p>
        Let’s shift gears to Gradle. In a nutshell, it’s a build system that’s
        utilized by Android Studio. It takes the Android project and builds/compiles
        it into an installable APK that in turn can be installed on devices.
    </p>
    <p>
        As shown below, you can find the
        <em>
            build.gradle
        </em>
        file, located under
        <em>
            Gradle scripts
        </em>
        , in your project at two levels: module level and project level. Most
        of the time, you’ll edit this file at the module level.
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
        Open up the
        <em>
            build.gradle (Module:app)
        </em>
        file. You’ll see the default gradle setup:
    </p>
    <pre lang="java" class="language-java hljs">
        apply plugin:
        <span class="hljs-string">
            'com.android.application'
        </span>
        android { compileSdkVersion
        <span class="hljs-number">
            25
        </span>
        buildToolsVersion
        <span class="hljs-string">
            "25.0.2"
        </span>
        defaultConfig { applicationId
        <span class="hljs-string">
            "com.raywenderlich.fortuneball"
        </span>
        minSdkVersion
        <span class="hljs-number">
            15
        </span>
        targetSdkVersion
        <span class="hljs-number">
            25
        </span>
        versionCode
        <span class="hljs-number">
            1
        </span>
        versionName
        <span class="hljs-string">
            "1.0"
        </span>
        testInstrumentationRunner
        <span class="hljs-string">
            "android.support.test.runner.AndroidJUnitRunner"
        </span>
        } buildTypes { release {
        <span class="hljs-function">
            minifyEnabled
            <span class="hljs-keyword">
                false
            </span>
            proguardFiles
            <span class="hljs-title">
                getDefaultProguardFile
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-string">
                    'proguard-android.txt'
                </span>
                )
            </span>
            , 'proguard-rules.pro' } } } dependencies
        </span>
        {
        <span class="hljs-function">
            compile
            <span class="hljs-title">
                fileTree
            </span>
            <span class="hljs-params">
                (dir:
                <span class="hljs-string">
                    'libs'
                </span>
                , include: [
                <span class="hljs-string">
                    '*.jar'
                </span>
                ])
            </span>
            <span class="hljs-title">
                androidTestCompile
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-string">
                    'com.android.support.test.espresso:espresso-core:2.2.2'
                </span>
                , { exclude group:
                <span class="hljs-string">
                    'com.android.support'
                </span>
                ,
                <span class="hljs-keyword">
                    module
                </span>
                :
                <span class="hljs-string">
                    'support-annotations'
                </span>
                })
            </span>
            compile 'com.android.support:appcompat-v7:25.1.0' compile 'com.android.support:design:25.1.0'
            testCompile 'junit:junit:4.12' }
        </span>
    </pre>
    <p>
        Let’s step through the major components:
    </p>
    <li>
        <code>
            apply plugin: 'com.android.application'
        </code>
        applies the Android plugin at the parent level and makes available the
        top level build tasks required to build an Android app.
    </li>
    <li>
        Next in the
        <code>
            android{...}
        </code>
        section, you get configuration options such as
        <code>
            targetSdkVersion
        </code>
        . The target SDK for your application should be kept at the latest API
        level (
        <em>
            25
        </em>
        as we publish this tutorial). Another important component is the
        <code>
            minSDKVersion
        </code>
        which defines the minimum SDK version a device should have installed in
        order to run your application. For example, if your device’s SDK version
        was 14, then this app won’t be able to run on that device since here the
        minimum supported version is 15.
    </li>
    <li>
        The last component is
        <code>
            dependencies{...}
        </code>
        . The important dependencies to note are
        <code>
            compile 'com.android.support:appcompat-v7:VERSION'
        </code>
        and
        <code>
            compile 'com.android.support:design:VERSION'
        </code>
        . They provide support and compatibility with the new features from the
        latest API to the older APIs.
    </li>
    <p>
        In addition to Android compatibility libraries, you can also add other
        third party libraries in the
        <code>
            dependencies{...}
        </code>
        component. You’ll add an animation library where you’ll be able to add
        some cool effects to user interface elements in your application. Find
        <code>
            dependencies
        </code>
        , and add the following two lines at the bottom:
    </p>
    <pre lang="java" class="language-java hljs">
        dependencies { ... compile
        <span class="hljs-string">
            'com.daimajia.easing:library:2.0@aar'
        </span>
        compile
        <span class="hljs-string">
            'com.daimajia.androidanimations:library:2.2@aar'
        </span>
        }
    </pre>
    <p>
        Here you added two new third-party dependencies that will help you make
        FortuneBall shine. These libraries will be automatically downloaded and
        integrated by Android Studio.
    </p>
    <p>
        In fact, once you add these dependencies, Android Studio realizes that
        it needs to download them and tells you as much. Look for a bar across
        the top of the
        <em>
            build.gradle
        </em>
        file as shown the next screenshot. Click
        <em>
            Sync Now
        </em>
        to integrate these dependencies in your app.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/sync-700x92.png"
        alt="sync" width="700" height="92" class="aligncenter size-large wp-image-122953"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/sync-700x92.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/sync-480x63.png 480w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <p>
        Syncing takes couple of seconds. You can monitor the Gradle file update
        in the
        <em>
            Messages
        </em>
        tab in the bottom panel. Look for a success message in that panel as shown
        in the screenshot below.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/success-700x251.png"
        alt="success" width="700" height="251" class="aligncenter size-large wp-image-122954"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/success-700x251.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/12/success-480x172.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/12/success.png 1247w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <p>
        Alright, that’s all the config you need to do to Gradle for now. The whole
        point of this was so that you’re setup to add some fancy animations to
        your application, which you’ll do in a bit.
    </p>
    <h2>
        Importing files
    </h2>
    <p>
        An important part of making an Android app involves integrating other
        resources such as images, custom fonts, sounds, videos etc. These resources
        have to be imported into Android Studio and must be placed in appropriate
        folders. This allows the Android operating system to pick the correct resource
        for your app.
    </p>
    <p>
        For Fortune Ball, you’ll be importing image assets and will place them
        in drawable folders. Drawable folders can hold images or custom XML drawables
        (i.e. you can draw shapes via XML code and use them in your app’s layouts).
    </p>
    <p>
        To get started, download the image assets
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/11/drawable.zip"
        sl-processed="1">
            here
        </a>
        , then unzip the contents and save them where they can be easily accessed.
    </p>
    <p>
        Back in the project in Android Studio, switch the view from
        <em>
            Android
        </em>
        to
        <em>
            Project
        </em>
        . Open the
        <em>
            res
        </em>
        folder under
        <em>
            app &gt; src &gt; main
        </em>
        . Right click on the
        <em>
            res
        </em>
        folder, select
        <em>
            New &gt; Android resource directory
        </em>
        .
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
        You’ll get a window titled
        <em>
            New Resource Directory
        </em>
        . From the
        <em>
            Resource type
        </em>
        dropdown select the
        <em>
            drawable
        </em>
        option. In the
        <em>
            Available qualifiers
        </em>
        list, select
        <em>
            Density
        </em>
        and click the button highlighted in the screenshot below:
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
        In the subsequent window, select
        <em>
            XX-High Density
        </em>
        from the
        <em>
            Density
        </em>
        dropdown. Click
        <em>
            OK
        </em>
        .
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
        Repeat the same process and create
        <em>
            drawable-xhdpi
        </em>
        ,
        <em>
            drawable-hdpi
        </em>
        and
        <em>
            drawable-mdpi
        </em>
        folders by selecting X-High, high, and medium density respectively from
        the
        <em>
            Density
        </em>
        dropdown.
    </p>
    <p>
        Each drawable folder that has a density qualifier (i.e. xxhdpi, xhdpi,
        hdpi) houses images corresponding to that particular density or resolution.
        For example, the folder
        <em>
            drawable-xxhdpi
        </em>
        contains the image that is extra high density, meaning an Android device
        with a high resolution screen will pick the image from this folder. This
        allows your app to look great on all Android devices, irrespective of the
        screen quality. To learn more about screen densities, check out the
        <a href="https://developer.android.com/guide/practices/screens_support.html"
        target="_blank" sl-processed="1">
            Android documentation
        </a>
        .
    </p>
    <p>
        After creating all the drawable folders, go back to the unzipped contents
        in the finder, and copy (
        <em>
            cmd + C
        </em>
        ) the image from each folder and paste (
        <em>
            cmd + V
        </em>
        ) it into the corresponding folder in Android Studio.
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
        When you paste the files, you’ll be presented with the
        <em>
            Copy
        </em>
        window. Select
        <em>
            OK
        </em>
        .
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
        You’ve just put the ball in Fortune Ball and know how to import things
        now. Looks like you just checked another feature off your to-learn list!
    </p>
    <h3>
        XML View with Dynamic Layout Previews
    </h3>
    <p>
        An incredibly important part of building an Android application is creating
        a layout that the users of the application interact with. In Android Studio,
        you do this task in the layout editor. Open up
        <em>
            content_main.xml
        </em>
        from
        <em>
            res/layout
        </em>
        . You’ll initially land on the
        <em>
            Design
        </em>
        tab of the layout editor. In this tab, you can drag user interface elements
        like buttons, text fields etc. in the editor.
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
        On the right hand side of the
        <em>
            Design
        </em>
        tab is the
        <em>
            Text
        </em>
        tab. Switching to this view allows you to edit the XML that makes up the
        layout directly.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2015/12/text_tab-480x204.png"
        alt="text_tab" width="480" height="204" class="aligncenter size-medium wp-image-122960"
        srcset="https://koenig-media.raywenderlich.com/uploads/2015/12/text_tab-480x204.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/12/text_tab.png 696w"
        sizes="(max-width: 480px) 100vw, 480px">
    </p>
    <p>
        In both tabs, you’ll be able to preview the layout in the device as you
        build. Choose the
        <em>
            Text
        </em>
        tab to start building the layout for Fortune Ball.
    </p>
    <p>
        Before you start building the view, you need to define some values. Open
        up
        <em>
            strings.xml
        </em>
        under
        <em>
            res/values
        </em>
        and add the following:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "fortune_description"
            </span>
            &gt;
        </span>
        Suggest the question, which you can answer “yes” or “no”, then click on
        the magic ball.
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
    </pre>
    <p>
        <em>
            strings.xml
        </em>
        contains all the user-facing strings that appear in your app. Splitting
        the strings out into their own file makes internationalization a breeze,
        as you just provide a strings file for each language you wish to support.
        Although you might not want to translate your app right away, it’s considered
        a best-practice to use a strings file.
    </p>
    <p>
        Next, open
        <em>
            dimens.xml
        </em>
        under
        <em>
            res/values
        </em>
        and add the following:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                dimen
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "description_text_size"
            </span>
            &gt;
        </span>
        15sp
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                dimen
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                dimen
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "fortune_text_size"
            </span>
            &gt;
        </span>
        20sp
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                dimen
            </span>
            &gt;
        </span>
    </pre>
    <p>
        <em>
            dimens.xml
        </em>
        contains all the dimensions values such as margin spacing for your layouts,
        sizes of text etc. Again, it’s a good practice to keep the dimensions in
        this file so that they can be re-used in constructing layouts.
    </p>
    <p>
        Head back to
        <em>
            content_main.xml
        </em>
        and replace the entire contents of the file with the code below.
    </p>
    <pre lang="xml" class="language-xml hljs">
        &lt;?xml version="1.0" encoding="utf-8"?&gt;
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                RelativeLayout
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            <span class="hljs-attr">
                xmlns:tools
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/tools"
            </span>
            <span class="hljs-attr">
                xmlns:app
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res-auto"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                app:layout_behavior
            </span>
            =
            <span class="hljs-string">
                "@string/appbar_scrolling_view_behavior"
            </span>
            <span class="hljs-attr">
                tools:showIn
            </span>
            =
            <span class="hljs-string">
                "@layout/activity_main"
            </span>
            <span class="hljs-attr">
                tools:context
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
                TextView
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/descriptionText"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:text
            </span>
            =
            <span class="hljs-string">
                "@string/fortune_description"
            </span>
            <span class="hljs-attr">
                android:gravity
            </span>
            =
            <span class="hljs-string">
                "center"
            </span>
            <span class="hljs-attr">
                android:textSize
            </span>
            =
            <span class="hljs-string">
                "@dimen/description_text_size"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                ImageView
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/fortunateImage"
            </span>
            <span class="hljs-attr">
                android:src
            </span>
            =
            <span class="hljs-string">
                "@drawable/img_crystal"
            </span>
            <span class="hljs-attr">
                android:layout_centerHorizontal
            </span>
            =
            <span class="hljs-string">
                "true"
            </span>
            <span class="hljs-attr">
                android:layout_below
            </span>
            =
            <span class="hljs-string">
                "@id/descriptionText"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "10dp"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                TextView
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/fortuneText"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:layout_below
            </span>
            =
            <span class="hljs-string">
                "@id/fortunateImage"
            </span>
            <span class="hljs-attr">
                android:gravity
            </span>
            =
            <span class="hljs-string">
                "center"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "20dp"
            </span>
            <span class="hljs-attr">
                android:textSize
            </span>
            =
            <span class="hljs-string">
                "@dimen/fortune_text_size"
            </span>
            <span class="hljs-attr">
                android:textStyle
            </span>
            =
            <span class="hljs-string">
                "bold"
            </span>
            <span class="hljs-attr">
                android:textColor
            </span>
            =
            <span class="hljs-string">
                "@android:color/holo_red_dark"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                Button
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/fortuneButton"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "match_parent"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "50dp"
            </span>
            <span class="hljs-attr">
                android:layout_below
            </span>
            =
            <span class="hljs-string">
                "@id/fortuneText"
            </span>
            <span class="hljs-attr">
                android:text
            </span>
            =
            <span class="hljs-string">
                "What's my fortune?"
            </span>
            <span class="hljs-attr">
                android:layout_centerHorizontal
            </span>
            =
            <span class="hljs-string">
                "true"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "10dp"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                RelativeLayout
            </span>
            &gt;
        </span>
    </pre>
    <p>
        This rather large chunk of XML creates the layout of FortuneBall. At the
        top level you’ve added a
        <em>
            RelativeLayout
        </em>
        , whose job it is to layout its contents. It is stretched to match the
        size of its parent (i.e. the full activity).
    </p>
    <p>
        Within the relative layout you added two pieces of text, an image and
        a button. These will appear within the container in the order that you
        added them, and their content is read from the
        <em>
            strings.xml
        </em>
        in the case of the text views, and from the drawable you added in the
        case of the image.
    </p>
    <p>
        As you’re updating
        <em>
            content_main.xml
        </em>
        , notice how the
        <em>
            Preview
        </em>
        window updates the UI:
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
            : If you can’t see the preview window, then click on the
            <em>
                Preview
            </em>
            button on the right-hand side panel of the layout editor while you’re
            still in the
            <em>
                Text
            </em>
            tab.
        </p>
    </div>
    <p>
        Build and run.
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
        Congrats! You’ve designed your app’s layout. However, it’s only a pretty
        picture at this point — clicking on that button doesn’t do anything. Ready
        to play around with activities?
    </p>
    <h2>
        Connecting Views with Activities
    </h2>
    <p>
        You use the java files located in
        <em>
            app / src / main / java
        </em>
        to implement your app’s logic.
    </p>
    <p>
        Open
        <em>
            MainActivity.java
        </em>
        and add these imports directly below the existing imports
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            import
        </span>
        java.util.Random;
        <span class="hljs-keyword">
            import
        </span>
        android.view.View;
        <span class="hljs-keyword">
            import
        </span>
        android.widget.Button;
        <span class="hljs-keyword">
            import
        </span>
        android.widget.ImageView;
        <span class="hljs-keyword">
            import
        </span>
        android.widget.TextView;
        <span class="hljs-keyword">
            import
        </span>
        com.daimajia.androidanimations.library.Techniques;
        <span class="hljs-keyword">
            import
        </span>
        com.daimajia.androidanimations.library.YoYo;
    </pre>
    <p>
        The first five imports indicate that you will be referencing the Random,
        View, Button, ImageView and TextView classes respectively in your code.
        The next two imports indicate that you will be using two classes from the
        libraries included in the
        <em>
            build.gradle
        </em>
        earlier for animations. Inside of
        <em>
            MainActivity.java
        </em>
        add the following inside the
        <code>
            MainActivity
        </code>
        class:
    </p>
    <pre lang="java" class="language-java hljs">
        String fortuneList[] = {
        <span class="hljs-string">
            "Don’t count on it"
        </span>
        ,
        <span class="hljs-string">
            "Ask again later"
        </span>
        ,
        <span class="hljs-string">
            "You may rely on it"
        </span>
        ,
        <span class="hljs-string">
            "Without a doubt"
        </span>
        ,
        <span class="hljs-string">
            "Outlook not so good"
        </span>
        ,
        <span class="hljs-string">
            "It's decidedly so"
        </span>
        ,
        <span class="hljs-string">
            "Signs point to yes"
        </span>
        ,
        <span class="hljs-string">
            "Yes definitely"
        </span>
        ,
        <span class="hljs-string">
            "Yes"
        </span>
        ,
        <span class="hljs-string">
            "My sources say NO"
        </span>
        }; TextView mFortuneText; Button mGenerateFortuneButton; ImageView mFortuneBallImage;
    </pre>
    <p>
        In this small chunk of code you’ve declared 4 member variables for the
        activity. The first is an array of strings that represent the possible
        fortunes, and the remaining three represent the UI elements you created
        in the layout.
    </p>
    <p>
        Next, replace the content of the
        <code>
            onCreate()
        </code>
        method with the following:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-comment">
            // 1:
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState);
        <span class="hljs-comment">
            // 2:
        </span>
        setContentView(R.layout.activity_main); Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);
        <span class="hljs-comment">
            // 3:
        </span>
        mFortuneText = (TextView) findViewById(R.id.fortuneText); mFortuneBallImage
        = (ImageView) findViewById(R.id.fortunateImage); mGenerateFortuneButton
        = (Button) findViewById(R.id.fortuneButton);
        <span class="hljs-comment">
            // 4:
        </span>
        mGenerateFortuneButton.setOnClickListener(
        <span class="hljs-keyword">
            new
        </span>
        View.OnClickListener() {
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onClick
            </span>
            <span class="hljs-params">
                (View view)
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 5:
        </span>
        <span class="hljs-keyword">
            int
        </span>
        index =
        <span class="hljs-keyword">
            new
        </span>
        Random().nextInt(fortuneList.length); mFortuneText.setText(fortuneList[index]);
        <span class="hljs-comment">
            // 6:
        </span>
        YoYo.with(Techniques.Swing) .duration(
        <span class="hljs-number">
            500
        </span>
        ) .playOn(mFortuneBallImage); } });
    </pre>
    <p>
        Taking the numbered sections one-by-one:
    </p>
    <ol>
        <li>
            Call the superclass implementation to ensure the activity is ready to
            go.
        </li>
        <li>
            Specify that the layout for this activity is provided by the layout you
            created before, and perform some preparation on the toolbar.
        </li>
        <li>
            Populate the values of the three member variables you created before for
            the views in the layout using the
            <code>
                findViewById
            </code>
            method. The
            <code>
                id
            </code>
            value is the same as the one you provided in the XML layout.
        </li>
        <li>
            Add an
            <code>
                OnClickListener
            </code>
            to the button. This is a simple class that encapsulates the functionality
            you’d like to perform when the button is pressed.
        </li>
        <li>
            Find a random fortune from the
            <code>
                fortuneList
            </code>
            array, and update the fortune text to show it.
        </li>
        <li>
            Use the third-party animation library you added as a dependency to the
            gradle file to add a fun animation to the crystal ball image.
        </li>
    </ol>
    <p>
        OK—that wasn’t too bad right? Build and run, and hit the button to test
        out your fortune-telling powers.
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
        Tidy Up
    </h2>
    <p>
        You’re almost done. But before you start planning your release party,
        you have some clean up ahead, like getting rid of that floating button.
        Head to
        <em>
            res / layout
        </em>
        and open
        <em>
            activity_main.xml
        </em>
        .
    </p>
    <p>
        This layout file contains a reference to
        <em>
            content_main.xml
        </em>
        that you previously edited. It wraps the content with the default toolbar
        and floating action button. However, Fortune Ball doesn’t need a floating
        action button, so remove the following code block from this xml file:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                android.support.design.widget.FloatingActionButton
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/fab"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:layout_gravity
            </span>
            =
            <span class="hljs-string">
                "bottom|end"
            </span>
            <span class="hljs-attr">
                android:layout_margin
            </span>
            =
            <span class="hljs-string">
                "@dimen/fab_margin"
            </span>
            <span class="hljs-attr">
                android:src
            </span>
            =
            <span class="hljs-string">
                "@android:drawable/ic_dialog_email"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        Build and run. You won’t be seeing that the floating button on the bottom
        right-hand corner around here anymore:
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
        Ask a question, click or tap on
        <em>
            What’s my fortune?
        </em>
        and let your future unfold before your eyes!
    </p>
    <h2>
        Android Monitor
    </h2>
    <p>
        Android Studio provides a bunch of tools to help you look under the hood
        of your application. Take a look, by opening the
        <em>
            Android Monitor
        </em>
        tab on the bottom of your Android Studio window.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/02/android_monitor_tab.png"
        alt="android monitor tab" width="470" height="17" class="aligncenter size-full wp-image-156539">
    </p>
    <p>
        Here, you find a wealth of helpful developer options. Let’s walk through
        a few of them. Don’t worry; you don’t have to memorize them all and there
        won’t be a quiz. :]
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
        Start at the top, where you specify the device or emulator you want to
        monitor, and the “process” you are most interested in (you should select
        your app’s package name if it’s not already selected).
    </p>
    <p>
        Continue by hovering over some of the buttons on the left, to reveal their
        tooltips.
    </p>
    <ul>
        <li>
            The camera and play button in the top left enable taking screenshots or
            <a href="https://developer.android.com/studio/debug/am-video.html" sl-processed="1">
                screen video recordings
            </a>
            .
        </li>
        <li>
            The magnifying glass reveals several more options, like analyzing your
            app’s memory usage.
        </li>
        <li>
            The
            <em>
                Layout Inspector
            </em>
            gives a very cool visual interface to help you determine exactly why your
            app’s UI looks the way it does.
        </li>
    </ul>
    <p>
        Finally, there is LogCat, which gives you a detailed view into your device’s
        system messages with the ability to drill down into a specific application,
        or even use the search bar to filter out messages unless they contain specific
        text.
    </p>
    <p>
        Make sure you’ve selected
        <em>
            Show only selected application
        </em>
        in the top right, as shown in the screenshot earlier. Now, you will only
        see messages from your app, including those you write yourself. Oh, what?
        You’ve not added any messages for yourself?
    </p>
    <p>
        Head to
        <em>
            MainActivity.java
        </em>
        and add the following to the list of imports
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.util.Log;
    </pre>
    <p>
        At the end of
        <code>
            onCreate()
        </code>
        in
        <em>
            MainActivity.java
        </em>
        add the following line:
    </p>
    <pre lang="java" class="language-java hljs">
        Log.v(
        <span class="hljs-string">
            "FORTUNE APP TAG"
        </span>
        ,
        <span class="hljs-string">
            "onCreateCalled"
        </span>
        );
    </pre>
    <p>
        The
        <code>
            Log.v
        </code>
        calls for two parameters — a tag and a message. In this case, you’ve defined
        the tag as
        <code>
            "FORTUNE APP TAG"
        </code>
        and the message as
        <code>
            "onCreateCalled"
        </code>
        .
    </p>
    <p>
        Build and run the app so you can see this log message in the
        <em>
            Logcat
        </em>
        panel.
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
        To filter the LogCat contents to just your message alone, type
        <em>
            onCreateCalled
        </em>
        into the search box above the console, like this:
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
        Then remove your search text to see all the log messages again.
    </p>
    <p>
        Another very useful utility of logcat is the ability to see stacktrace
        or error messages from app crashes and exceptions. You’ll add a bug to
        your perfectly working app to see how that works.
    </p>
    <p>
        Go to
        <em>
            MainActivity.java
        </em>
        and comment out the following line in
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-comment">
            //mFortuneText = (TextView) findViewById(R.id.fortuneText);
        </span>
    </pre>
    <p>
        Build and run the application. Once it launches click the
        <em>
            What’s My Fortune?
        </em>
        button on the screen. Oh no! It crashed.
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
        How would you go about fixing this if you hadn’t put the bug in on purpose?
        Logcat to the rescue!
    </p>
    <p>
        Head back to the
        <em>
            Logcat
        </em>
        panel — it’ll look something like this:
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
        That sure is a lot of red text, and it’s exactly where to go sniffing
        around for clues. You’re looking for an exception somewhere. In this case,
        it’s line 50 in the
        <em>
            MainActivity.java
        </em>
        file. LogCat has even helpfully turned that link into a blue hyperlink,
        and if you click it you will be taken right to the problematic line!
    </p>
    <p>
        By commenting out
        <code>
            mFortuneText = (TextView) findViewById(R.id.fortuneText)
        </code>
        , you created a variable but didn’t assign it a value — hence the null
        pointer exception.
    </p>
    <p>
        Go ahead and uncomment that code and build and run the application. This
        time there’s no crash!
    </p>
    <p>
        Logcat is a powerful tool that lets you debug your application errors
        and exception.
    </p>
    <h2>
        Where to Go From Here?
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
        You can
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/02/FortuneBall-3.zip"
        target="_blank" title="final project" sl-processed="1">
            download the final project here
        </a>
        .
    </p>
    <p>
        Practice makes perfect! You’ve learned your way around and can now create
        a project, play around with Gradle, import assets, set up layouts and do
        some testing.
    </p>
    <p>
        There’s a lot of cool stuff to learn about Android, and I suggest you
        start with these next steps:
    </p>
    <ul>
        <li>
            Get familiar with Logcat and the filtering mechanism. Filter by different
            criteria.
        </li>
        <li>
            There will be times where you’ll want to test your application’s robustness
            in different network environments. See the
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
            This beginning Android development tutorial has just touched on some of
            the tools used to build out the layout and UI. To learn more, pour over
            the official
            <a href="http://developer.android.com/guide/topics/ui/index.html" target="_blank"
            title="Android documentation for UI" sl-processed="1">
                Android documentation for UI
            </a>
            .
        </li>
        <li>
            Keep coming back to raywenderlich.com—- we’ve got some great Android content
            coming your way over the next days, weeks and months.
        </li>
        <li>
            Talk to other developers. Make use of the forums below and ask your questions,
            share your findings and pick up tips.
        </li>
    </ul>
    <div class="note">
        <em>
            Note:
        </em>
        Also, another great next step would be to check out our Android Core Concepts
        tutorials:
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