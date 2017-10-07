# Android Activity的介绍 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/165824/introduction-android-activities-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                Update Note
            </em>
            : This tutorial has been updated to Kotlin and Android Studio 3.0 by Joe
            Howard. The original tutorial was written by Namrata Bandekar.
        </p>
    </div>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/07/Activities-feature.png"
        alt="Learn how to juggle like an Android!" width="250" height="250" class="alignright size-full bordered">
    </p>
    <p>
        When you make an Android app, it’s pretty likely that the first thing
        you’ll do is plot and plan how you’ll take over the world. Just kidding.
        Actually, the first thing you do is create an
        <em>
            Activity
        </em>
        . Activities are where all the action happens, because they are the screens
        that allow the user to interact with your app.
    </p>
    <p>
        In short, activities are one of the basic building blocks of an Android
        application.
    </p>
    <p>
        In this Introduction to Android Activities Tutorial, you’ll dive into
        how to work with activities. You’ll create a to-do list app named
        <em>
            Forget Me Not
        </em>
        and along the way learn:
    </p>
    <ul>
        <li>
            The process for creating, starting and stopping an activity, and how to
            handle navigation between activities.
        </li>
        <li>
            The various stages in the lifecycle of an activity and how to handle each
            stage gracefully.
        </li>
        <li>
            The way to manage configuration changes and persist data within your activity.
        </li>
    </ul>
    <p>
        In addition, you’ll use the (newly official)
        <em>
            Kotlin
        </em>
        programming language and Android Studio 3.0. You’ll need to use Kotlin
        1.1.3 or later and Android Studio 3.0 Canary 5 or later.
    </p>
    <p>
        This tutorial assumes you’re familiar with the basics of Android development.
        If you’re completely new to Kotlin, XML or Android Studio, you should take
        a look at the
        <a href="https://www.raywenderlich.com/161318/beginning-android-development-part-one-installing-android-studio"
        target="_blank" title="Beginning Android Development Series" sl-processed="1">
            Beginning Android Development Series
        </a>
        and
        <a href="https://www.raywenderlich.com/132381/kotlin-for-android-an-introduction"
        target="_blank" title="Kotlin For Android: An Introduction" sl-processed="1">
            Kotlin For Android: An Introduction
        </a>
        before you start.
    </p>
    <h2>
        Getting Started
    </h2>
    <p>
        Download and extract the
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/07/ForgetMeNot-starter.zip"
        title="starter project" sl-processed="1">
            starter project
        </a>
        for this tutorial. Open
        <em>
            Android Studio
        </em>
        3.0 or later, and choose
        <em>
            Open an existing Android Studio project
        </em>
        . Then select the project you just extracted.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM-650x403.png"
            alt="" width="650" height="403" class="aligncenter size-large wp-image-165861"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM-650x403.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM-480x298.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/06/Screen-Shot-2017-06-19-at-11.32.28-AM.png 1554w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        Your subject and new best friend for the rest of the tutorial is
        <em>
            Forget Me Not
        </em>
        , which is a simple app that lets you add and delete tasks from a list.
        It also displays the current date and time so you’re always on top of your
        game!
    </p>
    <p>
        <em>
            Run
        </em>
        the project as it is now and you’ll see a very basic screen:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7-280x500.png"
            alt="" width="280" height="500" class="aligncenter size-large wp-image-165885"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7-280x500.png 280w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7-179x320.png 179w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn7.png 799w"
            sizes="(max-width: 280px) 100vw, 280px">
        </a>
    </p>
    <p>
        At this point, there isn’t much you can do. Your to-do list is empty and
        the “ADD A TASK” button does nothing when you tap it. Your mission is to
        liven up this screen by making the to-do list modifiable.
    </p>
    <h2>
        Activity Lifecycle
    </h2>
    <p>
        Before firing up your fingers, indulge yourself in a bit of theory.
    </p>
    <p>
        As mentioned earlier, activities are the foundations upon which you build
        screens for your app. They encompass multiple components the user can interact
        with, and it’s likely that your app will have multiple activities to handle
        the various screens you create.
    </p>
    <p>
        Having all these activities doing different things makes it sound like
        developing an Android app is a complicated undertaking.
    </p>
    <p>
        Fortunately, Android handles this with specific
        <em>
            callback methods
        </em>
        that initiate code only when it’s needed. This system is known as the
        <em>
            activity lifecycle
        </em>
        .
    </p>
    <p>
        Handling the various lifecycle stages of your activities is crucial to
        creating a robust and reliable app. The lifecycle of an activity is best
        illustrated as a step pyramid of different stages linked by the core callback
        methods:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid.png"
            alt="Adapted from developer.android.com" width="630" height="429" class="aligncenter size-large wp-image-116817"
            srcset="https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid.png 630w, https://koenig-media.raywenderlich.com/uploads/2015/09/activity_lifecycle_pyramid-470x320.png 470w"
            sizes="(max-width: 630px) 100vw, 630px">
        </a>
    </p>
    <p>
        Following the diagram above, you can picture the lifecycle in action as
        it courses through your code. Take a closer look at each of the callbacks:
    </p>
    <ul>
        <li>
            <em>
                onCreate()
            </em>
            : Called by the OS when the activity is first created. This is where you
            initialize any UI elements or data objects. You also have the
            <code>
                savedInstanceState
            </code>
            of the activity that contains its previously saved state, and you can
            use it to recreate that state.
        </li>
        <li>
            <em>
                onStart()
            </em>
            : Just before presenting the user with an activity, this method is called.
            It’s always followed by
            <code>
                onResume()
            </code>
            . In here, you generally should start UI animations, audio based content
            or anything else that requires the activity’s contents to be on screen.
        </li>
        <li>
            <em>
                onResume()
            </em>
            : As an activity enters the foreground, this method is called. Here you
            have a good place to restart animations, update UI elements, restart camera
            previews, resume audio/video playback or initialize any components that
            you release during
            <code>
                onPause()
            </code>
            .
        </li>
        <li>
            <em>
                onPause()
            </em>
            : This method is called before sliding into the background. Here you should
            stop any visuals or audio associated with the activity such as UI animations,
            music playback or the camera. This method is followed by
            <code>
                onResume()
            </code>
            if the activity returns to the foreground or by
            <code>
                onStop()
            </code>
            if it becomes hidden.
        </li>
        <li>
            <em>
                onStop()
            </em>
            : This method is called right after
            <code>
                onPause()
            </code>
            , when the activity is no longer visible to the user, and it’s a good
            place to save data that you want to commit to the disk. It’s followed by
            either
            <code>
                onRestart()
            </code>
            , if this activity is coming back to the foreground, or
            <code>
                onDestroy()
            </code>
            if it’s being released from memory.
        </li>
        <li>
            <em>
                onRestart()
            </em>
            : Called after stopping an activity, but just before starting it again.
            It’s always followed by
            <code>
                onStart()
            </code>
            .
        </li>
        <li>
            <em>
                onDestroy()
            </em>
            : This is the final callback you’ll receive from the OS before the activity
            is destroyed. You can trigger an activity’s desctruction by calling
            <code>
                finish()
            </code>
            , or it can be triggered by the system when the system needs to recoup
            memory. If your activity includes any background threads or other long-running
            resources, destruction could lead to a memory leak if they’re not released,
            so you need to remember to stop these processes here as well.
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : You do not call any of the above callback methods directly in your own
            code (other than superclass invocations) — you only override them as needed
            in your activity subclasses. They are called by the OS when a user opens,
            hides or exits the activity.
        </p>
    </div>
    <p>
        So many methods to remember! In the next section, you’ll see some of these
        lifecycle methods in action, and then it’ll be a lot easier to remember
        what everything does.
    </p>
    <h2>
        Configuring an Activity
    </h2>
    <p>
        Keeping the activity lifecycle in mind, take a look at an activity in
        the sample project. Open
        <em>
            MainActivity.kt
        </em>
        , and you’ll see that the class with its
        <code>
            onCreate()
        </code>
        override looks like this:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainActivity
            </span>
            :
            <span class="hljs-type">
                AppCompatActivity
            </span>
        </span>
        () {
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        taskList: MutableList&lt;String&gt; = mutableListOf()
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        adapter
        <span class="hljs-keyword">
            by
        </span>
        lazy { makeAdapter(taskList) }
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
        <span class="hljs-comment">
            // 2
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState)
        <span class="hljs-comment">
            // 3
        </span>
        setContentView(R.layout.activity_main)
        <span class="hljs-comment">
            // 4
        </span>
        taskListView.adapter = adapter
        <span class="hljs-comment">
            // 5
        </span>
        taskListView.onItemClickListener = AdapterView.OnItemClickListener { parent,
        view, position, id -&gt; } }
        <span class="hljs-comment">
            // 6
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                addTaskClicked
            </span>
            <span class="hljs-params">
                (view:
                <span class="hljs-type">
                    View
                </span>
                )
            </span>
        </span>
        { }
        <span class="hljs-comment">
            // 7
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                makeAdapter
            </span>
            <span class="hljs-params">
                (list:
                <span class="hljs-type">
                    List
                </span>
                &lt;
                <span class="hljs-type">
                    String
                </span>
                &gt;)
            </span>
        </span>
        : ArrayAdapter&lt;String&gt; = ArrayAdapter(
        <span class="hljs-keyword">
            this
        </span>
        , android.R.layout.simple_list_item_1, list) }
    </pre>
    <p>
        Here’s a play-by-play of what’s happening above:
    </p>
    <ol>
        <li>
            You initialize the activity’s properties, which include an empty mutable
            list of tasks and an adapter initialized using
            <code>
                by lazy
            </code>
            .
        </li>
        <li>
            You call
            <code>
                onCreate()
            </code>
            on the superclass — remember that this is (usually) the first thing you
            should do in a callback method. There are some advanced cases in which
            you may call code prior to calling the superclass.
        </li>
        <li>
            You set the content view of your activity with the corresponding layout
            file resource.
        </li>
        <li>
            Here you set up the adapter for
            <code>
                taskListView
            </code>
            . The reference to
            <code>
                taskListView
            </code>
            is initialized using
            <em>
                Kotlin Android Extensions
            </em>
            , on which you can find more info
            <a href="https://kotlinlang.org/docs/tutorials/android-plugin.html" sl-processed="1">
                here
            </a>
            . This replaces
            <code>
                findViewById()
            </code>
            calls and the need for other view-binding libraries.
        </li>
        <li>
            You add an empty
            <code>
                OnItemClickListener()
            </code>
            to the
            <code>
                ListView
            </code>
            to capture the user’s taps on individual list entries. The listener is
            a Kotlin lambda.
        </li>
        <li>
            An empty on-click method for the “ADD A TASK” button, designated by the
            <em>
                activity_main.xml
            </em>
            layout.
        </li>
        <li>
            A private function that initializes the adapter for the list view. Here
            you are using the Kotlin = syntax for a single-expression function.
        </li>
    </ol>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : To learn more about
            <code>
                ListViews
            </code>
            and
            <code>
                Adapters
            </code>
            , refer to the
            <a href="http://developer.android.com/guide/topics/ui/layout/listview.html"
            target="_blank" title="Android Developer docs" sl-processed="1">
                Android Developer docs
            </a>
            .
        </p>
    </div>
    <p>
        Your implementation follows the theory in the previous section — you’re
        doing the layout, adapter and click listener initialization for your activity
        during creation.
    </p>
    <h2>
        Starting an Activity
    </h2>
    <p>
        In its current state, the app is a fairly useless lump of ones and zeros
        because you can’t add anything to the to-do list. You have the power to
        change that, and that’s exactly what you’ll do next.
    </p>
    <p>
        In the
        <em>
            MainActivity.kt
        </em>
        file you have open, add a property to the top of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        ADD_TASK_REQUEST =
        <span class="hljs-number">
            1
        </span>
    </pre>
    <p>
        You’ll use this immutable value to reference your request to add new tasks
        later on.
    </p>
    <p>
        Then add this import statement at the top of the file:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.content.Intent
    </pre>
    <p>
        And add the following implementation for
        <code>
            addTaskClicked()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        intent = Intent(
        <span class="hljs-keyword">
            this
        </span>
        , TaskDescriptionActivity::
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            .
            <span class="hljs-title">
                java
            </span>
            )
        </span>
        startActivityForResult(intent, ADD_TASK_REQUEST)
    </pre>
    <p>
        When the user taps the “ADD A TASK” button, the Android OS calls
        <code>
            addTaskClicked()
        </code>
        . Here you create an
        <code>
            Intent
        </code>
        to launch the
        <code>
            TaskDescriptionActivity
        </code>
        from
        <code>
            MainActivity
        </code>
        .
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : There will be a compile error since you have yet to define
            <code>
                TaskDescriptionActivity
            </code>
            .
        </p>
    </div>
    <p>
        You can start an activity with either
        <code>
            startActivity()
        </code>
        or
        <code>
            startActivityForResult()
        </code>
        . They are similar except that
        <code>
            startActivityForResult()
        </code>
        will result in
        <code>
            onActivityResult()
        </code>
        being called once the
        <code>
            TaskDescriptionActivity
        </code>
        finishes. You’ll implement this callback later so you can know if there
        is a new task to add to your list or not.
    </p>
    <p>
        But first, you need a way to enter new tasks in Forget Me Not — you’ll
        do so by creating the
        <code>
            TaskDescriptionActivity
        </code>
        .
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            :
            <code>
                Intents
            </code>
            are used to start activities and pass data between them. For more information,
            check out the
            <a href="https://www.raywenderlich.com/?p=160019" target="_blank" title="Android: Intents Tutorial"
            sl-processed="1">
                Android: Intents Tutorial
            </a>
        </p>
    </div>
    <h2>
        Creating an Activity
    </h2>
    <p>
        Android Studio makes it very easy to create an activity. Just right-click
        on the package where you want to add the activity — in this case, the package
        is
        <em>
            com.raywenderlich.android.forgetmenot
        </em>
        . Then navigate to
        <em>
            New\Activity
        </em>
        , and choose
        <em>
            Empty Activity
        </em>
        , which is a basic template for an activity:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10-650x391.png"
            alt="" width="650" height="391" class="aligncenter size-large wp-image-165897"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10-650x391.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn10-480x289.png 480w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        On the next screen, enter
        <em>
            TaskDescriptionActivity
        </em>
        as the
        <em>
            Activity Name
        </em>
        and Android Studio will automatically fill the other fields based on that.
    </p>
    <p>
        Click
        <em>
            Finish
        </em>
        and put your hands in the air to celebrate. You’ve just created your first
        activity!
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11-595x500.png"
            alt="" width="595" height="500" class="aligncenter size-large wp-image-165898"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11-595x500.png 595w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11-381x320.png 381w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn11.png 1600w"
            sizes="(max-width: 595px) 100vw, 595px">
        </a>
    </p>
    <p>
        Android Studio will automatically generate the corresponding resources
        needed to create the activity. These are:
    </p>
    <ul>
        <li>
            <em>
                Class
            </em>
            : The class file is named
            <em>
                TaskDescriptionActivity.kt
            </em>
            . This is where you implement the activity’s behavior. This class must
            subclass the
            <a href="http://developer.android.com/reference/android/app/Activity.html"
            title="Activity" target="_blank" sl-processed="1">
                Activity
            </a>
            class or an existing subclass of it, such as
            <a href="https://developer.android.com/reference/android/support/v7/app/AppCompatActivity.html"
            title="AppCompatActivity" target="_blank" sl-processed="1">
                AppCompatActivity
            </a>
            .
        </li>
        <li>
            <em>
                Layout
            </em>
            : The layout file is located under
            <code>
                res/layout/
            </code>
            and named
            <em>
                activity_task_description.xml
            </em>
            . It defines the placement of different UI elements on the screen when
            the activity is created.
        </li>
    </ul>
    <p>
        The layout file created from the
        <em>
            Empty Activity
        </em>
        template in Android Studio 3.0 defaults to using a
        <em>
            ConstraintLayout
        </em>
        for the root view group. For more information on ConstraintLayout, please
        see the android developer docs
        <a href="https://developer.android.com/training/constraint-layout/index.html"
        title="here" target="_blank" sl-processed="1">
            here
        </a>
        .
    </p>
    <p>
        In addition to this, you will see a new addition to your app’s
        <em>
            AndroidManifest.xml
        </em>
        file:
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
                ".TaskDescriptionActivity"
            </span>
            &gt;
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
        The
        <code>
            activity
        </code>
        element declares the activity. Android apps have a strong sense of order,
        so all available activities must be declared in the manifest to ensure
        the app only has control of activities declared here. You don’t want your
        app to accidentally use the wrong activity, or even worse, have it use
        activities that are used by other apps without explicit permission.
    </p>
    <p>
        There are several attributes that you can include in this element to define
        properties for the activity, such as a label or icon, or a theme to style
        the activity’s UI.
    </p>
    <p>
        <code>
            android:name
        </code>
        is the only required attribute. It specifies the activity’s class name
        relative to the app package (hence the period at the beginning).
    </p>
    <p>
        Now build and run the app. When you tap on
        <em>
            ADD A TASK
        </em>
        , you’re presented with your newly generated activity!
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4-282x500.png"
            alt="" width="282" height="500" class="aligncenter size-large wp-image-165882"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4-282x500.png 282w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn4.png 802w"
            sizes="(max-width: 282px) 100vw, 282px">
        </a>
    </p>
    <p>
        Looking good, except for the fact that it’s lacking substance. Now for
        a quick remedy to that!
    </p>
    <p>
        In your newly generated
        <em>
            TaskDescriptionActivity
        </em>
        , paste the following into your class file, overwriting anything else
        except the class declaration and its brackets.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            companion
        </span>
        <span class="hljs-keyword">
            object
        </span>
        {
        <span class="hljs-keyword">
            val
        </span>
        EXTRA_TASK_DESCRIPTION =
        <span class="hljs-string">
            "task"
        </span>
        }
        <span class="hljs-comment">
            // 2
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
        .onCreate(savedInstanceState) setContentView(R.layout.activity_task_description)
        }
        <span class="hljs-comment">
            // 3
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                doneClicked
            </span>
            <span class="hljs-params">
                (view:
                <span class="hljs-type">
                    View
                </span>
                )
            </span>
        </span>
        { }
    </pre>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : You can quickly fix any missing imports that Android Studio complains
            about by placing your cursor on the item and pressing Option-Enter.
        </p>
    </div>
    <p>
        Here, you’ve accomplished the following:
    </p>
    <ol>
        <li>
            Used the Kotlin
            <a href="https://kotlinlang.org/docs/reference/object-declarations.html#companion-objects"
            sl-processed="1">
                companion object
            </a>
            for the class to define attributes common across the class, similar to
            <em>
                static
            </em>
            members in Java.
        </li>
        <li>
            Overriden the
            <code>
                onCreate()
            </code>
            lifecycle method to set the content view for the activity from the layout
            file.
        </li>
        <li>
            Added an empty click handler that will be used to finish the activity.
        </li>
    </ol>
    <p>
        Jump over to your associated layout in
        <em>
            res/layout/activity_task_description.xml
        </em>
        and replace everything with the following:
    </p>
    <pre lang="xml" class="language-xml hljs">
        &lt;?xml version="1.0" encoding="utf-8"?&gt;
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                android.support.constraint.ConstraintLayout
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            <span class="hljs-attr">
                xmlns:app
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res-auto"
            </span>
            <span class="hljs-attr">
                xmlns:tools
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/tools"
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
                android:padding
            </span>
            =
            <span class="hljs-string">
                "@dimen/default_padding"
            </span>
            <span class="hljs-attr">
                tools:context
            </span>
            =
            <span class="hljs-string">
                "com.raywenderlich.android.forgetmenot.TaskDescriptionActivity"
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
                "@+id/descriptionLabel"
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
                android:padding
            </span>
            =
            <span class="hljs-string">
                "@dimen/default_padding"
            </span>
            <span class="hljs-attr">
                android:text
            </span>
            =
            <span class="hljs-string">
                "@string/description"
            </span>
            <span class="hljs-attr">
                app:layout_constraintLeft_toLeftOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintRight_toRightOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toTopOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                EditText
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
                "100dp"
            </span>
            <span class="hljs-attr">
                android:inputType
            </span>
            =
            <span class="hljs-string">
                "textMultiLine"
            </span>
            <span class="hljs-attr">
                android:padding
            </span>
            =
            <span class="hljs-string">
                "@dimen/default_padding"
            </span>
            <span class="hljs-attr">
                app:layout_constraintLeft_toLeftOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintRight_toRightOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "@+id/descriptionLabel"
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
                "@+id/doneButton"
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
                android:onClick
            </span>
            =
            <span class="hljs-string">
                "doneClicked"
            </span>
            <span class="hljs-attr">
                android:padding
            </span>
            =
            <span class="hljs-string">
                "@dimen/default_padding"
            </span>
            <span class="hljs-attr">
                android:text
            </span>
            =
            <span class="hljs-string">
                "@string/done"
            </span>
            <span class="hljs-attr">
                app:layout_constraintLeft_toLeftOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "@+id/descriptionText"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                android.support.constraint.ConstraintLayout
            </span>
            &gt;
        </span>
    </pre>
    <p>
        Here you change the layout so there is a
        <code>
            TextView
        </code>
        prompting for a task description, an
        <code>
            EditText
        </code>
        for the user to input the description, and a Done button to save the new
        task.
    </p>
    <p>
        Run the app again, tap
        <em>
            ADD A TASK
        </em>
        and your new screen will look a lot more interesting.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-165883"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn5.png 801w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        Stopping an Activity
    </h2>
    <p>
        Just as important as starting an activity with all the right methods is
        properly stopping it.
    </p>
    <p>
        In
        <em>
            TaskDescriptionActivity.kt
        </em>
        , add these imports, including one for Kotlin Android Extensions:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
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
        kotlinx.android.synthetic.main.activity_task_description.*
    </pre>
    <p>
        Then add the following to
        <code>
            doneClicked()
        </code>
        , which is called when the
        <em>
            Done
        </em>
        button is tapped in this activity:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            val
        </span>
        taskDescription = descriptionText.text.toString()
        <span class="hljs-keyword">
            if
        </span>
        (!taskDescription.isEmpty()) {
        <span class="hljs-comment">
            // 2
        </span>
        <span class="hljs-keyword">
            val
        </span>
        result = Intent() result.putExtra(EXTRA_TASK_DESCRIPTION, taskDescription)
        setResult(Activity.RESULT_OK, result) }
        <span class="hljs-keyword">
            else
        </span>
        {
        <span class="hljs-comment">
            // 3
        </span>
        setResult(Activity.RESULT_CANCELED) }
        <span class="hljs-comment">
            // 4
        </span>
        finish()
    </pre>
    <p>
        You can see a few things are happening here:
    </p>
    <ol>
        <li>
            You retrieve the task description from the
            <code>
                descriptionText
            </code>
            <code>
                EditText
            </code>
            , where Kotlin Android Extensions has again been used to get references
            to view fields.
        </li>
        <li>
            You create a result
            <code>
                Intent
            </code>
            to pass back to
            <code>
                MainActivity
            </code>
            if the task description retrieved in step one is not empty. Then you bundle
            the task description with the intent and set the activity result to
            <code>
                RESULT_OK
            </code>
            , indicating that the user successfully entered a task.
        </li>
        <li>
            If the user has not entered a task description, you set the activity result
            to
            <code>
                RESULT_CANCELED
            </code>
            .
        </li>
        <li>
            Here you close the activity.
        </li>
    </ol>
    <p>
        Once you call
        <code>
            finish()
        </code>
        in step four, the callback
        <code>
            onActivityResult()
        </code>
        will be called in
        <code>
            MainActivity
        </code>
        — in turn, you need to add the task to the to-do list.
    </p>
    <p>
        Add the following method to
        <em>
            MainActivity.kt
        </em>
        , right after
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onActivityResult
            </span>
            <span class="hljs-params">
                (requestCode:
                <span class="hljs-type">
                    Int
                </span>
                , resultCode:
                <span class="hljs-type">
                    Int
                </span>
                ,
                <span class="hljs-keyword">
                    data
                </span>
                :
                <span class="hljs-type">
                    Intent
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            if
        </span>
        (requestCode == ADD_TASK_REQUEST) {
        <span class="hljs-comment">
            // 2
        </span>
        <span class="hljs-keyword">
            if
        </span>
        (resultCode == Activity.RESULT_OK) {
        <span class="hljs-comment">
            // 3
        </span>
        <span class="hljs-keyword">
            val
        </span>
        task =
        <span class="hljs-keyword">
            data
        </span>
        ?.getStringExtra(TaskDescriptionActivity.EXTRA_TASK_DESCRIPTION) task?.let
        { taskList.add(task)
        <span class="hljs-comment">
            // 4
        </span>
        adapter.notifyDataSetChanged() } } } }
    </pre>
    <p>
        Let’s take this step-by-step:
    </p>
    <ol>
        <li>
            You check the
            <code>
                requestCode
            </code>
            to ensure the activity result is indeed for your add task request you
            started with
            <code>
                TaskDescriptionActivity
            </code>
            .
        </li>
        <li>
            You make sure the
            <code>
                resultCode
            </code>
            is
            <code>
                RESULT_OK
            </code>
            — the standard activity result for a successful operation.
        </li>
        <li>
            Here you extract the task description from the result intent and, after
            a null check with the
            <code>
                let
            </code>
            function, add it to your list.
        </li>
        <li>
            Finally, you call
            <code>
                notifyDataSetChanged()
            </code>
            on your list adapter. In turn, it notifies the
            <code>
                ListView
            </code>
            about changes in your data model so it can trigger a refresh of its view.
        </li>
    </ol>
    <p>
        Build and run the project to see it in action. After the app starts, tap
        <em>
            ADD A TASK
        </em>
        . This will bring up a new screen that lets you enter a task. Now add
        a description and tap
        <em>
            Done
        </em>
        . The screen will close and the new task will be on your list:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1-596x500.png"
            alt="" width="596" height="500" class="aligncenter size-large wp-image-165952"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1-596x500.png 596w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn12-1-381x320.png 381w"
            sizes="(max-width: 596px) 100vw, 596px">
        </a>
    </p>
    <h2>
        Registering Broadcast Receivers
    </h2>
    <p>
        Every to-do list needs to have a good grasp on date and time, so a time
        display should be the next thing you add to your app. Open
        <em>
            MainActivity.kt
        </em>
        and add the following after the existing property declarations at the
        top:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        tickReceiver
        <span class="hljs-keyword">
            by
        </span>
        lazy { makeBroadcastReceiver() }
    </pre>
    <p>
        Then add a
        <em>
            companion object
        </em>
        near the top of
        <code>
            MainActivity
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            companion
        </span>
        <span class="hljs-keyword">
            object
        </span>
        {
        <span class="hljs-keyword">
            private
        </span>
        const
        <span class="hljs-keyword">
            val
        </span>
        LOG_TAG =
        <span class="hljs-string">
            "MainActivityLog"
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                getCurrentTimeStamp
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        : String {
        <span class="hljs-keyword">
            val
        </span>
        simpleDateFormat = SimpleDateFormat(
        <span class="hljs-string">
            "yyyy-MM-dd HH:mm"
        </span>
        , Locale.US)
        <span class="hljs-keyword">
            val
        </span>
        now = Date()
        <span class="hljs-keyword">
            return
        </span>
        simpleDateFormat.format(now) } }
    </pre>
    <p>
        And initialize the
        <code>
            tickReceiver
        </code>
        by adding the following to the bottom of
        <code>
            MainActivity
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                makeBroadcastReceiver
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        : BroadcastReceiver {
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-keyword">
            object
        </span>
        : BroadcastReceiver() {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onReceive
            </span>
            <span class="hljs-params">
                (context:
                <span class="hljs-type">
                    Context
                </span>
                , intent:
                <span class="hljs-type">
                    Intent
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (intent?.action == Intent.ACTION_TIME_TICK) { dateTimeTextView.text =
        getCurrentTimeStamp() } } } }
    </pre>
    <p>
        Here, you create a
        <em>
            BroadcastReceiver
        </em>
        that sets the date and time on the screen if it receives a time change
        broadcast from the system. You use
        <code>
            getCurrentTimeStamp()
        </code>
        , which is a utility method in your activity, to format the current date
        and time.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : If you’re not familiar with
            <code>
                BroadcastReceivers
            </code>
            , you should refer to the
            <a href="http://developer.android.com/reference/android/content/BroadcastReceiver.html"
            title="Android Developer documentation" target="_blank" sl-processed="1">
                Android Developer documentation
            </a>
            .
        </p>
    </div>
    <p>
        Next add the following methods to
        <code>
            MainActivity
        </code>
        underneath
        <code>
            onCreate()
        </code>
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onResume
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onResume()
        <span class="hljs-comment">
            // 2
        </span>
        dateTimeTextView.text = getCurrentTimeStamp()
        <span class="hljs-comment">
            // 3
        </span>
        registerReceiver(tickReceiver, IntentFilter(Intent.ACTION_TIME_TICK))
        }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onPause
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 4
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onPause()
        <span class="hljs-comment">
            // 5
        </span>
        <span class="hljs-keyword">
            try
        </span>
        { unregisterReceiver(tickReceiver) }
        <span class="hljs-keyword">
            catch
        </span>
        (e: IllegalArgumentException) { Log.e(MainActivity.LOG_TAG,
        <span class="hljs-string">
            "Time tick Receiver not registered"
        </span>
        , e) } }
    </pre>
    <p>
        Here you do a few things:
    </p>
    <ol>
        <li>
            You call
            <code>
                onResume()
            </code>
            on the superclass.
        </li>
        <li>
            You update the date and time
            <code>
                TextView
            </code>
            with the current time stamp, because the broadcast receiver is not currently
            registered.
        </li>
        <li>
            You then register the broadcast receiver in
            <code>
                onResume()
            </code>
            . This ensures it will receive the broadcasts for
            <a href="http://developer.android.com/reference/android/content/Intent.html#ACTION_TIME_TICK"
            title="ACTION_TIME_TICK" target="_blank" sl-processed="1">
                ACTION_TIME_TICK
            </a>
            . These are sent every minute after the time changes.
        </li>
        <li>
            In
            <code>
                onPause()
            </code>
            , you first call
            <code>
                onPause()
            </code>
            on the superclass.
        </li>
        <li>
            You then unregister the broadcast receiver in
            <code>
                onPause()
            </code>
            , so the activity no longer receives the time change broadcasts while
            paused. This cuts down unnecessary system overhead.
        </li>
    </ol>
    <p>
        Build and run the app. Now you should now see the current date and time
        at the top of the screen. Even if you navigate to the add task screen and
        come back, the time still gets updated.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-165879"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn1.png 800w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        Persisting State
    </h2>
    <p>
        Every to-do list is good at remembering what you need to do, except for
        your friend Forget Me Not. Unfortunately, the app is quite forgetful at
        the moment. See it for yourself.
    </p>
    <p>
        Open the app and follow these steps.
    </p>
    <ol>
        <li>
            Tap
            <em>
                ADD A TASK
            </em>
            .
        </li>
        <li>
            Enter “Replace regular with decaf in the breakroom” as the task description
            and tap
            <em>
                Done
            </em>
            . You’ll see your new task in the list.
        </li>
        <li>
            Close the app from the recent apps.
        </li>
        <li>
            Open the app again.
        </li>
    </ol>
    <p>
        You can see that it forgot about your evil plans.
    </p>
    <h3>
        Persisting Data Between Launches
    </h3>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        , and add the following properties to the top of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        PREFS_TASKS =
        <span class="hljs-string">
            "prefs_tasks"
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        KEY_TASKS_LIST =
        <span class="hljs-string">
            "tasks_list"
        </span>
    </pre>
    <p>
        And add the following underneath the rest of your activity lifecycle methods.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onStop
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onStop()
        <span class="hljs-comment">
            // Save all data which you want to persist.
        </span>
        <span class="hljs-keyword">
            val
        </span>
        savedList = StringBuilder()
        <span class="hljs-keyword">
            for
        </span>
        (task
        <span class="hljs-keyword">
            in
        </span>
        taskList) { savedList.append(task) savedList.append(
        <span class="hljs-string">
            ","
        </span>
        ) } getSharedPreferences(PREFS_TASKS, Context.MODE_PRIVATE).edit() .putString(KEY_TASKS_LIST,
        savedList.toString()).apply() }
    </pre>
    <p>
        Here you build a comma separated string with all the task descriptions
        in your list, and then you save the string to
        <a href="http://developer.android.com/reference/android/content/SharedPreferences.html"
        title="Shared Preferences" target="_blank" sl-processed="1">
            SharedPreferences
        </a>
        in the
        <code>
            onStop()
        </code>
        callback. As mentioned earlier,
        <code>
            onStop()
        </code>
        is a good place to save data that you want to persist across app uses.
    </p>
    <p>
        Next add the following to
        <code>
            onCreate()
        </code>
        below the existing initialization code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        savedList = getSharedPreferences(PREFS_TASKS, Context.MODE_PRIVATE).getString(KEY_TASKS_LIST,
        <span class="hljs-literal">
            null
        </span>
        )
        <span class="hljs-keyword">
            if
        </span>
        (savedList !=
        <span class="hljs-literal">
            null
        </span>
        ) {
        <span class="hljs-keyword">
            val
        </span>
        items = savedList.split(
        <span class="hljs-string">
            ","
        </span>
        .toRegex()).dropLastWhile { it.isEmpty() }.toTypedArray() taskList.addAll(items)
        }
    </pre>
    <p>
        Here you read the saved list from the
        <code>
            SharedPreferences
        </code>
        and initialize
        <code>
            taskList
        </code>
        by converting the retrieved comma separated string to a typed array.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : You used
            <code>
                SharedPreferences
            </code>
            since you were only saving primitive data types. For more complex data
            you can use a variety of
            <a href="http://developer.android.com/guide/topics/data/data-storage.html"
            sl-processed="1">
                storage options
            </a>
            available on Android.
        </p>
    </div>
    <p>
        Now, build and run the app. Add a task, close and reopen the app. Do you
        see a difference? You are now able to retain tasks in your list!
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-165880"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn2.png 799w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        Configuration Changes
    </h2>
    <p>
        You need the ability to delete entries from Forget Me Not.
    </p>
    <p>
        Still in
        <em>
            MainActivity.kt
        </em>
        , at the bottom of the class add:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                taskSelected
            </span>
            <span class="hljs-params">
                (position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        AlertDialog.Builder(
        <span class="hljs-keyword">
            this
        </span>
        )
        <span class="hljs-comment">
            // 2
        </span>
        .setTitle(R.string.alert_title)
        <span class="hljs-comment">
            // 3
        </span>
        .setMessage(taskList[position]) .setPositiveButton(R.string.delete, {
        _, _ -&gt; taskList.removeAt(position) adapter.notifyDataSetChanged() })
        .setNegativeButton(R.string.cancel, { dialog, _ -&gt; dialog.cancel() })
        <span class="hljs-comment">
            // 4
        </span>
        .create()
        <span class="hljs-comment">
            // 5
        </span>
        .show() }
    </pre>
    <p>
        In a nutshell, you’re creating and showing an alert dialog when you select
        a task from the list. Here is the step-by-step explanation:
    </p>
    <ol>
        <li>
            You create an
            <code>
                AlertDialog.Builder
            </code>
            which facilitates the creation of an
            <code>
                AlertDialog
            </code>
            .
        </li>
        <li>
            You set the alert dialog title.
        </li>
        <li>
            You set the alert dialog message to be the description of the selected
            task. Then you also implement the
            <code>
                PositiveButton
            </code>
            to remove the item from the list and refresh it, and the
            <code>
                NegativeButton
            </code>
            to dismiss the dialog.
        </li>
        <li>
            You create the alert dialog.
        </li>
        <li>
            You display the alert dialog to the user.
        </li>
    </ol>
    <p>
        Update the
        <code>
            OnItemClickListener
        </code>
        of the
        <code>
            taskListView
        </code>
        in
        <code>
            onCreate()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        taskListView.onItemClickListener = AdapterView.OnItemClickListener { _,
        _, position, _ -&gt; taskSelected(position) }
    </pre>
    <p>
        Your app won’t compile though until you define some strings. It’s good
        practice to keep text you want in your app separate from the code. The
        reason is so that you can easily change it, which is especially useful
        for text that you use in multiple places. It’s also handy for those times
        you need to translate your app into another language.
    </p>
    <p>
        To configure the strings, open
        <em>
            res/values/strings.xml
        </em>
        and within the
        <code>
            resources
        </code>
        element add:
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
                "alert_title"
            </span>
            &gt;
        </span>
        Task
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
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
                "delete"
            </span>
            &gt;
        </span>
        Delete
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
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
                "cancel"
            </span>
            &gt;
        </span>
        Cancel
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
    </pre>
    <p>
        Build and run the app. Tap on one of the tasks. You’ll see an alert dialog
        with options to
        <em>
            CANCEL
        </em>
        or
        <em>
            DELETE
        </em>
        the task from the list:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3-280x500.png"
            alt="" width="280" height="500" class="aligncenter size-large wp-image-165881"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3-280x500.png 280w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn3.png 796w"
            sizes="(max-width: 280px) 100vw, 280px">
        </a>
    </p>
    <p>
        Now try rotating the device. (Make sure you have rotation in the device
        settings set to auto-rotate.)
    </p>
    <p>
        As soon as you rotate the device, the alert dialog is dismissed. This
        makes for an unreliable, undesirable user experience — users don’t like
        it when things just vanish from their screen without reason.
    </p>
    <h3>
        Handling Configuration Changes
    </h3>
    <p>
        Configuration changes, such as rotation, keyboard visibility and so on,
        cause an activity to shut down and restart. You can find the full list
        of system events that cause an activity to be recreated
        <a href="http://developer.android.com/guide/topics/manifest/activity-element.html#config"
        title="here" target="_blank" sl-processed="1">
            here
        </a>
        .
    </p>
    <p>
        There are a couple of ways you can handle a configuration change.
    </p>
    <p>
        One way is as follows. In
        <em>
            AndroidManifest.xml
        </em>
        , find the start tag:
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
                ".MainActivity"
            </span>
            &gt;
        </span>
    </pre>
    <p>
        And change it to:
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
                ".MainActivity"
            </span>
            <span class="hljs-attr">
                android:configChanges
            </span>
            =
            <span class="hljs-string">
                "orientation|screenSize"
            </span>
            &gt;
        </span>
    </pre>
    <p>
        Here, you declare that your
        <code>
            MainActivity
        </code>
        will handle any configuration changes that arise from a change in orientation
        or screen size. This simple line prevents a restart of your activity by
        the system, and it passes the work to
        <code>
            MainActivity
        </code>
        .
    </p>
    <p>
        You can then handle these configuration changes by implementing
        <code>
            onConfigurationChanged()
        </code>
        . In
        <em>
            MainActivity.kt
        </em>
        , add the following method after
        <code>
            onStop()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onConfigurationChanged
            </span>
            <span class="hljs-params">
                (newConfig:
                <span class="hljs-type">
                    Configuration
                </span>
                ?)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onConfigurationChanged(newConfig) }
    </pre>
    <p>
        Here you’re just calling the superclass’s
        <code>
            onConfigurationChanged()
        </code>
        method since you’re not updating or resetting any elements based on screen
        rotation or size.
    </p>
    <p>
        <code>
            onConfigurationChanged()
        </code>
        is passed a
        <code>
            Configuration
        </code>
        object that contains the updated device configuration.
    </p>
    <p>
        By reading fields in this
        <code>
            newConfig
        </code>
        , you can determine the new configuration and make appropriate changes
        to update the resources used in your interface.
    </p>
    <p>
        Now, build and run the app and rotate the device again. This time, the
        dialog stays in place until you dismiss it.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9-650x365.png"
            alt="" width="650" height="365" class="aligncenter size-large wp-image-165887"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9-650x365.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9-480x270.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/06/fmn9.png 1423w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        An alternative way to handle configuration changes is to retain a stateful
        object that’s carried forward to the recreated instance of your activity.
        You can accomplish this by implementing the
        <code>
            onSaveInstanceState()
        </code>
        callback.
    </p>
    <p>
        When you do this, the system saves your activity’s state in a
        <code>
            Bundle
        </code>
        , and you can restore it when you implement the corresponding
        <code>
            onRestoreInstanceState()
        </code>
        callback. However, the
        <code>
            Bundle
        </code>
        is not designed to hold large data sets such as bitmaps, and it can only
        store data that is
        <a href="http://developer.android.com/reference/java/io/Serializable.html"
        title=" serializable " target="_blank" sl-processed="1">
            serializable
        </a>
        .
    </p>
    <p>
        The downside of the stateful object solution is that serializing and deserializing
        the data during a configuration change can come at a high cost. It can
        consume a lot of memory and slow down the activity restart process.
    </p>
    <p>
        In such instances, retaining a
        <code>
            Fragment
        </code>
        is currently the most preferable way to handle a configuration change.
        You can learn more about fragments and how to use them to retain information
        when your activity is restarted in our
        <a href="https://www.raywenderlich.com/149112/android-fragments-tutorial-introduction"
        title="Android Fragments Tutorial" target="_blank" sl-processed="1">
            Android Fragments Tutorial
        </a>
        .
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
        Congratulations! You have just learned the basics of using activities
        in Android and now have an excellent understanding of the ever-important
        activity lifecycle.
    </p>
    <p>
        You covered quite a few concepts, including:
    </p>
    <ul>
        <li>
            How to create an activity
        </li>
        <li>
            How to stop an activity
        </li>
        <li>
            How to persist data when an activity stops
        </li>
        <li>
            How to work around a configuration change
        </li>
    </ul>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/09/congratulations.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2015/09/congratulations-467x320.png"
            alt="congratulations" width="467" height="320" class="aligncenter size-medium wp-image-116870">
        </a>
    </p>
    <p>
        You can download the completed project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/07/ForgetMeNot-final.zip"
        title="here" sl-processed="1">
            here
        </a>
        . If you’re still hungry for more, check out Google’s
        <a href="http://developer.android.com/reference/android/app/Activity.html#ActivityLifecycle"
        title="documentation" target="_blank" sl-processed="1">
            documentation
        </a>
        .
    </p>
</div>