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
            本教程的起始项目
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
        You’ve imported the correct
        <code>
            Observable
        </code>
        class and you’re using the
        <em>
            Kotlin Android Extensions
        </em>
        to get references to view objects.
    </p>
    <p>
        Here’s what’s going on in the code above:
    </p>
    <ol>
        <li>
            You declare a function that returns an observable that will emit strings.
        </li>
        <li>
            You create an observable with
            <code>
                Observable.create()
            </code>
            , and supply it with a new
            <code>
                ObservableOnSubscribe
            </code>
            .
        </li>
        <li>
            Set up an
            <code>
                OnClickListener
            </code>
            on
            <code>
                searchButton
            </code>
            .
        </li>
        <li>
            When the click event happens, call
            <code>
                onNext
            </code>
            on the emitter and pass it the current text value of
            <code>
                queryEditText
            </code>
            .
        </li>
        <li>
            Keeping references can cause memory leaks in Java or Kotlin. It’s a useful
            habit to remove listeners as soon as they are no longer needed. But what
            do you call when you are creating your own
            <code>
                Observable
            </code>
            ? For that very reason,
            <code>
                ObservableEmitter
            </code>
            has
            <code>
                setCancellable()
            </code>
            . Override
            <code>
                cancel()
            </code>
            , and your implementation will be called when the Observable is disposed,
            such as when the Observable is completed or all Observers have unsubscribed
            from it.
        </li>
        <li>
            For
            <code>
                OnClickListener
            </code>
            , the code that removes the listener is
            <code>
                setOnClickListener(null)
            </code>
            .
        </li>
    </ol>
    <p>
        Now that you’ve defined your Observable, you need to set up the subscription
        to it. Before you do, you need to learn about one more interface,
        <code>
            Consumer
        </code>
        . It’s a simple way to accept values coming in from an emitter.
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">Consumer</span>&lt;<span class="hljs-title">T</span>&gt; </span>{
  <span class="hljs-function"><span class="hljs-keyword">void</span> <span class="hljs-title">accept</span><span class="hljs-params">(T t)</span> <span class="hljs-keyword">throws</span> Exception</span>;
}
</pre>
    <p>
        This interface is handy when you want to set up a simple subscription
        to an Observable.
    </p>
    <p>
        The
        <code>
            Observable
        </code>
        interface requires several versions of
        <code>
            subscribe()
        </code>
        , all with different parameters. For example, you could pass a full
        <code>
            Observer
        </code>
        if you like, but then you’d need to implement all the necessary methods.
    </p>
    <p>
        If all you need out of your subscription is for the observer to respond
        to values sent to
        <code>
            onNext()
        </code>
        , you can use the version of
        <code>
            subscribe()
        </code>
        that takes in a single
        <code>
            Consumer
        </code>
        (the parameter is even named
        <code>
            onNext
        </code>
        , to make the connection clear).
    </p>
    <p>
        You’ll do exactly that when you subscribe in your activity’s
        <code>
            onStart()
        </code>
        . Add the following code to
        <em>
            CheeseActivity.kt
        </em>
        :
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
        Here’s an explanation of each step:
    </p>
    <ol>
        <li>
            First, create an observable by calling the method you just wrote.
        </li>
        <li>
            Subscribe to the observable with
            <code>
                subscribe()
            </code>
            , and supply a simple
            <code>
                Consumer
            </code>
            .
        </li>
        <li>
            Finally, perform the search and show the results.
        </li>
    </ol>
    <p>
        Build and run the app. Enter some letters and press the
        <em>
            Search
        </em>
        button. After a simulated delay (see
        <em>
            CheeseSearchEngine
        </em>
        ), you should see a list of cheeses that match your request:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500.png"
        alt="enter-and-press-300x500" width="300" height="533" class="aligncenter size-full wp-image-143326"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/enter-and-press-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <p>
        Sounds yummy! :]
    </p>
    <h2>
        RxJava Threading Model
    </h2>
    <p>
        You’ve had your first taste of reactive programming. There is one problem
        though: the UI freezes up for a few seconds when the search button is pressed.
    </p>
    <p>
        You might also notice the following line in Android Monitor:
    </p>
    <pre lang="text" class="language-text">
        &gt; 08-24 14:36:34.554 3500-3500/com.raywenderlich.cheesefinder I/Choreographer:
        Skipped 119 frames! The application may be doing too much work on its main
        thread.
    </pre>
    <p>
        This happens because
        <code>
            search
        </code>
        is executed on the main thread. If
        <code>
            search
        </code>
        were to perform a network request, Android will crash the app with a
        <code>
            NetworkOnMainThreadException
        </code>
        exception. It’s time to fix that.
    </p>
    <p>
        One popular myth about RxJava is that it is multi-threaded by default,
        similar to
        <code>
            AsyncTask
        </code>
        . However, if not otherwise specified, RxJava does all the work in the
        same thread it was called from.
    </p>
    <p>
        You can change this behavior with the
        <code>
            subscribeOn
        </code>
        and
        <code>
            observeOn
        </code>
        operators.
    </p>
    <p>
        <code>
            subscribeOn
        </code>
        is supposed to be called only once in the chain of operators. If it’s
        not, the first call wins.
        <code>
            subscribeOn
        </code>
        specifies the thread on which the observable will be subscribed (i.e.
        created). If you use observables that emit events from an Android View,
        you need to make sure subscription is done on the Android UI thread.
    </p>
    <p>
        On the other hand, it’s okay to call
        <code>
            observeOn
        </code>
        as many times as you want in the chain.
        <code>
            observeOn
        </code>
        specifies the thread on which the next operators in the chain will be
        executed. For example:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        myObservable
        <span class="hljs-comment">
            // observable will be subscribed on i/o thread
        </span>
        .subscribeOn(Schedulers.io()) .observeOn(AndroidSchedulers.mainThread())
        .map {
        <span class="hljs-comment">
            /* this will be called on main thread... */
        </span>
        } .doOnNext{
        <span class="hljs-comment">
            /* ...and everything below until next observeOn */
        </span>
        } .observeOn(Schedulers.io()) .subscribe {
        <span class="hljs-comment">
            /* this will be called on i/o thread */
        </span>
        }
    </pre>
    <p>
        The most useful schedulers are:
    </p>
    <ul>
        <li>
            <code>
                Schedulers.io()
            </code>
            : Suitable for I/O-bound work such as network requests or disk operations.
        </li>
        <li>
            <code>
                Schedulers.computation()
            </code>
            : Works best with computational tasks like event-loops and processing
            callbacks.
        </li>
        <li>
            <code>
                AndroidSchedulers.mainThread()
            </code>
            executes the next operators on the UI thread.
        </li>
    </ul>
    <h2>
        The Map Operator
    </h2>
    <p>
        The
        <code>
            map
        </code>
        operator applies a function to each item emitted by an observable and
        returns another observable that emits results of those function calls.
        You’ll need this to fix the threading issue as well.
    </p>
    <p>
        If you have an observable called
        <code>
            numbers
        </code>
        that emits the following:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/map-0-1.png"
        alt="map-0" width="500" height="214" class="aligncenter size-full wp-image-142688"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/map-0-1.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/08/map-0-1-480x205.png 480w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        And if you apply
        <code>
            map
        </code>
        as follows:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        numbers.map { number -&gt; number * number }
    </pre>
    <p>
        The result would be the following:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/map-1-1.png"
        alt="map-1" width="500" height="214" class="aligncenter size-full wp-image-142689"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/map-1-1.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/08/map-1-1-480x205.png 480w"
        sizes="(max-width: 500px) 100vw, 500px">
    </p>
    <p>
        That’s a handy way to iterate over multiple items with little code. Let’s
        put it to use!
    </p>
    <p>
        Modify
        <code>
            onStart()
        </code>
        in
        <code>
            CheeseActivity
        </code>
        class to look like the following:
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
                onStart
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onStart()
        <span class="hljs-keyword">
            val
        </span>
        searchTextObservable = createButtonClickObservable() searchTextObservable
        <span class="hljs-comment">
            // 1
        </span>
        .subscribeOn(AndroidSchedulers.mainThread())
        <span class="hljs-comment">
            // 2
        </span>
        .observeOn(Schedulers.io())
        <span class="hljs-comment">
            // 3
        </span>
        .map { cheeseSearchEngine.search(it) }
        <span class="hljs-comment">
            // 4
        </span>
        .observeOn(AndroidSchedulers.mainThread()) .subscribe { showResult(it)
        } }
    </pre>
    <p>
        Going over the code above:
    </p>
    <ol>
        <li>
            First, specify that code down the chain should start on the main thread
            instead of on the I/O thread. In Android, all code that works with
            <code>
                View
            </code>
            s should execute on the main thread.
        </li>
        <li>
            Specify that the next operator should be called on the I/O thread.
        </li>
        <li>
            For each search query, you return a list of results.
        </li>
        <li>
            Finally, make sure that the results are passed to the list on the main
            thread
        </li>
    </ol>
    <p>
        Build and run your project. Now the UI should be responsive even when
        a search is in progress.
    </p>
    <h2>
        Show Progress Bar with doOnNext
    </h2>
    <p>
        It’s time to display the progress bar!
    </p>
    <p>
        For that you’ll need a
        <code>
            doOnNext
        </code>
        operator.
        <code>
            doOnNext
        </code>
        takes a
        <code>
            Consumer
        </code>
        and allows you do something each time an item is emitted by observable.
    </p>
    <p>
        In the same
        <code>
            CheeseActivity
        </code>
        class modify
        <code>
            onStart()
        </code>
        to the following:
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
                onStart
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onStart()
        <span class="hljs-keyword">
            val
        </span>
        searchTextObservable = createButtonClickObservable() searchTextObservable
        <span class="hljs-comment">
            // 1
        </span>
        .observeOn(AndroidSchedulers.mainThread())
        <span class="hljs-comment">
            // 2
        </span>
        .doOnNext { showProgress() } .observeOn(Schedulers.io()) .map { cheeseSearchEngine.search(it)
        } .observeOn(AndroidSchedulers.mainThread()) .subscribe {
        <span class="hljs-comment">
            // 3
        </span>
        hideProgress() showResult(it) } }
    </pre>
    <p>
        Taking each numbered comment in turn:
    </p>
    <ol>
        <li>
            Ensure that the next operator in chain will be run on the main thread.
        </li>
        <li>
            Add the
            <code>
                doOnNext
            </code>
            operator so that
            <code>
                showProgress()
            </code>
            will be called every time a new item is emitted.
        </li>
        <li>
            Don’t forget to call
            <code>
                hideProgress()
            </code>
            when you are just about to display a result.
        </li>
    </ol>
    <p>
        Build and run your project. You should see the progress bar appearing
        when you initiate the search:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500.png"
        alt="progressbar" width="300" height="533" class="aligncenter size-full wp-image-143328"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/progressbar-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <h2>
        Observe Text Changes
    </h2>
    <p>
        What if you want to perform search automatically when the user types some
        text, just like Google?
    </p>
    <p>
        First, you need to subscribe to
        <code>
            TextView
        </code>
        text changes. Add the following function to the
        <code>
            CheeseActivity
        </code>
        class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-comment">
            // 1
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                createTextChangeObservable
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        : Observable&lt;String&gt; {
        <span class="hljs-comment">
            // 2
        </span>
        <span class="hljs-keyword">
            val
        </span>
        textChangeObservable = Observable.create&lt;String&gt; { emitter -&gt;
        <span class="hljs-comment">
            // 3
        </span>
        <span class="hljs-keyword">
            val
        </span>
        textWatcher =
        <span class="hljs-keyword">
            object
        </span>
        : TextWatcher {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                afterTextChanged
            </span>
            <span class="hljs-params">
                (s:
                <span class="hljs-type">
                    Editable
                </span>
                ?)
            </span>
        </span>
        =
        <span class="hljs-built_in">
            Unit
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                beforeTextChanged
            </span>
            <span class="hljs-params">
                (s:
                <span class="hljs-type">
                    CharSequence
                </span>
                ?, start:
                <span class="hljs-type">
                    Int
                </span>
                , count:
                <span class="hljs-type">
                    Int
                </span>
                , after:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        =
        <span class="hljs-built_in">
            Unit
        </span>
        <span class="hljs-comment">
            // 4
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onTextChanged
            </span>
            <span class="hljs-params">
                (s:
                <span class="hljs-type">
                    CharSequence
                </span>
                ?, start:
                <span class="hljs-type">
                    Int
                </span>
                , count:
                <span class="hljs-type">
                    Int
                </span>
                , after:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        { s?.toString()?.let { emitter.onNext(it) } } }
        <span class="hljs-comment">
            // 5
        </span>
        queryEditText.addTextChangedListener(textWatcher)
        <span class="hljs-comment">
            // 6
        </span>
        emitter.setCancellable { queryEditText.removeTextChangedListener(textWatcher)
        } }
        <span class="hljs-comment">
            // 7
        </span>
        <span class="hljs-keyword">
            return
        </span>
        textChangeObservable }
    </pre>
    <p>
        Here’s the play-by-play of each step above:
    </p>
    <ol>
        <li>
            Declare a function that will return an observable for text changes.
        </li>
        <li>
            Create
            <code>
                textChangeObservable
            </code>
            with
            <code>
                create()
            </code>
            , which takes an
            <code>
                ObservableOnSubscribe
            </code>
            .
        </li>
        <li>
            When an observer makes a subscription, the first thing to do is to create
            a
            <code>
                TextWatcher
            </code>
            .
        </li>
        <li>
            You aren’t interested in
            <code>
                beforeTextChanged()
            </code>
            and
            <code>
                afterTextChanged()
            </code>
            . When the user types and
            <code>
                onTextChanged()
            </code>
            triggers, you pass the new text value to an observer.
        </li>
        <li>
            Add the watcher to your
            <code>
                TextView
            </code>
            by calling
            <code>
                addTextChangedListener()
            </code>
            .
        </li>
        <li>
            Don’t forget to remove your watcher. To do this, call
            <code>
                emitter.setCancellable()
            </code>
            and overwrite
            <code>
                cancel()
            </code>
            to call
            <code>
                removeTextChangedListener()
            </code>
        </li>
        <li>
            Finally, return the created observable.
        </li>
    </ol>
    <p>
        To see this observable in action, replace the declaration of
        <code>
            searchTextObservable
        </code>
        in
        <code>
            onStart()
        </code>
        of
        <code>
            CheeseActivity
        </code>
        as follows:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        searchTextObservable = createTextChangeObservable()
    </pre>
    <p>
        Build and run your app. You should see the search kick off when you start
        typing text in the
        <code>
            TextView
        </code>
        :
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500.png"
        alt="text-view-changes-simple" width="300" height="533" class="aligncenter size-full wp-image-143329"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/09/text-view-changes-simple-300x500-281x500.png 281w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <h2>
        Filter Queries by Length
    </h2>
    <p>
        It doesn’t make sense to search for queries as short as a single letter.
        To fix this, let’s introduce the powerful
        <code>
            filter
        </code>
        operator.
    </p>
    <p>
        <code>
            filter
        </code>
        passes only those items which satisfy a particular condition.
        <code>
            filter
        </code>
        takes in a
        <code>
            Predicate
        </code>
        , which is an interface that defines the test that input of a given type
        needs to pass, with a
        <code>
            boolean
        </code>
        result. In this case, the Predicate takes a
        <code>
            String
        </code>
        and returns
        <code>
            true
        </code>
        if the string’s length is two or more characters.
    </p>
    <p>
        Replace
        <code>
            return textChangeObservable
        </code>
        in
        <code>
            createTextChangeObservable()
        </code>
        with the following code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            return
        </span>
        textChangeObservable.filter { it.length &gt;=
        <span class="hljs-number">
            2
        </span>
        }
    </pre>
    <p>
        Everything will work exactly the same, except that text queries with
        <code>
            length
        </code>
        less than
        <code>
            2
        </code>
        won’t get sent down the chain.
    </p>
    <p>
        Run the app; you should see the search kick off only when you type the
        second character:
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
        Debounce operator
    </h2>
    <p>
        You don’t want to send a new request to the server every time the query
        is changed by one symbol.
    </p>
    <p>
        <code>
            debounce
        </code>
        is one of those operators that shows the real power of reactive paradigm.
        Much like the
        <code>
            filter
        </code>
        operator,
        <code>
            debounce
        </code>
        , filters items emitted by the observable. But the decision on whether
        the item should be filtered out is made not based on
        <i>
            what
        </i>
        the item is, but based on
        <i>
            when
        </i>
        the item was emitted.
    </p>
    <p>
        <code>
            debounce
        </code>
        waits for a specified amount of time after each item emission for another
        item. If no item happens to be emitted during this wait, the last item
        is finally emitted:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674-650x219.png"
        alt="719f0e58_1472502674" width="650" height="219" class="aligncenter size-large wp-image-142671"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674-650x219.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674-480x161.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/08/719f0e58_1472502674.png 812w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        In
        <code>
            createTextChangeObservable()
        </code>
        , add the
        <code>
            debounce
        </code>
        operator just below the
        <code>
            filter
        </code>
        so that the
        <code>
            return
        </code>
        statement will look like the following code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            return
        </span>
        textChangeObservable .filter { it.length &gt;=
        <span class="hljs-number">
            2
        </span>
        } .debounce(
        <span class="hljs-number">
            1000
        </span>
        , TimeUnit.MILLISECONDS)
        <span class="hljs-comment">
            // add this line
        </span>
    </pre>
    <p>
        Run the app. You’ll notice that the search begins only when you stop making
        quick changes:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/debounce-500px-1.gif"
        alt="debounce-500px" width="300" height="533" class="aligncenter size-full wp-image-143337">
    </p>
    <p>
        <code>
            debounce
        </code>
        waits for 1000 milliseconds before emitting the latest query text.
    </p>
    <h2>
        Merge Operator
    </h2>
    <p>
        You started by creating an observable that reacted to button clicks and
        then implemented an observable that reacts to text field changes. But how
        do you react to both?
    </p>
    <p>
        There are a lot of operators to combine observables. The most simple and
        useful one is
        <code>
            merge
        </code>
        .
    </p>
    <p>
        <code>
            merge
        </code>
        takes items from two or more observables and puts them into a single observable:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259-650x296.png"
        alt="ae08759b_1472502259" width="650" height="296" class="aligncenter size-large wp-image-142669"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259-650x296.png 650w, https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259-480x218.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/08/ae08759b_1472502259.png 809w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        Change the beginning of
        <code>
            onStart()
        </code>
        to the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        buttonClickStream = createButtonClickObservable()
        <span class="hljs-keyword">
            val
        </span>
        textChangeStream = createTextChangeObservable()
        <span class="hljs-keyword">
            val
        </span>
        searchTextObservable = Observable.merge&lt;String&gt;(buttonClickStream,
        textChangeStream)
    </pre>
    <p>
        Run your app. Play with the text field and the search button; the search
        will kick off either when you finish typing two or more symbols or when
        you simply press the Search button.
    </p>
    <h2>
        RxJava and Activity/Fragment lifecycle
    </h2>
    <p>
        Remember those
        <code>
            setCancellable
        </code>
        methods you set up? They won’t fire until the observable is unsubscribed.
    </p>
    <p>
        The
        <code>
            Observable.subscribe()
        </code>
        call returns a
        <code>
            Disposable
        </code>
        .
        <code>
            Disposable
        </code>
        is an interface that has two methods:
    </p>
    <pre lang="java" class="language-java hljs">
        <span class="hljs-keyword">
            public
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                interface
            </span>
            <span class="hljs-title">
                Disposable
            </span>
        </span>
        {
        <span class="hljs-function">
            <span class="hljs-keyword">
                void
            </span>
            <span class="hljs-title">
                dispose
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        ;
        <span class="hljs-comment">
            // ends a subscription
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                boolean
            </span>
            <span class="hljs-title">
                isDisposed
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        ;
        <span class="hljs-comment">
            // returns true if resource is disposed (unsubscribed)
        </span>
        }
    </pre>
    <p>
        Add the following property to
        <code>
            CheeseActivity
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            lateinit
        </span>
        <span class="hljs-keyword">
            var
        </span>
        disposable: Disposable
    </pre>
    <p>
        In
        <code>
            onStart()
        </code>
        , set the returned value of
        <code>
            subscribe()
        </code>
        to
        <code>
            disposable
        </code>
        with the following code (only the first line changes):
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        disposable = searchTextObservable
        <span class="hljs-comment">
            // change this line
        </span>
        .observeOn(AndroidSchedulers.mainThread()) .doOnNext { showProgress()
        } .observeOn(Schedulers.io()) .map { cheeseSearchEngine.search(it) } .observeOn(AndroidSchedulers.mainThread())
        .subscribe { hideProgress() showResult(it) }
    </pre>
    <p>
        Since you subscribed to the observable in
        <code>
            onStart()
        </code>
        ,
        <code>
            onStop()
        </code>
        would be a perfect place to unsubscribe.
    </p>
    <p>
        Add the following code to
        <em>
            CheeseActivity.kt
        </em>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-meta">
            @Override
        </span>
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
        <span class="hljs-keyword">
            if
        </span>
        (!disposable.isDisposed) { disposable.dispose() } }
    </pre>
    <p>
        And that’s it! Build and run the app. You won’t “observe” any changes
        yourself, but now the app is successfully avoiding RxJava memory leaks.
        :]
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
        You can download the final project from this tutorial
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/cheesefinder-final.zip"
        sl-processed="1">
            here
        </a>
        .
    </p>
    <p>
        You’ve learned a lot in this tutorial. But that’s only a glimpse of the
        RxJava world. For example, there is
        <a href="https://github.com/JakeWharton/RxBinding" sl-processed="1">
            RxBinding
        </a>
        , a library that includes most of the Android View APIs. Using this library,
        you can create a click observable by just calling
        <code>
            RxView.clicks(viewVariable)
        </code>
        .
    </p>
    <p>
        To learn more about RxJava refer to the
        <a href="http://reactivex.io/" target="_blank" sl-processed="1">
            ReactiveX documentation
        </a>
        .
    </p>
    <h3>
        What’s new in RxJava 2
    </h3>
    <p>
        The second version of RxJava is quite different from the first one, since
        RxJava 2 was completely rewritten. You should get acquainted with some
        entirely new classes like
        <code>
            Flowable
        </code>
        and
        <code>
            Maybe
        </code>
        .
    </p>
    <p>
        With
        <code>
            Flowable
        </code>
        , you can now avoid getting such well-known problems as
        <code>
            MissingBackpressureException
        </code>
        or
        <code>
            OutOfMemoryError
        </code>
        . You can use it to handle a flow of 10k+ elements.
    </p>
    <p>
        <code>
            Maybe
        </code>
        is a combination of
        <code>
            Single
        </code>
        and
        <code>
            Completable
        </code>
        . Like
        <code>
            Single
        </code>
        , it can receive at most one item or fail, and like
        <code>
            Completable
        </code>
        it can finish successfully without any received items or fail.
    </p>
    <p>
        Find some time to skim all the
        <a href="https://github.com/ReactiveX/RxJava/wiki/What%27s-different-in-2.0"
        target="_blank" sl-processed="1">
            changelog
        </a>
        of RxJava2 :]
    </p>
</div>