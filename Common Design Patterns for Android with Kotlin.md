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
                创建性模式：
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
            如何
            <i>
                构建
            </i>
            对象。
        </li>
        <li>
            <em>
                行为模式
            </em>
            如何
            <i>
                协调
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
            Builder
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
        本教程和传统的raywenderlich.com有所不同，它没有一个相应的样本项目供你跟着做。品味它以加深对不同设计模式的理解，来提高你的编写代码的能力。
    </div>
    <h2>
        创建性模式
    </h2>
    <p>
        <i>
            “当我需要一个特别负责的对象的时候，该怎么做？” – Future
            You
        </i>
    </p>
    <p>
        Future You希望这个答案不是“每次需要这个代码的实例时，就拷贝并粘贴相同的代码。”而是通过创建性的模式，使得创建对象简单并易于重复。
    </p>
    <p>
        有几个例子：
    </p>
    <h3>
        Builder
    </h3>
    <p>
        就在街上的那个三明治点，我用了一支小铅笔，从一张纸的清单上，来核对我想在三明治上添加的面包，配料和调味品。虽然清单的标题说是“自助的”三明治，但我其实只需填好这张表并递给服务员就可以了。我并没有实际地制作三明治，只是进行了自定义，以及消费。:]
    </p>
    <p>
        类似的，Builder模式会将构建一个复杂的对象（面包切片，泡菜堆），与它的表示（美味的三明治）拆分开。这样，就可以用相同的构造过程来创建不同的表示。
    </p>
    <p>
        在Android中，Builder模式会在当使用类似
        <code>
            AlertDialog.Builder
        </code>
        的对象时出现：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">AlertDialog.Builder(<span class="hljs-keyword">this</span>)
  .setTitle(<span class="hljs-string">"Metaphorical Sandwich Dialog"</span>)
  .setMessage(<span class="hljs-string">"Metaphorical message to please use the spicy mustard."</span>)
  .setNegativeButton(<span class="hljs-string">"No thanks"</span>, { dialogInterface, i -&gt;
    <span class="hljs-comment">// "No thanks" button was clicked</span>
  })
  .setPositiveButton(<span class="hljs-string">"OK"</span>, { dialogInterface, i -&gt;
    <span class="hljs-comment">// "OK" button was clicked</span>
  })
  .show()
</pre>
    <p>
        这个builder过程一步一步地指定了
        <code>
            AlertDialog
        </code>
        中的每个部分。参考一下
        <a href="https://developer.android.com/reference/android/app/AlertDialog.Builder.html"
        target="_blank" title="AlertDialog.Builder docs">
            AlertDialog.Builder文档
        </a>
        ，你可以看到很多构建警告框时可用的选项。
    </p>
    <p>
        上面的代码片段会生成如下的警告框：
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
        不同的选项集就会创建出完全不同的三明治 - 嗯，是警告框啦 :]
    </p>
    <h3>
        依赖注入
    </h3>
    <p>
        依赖注入就像是你进入到了一个已装备好家具的房间，所需的一切都早已存在，无需再等待投递，或跟随宜家的指南来组装Borgsjö的书架。
    </p>
    <p>
        在正规的软件术语中，依赖注入提供了当你初始化一个新对象的时候所需的任何对象；这样新的对象就无需自己来构造或定制对象了。
    </p>
    <p>
        在Android中，你会发现你需要在app从很多地方访问一些相同但很复杂的对象，例如网络客户端，图片加载器，或是本地保存的
        <code>
            SharedPreferences
        </code>
        。你就可以将这些对象
        <em>
            注入
        </em>
        到你的activity或fragment中来直接访问它们。
    </p>
    <p>
        <a href="http://google.github.io/dagger/">
            Dagger 2
        </a>
        是Android最流行的开源依赖注入框架，用于支持在Google和Square之间的协同开发。你只需将一个类标记为
        <code>
            @Module
        </code>
        ，并用
        <code>
            @Provides
        </code>
        来标记相应的方法：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-meta">@Module</span>
<span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">AppModule</span> </span>{
  <span class="hljs-meta">@Provides</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">provideSharedPreferences</span><span class="hljs-params">(app: <span class="hljs-type">Application</span>)</span></span>: SharedPreferences {
    <span class="hljs-keyword">return</span> app.getSharedPreferences(<span class="hljs-string">"prefs"</span>, Context.MODE_PRIVATE)
  }
}
</pre>
    <p>
        上述的模块创建并配置了所有必须的对象。作为一项在大型app中的最佳实践，你甚至可以创建由函数分隔的多个模块。
    </p>
    <p>
        然后，你就可以创建一个
        <em>
            Component
        </em>
        interface来列出你的模块，和你将注入的类：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-meta">@Component(modules = arrayOf(AppModule::class)</span>)
<span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">AppComponent</span> </span>{
  <span class="hljs-comment">// ...</span>
}
</pre>
    <p>
        component会将依赖的
        <i>
            来源
        </i>
        （模块），及
        <i>
            注入到
        </i>
        的地方联结起来。
    </p>
    <p>
        最后，在你需要的地方使用
        <code>
            @Inject
        </code>
        annotation来请求依赖，以及
        <code>
            lateinit
        </code>
        包含的对象被创建之后，初始化non-nullable的property：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-meta">@Inject</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> sharedPreferences: SharedPreferences
</pre>
    <p>
        在这个例子中，你就可以在Activity中使用这个方法，然后再使用本地的储存，
        <i>
            无需
        </i>
        知道
        <code>
            SharedPreferences
        </code>
        对象来源何处。
    </p>
    <p>
        上面是只一个很简单的概述，你可以在
        <a href="http://google.github.io/dagger/">
            Dagger documentation
        </a>
        中阅读更多实现的细节，还可以参考
        <a href="https://www.raywenderlich.com/146804/dependency-injection-dagger-2"
        target="_blank" title="Dependency Injection in Android with Dagger 2">
            Dependency Injection in Android with Dagger 2
        </a>
        。这个模式开始看起来会有点复杂和魔幻，但却可以用来简化你的activity和fragment。
    </p>
    <h3>
        单例
    </h3>
    <p>
        单例模式指定了这个类全局都只能有一个实例，无论何时访问都只能访问它。在Kotlin中关键字
        <code>
            object
        </code>
        用来声明一个单例，无需像其它语言中一样去指定一个静态实例：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">object</span> ExampleSingleton {
  <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">exampleMethod</span><span class="hljs-params">()</span></span> {
    <span class="hljs-comment">// ...</span>
  }
}
</pre>
    <p>
        当你需要单例对象的成员的时候，只需想下面这样子调用就可以了：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">ExampleSingleton.exampleMethod()
</pre>
    <p>
        在表象后，Kotlin的对象是由一个
        <code>
            INSTANCE
        </code>
        的静态字段来支持的，因此如果你需要在Java的代码中访问Kotlin的对象，只需将调用修改为下面的样子：
    </p>
    <pre lang="java" class="language-java hljs">ExampleSingleton.INSTANCE.exampleMethod();
</pre>
    <p>
        在
        <code>
            object
        </code>
        关键字的作用下，你的app就只会访问到这个类的相同的实例。
    </p>
    <p>
        单例可能是一上来最容易理解的设计模式，但却存在着很容易被滥用的风险。它在很多对象中都可以访问，可能就会遇到意料之外的难以追踪的副作用 - Future You并不想去处理它们。理解这个模式非常重要，但其它的设计模式会更加得安全且易于维护。
    </p>
    <h2>
        结构性的模式
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">TribbleAdapter</span></span>(<span class="hljs-keyword">private</span> <span class="hljs-keyword">val</span> tribbles: List&lt;Tribble&gt;) : RecyclerView.Adapter&lt;TribbleViewHolder&gt;() {
  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onCreateViewHolder</span><span class="hljs-params">(viewGroup: <span class="hljs-type">ViewGroup</span>, i: <span class="hljs-type">Int</span>)</span></span>: TribbleViewHolder {
    <span class="hljs-keyword">val</span> inflater = LayoutInflater.from(viewGroup.context)
    <span class="hljs-keyword">val</span> view = inflater.inflate(R.layout.row_tribble, viewGroup, <span class="hljs-literal">false</span>)
    <span class="hljs-keyword">return</span> TribbleViewHolder(view)
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onBindViewHolder</span><span class="hljs-params">(viewHolder: <span class="hljs-type">TribbleViewHolder</span>, i: <span class="hljs-type">Int</span>)</span></span> {
    viewHolder.bind(tribbles[i])
  }

  <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">getItemCount</span><span class="hljs-params">()</span></span> = tribbles.size
}
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">BooksApi</span> </span>{
  <span class="hljs-meta">@GET(<span class="hljs-meta-string">"books"</span>)</span>
  <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">listBooks</span><span class="hljs-params">()</span></span>: Call&lt;List&lt;Book&gt;&gt;
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> retrofit = Retrofit.Builder()
  .baseUrl(<span class="hljs-string">"http://www.myexampleurl.com"</span>)
  .addConverterFactory(GsonConverterFactory.create())
  .build()

<span class="hljs-keyword">val</span> api = retrofit.create&lt;BooksApi&gt;(BooksApi::<span class="hljs-class"><span class="hljs-keyword">class</span>.<span class="hljs-title">java</span>)</span>
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
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MySpecificEvent</span> </span>{ <span class="hljs-comment">/* Additional fields if needed */</span> }
</pre>
    <p>
        After defining your event, you obtain an instance of
        <code>
            EventBus
        </code>
        and register an object as a subscriber:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">eventBus.register(<span class="hljs-keyword">this</span>)
</pre>
    <p>
        Now that the object is a subscriber, tell it what type of event to subscribe
        to and what it should do when it receives one:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onEvent</span><span class="hljs-params">(event: <span class="hljs-type">MySpecificEvent</span>)</span></span> {
  <span class="hljs-comment">/* Do something */</span>
}
</pre>
    <p>
        Finally, create and post one of those events based on your criteria:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">eventBus.post(event)
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
    <pre lang="kotlin" class="language-kotlin hljs">apiService.getData(someData)
  .subscribeOn(Schedulers.io())
  .observeOn(AndroidSchedulers.mainThread())
  .subscribe (<span class="hljs-comment">/* an Observer */</span>)
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
</div>