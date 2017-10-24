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
            "当我打开一个类的时候，如何可以记得它在做什么，已经如何组合到一起的？" – Future You
        </i>
    </p>
    <p>
        结构性的模式可以帮助你将类和对象组织成易于熟悉的排列，方便执行典型的任务。在Android中常见的两个模式就是
        <em>
            Adapter
        </em>
        和
        <em>
            Facade
        </em>
        。
    </p>
    <h3>
        Adapter
    </h3>
    <p>
        电影阿波罗13中，有一个
        <a href="https://youtu.be/1cYzkyXp0jg" target="_blank" title="Apollo 13">
            著名的场景
        </a>
        ，工程师的团队负责将一个方钉钉入圆孔。这就是对adapter用途很好的一个比方。在软件学的术语中，该模式可以让两个不兼容的类在一起进行工作，将一个类的接口转换为客户所期望的另一个接口。
    </p>
    <p>
        考虑你的app业务逻辑，它可能是一个产品，一个用户，或是一个组合物，也就是那个方钉。同样，
        <code>
            RecyclerView
        </code>
        则是一个所有Android app中都有的基本对象，也就是那个圆洞。
    </p>
    <p>
        在该情况下，你就可以用
        <code>
            RecyclerView.Adapter
        </code>
        的子类来实现所需的方法，让一切work起来：
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
        并不知道Tribble是什么，也从未见过星际迷航的单曲的样子 - 甚至连新电影也是。:] 相反，它是adapter所负责的工作，处理数据，并将
        <code>
            bind
        </code>
        命令发送给正确的
        <code>
            ViewHolder
        </code>
        。
    </p>
    <h3>
        Facade
    </h3>
    <p>
        Facade模式提供了更高层级的接口，让其它的接口更易被使用。下列的图表则展示了更为详尽的细节：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2013/07/facade2.png">
            <img class="aligncenter size-full wp-image-47211" src="https://koenig-media.raywenderlich.com/uploads/2013/07/facade2.png"
            alt="facade2" width="453" height="228" srcset="https://koenig-media.raywenderlich.com/uploads/2013/07/facade2.png 604w, https://koenig-media.raywenderlich.com/uploads/2013/07/facade2-480x241.png 480w"
            sizes="(max-width: 453px) 100vw, 453px">
        </a>
    </p>
    <p>
        如果你的Activity需要一个书籍的列表，它应当可以在
        <i>
            不
        </i>
        了解本地存储，缓存，API客户端等内部机制的情况下，能够访问其中的一个对象。除了可以让你的Activity和Fragment保持简明和整洁，还可以让Future You在对API的实现做出任何改变的时候，不至于影响到Activity。
    </p>
    <p>
        来自Square的
        <a href="http://square.github.io/retrofit/">
            Retrofit
        </a>
        是一个开源的Android库，可以帮助你实现Facade的设计模式，你会创建一个接口来向客户的类提供api的数据，就像这样：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">BooksApi</span> </span>{
  <span class="hljs-meta">@GET(<span class="hljs-meta-string">"books"</span>)</span>
  <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">listBooks</span><span class="hljs-params">()</span></span>: Call&lt;List&lt;Book&gt;&gt;
}
</pre>
    <p>
        客户只要调用
        <code>
            listBooks()
        </code>
        ，然后在回调中接收
        <code>
            Book
        </code>
        对象的列表即可。多么得整洁，总所周知，你可以有一个Tribble的军队来装配列表，并通过线缆将它发送回去。:]
    </p>
    <p>
        这让你可以在不影响到客户端的情况下，进行所有类型的自定义。例如，你可以指定一个定制的JSON解析器，Activity于此并无关系：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> retrofit = Retrofit.Builder()
  .baseUrl(<span class="hljs-string">"http://www.myexampleurl.com"</span>)
  .addConverterFactory(GsonConverterFactory.create())
  .build()

<span class="hljs-keyword">val</span> api = retrofit.create&lt;BooksApi&gt;(BooksApi::<span class="hljs-class"><span class="hljs-keyword">class</span>.<span class="hljs-title">java</span>)</span>
</pre>
    <p>
        注意
        <code>
            GsonConverterFactory
        </code>
        的使用，它会作为一个JSON解析器在背后执行工作。通过Retrofit，你可以进一步地定制关于
        <code>
            Interceptor
        </code>
        和
        <code>
            OkHttpClient
        </code>
        的操作，来控制缓存和日志的行为，且无需客户端了解发了什么。
    </p>
    <p>
        每个对象了解场景背后发生的事越少，Future You就越容易管理app的变化。该模式可以被应用在其它很多的context中，Retrofit只是其中的一种机制。
    </p>
    <h2>
        行为性的模式
    </h2>
    <p>
        <i>
            "那么...我怎么知道哪个类负责什么？" – Future You
        </i>
    </p>
    <p> 
        行为性的模式可以为app不同的功能分配相应的“负责人”。Future You可以使用他们来查找项目的结构和架构。这些模式可以应用在各种范围之下，从两个对象之间到你整个app的架构。通常，一个app都会包含各种各样的行为模式。
    </p>
    <h3>
        Command
    </h3>
    <p>
        在一家印度餐馆中点一些菠菜奶酪，你无需知道将由哪位厨子给你制作的，只需将订单递给服务员，ta就会提交给厨房中下一个有空的厨子来帮你制作。
    </p>
    <p>
        类似的，命令模式可以让你在未知接受者的情况下提出请求。你将请求封装成一个对象并发送出来，而如何完成这个请求则是完全分离的机制。
    </p>
    <p>
        Greenrobot的
        <a href="https://github.com/greenrobot/EventBus" target="_blank" title="EventBus">
            EventBus
        </a>
        是一个流行的Android框架，可以以下列的形式来支持命令模式：
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe.png">
            <img class="aligncenter size-large wp-image-110104" src="https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe-700x262.png"
            alt="EventBus-Publish-Subscribe" width="700" height="262" srcset="https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe-700x262.png 700w, https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe-480x180.png 480w, https://koenig-media.raywenderlich.com/uploads/2015/07/EventBus-Publish-Subscribe.png 1280w"
            sizes="(max-width: 700px) 100vw, 700px">
        </a>
    </p>
    <p>
        <code>
            Event
        </code>
        是一个命令行风格的对象，可以通过app中用户的输入，服务器数据等机制来触发。你还可以创建用来承载数据的子类：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MySpecificEvent</span> </span>{ <span class="hljs-comment">/* Additional fields if needed */</span> }
</pre>
    <p>
        在定义你的event之后，你就获取到一个
        <code>
            EventBus
        </code>
        的实例，并注册一个对象作为subscriber：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">eventBus.register(<span class="hljs-keyword">this</span>)
</pre>
    <p>
        现在这个对象就成为了subscriber，告诉它订阅哪种类型的事件，以及接收到事件后的处理方式：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onEvent</span><span class="hljs-params">(event: <span class="hljs-type">MySpecificEvent</span>)</span></span> {
  <span class="hljs-comment">/* Do something */</span>
}
</pre>
    <p>
        最后，基于你的标准创建并发送事件：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">eventBus.post(event)
</pre>
    <p>
        由于该模式很多都是在运行时进行工作的，Future You追踪这个模式的时候可能会有一点麻烦，除非你进行了很好的测试覆盖。因此，一个经过很好设计的命令模式应当平衡易读性，及易于在将来进行追踪。
    </p>
    <h3>
        观察者
    </h3>
    <p>
        观察者模式定义了对象之间一对多的依赖。当一个对象的状态发生改变的时候，所有与之关联的对象都会被通知到并自动进行更新。
    </p>
    <p>
        这是一个全能的模式，你可以通过它来完成不确定时间的操作，如API的调用；还可以用来响应用户的输入。
    </p>
    <p>
        <a href="https://github.com/ReactiveX/RxAndroid" target="_blank" title="RxAndroid">
            RxAndroid
        </a>
        框架（也就是Reactive Android）可以帮助你在app中实现这个模式：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">apiService.getData(someData)
  .subscribeOn(Schedulers.io())
  .observeOn(AndroidSchedulers.mainThread())
  .subscribe (<span class="hljs-comment">/* an Observer */</span>)
</pre>
    <p>
        简单地说，就是定义一个用来
        <i>
            发送
        </i>
        值的
        <code>
            Observable
        </code>
        对象。你可以一次发送多个值，或作为持续性的流发送，或以任意的速度和持续时间进行发送。
    </p>
    <p>
        <code>
            Subscriber
        </code>
        对象则会
        <i>
            监听
        </i>
        这些值，并在接收到这些值的时候进行处理。例如，你可以在调用API请求时打开订阅者，监听从服务器返回的请求，然后做出相应的处理。
    </p>
    <h3>
        MVC
    </h3>
    <p>
        <em>
            MVC
        </em>
        ，也就是Model View Controller，是当前处于统治地位的跨平台结构模式，在Android中非常易于配置你的项目。在这个模式中的类可分为三大类：
    </p>
    <ul>
        <li>
            <em>
                Model：
            </em>
            是你的数据类。如果你有着
            <code>
                User
            </code>
            或
            <code>
                Product
            </code>
            对象，它们就会模拟真实世界中的东西。
        </li>
        <li>
            <em>
                View:
            </em>
            是你的可视部分的类。用户能看到的所有内容都处于该分类中。
        </li>
        <li>
            <em>
                Controller：
            </em>
            上述两者之间的粘合剂。它负责更新view，接收用户的输入，并使model做出改变。
        </li>
    </ul>
    <p>
        将你的代码拆分为以上的三大类，会大大地有助于代码的解耦和复用。
    </p>
    <p>
        Future You接收到客户的请求，会诸如在app上添加一个新的页面，但只能使用app中已存在的数据，遵循MVC的范例就意味着Future You可以轻松地重用相同的model，只需对view做出改变即可。或者是客户要求Future You将一个花俏的器件从首页移动到详情页中，MVC就可以让其成为一个易于完成的任务。
    </p>
    <p>
        此外，尽可能地将布局和资源的逻辑移动到Android的XML文件中，也可以让你的View层保持干净和整洁。多么得赞！
    </p>
    <p>
        有时你不得不地在Kotlin中进行一些绘图的操作，通过MVC模式就可以将绘制的操作从activity何fragment中分离出来。
    </p>
    <p>
        随着时间流逝，MVC的架构可以帮助Future You更加容易地解决出现的问题。
    </p>
    <h3>
        MVVM（Model View ViewModel）
    </h3>
    <p>
        这个名字看起来如此倒霉和难懂的结构模式，非常类似于MVC，其中的Model和View成分都是相同的。ViewModel对象是model和view层之间的粘合剂，但它负责的部分和Controller是并不相同。相反，它公开了view的一些命令，并将其绑定到model上。当model更新的时候，相应的view就会通过数据绑定进行更新。类似的，当用户和view进行交互的时候，binding就会以相反的方向自动更新model。这种反应模式就消除了很多的“胶水代码”。
    </p>
    <p>
        MVVM模式正在变得越来越流行，但它是最近才添加到模式库中的。Google最近引入了这个模式，作为
        <a href="https://developer.android.com/topic/libraries/architecture/viewmodel.html"
        target="_blank" title="Android Architecture Components">
            架构组件
        </a>
        库的一部分！只要持续关注下去，Future You一定就会爱上它！:]
    </p>
    <h3>
        清洁的架构
    </h3>
    <p>
        <em>
            清洁的架构
        </em>
        是一个比MVC和MVVM更高的抽象层级。它描述了整体性的app架构：app的各层（业务对象，用例，演示者，数据存储，和UI）之间的通信方式。它非常类似于
        <a href="http://alistair.cockburn.us/Hexagonal+architecture" target="_blank"
        title="Hexagonal architecture">
            六边形架构
        </a>
        及其它的app架构。在外部表示和UI层面，MVC和MVVM存在于清洁架构的内部。
    </p>
    <p>
        原始清洁架构的定义在
        <a href="https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html"
        target="_blank" title="Clean Architecture">
            这里
        </a>
        ，很多的例子都可以在Android的清洁架构中被找到，包括
        <a href="https://fernandocejas.com/2015/07/18/architecting-android-the-evolution/"
        target="_blank" title="Architecting Android">
            Architecting Android…The evolution
        </a>
        。
    </p>
    <h2>
        从这儿去向哪里？
    </h2>
    <p>
        尽管与最新的flashy API并驾齐驱的感觉非常好，但持续地更新app，会很快地导致重新设计疲劳。尽早地投资软件设计模式，就能够在开发时间上获得回报，你就可以用较少的努力来获取更多的工作。
    </p>
    <p>
        推荐阅读类似
        <a href="https://en.wikipedia.org/wiki/Design_Patterns">
            Design Patterns by the “Gang of Four.”
        </a>
        这样的永恒经典。相比于“材料设计”或“Android Wear”，它可能会显得比较“老”，但记录了很多在Android之前的非常有用的设计模式！
    </p>
</div>