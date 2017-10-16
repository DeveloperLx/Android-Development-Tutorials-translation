# Android的常用设计模式 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/168038/common-design-patterns-android-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志
            </em>
            ：本教程已由Joe Howard更新至Kotlin版本。原教程是由Matt Luedke编写。
        </p>
    </div>
    <div id="attachment_119228" style="width: 260px" class="wp-caption alignright">
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/AndroidDesignPatterns-feature-2.png"
        alt="&quot;Future You&quot;" width="250" height="250" class="size-full wp-image-119228">
        <p class="wp-caption-text">
            “Future You”
        </p>
    </div>
    <p>
        除了满足你的客户雇主外，还有一个重要的特性可以让你在开发者的职业生涯中保持快乐：Future You! （Future You的概念，就是暗指这么酷的开发者衬衫，保不齐不久的将来就会有）:]
    </p>
    <p>
        将来的你会继承自己在某个时间的写的代码，并且生出很多关于你当时为何要这样写的问题。而相对于在代码中留出无数困惑的注释，更好的方式是采取常见的
        <em>
            设计模式
        </em>
        。
    </p>
    <p>
        本教程会介绍一些Android常见的设计模式，你可以在开发app的时候用到它们。设计模式是对常见软件问题的可重用的解决方案。这里覆盖的既不是一份详尽的列表，也不是学术上可引用的论文。相反，它只是一个可落实行动的指南和进一步调研的起点。
    </p>
    <p>
        本文还假设你熟悉Android开发的基础。如果你是个Kotlin的纯小白，XML或Android Studio，请首先参考
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Beginning%20Android%20Development%20Part%20One%20Installing%20Android%20Studio.md"
        target="_blank" title="Beginning Android Development Series">
            开始Android开发系列
        </a>
        and
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Kotlin%20For%20Android%20An%20Introduction.md"
        target="_blank" title="Kotlin For Android: An Introduction">
            Kotlin开发Android：介绍
        </a>
        。
    </p>
    <h2>
        入门
    </h2>
    <p>
        <i>
            “项目中有什么地方，让你为了改变同一的事情，必须要在多个地方来进行么？” – Future You
        </i>
    </p>
    <p>
        Future You应当最小化用于寻找复杂的项目依赖的“侦探工作”的时间，因此我们希望项目应当具有尽可能好的可复用性，可读性和易辨别性。这些目标可以是从单个的一个对象，直到整个项目的贯彻。且可以将这些模式分为下列的种类：
    </p>
    <ul>
        <li>
            <em>
                创建型模式：
            </em>
            如何
            <i>
                创建
            </i>
            对象。
        </li>
        <li>
            <em>
                结构性的模式：
            </em>
            如何构建
            <i>
                compose
            </i>
            对象。
        </li>
        <li>
            <em>
                行为模式
            </em>
            如何协调
            <i>
                coordinate
            </i>
            对象之间的交互。
        </li>
    </ul>
    <p>
        你可能早就使用了一个或几个的模式，只是没有赋予它正式的名称，而Future You就会将它们从你的直觉中独立出来。
    </p>
    <p>
        在以下的部分，你会覆盖下列来自于每个种类的模式，并查看如何将它们应用到Android上：
    </p>
    <p>
        <em>
            创建性的
        </em>
    </p>
    <ul>
        <li>
            构建器
        </li>
        <li>
            依赖注入
        </li>
        <li>
            单例
        </li>
    </ul>
    <p>
        <em>
            结构性的
        </em>
    </p>
    <ul>
        <li>
            Adapter
        </li>
        <li>
            Facade
        </li>
    </ul>
    <p>
        <em>
            行为性的
        </em>
    </p>
    <ul>
        <li>
            Command
        </li>
        <li>
            观察者
        </li>
        <li>
            MVC
        </li>
        <li>
            MVVM
        </li>
        <li>
            干净的架构
        </li>
    </ul>
    <div class="note">
        <em>
            注意：
        </em>
        This article isn’t like a traditional raywenderlich.com tutorial in that
        it doesn’t have an accompanying sample project that you can follow along
        with. Treat it instead like an article to get you up to speed to the different
        patterns you’ll see used in our other Android tutorials, and to discover
        ways to improve your own code.
    </div>
    <h2>
        Creational Patterns
    </h2>
    <p>
        <i>
            “When I need a particular complex object, how do I get one?” – Future
            You
        </i>
    </p>
    <p>
        Future You hopes the answer is not “copy and paste the same code every
        time you need an instance of this object.” Instead, creational patterns
        make object creation simple and easily repeatable.
    </p>
    <p>
        Here are several examples:
    </p>
    <h3>
        Builder
    </h3>
    <p>
        At a sandwich spot down my block, I use a small pencil to check off the
        bread, ingredients, and condiments I’d like on my sandwich from a checklist
        on a slip of paper. Even though the checklist’s title instructs me to “build
        my own” sandwich, I really only fill out the form and hand it over the
        counter. I’m not actually doing the sandwich-building, just the customizing…and
        the consuming. :]
    </p>
    <p>
        Similarly, the Builder pattern separates the construction of a complex
        object (the slicing of bread, the stacking of pickles) from its representation
        (a yummy sandwich); in this way, the same construction process can create
        different representations.
    </p>
    <p>
        In Android, the Builder pattern appears when using objects like
        <code>
            AlertDialog.Builder
        </code>
        :
    </p>
    <pre lang="kotlin">
        AlertDialog.Builder(this) .setTitle("Metaphorical Sandwich Dialog") .setMessage("Metaphorical
        message to please use the spicy mustard.") .setNegativeButton("No thanks",
        { dialogInterface, i -&gt; // "No thanks" button was clicked }) .setPositiveButton("OK",
        { dialogInterface, i -&gt; // "OK" button was clicked }) .show()
    </pre>
    <p>
        This builder proceeds step-by-step and lets you specify only the parts
        of your
        <code>
            AlertDialog
        </code>
        that matter to you. Take a look at the
        <a href="https://developer.android.com/reference/android/app/AlertDialog.Builder.html"
        target="_blank" title="AlertDialog.Builder docs">
            AlertDialog.Builder documentation
        </a>
        ; you’ll see there are quite a few commands to choose from when building
        your alert.
    </p>
    <p>
        The code block above produces the following alert:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-07-at-2.03.02-PM.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-07-at-2.03.02-PM-480x260.png"
            alt="" width="480" height="260" class="aligncenter size-medium wp-image-168051"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-07-at-2.03.02-PM-480x260.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-07-at-2.03.02-PM-650x352.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/08/Screen-Shot-2017-08-07-at-2.03.02-PM.png 768w"
            sizes="(max-width: 480px) 100vw, 480px">
        </a>
    </p>
    <p>
        A different set of choices would result in a completely different sandwich
        – er, alert. :]
    </p>
    <h3>
        Dependency Injection
    </h3>
    <p>
        Dependency injection is like moving into a furnished apartment. Everything
        you need is already there; you don’t have to wait for furniture delivery
        or follow pages of IKEA instructions to put together a Borgsjö bookshelf.
    </p>
    <p>
        In strictly software terms, dependency injection has you provide any objects
        required when you instantiate a new object; the new object doesn’t need
        to construct or customize the objects itself.
    </p>
    <p>
        In Android, you might find you need to access the same complex objects
        from various points in your app, such as a network client, an image loader,
        or
        <code>
            SharedPreferences
        </code>
        for local storage. You can
        <em>
            inject
        </em>
        these objects into your activities and fragments and access them right
        away.
    </p>
    <p>
        <a href="http://google.github.io/dagger/">
            Dagger 2
        </a>
        is the most popular open-source dependency injection framework for Android
        and was developed in collaboration between Google and Square. You simply
        annotate a class with
        <code>
            @Module
        </code>
        , and populate it with
        <code>
            @Provides
        </code>
        methods such as the following:
    </p>
    <pre lang="kotlin">
        @Module class AppModule { @Provides fun provideSharedPreferences(app:
        Application): SharedPreferences { return app.getSharedPreferences("prefs",
        Context.MODE_PRIVATE) } }
    </pre>
    <p>
        The module above creates and configures all required objects. As an additional
        best-practice in larger apps, you could even create multiple modules separated
        by function.
    </p>
    <p>
        Then, you make a
        <em>
            Component
        </em>
        interface to list your modules and the classes you’ll inject:
    </p>
    <pre lang="kotlin">
        @Component(modules = arrayOf(AppModule::class)) interface AppComponent
        { // ... }
    </pre>
    <p>
        The component ties together where the dependencies are
        <i>
            coming from
        </i>
        (the modules), and where they are
        <i>
            going to
        </i>
        (the injection points).
    </p>
    <p>
        Finally, you use the
        <code>
            @Inject
        </code>
        annotation to request the dependency wherever you need it, along with
        <code>
            lateinit
        </code>
        to allow a non-nullable property to be initialized after the containing
        object is created:
    </p>
    <pre lang="kotlin">
        @Inject lateinit var sharedPreferences: SharedPreferences
    </pre>
    <p>
        As an example, you could use this approach in an Activity and then use
        local storage,
        <i>
            without
        </i>
        any need for the Activity having to know how the
        <code>
            SharedPreferences
        </code>
        object came to be.
    </p>
    <p>
        Admittedly this is a simplified overview, but you can read up on the
        <a href="http://google.github.io/dagger/">
            Dagger documentation
        </a>
        for more detailed implementation details, and also check out
        <a href="https://www.raywenderlich.com/146804/dependency-injection-dagger-2"
        target="_blank" title="Dependency Injection in Android with Dagger 2">
            Dependency Injection in Android with Dagger 2
        </a>
        . This pattern may seem complicated and “magical” at first, but its use
        can help simplify your activities and fragments.
    </p>
    <h3>
        Singleton
    </h3>
    <p>
        The Singleton Pattern specifies that only a single instance of a class
        should exist with a global point of access. This works well when modeling
        real-world objects only having one instance. The Kotlin
        <code>
            object
        </code>
        keyword is used to declare a singleton, without the need to specify a
        static instance as in other languages:
    </p>
    <pre lang="kotlin">
        object ExampleSingleton { fun exampleMethod() { // ... } }
    </pre>
    <p>
        When you need to access members of the singleton object, you simply make
        a call as follows:
    </p>
    <pre lang="kotlin">
        ExampleSingleton.exampleMethod()
    </pre>
    <p>
        Behind the scenes, the Kotlin object is backed by an
        <code>
            INSTANCE
        </code>
        static field, so if you need to use a Kotlin object from Java code, you
        modify the call as follows:
    </p>
    <pre lang="java">
        ExampleSingleton.INSTANCE.exampleMethod();
    </pre>
    <p>
        By using
        <code>
            object
        </code>
        , you’ll know you’re using the same instance of that class throughout
        your app.
    </p>
    <p>
        The Singleton is probably the easiest pattern to initially understand,
        but can be dangerously easy to overuse – and abuse. Since it’s accessible
        from multiple objects, the singleton can undergo unexpected side effects
        that are difficult to track down – exactly what Future You doesn’t want
        to deal with. It’s important to understand the pattern, but other design
        patterns may be safer and easier to maintain.
    </p>
    <h2>
        Structural Patterns
    </h2>
    <p>
        <i>
            “So when I open up this class, how will I remember what’s it’s doing and
            how it’s put together?” – Future You
        </i>
    </p>
    <p>
        Future You will undoubtedly appreciate the Structural Patterns you used
        to help organize the guts of your classes and objects into familiar arrangements
        that perform typical tasks. Two commonly-seen patterns in Android are
        <em>
            Adapter
        </em>
        and
        <em>
            Facade
        </em>
        .
    </p>
    <h3>
        Adapter
    </h3>
    <p>
        A
        <a href="https://youtu.be/1cYzkyXp0jg" target="_blank" title="Apollo 13">
            famous scene
        </a>
        in the movie Apollo 13 features a team of engineers tasked with fitting
        a square peg into a round hole. This, metaphorically, is the role of an
        adapter. In software terms, this pattern lets two incompatible classes
        work together by converting the interface of a class into another interface
        the client expects.
    </p>
    <p>
        Consider the business logic of your app; it might be a Product, or a User,
        or a Tribble. It’s the square peg. Meanwhile, a
        <code>
            RecyclerView
        </code>
        is the same basic object across all Android apps. It’s the round hole.
    </p>
    <p>
        In this situation, you can use a subclass of
        <code>
            RecyclerView.Adapter
        </code>
        and implement the required methods to make everything work:
    </p>
    <pre lang="kotlin">
        class TribbleAdapter(private val tribbles: List&lt;Tribble&gt;) : RecyclerView.Adapter&lt;TribbleViewHolder&gt;()
        { override fun onCreateViewHolder(viewGroup: ViewGroup, i: Int): TribbleViewHolder
        { val inflater = LayoutInflater.from(viewGroup.context) val view = inflater.inflate(R.layout.row_tribble,
        viewGroup, false) return TribbleViewHolder(view) } override fun onBindViewHolder(viewHolder:
        TribbleViewHolder, i: Int) { viewHolder.bind(tribbles[i]) } override fun
        getItemCount() = tribbles.size }
    </pre>
    <p>
        <code>
            RecyclerView
        </code>
        doesn’t know what a Tribble is, as it’s never seen a single episode of
        Star Trek – not even the new movies. :] Instead, it’s the adapter’s job
        to handle the data and send the
        <code>
            bind
        </code>
        command to the correct
        <code>
            ViewHolder
        </code>
        .
    </p>
    <h3>
        Facade
    </h3>
    <p>
        The Facade pattern provides a higher-level interface that makes a set
        of other interfaces easier to use. The following diagram illustrates this
        idea in more detail:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2013/07/facade2.png">
            <img class="aligncenter size-full wp-image-47211" src="https://koenig-media.raywenderlich.com/uploads/2013/07/facade2.png"
            alt="facade2" width="453" height="228" srcset="https://koenig-media.raywenderlich.com/uploads/2013/07/facade2.png 604w, https://koenig-media.raywenderlich.com/uploads/2013/07/facade2-480x241.png 480w"
            sizes="(max-width: 453px) 100vw, 453px">
        </a>
    </p>
    <p>
        If your Activity needs a list of books, it should be able to ask a single
        object for that list
        <i>
            without
        </i>
        understanding the inner workings of your local storage, cache, and API
        client. Beyond keeping your Activities and Fragments code clean and concise,
        this lets Future You make any required changes to the API implementation
        without any impact on the Activity.
    </p>
    <p>
        <a href="http://square.github.io/retrofit/">
            Retrofit
        </a>
        from Square is an open-source Android library that helps you implement
        the Facade pattern; you create an interface to provide API data to client
        classes like so:
    </p>
    <pre lang="kotlin">
        interface BooksApi { @GET("books") fun listBooks(): Call&lt;List&lt;Book&gt;&gt;
        }
    </pre>
    <p>
        The client simply needs to call
        <code>
            listBooks()
        </code>
        to receive a list of
        <code>
            Book
        </code>
        objects in the callback. It’s nice and clean; for all it knows, you could
        have an army of Tribbles assembling the list and sending it back via transporter
        beam. :]
    </p>
    <p>
        This lets you make all types of customizations underneath without affecting
        the client. For example, you can specify a customized JSON deserializer
        about which the Activity has no clue:
    </p>
    <pre lang="kotlin">
        val retrofit = Retrofit.Builder() .baseUrl("http://www.myexampleurl.com")
        .addConverterFactory(GsonConverterFactory.create()) .build() val api =
        retrofit.create&lt;BooksApi&gt;(BooksApi::class.java)
    </pre>
    <p>
        Notice the use of
        <code>
            GsonConverterFactory
        </code>
        , working behind the scenes as a JSON deserializer. With Retrofit, you
        can further customize operations with
        <code>
            Interceptor
        </code>
        and
        <code>
            OkHttpClient
        </code>
        to control caching and logging behavior without the client knowing what’s
        going on.
    </p>
    <p>
        The less each object knows about what’s going on behind the scenes, the
        easier it will be for Future You to manage changes in the app. This pattern
        can be used in a lot of other contexts; Retrofit is only one mechanism
        among many.
    </p>
    <h2>
        Behavioral Patterns
    </h2>
    <p>
        <i>
            “So… how do I tell which class is responsible for what?” – Future You
        </i>
    </p>
    <p>
        Behavioral patterns let you assign responsibility for different app functions;
        Future You can use them to navigate the structure and architecture of the
        project. These patterns can vary in scope, from the relationship between
        two objects to the entire architecture of your app. In many cases, the
        various behaviorial patterns are used together in the same app.
    </p>
    <h3>
        Command
    </h3>
    <p>
        When you order some excellent Saag Paneer at an Indian restaurant, you
        don’t necessarily know which cook will prepare your dish; you only give
        your order to the waiter, who posts the order in the kitchen for the next
        available cook.
    </p>
    <p>
        Similarly, the Command pattern lets you issue requests without knowing
        the receiver. You encapsulate a request as an object and send it off; deciding
        how to complete the request is an entirely separate mechanism.
    </p>
    <p>
        Greenrobot’s
        <a href="https://github.com/greenrobot/EventBus" target="_blank" title="EventBus">
            EventBus
        </a>
        is a popular Android framework that supports this pattern in the following
        manner:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe.png">
            <img class="aligncenter size-large wp-image-110104" src="https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe-700x262.png"
            alt="EventBus-Publish-Subscribe" width="700" height="262" srcset="https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe-700x262.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe-480x180.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe.png 1280w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        An
        <code>
            Event
        </code>
        is a command-style object that can be triggered by user input, server
        data, or pretty much anything else in your app. You can create specific
        subclasses which carry data as well:
    </p>
    <pre lang="kotlin">
        class MySpecificEvent { /* Additional fields if needed */ }
    </pre>
    <p>
        After defining your event, you obtain an instance of
        <code>
            EventBus
        </code>
        and register an object as a subscriber:
    </p>
    <pre lang="kotlin">
        eventBus.register(this)
    </pre>
    <p>
        Now that the object is a subscriber, tell it what type of event to subscribe
        to and what it should do when it receives one:
    </p>
    <pre lang="kotlin">
        fun onEvent(event: MySpecificEvent) { /* Do something */ }
    </pre>
    <p>
        Finally, create and post one of those events based on your criteria:
    </p>
    <pre lang="kotlin">
        eventBus.post(event)
    </pre>
    <p>
        Since so much of this pattern works its magic at run-time, Future You
        might have a little trouble tracing this pattern unless you have good test
        coverage. Still, a well-designed flow of commands balances out the readability
        and should be easy enough to follow at a later date.
    </p>
    <h3>
        Observer
    </h3>
    <p>
        The Observer pattern defines a one-to-many dependency between objects.
        When one object changes state, all of its dependents are notified and updated
        automatically.
    </p>
    <p>
        This is a versatile pattern; you can use it for operations of indeterminate
        time, such as API calls. You can also use it to respond to user input.
    </p>
    <p>
        The
        <a href="https://github.com/ReactiveX/RxAndroid" target="_blank" title="RxAndroid">
            RxAndroid
        </a>
        framework (aka Reactive Android) will let you implement this pattern throughout
        your app:
    </p>
    <pre lang="kotlin">
        apiService.getData(someData) .subscribeOn(Schedulers.io()) .observeOn(AndroidSchedulers.mainThread())
        .subscribe (/* an Observer */)
    </pre>
    <p>
        In short, you define
        <code>
            Observable
        </code>
        objects that will
        <i>
            emit
        </i>
        values. These values can emit all at once, as a continuous stream, or
        at any rate and duration.
    </p>
    <p>
        <code>
            Subscriber
        </code>
        objects will
        <i>
            listen
        </i>
        for these values and react to them as they arrive. For example, you can
        open a subscription when you make an API call, listen for the response
        from the server, and react accordingly.
    </p>
    <h3>
        Model View Controller
    </h3>
    <p>
        <em>
            Model View Controller
        </em>
        , aka MVC, refers to the current reigning presentation architectural pattern
        across several platforms; it’s particularly easy to set your project up
        in this way on Android. It refers to the three divisions of classes used
        in this pattern:
    </p>
    <ul>
        <li>
            <em>
                Model:
            </em>
            your data classes. If you have
            <code>
                User
            </code>
            or
            <code>
                Product
            </code>
            objects, these “model” the real world.
        </li>
        <li>
            <em>
                View:
            </em>
            your visual classes. Everything the user sees falls under this category.
        </li>
        <li>
            <em>
                Controller:
            </em>
            the glue between the two. It updates the view, takes user input, and makes
            changes to the model.
        </li>
    </ul>
    <p>
        Dividing your code between these three categories will go a long way toward
        making your code decoupled and reusable.
    </p>
    <p>
        Future You will eventually get a request from the client to add a new
        screen to the app, but simply using the existing data in the app; following
        the MVC paradigm means Future You can easily re-use the same models and
        only change the views. Or perhaps the client will ask Future You to move
        that fancy widget from the home screen to the detail screen. Separating
        your view logic makes this an easy task.
    </p>
    <p>
        Additionally, moving as much layout and resource logic as possible into
        Android XML keeps your View layer clean and tidy. Nice!
    </p>
    <p>
        You may have to do some drawing in Kotlin from time to time, in which
        case it will help to separate&nbsp;the drawing operations from your activity
        and fragment classes.
    </p>
    <p>
        Over time, you’ll find making architectural decisions easier under MVC
        and Future You can more easily solve issues as they arise.
    </p>
    <h3>
        Model View ViewModel
    </h3>
    <p>
        This unfortunately-quite-confusingly-named presentation architectural
        pattern is similar to the MVC pattern; the Model and View components are
        the same. The ViewModel object is the “glue” between the model and view
        layers, but operates differently than the Controller component. Instead,
        it exposes commands for the view and binds the view to the model. When
        the model updates, the corresponding views update as well via the data
        binding. Similarly, as the user interacts with the view, the bindings work
        in the opposite direction to automatically update the model. This reactive
        pattern removes a lot of glue code.
    </p>
    <p>
        The MVVM pattern is trending upwards in popularity but is still a fairly
        recent addition to the pattern library. Google recently introduced this
        pattern as part of its
        <a href="https://developer.android.com/topic/libraries/architecture/viewmodel.html"
        target="_blank" title="Android Architecture Components">
            Architecture Components
        </a>
        library! Future You would love it if you kept your eye on this one! :]
    </p>
    <h3>
        Clean Architecture
    </h3>
    <p>
        <em>
            Clean Architecture
        </em>
        exists at a higher abstraction level than the MVC and MVVM presentation
        architecture patterns. It describes the overall application architecture:
        how the various layers of an app (business objects, use cases, presenters,
        data storage, and UI) communicate with one another. It is similar to the
        <a href="http://alistair.cockburn.us/Hexagonal+architecture" target="_blank"
        title="Hexagonal architecture">
            Hexagonal architecture
        </a>
        as well other application architectures. MVC and MVVM exist within Clean
        Architecture at the outer presentation and UI layers.
    </p>
    <p>
        The original Clean Architecture definition is
        <a href="https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html"
        target="_blank" title="Clean Architecture">
            here
        </a>
        , and many examples can be found on Clean Architecture for Android, including
        <a href="https://fernandocejas.com/2015/07/18/architecting-android-the-evolution/"
        target="_blank" title="Architecting Android">
            Architecting Android…The evolution
        </a>
        .
    </p>
    <h2>
        Where to Go From Here?
    </h2>
    <p>
        While it feels great to keep abreast of the latest flashy APIs, keeping
        your apps updated can quickly lead to redesign-fatigue. Investing in software
        design patterns early on will improve your return on development time;
        you’ll start to notice you get more done with less effort.
    </p>
    <p>
        I recommend checking out timeless classics such as
        <a href="https://en.wikipedia.org/wiki/Design_Patterns">
            Design Patterns by the “Gang of Four.”
        </a>
        Compared to Material Design or Android Wear, this book might be considered
        “ancient”, but documents many useful design patterns that predate Android
        itself !
    </p>
    <p>
        I hope this article serves as a starting point for your research into
        common design patterns for Android! If you have any questions or comments,
        feel free to join the forum discussion below – Future You would be happy
        if you did. :]
    </p>
</div>