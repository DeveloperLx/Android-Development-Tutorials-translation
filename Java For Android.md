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
        Java最吸引人的一点，就是“一次编写，处处运行”。这门语言的最大卖点就是降低了将软件从一个平台迁移到另一个平台的巨大代价。
    </p>
    <p>
        这个软件工程的真正奇迹，在于Java程序编译过程中可以发生的无限可能。
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
        现在你就懂了，为何大多数的Java程序，会在你还没有的情况下，提示你下载Java Runtime Environment（JRE）- 它是大多数平台默认的VM程序。
    </p>
    <h2>
        Android中的Java...有一点不同
    </h2>
    <p>
        编译android的app也是相同的过程，将Java文件转换为Bytecode。与此有所不同的是，在安装的过程中会发生第二个步骤。app的Bytecode会被优化为适合Android设备的机器码，这样就提示了app运行时的性能。这个过程被称作
        <em>
            Ahead of Time compilation
        </em>
        （AoT），它是由
        <em>
            Android Runtime
        </em>
        （ART）虚拟机实现的。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：
            <em>
                Ahead of Time Compilation
            </em>
            （AoT）是在很多的编程语言中通用的概念。你可以在
            <a title="on Wikipedia" href="https://en.wikipedia.org/wiki/Ahead-of-time_compilation"
            target="_blank" sl-processed="1">
                维基百科
            </a>
            上阅读更多有关它的内容。
        </p>
    </div>
    <p>
        <em>
            AoT
        </em>
        的编译机制只有在Android KitKat（4.4）以上的版本中才可以生效，但它也提供了向后的兼容。之前的Android版本依赖于另一个被称作
        <em>
            Dalvik
        </em>
        的虚拟机机制。像ART一样，Dalvik改变了Java的Bytecode，并将它转为为特定的形式，以进行各种效率上的优化，以适应一开始的那些低性能的Android设备。
    </p>
    <p>
        然而，和ART不同，Dalvik在运行之前并不能将Bytecode转化为机器码 - 它会使用一种叫做
        <em>
            Just in Time
        </em>
        （JIT）的编译方法。这个过程会更接近于Java在PC机上的虚拟环境。
    </p>
    <p>
        Android Froyo（2.2）进行了一个改进，Dalvik获取了 在运行时为Dalvik Bytecode中的常用部分“profile”app的能力。这些指令会通过Dalvik将代码永久地翻译为机器码，以提升启动app的速度。
    </p>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：基于JIT追踪的机制并不仅仅在于Java之中，同上，你可以在
            <a title="Wikipedia" href="https://en.wikipedia.org/wiki/Tracing_just-in-time_compilation"
            target="_blank" sl-processed="1">
                Wikipedia
                维基百科
            </a>
            中获取关于这点的很好的解释。
        </p>
    </div>
    <p>
        任何一种Android app的编译模式都是Bytecode的转换，它会使得为Android撰写Java变得不怎么“pure”。
    </p>
    <p>
        上述对于Bytecode的改变会束缚app的可移植性，因而销蚀了Java语言：“一次编写，处处运行”的特性。
    </p>
    <p>
        Android相应于Java的另一个差别，是标准库的可用性。Java如此得方便，是因为它依赖于一套标准库的集合，它能够在多个平台下生效，例如网络和UI的标准库。
    </p>
    <p>
        Android提供的是Java中的一个子集，它提供的这些是
        <i>
            仅仅
        </i>
        为了Android所用的。
    </p>
    <p>
        &nbsp;
    </p>
    <h2>
        漫步于Android中的Java
    </h2>
    <p>
        Android针对于Java的
        <em>
            面向对象特性
        </em>
        进行了扩展，旨在解决有关
        <em>
            封装
        </em>
        ，
        <em>
            继承
        </em>
        和
        <em>
            多态
        </em>
        的相关概念。你会使用所有的这些特性来构建你的app。
    </p>
    <p>
        所有在Android中的对象，都以某种方式继承了
        <code>
            Object
        </code>
        类，以基于此提供一些特定的功能和特性。你可以在
        <a title="Android API" href="http://developer.android.com/reference/android/package-summary.html"
        target="_blank" sl-processed="1">
            Android API
        </a>
        中找到一些可用的对象；你会发现它们最终都继承自
        <code>
            Object
        </code>
        。
    </p>
    <h3>
        并非那么超常的Activity
    </h3>
    <p>
        <code>
            Activity
        </code>
        类用来表示app的一个特定的屏幕。可以认为它处理和展示了所有在屏幕上的发生的工作。
    </p>
    <p>
        由于你的app至少也会有一到两个功能，这必须得跨越若干个屏幕实现，再能不让你的界面变得混乱。要创建一个“屏幕”，你需要
        <em>
            创建一个新的Java类
        </em>
        并让它继承自
        <code>
            Activity
        </code>
        ，就像这样：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainMenuActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Activity</span> </span>{

}
</pre>
    <p>
        就像这样，你为了特定的目的在你的app中划定了一个区域。
        <code>
            Activity
        </code>
        现在还不知道它该做什么，因为你还没有告诉它该做什么或如何出现。
    </p>
    <p>
        你现在就可以创建activity的界面了，也就是
        <em>
            Layout
        </em>
        ，可以在下面的两种方式中进行选择：
    </p>
    <ul>
        <li>
            在一个XML文件中进行声明
        </li>
        <li>
            用一个Java类以编程的方式来创建
        </li>
    </ul>
    <p>
        用一个XML文件来创建UI是更常用的方式。如果你需要对部分的布局进行定做，也可以使用编程的方式。
    </p>
    <p>
        这篇文章不会带你走遍创建布局的过程，但如果你想要为Android编写app的话，理解如何去创建是非常有帮助的，因为这是一个常规的工作。了解更多关于布局的内容，可以参考
        <a title="Android's documentation" href="http://developer.android.com/guide/topics/ui/declaring-layout.html"
        target="_blank" sl-processed="1">
            Android的官方文档
        </a>
        。
    </p>
    <p>
        下列的代码片段演示了，如何将一个activity指定为
        <em>
            res/layout/activity_main_menu.xml
        </em>
        这个XML布局文件中所表示的外观。
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainMenuActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Activity</span> </span>{
  <span class="hljs-comment">// 1</span>
  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState); <span class="hljs-comment">// 2</span>
    setContentView(R.layout.activity_main_menu); 
    <span class="hljs-comment">// 3</span>
  }
}
</pre>
    <p>
        一步一步来看一下：
    </p>
    <ol>
        <li>
            首先，你重写
            <code>
                onCreate()
            </code>
            了方法，它是你在
            <code>
                Activity
            </code>
            中可用的方法之一。它会在你的
            <code>
                Activity
            </code>
            被创建时调用，并给你充足的时间来设置你所需的内容。通常它都是你创建一个
            <code>
                Activity
            </code>
            时首先用到的方法。
        </li>
        <li>
            接着你会调用父类的
            <code>
                onCreate()
            </code>
            的实现，以确保
            <code>
                Activity
            </code>
            本身所要求的设置已完成。这是一个必须的步骤，如果你不这么做的话，app就会crash并抛出一个异常警告。
        </li>
        <li>
            最后，调用
            <code>
                setContentView()
            </code>
            方法来让你的
            <code>
                Activity
            </code>
            展示内容到屏幕上，它需要传递一个引用自
            <code>
                R
            </code>
            的布局参数。
        </li>
    </ol>
    <div class="note">
        <p>
            <em>
                注意
            </em>
            ：
            <code>
                R
            </code>
            是Android自动为你的app各种资源生成的一个特殊的类。它可以是你上面所看到一个屏幕的布局，也可以是本地化的字符串，图片，或是动画。Android会在构建的时候生成这个
            <code>
                R
            </code>
            类，因此你完全都不可以修改它。关于这里的更多详情可以访问
            <a title="developer.android.com" href="http://developer.android.com/guide/topics/resources/accessing-resources.html"
            target="_blank" sl-processed="1">
                developer.android.com
            </a>
            。
        </p>
    </div>
    <p>
        这个XML几乎包含了所有构成UI的元素。你在
        <code>
            Activity
        </code>
        中就通过这个
        <code>
            R
        </code>
        来访问这些元素，就像这样：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainMenuActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Activity</span> </span>{

  TextView mTextView;
  Button mButton;

  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);

    setContentView(R.layout.activity_main_menu); 

    mTextView = (TextView) findViewById(R.id.textview_main_menu);
    mButton = (Button) findViewById(R.id.button_main_menu);
  }
}
</pre>
    <p>
        <code>
            <span style="font-family: Georgia, 'Times New Roman', 'Bitstream Charter', Times, serif;">
                这其中的关键就是
            </span>
            findViewById()
        </code>
        ，它会通过指定的ID来搜索XML布局中相应的对象，以便你在Java代码中对他们进行操作。注意，你必须在每次调用时将返回的对象强转为恰当的
        <code>
            View
        </code>
        的子类，因为
        <code>
            findViewById()
        </code>
        只会返回
        <code>
            View
        </code>
        类型的对象-它是所有UI组件共有的基类。
    </p>
    <p>
        当你可以在Java的代码中访问到每个视图元素后，你就可以和它们进行交互，并让它按照你的需要来执行操作。下面的代码演示了如何添加一个当用户点击按钮时去执行的操作：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainMenuActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Activity</span> </span>{

  TextView mTextView;
  Button mButton;

  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
    <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main_menu); 
    mTextView = (TextView) findViewById(R.id.textview_main_menu);
    mButton = (Button) findViewById(R.id.button_main_menu);
    mButton.setOnClickListener(<span class="hljs-keyword">new</span> View.OnClickListener() {
      <span class="hljs-meta">@Override</span>
      <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onClick</span><span class="hljs-params">(View v)</span> </span>{
        mTextView.setText(<span class="hljs-string">"Hello World"</span>);
      }
    });
  }
}
</pre>
    <p>
        上述代码实现了当你每次点击按钮的时候，都会执行
        <code>
            onClick()
        </code>
        方法。在
        <code>
            onClick()
        </code>
        中，你将
        <code>
            TextView
        </code>
        中的文本设置成了“Hello World”。
    </p>
    <p>
        通过简单的方法把view连接到你的类中，并提供动作以在确定的事件发生时去执行，记住这些基本的步骤，你就可以逐步地把Java和Android应用起来。
    </p>
    <h2>
        开始建模
    </h2>
    <p>
        模型是编写Android app的关键。不要困惑于如同时装秀般繁杂的model的种类，Java允许你创建由数据结构和功能组成的对象。你可以使用它们发挥出巨大的作用。
    </p>
    <p>
        模型存在于你的UI类之外的类中。这种分离式的结构不止有助于你的app保持组织性，还遵循了面向对象的编程思想。
    </p>
    <p>
        一个典型的模型看起来就像下面这样：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">ReminderList</span> </span>{
    
  <span class="hljs-keyword">private</span> ArrayList mReminderArrayList;

  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-title">ReminderList</span><span class="hljs-params">()</span> </span>{
    mReminderArrayList = <span class="hljs-keyword">new</span> ArrayList&lt;&gt;();
  }

  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">setReminderArrayList</span><span class="hljs-params">(ArrayList reminderArrayList)</span> </span>{
    <span class="hljs-keyword">this</span>.mReminderArrayList = reminderArrayList;
  }
    
  <span class="hljs-function"><span class="hljs-keyword">public</span> ArrayList <span class="hljs-title">getReminderArrayList</span><span class="hljs-params">()</span> </span>{
    <span class="hljs-keyword">return</span> mReminderArrayList;
  }
    
  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">removeLastItemFromList</span><span class="hljs-params">()</span> </span>{
    <span class="hljs-keyword">if</span> (!mReminderArrayList.isEmpty()) {
        mReminderArrayList.remove(mReminderArrayList.size() - <span class="hljs-number">1</span>);
    }
  }
}
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
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">private</span> ArrayList mReminderArrayList;

<span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">setReminderArrayList</span><span class="hljs-params">(ArrayList reminderArrayList)</span> </span>{
  <span class="hljs-keyword">this</span>.mReminderArrayList = reminderArrayList;
}
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
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EmbeddedFragment</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Fragment</span> </span>{
  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">public</span> View <span class="hljs-title">onCreateView</span><span class="hljs-params">(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)</span> </span>{
    <span class="hljs-comment">// Inflate the layout for this fragment</span>
    <span class="hljs-keyword">return</span> inflater.inflate(R.layout.fragment_embedded, container, <span class="hljs-keyword">false</span>);
  }
}
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
    <pre lang="java" class="language-java hljs"><span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">updateFragment</span><span class="hljs-params">()</span> </span>{
  EmbeddedFragment fragment = (EmbeddedFragment) getFragmentManager().findFragmentById(R.id.fragment_embedded);
  fragment.setTextViewText(<span class="hljs-string">"Hello Little Fragment"</span>);
}
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
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">EmbeddedFragment</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Fragment</span> </span>{
  <span class="hljs-comment">// 1</span>
  OnItemInListSelectedListener mCallback;

  <span class="hljs-comment">// 2</span>
  <span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">interface</span> <span class="hljs-title">OnItemInListSelectedListener</span> </span>{
    <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onItemInListSelected</span><span class="hljs-params">(<span class="hljs-keyword">int</span> position)</span></span>;
  }

  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onAttach</span><span class="hljs-params">(Activity activity)</span> </span>{
    <span class="hljs-keyword">super</span>.onAttach(activity);
    <span class="hljs-comment">// 3      </span>
    <span class="hljs-keyword">try</span> {
      mCallback = (OnItemInListSelectedListener) activity;
    } 
    <span class="hljs-keyword">catch</span> (ClassCastException e) {
      <span class="hljs-keyword">throw</span> <span class="hljs-keyword">new</span> ClassCastException(activity.toString()  + <span class="hljs-string">" must implement OnItemInListSelectedListener"</span>);
    }
  }

  <span class="hljs-meta">@Override</span>
  <span class="hljs-function"><span class="hljs-keyword">public</span> View <span class="hljs-title">onCreateView</span><span class="hljs-params">(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState)</span> </span>{
    <span class="hljs-keyword">return</span> inflater.inflate(R.layout.fragment_embedded, container, <span class="hljs-keyword">false</span>);
  }
}
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
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainMenuActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Activity</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">EmbeddedFragment</span>.<span class="hljs-title">OnItemInListSelectedListener</span> </span>{

  ...

  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onItemInListSelected</span><span class="hljs-params">(<span class="hljs-keyword">int</span> position)</span> </span>{
      <span class="hljs-comment">// Received a message from the Fragment, you'll do something neat here</span>
  }
}
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
    <pre lang="java" class="language-java hljs"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onItemInListSelected</span><span class="hljs-params">(<span class="hljs-keyword">int</span> position)</span> </span>{
  ListDetailFragment listDetailFragment = (ListDetailFragment) getFragmentManager.findFragmentById(R.id.fragment_list_detail);
  listDetailFragment.showListItemDetails(position);   
}
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
    <pre lang="java" class="language-java hljs"><span class="hljs-meta">@Override</span>
<span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
  <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
}
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