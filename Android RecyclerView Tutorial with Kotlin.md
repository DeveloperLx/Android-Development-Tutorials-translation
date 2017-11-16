# Android RecyclerView教程 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/170075/android-recyclerview-tutorial-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <p>
            <em>
                更新日志
            </em>
            ：本教程已由Rod Biresch更新至Kotlin，Android 26 (Oreo)及Android Studio 3.0的版本。原教材由Darryl
            Bayliss编写。
        </p>
    </div>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-320x320.png"
        alt="RecyclerView-feature" width="250" height="250" class="alignright size-medium wp-image-136529"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/06/RecyclerView-feature-128x128.png 128w"
        sizes="(max-width: 250px) 100vw, 250px">
        <br>
        Recycling is one of those things that is good for the planet, 
        and it’s a common sense way to make sure we don’t find ourselves buried in our own
        rubbish or without sufficient resources in the future.
    </p>
    <p>
        A few Android engineers thought about the benefits of recycling and realized
        that an OS can also run more efficiently if it recycles. The result of
        this inspiration was millions of eco-Warriors and recycling enthusiasts
        rejoicing when the
        <code>
            RecyclerView
        </code>
        widget was introduced into Android Lollipop — or something like that.
        :]
    </p>
    <p>
        There was even more celebration when Google announced a support library
        to make this clean, green, recycling machine backwards compatible all the
        way to Android Eclair (2.2), which was released back in 2010!
    </p>
    <p>
        In this tutorial, you’re going to experience the power of RecyclerView
        in action and learn:
    </p>
    <ul>
        <li>
            The purpose of a RecyclerView
        </li>
        <li>
            The components that make up a RecyclerView
        </li>
        <li>
            How to change the layout of a RecyclerView
        </li>
        <li>
            How to add some nice animations to your RecyclerView
        </li>
    </ul>
    <p>
        You’re also going to blast off into outer space with the sample app
        <em>
            Galacticon
        </em>
        . You’ll use it to build out a feed of daily astronomy photos from a public
        NASA API.
    </p>
    <div class="note">
        <p>
            <em>
                Prerequisites
            </em>
            : You should have a working knowledge of developing for Android with Kotlin
            before working through this tutorial. If you need a refresher, take a look
            at some of our
            <a title="Android Tutorials" href="http://www.raywenderlich.com/category/android"
            target="_blank">
                introductory tutorials
            </a>
            ! Also, you will need Android Studio 3.0 or greater.
        </p>
    </div>
    <h2>
        Heading to Cape Canaveral: Getting Started
    </h2>
    <p>
        Download the
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/galacticon-starter-5.zip">
            starter project
        </a>
        and open it up in Android Studio. There isn’t much to it yet, nor is the
        almighty RecyclerView anywhere to be seen.
    </p>
    <p>
        Click the
        <em>
            Run app
        </em>
        button at the top and you’ll see something that resembles outer space
        in all the wrong ways:
        <br>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1-281x500.png"
        alt="" width="281" height="500" class="aligncenter size-large wp-image-170498"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/1-empty-app-1.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        It’s empty, but that’s ok. You wouldn’t learn much if all the work was
        done for you! Before you can add that amazing astrophotography from NASA,
        you’ll need to do some set up work.
    </p>
    <h2>
        Obtaining The (API) Keys to the Shuttle
    </h2>
    <p>
        You’ll use the
        <a href="http://apod.nasa.gov" target="_blank" title="Astronomy Picture of the Day API">
            Astronomy Picture of the Day API
        </a>
        , one of the most popular web services provided by NASA. To ensure it
        doesn’t fall victim to unsolicited traffic, the service requires you to
        have an API key to use it in an application.
    </p>
    <p>
        Fortunately, getting a key is as simple as putting your name and email
        address into
        <a href="https://api.nasa.gov/index.html#apply-for-an-api-key" target="_blank"
        title="webpage">
            api.nasa.gov
        </a>
        and copying the API key that appears on the screen or the email sent to
        you.
    </p>
    <p>
        Once you’ve acquired your API key, copy it and open the
        <em>
            strings.xml
        </em>
        file in your project. Paste your API key into the
        <code>
            api_key
        </code>
        string resource, replacing
        <code>
            INSERT API KEY HERE
        </code>
        :
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-700x296.png"
        alt="4. API_KEY paste" width="700" height="296" class="aligncenter size-large wp-image-126540"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-700x296.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-480x203.png 480w, https://koenig-media.raywenderlich.com/uploads/2016/02/4.-API_KEY-paste-768x325.png 768w"
        sizes="(max-width: 700px) 100vw, 700px">
    </p>
    <h2>
        Space Oddity: Learning About RecyclerView
    </h2>
    <p>
        You’re about to blast off into outer space to explore the vastness of
        RecyclerViews, but no competent commander heads into the unknown without
        preparation. You have questions, and you need answers before you go any
        further. Consider this section as your mission brief.
    </p>
    <p>
        A RecyclerView can be thought of as a combination of a
        <em>
            ListView
        </em>
        and a
        <em>
            GridView
        </em>
        . However, there are extra features that separate your code into maintainable
        components even as they enforce memory-efficient design patterns.
    </p>
    <p>
        But how could it be better than the tried and tested ListView and GridView
        you’re used to? Could it be some kind of alien technology? The answers,
        as always, are in the details.
    </p>
    <h3>
        Why You Need RecyclerView
    </h3>
    <p>
        Imagine you’re creating a ListView where the custom items you want to
        show are quite complicated. You take time to lovingly create a row layout
        for these items, and then use that layout inside your adapter.
    </p>
    <p>
        Inside your
        <code>
            getView()
        </code>
        method, you inflate your new item layout. You then reference every view
        within by using the unique ids you provided in your XML to customize and
        add some view logic. Once finished, you pass that view to the ListView,
        ready to be drawn on the screen. All is well…or is it?
    </p>
    <p>
        The truth is that ListViews and GridViews only do half the job of achieving
        true memory efficiency. They recycle the item
        <em>
            layout
        </em>
        , but don’t keep references to the layout children, forcing you to call
        <code>
            findViewById()
        </code>
        for every child of your item layout every time you call
        <code>
            getView()
        </code>
        .
    </p>
    <p>
        All this calling around can become
        <i>
            very
        </i>
        processor-intensive, especially for complicated layouts. Furthermore,
        the situation can cause your ListView scrolling to become jerky or non-responsive
        as it frantically tries to grab references to the views you need.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/02/ListView--700x491.png"
        alt="ListView-" width="600" height="421" class="aligncenter size-large wp-image-126766"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/02/ListView-.png 700w, https://koenig-media.raywenderlich.com/uploads/2016/02/ListView--456x320.png 456w"
        sizes="(max-width: 600px) 100vw, 600px">
    </p>
    <p>
        Android engineers initially provided a solution to this problem on the
        Android Developers site with
        <a href="http://developer.android.com/training/improving-layouts/smooth-scrolling.html#ViewHolder"
        title="smooth scrolling" target="_blank">
            smooth scrolling
        </a>
        , via the power of the
        <code>
            View Holder
        </code>
        pattern.
    </p>
    <p>
        When you use this pattern, you create a class that becomes an in-memory
        reference to all the views needed to fill your layout. The benefit is you
        set the references once and reuse them, effectively working around the
        performance hit that comes with repeatedly calling
        <code>
            findViewById()
        </code>
        .
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/viewholder_new_larger.png"
        alt="viewholder_new_larger" width="594" height="455" class="aligncenter size-full wp-image-134106"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/05/viewholder_new_larger.png 594w, https://koenig-media.raywenderlich.com/uploads/2016/05/viewholder_new_larger-418x320.png 418w"
        sizes="(max-width: 594px) 100vw, 594px">
    </p>
    <p>
        The problem is that it’s an optional pattern for a ListView or GridView.
        If you’re unaware of this detail, then you may wonder why your precious
        ListViews and GridViews are so slow.
    </p>
    <h2>
        First Contact: RecyclerView and Layouts
    </h2>
    <p>
        The arrival of the RecyclerView changed everything. It still uses an
        <em>
            Adapter
        </em>
        to act as a data source; however, you have to create
        <em>
            ViewHolders
        </em>
        to keep references in memory.
    </p>
    <p>
        When you need a new view, it either creates a new ViewHolder object to
        inflate the layout and hold those references, or it recycles one from the
        existing stack.
    </p>
    <p>
        Now you know why it’s called a RecyclerView!
    </p>
    <p>
        Another perk of using RecyclerViews is that they come with default animations
        that you don’t have to create or add yourself — they just work.
    </p>
    <p>
        Thanks to the requirement for a ViewHolder, the RecyclerView knows exactly
        which animation to apply to which item. Best of all, it just does it as
        required. You can even create your own animations and apply them as needed.
    </p>
    <p>
        The last and most interesting component of a RecyclerView is its
        <em>
            LayoutManager
        </em>
        . This object positions the RecyclerView’s items and tells it when to
        recycle items that have transitioned off-screen.
    </p>
    <p>
        Layout Managers come in three default flavors:
    </p>
    <ul>
        <li>
            <em>
                LinearLayoutManager
            </em>
            positions your items to look like a standard ListView
        </li>
        <li>
            <em>
                GridLayoutManager
            </em>
            positions your items in a grid format similar to a GridView
        </li>
        <li>
            <em>
                StaggeredGridLayoutManager
            </em>
            positions your items in a staggered grid format.
        </li>
    </ul>
    <p>
        You can also create your own
        <code>
            LayoutManagers
        </code>
        to use with a
        <code>
            RecyclerView
        </code>
        if you want an extra bit of customization.
    </p>
    <p>
        Hopefully that answers all your questions, commander. Now, onto the mission!
    </p>
    <h2>
        Preparing for Launch: Creating the RecyclerView
    </h2>
    <p>
        To create the RecyclerView, you’ll break the work into four parts:
    </p>
    <ol>
        <li>
            Declare the RecyclerView in an activity layout and reference it in your
            activity Kotlin file.
        </li>
        <li>
            Create a custom item XML layout for your RecyclerView to use for its items.
        </li>
        <li>
            Create the view holder for your view items, hook up the data source of
            the RecyclerView and handle the view logic by creating a RecyclerView Adapter.
        </li>
        <li>
            Attach the adapter to the RecyclerView.
        </li>
    </ol>
    <p>
        Step one should be familiar. Open up the
        <em>
            activity_main.xml
        </em>
        layout file, and add the following as a child of the LinearLayout:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                android.support.v7.widget.RecyclerView
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/recyclerView"
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
                android:scrollbars
            </span>
            =
            <span class="hljs-string">
                "vertical"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        Here you’re setting up the layout and telling the RecyclerView to match
        its parent.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : You’re using the v7 support library for backwards compatibility with
            older devices. The starter project already adds the RecyclerView Support
            Library as a dependency in your app’s
            <em>
                build.gradle
            </em>
            file. If you want more information on how to do it yourself, check out
            the
            <a href="http://developer.android.com/tools/support-library/setup.html"
            target="_blank">
                Android developer website
            </a>
            .
        </p>
    </div>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        and declare the following property at the top of the class:
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
        linearLayoutManager: LinearLayoutManager
    </pre>
    <p>
        In
        <code>
            onCreate()
        </code>
        , add the following lines after
        <code>
            setContentView
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        linearLayoutManager = LinearLayoutManager(
        <span class="hljs-keyword">
            this
        </span>
        ) recyclerView.layoutManager = linearLayoutManager
    </pre>
    <p>
        Android Studio should prompt you to import
        <code>
            kotlinx.android.synthetic.main.activity_main.*
        </code>
        for
        <code>
            recyclerView
        </code>
        . You may wonder how do we have a reference to
        <code>
            recyclerView
        </code>
        without first finding the view, i.e.
        <code>
            findViewById()
        </code>
        ? The project has been configured to use
        <a href="https://kotlinlang.org/docs/tutorials/android-plugin.html" target="_blank">
            Kotlin Android Extensions
        </a>
        plugin. This plugin enables the ability to import views in a layout as
        “synthetic” properties.
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        kotlinx.android.synthetic.main.activity_main.*
    </pre>
    <p>
        The
        <code>
            recyclerView
        </code>
        is now an extension property for
        <code>
            Activity
        </code>
        , and it has the same type as declared in
        <code>
            activity_main.xml
        </code>
        . The plugin removes a lot of boilerplate code and reduces the risk of
        potential bugs.
    </p>
    <p>
        Phase one of ignition is complete! You’ve declared and allocated memory
        for two parts of the puzzle that RecyclerViews need to work: The RecyclerView
        and its Layout Manager.
    </p>
    <h2>
        Ignition Phase 2: Laying out the RecyclerView Items
    </h2>
    <p>
        Phase two of ignition involves creating a custom layout for the item you
        want your RecyclerView to use. It works exactly the same as it does when
        you create a custom layout for a ListView or Gridview.
    </p>
    <p>
        Head over to your layout folder and create a new layout with the name
        <code>
            recyclerview_item_row
        </code>
        and set the root element as a
        <code>
            LinearLayout
        </code>
        . In your new layout, add the following XML elements as children of your
        LinearLayout:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                ImageView
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/itemImage"
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
                android:layout_gravity
            </span>
            =
            <span class="hljs-string">
                "center"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "8dp"
            </span>
            <span class="hljs-attr">
                android:layout_weight
            </span>
            =
            <span class="hljs-string">
                "3"
            </span>
            <span class="hljs-attr">
                android:adjustViewBounds
            </span>
            =
            <span class="hljs-string">
                "true"
            </span>
            /&gt;
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
                "@+id/itemDate"
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
                android:layout_gravity
            </span>
            =
            <span class="hljs-string">
                "top|start"
            </span>
            <span class="hljs-attr">
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "8dp"
            </span>
            <span class="hljs-attr">
                android:layout_weight
            </span>
            =
            <span class="hljs-string">
                "1"
            </span>
            <span class="hljs-attr">
                tools:text
            </span>
            =
            <span class="hljs-string">
                "Some date"
            </span>
            /&gt;
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
                "@+id/itemDescription"
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
                android:layout_gravity
            </span>
            =
            <span class="hljs-string">
                "center|start"
            </span>
            <span class="hljs-attr">
                android:layout_weight
            </span>
            =
            <span class="hljs-string">
                "1"
            </span>
            <span class="hljs-attr">
                android:ellipsize
            </span>
            =
            <span class="hljs-string">
                "end"
            </span>
            <span class="hljs-attr">
                android:maxLines
            </span>
            =
            <span class="hljs-string">
                "5"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        No rocket science here: You declared a few views as children of your layout,
        and can now use them in your adapter.
    </p>
    <h2>
        Adapters: Rocket Fuel for Your RecyclerView
    </h2>
    <p>
        Right-click on the
        <em>
            com.raywenderlich.galacticon
        </em>
        folder, select
        <em>
            New \ Kotlin File/Class
        </em>
        , and name it
        <em>
            RecyclerAdapter
        </em>
        and select
        <em>
            Class
        </em>
        for Kind. At the top of the file below the
        <code>
            package
        </code>
        declaration, import the support library’s version of RecyclerView:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        android.support.v7.widget.RecyclerView
    </pre>
    <p>
        Make the class extend
        <em>
            RecyclerView.Adapter
        </em>
        so it looks like the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                RecyclerAdapter
            </span>
            :
            <span class="hljs-type">
                RecyclerView.Adapter
            </span>
            &lt;
            <span class="hljs-type">
                RecyclerAdapter.PhotoHolder
            </span>
            &gt;
        </span>
        () { }
    </pre>
    <p>
        Android Studio will detect that you’re extending a class that has required
        methods and will underline your class declaration with a red squiggle.
    </p>
    <p>
        To resolve this, click on the line of code to insert your cursor, then
        press
        <em>
            Option + Return
        </em>
        (or
        <em>
            Alt + Enter
        </em>
        on a PC) to bring up a context menu. Select
        <em>
            Implement Methods
        </em>
        :
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/5-Implements-RecyclerView-Adapter-Methods-650x382.png"
        alt="5" width="650" height="382" class="aligncenter size-large wp-image-170792"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/5-Implements-RecyclerView-Adapter-Methods-650x382.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/5-Implements-RecyclerView-Adapter-Methods-480x282.png 480w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        Confirm you want to implement the suggested methods by clicking
        <em>
            OK
        </em>
        :
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/6-Confirm-RecyclerView-Implemention-Methods-650x381.png"
        alt="" width="650" height="381" class="aligncenter size-large wp-image-170793"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/6-Confirm-RecyclerView-Implemention-Methods-650x381.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/6-Confirm-RecyclerView-Implemention-Methods-480x282.png 480w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        These methods are the driving force behind your RecyclerView adapter.
        Note how there is still a compiler error for the moment– this is because
        your adapter and the required methods are actually defined using your ViewHolder
        class,
        <code>
            PhotoHolder
        </code>
        , which doesn’t exist just yet. You’ll get to define your ViewHolder and
        see what each required method does shortly, so just hang tight, Commander!
    </p>
    <p>
        As with every adapter, you need to provide the corresponding view a means
        of populating items and deciding how many items there should be.
    </p>
    <p>
        Item clicks were previously managed by a ListView’s or GridView’s
        <code>
            onItemClickListener
        </code>
        . A RecyclerView doesn’t provide methods like this because it has one
        focus: ensuring the items inside are positioned properly and managed efficiently.
    </p>
    <p>
        The job of listening for actions is now the responsibility of the RecyclerView
        item and its children. This may seem like more overhead, but in return,
        you get fine-grained control over how your item’s children can act.
    </p>
    <p>
        At the top of your RecyclerAdapter class, add a variable
        <code>
            photos
        </code>
        to hold your photos in the primary constructor:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                RecyclerAdapter
            </span>
        </span>
        (
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        photos: ArrayList&lt;Photo&gt;) RecyclerView.Adapter&lt;RecyclerAdapter.PhotoHolder&gt;()
        {
    </pre>
    <p>
        Nice job, Commander! Your adapter now knows where to look for data. Soon
        you’ll have an ArrayList of photos filled with the finest astrophotography!
    </p>
    <p>
        Next, you’ll populate the stubbed methods that were added by Android Studio.
    </p>
    <p>
        The first method,
        <code>
            getItemCount()
        </code>
        , is pretty simple and should be familiar from your work with ListViews
        or GridViews.
    </p>
    <p>
        The adapter will work out how many items to display. In this case, you
        want the adapter to show every photo you’ve downloaded from NASA’s API.
        To do that, add update
        <code>
            getItemCount()
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
                getItemCount
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        = photos.size
    </pre>
    <p>
        Next, you’re going to exploit the
        <code>
            ViewHolder
        </code>
        pattern to make an object that holds all your view references.
    </p>
    <h2>
        Velcro For All: Keeping Hold Of Your Views
    </h2>
    <p>
        To create a
        <strong>
            PhotoHolder
        </strong>
        for your view references, you’ll create a nested class in your adapter.
        You’ll add it here rather than in a separate class because its behavior
        is tightly coupled with the adapter. First, import synthetic properties
        for the recycler view item so you can reference the view properties:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            import
        </span>
        kotlinx.android.synthetic.main.recyclerview_item_row.view.*
    </pre>
    <p>
        Add the following code at the bottom of the RecyclerAdapter class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-comment">
            //1
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                PhotoHolder
            </span>
        </span>
        (v: View) : RecyclerView.ViewHolder(v), View.OnClickListener {
        <span class="hljs-comment">
            //2
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        view: View = v
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        photo: Photo? =
        <span class="hljs-literal">
            null
        </span>
        <span class="hljs-comment">
            //3
        </span>
        init { v.setOnClickListener(
        <span class="hljs-keyword">
            this
        </span>
        ) }
        <span class="hljs-comment">
            //4
        </span>
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onClick
            </span>
            <span class="hljs-params">
                (v:
                <span class="hljs-type">
                    View
                </span>
                )
            </span>
        </span>
        { Log.d(
        <span class="hljs-string">
            "RecyclerView"
        </span>
        ,
        <span class="hljs-string">
            "CLICK!"
        </span>
        ) }
        <span class="hljs-keyword">
            companion
        </span>
        <span class="hljs-keyword">
            object
        </span>
        {
        <span class="hljs-comment">
            //5
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        PHOTO_KEY =
        <span class="hljs-string">
            "PHOTO"
        </span>
        } }
    </pre>
    <p>
        So what did you do here?
    </p>
    <ol>
        <li>
            Made the class extend RecyclerView.ViewHolder, allowing it to be used
            as a ViewHolder for the adapter.
        </li>
        <li>
            Added a reference to the lifecycle of the object to allow the ViewHolder
            to hang on to your View, so it can access the ImageView and TextView as
            an extension property. Kotlin Android Extensions plugin adds in hidden
            caching functions and fields so that views are not constantly queried.
        </li>
        <li>
            Initialized the
            <code>
                View.OnClickListener
            </code>
            .
        </li>
        <li>
            Implemented the required method for
            <code>
                View.OnClickListener
            </code>
            since ViewHolders are responsible for their own event handling.
        </li>
        <li>
            Added a key for easier reference to the particular item being used to
            launch your RecyclerView.
        </li>
    </ol>
    <p>
        You should still have a compiler errors with
        <code>
            onBindViewHolder
        </code>
        and
        <code>
            onCreateViewHolder
        </code>
        methods. Change the
        <code>
            holder: ?
        </code>
        argument on
        <code>
            onBindViewHolder
        </code>
        to have a type
        <code>
            RecyclerAdapter.PhotoHolder
        </code>
        .
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
                onBindViewHolder
            </span>
            <span class="hljs-params">
                (holder:
                <span class="hljs-type">
                    RecyclerAdapter
                </span>
                .
                <span class="hljs-type">
                    PhotoHolder
                </span>
                , position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        { TODO(
        <span class="hljs-string">
            "not implemented"
        </span>
        )
        <span class="hljs-comment">
            //To change body of created functions use File | Settings | File Templates.
        </span>
        }
    </pre>
    <p>
        Then add a
        <code>
            RecyclerAdapter.PhotoHolder
        </code>
        return type to the
        <code>
            onCreateViewHolder
        </code>
        method and remove the safe call operator (i.e.
        <code>
            ?
        </code>
        ) of the
        <code>
            parent
        </code>
        argument type.
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
                onCreateViewHolder
            </span>
            <span class="hljs-params">
                (parent:
                <span class="hljs-type">
                    ViewGroup
                </span>
                , viewType:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        : RecyclerAdapter.PhotoHolder { TODO(
        <span class="hljs-string">
            "not implemented"
        </span>
        )
        <span class="hljs-comment">
            //To change body of created functions use File | Settings | File Templates.
        </span>
        }
    </pre>
    <p>
        You should now be able to build and run the app again, but it’ll look
        about the same because you haven’t told the RecyclerView how to associate
        the PhotoHolder with a view.
    </p>
    <h2>
        Assembling The Pieces
    </h2>
    <p>
        Sometimes there are no ViewHolders available. In this scenario, RecylerView
        will ask
        <code>
            onCreateViewHolder()
        </code>
        from RecyclerAdapter to make a new one. You’ll use the item layout — PhotoHolder
        — to create a view for the ViewHolder.
    </p>
    <p>
        The inflate code could simply be added to
        <code>
            onCreateViewHolder()
        </code>
        . However, this is a nice opportunity to show a really cool Kotlin feature
        called
        <a href="https://kotlinlang.org/docs/reference/extensions.html" target="_blank">
            Extensions
        </a>
        .
    </p>
    <p>
        First, add a new Kotlin file named
        <em>
            Extensions.kt
        </em>
        to the project and then add the following new extension function to the
        new file:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            ViewGroup.
            <span class="hljs-title">
                inflate
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-meta">
                    @LayoutRes
                </span>
                layoutRes:
                <span class="hljs-type">
                    Int
                </span>
                , attachToRoot:
                <span class="hljs-type">
                    Boolean
                </span>
                =
                <span class="hljs-literal">
                    false
                </span>
                )
            </span>
        </span>
        : View {
        <span class="hljs-keyword">
            return
        </span>
        LayoutInflater.from(context).inflate(layoutRes,
        <span class="hljs-keyword">
            this
        </span>
        , attachToRoot) }
    </pre>
    <p>
        Replace the
        <code>
            TODO("not implemented")
        </code>
        line between the curly braces in
        <code>
            onCreateViewHolder()
        </code>
        with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        inflatedView = parent.inflate(R.layout.recyclerview_item_row,
        <span class="hljs-literal">
            false
        </span>
        )
        <span class="hljs-keyword">
            return
        </span>
        PhotoHolder(inflatedView)
    </pre>
    <p>
        Here you inflate the view from its layout and pass it in to a PhotoHolder.
        The
        <code>
            parent.inflate(R.layout.recyclerview_item_row, false)
        </code>
        method will execute the new
        <code>
            ViewGroup.inflate(...)
        </code>
        extension function to inflate the layout.
    </p>
    <p>
        And with that, you’ve made it so the object holds onto those references
        while it’s recycled, but there are still more pieces to put together before
        you can launch your rocketship.
    </p>
    <p>
        Start a new activity by replacing the log in ViewHolder’s
        <code>
            onClick
        </code>
        with this code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        context = itemView.context
        <span class="hljs-keyword">
            val
        </span>
        showPhotoIntent = Intent(context, PhotoActivity::
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
        showPhotoIntent.putExtra(PHOTO_KEY, photo) context.startActivity(showPhotoIntent)
    </pre>
    <p>
        This grabs the current context of your item view and creates an intent
        to show a new activity on the screen, passing the photo object you want
        to show. Passing the context object into the intent allows the app to know
        what activity it is leaving.
    </p>
    <p>
        Next thing to do is to add this method inside
        <code>
            PhotoHolder
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                bindPhoto
            </span>
            <span class="hljs-params">
                (photo:
                <span class="hljs-type">
                    Photo
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            this
        </span>
        .photo = photo Picasso.with(view.context).load(photo.url).into(view.itemImage)
        view.itemDate.text = photo.humanDate view.itemDescription.text = photo.explanation
        }
    </pre>
    <p>
        This binds the photo to the PhotoHolder, giving your item the data it
        needs to work out what it should show.
    </p>
    <p>
        It also adds the suggested
        <a href="http://square.github.io/picasso/" target="_blank" title="Picasso">
            Picasso
        </a>
        import, which is a library that makes it significantly simpler to get
        images from a given URL.
    </p>
    <p>
        The last piece of the PhotoHolder assembly will tell it how to show the
        right photo at the right moment. It’s the RecyclerAdapter’s
        <code>
            onBindViewHolder
        </code>
        , and it lets you know a new item will be available on screen and the
        holder needs some data.
    </p>
    <p>
        Add the following code inside the
        <code>
            onBindViewHolder()
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        itemPhoto = photos[position] holder.bindPhoto(itemPhoto)
    </pre>
    <p>
        Here you’re passing in a copy of your ViewHolder and the position where
        the item will show in your RecyclerView, and calling
        <code>
            bindPhoto(...)
        </code>
        .
    </p>
    <p>
        And that’s all you needed to do here on the assembly — just use the position
        where your ViewHolder will appear to grab the photo out of your list, and
        then pass it to your ViewHolder.
    </p>
    <p>
        Step three of your ignition check protocol is complete!
    </p>
    <h2>
        Countdown And Liftoff: Hooking up the Adapter And RecyclerView
    </h2>
    <p>
        This is the moment you’ve been waiting for, the final stage before blast
        off! All you need to do is hook your adapter up to your RecyclerView and
        make sure it retrieves photos when it’s created so you can explore space
        — in pictures.
    </p>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        , and add this property at the top:
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
        adapter: RecyclerAdapter
    </pre>
    <p>
        Next, underneath the assignment of
        <code>
            recyclerView.layoutManager
        </code>
        , add the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        adapter = RecyclerAdapter(photosList) recyclerView.adapter = adapter
    </pre>
    <p>
        Here you’re creating the adapter, passing in the constructors it needs
        and setting it as the adapter for your RecyclerView.
    </p>
    <p>
        Although the adapter is connected, there’s one more thing to do to make
        sure you don’t have an empty screen.
    </p>
    <p>
        In
        <code>
            onStart()
        </code>
        , underneath the call to
        <code>
            super
        </code>
        , add this code:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            if
        </span>
        (photosList.size ==
        <span class="hljs-number">
            0
        </span>
        ) { requestPhoto() }
    </pre>
    <p>
        This adds a check to see if your list is empty, and if yes, it requests
        a photo.
    </p>
    <p>
        Next, in
        <code>
            receivedNewPhoto()
        </code>
        , update the method so it looks like the following:
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
                receivedNewPhoto
            </span>
            <span class="hljs-params">
                (newPhoto:
                <span class="hljs-type">
                    Photo
                </span>
                )
            </span>
        </span>
        { runOnUiThread { photosList.add(newPhoto) adapter.notifyItemInserted(photosList.size)
        } }
    </pre>
    <p>
        Here you are informing the recycler adapter that an item was added after
        the list of photos was updated.
    </p>
    <p>
        Now you’re ready to commence the ignition sequence, er…I mean run the
        app.
    </p>
    <p>
        <em>
            Run the app
        </em>
        , load up the emulator and before long, Galacticon should look something
        like this:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-281x500.png"
        alt="7. RecyclerView Working" width="281" height="500" class="aligncenter size-large wp-image-171028"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/7-RecyclerView-Working.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        That’s not all. Tap on the photo, and you should be greeted with a new
        activity that brings that item into focus:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-281x500.png"
        alt="8. Focus Activity" width="281" height="500" class="aligncenter size-large wp-image-171029"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/8-Focus-Activity.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        But that’s still not all! Try
        <em>
            rotating your device or emulator
        </em>
        (function + control + F11/F12) and you’ll see the image in full screen
        glory!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-650x366.png"
        alt="9. Landscape focus" width="650" height="366" class="aligncenter size-large wp-image-171030"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-650x366.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-480x270.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/9-Landscape-Focus-266x151.png 266w"
        sizes="(max-width: 650px) 100vw, 650px">
    </p>
    <p>
        Depending on the size of the image and your device screen it may look
        a little distorted, but don’t worry about that.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-320x320.png"
        alt="" width="320" height="320" class="aligncenter size-medium wp-image-173047"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/10/stars_so_beautiful-128x128.png 128w"
        sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <p>
        Congratulations! You have a working RecyclerView and can take your journey
        amongst the stars.
    </p>
    <h2>
        Taking A Spacewalk: Adding Scrolling support
    </h2>
    <p>
        If you head back to
        <em>
            MainActivity
        </em>
        on your device and try to scroll down, you’ll notice something is amiss
        — your RecyclerView isn’t retrieving any new photos.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-281x500.png"
        alt="10. Scrolling Not Working" width="281" height="500" class="aligncenter size-large wp-image-171032"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/10-Scrolling-Not-Working.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        Your RecyclerView is doing exactly as it’s told by showing the contents
        of
        <code>
            photosList
        </code>
        . The problem is that the app will only retrieve one photo when you load
        the app. It has no idea when or how to grab more photos.
    </p>
    <p>
        So next, you’ll retrieve the number of the photos and the last visible
        photo index while scrolling. Then you’ll check to see if the last photo
        is visible and if there are no photos already on request. If these are
        both true, then your app goes and downloads more pretty photos!
    </p>
    <p>
        This patch will require a spacewalk, so break out your spacesuit and get
        ready for a zero gravity experience.
    </p>
    <p>
        In
        <em>
            MainActivity.kt
        </em>
        , add this property with custom accessor below to MainActivity:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        lastVisibleItemPosition:
        <span class="hljs-built_in">
            Int
        </span>
        <span class="hljs-keyword">
            get
        </span>
        () = linearLayoutManager.findLastVisibleItemPosition()
    </pre>
    <p>
        This uses your RecyclerView’s LinearLayoutManager to get the index of
        the last visible item on the screen.
    </p>
    <p>
        Next, you add a method that inserts an
        <code>
            onScrollListener
        </code>
        to your RecyclerView, so it can get a callback when the user scrolls:
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
                setRecyclerViewScrollListener
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        { recyclerView.addOnScrollListener(
        <span class="hljs-keyword">
            object
        </span>
        : RecyclerView.OnScrollListener() {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onScrollStateChanged
            </span>
            <span class="hljs-params">
                (recyclerView:
                <span class="hljs-type">
                    RecyclerView
                </span>
                ?, newState:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            super
        </span>
        .onScrollStateChanged(recyclerView, newState)
        <span class="hljs-keyword">
            val
        </span>
        totalItemCount = recyclerView!!.layoutManager.itemCount
        <span class="hljs-keyword">
            if
        </span>
        (!imageRequester.isLoadingData &amp;&amp; totalItemCount == lastVisibleItemPosition
        +
        <span class="hljs-number">
            1
        </span>
        ) { requestPhoto() } } }) }
    </pre>
    <p>
        This function gives the RecyclerView a scroll listener that is triggered
        by scrolling. During scrolling, the listener retrieves the count of the
        items in its LayoutManager and calculates the last visible photo index.
        Once done, it compares these numbers (incrementing the index by 1 because
        the index begins at 0 while the count begins at 1). If they match and there
        are no photos already on request, then you request a new photo.
    </p>
    <p>
        Finally, hook everything to the RecyclerView by calling this method from
        <code>
            onCreate
        </code>
        , just beneath where you set your RecyclerView Adapter:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setRecyclerViewScrollListener()
    </pre>
    <p>
        Hop back in the ship (build and run the app again). Scroll down and you
        should see quite an improvement!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-281x500.png"
        alt="11. Scrolling Update" width="281" height="500" class="aligncenter size-large wp-image-171033"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/11-Scrolling-Update.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        Excellent work, your RecyclerView now updates to show the latest photo
        requested by your app. The great thing is that
        <code>
            receivedNewPhoto()
        </code>
        handles most of the work because you told it to notify your adapter about
        new items.
    </p>
    <p>
        That earns an intergalactic thumbs up for upcycling code!
    </p>
    <h2>
        Layout Changes
    </h2>
    <p>
        Now that your RecyclerView is up and running, it’s time to trick out your
        spaceship.
    </p>
    <p>
        Wouldn’t it be cool if your RecyclerView could change its layout? Good
        news: RecyclerView’s item positioning is separated into a layout manager.
    </p>
    <p>
        Add a property for a
        <em>
            GridLayoutManager
        </em>
        to the top of
        <em>
            MainActivity.kt
        </em>
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
        gridLayoutManager: GridLayoutManager
    </pre>
    <p>
        Note that GridLayoutManager is a built-in layout manager, but it could
        just as easily be custom.
    </p>
    <p>
        In
        <code>
            onCreate()
        </code>
        , initialize the LayoutManager below the existing Linear Layout Manager:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        gridLayoutManager = GridLayoutManager(
        <span class="hljs-keyword">
            this
        </span>
        ,
        <span class="hljs-number">
            2
        </span>
        )
    </pre>
    <p>
        Just like you did with the previous LayoutManager, you pass in the context
        the manager will appear in, but unlike the former, it takes an integer
        parameter. In this case, you’re setting the number of columns the grid
        will have.
    </p>
    <p>
        Add this method to MainActivity:
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
                changeLayoutManager
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (recyclerView.layoutManager == linearLayoutManager) {
        <span class="hljs-comment">
            //1
        </span>
        recyclerView.layoutManager = gridLayoutManager
        <span class="hljs-comment">
            //2
        </span>
        <span class="hljs-keyword">
            if
        </span>
        (photosList.size ==
        <span class="hljs-number">
            1
        </span>
        ) { requestPhoto() } }
        <span class="hljs-keyword">
            else
        </span>
        {
        <span class="hljs-comment">
            //3
        </span>
        recyclerView.layoutManager = linearLayoutManager } }
    </pre>
    <p>
        This code checks to see what LayoutManager your RecyclerView is using,
        and then:
    </p>
    <ol>
        <li>
            If it’s using the LinearLayoutManager, it swaps in the GridLayoutManager
        </li>
        <li>
            It requests a new photo if your grid layout only has one photo to show
        </li>
        <li>
            If it’s using the GridLayoutManager, it swaps in the LinearLayoutManager
        </li>
    </ol>
    <p>
        Next, you need to make some changes to
        <code>
            lastVisibleItemPosition
        </code>
        to help it handle the new LayoutManager. Make it look like the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        lastVisibleItemPosition:
        <span class="hljs-built_in">
            Int
        </span>
        <span class="hljs-keyword">
            get
        </span>
        () =
        <span class="hljs-keyword">
            if
        </span>
        (recyclerView.layoutManager == linearLayoutManager) { linearLayoutManager.findLastVisibleItemPosition()
        }
        <span class="hljs-keyword">
            else
        </span>
        { gridLayoutManager.findLastVisibleItemPosition() }
    </pre>
    <p>
        Here you ask the RecyclerView to tell you what its LayoutManager is, then
        you ask that LayoutManager to tell you the position of the last visible
        item.
    </p>
    <p>
        To use the grid layout, make use of the Options menu button that is already
        available in the app. Add the following code underneath
        <code>
            onStart()
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
                onOptionsItemSelected
            </span>
            <span class="hljs-params">
                (item:
                <span class="hljs-type">
                    MenuItem
                </span>
                )
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Boolean
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (item.itemId == R.id.action_change_recycler_manager) { changeLayoutManager()
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-literal">
            true
        </span>
        }
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-keyword">
            super
        </span>
        .onOptionsItemSelected(item) }
    </pre>
    <p>
        This checks the ID of the item tapped in the menu, then works out what
        to do about it. In this case, there should only be one ID that will match
        up, effectively telling the app to go away and rearrange the RecyclerView’s
        LayoutManager.
    </p>
    <p>
        And just like that, you’re ready to go! Load up the app and tap the button
        at the top right of the screen, and you’ll begin to see the stars shift:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-281x500.png"
        alt="12. Grid Layout" width="281" height="500" class="aligncenter size-large wp-image-171037"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/12-Grid-Layout.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h2>
        Star Killer
    </h2>
    <p>
        Sometimes you’ll see things you just don’t like the look of, perhaps a
        galaxy far, far away that has fallen to the dark side or a planet that
        is prime for destruction. How could you go about killing it with a swipe?
    </p>
    <p>
        Luckily, Android engineers have provided a useful class named
        <code>
            ItemTouchHelper
        </code>
        that gives you easy swipe behavior. Creating and attaching this to a RecyclerView
        requires just a few lines of code.
    </p>
    <p>
        In
        <em>
            MainActivity.kt
        </em>
        , underneath
        <code>
            setRecyclerViewScrollListener()
        </code>
        add the following method:
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
                setRecyclerViewItemTouchListener
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            //1
        </span>
        <span class="hljs-keyword">
            val
        </span>
        itemTouchCallback =
        <span class="hljs-keyword">
            object
        </span>
        : ItemTouchHelper.SimpleCallback(
        <span class="hljs-number">
            0
        </span>
        , ItemTouchHelper.LEFT or ItemTouchHelper.RIGHT) {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onMove
            </span>
            <span class="hljs-params">
                (recyclerView:
                <span class="hljs-type">
                    RecyclerView
                </span>
                , viewHolder:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                , viewHolder1:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                )
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Boolean
        </span>
        {
        <span class="hljs-comment">
            //2
        </span>
        <span class="hljs-keyword">
            return
        </span>
        <span class="hljs-literal">
            false
        </span>
        }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onSwiped
            </span>
            <span class="hljs-params">
                (viewHolder:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                , swipeDir:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-comment">
            //3
        </span>
        <span class="hljs-keyword">
            val
        </span>
        position = viewHolder.adapterPosition photosList.removeAt(position) recyclerView.adapter.notifyItemRemoved(position)
        } }
        <span class="hljs-comment">
            //4
        </span>
        <span class="hljs-keyword">
            val
        </span>
        itemTouchHelper = ItemTouchHelper(itemTouchCallback) itemTouchHelper.attachToRecyclerView(recyclerView)
        }
    </pre>
    <p>
        Let’s go through this step by step:
    </p>
    <ol>
        <li>
            You create the callback and tell it what events to listen for. It takes
            two parameters, one for drag directions and one for swipe directions, but
            you’re only interested in swipe, so you pass 0 to inform the callback not
            to respond to drag events.
        </li>
        <li>
            You return false in
            <code>
                onMove
            </code>
            because you don’t want to perform any special behavior here.
        </li>
        <li>
            <code>
                onSwiped
            </code>
            is called when you swipe an item in the direction specified in the
            <code>
                ItemTouchHelper
            </code>
            . Here, you request the
            <code>
                viewHolder
            </code>
            parameter passed for the position of the item view, then you remove that
            item from your list of photos. Finally, you inform the RecyclerView adapter
            that an item has been removed at a specific position.
        </li>
        <li>
            You initialize the
            <code>
                ItemTouchHelper
            </code>
            with the callback behavior you defined, and then attach it to the RecyclerView.
        </li>
    </ol>
    <p>
        Add the method to the activity’s
        <code>
            onCreate()
        </code>
        , underneath
        <code>
            setRecyclerViewScrollListener()
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setRecyclerViewItemTouchListener()
    </pre>
    <p>
        This will attach the
        <code>
            ItemTouchListener
        </code>
        to the RecyclerView using the code you just wrote.
    </p>
    <p>
        <em>
            Run the app
        </em>
        once more and
        <em>
            swipe across
        </em>
        one of your items, you should see it begin to move. If you swipe the item
        far enough, you should see it animate and vanish. If other items are visible,
        then they will reorganize themselves to cover the hole. How cool is that?
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item-281x500.png"
        alt="13 Swipe Away Item" width="281" height="500" class="aligncenter size-large wp-image-171038"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/13-Swipe-Away-Item.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h2>
        Where To Go From Here?
    </h2>
    <div class="inline-video-ad" id="sub-banner-inline">
        <div class="inline-video-ad-wrapper">
            <a href="https://videos.raywenderlich.com/courses">
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
        Nice job! You’ve been on quite an adventure, but now it’s time to head
        back to Earth and think about what you’ve learned.
    </p>
    <ul>
        <li>
            You’ve created a RecyclerView and all the components it needs, such as
            a LayoutManager, an Adapter and a ViewHolder.
        </li>
        <li>
            You’ve updated and removed items from an Adapter.
        </li>
        <li>
            You’ve added some cool features like changing layouts and adding swipe
            functionality.
        </li>
    </ul>
    <p>
        Above all, you’ve experienced how separation of components — a key attribute
        of RecyclerViews — provides so much functionality with such ease. If you
        want your collections to be flexible and provide some excitement, then
        look no further than the all-powerful RecyclerView.
    </p>
    <p>
        The final project for this tutorial is available
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/galacticon-final.zip">
            here
        </a>
        .
    </p>
    <p>
        If you want to learn more about RecyclerViews then check out the
        <a href="http://developer.android.com/reference/android/support/v7/widget/RecyclerView.html"
        target="_blank" title="Android documentation">
            Android documentation
        </a>
        to see what it can do. Take a look at the
        <a href="http://developer.android.com/tools/support-library/features.html#v7-recyclerview"
        target="_blank" title="support library">
            support library
        </a>
        for RecyclerViews to learn how to use it on older devices. If you want
        to make them fit with the material design spec then check out the
        <a href="https://www.google.com/design/spec/components/lists.html" target="_blank"
        title="list component">
            list component
        </a>
        design specification.
    </p>
</div>