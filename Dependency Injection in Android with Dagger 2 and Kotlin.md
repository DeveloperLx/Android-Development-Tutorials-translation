# Android中的依赖注入 - Dagger 2及Kotlin
---
#### [原文地址](https://www.raywenderlich.com/171327/dependency-injection-android-dagger-2) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志
            </em>
            本Dagger 2教程已由Dario Coletto更新至最新版本的Android Studio（3.0.1版），并使用Kotlin作为开发语言。原教程是由Joe Howard编写的。
        </p>
    </div>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-250x250.png"
            alt="Dagger-feature" width="250" height="250" class="alignright size-thumbnail wp-image-149255"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/11/Dagger-feature-128x128.png 128w"
            sizes="(max-width: 250px) 100vw, 250px">
        </a>
        “你必须做依赖注入！”的声音一直广泛传播在现代的软件开发术语中。
        <em>
            依赖注入
        </em>
        （或简称DI）这样的名字可以吓到任何的软件开发者。
    </p>
    <p>
        It turns out that Dependency Injection is nowhere near as complex as its
        name implies. And it is a key tool for building software systems that are
        maintainable and testable. In the end, relying on dependency injection
        will simplify your code quite a bit and also allow for a clearer path to
        writing testable code.
    </p>
    <p>
        In this tutorial, you’ll update an existing app named
        <em>
            DroidWiki
        </em>
        to use DI. The DroidWiki app is a simple wikipedia client for android,
        based on
        <em>
            Dagger 2
        </em>
        and
        <em>
            OkHttp 3
        </em>
        . The Wikipedia API is based on MediaWiki, and you can find the documentation
        <a href="https://www.mediawiki.org/wiki/API:Main_page">
            here
        </a>
        . These API are public and there is no need to get API keys or other stuff.
        But you should definitely check out
        <a href="https://www.mediawiki.org/wiki/API:Etiquette">
            MediaWiki Etiquette
        </a>
        .
    </p>
    <p>
        Here’s a quick peek at the search result screen in DroidWiki:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-SearchActivity.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-SearchActivity-333x500.png"
            alt="DroidWiki app" width="333" height="500" class="aligncenter size-large wp-image-172017"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-SearchActivity-333x500.png 333w, https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-SearchActivity-213x320.png 213w, https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-SearchActivity.png 1080w"
            sizes="(max-width: 333px) 100vw, 333px">
        </a>
    </p>
    <h2>
        Introduction
    </h2>
    <p>
        Before we begin, if you don’t know what Dependency Injection is, here’s
        some great news: you’re probably already using it without knowing it!
    </p>
    <h3>
        What is Dependency Injection?
    </h3>
    <p>
        First, what is a dependency? Any non-trivial software program is going
        to contain components that pass information and send message calls back
        and forth between one another.
    </p>
    <p>
        For example, when using an Object Oriented Programming language (such
        as Java/Kotlin on Android), objects will call methods on other objects
        that they have references to. A
        <i>
            dependency
        </i>
        is when one of the objects depends on the concrete implementation of another
        object.
    </p>
    <h3>
        Practical example of Dependency Injection
    </h3>
    <p>
        Consider a practical example in Kotlin code. You can identify a dependency
        in your code whenever you instantiate an object within another. In such
        a case, you are responsible for creating and configuring the object that
        is being created. For example, consider the following class
        <code>
            Parent
        </code>
        :
    </p>
    <pre lang="kotlin">
        class Parent { private val child = Child() }
    </pre>
    <p>
        A
        <code>
            Parent
        </code>
        instance creates its
        <code>
            child
        </code>
        field when it’s instantiated. The
        <code>
            Parent
        </code>
        instance is dependent on the concrete implementation of
        <code>
            Child
        </code>
        and on configuring the
        <code>
            child
        </code>
        field to use it.
    </p>
    <p>
        This presents a
        <em>
            coupling
        </em>
        or
        <em>
            dependency
        </em>
        of the
        <code>
            Parent
        </code>
        class on the
        <code>
            Child
        </code>
        class. If the setup of a
        <code>
            Child
        </code>
        object is complex, all that complexity will be reflected within the
        <code>
            Parent
        </code>
        class as well. You will need to edit
        <code>
            Parent
        </code>
        to configure a
        <code>
            Child
        </code>
        object.
    </p>
    <p>
        If the
        <code>
            Child
        </code>
        class itself depends on a class
        <code>
            C
        </code>
        , which in turn depends on class
        <code>
            D
        </code>
        , then all that complexity will propagate throughout the code base and
        hence result in a tight coupling between the components of the application.
    </p>
    <p>
        <em>
            Dependency Injection
        </em>
        is the term used to describe the technique of loosening the coupling just
        described. In the simple example above, only one tiny change is needed:
    </p>
    <pre lang="kotlin">
        class Parent(private val child: Child)
    </pre>
    <p>
        Voilà — that’s dependency injection at its core!
    </p>
    <p>
        Rather than creating the
        <code>
            child
        </code>
        object inside the
        <code>
            Parent
        </code>
        class, the
        <code>
            child
        </code>
        object is passed into or
        <i>
            injected
        </i>
        into
        <code>
            Parent
        </code>
        ‘s constructor. The responsibility for configuring
        <code>
            child
        </code>
        is elsewhere, and the
        <code>
            Parent
        </code>
        class is a consumer of the
        <code>
            Child
        </code>
        class.
    </p>
    <h3>
        The Dependency Inversion Principle
    </h3>
    <p>
        Dependency injection is often discussed in conjunction with one of the
        five
        <em>
            SOLID principles
        </em>
        of Object-Oriented Design: the
        <em>
            Dependency Inversion principle
        </em>
        . For a great introduction to the SOLID principles, particularly on Android,
        check out this
        <a href="https://realm.io/news/donn-felker-solid-part-5/">
            post from Realm on Dependency Inversion
        </a>
        .
    </p>
    <p>
        The gist of the Dependency Inversion principle is that it is important
        to depend on abstractions rather than concrete implementations.
    </p>
    <p>
        In the simple example above, this means changing
        <code>
            Child
        </code>
        to a Kotlin
        <code>
            interface
        </code>
        rather than a Kotlin
        <code>
            class
        </code>
        . With this change, many different types of concrete
        <code>
            Child
        </code>
        type objects that adhere to the
        <code>
            Child
        </code>
        interface can be passed into the
        <code>
            Parent
        </code>
        constructor. This presents several key benefits:
    </p>
    <ul>
        <li>
            Allows for the
            <code>
                Parent
            </code>
            class to be tested with various kinds of
            <code>
                Child
            </code>
            objects.
        </li>
        <li>
            Mock
            <code>
                Child
            </code>
            objects can be used as needed in certain test scenarios.
        </li>
        <li>
            Testing of
            <code>
                Parent
            </code>
            is independent of the implementation of
            <code>
                Child
            </code>
            .
        </li>
    </ul>
    <h3>
        How can Dagger 2 help with DI
    </h3>
    <p>
        <a href="https://google.github.io/dagger/">
            Dagger 2
        </a>
        is the result of a collaboration between the team behind
        <a href="https://github.com/google/guice">
            Guice
        </a>
        (developed by Google) and
        <a href="http://square.github.io/dagger/">
            Dagger
        </a>
        (the predecessor of Dagger 2, created by Square).
    </p>
    <p>
        They fixed a lot of problems from their previous work, and Dagger 2 is
        the faster framework for DI (since it works at compile time rather than
        at runtime with reflection).
    </p>
    <div class="note">
        <p>
            <em>
                Note:
            </em>
            Dagger 2 is written in Java, but it works with Kotlin without any modification.
            However, the code generated by the annotation processor will be Java code
            (that is 100% interoperable with Kotlin).
        </p>
    </div>
    <p>
        The name “Dagger” is inspired in part by the nature of dependencies in
        software development. The web of dependencies that occur between objects
        such as
        <code>
            Parent
        </code>
        ,
        <code>
            Child
        </code>
        ,
        <code>
            OtherClass
        </code>
        , etc., create a structure called a
        <em>
            Directed Acyclic Graph
        </em>
        . Dagger 2 is used to simplify the creation of such graphs in your Java
        and Android projects.
    </p>
    <p>
        Enough theory! Time to start writing some code.
    </p>
    <h2>
        Getting Started
    </h2>
    <p>
        Download the starter project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/droidwiki-starter.zip">
            here
        </a>
        .
    </p>
    <p>
        Open the starter app in Android Studio 3.0.1 or greater and if it prompts
        you to update your gradle version, go ahead and do so. Run the starter
        app in either an emulator or on a device, and you should see a screen like
        the following:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-HomepageActivity.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-HomepageActivity-333x500.png"
            alt="HomepageActivity" width="333" height="500" class="aligncenter size-large wp-image-172019"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-HomepageActivity-333x500.png 333w, https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-HomepageActivity-213x320.png 213w, https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-HomepageActivity.png 1080w"
            sizes="(max-width: 333px) 100vw, 333px">
        </a>
    </p>
    <p>
        The app consists of three screens. The first one is just a splashscreen.
    </p>
    <p>
        In the second one you’ll see an HTML version of the Wikipedia homepage,
        obtained through the WikiMedia API. The
        <code>
            Toolbar
        </code>
        at the top of the page contains a magnifier that, when tapped, will lead
        you to the third screen.
    </p>
    <p>
        From there, you can type something to search on Wikipedia and press the
        search button to run a query. Results will be displayed as a list of
        <code>
            CardView
        </code>
        s inside a
        <code>
            RecyclerView
        </code>
        .
    </p>
    <p>
        Examine the app project structure and existing classes. You’ll see that
        the app uses the
        <em>
            Model-View-Presenter
        </em>
        (MVP) pattern to structure the code. Besides Dagger 2, the app uses common
        Android libraries such as:
    </p>
    <ul>
        <li>
            <a href="http://square.github.io/okhttp/">
                OkHttp 3
            </a>
        </li>
        <li>
            RecyclerView
        </li>
        <li>
            <a href="https://kotlinlang.org/docs/tutorials/android-plugin.html">
                Kotlin synthetic properties
            </a>
        </li>
    </ul>
    <p>
        The subpackages in the main package are
        <code>
            application
        </code>
        ,
        <code>
            model
        </code>
        ,
        <code>
            network
        </code>
        ,
        <code>
            ui
        </code>
        and
        <code>
            utils
        </code>
        . If you explore the
        <code>
            ui
        </code>
        package, you’ll see subpackages for the three screens. Except for the
        splashscreen, each other package has classes for the view and presenter
        classes for the screen.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-14-54-59.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-14-54-59-309x500.png"
            alt="DroidWiki Hierarchy Tree" width="309" height="500" class="aligncenter size-large wp-image-179495"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-14-54-59-309x500.png 309w, https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-14-54-59-198x320.png 198w, https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-14-54-59.png 450w"
            sizes="(max-width: 309px) 100vw, 309px">
        </a>
    </p>
    <p>
        By examining the app
        <em>
            build.gradle
        </em>
        file, you’ll also see that the app applies the plugin
        <em>
            kotlin-android-extensions
        </em>
        . It is used to implement view binding and
        <em>
            kotlin-kapt
        </em>
        for annotation processing.
    </p>
    <h3>
        MVP
    </h3>
    <p>
        In case you’re unfamiliar with the MVP pattern, there are many good online
        resources for getting started.
    </p>
    <p>
        MVP is similar to other structural patterns for implementing
        <i>
            separation of concerns
        </i>
        . Examples are
        <em>
            Model-View-Controller
        </em>
        and
        <em>
            Model-View-ViewModel
        </em>
        . In MVP on Android, your activities and fragments typically act as the
        <em>
            view
        </em>
        objects. They do so by implementing a view interface and handling interaction
        of the app with the user.
    </p>
    <p>
        The view passes on user actions to the
        <em>
            presenter
        </em>
        , which handles the business logic and interaction with data repositories,
        such as a server API or database. The
        <em>
            model
        </em>
        layer consists of the objects that make up the content of the app.
    </p>
    <p>
        In the case of DroidWiki, the
        <code>
            HomepageActivity
        </code>
        class implements the
        <code>
            HomepageView
        </code>
        interface.
        <code>
            HomepageActivity
        </code>
        has a reference to a
        <code>
            HomepagePresenter
        </code>
        interface. This controls access to model objects of type
        <code>
            Homepage
        </code>
    </p>
    <p>
        The use of OkHttp 3 is found in the
        <code>
            WikiApi
        </code>
        class in the
        <code>
            network
        </code>
        package. This class defines the interface to the WikiMedia API required
        by the app. There are two calls of type
        <em>
            GET
        </em>
        defined and the
        <code>
            JSONObject
        </code>
        will let you parse the obtained responses. The parsing will be executed
        in the
        <code>
            HomepageResult
        </code>
        and the
        <code>
            SearchResult
        </code>
        classes. And you will get a
        <code>
            WikiHomepage
        </code>
        object and a list of
        <code>
            Entry
        </code>
        objects.
    </p>
    <div class="note">
        <p>
            <em>
                Note:
            </em>
            Since Kotlin doesn’t need you to write getters and setters, you can replace
            POJO classes with a
            <code>
                data class
            </code>
            . For more information, see
            <a href="https://kotlinlang.org/docs/reference/data-classes.html">
                the official kotlin data classes documentation
            </a>
            .
        </p>
    </div>
    <h3>
        Dependencies in DroidWiki
    </h3>
    <p>
        Open the
        <code>
            HomepageActivity
        </code>
        class in the
        <code>
            ui.homepage
        </code>
        package. In its
        <code>
            onCreate()
        </code>
        method, there are several calls to configure a
        <code>
            HomepagePresenter
        </code>
        :
    </p>
    <pre lang="kotlin">
        private val presenter: HomepagePresenter = HomepagePresenterImpl() ...
        presenter.setView(this) presenter.loadHomepage()
    </pre>
    <p>
        Here, you create a concrete implementation of a
        <code>
            HomepagePresenter
        </code>
        when the activity is instantiated.
    </p>
    <p>
        Open
        <em>
            HomepagePresenterImpl.kt
        </em>
        and take a look at
        <code>
            loadHomepage()
        </code>
        . Both an
        <code>
            OkHttpClient
        </code>
        object and a
        <code>
            WikiApi
        </code>
        object are created and configured in the
        <code>
            loadHomepage()
        </code>
        method. The same happens for the
        <code>
            SearchActivity
        </code>
        with an
        <code>
            EntryPresenter
        </code>
        and a list of
        <code>
            EntryView
        </code>
        .
    </p>
    <p>
        This creation of dependencies couple the model, view, and presenter layers
        too tightly. Swapping in a mock presenter for the view is impossible as
        written without updating the view code. The code for creating the
        <code>
            OkHttpClient
        </code>
        and
        <code>
            WikiApi
        </code>
        objects is repeated between the two presenter implementations in the app:
        <code>
            HomepagePresenterImpl
        </code>
        and
        <code>
            EntryPresenterImpl
        </code>
        .
    </p>
    <p>
        Finally, it’s time to start writing some code to remove code duplication
        and some coupling between layers!
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-320x320.png"
            alt="Lets do this" width="320" height="320" class="aligncenter size-medium wp-image-179499"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-500x500.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/12/letsdothis-128x128.png 128w"
            sizes="(max-width: 320px) 100vw, 320px">
        </a>
    </p>
    <h2>
        Configure the Project With Dagger 2
    </h2>
    <p>
        Configuring Dagger with Kotlin is a little bit different from how you
        may have done with Java.
        <br>
        Dagger requires an
        <em>
            annotation processor
        </em>
        , and thus the main difference is which one you are going to use. In fact
        with Java you used the Groovy methods
        <code>
            apt
        </code>
        or the newer
        <code>
            annotationProcessor
        </code>
        , while with Kotlin you need to use
        <code>
            kapt
        </code>
        .
    </p>
    <p>
        By default kapt is not enabled in Kotlin, and to enable it you must apply
        its plugin to your app
        <em>
            build.gradle
        </em>
        , so add the line
        <code>
            apply plugin: 'kotlin-kapt'
        </code>
        :
    </p>
    <pre lang="groovy">
        apply plugin: 'com.android.application' apply plugin: 'kotlin-android'
        // Add this line to enable kapt apply plugin: 'kotlin-kapt' ...
    </pre>
    <p>
        Then add these dependencies to actually “install” dagger
    </p>
    <pre lang="groovy">
        dependencies { ... implementation 'com.google.dagger:dagger:2.11' kapt
        'com.google.dagger:dagger-compiler:2.11' provided 'javax.annotation:jsr250-api:1.0'
        ... }
    </pre>
    <p>
        Here we’re using Dagger 2.11, you can check the latest version in the
        <a href="https://mvnrepository.com/artifact/com.google.dagger/dagger">
            Maven repository
        </a>
        .
    </p>
    <p>
        Android Studio will prompt you to sync your gradle files on this change,
        so please go ahead and do so to ensure that you’re including Dagger correctly.
        Notice that you are including an annotation library from
        <code>
            javax
        </code>
        , because many of the features of Dagger are provided by
        <em>
            Java annotations
        </em>
        .
    </p>
    <h2>
        Dagger 2 public APIs
    </h2>
    <p>
        Dagger 2 can seem complex at the beginning, but it’s really not so hard.
        In fact, the
        <i>
            complete
        </i>
        public API of Dagger is composed by less than 30 lines of code. And from
        these lines you can remove a pair of interfaces that are rarely used (Lazy
        and MapKey), so the most used public APIs are composed of 3 annotations:
    </p>
    <pre lang="java">
        public @interface Component { Class&lt;?&gt; [] modules() default {};
        Class&lt;?&gt; [] dependencies() default {}; } public @interface Module
        { Class&lt;?&gt; [] includes() default {}; } public @interface Provides
        {}
    </pre>
    <p>
        Now let’s see how these annotations are used to bring dependency injection
        to your projects!
    </p>
    <h3>
        Module
    </h3>
    <p>
        The first annotation you’ll use is the
        <code>
            @Module
        </code>
        annotation. Start by creating a new package named
        <code>
            dagger
        </code>
        under the app main package, by right-clicking the main package and selecting
        <em>
            New/Package
        </em>
        :
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-15-27-13.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-15-27-13-650x167.png"
            alt="New package" width="650" height="167" class="aligncenter size-large wp-image-179500"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-15-27-13-650x167.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-15-27-13-480x123.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/12/Screenshot-from-2017-12-04-15-27-13.png 1081w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        Next, create a new file in the
        <code>
            dagger
        </code>
        package. Right-click
        <em>
            dagger
        </em>
        and select
        <em>
            New/Kotlin File/Class
        </em>
        . Name the class
        <code>
            AppModule
        </code>
        .
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-NewKotlinClass.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-NewKotlinClass-480x122.png"
            alt="New Kotlin Class" width="480" height="122" class="aligncenter size-medium wp-image-172026"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-NewKotlinClass-480x122.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-NewKotlinClass.png 631w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        Add the following empty class to the new file:
    </p>
    <pre lang="kotlin">
        @Module class AppModule { }
    </pre>
    <p>
        Here, you’ve created a class named
        <code>
            AppModule
        </code>
        and annotated it with the Dagger
        <code>
            @Module
        </code>
        annotation. Android Studio should automatically create any necessary import
        statements for you. But if not, hit
        <em>
            option+return
        </em>
        on Mac or
        <em>
            Alt+Enter
        </em>
        on PC to create them as needed.
    </p>
    <p>
        The
        <code>
            @Module
        </code>
        annotation tells Dagger that the
        <code>
            AppModule
        </code>
        class will provide dependencies for a part of the application. It is normal
        to have multiple Dagger modules in a project, and it is typical for one
        of them to provide app-wide dependencies.
    </p>
    <p>
        Add that capability now by inserting the following code within the body
        of the
        <code>
            AppModule
        </code>
        class:
    </p>
    <pre lang="kotlin">
        @Module class AppModule(private val app: Application) { @Provides @Singleton
        fun provideContext(): Context = app }
    </pre>
    <p>
        You’ve added a private field to hold a reference to the
        <code>
            app
        </code>
        object, a constructor to configure
        <code>
            app
        </code>
        , and a
        <code>
            provideContext()
        </code>
        method that returns the
        <code>
            app
        </code>
        object. Notice that there are two more Dagger annotations on that method:
        <code>
            @Provides
        </code>
        and
        <code>
            @Singleton
        </code>
        .
    </p>
    <h3>
        @Provides and @Singleton
    </h3>
    <p>
        The
        <code>
            @Provides
        </code>
        annotation tells Dagger that the method provides a certain type of dependency,
        in this case, a
        <code>
            Context
        </code>
        object. When a part of the app requests that Dagger inject a
        <code>
            Context
        </code>
        , the
        <code>
            @Provides
        </code>
        annotation tells Dagger where to find it.
    </p>
    <div class="note">
        <p>
            <em>
                Note:
            </em>
            The method names for the providers, such as
            <code>
                provideContext()
            </code>
            , are not important and can be named anything you like. Dagger only looks
            at the return type. Using
            <code>
                provide
            </code>
            as a prefix is a common convention.
        </p>
    </div>
    <p>
        The
        <code>
            @Singleton
        </code>
        annotation is not part of the Dagger API. It’s contained inside the javax
        package you added to your build.gradle at the beginning. It tells Dagger
        that there should only be a single instance of that dependency. So when
        generating the code Dagger will handle all the logic for you, and you won’t
        write all the boilerplate code to check if another instance of the object
        is already available.
    </p>
    <h3>
        Component
    </h3>
    <p>
        Now that you have a Dagger module that contains a dependency that can
        be injected, how do you use it?
    </p>
    <p>
        That requires the use of another Dagger annotation,
        <code>
            @Component
        </code>
        . As you’ve done for the AppModule, create a new Kotlin file in the
        <code>
            dagger
        </code>
        package and name it
        <code>
            AppComponent
        </code>
        .
    </p>
    <p>
        Add the following code to the file:
    </p>
    <pre lang="kotlin">
        @Singleton @Component(modules = [AppModule::class]) interface AppComponent
    </pre>
    <p>
        You’ve told Dagger that
        <code>
            AppComponent
        </code>
        is a singleton component interface for the app. The
        <code>
            @Component
        </code>
        annotation takes a list of
        <code>
            modules
        </code>
        as an input. You’re using the literal array syntax available in Kotlin,
        <code>
            [AppModule::class]
        </code>
        .
    </p>
    <p>
        The component is used to connect objects to their dependencies, typically
        by use of overridden
        <code>
            inject()
        </code>
        methods. In order to use the component, it must be accessible from the
        parts of the app that need injection. Typically, that will happen from
        the app
        <code>
            Application
        </code>
        subclass, as follows.
    </p>
    <p>
        First, add the following field to
        <code>
            WikiApplication
        </code>
        :
    </p>
    <pre lang="kotlin">
        lateinit var wikiComponent: AppComponent
    </pre>
    <p>
        Now, you must initialize
        <code>
            AppComponent
        </code>
        . Do so by adding the following method to
        <code>
            WikiApplication
        </code>
        :
    </p>
    <pre lang="kotlin">
        private fun initDagger(app: WikiApplication): AppComponent = DaggerAppComponent.builder()
        .appModule(AppModule(app)) .build()
    </pre>
    <p>
        You’ll likely notice an error called out by Android Studio on
        <code>
            DaggerAppComponent
        </code>
        . Click
        <em>
            Make Module ‘app’
        </em>
        from the Android Studio
        <em>
            Build
        </em>
        menu. This will generate a new file, called
        <code>
            DaggerAppComponent.java
        </code>
    </p>
    <p>
        Import the generated
        <code>
            DaggerAppComponent
        </code>
        to clear the compile errors. Ignore the deprecation warning on the
        <code>
            appModule()
        </code>
        method; that will be fixed shortly.
    </p>
    <p>
        Finally, update
        <code>
            onCreate()
        </code>
        in
        <code>
            WikiApplication
        </code>
        to read as follows:
    </p>
    <pre lang="kotlin">
        override fun onCreate() { super.onCreate() wikiComponent = initDagger(this)
        }
    </pre>
    <p>
        This initializes the
        <code>
            wikiComponent
        </code>
        field when the application first starts up.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-320x320.png"
        alt="Time for injection" width="320" height="320" class="aligncenter size-medium wp-image-179501"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-500x500.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor-128x128.png 128w, https://koenig-media.raywenderlich.com/uploads/2017/12/timefor.png 1000w"
        sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <h2>
        Your first (dependency) injection
    </h2>
    <p>
        Add the following method declaration within the
        <code>
            AppComponent
        </code>
        interface:
    </p>
    <pre lang="kotlin">
        fun inject(target: HomepageActivity)
    </pre>
    <p>
        Here, you’ve specified that the
        <code>
            HomepageActivity
        </code>
        class will require injection from
        <code>
            AppComponent
        </code>
        .
    </p>
    <p>
        Create a new class in the
        <code>
            dagger
        </code>
        package and name it
        <code>
            PresenterModule
        </code>
        . Add the following code into
        <code>
            PresenterModule
        </code>
        :
    </p>
    <pre lang="java">
        @Module class PresenterModule { @Provides @Singleton fun provideHomepagePresenter():
        HomepagePresenter = HomepagePresenterImpl() }
    </pre>
    <p>
        You’re specifying that a
        <code>
            HomepagePresenter
        </code>
        will be provided, and that the presenter returned will be the concrete
        implementation
        <code>
            HomepagePresenterImpl
        </code>
        .
    </p>
    <p>
        Next, wire up
        <code>
            PresenterModule
        </code>
        with
        <code>
            AppComponent
        </code>
        by updating the
        <code>
            @Component
        </code>
        annotation in
        <code>
            AppComponent
        </code>
        to read:
    </p>
    <pre lang="kotlin">
        @Component(modules = [AppModule::class, PresenterModule::class])
    </pre>
    <h3>
        Update HomepageActivity
    </h3>
    <p>
        Finally, open up the
        <code>
            HomepageActivity
        </code>
        class in the
        <code>
            ui.homepage
        </code>
        package.
    </p>
    <p>
        You need to update the
        <code>
            presenter
        </code>
        field with the following changes:
    </p>
    <ul>
        <li>
            remove the private modifier (Dagger can’t inject private fields)
        </li>
        <li>
            add the
            <code>
                @Inject
            </code>
            annotation
        </li>
        <li>
            add the
            <a href="https://kotlinlang.org/docs/reference/properties.html">
                lateinit
            </a>
            modifier
        </li>
        <li>
            replace
            <em>
                val
            </em>
            with
            <em>
                var
            </em>
        </li>
        <li>
            remove the initialization
        </li>
    </ul>
    <p>
        When you’re done, the
        <code>
            presenter
        </code>
        declaration looks like this:
    </p>
    <pre lang="kotlin">
        @Inject lateinit var presenter: HomepagePresenter
    </pre>
    <p>
        Again, the
        <code>
            @Inject
        </code>
        annotation is not part of Dagger; it belongs to
        <em>
            javax annotations
        </em>
        .
    </p>
    <p>
        The
        <code>
            @Inject
        </code>
        annotation tells Dagger that you want it to do an injection of the
        <code>
            presenter
        </code>
        field.
    </p>
    <p>
        Update
        <code>
            onCreate()
        </code>
        by adding the call to
        <code>
            AppComponent.inject()
        </code>
        as follows:
    </p>
    <pre lang="kotlin">
        override fun onCreate(savedInstanceState: Bundle?) { super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_homepage) (application as WikiApplication).wikiComponent.inject(this)
        ... }
    </pre>
    <p>
        You are getting the
        <code>
            AppComponent
        </code>
        from
        <code>
            WikiApplication
        </code>
        and asking it to inject all known dependencies into
        <code>
            HomepageActivity
        </code>
        . Since you annotated
        <code>
            presenter
        </code>
        with
        <code>
            @Inject
        </code>
        , Dagger will inject a concrete
        <code>
            HomepagePresenter
        </code>
        object into
        <code>
            HomepageActivity
        </code>
        .
    </p>
    <p>
        Dagger knows that you defined
        <code>
            provideHomepagePresenter()
        </code>
        in the
        <code>
            PresenterModule
        </code>
        class, and uses it to create the injected
        <code>
            HomepagePresenter
        </code>
        object.
    </p>
    <p>
        Build and run your app now. It should behave exactly as before, and you’ve
        avoided the exception. You’ve just finished your first dependency injection
        with Dagger 2!
    </p>
    <h3>
        The General Pattern
    </h3>
    <p>
        There is a general pattern that emerges based on the previous code changes.
        Think about the steps just taken to use Dagger dependency injection with
        <code>
            HomepageActivity
        </code>
        :
    </p>
    <ul>
        <li>
            Add
            <code>
                inject()
            </code>
            in
            <code>
                AppComponent
            </code>
            with
            <code>
                HomepageActivity
            </code>
            argument.
        </li>
        <li>
            Add
            <code>
                provideHomepagePresenter()
            </code>
            in
            <code>
                PresenterModule
            </code>
            .
        </li>
        <li>
            Add
            <code>
                @Inject
            </code>
            annotation to
            <code>
                HomepagePresenter presenter
            </code>
            in
            <code>
                HomepageActivity
            </code>
            .
        </li>
        <li>
            Add
            <code>
                WikiApplication.wikiComponent.inject(this)
            </code>
            in
            <code>
                onCreate()
            </code>
            in
            <code>
                HomepageActivity
            </code>
            .
        </li>
    </ul>
    <p>
        If you consider
        <code>
            HomepageActivity
        </code>
        as the target class, and
        <code>
            HomepagePresenter
        </code>
        as the source interface to be injected, then the above steps can be generalized
        as follows for any target class requiring source interfaces to be injected:
    </p>
    <ul>
        <li>
            Add
            <code>
                inject()
            </code>
            in
            <code>
                AppComponent
            </code>
            with
            <code>
                Target
            </code>
            class argument.
        </li>
        <li>
            Add
            <code>
                @Provides
            </code>
            annotated method in
            <code>
                PresenterModule
            </code>
            for each source object to be injected.
        </li>
        <li>
            Add
            <code>
                @Inject
            </code>
            annotation to each
            <code>
                Source
            </code>
            member variable in
            <code>
                Target
            </code>
            class.
        </li>
        <li>
            Add
            <code>
                WikiApplication.wikiComponent.inject(this)
            </code>
            in
            <code>
                onCreate()
            </code>
            in
            <code>
                Target
            </code>
            class.
        </li>
    </ul>
    <p>
        As a challenge, see if you can perform an injection of the
        <code>
            EntryPresenter
        </code>
        detail screen into
        <code>
            SearchActivity
        </code>
        . This will include removing the following line of code:
    </p>
    <pre lang="kotiln">
        private val presenter: EntryPresenter = EntryPresenterImpl()
    </pre>
    <p>
        The steps are just the same as above for
        <code>
            HomepageActivity
        </code>
        . Use the pattern, and if you get stuck, check out the final project code
        at the end of this tutorial.
    </p>
    <h2>
        Injecting the Network Graph
    </h2>
    <p>
        In the app as written currently, both the list screen and detail screen
        presenters create their own network dependencies. In a typical app that
        uses Dagger 2 and OkHttp 3 together, OkHttp will be provided by dependency
        injection.
    </p>
    <p>
        Here you will see some of the many advantages of using dependency injection
        and Dagger 2, including:
    </p>
    <ul>
        <li>
            Eliminating code duplication.
        </li>
        <li>
            Eliminating the need for dependency configuration.
        </li>
        <li>
            Automatic construction of a dependency graph.
        </li>
    </ul>
    <h3>
        NetworkModule
    </h3>
    <p>
        Start by creating a new file in the
        <code>
            dagger
        </code>
        package, this time named
        <code>
            NetworkModule
        </code>
        , which starts off as follows:
    </p>
    <pre lang="kotlin">
        @Module class NetworkModule { }
    </pre>
    <p>
        What you’re looking to do here is to inject a
        <code>
            WikiApi
        </code>
        object into the app’s presenter implementations, so that the presenters
        can call the API.
    </p>
    <p>
        For example, if you look at the current
        <code>
            HomepagePresenterImpl
        </code>
        , you see that
        <code>
            WikiApi
        </code>
        depends on a
        <code>
            OkHttpClient
        </code>
        object, and if you need some complex setup for the HTTP client, you will
        need to configure the
        <code>
            OkHttpClient
        </code>
        every time (for example if you want to enable logging with a
        <code>
            LoggingInterceptor
        </code>
        ).
    </p>
    <p>
        Moreover the
        <code>
            WikiApi
        </code>
        requires 3 Strings that represents:
    </p>
    <ul>
        <li>
            the protocol for the request (HTTP or HTTPS)
        </li>
        <li>
            the language of Wikipedia you are querying.
        </li>
        <li>
            the rest of the base URL for the Wikipedia API (wikipedia.org/w/api.php)
        </li>
    </ul>
    <h3>
        Simplifying API builder
    </h3>
    <p>
        For the sake of simplicity you’re going to merge all these 3 Strings in
        a single
        <em>
            provider
        </em>
        .
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-DependencyDiagram.jpg">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-DependencyDiagram.jpg"
            alt="Dependency Diagram" width="311" height="371" class="aligncenter size-full wp-image-172022"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-DependencyDiagram.jpg 311w, https://koenig-media.raywenderlich.com/uploads/2017/09/DroidWiki-DependencyDiagram-268x320.jpg 268w"
            sizes="(max-width: 311px) 100vw, 311px">
        </a>
    </p>
    <p>
        Start by adding this method into
        <code>
            NetworkModule
        </code>
        along with a constant string:
    </p>
    <pre lang="kotlin">
        companion object { private const val NAME_BASE_URL = "NAME_BASE_URL" }
        @Provides @Named(NAME_BASE_URL) fun provideBaseUrlString() = "${Const.PROTOCOL}://${Const.LANGUAGE}.${Const.BASE_URL}"
    </pre>
    <p>
        Here you can see the
        <code>
            @Named
        </code>
        annotation, that again, is not part of Dagger, but it’s provided by
        <em>
            javax
        </em>
        .
    </p>
    <p>
        You are injecting a
        <code>
            String
        </code>
        object, and since
        <code>
            String
        </code>
        is such a common type to use in an Android app, you’ve taken advantage
        of the
        <code>
            @Named
        </code>
        annotation to specify a specific string to be provided. This same technique
        can be used for your own types if you need multiple variations injected.
    </p>
    <p>
        Now that you have the
        <code>
            String
        </code>
        representing the base URL, add the following to the bottom of
        <code>
            NetworkModule
        </code>
        :
    </p>
    <pre lang="kotlin">
        @Provides @Singleton fun provideHttpClient() = OkHttpClient() @Provides
        @Singleton fun provideRequestBuilder(@Named(NAME_BASE_URL) baseUrl: String)
        = HttpUrl.parse(baseUrl)?.newBuilder() @Provides @Singleton fun provideWikiApi(client:
        OkHttpClient, requestBuilder: HttpUrl.Builder?) = WikiApi(client, requestBuilder)
    </pre>
    <p>
        You’re providing an HTTP client, a request builder, and a
        <code>
            WikiApi
        </code>
        .
    </p>
    <h3>
        WikiModule
    </h3>
    <p>
        Next, create a new file in the
        <code>
            dagger
        </code>
        package called
        <em>
            WikiModule
        </em>
        , and add provide methods for the API:
    </p>
    <pre lang="kotlin">
        @Module class WikiModule { @Provides @Singleton fun provideHomepage(api:
        WikiApi) = Homepage(api) @Provides @Singleton fun provideWiki(api: WikiApi)
        = Wiki(api) }
    </pre>
    <p>
        In the
        <em>
            NetworkModule
        </em>
        you’ve added the provides methods for an
        <code>
            OkHttpClient
        </code>
        object, an
        <code>
            HttpUrl.Builder
        </code>
        object, and a
        <code>
            WikiApi
        </code>
        object. Then in the
        <em>
            WikiModule
        </em>
        you’ve added the methods for a
        <code>
            Homepage
        </code>
        and
        <code>
            Wiki
        </code>
        objects, requesting dependencies from the previous methods.
    </p>
    <p>
        This allows Dagger to construct a dependency graph, so that, for example,
        when an object asks for a
        <code>
            Wiki
        </code>
        object to be injected, Dagger will first provide a
        <code>
            WikiApi
        </code>
        and then
        <code>
            OkHttpClient
        </code>
        and
        <em>
            HttpUrl.Builder
        </em>
        objects starting from
        <code>
            provideWiki(api: WikiApi)
        </code>
        .
    </p>
    <p>
        Dagger will then continue walking up the graph to find a
        <code>
            baseUrl
        </code>
        for
        <code>
            provideRequestBuilder(@Named(NAME_BASE_URL) baseUrl: String)
        </code>
        .
    </p>
    <p>
        By using the
        <code>
            @Singleton
        </code>
        annotations, only one instance of the
        <code>
            WikiApi
        </code>
        and
        <code>
            OkHttpClient
        </code>
        objects will be created and shared between both activities in the app.
    </p>
    <p>
        Add your
        <code>
            NetworkModule
        </code>
        and
        <code>
            WikiModule
        </code>
        to
        <code>
            AppComponent
        </code>
        by updating the
        <code>
            @Component
        </code>
        annotation to the following:
    </p>
    <pre lang="kotlin">
        @Component(modules = [ AppModule::class, PresenterModule::class, NetworkModule::class,
        WikiModule::class])
    </pre>
    <h3>
        Update PresenterModule
    </h3>
    <p>
        Next, update the
        <code>
            PresenterModule
        </code>
        provide methods so that the
        <code>
            Context
        </code>
        is passed as a constructor argument:
    </p>
    <pre lang="kotlin">
        @Provides @Singleton fun provideHomepagePresenter(homepage: Homepage):
        HomepagePresenter = HomepagePresenterImpl(homepage) @Provides @Singleton
        fun provideEntryPresenter(wiki: Wiki): EntryPresenter = EntryPresenterImpl(wiki)
    </pre>
    <p>
        And of course update the
        <code>
            HomepagePresenterImpl
        </code>
        and
        <code>
            EntryPresenterImpl
        </code>
        constructors:
    </p>
    <pre lang="kotlin">
        class HomepagePresenterImpl @Inject constructor(private val homepage:
        Homepage) : HomepagePresenter { ... }
    </pre>
    <pre lang="kotlin">
        class EntryPresenterImpl @Inject constructor(private val wiki: Wiki) :
        EntryPresenter { ... }
    </pre>
    <p>
        <code>
            Homepage/Wiki
        </code>
        constructors require a
        <code>
            WikiApi
        </code>
        parameter, but we don’t need to provide it anymore as Dagger will inject
        it since it’s present in its graph. At this point you can remove the initialization:
    </p>
    <pre lang="kotlin">
        private val client: OkHttpClient = OkHttpClient() private val api: WikiApi
        = WikiApi(client) private val homepage: Homepage = Homepage(api)
    </pre>
    <pre lang="kotlin">
        private val client: OkHttpClient = OkHttpClient() private val api: WikiApi
        = WikiApi(client) private val wiki: Wiki = Wiki(api)
    </pre>
    <p>
        You’ve injected the
        <code>
            WikiApi
        </code>
        dependency into the presenters. This allowed you to remove the duplicated
        creation of the
        <code>
            OkHttpClient
        </code>
        and
        <code>
            WikiApi
        </code>
        objects.
    </p>
    <h3>
        Update WikiApi
    </h3>
    <p>
        As a last step, the
        <code>
            WikiApi
        </code>
        class needs a constructor with an injected parameter, so you must update
        it:
    </p>
    <pre lang="kotlin">
        class WikiApi @Inject constructor(private val client: OkHttpClient, private
        val requestBuilder: HttpUrl.Builder?) { ... }
    </pre>
    <p>
        Now you don’t need to create an
        <code>
            HttpUrl.Builder
        </code>
        each time anymore, so you can update the methods
        <code>
            getHomepage()/search(query: String)
        </code>
        :
    </p>
    <pre lang="kotlin">
        val urlBuilder = requestBuilder ?.addQueryParameter(...) ...
    </pre>
    <p>
        Now everything should be ready to go. Build and run the app, and bask
        in the glory of decoupled, injected code!
    </p>
    <h2>
        Where to Go From Here?
    </h2>
    <p>
        You can download the final project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/droidwiki-final.zip">
            here
        </a>
        .
    </p>
    <p>
        A lot of developers asks themselves if all the changes you’ve applied
        to the DroidWiki app are useful or not. Especially since everything was
        already working before implementing dependency injection. The utility of
        dependency injection and a framework like Dagger 2 become most evident
        in real-world production apps, where the dependency graph can get very
        complex.
    </p>
    <p>
        Dagger 2 and dependency injection become especially useful when implementing
        proper testing into your app, allowing mock implementations of back-end
        APIs and data repositories to be used in testing.
    </p>
    <p>
        There’s much more to learn about in Dagger 2 and its usage, including:
    </p>
    <ul>
        <li>
            Scopes
        </li>
        <li>
            Subcomponents
        </li>
        <li>
            Testing with Mockito
        </li>
    </ul>
    <p>
        There are many great resources out there on the interwebs to dive into
        these topics and one I
        <i>
            must
        </i>
        suggest is a
        <a href="https://www.youtube.com/watch?v=plK0zyRLIP8">
            talk by Jake Wharton at DevOxx
        </a>
        , where you can get some more information about the history of DI on Android,
        some theory and some nice examples. As you do, happy injecting!
    </p>
</div>