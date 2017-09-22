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
        这其中没有提到一个view或activity！只有数据的结构，原始的数据类型以及各种功能。事实上它就是一个平常的Java对象（POJO） - 完全没有什么神秘。这个模型被完美地封装，意味着你就可以把它放入到任何的Android app，并直接去使用它。
    </p>
    <p>
        在其它基于面向对象的语言中，通常都会基于对象的上下文，来定义全局的实例变量以创建对象。在Android中，通常也会以
        <em>
            m
        </em>
        前缀标记这种实例变量，这样就可以轻松地看出哪些是非公开，非静态的实例变量，哪些不是。开始你会感到有一点奇怪，但这是一种很好的编码习惯，尤其因为Android的源码中
        <a title="specifies this convention" href="http://source.android.com/source/code-style.html#follow-field-naming-conventions"
        target="_blank" sl-processed="1">
            指定了这个惯例
        </a>
        ，你需要这样做以直接为Android的源码做贡献。
    </p>
    <p>
        成员变量的
        <em>
            Getters
        </em>
        和
        <em>
            setters
        </em>
        也是Android开发的主要内容。这些短小的方法组成了你app的剩余部分，以在你需要的时候改变成员变量；当然你也可以在获取和设置成员变量时，执行一些额外的操作。
    </p>
    <h2>
        访问修饰符
    </h2>
    <p>
        帮助setter和getter工作的最后一个难题就是访问修饰符了。看一下上述模型中的下述代码片段：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">private</span> ArrayList mReminderArrayList;

<span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">setReminderArrayList</span><span class="hljs-params">(ArrayList reminderArrayList)</span> </span>{
  <span class="hljs-keyword">this</span>.mReminderArrayList = reminderArrayList;
}
</pre>
    <p>
        注意到
        <em>
            private
        </em>
        和
        <em>
            public
        </em>
        这些关键字了么？它们就是
        <em>
            访问修饰符
        </em>
        ，负责指定你的模型中的哪些元素是可以被其它的类访问的，以协助封装你的对象。
    </p>
    <ul>
        <li>
            <em>
                Public
            </em>
            - 允许被其它所有的对象访问。被标记为public的方法和变量构成了这个类的API。
        </li>
        <li>
            <em>
                Private
            </em>
            - 只允许被自己访问。甚至连它的子类都不可以访问。
        </li>
        <li>
            <em>
                Protected
            </em>
            - 可以被自己和自己的子类访问。其它的对象则不可以访问。
        </li>
    </ul>
    <p>
        成员变量应当总是被设置成private或protected的。要在类的外部访问它们，必须通过public的getter和setter方法，就像在上面的代码片段中演示的一样。这样就避免了难以被追踪的副作用和高耦合的代码。
    </p>
    <p>
        如果你想要创建一个上述model的子类，并希望你的子类能够访问
        <code>
            mReminderArrayList
        </code>
        ，你就要把它的访问修饰符修改为
        <em>
            protected
        </em>
        。这样就能够在子类中访问这些变量了，以便你进行更进一步的定制和处理这些变量。
    </p>
    <h2>
        Fragments
    </h2>
    <p>
        在进入下一个话题之前，你需要对Android app如何构建它的UI进行更多的了解。Activity用于管理屏幕上的全部内容，但并不便于进行分享。幸运的是，有一种很棒的方式，可以将UI拆分为较小的称作
        <em>
            fragments
        </em>
        的组件。
    </p>
    <p>
        Fragment和activity非常得像，但可以被嵌入到activity中就好像它是view一样。它拥有类似于activity的生命周期方法
        <code>
            onCreate()
        </code>
        并可以像一个activity一样接受输入。
    </p>
    <p>
        一个fragment的布局文件几乎和activity的完全一样，它包含了若干view的声明。你甚至会使用相同的方法把它们接入到代码中，通过将view声明为一个变量，并通过你在布局文件中提供的标识符找到它们。
    </p>
    <p>
        下列的代码就创建了一个fragment的布局文件，位于
        <em>
            res/layout/fragment_embedded.xml
        </em>
        ：
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
        你首先继承了Fragment类的行为，然后使用了它其中一个的生命周期方法，也就是
        <code>
            onCreateView()
        </code>
        来设置fragment。然后你返回了一个布局以展示特定的fragment。
    </p>
    <p>
        当你的activity和fragment相互隔离时，上述的代码就已足够，但如果你需要在它们之间传递信息的时候呢？以下是一个简单的示例，在一个activity中的方法，尝试与fragment进行信息传递：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-function"><span class="hljs-keyword">private</span> <span class="hljs-keyword">void</span> <span class="hljs-title">updateFragment</span><span class="hljs-params">()</span> </span>{
  EmbeddedFragment fragment = (EmbeddedFragment) getFragmentManager().findFragmentById(R.id.fragment_embedded);
  fragment.setTextViewText(<span class="hljs-string">"Hello Little Fragment"</span>);
}
</pre>
    <p>
        由于fragment是存在于activity中的，因此你要通过
        <code>
            findFragmentById
        </code>
        以及定义在XML中的identifier来访问它。之后，你就可以调用fragment的公有方法了，就像上面例子中的  
        <code>
            setTextViewText()
        </code>
        一样。
    </p>
    <p>
        相应的，fragment可以通过调用
        <code>
            getActivity()
        </code>
        方法来访问所在的activity。上述的方案可以作用在很多简单的情况下，但在更复杂的场景中来讨论会更加的有趣。
    </p>
    <h2>
        Interfaces
    </h2>
    <p>
        如果你的activity有三个活跃的fragment，每个都负责各自的工作，但需要通知其它fragment，它们在特定的时刻执行了某个动作，该怎么办？
    </p>
    <p>
        理论上，fragment应当只关心它们自己的目标，不需要知道他们存在于其它fragment的旁边；activity某种意义上是一个策划者。它是唯一可以访问所有的fragment，并了解它们在做什么的对象。
    </p>
    <p>
        这就需要一个被叫做
        <em>
            Interfaces
        </em>
        的Java特性。
    </p>
    <p>
        一个interface看起来就像是一个类，但是没有实现的部分。它定义了公共的API。之后的类就可以实现这些interface，并且你的代码可以不再依赖具体类的实现，只需知道“这是一个我可以调用这些interface方法的未知的对象”。
    </p>
    <p>
        Interface让你可以在不暴露对象内部工作方式的情况下，间接地与其它对象之间交互。想象一些构建极其复杂，但使用却相当简单的东西：汽车，电视机，甚至是你此刻正在用于阅读本教程的设备。
    </p>
    <p>
        你可能并不知道这些东西内部是如何工作的，当你肯定知道如何去操作它们。Interface就起到了同样的作用。
    </p>
    <p>
        在Android中，interface对于处理fragment到activity，或fragment之间的信息传递是非常有用的。它工作时就如同下面的样子：
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
        详细地看一下：
    </p>
    <ol>
        <li>
            在fragment中，你声明了一个成员变量来储存定制的实现了
            <code>
                OnItemInListSelectedListener
            </code>
            interface的对象，这个成员变量被命名为
            <code>
                mCallback
            </code>
            。
        </li>
        <li>
            接下来，你创建了interface并声明要求的方法 - 你的interface可以有很多的方法。
        </li>
        <li>
            在
            <code>
                onAttach()
            </code>
            （一个fragment的生命周期方法）中，你首先检查了你的fragment是否遵循了
            <code>
                OnItemInListSelectedListener
            </code>
            。如果没有的话，它就不能服务于你的目标，并且你会遇到一个问题。
            <code>
                ClassCastException
            </code>
            ClassCastException就代表了这个运行时的错误。这样就可以把这个消息发送给你自己和其他的程序员，尽早地解决问题。
        </li>
    </ol>
    <p>
        下面要做的事是让你的activity使用interface：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-keyword">public</span> <span class="hljs-class"><span class="hljs-keyword">class</span> <span class="hljs-title">MainMenuActivity</span> <span class="hljs-keyword">extends</span> <span class="hljs-title">Activity</span> <span class="hljs-keyword">implements</span> <span class="hljs-title">EmbeddedFragment</span>.<span class="hljs-title">OnItemInListSelectedListener</span> </span>{

  ...

  <span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onItemInListSelected</span><span class="hljs-params">(<span class="hljs-keyword">int</span> position)</span> </span>{
      <span class="hljs-comment">// Received a message from the Fragment, you'll do something neat here</span>
  }
}
</pre>
    <p>
        在类定义中的关键字
        <code>
            implements
        </code>
        表明了这个类将会实现指定的interface。接下来你就需要为所有interface中声明的方法提供具体的实现。在这个自定义的interface中，现在只有一个方法，你可以看到在上述代码中有一个骨架的实现。
    </p>
    <p>
        这是一个困难的部分，但你现在仍然没有在fragment之间进行信息传递。假定你使用标识符
        <em>
            fragment_list_detail
        </em>
        和一个名为
        <em>
            showListItemDetails(int)
        </em>
        的方法，定义了第二个
        <em>
            ListDetailFragment
        </em>
        的fragment。为了让它们之间可以进行信息传递，你只需跟之前一样，使用fragment的一个public的方法来建立activity到fragment的信息传递：
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-function"><span class="hljs-keyword">public</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onItemInListSelected</span><span class="hljs-params">(<span class="hljs-keyword">int</span> position)</span> </span>{
  ListDetailFragment listDetailFragment = (ListDetailFragment) getFragmentManager.findFragmentById(R.id.fragment_list_detail);
  listDetailFragment.showListItemDetails(position);   
}
</pre>
    <p>
        就像这样，你构建了fragment到activity之间的信息交流。学习组件如何同fragment和activity进行协同工作，是保持你的app架构灵活性的关键部分。
    </p>
    <h2>
        Annotations
    </h2>
    <p>
        注意到本文代码中的一些方法上面，特殊代码标记了么？
    </p>
    <pre lang="java" class="language-java hljs"><span class="hljs-meta">@Override</span>
<span class="hljs-function"><span class="hljs-keyword">protected</span> <span class="hljs-keyword">void</span> <span class="hljs-title">onCreate</span><span class="hljs-params">(Bundle savedInstanceState)</span> </span>{
  <span class="hljs-keyword">super</span>.onCreate(savedInstanceState);
}
</pre>
    <p>
        这些带有
        <em>
            @
        </em>
        前缀的关键字就是
        <em>
            Annotation
        </em>
        。它们会在app的各个阶段提供额外的信息。Annotation会在运行时向编译器提供额外的信息，甚至生成额外的代码。
    </p>
    <p>
        在Android中最常用的annotation就是
        <em>
            @Override
        </em>
        了，它会告诉编译器，它指定给的这个方法应当覆盖父类中相应的方法。如果这个方法事实上并没有覆盖父类中的方法，就会导致编译器的失败并通知给你，这样就提供了一个非常棒的安全特性，以避免任何你可能遇到的奇怪状况。
    </p>
    <p>
        另一个有名的annotation就是
        <em>
            @TargetApi
        </em>
        。它表明你的方法只可以应用于特定或更新版本的Android上。如果你使用@TargetApi将一个方法标记为高于你当前app target的版本，编译器就会抱怨你正在使用的功能在你当前版本的Android上并不可用。
    </p>
    <p>
        这是一个抱怨，但同时也是一个很有礼貌的警告。你仍然可以运行你的app，但也已经可以准备遭遇随之而来的崩溃了。
    </p>
    <p>
        当你构建Android app的时候，你基本依靠这两个annotation就可以了。你还可以从Android的API文档中了解其它的annotation。你还可以创建自己的annotation来自动执行特定的任务，生成代码和其它有用的功能。
    </p>
    <p>
        关于annotation的一个经典的例子就是第三方库
        <a href="http://androidannotations.org" sl-processed="1">
            AndroidAnnotations
        </a>
        。它提供了各种定制的annotation，以将多行的功能简化为单行的annotation，还包含了其它有用的功能。你可以查看一下哪些是有用的，以及它们可以为你的app提供什么。
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