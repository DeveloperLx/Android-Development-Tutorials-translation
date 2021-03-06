# 用RxAndroid进行响应式编程 - Kotlin: 介绍
---
#### [原文地址](https://www.raywenderlich.com/170233/reactive-programming-rxandroid-kotlin-introduction) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志：
            </em>
            本教程已由Irina Galata更新至Kotlin，Android 26 （Oreo），及Android Studio 3.0 Beta 5版本。原教程由Artem Kholodnyi编写。
        </p>
    </div>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-250x250.png"
            alt="AndroidReactive-feature" width="250" height="250" class="alignright size-thumbnail wp-image-147614"
            srcset="https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/11/AndroidReactive-feature-128x128.png 128w"
            sizes="(max-width: 250px) 100vw, 250px">
        </a>
        他们说，在人生中，你应当怀抱着一个主动的心态。然而，这点并不适用于Android的编程！:]
    </p>
    <p>
        响应式编程和其它的API不同。它是一个非常有用且全新的范式。
        <em>
            RxJava
        </em>
        是Android上响应式编程的实现。Android是开启你响应式世界的一个完美起点。甚至，使用
        <em>
            RxAndroid
        </em>
        还可以让其变得更容易，这是一个封装了异步UI事件，让它变得更像RxJava的库。
    </p>
    <p>
        不要害怕 - 我敢打赌，即使你还没有意识到，响应式编程的基本概念你也早已有所了解。:]
    </p>
    <div class="note">
        <p>
            <em>
                注意：
            </em>
            本教程要求你对Android和Kotlin的知识有一定的了解。为了加快这个过程，请首先访问我们的
            <a href="https://www.raywenderlich.com/category/android" sl-processed="1">
                Android开发教程
            </a>
            ，待准备好之后再回到本教程。
        </p>
    </div>
    <p>
        在本教程中，你会了解到下列的知识：
    </p>
    <ul>
        <li>
            理解什么是响应式编程
        </li>
        <li>
            定义一个
            <em>
                observable
            </em>
        </li>
        <li>
            将类似按钮点击，文本框内容发生变化等异步事件转化为observable
        </li>
        <li>
            转化observable项目
        </li>
        <li>
            过滤observable项目
        </li>
        <li>
            指定执行代码所应在的线程
        </li>
        <li>
            将几个observable合并为一个
        </li>
    </ul>
    <p>
        希望你是一个喜欢奶酪的人 - 因为你将构建一个发现奶酪的应用，借此学习上述的概念！:]
    </p>
    <h2>
        入门
    </h2>
    <p>
        下载
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/cheesefinder-starter.zip"
        sl-processed="1">
            本教程的初始项目
        </a>
        并在Android Studio 3.0 Beta 5或以上的版本中打开它。
    </p>
    <p>
        我们将会编写的所有代码都会在
        <em>
            CheeseActivity.kt
        </em>
        中。
        <code>
            CheeseActivity
        </code>
        类继承自
        <code>
            BaseSearchActivity
        </code>
        ，花一点时间来看下
        <code>
            BaseSearchActivity
        </code>
        ，它已经为你准备好了下列的功能：
    </p>
    <ul>
        <li>
            <code>
                showProgress()
            </code>
            ：一个方法，用来展示进度条...
        </li>
        <li>
            <code>
                hideProgress()
            </code>
            ：...用来隐藏进度条的方法。
        </li>
        <li>
            <code>
                showResult(result: List)
            </code>
            ：用来展示奶酪列表的方法。
        </li>
        <li>
            <code>
                cheeseSearchEngine
            </code>
            ：一个字段，它是
            <code>
                CheeseSearchEngine
            </code>
            的实例。它有一个
            <code>
                search
            </code>
            方法供你在想要搜索奶酪的时候使用。
        </li>
    </ul>
    <p>
        在Android设备或模拟器上运行项目。你会看到一个空空如也的搜索页面：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/starter-300x500.png"
        alt="starter-300x500" width="300" height="533" class="aligncenter size-full wp-image-143327"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/starter-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/starter-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/starter-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <h2>
        神马是响应式编程？
    </h2>
    <p>
        在创建你的第一个observable前，首先来学习一些理论知识吧。:]
    </p>
    <p>
        在
        <em>
            命令式
        </em>
        编程中，一个表达式只会被执行一次，且一个值会分配给一个变量：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">var</span> x = <span class="hljs-number">2</span>
<span class="hljs-keyword">var</span> y = <span class="hljs-number">3</span>
<span class="hljs-keyword">var</span> z = x * y <span class="hljs-comment">// z is 6</span>

x = <span class="hljs-number">10</span>
<span class="hljs-comment">// z is still 6</span>
</pre>
    <p>
        而在
        <em>
        响应式
            reactive
        </em>
        编程中，则会
        <i>
            响应值的变化
        </i>
        。
    </p>
    <p>
        虽然你还未意识到 - 但你其实早已进行过一些响应式编程。
    </p>
    <ul>
        <li>
            在电子表格中定义单元格的
            <em>
                值
            </em>
            ，就类似于在命令式编程中定义变量。
        </li>
        <li>
            而在电子表格中定义单元格的
            <em>
                表达式
            </em>
            就类似于在响应式编程中定义并操作observable。
        </li>
    </ul>
    <p>
        用下面的电子表格来实现上述的例子：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/reactive-spreadsheet-1-480x218.png"
        alt="" width="249" height="88" class="alignnone size-medium wp-image-171516">
    </p>
    <p>
        这个电子表格将B1的值定义为2，B2的值定义为3，B3则定义成一个表示式，让它的值为B1、B2中值的乘积。当表达式引用到的任一成分的值发生变化的时候，这个变化就会被表达式观察到，B3中的值就会重新计算并展示出来：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/reactive-spreadsheet-2.png"
        alt="" width="249" height="8" class="alignnone size-full wp-image-171515">
    </p>
    <h2>
        RxJava和RxKotlin的差别
    </h2>
    <p> 
        正如你所知的，由于Kotlin语言和Java是兼容的，在Kotlin的项目中使用Java的库是OK的。那这样的话，为何还要创建RxKotlin这个库？RxKotlin是RxJava的Kotlin封装，同时还提供了大量有用的扩展功能。实际上，RxKotlin可以使RxJava的用法更加Kotlin化。
    </p>
    <p>
        在本文中，我们会着重于RxJava，因为它是理解响应式编程的关键，当然，你学到的一切同样可以应用到RxKotlin上。
    </p>
    <div class="note">
        <em>
            注意：
        </em>
        要特别地关注
        <code>
            build.gradle
        </code>
        文件和项目的依赖关系。除了UI库之外，它还包含了
        <code>
            RxKotlin
        </code>
        和
        <code>
            RxAndroid
        </code>
        的包。我们无需在这里明确地指定
        <code>
            RxJava
        </code>
        ，因为
        <code>
            RxKotlin
        </code>
        早已包含了它。
    </div>
    <h2>
        RxJava Observable合约
    </h2>
    <p>
        RxJava使用了
        <em>
            观察者模式
        </em>
        。
    </p>
    <div class="note">
        <em>
            注意
        </em>
        ：要复习有关观察者模式的相关内容，请访问我们的
        <a href="https://github.com/DeveloperLx/Android-Development-Tutorials-translation/blob/master/Common%20Design%20Patterns%20for%20Android%20with%20Kotlin.md"
        target="_blank" sl-processed="1">
            Android的常用设计模式 - Kotlin
        </a>
        。
    </div>
    <p>
        在观察者模式中，你会有实现了两个关键的RxJava interface：
        <code>
            Observable
        </code>
        和
        <code>
            Observer
        </code>
        的对象。当
        <code>
            Observable
        </code>
        的状态发生变化的时候，所有的
        <code>
            Observer
        </code>
        对象就会收到相应的通知。
    </p>
    <p>
        而在
        <code>
            Observable
        </code>
        interface中的这个方法就是
        <code>
            subscribe()
        </code>
        了，一个
        <code>
            Observer
        </code>
        调用这个方法就可以订阅这个消息。
    </p>
    <p>
        从这点上看，
        <code>
            Observer
        </code>
        interface有三个方法可以在
        <code>
            Observable
        </code>
        需要时被调用：
    </p>
    <ul>
        <li>
            <code>
                onNext(T value)
            </code>
            为
            <code>
                Observer
            </code>
            提供了一个类型为T的新的item
        </li>
        <li>
            <code>
                onComplete()
            </code>
            会通知
            <code>
                Observer
            </code>
            <code>
                Observable
            </code>
            已完成了发送item
        </li>
        <li>
            <code>
                onError(Throwable e)
            </code>
            通知
            <code>
                Observer
            </code>
            <code>
                Observable
            </code>
            遇到了一个错误
        </li>
    </ul>
    <p>
        一般来说，一个行为良好的
        <code>
            Observable
        </code>
        可以发出0个或多个item，然后接着发出completion或是error。
    </p>
    <p>
        听起来有点复杂，但一些
        <em>
            marble diagrams
        </em>
        可以对其进行清理。
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/network-request-650x186.png"
        alt="network-request" width="650" height="186" class="aligncenter size-large wp-image-142657"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/network-request-650x186.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/08/network-request-480x137.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/08/network-request.png 700w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        圆圈代表了从observable发射一个item，而黑色的截止线则代表completion或error。拿一个例子来说，网络请求observable。这个请求通常会发送一个item（response）并立即再发送completes。
    </p>
    <p>
        一个鼠标移动的observable会不断地发送鼠标的坐标，但永远都不会发送complete：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/mouse-coords-650x186.png"
        alt="mouse-coords" width="650" height="186" class="aligncenter size-large wp-image-142659"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/mouse-coords-650x186.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/08/mouse-coords-480x137.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/08/mouse-coords.png 700w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        observable发送completed之后就不能再发送任何item了。下面是一个违反了
        <i>
            Observable contract
        </i>
        的行为异常的observable的例子：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/misbehaving-stream-650x186.png"
        alt="misbehaving-stream" width="650" height="186" class="aligncenter size-large wp-image-142660"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/misbehaving-stream-650x186.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/08/misbehaving-stream-480x137.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/08/misbehaving-stream.png 700w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        这是一个非常糟糕的observable，因为它违反了Observable的合约：它在发送completion后还发送了一个item。
    </p>
    <h2>
        如何创建一个Observable
    </h2>
    <p>
        这里有很多的库，可以帮你创建几乎任何类型事件的observable。然而，有时你只是想封装自己的事件。此外，这还是一个非常棒的学习路径！
    </p>
    <p>
        你将使用
        <code>
            Observable.create()
        </code>
        方法来创建Observable。以下是它的签名：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-function">Observable&lt;T&gt; <span class="hljs-title">create</span><span class="hljs-params">(ObservableOnSubscribe&lt;T&gt; source)</span>
</span></pre>
    <p>
        非常得简明，但含义是什么呢？什么是“Source？” 要理解这个签名，你需要知道
        <code>
            ObservableOnSubscribe
        </code>
        是什么。它是一个interface，其合约是：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">ObservableOnSubscribe</span>&lt;<span class="hljs-title">T</span>&gt; </span>{
  <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">subscribe</span><span class="hljs-params">(ObservableEmitter&lt;T&gt; e)</span> <span class="hljs-keyword">throws</span> Exception</span>;
}
</pre>
    <p>
        就像J.J. Abrams中的一集“Lost”或“Westworld”一样，回答了一些问题，却无可避免地提出了更多的问题。因此“source”就是你所需创建的
        <code>
            Observable
        </code>
        ，需要暴露出一个
        <code>
            subscribe()
        </code>
        方法，反过来在调用它的时候，就需要提供一个“emitter”作为参数。那么，emitter又是什么呢？
    </p>
    <p>
        RxJava的
        <code>
            Emitter
        </code>
        interface非常类似于
        <code>
            Observer
        </code>
        ：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Emitter</span>&lt;<span class="hljs-title">T</span>&gt; </span>{
  <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">onNext</span><span class="hljs-params">(T value)</span></span>;
  <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">onError</span><span class="hljs-params">(Throwable error)</span></span>;
  <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">onComplete</span><span class="hljs-params">()</span></span>;
}
</pre>
    <p>
        特别地，
        <code>
            ObservableEmitter
        </code>
        还提供了取消订阅的方法。
    </p>
    <p>
        为了让整个的情形更加形象化，想像一个水龙头调节水流的情形。这个水龙头就像是一个
        <code>
            Observable
        </code>
        ，如果你有接收的方法，它就会把水留给你。你构建了一个可以打开和关闭的手龙头，它就像是
        <code>
            ObservableEmitter
        </code>
        ，通过
        <code>
            Observable.create()
        </code>
        中的水管来将其连接起来，构成了一个很棒的装置。:]
    </p>
    <p>
        这个例子可以减少情形的抽象性，使其变得更清楚。是时候来创建你的第一个observable了！:]
    </p>
    <h2>
        观察按钮点击事件
    </h2>
    <p>
        在
        <code>
            CheeseActivity
        </code>
        类中添加下列的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">createButtonClickObservable</span><span class="hljs-params">()</span></span>: Observable&lt;String&gt; {
  <span class="hljs-comment">// 2</span>
  <span class="hljs-keyword">return</span> Observable.create { emitter -&gt;
    <span class="hljs-comment">// 3</span>
    searchButton.setOnClickListener {
      <span class="hljs-comment">// 4</span>
      emitter.onNext(queryEditText.text.toString())
    }
    <span class="hljs-comment">// 5</span>
    emitter.setCancellable {
      <span class="hljs-comment">// 6</span>
      searchButton.setOnClickListener(<span class="hljs-literal">null</span>)
    }
  }
}
</pre>
    <p>
        输入上述的代码后，你的import语句应当看起来像下面这样子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">import</span> io.reactivex.Observable
<span class="hljs-keyword">import</span> kotlinx.android.synthetic.main.activity_cheeses.*
</pre>
    <p>
        这样你就导入了正确的
        <code>
            Observable
        </code>
        类，并通过
        <em>
            Kotlin Android Extensions
        </em>
        获取了对view对象的使用。
    </p>
    <p>
        上述的代码：
    </p>
    <ol>
        <li>
            声明了一个方法，返回一个可以发送字符串的observable。
        </li>
        <li>
            用
            <code>
                Observable.create()
            </code>
            创建了一个observable，并为它提供一个新的
            <code>
                ObservableOnSubscribe
            </code>
            。
        </li>
        <li>
            在
            <code>
                searchButton
            </code>
            上设置一个
            <code>
                OnClickListener
            </code>
            。
        </li>
        <li>
            当点击事件发生的时候，就会调用emitter的
            <code>
                onNext
            </code>
            方法，并将当前
            <code>
                queryEditText
            </code>
            的值传给它。
        </li>
        <li>
            在Java或Kotlin中持有引用可能会造成内存泄漏。在listener不在被需要的时候，及时将其移除是一个非常棒的习惯。但在创建自己的
            <code>
                Observable
            </code>
            时，该调用什么呢？为解决这个问题，
            <code>
                ObservableEmitter
            </code>
            中含有
            <code>
                setCancellable()
            </code>
            。重写
            <code>
                cancel()
            </code>
            ，他会在Observable被disposed后调用，例如在Observable被completed，或观察者取消对其调用时调用。
        </li>
        <li>
            对于
            <code>
                OnClickListener
            </code>
            ，代码会在
            <code>
                setOnClickListener(null)
            </code>
            中移除listener。
        </li>
    </ol>
    <p>
        现在你已声明了Observable，接下来就应该设置对其的订阅了。在此之前，你需要学习另一个interface，
        <code>
            Consumer
        </code>
        。它提供了一个简单的方式，来接受来自emitter的值。
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Consumer</span>&lt;<span class="hljs-title">T</span>&gt; </span>{
  <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">accept</span><span class="hljs-params">(T t)</span> <span class="hljs-keyword">throws</span> Exception</span>;
}
</pre>
    <p>
        当你想设置订阅Observable的时候，这个interface是非常得方便的。
    </p>
    <p>
        这个
        <code>
            Observable
        </code>
        interface需要几个版本的
        <code>
            subscribe()
        </code>
        ，它们都有着不同的参数。例如，如果你喜欢的话，可以传递一个完整的
        <code>
            Observer
        </code>
        ，但接下来你就需要实现所有必须的方法。
    </p>
    <p>
        如果你的观察者订阅信号的所有需求，只是响应发送到
        <code>
            onNext()
        </code>
        的值，你就可以使用
        <code>
            subscribe()
        </code>
        这个版本，它接收了一个单独的
        <code>
            Consumer
        </code>
        （这个参数甚至被命名为
        <code>
            onNext
        </code>
        ，让连接变得更加清楚）。
    </p>
    <p>
        你会在activity的
        <code>
            onStart()
        </code>
        方法中订阅时完成它。添加下列的代码到
        <em>
            CheeseActivity.kt
        </em>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onStart</span><span class="hljs-params">()</span></span> {
  <span class="hljs-keyword">super</span>.onStart()
  <span class="hljs-comment">// 1</span>
  <span class="hljs-keyword">val</span> searchTextObservable = createButtonClickObservable()

  searchTextObservable
      <span class="hljs-comment">// 2</span>
      .subscribe { query -&gt;
        <span class="hljs-comment">// 3</span>
        showResult(cheeseSearchEngine.search(query))
      }
}
</pre>
    <p>
        下面是一步步的解释：
    </p>
    <ol>
        <li>
            首先，调用你刚写的方法来创建一个observable。
        </li>
        <li>
            用
            <code>
                subscribe()
            </code>
            方法对observable发起订阅，并提供一个简单的
            <code>
                Consumer
            </code>
            。
        </li>
        <li>
            最后，执行搜索并将结果展示出来。
        </li>
    </ol>
    <p>
        运行app。输入要搜索的文本并按下
        <em>
            Search
        </em>
        按钮。在一个模拟的延迟之后（查看
        <em>
            CheeseSearchEngine
        </em>
        ），你就可以看到一个对应于你请求的奶酪的列表：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500.png"
        alt="enter-and-press-300x500" width="300" height="533" class="aligncenter size-full wp-image-143326"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <p>
        怎么样，还不错吧！:]
    </p>
    <h2>
        RxJava线程模型
    </h2>
    <p>
        你已经完成了响应式编程的第一次尝试。但还留下了一个问题：当搜索按钮被按下的时候，UI会被卡住几秒。
    </p>
    <p>
        你可能还发现了Android监视器中的以下代码：
    </p>
    <pre lang="text" class="language-text">&gt; 08-24 14:36:34.554 3500-3500/com.raywenderlich.cheesefinder I/Choreographer: Skipped 119 frames!  The application may be doing too much work on its main thread.
</pre>
    <p>
        这是因为搜索的操作
        <code>
            搜索
        </code>
        的操作是在主线程上被执行的。如果这个搜索是一个真的网络请求，这个app就会崩溃，并抛出一个
        <code>
            NetworkOnMainThreadException
        </code>
        的异常。现在是时候去修复它了。
    </p>
    <p>
        类似于
        <code>
            AsyncTask
        </code>
        ，关于RxJava一个流行的传说，就是默认情况下它是多线程的。然而，如果没有特别的说明，RxJava的所有逻辑都是在同一线程中进行调用的。
    </p>
    <p>
        你可以使用
        <code>
            subscribeOn
        </code>
        和
        <code>
            observeOn
        </code>
        运算符来改变这个行为。
    </p>
    <p>
        <code>
            subscribeOn
        </code>
        应当只可以在操作符链中被调用一次。如果不是的话，就只有第一次调用会成功。
        <code>
            subscribeOn
        </code>
        指定了observable可以在哪个线程被订阅（也就是创建）。如果要使用一个从Android View发送事件的observable，你需要确保在Android的UI线程上进行调用。
    </p>
    <p>
        另一方面，在调用链中多次地对
        <code>
            observeOn
        </code>
        进行调用也是可以的。
        <code>
            observeOn
        </code>
        可以指定调用链中下一个操作对象将被执行在的线程。例如：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">myObservable <span class="hljs-comment">// observable will be subscribed on i/o thread</span>
      .subscribeOn(Schedulers.io())
      .observeOn(AndroidSchedulers.mainThread())
      .map { <span class="hljs-comment">/* this will be called on main thread... */</span> }
      .doOnNext{ <span class="hljs-comment">/* ...and everything below until next observeOn */</span> }
      .observeOn(Schedulers.io())
      .subscribe { <span class="hljs-comment">/* this will be called on i/o thread */</span> }
</pre>
    <p>
        最有用的调度者是：
    </p>
    <ul>
        <li>
            <code>
                Schedulers.io()
            </code>
            ：适用于I/O相关的工作，诸如网络请求或磁盘操作等。
        </li>
        <li>
            <code>
                Schedulers.computation()
            </code>
            ：适用于计算型的任务，如事件循环和回调处理等。
        </li>
        <li>
            <code>
                AndroidSchedulers.mainThread()
            </code>
            可以在UI线程上执行下一个操作符。
        </li>
    </ul>
    <h2>
        Map操作符
    </h2>
    <p>
        <code>
            map
        </code>
        操作符会作用于由observable发出的每个item，并返回另一个发送处理item后结果的observable。你还需要这个来修复线程问题。
    </p>
    <p>
        如果你有一个可以发送
        <code>
            numbers
        </code>
        的observable，它发送了如下的内容：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/map-0-1.png"
        alt="map-0" width="500" height="214" class="aligncenter size-full wp-image-142688"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/map-0-1.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/08/map-0-1-480x205.png 480w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        如果你将
        <code>
            map
        </code>
        实现如下：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">numbers.map { number -&gt; number * number }
</pre>
    <p>
        结果就像下面这个样子：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/map-1-1.png"
        alt="map-1" width="500" height="214" class="aligncenter size-full wp-image-142689"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/map-1-1.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/08/map-1-1-480x205.png 480w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        这是一个用少量的代码就可以迭代多个item的方便的方法。让我们来使用一下吧！
    </p>
    <p>
        在
        <code>
            CheeseActivity
        </code>
        类中将
        <code>
            onStart()
        </code>
        方法修改为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onStart</span><span class="hljs-params">()</span></span> {
  <span class="hljs-keyword">super</span>.onStart()

  <span class="hljs-keyword">val</span> searchTextObservable = createButtonClickObservable()

  searchTextObservable
      <span class="hljs-comment">// 1</span>
      .subscribeOn(AndroidSchedulers.mainThread())
      <span class="hljs-comment">// 2</span>
      .observeOn(Schedulers.io())
      <span class="hljs-comment">// 3</span>
      .map { cheeseSearchEngine.search(it) }
      <span class="hljs-comment">// 4</span>
      .observeOn(AndroidSchedulers.mainThread())
      .subscribe {
        showResult(it)
      }
}
</pre>
    <p>
        上述代码：
    </p>
    <ol>
        <li>
            首先，指定的代码应当在主线程而非I/O线程上启动。在Android中，所有关于
            <code>
                View
            </code>
            的代码都应当在主线程上被执行。
        </li>
        <li>
            指定应当在I/O线程上调用下一个操作符。
        </li>
        <li>
            对于每次的搜索，都会返回一个结果的列表。
        </li>
        <li>
            最后，确保将结果传递到主线程的列表上
        </li>
    </ol>
    <p>
        运行项目。现在，即使正在进行搜索，UI也会保持可响应的状态。
    </p>
    <h2>
        用doOnNext来展示进度条
    </h2>
    <p>
        是时候该展示进度条了！
    </p>
    <p>
        因此你需要一个
        <code>
            doOnNext
        </code>
        操作符。
        <code>
            doOnNext
        </code>
        需要一个
        <code>
            Consumer
        </code>
        以便在每次收到observable发送的消息时进行处理。
    </p>
    <p>
        还是在
        <code>
            CheeseActivity
        </code>
        类中，将
        <code>
            onStart()
        </code>
        方法修改为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onStart</span><span class="hljs-params">()</span></span> {
  <span class="hljs-keyword">super</span>.onStart()

  <span class="hljs-keyword">val</span> searchTextObservable = createButtonClickObservable()

  searchTextObservable
      <span class="hljs-comment">// 1</span>
      .observeOn(AndroidSchedulers.mainThread())
      <span class="hljs-comment">// 2</span>
      .doOnNext { showProgress() }
      .observeOn(Schedulers.io())
      .map { cheeseSearchEngine.search(it) }
      .observeOn(AndroidSchedulers.mainThread())
      .subscribe {
        <span class="hljs-comment">// 3</span>
        hideProgress()
        showResult(it)
      }
}
</pre>
    <p>
        一条一条来看：
    </p>
    <ol>
        <li>
            让调用链中的下一个操作符在主线程上执行。
        </li>
        <li>
            添加
            <code>
                doOnNext
            </code>
            操作符，这样
            <code>
                showProgress()
            </code>
            就会在每次发送新item时被调用。
        </li>
        <li>
            展示结果时，不要忘记调用
            <code>
                hideProgress()
            </code>
            。
        </li>
    </ol>
    <p>
        运行项目。开始搜索时，就会出现进度条：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500.png"
        alt="progressbar" width="300" height="533" class="aligncenter size-full wp-image-143328"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <h2>
        观察文本的变化
    </h2>
    <p>
        如果你希望在用户输入文本时，就自动执行搜索，就像Google那样，该怎么做呢？
    </p>
    <p>
        首先，你需要订阅
        <code>
            TextView
        </code>
        文本的变化。添加下列的方法到
        <code>
            CheeseActivity
        </code>
        类中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-comment">// 1</span>
<span class="hljs-keyword">private</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">createTextChangeObservable</span><span class="hljs-params">()</span></span>: Observable&lt;String&gt; {
  <span class="hljs-comment">// 2</span>
  <span class="hljs-keyword">val</span> textChangeObservable = Observable.create&lt;String&gt; { emitter -&gt;
    <span class="hljs-comment">// 3</span>
    <span class="hljs-keyword">val</span> textWatcher = <span class="hljs-keyword">object</span> : TextWatcher {
      <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">afterTextChanged</span><span class="hljs-params">(s: <span class="hljs-type">Editable</span>?)</span></span> = <span class="hljs-built_in">Unit</span>
      <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">beforeTextChanged</span><span class="hljs-params">(s: <span class="hljs-type">CharSequence</span>?, start: <span class="hljs-type">Int</span>, count: <span class="hljs-type">Int</span>, after: <span class="hljs-type">Int</span>)</span></span> = <span class="hljs-built_in">Unit</span>
      <span class="hljs-comment">// 4</span>
      <span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onTextChanged</span><span class="hljs-params">(s: <span class="hljs-type">CharSequence</span>?, start: <span class="hljs-type">Int</span>, count: <span class="hljs-type">Int</span>, after: <span class="hljs-type">Int</span>)</span></span> {
        s?.toString()?.let { emitter.onNext(it) }
      }
    }
    <span class="hljs-comment">// 5</span>
    queryEditText.addTextChangedListener(textWatcher)
    <span class="hljs-comment">// 6</span>
    emitter.setCancellable {
      queryEditText.removeTextChangedListener(textWatcher)
    }
  }

  <span class="hljs-comment">// 7</span>
  <span class="hljs-keyword">return</span> textChangeObservable
}
</pre>
    <p>
        一步一步来看上述的代码：
    </p>
    <ol>
        <li>
            声明一个返回用来观察文本变化的observable的方法。
        </li>
        <li>
            用
            <code>
                create()
            </code>
            创建一个
            <code>
                textChangeObservable
            </code>
            ，并传递
            <code>
                ObservableOnSubscribe
            </code>
            。
        </li>
        <li>
            当观察者进行订阅时，第一件事就是创建
            <code>
                TextWatcher
            </code>
            。
        </li>
        <li>
            你不需要关心
            <code>
                beforeTextChanged()
            </code>
            和
            <code>
                afterTextChanged()
            </code>
            。当用户进行输入的时候，就会触发
            <code>
                onTextChanged()
            </code>
            ，并传递新的文本值给观察者。
        </li>
        <li>
            通过调用
            <code>
                addTextChangedListener()
            </code>
            来添加观察者到
            <code>
                TextView
            </code>
            上。
        </li>
        <li>
            不要忘记移除你的观察者。因此，调用
            <code>
                emitter.setCancellable()
            </code>
            并重写
            <code>
                cancel()
            </code>
            来调用
            <code>
                removeTextChangedListener()
            </code>
            。
        </li>
        <li>
            最后，返回创建好的observable。
        </li>
    </ol>
    <p>
        实际地来看一下这个observable吧，将
        <code>
            CheeseActivity
        </code>
        类的
        <code>
            onStart()
        </code>
        方法中，
        <code>
            searchTextObservable
        </code>
        的声明替换为下列代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> searchTextObservable = createTextChangeObservable()
</pre>
    <p>
        运行app。你就会看到在
        <code>
            TextView
        </code>
        输入文本时，搜索就开始执行了：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500.png"
        alt="text-view-changes-simple" width="300" height="533" class="aligncenter size-full wp-image-143329"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <h2>
        基于长度过滤查询
    </h2>
    <p>
        在搜索文本只有一个字母时就进行搜索是没有意义的。要修复这点，我们将引入强有力的
        <code>
            filter
        </code>
        操作符。
    </p>
    <p>
        <code>
            filter
        </code>
        只会传递那些满足特定条件的item。
        <code>
            filter
        </code>
        会接受一个
        <code>
            Predicate
        </code>
        ，它是一个interface，声明了判断输入的内容是否可被传递的方法，并带有一个
        <code>
            boolean
        </code>
        类型的返回值。在本例中，这个Predicate就会接收一个
        <code>
            String
        </code>
        类型的值，如果字符串的长度大于等于2的话，就返回
        <code>
            true
        </code>
        。
    </p>
    <p>
        在
        <code>
            createTextChangeObservable()
        </code>
        中将
        <code>
            return textChangeObservable
        </code>
        替换为如下的代码：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">return</span> textChangeObservable.filter { it.length &gt;= <span class="hljs-number">2</span> }
</pre>
    <p>
        一切都和之前的行为完全一致，除了
        <code>
            length
        </code>
        少于
        <code>
            2
        </code>
        时不会被发送到调用链上。
    </p>
    <p>
        运行app，你会发现只有输入到第二个字符时，才看得到搜索的结果：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/filter-0-300x500.png"
        alt="filter-0" width="300" height="533" class="aligncenter size-full wp-image-143330"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/filter-0-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/filter-0-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/filter-0-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/filter-1-300x500.png"
        alt="filter-1" width="300" height="533" class="aligncenter size-full wp-image-143331"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/filter-1-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/filter-1-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/filter-1-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <h2>
        防抖动操作符
    </h2>
    <p>
        你并不希望在每次改变一个字符时，都向服务器发送新的请求。
    </p>
    <p>
        <code>
            debounce
        </code>
        是显示响应式范式真正能量的操作符之一。就像
        <code>
            filter
        </code>
        这个操作符一样，
        <code>
            debounce
        </code>
        会过滤由observable所发送的item。但这个item是否被过滤掉，并非基于这个item是
        <i>
            什么
        </i>
        ，而是它在
        <i>
            什么时候
        </i>
        被发送。
    </p>
    <p>
        <code>
            debounce
        </code>
        会在每个item发送后等待一定的时间，看是否有下一个item被发送。如果没有的话，才会最终发送这个item：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674-650x219.png"
        alt="719f0e58_1472502674" width="650" height="219" class="aligncenter size-large wp-image-142671"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674-650x219.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674-480x161.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674.png 812w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        在
        <code>
            createTextChangeObservable()
        </code>
        中，添加
        <code>
            debounce
        </code>
        操作符，就在
        <code>
            filter
        </code>
        的下面。现在
        <code>
            return
        </code>
        语句看起来就像下面这个样子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">return</span> textChangeObservable
      .filter { it.length &gt;= <span class="hljs-number">2</span> }
      .debounce(<span class="hljs-number">1000</span>, TimeUnit.MILLISECONDS) <span class="hljs-comment">// add this line</span>
</pre>
    <p>
        运行程序。你会看到，只有停止快速改变文本时，才会真正地开始搜索：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/debounce-500px-1.gif"
        alt="debounce-500px" width="300" height="533" class="aligncenter size-full wp-image-143337">
    </p>
    <p>
        <code>
            debounce
        </code>
        会在发送最新的查询文本前，等待1000毫秒。
    </p>
    <h2>
        合并操作符
    </h2>
    <p>
        你首先创建了一个用来响应按钮点击事件的observable，然后又实现了一个observable来响应文本字段的变化。但你如何一起响应它们呢？
    </p>
    <p>
        有很多操作符可以将这些observable合并到一起。其中最简单且最有用的一个就是
        <code>
            merge
        </code>
        了。
    </p>
    <p>
        <code>
            merge
        </code>
        可以将来自两个或多个observable中的item合并成一个observable：
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259-650x296.png"
        alt="ae08759b_1472502259" width="650" height="296" class="aligncenter size-large wp-image-142669"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259-650x296.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259-480x218.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259.png 809w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        将
        <code>
            onStart()
        </code>
        的开头修改为如下的样子：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">val</span> buttonClickStream = createButtonClickObservable()
<span class="hljs-keyword">val</span> textChangeStream = createTextChangeObservable()

<span class="hljs-keyword">val</span> searchTextObservable = Observable.merge&lt;String&gt;(buttonClickStream, textChangeStream)
</pre>
    <p>
        运行app。测试一下文本框和搜索按钮，当输入两个及以上的字符，或按下搜索按钮的时候，就会开始进行搜索了。
    </p>
    <h2>
        RxJava和Activity/Fragment的声明周期
    </h2>
    <p>
        还记得那些你设置的
        <code>
            setCancellable
        </code>
        方法么？它们直到observable被取消订阅的时候才会被调用。
    </p>
    <p>
        调用
        <code>
            Observable.subscribe()
        </code>
        会返回一个
        <code>
            Disposable
        </code>
        。
        <code>
            Disposable
        </code>
        是一个interface，其中含有两个方法：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Disposable</span> </span>{
  <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">dispose</span><span class="hljs-params">()</span></span>;  <span class="hljs-comment">// ends a subscription</span>
  <span class="hljs-function"><span class="hljs-keyword">boolean</span> <span class="hljs-title">isDisposed</span><span class="hljs-params">()</span></span>; <span class="hljs-comment">// returns true if resource is disposed (unsubscribed)</span>
}
</pre>
    <p>
        添加下列的property到
        <code>
            CheeseActivity
        </code>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-keyword">private</span> <span class="hljs-keyword">lateinit</span> <span class="hljs-keyword">var</span> disposable: Disposable
</pre>
    <p>
        在
        <code>
            onStart()
        </code>
        中，使用下列的代码将
        <code>
            subscribe()
        </code>
        的返回值设置为
        <code>
            disposable
        </code>
        （只有第一行的代码发生过变化）：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">disposable = searchTextObservable <span class="hljs-comment">// change this line</span>
      .observeOn(AndroidSchedulers.mainThread())
      .doOnNext { showProgress() }
      .observeOn(Schedulers.io())
      .map { cheeseSearchEngine.search(it) }
      .observeOn(AndroidSchedulers.mainThread())
      .subscribe {
        hideProgress()
        showResult(it)
      }
</pre>
    <p>
        由于你是在
        <code>
            onStart()
        </code>
        中订阅的observable，因此
        <code>
            onStop()
        </code>
        就是一个取消订阅的很好地方。
    </p>
    <p>
        添加下列的代码到
        <em>
            CheeseActivity.kt
        </em>
        中：
    </p>
    <pre lang="kotlin" class="language-kotlin hljs"><span class="hljs-meta">@Override</span>
<span class="hljs-keyword">override</span> <span class="hljs-function"><span class="hljs-keyword">fun</span> <span class="hljs-title">onStop</span><span class="hljs-params">()</span></span> {
  <span class="hljs-keyword">super</span>.onStop()
  <span class="hljs-keyword">if</span> (!disposable.isDisposed) {
    disposable.dispose()
  }
}
</pre>
    <p>
        全部都完工了！运行app。你无法自己”观察到“任何的变化，但现在app已经成功地避免了由RxJava所造成的内存泄漏。:]
    </p>
    <h2>
        从这儿去向哪里？
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
        你可以在
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/cheesefinder-final.zip"
        sl-processed="1">
            这里
        </a>
        下载最终的项目。
    </p>
    <p>
        你已在本教程中学到了很多的内容。但这只是RxJava世界的冰山一角。例如，
        <a href="https://github.com/JakeWharton/RxBinding" sl-processed="1">
            RxBinding
        </a>
        是一个包含了大部分Android View API的库。使用这个库，只需调用
        <code>
            RxView.clicks(viewVariable)
        </code>
        你就可以创建一个点击事件的observable。
    </p>
    <p>
        想了解更多关于RxJava的内容，请参考
        <a href="http://reactivex.io/" target="_blank" sl-processed="1">
            ReactiveX documentation
        </a>
        。
    </p>
    <h3>
        RxJava 2的新特性
    </h3>
    <p>
        RxJava的第二个版本和第一个相当得不同，它是完全地被重写过的。你需要熟悉一些类似
        <code>
            Flowable
        </code>
        和
        <code>
            Maybe
        </code>
        这样全新的类。
    </p>
    <p>
        通过
        <code>
            Flowable
        </code>
        ，你可以避免一些像
        <code>
            MissingBackpressureException
        </code>
        或
        <code>
            OutOfMemoryError
        </code>
        这样著名的问题。你可以用它来处理超过10k+的元素流。
    </p>
    <p>
        <code>
            Maybe
        </code>
        则是
        <code>
            Single
        </code>
        和
        <code>
            Completable
        </code>
        的结合体。
        <code>
            Single
        </code>
        最多只能接受一个item，否则便会失败；而
        <code>
            Completable
        </code>
        ，则可以在没有接收到任何item，或是失败的情况下直接完成。
    </p>
    <p>
        找点时间去浏览一下RxJava2的
        <a href="https://github.com/ReactiveX/RxJava/wiki/What%27s-different-in-2.0"
        target="_blank" sl-processed="1">
            更新日志
        </a>
        吧 :]
    </p>
</div>