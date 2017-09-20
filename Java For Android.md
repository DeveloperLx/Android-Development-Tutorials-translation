# Java在Android中的应用
---
#### [原文地址](https://www.raywenderlich.com/110452/java-for-android) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/08/android_w_java.png"
        sl-processed="1">
            <img class="alignright size-full wp-image-112357" src="https://koenig-media.raywenderlich.com/uploads/2015/08/android_w_java.png"
            alt="Android with Java" width="250" height="250" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/android_w_java.png 250w, https://koenig-media.raywenderlich.com/uploads/2015/08/android_w_java-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2015/08/android_w_java-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2015/08/android_w_java-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2015/08/android_w_java-128x128.png 128w"
            sizes="(max-width: 250px) 100vw, 250px">
        </a>
    </p>
    <p>
        尽管大量的语言都可以用来开发Android app，但Google推荐开发者使用
        <em>
            Java
        </em>
        语言。然而，和你在其它平台上所用到的Java不同，作为一个Android开发者用到的Java会有一些微妙的差别和特殊性，它们是非常重要的，可能会把你的脑袋绕晕。
    </p>
    <p>
        在本教程中，你将对Android世界中的Java进行一次快速的旅程，发现更多它所提供的特性。你还将了解到：
    </p>
    <ul>
        <li>
            Android的app和PC上的Java程序有什么区别
        </li>
        <li>
            在Android中如何应用
            <em>
                面向对象编程
            </em>
        </li>
        <li>
            Java的
            <em>
                Interface
            </em>
            是什么，以及你如何使用它来同你app的其它部分进行交流
        </li>
        <li>
            什么是Java的
            <em>
                Annotations
            </em>
            ，以及它们如何为你的部分app提供额外的信息
        </li>
    </ul>
    <p>
        本教程假定你已经熟悉了至少一种的面向对象编程语言。当然这并不是绝对必要的，但这将有助于你理解在本教程中所讨论到的概念。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：这篇文章和标准的raywenderlich.com教程会有一点不同，它会讨论很多高级的话题，而不是一个让你跟着来做的示例app。我们推荐你在着手开发Android app之前首先进行阅读，以便你能够快速地适应Android中独特的Java代码。
        </p>
    </div>
    <p>
        用你最喜爱的“Java”进入到这门语言的魔法旅程 - Android风格！
    </p>
    <h2>
        Java在Android中的应用
    </h2>
    <p>
        有趣的事实：Android并不会使用“pure”的Java！这听起来很奇怪，因为当你对比传统的程序和Android app中的代码时，你会纠结于其中的差别。
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/08/no_java_rager.png"
        sl-processed="1">
            <img class="aligncenter size-medium wp-image-112359" src="https://koenig-media.raywenderlich.com/uploads/2015/08/no_java_rager-288x320.png"
            alt="No Java, What?" width="216" height="240" srcset="https://koenig-media.raywenderlich.com/uploads/2015/08/no_java_rager-288x320.png 288w, https://koenig-media.raywenderlich.com/uploads/2015/08/no_java_rager.png 373w"
            sizes="(max-width: 216px) 100vw, 216px">
        </a>
    </p>
    <p>
        尽管对于有经验的Java开发者来说，编写和开发Android app会让他们感到比较熟悉，但当你编译和运行项目的时候，这种熟悉感还是会突然中止。原因是Android在编译过程中，处理app的方式处于你未知的领域。
    </p>
    <p>
        Java’s major appeal is its ability to “Write once, run everywhere”. This
        language is sold as the silver bullet to the expensive process&nbsp;of
        porting software from one platform to another.
    </p>
    <p>
        This veritable marvel of software engineering is made possible thanks
        to what happens when a Java program compiles.
    </p>
    <p>
        对于大多数其它的语言，编译器会首先连接和优化程序，然后将它翻译为
        <em>
            机器语言
        </em>
        ，也就是当你运行程序的时候，计算机可以理解和执行的指令集。
    </p>
    <p>
        尽管执行机器代码是非常快速的，但由于会依赖于它所运行的平台，因而会受到一些限制。如果你曾好奇，为何一个为iOS平台所写的程序无法运行在Windows上，这是其中的原因之一。
    </p>
    <p>
        Java与之不同；它会将源码翻译为一种中间形式的叫做
        <em>
            Bytecode
        </em>
        的代码，而不是机器码。它会创建一系列的类似于机器码的指令集，它定位于运行在
        <em>
            虚拟机
        </em>
        （VM）上而非指定架构的平台。
    </p>
    <p>
        使用了虚拟机，就意味着只要能够阅读和翻译Bytecode的指令集，这个程序就可以很愉快地运行相应的平台上了，这就确保了跨平台的兼容性。
    </p>
    <p>
        现在你就懂了，为何大多数的Java程序，会在你还没有的情况下，提示你下载Java Runtime Environment（JRE）- 它是大多数平台默认的VM程序。e it – it’s the default
        VM for the majority of platforms.
    </p>
    <h2>
        Android中的Java...有一点不同
    </h2>
    <p>
        Compiling an app for Android follows the same path as converting Java
        files into Bytecode. Except that it doesn’t. When the app (composed of
        Bytecode) installs on a device, a second step occurs during installation.
        The app’s Bytecode is converted into machine code that’s optimized for
        that Android device, improving the app’s runtime performance. This process
        is known as
        <em>
            Ahead of Time compilation
        </em>
        (AoT) and is made possible by the
        <em>
            Android Runtime
        </em>
        (ART) virtual machine.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            :
            <em>
                Ahead of Time Compilation
            </em>
            (AoT) is a concept used across many programming languages. You can read
            more about it
            <a title="on Wikipedia" href="https://en.wikipedia.org/wiki/Ahead-of-time_compilation"
            target="_blank" sl-processed="1">
                on Wikipedia
            </a>
            .
        </p>
    </div>
    <p>
        <em>
            AoT
        </em>
        compilation only occurs in Android KitKat (4.4) and above, but it also
        provides backwards compatibility. Prior versions of Android relied on another
        virtual machine known as
        <em>
            Dalvik
        </em>
        . Like ART, Dalvik made changes to the Java Bytecode, converting it into
        a specific form that made various efficiency changes to optimize the app
        for the kinds of low-powered devices Android was originally designed for.
    </p>
    <p>
        However, unlike ART, Dalvik didn’t compile the Bytecode into machine code
        until runtime — using an approach&nbsp;known as
        <em>
            Just in Time
        </em>
        compilation (JIT). This process is much closer to that used&nbsp;in Java
        Virtual Environments on a PC.
    </p>
    <p>
        Android Froyo (2.2) saw an improvement when Dalvik gained the ability
        to profile the app during runtime for commonly used portions of Dalvik
        Bytecode. These instructions were then permanently translated into machine
        code by Dalvik to boost the app’s speed.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : Trace Based Just in Time Compilation (JIT) is not unique to Java, and
            once again,&nbsp;
            <a title="Wikipedia" href="https://en.wikipedia.org/wiki/Tracing_just-in-time_compilation"
            target="_blank" sl-processed="1">
                Wikipedia
            </a>
            does a nice job of explaining it.
        </p>
    </div>
    <p>
        In either case of Android app compilation, it’s the conversion of Bytecode
        that makes the Java written for Android less “pure”.
    </p>
    <p>
        The changes to the Bytecode constrain the app’s portability, thereby negating
        one of the promises of Java language: “Write once, run everywhere”.
    </p>
    <p>
        Another way Android diverges from Java is with the availability of standard
        libraries. Java is so portable is because it relies on a standardized collection
        of libraries it can use across various platforms, such as networking and
        UI libraries.
    </p>
    <p>
        Android offers a subset of what Java provides, and what it does provide
        is
        <i>
            only
        </i>
        for Android.
    </p>
    <p>
        &nbsp;
    </p>
    <h2>
        Walking Through Java on Android
    </h2>
    <p>
        Android makes extensive use of Java’s adoption of the
        <em>
            Object Oriented Programming
        </em>
        paradigm, and it’s designed to work around the concepts of
        <em>
            encapsulation
        </em>
        ,
        <em>
            inheritance
        </em>
        and
        <em>
            polymorphism
        </em>
        . You utilize all of these when you build apps.
    </p>
    <p>
        All objects in Android inherit from the
        <code>
            Object
        </code>
        class in some form, building upon its functions to provide specialized
        behaviour and features. Take a look at some of the objects available through
        the
        <a title="Android API" href="http://developer.android.com/reference/android/package-summary.html"
        target="_blank" sl-processed="1">
            Android API
        </a>
        ; you can see the hierarchy that each object inherits, and all of them
        eventually inherit
        <code>
            Object
        </code>
        .
    </p>
    <h3>
        Not-So-Paranormal Activity
    </h3>
    <p>
        The
        <code>
            Activity
        </code>
        class is an object dedicated to a specific screen of an app. Think of
        it as something that handles and displays all the associated work that
        drives the functionality for that screen.
    </p>
    <p>
        Since your app will have at least have one or two functions, it would
        make sense to spread them across a few screens so your interface isn’t
        cluttery. To create a screen, you
        <em>
            create a new Java class
        </em>
        and have it extend
        <code>
            Activity
        </code>
        like so:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainMenuActivity
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                Activity
            </span>
        </span>
        { }
    </pre>
    <p>
        Just like that, you stub out an area of your app for a specific purpose.
        Your
        <code>
            Activity
        </code>
        doesn’t yet know its purpose because you haven’t told it what to do or
        how to appear.
    </p>
    <p>
        You can create your activity’s appearance, aka
        <em>
            Layout
        </em>
        , one of two ways:
    </p>
    <ul>
        <li>
            Declare it in an XML file
        </li>
        <li>
            Programatically create it in a Java class
        </li>
    </ul>
    <p>
        The more common approach is creating the layout in an XML file. You’d
        take the programmatic approach if you need to tailor some aspect of your
        layout.
    </p>
    <p>
        This article won’t take you take through either process for creating layouts,
        but understanding how to do it is helpful if you intend to write apps for
        Android, because it’s a regular task. Learn more about layouts from
        <a title="Android's documentation" href="http://developer.android.com/guide/topics/ui/declaring-layout.html"
        target="_blank" sl-processed="1">
            Android’s documentation
        </a>
        .
    </p>
    <p>
        The following code snippet&nbsp;demonstrates how you would specify that
        an activity should determine its appearance using the XML layout in&nbsp;
        <em>
            res/layout/activity_main_menu.xml
        </em>
        .
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainMenuActivity
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                Activity
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                protected
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onCreate
            </span>
            <span class="hljs-params">
                (Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState);
        <span class="hljs-comment">
            // 2
        </span>
        setContentView(R.layout.activity_main_menu);
        <span class="hljs-comment">
            // 3
        </span>
        } }
    </pre>
    <p>
        Take a look at it bit-by-bit:
    </p>
    <ol>
        <li>
            First, you override
            <code>
                onCreate()
            </code>
            , one of the methods available to you in an
            <code>
                Activity
            </code>
            . It runs when your
            <code>
                Activity
            </code>
            is created, giving you ample time to set up anything you need. This is
            often the first method you create for an
            <code>
                Activity
            </code>
            .
        </li>
        <li>
            You then call the superclass implementation of
            <code>
                onCreate()
            </code>
            to ensure any set up required for the
            <code>
                Activity
            </code>
            is performed. This is a required step. If you don’t do it, your app will
            crash with an exception warning.
        </li>
        <li>
            Finally, you tell your
            <code>
                Activity
            </code>
            to show a screen by using
            <code>
                setContentView()
            </code>
            , passing in a layout that’s referenced from
            <code>
                R
            </code>
            .
        </li>
    </ol>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            :
            <code>
                R
            </code>
            is a special class generated by Android for your app’s various assets.
            These could be a screen layout like you see above, or it could be something
            like a localized string, image or animation. Android generates
            <code>
                R
            </code>
            while building, so you shouldn’t modify it at all. More information about
            it is available from
            <a title="developer.android.com" href="http://developer.android.com/guide/topics/resources/accessing-resources.html"
            target="_blank" sl-processed="1">
                developer.android.com
            </a>
            .
        </p>
    </div>
    <p>
        The XML layout will most likely include elements which make up the UI.
        You access these elements though&nbsp;
        <code>
            R
        </code>
        &nbsp;in an&nbsp;
        <code>
            Activity
        </code>
        , like this:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainMenuActivity
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                Activity
            </span>
        </span>
        { TextView mTextView; Button mButton;
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                protected
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onCreate
            </span>
            <span class="hljs-params">
                (Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState); setContentView(R.layout.activity_main_menu);
        mTextView = (TextView) findViewById(R.id.textview_main_menu); mButton =
        (Button) findViewById(R.id.button_main_menu); } }
    </pre>
    <p>
        <code>
            <span style="font-family: Georgia, 'Times New Roman', 'Bitstream Charter', Times, serif;">
                The key aspect is&nbsp;
            </span>
            findViewById()
        </code>
        , which searches the XML layout for view objects specified by their ID,
        allowing you to manipulate them from Java.&nbsp;Note that you have to&nbsp;typecast
        each call into an appropriate&nbsp;
        <code>
            View
        </code>
        subclass, since&nbsp;
        <code>
            findViewById()
        </code>
        only returns a&nbsp;
        <code>
            View
        </code>
        object—the root object from which all UI components inherit.
    </p>
    <p>
        Once you have access to the individual view elements within the Java code,
        you would be able to interact with them and make them perform actions as
        you see fit. The following code segment demonstrates adding an action for
        when the user clicks a button:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainMenuActivity
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                Activity
            </span>
        </span>
        { TextView mTextView; Button mButton;
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                protected
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onCreate
            </span>
            <span class="hljs-params">
                (Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState); setContentView(R.layout.activity_main_menu);
        mTextView = (TextView) findViewById(R.id.textview_main_menu); mButton =
        (Button) findViewById(R.id.button_main_menu); mButton.setOnClickListener(
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
                (View v)
            </span>
        </span>
        { mTextView.setText(
        <span class="hljs-string">
            "Hello World"
        </span>
        ); } }); } }
    </pre>
    <p>
        The code above runs
        <code>
            onClick()
        </code>
        every time your button is clicked. In
        <code>
            onClick()
        </code>
        , you tell your
        <code>
            TextView
        </code>
        , initially empty, to show the text “Hello World”.
    </p>
    <p>
        Using this simple approach to link views to your class and provide actions
        to perform on a certain event, you can build highly complex activities.
        Remember these basic steps, and you’ll be on your way to grasping how Java
        and Android come together.
    </p>
    <h2>
        Lets Go Modeling
    </h2>
    <p>
        Models are integral to writing an Android app. Not to be confused with
        the kind of model that struts down the catwalk, they allow you to create
        objects that consist of data structures and functionality that you can
        utilize to great effect.
    </p>
    <p>
        Models exist in separate classes from your UI classes. This separation
        not only helps keep your app organized, but it conforms to the idea of
        encapsulation in Object Oriented Programming.
    </p>
    <p>
        A typical model looks something like this:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                ReminderList
            </span>
        </span>
        {
        <span class="hljs-keyword">
            private
        </span>
        ArrayList mReminderArrayList;
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-title">
                ReminderList
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        { mReminderArrayList =
        <span class="hljs-keyword">
            new
        </span>
        ArrayList&lt;&gt;(); }
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                setReminderArrayList
            </span>
            <span class="hljs-params">
                (ArrayList reminderArrayList)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            this
        </span>
        .mReminderArrayList = reminderArrayList; }
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            ArrayList
            <span class="hljs-title">
                getReminderArrayList
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            return
        </span>
        mReminderArrayList; }
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                removeLastItemFromList
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (!mReminderArrayList.isEmpty()) { mReminderArrayList.remove(mReminderArrayList.size()
        -
        <span class="hljs-number">
            1
        </span>
        ); } } }
    </pre>
    <p>
        No mentions of a view or activity in sight! Just data structures, raw
        data types and various functions. In fact this is just a Plain Old Java
        Object (POJO) — no secret sauce at all. This model is perfectly encapsulated,
        meaning you could drop it into any Android app and start using it straight
        away.
    </p>
    <p>
        When creating objects in other OOP based languages, it’s conventional
        to create instance variables that are defined globally within the context
        of the object.&nbsp;In Android, it’s also conventional to prefix these
        instance variables with an
        <em>
            m
        </em>
        so it’s easy to tell what is a non-public, non-static instance variable
        and what isn’t. It feels a bit odd at first but is a good habit to get
        into, especially since Android source code
        <a title="specifies this convention" href="http://source.android.com/source/code-style.html#follow-field-naming-conventions"
        target="_blank" sl-processed="1">
            specifies this convention
        </a>
        and you’d need to do it to contribute to Android source code directly.
    </p>
    <p>
        <em>
            Getters
        </em>
        and
        <em>
            setters
        </em>
        for member variables are also a staple of Android development. These short
        methods provide the rest of your app with a way to change a member variable
        if needed, and they allow you to provide extra behavior when getting and
        setting member variables.
    </p>
    <h2>
        Access Modifiers
    </h2>
    <p>
        One final piece of the puzzle that helps setters and getters work is access
        modifiers. Take a look at the following snippet from the model above:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            private
        </span>
        ArrayList mReminderArrayList;
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                setReminderArrayList
            </span>
            <span class="hljs-params">
                (ArrayList reminderArrayList)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            this
        </span>
        .mReminderArrayList = reminderArrayList; }
    </pre>
    <p>
        Notice the
        <em>
            private
        </em>
        and
        <em>
            public
        </em>
        keywords? These are
        <em>
            access modifiers
        </em>
        and they’re responsible for&nbsp;specifying&nbsp;which elements of your
        model class are accessible to other classes, helping to encapsulate your
        objects.
    </p>
    <ul>
        <li>
            <em>
                Public
            </em>
            &nbsp;— accessible by all other objects. The public methods and variables
            form the API of the class.
        </li>
        <li>
            <em>
                Private
            </em>
            — only accessible to this object. Not even available to subclasses.
        </li>
        <li>
            <em>
                Protected
            </em>
            — accessible to this object and its subclasses. Not available to any other
            objects.
        </li>
    </ul>
    <p>
        Member variables should always be set to private or protected. Access
        to them from outside the class should be via public getters and setters,
        as demonstrated in the above code snippet. This avoids hard-to-trace side-effects
        and tightly-coupled code.
    </p>
    <p>
        If you made a subclass of the model above and wanted your subclass to
        have access to
        <code>
            mReminderArrayList
        </code>
        , you would change its access modifier to
        <em>
            protected
        </em>
        . This grants access to that variable in your subclass, while allowing
        you to further customize or work with that variable.
    </p>
    <h2>
        Fragments
    </h2>
    <p>
        Before tackling the next topic in Java for Android, you need to know a
        little bit more about how the UI of an Android app is constructed. Activities
        are great for managing the entire content of the screen, but they don’t
        like to share. Luckily there’s a great way to break down the UI into smaller
        component called
        <em>
            fragments
        </em>
        .
    </p>
    <p>
        Fragments are&nbsp;like activities, but with the added bonus of being
        able to be embed in activities as though they were views. They have lifecycle
        methods similar to an activity’s
        <code>
            onCreate()
        </code>
        and can receive input just like an activity.
    </p>
    <p>
        A layout for a fragment looks exactly the same as a layout for an activity;
        it contains a few view declarations. You even hook them up to the code
        in the same way, by declaring the view as a variable and finding the view
        through the identifier you provide in the layout.
    </p>
    <p>
        The following code creates a fragment from a layout file at&nbsp;
        <em>
            res/layout/fragment_embedded.xml
        </em>
        :
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                EmbeddedFragment
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                Fragment
            </span>
        </span>
        {
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            View
            <span class="hljs-title">
                onCreateView
            </span>
            <span class="hljs-params">
                (LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-comment">
            // Inflate the layout for this fragment
        </span>
        <span class="hljs-keyword">
            return
        </span>
        inflater.inflate(R.layout.fragment_embedded, container,
        <span class="hljs-keyword">
            false
        </span>
        ); } }
    </pre>
    <p>
        You first extend your class to inherit the behavior of a fragment and
        then use one of its lifecycle methods, namely
        <code>
            onCreateView()
        </code>
        , to set up the fragment. Then you return a layout to show for that particular
        fragment.
    </p>
    <p>
        This is all simple enough when your activity and embedded fragment work
        in isolation, but what if you need them to communicate? Here’s an example
        method inside an activity that is trying to communicate with a fragment:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                private
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                updateFragment
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        { EmbeddedFragment fragment = (EmbeddedFragment) getFragmentManager().findFragmentById(R.id.fragment_embedded);
        fragment.setTextViewText(
        <span class="hljs-string">
            "Hello Little Fragment"
        </span>
        ); }
    </pre>
    <p>
        Because the fragment exists within the activity, you access it with
        <code>
            findFragmentById
        </code>
        and an identifier defined in XML. Then, you can easily invoke a fragment’s
        public methods, as shown&nbsp;in the above example,
        <code>
            setTextViewText()
        </code>
        .
    </p>
    <p>
        Conversely, a fragment can access its associated activity by calling
        <code>
            getActivity()
        </code>
        . This works in many simple situations, but it’s more fun to discuss in
        terms of an intricate scenario.
    </p>
    <h2>
        Interfaces
    </h2>
    <p>
        What if your activity was home to three lively fragments, each doing its
        own job, but needing to inform other fragments of what it’s doing at specific
        times?
    </p>
    <p>
        In theory, fragments should only concern themselves with their own purpose
        and needn’t know they exist next to others; the activity is the mastermind
        in a sense. It’s the only one that has access to all the fragments and
        knows what they do.
    </p>
    <p>
        This calls for a Java feature known as
        <em>
            Interfaces
        </em>
        .
    </p>
    <p>
        An interface is like a class, but without the implementation. Instead
        it defines the public API. Classes can then implement these interfaces
        and your code no longer relies on concrete class implementations, instead
        knowing only&nbsp;that “this is an unknown object upon which I can call
        these interface methods”.
    </p>
    <p>
        Interfaces allow your objects to work indirectly with other objects without
        exposing their inner workings. Think of something that is extremely complicated
        to build but quite simple to use: a car, a television set or even the device
        you’re using to read this tutorial.
    </p>
    <p>
        You probably don’t know all of the inner workings of these things, but
        you certainly know how to operate them. Interfaces do the same thing.
    </p>
    <p>
        In Android, interfaces are useful for facilitating communication fragment
        to activity, or fragment to fragment. It works like this:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                EmbeddedFragment
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                Fragment
            </span>
        </span>
        {
        <span class="hljs-comment">
            // 1
        </span>
        OnItemInListSelectedListener mCallback;
        <span class="hljs-comment">
            // 2
        </span>
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                interface
            </span>
            <span class="hljs-title">
                OnItemInListSelectedListener
            </span>
        </span>
        {
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onItemInListSelected
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-keyword">
                    int
                </span>
                position)
            </span>
        </span>
        ; }
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
                onAttach
            </span>
            <span class="hljs-params">
                (Activity activity)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onAttach(activity);
        <span class="hljs-comment">
            // 3
        </span>
        <span class="hljs-keyword">
            try
        </span>
        { mCallback = (OnItemInListSelectedListener) activity; }
        <span class="hljs-keyword">
            catch
        </span>
        (ClassCastException e) {
        <span class="hljs-keyword">
            throw
        </span>
        <span class="hljs-keyword">
            new
        </span>
        ClassCastException(activity.toString() +
        <span class="hljs-string">
            " must implement OnItemInListSelectedListener"
        </span>
        ); } }
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            View
            <span class="hljs-title">
                onCreateView
            </span>
            <span class="hljs-params">
                (LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            return
        </span>
        inflater.inflate(R.layout.fragment_embedded, container,
        <span class="hljs-keyword">
            false
        </span>
        ); } }
    </pre>
    <p>
        Look at this in detail:
    </p>
    <ol>
        <li>
            In the fragment, you declare a member variable to store a custom object
            that implements
            <code>
                OnItemInListSelectedListener
            </code>
            and you name it
            <code>
                mCallback
            </code>
            .
        </li>
        <li>
            Next, you create the interface and declare the required methods — your
            interface can have many methods.
        </li>
        <li>
            In
            <code>
                onAttach()
            </code>
            , a fragment lifecycle method, you check if the activity your fragment
            is attached to conforms to
            <code>
                OnItemInListSelectedListener
            </code>
            . If not, then it can’t serve your purposes and you have a problem. The
            <code>
                ClassCastException
            </code>
            describes this during runtime. It’s best to signal this to yourself and
            other programmers so you can catch the problem early.
        </li>
    </ol>
    <p>
        The next thing is to make your activity use the interface:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                MainMenuActivity
            </span>
            <span class="hljs-keyword">
                extends
            </span>
            <span class="hljs-title">
                Activity
            </span>
            <span class="hljs-keyword">
                implements
            </span>
            <span class="hljs-title">
                EmbeddedFragment
            </span>
            .
            <span class="hljs-title">
                OnItemInListSelectedListener
            </span>
        </span>
        { ...
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onItemInListSelected
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-keyword">
                    int
                </span>
                position)
            </span>
        </span>
        {
        <span class="hljs-comment">
            // Received a message from the Fragment, you'll do something neat here
        </span>
        } }
    </pre>
    <p>
        The
        <code>
            implements
        </code>
        keyword in the class definition states that this class will implement
        the specified interface. You then need to provide implementations for all
        the methods specified on the interface. On this custom interface there
        is only one method, and you can see that it has a skeleton implementation
        in the above code snippet.
    </p>
    <p>
        That’s the hard part, but you’re still not communicating fragment to fragment.
        Say you have defined a second fragment,
        <em>
            ListDetailFragment
        </em>
        , with identifier
        <em>
            fragment_list_detail
        </em>
        and a method named
        <em>
            showListItemDetails(int)
        </em>
        . To get them talking, you simply do what you did earlier to establish
        activity to fragment communications with one of the fragment’s public methods:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                public
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onItemInListSelected
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-keyword">
                    int
                </span>
                position)
            </span>
        </span>
        { ListDetailFragment listDetailFragment = (ListDetailFragment) getFragmentManager.findFragmentById(R.id.fragment_list_detail);
        listDetailFragment.showListItemDetails(position); }
    </pre>
    <p>
        Just like that, you’ve built a way to communicate between fragments and
        activities. Interfaces are useful for establishing communication while
        keeping components separate. Learning how components work with fragments
        and activities is a vital part of keeping your app architecture flexible.
    </p>
    <h2>
        Annotations
    </h2>
    <p>
        Have you noticed those peculiar lines of code above some of the method
        names in this article?
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-meta">
            @Override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                protected
            </span>
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                onCreate
            </span>
            <span class="hljs-params">
                (Bundle savedInstanceState)
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onCreate(savedInstanceState); }
    </pre>
    <p>
        Those words prefixed with an
        <em>
            @
        </em>
        are
        <em>
            Annotations
        </em>
        . They provide extra information at a variety of stages of an app. Annotations
        provide extra information to the compiler at runtime or even to generate
        extra code.
    </p>
    <p>
        The most common annotation in Android is
        <em>
            @Override
        </em>
        , which exists to inform the compiler that a specific method should override
        one from the super class. If your method doesn’t actually override anything,
        then the compiler will fail and tell you, providing a nice safety net from
        any oddities you might have encountered.
    </p>
    <p>
        Another well-known annotation is
        <em>
            @TargetApi
        </em>
        . It exists to allow your methods to indicate they are for use on a specific
        or newer version of Android. Using a method with @TargetApi set to a version
        higher than the current target of your app will cause the compiler to complain
        that you’re using functionality that isn’t available for your version of
        Android.
    </p>
    <p>
        It’s a complaint, but it’s also a polite warning. You can still run your
        app despite the warning, but you can pretty much count on an ensuing crash.
    </p>
    <p>
        When you’re building an Android app, you can almost count on needing these
        two annotations. There are others, and you can learn about the form the
        Android API documentation. It’s also possible to create your own annotations
        to automate specific tasks, generate code and other helpful functions.
    </p>
    <p>
        A shining example of this is the third party library
        <a href="http://androidannotations.org" sl-processed="1">
            AndroidAnnotations
        </a>
        . It provides a variety of custom annotations that simplify multi-line
        functions into single-line annotations and other useful features. Take
        a look at what annotations are available and what they offer to your apps.
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
        Building an Android app requires time, patience and compiling multiple
        subjects under one roof. Hopefully this article has shed some light on
        the inner workings and the tricky relationship between Android and Java.
    </p>
    <p>
        You’ve had a brief intro into these topics:
    </p>
    <ul>
        <li>
            The Android VM. One of the key ways that Java for Android differs from
            standard Java is in its compilation process, and its virtual machines.
        </li>
        <li>
            Use of POJOs. Plain old java objects are extensively used within Android
            to form the basis of model objects.
        </li>
        <li>
            Access Modifiers. These are key to making your code readable and easy
            to reason about.
        </li>
        <li>
            Interfaces. A hugely important topic in Android, as they are in the wider
            world of Java. Referring to objects via interfaces rather than concrete
            class implementations will really help to decouple code and create nicely
            reusable components.
        </li>
        <li>
            Annotations. The Android-specific Java annotations that you’ll be using
            right from day 1.
        </li>
    </ul>
    <p>
        There is no substitute for actually making an app; creating an app and
        experimenting with some of the concepts demonstrated here, and see what
        works and what fails.
    </p>
    <p>
        If you’re new to Java, or want to refresh your memory, you can download
        a
        <a href="http://www.raywenderlich.com/?p=119175" sl-processed="1">
            free PDF cheat sheet and quick reference
        </a>
        that’ll make writing your first Java much smoother.
    </p>
    <p>
        The forums, found below, are open to you to discuss this tutorial, ask
        questions, share ideas and muse on the larger theme of developing with
        Java for Android. There certainly is a lot to talk about!
    </p>
    <p>
        <i>
            The Android robot is reproduced or modified from work created and shared
            by Google and used according to terms described in the Creative Commons
            3.0 Attribution License.
        </i>
    </p>
</div>