# Java在Android中的应用
---
#### [原文地址](https://www.raywenderlich.com/172711/intermediate-recyclerview) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/RecyclerViewIntermediate-feature.png"
        alt="Android RW" width="250" height="250" class="alignright size-full wp-image-87100">
    </p>
    <p>
        Have you ever wanted to go to Mars or just look out over Mars’ horizon?
        We can’t send you there but we can give you the next best thing: 
        an app with images from all the Mars rovers.
    </p>
    <p>
        To show those images, 
        we’ll use one of Android’s most popular views: 
        the
        <em>
            RecyclerView
        </em>
        .
    </p>
    <p>
        The
        <em>
            RecyclerView
        </em>
        layout was introduced in the Lollipop support library and Android developers have been using it for awhile. 
        It is one of the most useful layouts and
        gives you more flexibility compared to a
        <em>
            ListView
        </em>
        in a much more performant package.
    </p>
    <p>
        However, you may not know all that you can do with it. In this tutorial,
        you’ll see how to add sections, animations, dividers, and swipe gestures.
    </p>
    <p>
        You should be familiar with the basics of using
        <em>
            ReyclerView
        </em>
        . If not, you can read an introduction to using
        <em>
            RecyclerView
        </em>
        <a href="https://www.raywenderlich.com/126528/android-recyclerview-tutorial"
        target="_blank" sl-processed="1">
            here
        </a>
        .
    </p>
    <p>
        Here is a screenshot from the final version of our app:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png"
        alt="mars rover screenshot" width="281" height="500" class="aligncenter size-large wp-image-173107"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        Checkout those amazing Mars landscapes! :]
    </p>
    <p>
        You’re going to continue with the NASA site used in the previous
        <em>
            RecyclerView
        </em>
        tutorial, but do things a bit differently. 
        You’ll be using an API that will return a list of Mars rover photos. 
        Along with the
        <em>
            RecyclerView
        </em>
        of photos, there are two spinners to change the list of photos: 
        one for rovers and the other for cameras.
    </p>
    <h2>
        Getting Started
    </h2>
    <p>
        Download the starter project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/marsrovers-starter-1.zip"
        sl-processed="1">
            here
        </a>
        . Open it up in Android Studio 3.0.1 or later.
    </p>
    <p>
        Next, head to the NASA site (
        <a href="https://api.nasa.gov/index.html#apply-for-an-api-key" target="
        _blank"="" sl-processed="1">
            https://api.nasa.gov/index.html#apply-for-an-api-key
        </a>
        ) and get an API key to use for the rover photos.
    </p>
    <p>
        Build and run your app on an emulator or phone. You should see a default”Hello World!”
        <em>
            TextView
        </em>
        in the center.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953-281x500.png” alt="" width="281" height="500" class="aligncenter size-large wp-image-172715” srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953-281x500.png
        281w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953-180x320.png
        180w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170925-222953.png
        1440w" sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h3>
        Manifest
    </h3>
    <p>
        Add the following to your
        <em>
            AndroidManifest.xml
        </em>
        file before the application tag:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                uses-permission
            </span>
            <span class="hljs-attr">
                android:name
            </span>
            =
            <span class="hljs-string">
                "android.permission.INTERNET"
            </span>
            /&gt;
        </span>
    </pre>
    <p>
        This will allow you to get information from the NASA website. Note that
        this is not considered a “dangerous” permission and the user will not be
        asked to approve it.
    </p>
    <h3>
        String Data
    </h3>
    <p>
        To populate the spinners on the main screen, you will need to add strings
        for the spinners to the
        <em>
            strings.xml
        </em>
        file. Open
        <em>
            strings.xml
        </em>
        in the
        <em>
            res/values
        </em>
        folder and add the following after the
        <em>
            app_name
        </em>
        string:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "api_error "
            </span>
            &gt;
        </span>
        Problems getting Photos
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "rovers "
            </span>
            &gt;
        </span>
        Rovers
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "cameras "
            </span>
            &gt;
        </span>
        Cameras
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string-array
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "rovers"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Curiosity
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Opportunity
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Spirit
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string-array
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string-array
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "camera_names"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Front Hazard
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Rear Hazard
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Navigation
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Panoramic
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        Mast
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string-array
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                string-array
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "camera_values"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        FHAZ
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        RHAZ
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        NAVCAM
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        PANCAM
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        MAST
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                item
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                string-array
            </span>
            &gt;
        </span>
    </pre>
    <h2>
        Main Layout
    </h2>
    <p>
        You need to modify the main layout and add some code to the
        <code>
            MainActivity
        </code>
        class. Start out by replacing the layout in the
        <em>
            activity_main.xml
        </em>
        file.
    </p>
    <pre lang="xml" class="language-xml hljs">
        &lt;?xml version="1.0 " encoding="utf-8"?&gt;
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                android.support.constraint.ConstraintLayout
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            <span class="hljs-attr">
                xmlns:app
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res-auto"
            </span>
            <span class="hljs-attr">
                xmlns:tools
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/tools"
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
                tools:context
            </span>
            =
            <span class="hljs-string">
                "com.raywenderlich.marsrovers.MainActivity"
            </span>
            &gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                android.support.constraint.ConstraintLayout
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/control_layout"
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
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:padding
            </span>
            =
            <span class="hljs-string">
                "10dp"
            </span>
            <span class="hljs-attr">
                app:layout_constraintLeft_toLeftOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toTopOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            &gt;
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
                "@+id/roverLabel"
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
                android:text
            </span>
            =
            <span class="hljs-string">
                "@string/rovers"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toTopOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                android.support.v7.widget.AppCompatSpinner
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/rovers"
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
                app:layout_constraintRight_toRightOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toTopOf
            </span>
            =
            <span class="hljs-string">
                "parent"
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
                "@+id/cameraLabel"
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
                android:layout_marginTop
            </span>
            =
            <span class="hljs-string">
                "4dp"
            </span>
            <span class="hljs-attr">
                android:text
            </span>
            =
            <span class="hljs-string">
                "@string/cameras"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "@+id/roverLabel"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                android.support.v7.widget.AppCompatSpinner
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/cameras"
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
                app:layout_constraintRight_toRightOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "@+id/rovers"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                android.support.constraint.ConstraintLayout
            </span>
            &gt;
        </span>
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
                "@+id/recycler_view"
            </span>
            <span class="hljs-attr">
                android:layout_width
            </span>
            =
            <span class="hljs-string">
                "0dp"
            </span>
            <span class="hljs-attr">
                android:layout_height
            </span>
            =
            <span class="hljs-string">
                "0dp"
            </span>
            <span class="hljs-attr">
                android:visibility
            </span>
            =
            <span class="hljs-string">
                "gone"
            </span>
            <span class="hljs-attr">
                app:layout_constraintBottom_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintLeft_toLeftOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintRight_toRightOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "@+id/control_layout"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                ProgressBar
            </span>
            <span class="hljs-attr">
                android:id
            </span>
            =
            <span class="hljs-string">
                "@+id/progress"
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
                android:indeterminate
            </span>
            =
            <span class="hljs-string">
                "true"
            </span>
            <span class="hljs-attr">
                app:layout_constraintBottom_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintLeft_toLeftOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintRight_toRightOf
            </span>
            =
            <span class="hljs-string">
                "parent"
            </span>
            <span class="hljs-attr">
                app:layout_constraintTop_toBottomOf
            </span>
            =
            <span class="hljs-string">
                "@+id/control_layout"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                android.support.constraint.ConstraintLayout
            </span>
            &gt;
        </span>
    </pre>
    <p>
        This uses Android’s new
        <em>
            ConstraintLayout
        </em>
        to add two rows of spinners, one for the Rover and one for the camera.
        There’s a
        <em>
            RecyclerView
        </em>
        below the spinners. Below the
        <em>
            RecyclerView
        </em>
        there is a
        <em>
            ProgressBar
        </em>
        that will spin while the data is loading.
    </p>
    <p>
        Now, time to modify
        <em>
            MainActivity.kt
        </em>
        . In the
        <code>
            onCreate()
        </code>
        method, after the call to
        <code>
            setContentView
        </code>
        , add the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        recycler_view.visibility = View.GONE recycler_view.layoutManager = LinearLayoutManager(
        <span class="hljs-keyword">
            this
        </span>
        )
    </pre>
    <p>
        When Android Studio gives you an error on
        <code>
            recycler_view
        </code>
        , put your cursor on
        <code>
            recycler_view
        </code>
        and hit
        <em>
            option+return
        </em>
        on Mac or
        <em>
            Alt+Enter
        </em>
        on PC and select “Import”. This uses the Kotlin Android Extensions to
        turn the
        <code>
            R.id.recycler_view id
        </code>
        into a
        <code>
            recycler_view
        </code>
        variable.
    </p>
    <p>
        Now, run the app and you should see the following:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951-281x500.png"
        alt="mars rover screenshot" width="281" height="500" 
        class="aligncenter size-large wp-image-173095" 
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951-281x500.png
        281w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951-180x320.png
        180w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507085951.png
        1080w" sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <h2>
        ViewHolder
    </h2>
    <p>
        The
        <em>
            ViewHolder
        </em>
        class holds the inflated view, is created in a
        <em>
            RecyclerView.Adapter
        </em>
        in
        <code>
            onCreateViewHolder
        </code>
        and bound in
        <code>
            onBindViewHolder
        </code>
        .
    </p>
    <p>
        Before
        <em>
            RecyclerView
        </em>
        , Android developers used
        <em>
            ListView
        </em>
        to achieve similar behavior. As
        <em>
            ListView
        </em>
        usage matured, developers started using the “view holder” pattern and
        Google then made
        <em>
            ViewHolder
        </em>
        a key part of the
        <em>
            RecyclerView
        </em>
        API.
    </p>
    <p>
        You’ll be creating a special
        <code>
            ViewHolder
        </code>
        class that will allow you to handle text and image views without using
        <code>
            findViewById
        </code>
        . In this
        <code>
            DefaultViewHolder
        </code>
        class, you’ll start by going through all of the child views and putting
        them in a map so that you can easily retrieve the view later. See the starter
        project for the full
        <code>
            DefaultViewHolder
        </code>
        class.
    </p>
    <h2>
        Adapter Layouts
    </h2>
    <p>
        You need to create the two layouts that will be used in the adapter, one
        for the section headers, and one for the rows themselves. First, you’ll
        add the header style needed for the header item layout.
    </p>
    <p>
        <em>
            Header Style
        </em>
    </p>
    <p>
        Open the
        <em>
            styles.xml
        </em>
        file in the values resource folder and add the following style that will
        be used in the
        <em>
            header_item.xml
        </em>
        file:
    </p>
    <pre lang="xml" class="language-xml hljs">
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                style
            </span>
            <span class="hljs-attr">
                name
            </span>
            =
            <span class="hljs-string">
                "header"
            </span>
            &gt;
        </span>
        <span class="xml">
            <span class="hljs-tag">
                &lt;
                <span class="hljs-name
                ">
                    item
                </span>
                <span class="hljs-attr">
                    name
                </span>
                =
                <span class="hljs-string">
                    "android:textSize "
                </span>
                &gt;
            </span>
            16sp
            <span class="hljs-tag">
                &lt;/
                <span class="hljs-name">
                    item
                </span>
                &gt;
            </span>
            <span class="hljs-tag">
                &lt;
                <span class="hljs-name
                ">
                    item
                </span>
                <span class="hljs-attr">
                    name
                </span>
                =
                <span class="hljs-string">
                    "android:textColor "
                </span>
                &gt;
            </span>
            @android:color/holo_red_dark
            <span class="hljs-tag">
                &lt;/
                <span class="hljs-name">
                    item
                </span>
                &gt;
            </span>
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                style
            </span>
            &gt;
        </span>
    </pre>
    <p>
        You can use any color you’d like. To create the header, go to the
        <em>
            res/layout
        </em>
        folder. Right-click and choose
        <em>
            New/Layout resource file
        </em>
        . Name the file
        <em>
            header_item.xml
        </em>
        . You can leave the root element as suggested and then replace everything with the following:
    </p>
    <pre lang="xml" class="language-xml hljs">
        &lt;?xml version="1.0 " encoding="utf-8"?&gt;
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                LinearLayout
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            <span class="hljs-attr">
                xmlns:tools
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/tools"
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
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:orientation
            </span>
            =
            <span class="hljs-string">
                "vertical"
            </span>
            <span class="hljs-attr">
                android:padding
            </span>
            =
            <span class="hljs-string">
                "10dp"
            </span>
            &gt;
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
                "@+id/header_text"
            </span>
            <span class="hljs-attr">
                style
            </span>
            =
            <span class="hljs-string">
                "@style/header"
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
                "wrap_content"
            </span>
            <span class="hljs-attr">
                tools:text
            </span>
            =
            <span class="hljs-string">
                "Front Hazard"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                LinearLayout
            </span>
            &gt;
        </span>
    </pre>
    <p>
        This is just a
        <em>
            TextView
        </em>
        for the header text.
    </p>
    <p>
        Next, right-click on the layout folder and create a new layout named
        <em>
            row_item.xml
        </em>
        . Again, leave the root element and replace with:
    </p>
    <pre lang="xml" class="language-xml hljs">
        &lt;?xml version="1.0 " encoding="utf-8"?&gt;
        <span class="hljs-tag">
            &lt;
            <span class="hljs-name">
                LinearLayout
            </span>
            <span class="hljs-attr">
                xmlns:android
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/apk/res/android"
            </span>
            <span class="hljs-attr">
                xmlns:tools
            </span>
            =
            <span class="hljs-string">
                "http://schemas.android.com/tools"
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
                "wrap_content"
            </span>
            <span class="hljs-attr">
                android:orientation
            </span>
            =
            <span class="hljs-string">
                "vertical"
            </span>
            &gt;
        </span>
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
                "@+id/camera_image"
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
                "80dp"
            </span>
            <span class="hljs-attr">
                android:adjustViewBounds
            </span>
            =
            <span class="hljs-string">
                "true"
            </span>
            <span class="hljs-attr">
                android:scaleType
            </span>
            =
            <span class="hljs-string">
                "fitXY"
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
                "@+id/date"
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
                tools:text
            </span>
            =
            <span class="hljs-string">
                "10/07/2017"
            </span>
            /&gt;
        </span>
        <span class="hljs-tag">
            &lt;/
            <span class="hljs-name">
                LinearLayout
            </span>
            &gt;
        </span>
    </pre>
    <p>
        This has an
        <em>
            ImageView
        </em>
        for the mars photo and a
        <em>
            TextView
        </em>
        for the date of the image below it.
    </p>
    <h2>
        Data
    </h2>
    <p>
        You’ll be populating the
        <em>
            RecyclerView.Adapter
        </em>
        using data from the NASA site:
        <a href="https://api.nasa.gov/api.html#MarsPhotos" sl-processed="1">
            https://api.nasa.gov/api.html#MarsPhotos
        </a>
        .
    </p>
    <p>
        An easy way to test an API is to use the Postman Chrome extension or the Postman app (
        <a href="https://www.getpostman.com/" sl-processed="1">
            https://www.getpostman.com/
        </a>
        ). Once you’ve installed it, take the url
        <a href="https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&amp;api_key="
        sl-processed="
        1">
            https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&amp;api_key=
        </a>
        and add your key to the end.
    </p>
    <p>
        Hit the “Send” button in Postman and you’ll see the returned JSON in the
        Response section. Notice how it returns an object that has 1 item named
        photos, which is an array of objects. Now, you’ll create models to hold
        the data that comes back.
    </p>
    <p>
        In Android Studio, navigate to the
        <code>
            com.raywenderlich.marsrovers
        </code>
        package. Right click and select
        <em>
            New/Package
        </em>
        to create a new package named
        <code>
            models
        </code>
        .
    </p>
    <p>
        Next, right-click on the
        <code>
            models
        </code>
        package and select
        <em>
            New/Kotlin File/Class
        </em>
        . Name the file
        <code>
            Camera
        </code>
        , choose
        <em>
            Class
        </em>
        as the “Kind” and replace the generated code with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            data
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                Camera
            </span>
        </span>
        (
        <span class="hljs-keyword">
            val
        </span>
        id:
        <span class="hljs-built_in">
            Int
        </span>
        ,
        <span class="hljs-keyword">
            val
        </span>
        name: String,
        <span class="hljs-keyword">
            val
        </span>
        rover_id:
        <span class="hljs-built_in">
            Int
        </span>
        ,
        <span class="hljs-keyword">
            val
        </span>
        full_name: String)
    </pre>
    <p>
        Notice that you are using the
        <code>
            data
        </code>
        keyword to have Kotlin create the getters and setters for you, and that
        the class doesn’t need a beginning or ending brace as there are no methods.
        The field names match the names of the fields in the JSON response returned
        from the NASA API endpoint. You could make the names more readable, but
        you’d have to add some annotations to do that. For now, just use the given
        names.
    </p>
    <p>
        Next, right-click on the
        <code>
            models
        </code>
        package and create a new Kotlin class named
        <code>
            Photo
        </code>
        and replace with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            data
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                Photo
            </span>
        </span>
        (
        <span class="hljs-keyword">
            val
        </span>
        id :
        <span class="hljs-built_in">
            Int
        </span>
        ,
        <span class="hljs-keyword">
            val
        </span>
        img_src : String,
        <span class="hljs-keyword">
            val
        </span>
        earth_date: String,
        <span class="hljs-keyword">
            val
        </span>
        camera: Camera)
    </pre>
    <p>
        Create another Kotlin class named
        <code>
            PhotoList
        </code>
        . The
        <code>
            PhotoList
        </code>
        class just holds a list of photos and is the root element of the JSON
        data:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            data
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                PhotoList
            </span>
        </span>
        (
        <span class="hljs-keyword">
            val
        </span>
        photos: List&lt;Photo&gt;)
    </pre>
    <p>
        Finally, create a
        <code>
            PhotoRow
        </code>
        class that will be used to indicate that a row is either a photo or a
        header. This way, you can just have a list of
        <code>
            PhotoRow
        </code>
        objects and check which type to show based on the value of the
        <code>
            RowType
        </code>
        enum. Create a new Kotlin file called
        <code>
            PhotoRow
        </code>
        in the
        <code>
            models
        </code>
        package and add the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            enum
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                RowType
            </span>
        </span>
        { PHOTO, HEADER }
        <span class="hljs-keyword">
            data
        </span>
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                PhotoRow
            </span>
        </span>
        (
        <span class="hljs-keyword">
            var
        </span>
        type: RowType,
        <span class="hljs-keyword">
            var
        </span>
        photo: Photo?,
        <span class="hljs-keyword">
            var
        </span>
        header: String?)
    </pre>
    <p>
        The
        <code>
            type
        </code>
        property will distinguish between photos and headers. The row will have
        either a photo or a header string. Both the photo and header variables
        are nullable.
    </p>
    <h2>
        Adapter
    </h2>
    <p>
        Your adapter will extend the
        <em>
            RecyclerView.Adapter
        </em>
        class and use
        <em>
            DefaultViewHolder
        </em>
        . Navigate to the
        <em>
            com.raywenderlich.marsrovers.recyclerview
        </em>
        package and add a new Kotlin class called
        <em>
            PhotoAdapter
        </em>
        .
    </p>
    <p>
        The class will start out like so:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                PhotoAdapter
            </span>
        </span>
        (
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        photoList: ArrayList&lt;PhotoRow&gt;) : RecyclerView.Adapter&lt;DefaultViewHolder&gt;()
        {
    </pre>
    <p>
        Along with the passed in list of photos, create two more variables at
        the beginning of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        filteredPhotos = ArrayList&lt;PhotoRow&gt;()
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        filtering =
        <span class="hljs-literal">
            false
        </span>
    </pre>
    <p>
        The
        <code>
            filterPhotos
        </code>
        list is used to hold photos for a specific camera, and the
        <code>
            filtering
        </code>
        flag will be true when the user is filtering.
    </p>
    <p>
        There are three abstract methods of
        <em>
            RecyclerView.Adapter
        </em>
        that have to be implemented:
        <code>
            getItemCount
        </code>
        ,
        <code>
            onCreateViewHolder
        </code>
        , and
        <code>
            onBindViewHolder
        </code>
        . You will also override the
        <code>
            getItemViewType
        </code>
        method to return different values for the header and photo row type.
    </p>
    <p>
        <code>
            getItemCount
        </code>
        returns the number of photos available. If filtering is on, return the
        size from the filtered list:
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
        :
        <span class="hljs-built_in">
            Int
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (filtering) {
        <span class="hljs-keyword">
            return
        </span>
        filteredPhotos.size }
        <span class="hljs-keyword">
            return
        </span>
        photoList.size }
    </pre>
    <p>
        <code>
            onBindViewHolder
        </code>
        is where you load the photo or set the header text.
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
                <span class="hljs-type
                ">
                    DefaultViewHolder
                </span>
                , position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            val
        </span>
        photoRow : PhotoRow =
        <span class="hljs-keyword">
            if
        </span>
        (filtering) { filteredPhotos[position] }
        <span class="hljs-keyword">
            else
        </span>
        { photoList[position] }
        <span class="hljs-keyword">
            if
        </span>
        (photoRow.type == RowType.PHOTO) {
        <span class="hljs-keyword">
            val
        </span>
        photo = photoRow.photo Glide.with(holder.itemView.context) .load(photo?.img_src)
        .into(holder.getImage(R.id.camera_image)) photo?.earth_date?.let { holder.setText(R.id.date,
        it) } }
        <span class="hljs-keyword">
            else
        </span>
        { photoRow.header?.let { holder.setText(R.id.header_text, it) } } }
    </pre>
    <p>
        You can see that you’re using
        <a href="https://github.com/bumptech/glide" sl-processed="1">
            Glide
        </a>
        to load images into the
        <em>
            ImageView
        </em>
        . Glide seemed to work better for all of the Mars photos than
        <a href="http://square.github.io/picasso/" sl-processed="1">
            Picasso
        </a>
        , which was only able to load some of the images.
    </p>
    <p>
        <code>
            onCreateViewHolder
        </code>
        is where you inflate the layout and return the
        <em>
            ViewHolder
        </em>
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
                onCreateViewHolder
            </span>
            <span class="hljs-params">
                (parent:
                <span class="hljs-type
                ">
                    ViewGroup
                </span>
                , viewType:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        : DefaultViewHolder {
        <span class="hljs-keyword">
            val
        </span>
        layoutInflater = LayoutInflater.from(parent.context)
        <span class="hljs-keyword">
            val
        </span>
        inflatedView : View =
        <span class="hljs-keyword">
            when
        </span>
        (viewType) { RowType.PHOTO.ordinal -&gt; layoutInflater.inflate(R.layout.row_item,
        parent,
        <span class="hljs-literal">
            false
        </span>
        )
        <span class="hljs-keyword">
            else
        </span>
        -&gt; layoutInflater.inflate(R.layout.header_item, parent,
        <span class="hljs-literal">
            false
        </span>
        ) }
        <span class="hljs-keyword">
            return
        </span>
        DefaultViewHolder(inflatedView) }
    </pre>
    <p>
        For the two methods
        <code>
            onCreateViewHolder
        </code>
        and
        <code>
            onBindViewHolder
        </code>
        , you need to distinguish between a header and photo row. You can do that
        by checking the
        <em>
            PhotoRow
        </em>
        ’s type, as you’ll see in the next section.
    </p>
    <h2>
        Section Headers
    </h2>
    <p>
        To provide headers for rows, you just need to have different row types.
        This is done by letting the
        <em>
            RecyclerView
        </em>
        know what type to use for each row.
    </p>
    <p>
        Override the
        <code>
            getItemViewType
        </code>
        method and return a different integer for each type. You will be returning
        two different types, one for the header and one for the photo. You can
        use the ordinal of the enum (so the returned values will be 0 and 1). Add
        the following method after
        <code>
            onCreateViewHolder
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
                getItemViewType
            </span>
            <span class="hljs-params">
                (position:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        =
        <span class="hljs-keyword">
            if
        </span>
        (filtering) { filteredPhotos[position].type.ordinal }
        <span class="hljs-keyword">
            else
        </span>
        { photoList[position].type.ordinal }
    </pre>
    <p>
        Both
        <code>
            getItemCount
        </code>
        and
        <code>
            getItemViewType
        </code>
        need to take into account the filtering flags to use either the original
        <code>
            photoList
        </code>
        or the
        <code>
            filteredPhotos
        </code>
        list.
    </p>
    <p>
        In
        <code>
            onCreateViewHolder
        </code>
        , you load in a row_item layout for photos and a head_item layout for
        the header. The
        <code>
            onBindViewHolder
        </code>
        checks the type and binds the appropriate items to the
        <em>
            ViewHolder
        </em>
        .
    </p>
    <p>
        Now run the app to make sure it builds. Since you haven’t added the adapter
        to the
        <em>
            RecyclerView
        </em>
        yet, you won’t see anything quite yet, only the spinning ProgressBar.
    </p>
    <h2>
        DiffUtil
    </h2>
    <p>
        <em>
            DiffUtil
        </em>
        is a utility class from the
        <em>
            RecyclerView
        </em>
        support library used to calculate the difference between two lists and
        create the operations that will morph one list into another. It will be
        used by the
        <em>
            RecyclerView.Adapter
        </em>
        to trigger the optimal data change notifications that are used to animate
        the
        <em>
            RecyclerView
        </em>
        ‘s rows.
    </p>
    <p>
        To use this method, you need to implement the
        <em>
            DiffUtil.Callback
        </em>
        . Add this to the end of the
        <em>
            PhotoAdapter
        </em>
        class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                PhotoRowDiffCallback
            </span>
        </span>
        (
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        newRows : List&lt;PhotoRow&gt;,
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        oldRows : List&lt;PhotoRow&gt;) : DiffUtil.Callback() {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                areItemsTheSame
            </span>
            <span class="hljs-params">
                (oldItemPosition:
                <span class="hljs-type
                ">
                    Int
                </span>
                , newItemPosition:
                <span class="hljs-type">
                    Int
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
            val
        </span>
        oldRow = oldRows[oldItemPosition]
        <span class="hljs-keyword">
            val
        </span>
        newRow = newRows[newItemPosition]
        <span class="hljs-keyword">
            return
        </span>
        oldRow.type == newRow.type }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                getOldListSize
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Int
        </span>
        = oldRows.size
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                getNewListSize
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Int
        </span>
        = newRows.size
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                areContentsTheSame
            </span>
            <span class="hljs-params">
                (oldItemPosition:
                <span class="hljs-type
                ">
                    Int
                </span>
                , newItemPosition:
                <span class="hljs-type">
                    Int
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
            val
        </span>
        oldRow = oldRows[oldItemPosition]
        <span class="hljs-keyword">
            val
        </span>
        newRow = newRows[newItemPosition]
        <span class="hljs-keyword">
            return
        </span>
        oldRow == newRow } }
    </pre>
    <p>
        This class checks the items to see if they are the same type or have the
        same values. The
        <code>
            areItemsTheSame
        </code>
        method just checks the row type but the
        <code>
            areContentsTheSame
        </code>
        checks to see if the rows are equal.
    </p>
    <h3>
        Additional Methods
    </h3>
    <p>
        To update the photo list, you need to pass in a new list, calculate the
        difference between the two lists and clear the filter. Add the following
        methods after
        <code>
            getItemViewType
        </code>
        in
        <code>
            PhotoAdapter
        </code>
        to support clearing the filter list, use
        <em>
            DiffUtil
        </em>
        to tell the
        <em>
            Adapter
        </em>
        how to update the photo views, and remove rows:
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
                clearFilter
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        { filtering =
        <span class="hljs-literal">
            false
        </span>
        filteredPhotos.clear() }
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                updatePhotos
            </span>
            <span class="hljs-params">
                (photos :
                <span class="hljs-type">
                    ArrayList
                </span>
                &lt;
                <span class="hljs-type
                ">
                    PhotoRow
                </span>
                &gt;)
            </span>
        </span>
        { DiffUtil.calculateDiff(PhotoRowDiffCallback(photos, photoList),
        <span class="hljs-literal">
            false
        </span>
        ).dispatchUpdatesTo(
        <span class="hljs-keyword">
            this
        </span>
        ) photoList = photos clearFilter() }
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                removeRow
            </span>
            <span class="hljs-params">
                (row :
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (filtering) { filteredPhotos.removeAt(row) }
        <span class="hljs-keyword">
            else
        </span>
        { photoList.removeAt(row) } notifyItemRemoved(row) }
    </pre>
    <p>
        Notice the
        <code>
            notifyItemRemoved
        </code>
        method. That method will allow animations to occur for the rows around
        the deleted row because it tells
        <em>
            RecyclerView
        </em>
        exactly how the data in the adapter has changed. It’s best not to use
        <code>
            notifyDataSetChanged
        </code>
        for this case, as that does not provide
        <em>
            RecyclerView
        </em>
        with details about exactly what has changed.
    </p>
    <h2>
        Retrofit
    </h2>
    <p>
        To get the data from NASA, you’ll be using the
        <a href="http://square.github.io/retrofit/” sl-processed="1">
            Retrofit
        </a>
        and
        <a href="https://github.com/square/moshi” sl-processed="1">
            Moshi
        </a>
        libraries. You’ll use Retrofit for downloading the data and Moshi for
        converting it from JSON to our models.
    </p>
    <p>
        First, create a service interface. Create a new package named
        <em>
            service
        </em>
        and then right click to create a new Kotlin interface named
        <em>
            NasaApi
        </em>
        . Replace the code with the following:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                interface
            </span>
            <span class="hljs-title">
                NasaApi
            </span>
        </span>
        {
        <span class="hljs-meta">
            @GET(
            <span class="hljs-meta-string">
                "mars-photos/api/v1/rovers/{rover}/photos?sol=1000&amp;api_key=&lt;key&gt;"
            </span>
            )
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                getPhotos
            </span>
            <span class="hljs-params">
                (
                <span class="hljs-meta
                ">
                    @Path(
                    <span class="hljs-meta-string">
                        "rover"
                    </span>
                    )
                </span>
                rover:
                <span class="hljs-type">
                    String
                </span>
                )
            </span>
        </span>
        : Call&lt;PhotoList&gt; }
    </pre>
    <p>
        Substitute your key from the NASA site for
        <em>
            &lt;key&gt;
        </em>
        . This sets up the method to get the list of Photos. 
        The passed in rover string will be substitued for {rover}.
    </p>
    <p>
        If you need to add an import for
        <em>
            Call
        </em>
        , be sure to use the one from the
        <em>
            retrofit2
        </em>
        package.
    </p>
    <p>
        Next, you’ll need to create the actual service. Your service should be
        a Singleton and in Kotlin, creating one is extremely easy.
    </p>
    <p>
        Right click on the
        <em>
            service
        </em>
        package and select
        <em>
            New/Kotlin File/Class
        </em>
        , name it
        <em>
            NasaPhotos
        </em>
        , and change the
        <em>
            Kind
        </em>
        to
        <em>
            Object
        </em>
        . That’s it! You now have a Kotlin Singleton.
    </p>
    <p>
        Create a variable named
        <code>
            service
        </code>
        that is used in the
        <code>
            getPhotos
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            object
        </span>
        NasaPhotos {
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            val
        </span>
        service : NasaApi
    </pre>
    <p>
        And then add an
        <code>
            init
        </code>
        method. This will create the instance of Retrofit, set Moshi as the JSON
        converter, and finally create the
        <code>
            service
        </code>
        object:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        init {
        <span class="hljs-keyword">
            val
        </span>
        retrofit = Retrofit.Builder() .baseUrl(
        <span class="hljs-string">“https://api.nasa.gov/"
        </span>
        ) .addConverterFactory(MoshiConverterFactory.create()) .build() service
        = retrofit.create(NasaApi::
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
        }
    </pre>
    <p>
        Then, create a new method to make the call for the photos:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                getPhotos
            </span>
            <span class="hljs-params">
                (rover:
                <span class="hljs-type">
                    String
                </span>
                )
            </span>
        </span>
        : Call&lt;PhotoList&gt; = service.getPhotos(rover)
    </pre>
    <p>
        You’re almost there. You just need to setup the spinners and the
        <em>
            RecyclerView
        </em>
        adapter, which you’ll do next.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/showme-320x320.png” alt="" width="320" height="320" class="aligncenter size-medium wp-image-179016” srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/showme-320x320.png
        320w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-250x250.png
        250w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-500x500.png
        500w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-32x32.png
        32w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-50x50.png
        50w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-64x64.png
        64w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-96x96.png
        96w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme-128x128.png
        128w, https://koenig-media.raywenderlich.com/uploads/2017/12/showme.png
        1000w" sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <h2>
        Updating the main UI
    </h2>
    <p>
        It’s time to update
        <em>
            MainActivity
        </em>
        to setup the spinners and load some photos!
    </p>
    <p>
        Add a few variables to hold the current rover string and the spinner positions,
        at the top of
        <code>
            MainActivity
        </code>
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        currentRover =
        <span class="hljs-string">“curiosity"
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        currentRoverPosition =
        <span class="hljs-number">
            0
        </span>
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-keyword">
            var
        </span>
        currentCameraPosition =
        <span class="hljs-number">
            0
        </span>
    </pre>
    <p>
        Above the
        <em>
            MainActivity
        </em>
        class declaration add:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            private
        </span>
        const
        <span class="hljs-keyword">
            val
        </span>
        TAG =
        <span class="hljs-string">“MarsRover"
        </span>
    </pre>
    <p>
        The
        <code>
            TAG
        </code>
        will be used for logging errors.
    </p>
    <p>
        Add the following below the
        <code>
            onCreate
        </code>
        method:
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
                setupSpinners
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        { setupRoverSpinner() setupCameraSpinner() }
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                setupCameraSpinner
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            // Camera spinner
        </span>
        <span class="hljs-keyword">
            val
        </span>
        cameraStrings = resources.getStringArray(R.array.camera_values)
        <span class="hljs-keyword">
            val
        </span>
        cameraAdapter = ArrayAdapter.createFromResource(
        <span class="hljs-keyword">
            this
        </span>
        , R.array.camera_names, android.R.layout.simple_spinner_item) cameraAdapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
        cameras.adapter = cameraAdapter cameras.onItemSelectedListener =
        <span class="hljs-keyword">
            object
        </span>
        : AdapterView.OnItemSelectedListener {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onNothingSelected
            </span>
            <span class="hljs-params">
                (parent:
                <span class="hljs-type">
                    AdapterView
                </span>
                &lt;*&gt;)
            </span>
        </span>
        { }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onItemSelected
            </span>
            <span class="hljs-params">
                (parent:
                <span class="hljs-type
                ">
                    AdapterView
                </span>
                &lt;*&gt;, view:
                <span class="hljs-type">
                    View
                </span>
                , position:
                <span class="hljs-type
                ">
                    Int
                </span>
                , id:
                <span class="hljs-type">
                    Long
                </span>
                )
            </span>
        </span>
        { currentCameraPosition = position } } }
        <span class="hljs-keyword">
            private
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                setupRoverSpinner
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        {
        <span class="hljs-comment">
            // Setup the spinners for selecting different rovers and cameras
        </span>
        <span class="hljs-keyword">
            val
        </span>
        roverStrings = resources.getStringArray(R.array.rovers)
        <span class="hljs-keyword">
            val
        </span>
        adapter = ArrayAdapter.createFromResource(
        <span class="hljs-keyword">
            this
        </span>
        , R.array.rovers, android.R.layout.simple_spinner_item) adapter.setDropDownViewResource(android.R.layout.simple_spinner_dropdown_item)
        rovers.adapter = adapter rovers.onItemSelectedListener =
        <span class="hljs-keyword">
            object
        </span>
        : AdapterView.OnItemSelectedListener {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onNothingSelected
            </span>
            <span class="hljs-params">
                (parent:
                <span class="hljs-type">
                    AdapterView
                </span>
                &lt;*&gt;)
            </span>
        </span>
        { }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onItemSelected
            </span>
            <span class="hljs-params">
                (parent:
                <span class="hljs-type
                ">
                    AdapterView
                </span>
                &lt;*&gt;, view:
                <span class="hljs-type">
                    View
                </span>
                , position:
                <span class="hljs-type
                ">
                    Int
                </span>
                , id:
                <span class="hljs-type">
                    Long
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (currentRoverPosition != position) { currentRover = roverStrings[position].toLowerCase()
        loadPhotos() } currentRoverPosition = position } } }
    </pre>
    <p>
        These setup the spinners to hold the corresponding string arrays.
    </p>
    <p>
        At the end of the
        <code>
            onCreate
        </code>
        method, add the following two lines that will setup the spinners and load
        the photos:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setupSpinners() loadPhotos()
    </pre>
    <p>
        Next, you’ll load and sort our photos. Add the following after
        <code>
            setupRoverSpinner
        </code>
        in the
        <code>
            MainActivity
        </code>
        :
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
                loadPhotos
            </span>
            <span class="hljs-params">
                ()
            </span>
        </span>
        { progress.visibility = View.VISIBLE recycler_view.visibility = View.GONE
        NasaPhotos.getPhotos(currentRover).enqueue(
        <span class="hljs-keyword">
            object
        </span>
        : Callback&lt;PhotoList&gt; {
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onFailure
            </span>
            <span class="hljs-params">
                (call:
                <span class="hljs-type
                ">
                    Call
                </span>
                &lt;
                <span class="hljs-type">
                    PhotoList
                </span>
                &gt;?, t:
                <span class="hljs-type">
                    Throwable
                </span>
                ?)
            </span>
        </span>
        { Snackbar.make(recycler_view, R.string.api_error, Snackbar.LENGTH_LONG)
        Log.e(TAG,
        <span class="hljs-string">“Problems getting Photos with error:
            <span class="hljs-variable">
                $t
            </span>
            .msg"
        </span>
        ) }
        <span class="hljs-keyword">
            override
        </span>
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                onResponse
            </span>
            <span class="hljs-params">
                (call:
                <span class="hljs-type">
                    Call
                </span>
                &lt;
                <span class="hljs-type">
                    PhotoList
                </span>
                &gt;?, response:
                <span class="hljs-type">
                    Response
                </span>
                &lt;
                <span class="hljs-type">
                    PhotoList
                </span>
                &gt;?)
            </span>
        </span>
        { response?.let { photoResponse -&gt;
        <span class="hljs-keyword">
            if
        </span>
        (photoResponse.isSuccessful) {
        <span class="hljs-keyword">
            val
        </span>
        body = photoResponse.body() body?.let { Log.d(TAG,
        <span class="hljs-string">“Received
            <span class="hljs-subst">
                ${body.photos.size}
            </span>
            photos"
        </span>
        )
        <span class="hljs-keyword">
            if
        </span>
        (recycler_view.adapter ==
        <span class="hljs-literal">
            null
        </span>
        ) {
        <span class="hljs-keyword">
            val
        </span>
        adapter = PhotoAdapter(sortPhotos(body)) recycler_view.adapter = adapter
        }
        <span class="hljs-keyword">
            else
        </span>
        { (recycler_view.adapter
        <span class="hljs-keyword">
            as
        </span>
        PhotoAdapter).updatePhotos(sortPhotos(body)) } } recycler_view.scrollToPosition(
        <span class="hljs-number">
            0
        </span>
        ) recycler_view.visibility = View.VISIBLE progress.visibility = View.GONE
        } } } }) }
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                sortPhotos
            </span>
            <span class="hljs-params">
                (photoList:
                <span class="hljs-type">
                    PhotoList
                </span>
                )
            </span>
        </span>
        : ArrayList&lt;PhotoRow&gt; {
        <span class="hljs-keyword">
            val
        </span>
        map = HashMap&lt;String, ArrayList&lt;Photo&gt;&gt;()
        <span class="hljs-keyword">
            for
        </span>
        (photo
        <span class="hljs-keyword">
            in
        </span>
        photoList.photos) {
        <span class="hljs-keyword">
            var
        </span>
        photos = map[photo.camera.full_name]
        <span class="hljs-keyword">
            if
        </span>
        (photos ==
        <span class="hljs-literal">
            null
        </span>
        ) { photos = ArrayList() map[photo.camera.full_name] = photos } photos.add(photo)
        }
        <span class="hljs-keyword">
            val
        </span>
        newPhotos = ArrayList&lt;PhotoRow&gt;()
        <span class="hljs-keyword">
            for
        </span>
        ((key, value)
        <span class="hljs-keyword">
            in
        </span>
        map) { newPhotos.add(PhotoRow(RowType.HEADER,
        <span class="hljs-literal">
            null
        </span>
        , key)) value.mapTo(newPhotos) { PhotoRow(RowType.PHOTO, it,
        <span class="hljs-literal">
            null
        </span>
        ) } }
        <span class="hljs-keyword">
            return
        </span>
        newPhotos }
    </pre>
    <p>
        You’ll have to import a few classes to get rid of the errors. Note that
        any of the imports that provide multiple options should use the ones in
        the
        <em>
            retrofit2
        </em>
        package.
    </p>
    <p>
        In the
        <code>
            sortPhotos
        </code>
        method, you put the photos into sections arranged by camera.
    </p>
    <p>
        Now it’s time to try it out. Build and run the app, and within about 10
        or 20 seconds, you should see something like:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png"
        alt="mars rover screenshot" width="281" height="500" class="aligncenter size-large wp-image-173107"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/10/Screenshot_1507091574.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        If you don’t see any images, make sure you have your personal key in the
        Retrofit @GET annotation.
    </p>
    <p>
        You can choose different rovers from the spinner in the top right and
        different cameras from the spinner below the rover spinner but they won’t
        do anything until they are hooked up. Note also that not all rovers have
        images from all cameras.
    </p>
    <h2>
        Filtering
    </h2>
    <p>
        In order to filter the list, add the
        <em>
            filterCamera
        </em>
        method to
        <em>
            PhotoAdapter
        </em>
        below
        <code>
            getItemViewType
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-function">
            <span class="hljs-keyword">
                fun
            </span>
            <span class="hljs-title">
                filterCamera
            </span>
            <span class="hljs-params">
                (camera:
                <span class="hljs-type">
                    String
                </span>
                )
            </span>
        </span>
        { filtering =
        <span class="hljs-literal">
            true
        </span>
        <span class="hljs-keyword">
            val
        </span>
        newPhotos = photoList.filter { photo -&gt; photo.type == RowType.PHOTO
        &amp;&amp; photo.photo?.camera?.name.equals(camera) }
        <span class="hljs-keyword">
            as
        </span>
        ArrayList&lt;PhotoRow&gt; DiffUtil.calculateDiff(PhotoRowDiffCallback(newPhotos,
        photoList),
        <span class="hljs-literal">
            false
        </span>
        ).dispatchUpdatesTo(
        <span class="hljs-keyword">
            this
        </span>
        ) filteredPhotos = newPhotos }
    </pre>
    <p>
        Now go back to your
        <em>
            MainActivity
        </em>
        and hook up the camera filtering. Add the following code to the beginning
        of the
        <code>
            OnItemSelectedListener.onItemSelected()
        </code>
        in the
        <code>
            setupCameraSpinner
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            if
        </span>
        (recycler_view.adapter !=
        <span class="hljs-literal">
            null
        </span>
        &amp;&amp; currentCameraPosition != position) { (recycler_view.adapter
        <span class="hljs-keyword">
            as
        </span>
        PhotoAdapter).filterCamera(cameraStrings[position]) }
    </pre>
    <p>
        You pass in the camera string to filter on and create a new list with
        just those photos. You use Kotlin’s
        <code>
            filter
        </code>
        function on the collection and return a list of photos and has the given
        camera value.
    </p>
    <p>
        Now run the app and choose Opportunity as the new rover and you should
        see something like:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity.png"
        sl-processed="1">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-179008"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/12/opportunity.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <h2>
        ItemDecorators
    </h2>
    <p>
        Unlike
        <em>
            ListView
        </em>
        ,
        <em>
            RecyclerView
        </em>
        does not come with any built-in dividers. Instead,
        <em>
            RecyclerView
        </em>
        allows you to add your own decorators.
    </p>
    <p>
        The
        <em>
            RecyclerView
        </em>
        library comes with a
        <em>
            DividerItemDecoration
        </em>
        that can be used to put dividers between your rows. You can add a divider
        with this one line, which you should add to
        <code>
            onCreate()
        </code>
        in
        <code>
            MainActivity
        </code>
        after the line:
        <code>
            recycler_view.visibility = View.GONE
        </code>
        :
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        recycler_view.addItemDecoration(DividerItemDecoration(
        <span class="hljs-keyword">
            this
        </span>
        , DividerItemDecoration.VERTICAL))
    </pre>
    <p>
        You can see the divider after the photo date on the last photo in a section.
    </p>
    <p>
        To create your own decorator, just subclass
        <em>
            ItemDecoration
        </em>
        and implement the
        <code>
            onDraw
        </code>
        and/or the
        <code>
            onDrawOver
        </code>
        methods.
    </p>
    <h2>
        Animations
    </h2>
    <p>
        <em>
            RecyclerView
        </em>
        s allow animations for each row and provides built-in animations for adding
        and removing rows.
    </p>
    <p>
        To show an animation for adding a row, make sure you use
        <code>
            notifyItemAdded(position)
        </code>
        instead of calling
        <code>
            notifyDataChanged()
        </code>
        . This lets the view know that just one row has been added and can animate
        that addition.
    </p>
    <p>
        For deleting, call
        <code>
            notifyItemRemoved(position)
        </code>
        .
    </p>
    <p>
        To animate the addition of each item, add the following method to
        <em>
            PhotoAdapter
        </em>
        :
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
                setAnimation
            </span>
            <span class="hljs-params">
                (viewToAnimate:
                <span class="hljs-type">
                    View
                </span>
                )
            </span>
        </span>
        {
        <span class="hljs-keyword">
            if
        </span>
        (viewToAnimate.animation ==
        <span class="hljs-literal">
            null
        </span>
        ) {
        <span class="hljs-keyword">
            val
        </span>
        animation = AnimationUtils.loadAnimation(viewToAnimate.context, android.R.anim.slide_in_left)
        viewToAnimate.animation = animation } }
    </pre>
    <p>
        This will provide an animation where the row slides in from the left.
    </p>
    <p>
        Then add:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        setAnimation(holder.itemView)
    </pre>
    <p>
        as the last line in
        <code>
            onBindViewHolder
        </code>
        . Now try running again.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/mars4.gif"
        alt="mars rover screenshot" width="238" height="500" class="aligncenter size-large wp-image-173282">
    </p>
    <p>
        The animation adds a nice dynamic effect to the presentation of the photos.
    </p>
    <h2>
        Swiping
    </h2>
    <p>
        Swiping is great way to let your user delete rows. You’re going to implement
        swiping in both the left and right direction to delete a row.
    </p>
    <p>
        <em>
            RecyclerView
        </em>
        uses an
        <em>
            ItemTouchHelper
        </em>
        class along with a swipe callback to handle the movement. The callback
        is simple and you will just call your adapter’s
        <code>
            removeRow
        </code>
        method in the
        <code>
            onSwiped
        </code>
        callback.
    </p>
    <p>
        Open
        <em>
            MainActivity.kt
        </em>
        and add the following at the bottom of the class:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-class">
            <span class="hljs-keyword">
                class
            </span>
            <span class="hljs-title">
                SwipeHandler
            </span>
        </span>
        (
        <span class="hljs-keyword">
            val
        </span>
        adapter: PhotoAdapter, dragDirs :
        <span class="hljs-built_in">
            Int
        </span>
        , swipeDirs :
        <span class="hljs-built_in">
            Int
        </span>
        ) : ItemTouchHelper.SimpleCallback(dragDirs, swipeDirs) {
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
                ?, viewHolder:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                ?, target:
                <span class="hljs-type">
                    RecyclerView
                </span>
                .
                <span class="hljs-type">
                    ViewHolder
                </span>
                ?)
            </span>
        </span>
        :
        <span class="hljs-built_in">
            Boolean
        </span>
        {
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
                , direction:
                <span class="hljs-type">
                    Int
                </span>
                )
            </span>
        </span>
        { adapter.removeRow(viewHolder.adapterPosition) } }
    </pre>
    <p>
        In
        <code>
            loadPhotos
        </code>
        you will find the following in the
        <code>
            onResponse
        </code>
        method:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            if
        </span>
        (recycler_view.adapter ==
        <span class="hljs-literal">
            null
        </span>
        ) {
        <span class="hljs-keyword">
            val
        </span>
        adapter = PhotoAdapter(sortPhotos(body)) recycler_view.adapter = adapter
    </pre>
    <p>
        Add the following after setting the
        <code>
            adapter
        </code>
        value:
    </p>
    <pre lang="kotlin" class="language-kotlin hljs">
        <span class="hljs-keyword">
            val
        </span>
        touchHandler = ItemTouchHelper(SwipeHandler(adapter,
        <span class="hljs-number">
            0
        </span>
        , (ItemTouchHelper.LEFT or ItemTouchHelper.RIGHT))) touchHandler.attachToRecyclerView(recycler_view)
    </pre>
    <p>
        Run the app and try swiping left or right to delete a row.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/mars5.gif"
        alt="mars rover final screenshot" width="238" height="500" class="aligncenter size-large wp-image-173286">
    </p>
    <p>
        Awesome! You’re just deleting the row from the display in the
        <em>
            RecyclerView
        </em>
        . In another app you would likely delete the item from a database and/or
        make an API call to delete the corresponding item on a server.
    </p>
    <h2>
        Where to go from here
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
        You’ve done a lot of work and now you know how to add animations, provide
        a swipe handler, add section headers, and use the
        <em>
            DiffUtil
        </em>
        class. Well done!
    </p>
    <p>
        A great next step would be to eliminate the
        <em>
            PhotoRow
        </em>
        model class and
        <em>
            DefaultViewHolder
        </em>
        and get the project working with separate Header and Photo model objects and a dedicated
        <em>
            ViewHolder
        </em>
        for each.
    </p>
    <p>
        The final project for this tutorial is available
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/12/marsrovers-final-1.zip"
        sl-processed="1">
            here
        </a>
        . In the final project, be sure to remember to set the API key in
        <em>
            NasaApi.kt
        </em>
        .
    </p>
    <p>
        If you need more information on
        <em>
            RecyclerView
        </em>
        s, you can check out the following Android developer documentation:
    </p>
    <ul>
        <li>
            <a href="https://developer.android.com/guide/topics/ui/layout/recyclerview.html"
            sl-processed="1">
                Recyclerview Layouts
            </a>
        </li>
        <li>
            <a href="https://developer.android.com/reference/android/support/v7/widget/RecyclerView.html"
            sl-processed="1">
                RecyclerView Class
            </a>
        </li>
        <li>
            <a href="https://developer.android.com/reference/android/support/v7/util/DiffUtil.html"
            sl-processed="1">
                DiffUtil Class
            </a>
        </li>
    </ul>
    <p>
        Go forward and make great animated
        <em>
            RecyclerView
        </em>
        s!
    </p>
</div>

