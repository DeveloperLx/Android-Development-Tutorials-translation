# Android动画教程 - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/173345/android-animation-tutorial-with-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <div class="note">
        <em>
            Update note
        </em>
        : This tutorial has been updated to Kotlin and Android Studio 3.0 by Lisa
        Luo. The original tutorial was written by Artem Kholodnyi.
    </div>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-250x250.png"
        alt="Android animation" width="250" height="250" class="alignright size-thumbnail wp-image-141919"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature.png 500w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/09/IntroToAnimation-feature-128x128.png 128w"
        sizes="(max-width: 250px) 100vw, 250px">
    </p>
    <p>
        It’s hard to imagine the mobile experience without animated elements–they’re
        fun, beautiful and hold the power of not only guiding users gracefully
        through an app, but also bringing screens to life.
    </p>
    <p>
        Building animations that make on-screen objects seem alive may look like
        aerospace engineering at first, but fear not! Android has quite a few tools
        to help you create animations with relative ease.
    </p>
    <p>
        You’ll learn to get comfortable with some essential animation tools in
        this tutorial as you work through launching Doge on a rocket into space
        (maybe even to the moon) and hopefully get it back safely on the ground
        :]
    </p>
    <p>
        By creating these Doge animations, you’ll learn how to:
    </p>
    <ul>
        <li>
            Create
            <em>
                property animations
            </em>
            — the most useful and simple Android animations
        </li>
        <li>
            Move and fade Android Views
        </li>
        <li>
            Combine animations in a sequence or start them simultaneously
        </li>
        <li>
            Repeat and reverse animations
        </li>
        <li>
            Adjust the animations’ timing
        </li>
        <li>
            Become a bit of a rocket scientist. :]
        </li>
    </ul>
    <div class="note">
        <p>
            <em>
                Prerequisites
            </em>
            : This Android tutorial is all about animation, so you need basic knowledge
            of Android programming and familiarity with Kotlin, Android Studio and
            XML layouts.
        </p>
        <p>
            If you’re completely new to Android, you might want to first check out
            <a href="https://www.raywenderlich.com/161318/beginning-android-development-part-one-installing-android-studio"
            target="_blank" title="Android Tutorial for Beginners: Part 1">
                Beginning Android Development Part One
            </a>
            .
        </p>
    </div>
    <p>
        Many animation. Such code. Fast rocket.
    </p>
    <h2>
        Getting Started
    </h2>
    <p>
        Animations are such a fun topic to explore! The best way to master building
        animations is by getting your hands dirty in code. :]
    </p>
    <p>
        First, download the
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/10/rocket_launcher-starter-1.zip">
            Rocket Launcher Starter
        </a>
        . Import it into Android Studio 3.0 Beta 7 or later, then run it on your
        device. You’ll find everything you need to get going quickly.
    </p>
    <p>
        Your device will display a list of all the animations you’ll implement.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/list.png"
        alt="list" width="300" height="500" class="aligncenter size-full wp-image-128166"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/03/list.png 300w, https://koenig-media.raywenderlich.com/uploads/2016/03/list-192x320.png 192w"
        sizes="(max-width: 300px) 100vw, 300px">
    </p>
    <p>
        Click any item on the list.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket-281x500.png"
        alt="doge_rocket" width="281" height="500" class="aligncenter size-large wp-image-136020"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2016/05/doge_rocket.png 1080w"
        sizes="(max-width: 281px) 100vw, 281px">
    </p>
    <p>
        You should see two static images: Doge and the rocket, and Doge is ready
        to take a ride. For now, all the screens are the same and none are yet
        animated.
    </p>
    <h2>
        How do Property Animations Work?
    </h2>
    <p>
        Before you work with the first animation, let’s take a walk down theory
        road so that you’re clear on the logic behind the magic. :]
    </p>
    <p>
        Imagine that you need to animate a rocket launch from the bottom edge
        to the top edge of the screen and that the rocket should make it exactly
        in 50 ms.
    </p>
    <p>
        Here’s a plotted graph that shows how the rocket’s position changes over
        time:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/linear-interpolator.gif"
        alt="linear-interpolator" width="272" height="400" class="aligncenter size-full wp-image-128117">
    </p>
    <p>
        The animation above appears to be smooth and continuous. However, smartphones
        are digital and work with discrete values. Time does not flow continuously
        for them; it advances by tiny steps.
    </p>
    <p>
        Animation consists of many still images, also known as
        <em>
            frames
        </em>
        , that are displayed one by one over a specified time period. The concept
        today is the same as it was for the first cartoons, but the rendering is
        a little different.
    </p>
    <p>
        Elapsed time between frames is named
        <em>
            frame refresh delay
        </em>
        — it’s 10 ms by default for property animations.
    </p>
    <p>
        Here’s where animation is different than it was in the early days of film:
        when you know the rocket moves at a constant speed, you can calculate the
        position of the rocket at any given time.
    </p>
    <p>
        You see six animation frames shown below. Notice that:
    </p>
    <ul>
        <li>
            In the beginning of the animation, the rocket is at the bottom edge of
            the screen.
        </li>
        <li>
            The rocket’s position moves upward by the same fraction of its path with
            every frame.
        </li>
        <li>
            By the end of the animation, the rocket is at the top edge of the screen.
        </li>
    </ul>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/frames.png"
        alt="frames" width="405" height="405" class="aligncenter size-full wp-image-134485"
        srcset="https://koenig-media.raywenderlich.com/uploads/2016/05/frames.png 405w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2016/05/frames-128x128.png 128w"
        sizes="(max-width: 405px) 100vw, 405px">
    </p>
    <p>
        TL/DR: When drawing a given frame, you calculate the rocket’s position
        based on the duration and frame refresh rate.
    </p>
    <p>
        Fortunately, you don’t have to do all the calculations manually because
        <code>
            ValueAnimator
        </code>
        is happy to do it for you. :]
    </p>
    <p>
        To set up an animation, you simply specify the start and end values of
        the property being animated, as well as the duration. You’ll also need
        to add a listener to call, which will set a new position for your rocket
        for each frame.
    </p>
    <h3>
        Time Interpolators
    </h3>
    <p>
        You probably noticed that your rocket moves with constant speed during
        the entire animation — not terribly realistic.
        <a href="https://material.io/">
            Material Design
        </a>
        encourages you to create vivid animations that catch the user’s attention
        while behaving in a more natural way.
    </p>
    <p>
        Android’s animation framework makes use of
        <em>
            time interpolators
        </em>
        .
        <code>
            ValueAnimator
        </code>
        incorporates a time interpolator – it has an object that implements
        <code>
            TimeInterpolator
        </code>
        interface. Time interpolators determine how the animated value changes
        over time.
    </p>
    <p>
        Have a look again at the graph of position changes over time in the simplest
        case — a
        <em>
            Linear Interpolator
        </em>
        :
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/linear-interpolator.gif"
        alt="linear-interpolator" width="272" height="400" class="aligncenter size-full wp-image-128117">
    </p>
    <p>
        Here is how this
        <code>
            LinearInterpolator
        </code>
        responds to time change:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/table_linear.png"
        alt="table_linear" width="175" height="250" class="aligncenter size-full wp-image-134326">
    </p>
    <p>
        Depending on the time, the rocket position changes at a constant speed,
        or
        <i>
            linearly
        </i>
        .
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/03/accelerate-interpolator.gif"
        alt="AccelerateInterpolator" width="273" height="400" class="aligncenter size-full wp-image-128128">
    </p>
    <p>
        Animations can also have non-linear interpolators. One such example is
        the
        <code>
            AccelerateInterpolator
        </code>
        , which looks much more interesting:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/table_acc.png"
        alt="table_acc" width="175" height="316" class="aligncenter size-full wp-image-134327">
    </p>
    <p>
        It squares the input value, making the rocket start slowly and accelerate
        quickly — just like a real rocket does!
    </p>
    <p>
        That’s pretty much all the theory you need to know to get started, so
        now it’s time for…
    </p>
    <h2>
        Your First Animation
    </h2>
    <p>
        Take some time to familiarize yourself with the project before you move
        on. The package
        <code>
            com.raywenderlich.rocketlauncher.animationactivities
        </code>
        contains
        <em>
            BaseAnimationActivity
        </em>
        and all other activities that extend this class.
    </p>
    <p>
        Open
        <em>
            activity_base_animation.xml
        </em>
        file in the
        <em>
            res/layout
        </em>
        folder.
    </p>
    <p>
        In the root, you’ll find a
        <code>
            FrameLayout
        </code>
        that contains two instances of
        <code>
            ImageView
        </code>
        with images: one has
        <em>
            rocket.png
        </em>
        and the other has
        <em>
            doge.png
        </em>
        . Both have
        <code>
            android:layout_gravity
        </code>
        set to
        <code>
            bottom|center_horizontal
        </code>
        to render the images at the bottom-center of the screen.
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : You’ll do a lot of file navigation in this tutorial. Use these handy
            shortcuts in Android Studio to move between things easily:
        </p>
        <ul>
            <li>
                <p>
                    Navigate to any file with
                    <em>
                        command + shift + O
                    </em>
                    on Mac /
                    <em>
                        Ctrl + Shift + N
                    </em>
                    on Linux and Windows
                </p>
            </li>
            <li>
                <p>
                    Navigate to a Kotlin class with
                    <em>
                        command + O
                    </em>
                    on Mac /
                    <em>
                        Ctrl + N
                    </em>
                    on Linux and Windows
                </p>
            </li>
        </ul>
    </div>
    <p>
        <code>
            BaseAnimationActivity
        </code>
        is a super class of all other animation activities in this app.
    </p>
    <p>
        Open
        <em>
            BaseAnimationActivity.kt
        </em>
        and have a look inside. At the top are
        <code>
            View
        </code>
        member variables that are accessible from all animation activities:
    </p>
    <ul>
        <li>
            <code>
                rocket
            </code>
            is the view with the image of the rocket
        </li>
        <li>
            <code>
                doge
            </code>
            is the view that contains the Doge image
        </li>
        <li>
            <code>
                frameLayout
            </code>
            is the FrameLayout that contains both
            <code>
                rocket
            </code>
            and
            <code>
                doge
            </code>
        </li>
        <li>
            <code>
                screenHeight
            </code>
            will equal the screen height for the sake of convenience
        </li>
    </ul>
    <p>
        Note that
        <code>
            rocket
        </code>
        and
        <code>
            doge
        </code>
        are both a type of
        <code>
            ImageView
        </code>
        , but you declare each as a
        <code>
            View
        </code>
        since property animations work with all Android Views. Views are also
        declared as
        <code>
            lateinit
        </code>
        values since they are null until the layout is inflated and bound in the
        appropriate lifecycle event, e.g.
        <code>
            onCreate()
        </code>
        in an Activity.
    </p>
    <p>
        Take a look at
        <code>
            onCreate()
        </code>
        to observe the code:
    </p>
    <pre lang="kotlin">
        // 1 super.onCreate(savedInstanceState) setContentView(R.layout.activity_base_animation)
        // 2 rocket = findViewById(R.id.rocket) doge = findViewById(R.id.doge)
        frameLayout = findViewById(R.id.container) // 3 frameLayout.setOnClickListener
        { onStartAnimation() }
    </pre>
    <p>
        Here is what you’ve got going on with this code:
    </p>
    <ol>
        <li>
            Call
            <code>
                onCreate()
            </code>
            on the superclass and then
            <code>
                setContentView(...)
            </code>
            with the layout file.
        </li>
        <li>
            Apply XML layout and bind
            <code>
                FrameLayout
            </code>
            ,
            <code>
                rocket
            </code>
            and
            <code>
                doge
            </code>
            to their corresponding views
        </li>
        <li>
            Set
            <code>
                onClickListener
            </code>
            on
            <code>
                FrameLayout
            </code>
            .
        </li>
        <li>
            Call
            <code>
                onStartAnimation()
            </code>
            whenever the user taps the screen. This is an abstract method defined
            by each of the activities that extend
            <code>
                BaseAnimationActivity
            </code>
            .
        </li>
    </ol>
    <p>
        This basic code is shared by all of the Activities you will be editing
        in this tutorial. Now that you’re familiar with it, it’s time to start
        customizing!
    </p>
    <h3>
        Launch the Rocket
    </h3>
    <p>
        Doge isn’t going anywhere unless you initiate the rocket launch, and it’s
        the best animation to start with because it’s pretty easy. Who’d have thought
        that rocket science is so simple?
    </p>
    <p>
        Open
        <em>
            LaunchRocketValueAnimatorAnimationActivity.kt
        </em>
        , and add the following code to the body of
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        //1 val valueAnimator = ValueAnimator.ofFloat(0f, -screenHeight) //2 valueAnimator.addUpdateListener
        { val value = it.animatedValue as Float rocket.translationY = value } //5
        valueAnimator.interpolator = LinearInterpolator() valueAnimator.duration
        = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION //6 valueAnimator.start()
    </pre>
    <ol>
        <li>
            Create an instance of
            <code>
                ValueAnimator
            </code>
            by calling the static method
            <code>
                ofFloat
            </code>
            . It accepts the floating point numbers that’ll apply to the specified
            property of the animated object over time. In this case, the values start
            at
            <code>
                0f
            </code>
            and end with
            <code>
                -screenHeight
            </code>
            . Android starts screen coordinates at the top-left corner, so the rocket’s
            Y translation changes from 0 to the negative of the screen height — it
            moves bottom to top.
        </li>
        <li>
            Call
            <code>
                addUpdateListener()
            </code>
            and pass in a listener.
            <code>
                ValueAnimator
            </code>
            calls this listener with every update to the animated value — remember
            the default delay of 10 ms.
        </li>
        <li>
            Get the current value from the animator and cast it to float; current
            value type is
            <code>
                float
            </code>
            because you created the
            <code>
                ValueAnimator
            </code>
            with
            <code>
                ofFloat
            </code>
            .
        </li>
        <li>
            Change the rocket’s position by setting its
            <code>
                translationY
            </code>
            value
        </li>
        <li>
            Set up the animator’s duration and interpolator.
        </li>
        <li>
            Start the animation.
        </li>
    </ol>
    <p>
        Build and run. Select
        <em>
            Launch a Rocket
        </em>
        in the list. You’ll get a new screen. Tap it!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/linear-launch.gif"
        alt="linear-launch" width="272" height="484" class="aligncenter size-full wp-image-134552">
    </p>
    <p>
        That was fun, right? :] Don’t worry about Doge getting left behind — he’ll
        catch his rocketship to the moon a bit later.
    </p>
    <h3>
        Put a Spin on It
    </h3>
    <p>
        How about giving the rocket a little spin action? Open
        <em>
            RotateRocketAnimationActivity.kt
        </em>
        and add the following to
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        // 1 val valueAnimator = ValueAnimator.ofFloat(0f, 360f) valueAnimator.addUpdateListener
        { val value = it.animatedValue as Float // 2 rocket.rotation = value }
        valueAnimator.interpolator = LinearInterpolator() valueAnimator.duration
        = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION valueAnimator.start()
    </pre>
    <p>
        Can you spot the difference?
    </p>
    <ol>
        <li>
            Changing the
            <code>
                valueAnimator
            </code>
            values to go from
            <code>
                0f
            </code>
            to
            <code>
                360f
            </code>
            causes the rocket to make a full turn. Note that you could create a U-turn
            effect with
            <code>
                0f
            </code>
            to
            <code>
                180f
            </code>
            .
        </li>
        <li>
            Instead of setting
            <code>
                translationY
            </code>
            , you set the rocket’s
            <code>
                rotation
            </code>
            because that’s what needs to change.
        </li>
    </ol>
    <p>
        Build, run and select
        <em>
            Spin a rocket
        </em>
        . Tap on the new screen:
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/spin.gif"
        alt="" width="283" height="500" class="aligncenter size-large wp-image-173336">
    </p>
    <h3>
        Accelerate the Launch
    </h3>
    <p>
        Open
        <em>
            AccelerateRocketAnimationActivity.kt
        </em>
        and add the following code to your old friend
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        // 1 val valueAnimator = ValueAnimator.ofFloat(0f, -screenHeight) valueAnimator.addUpdateListener
        { val value = it.animatedValue as Float rocket.translationY = value } //
        2 - Here set your favorite interpolator valueAnimator.interpolator = AccelerateInterpolator(1.5f)
        valueAnimator.duration = BaseAnimationActivity.DEFAULT_ANIMATION_DURATION
        // 3 valueAnimator.start()
    </pre>
    <p>
        The above code is identical to
        <code>
            onStartAnimation()
        </code>
        in
        <em>
            LaunchRocketValueAnimationActivity.kt
        </em>
        except for one line: the interpolator used to set
        <code>
            valueAnimator.interpolator
        </code>
        .
    </p>
    <p>
        Build, run and select
        <em>
            Accelerate a rocket
        </em>
        in the list. Tap on the new screen to see how your rocket behaves.
    </p>
    <p>
        Again, we see that poor Doge doesn’t catch the rocket to the moon…poor
        fella. Hang in there, buddy!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/accelerate.gif"
        alt="accelerate" width="272" height="484" class="aligncenter size-full wp-image-134549">
    </p>
    <p>
        Since you used
        <code>
            AccelerateInterpolator
        </code>
        , you should see your rocket accelerating after liftoff. Feel free to
        play around with interpolators if you’d like. I’ll sit here and wait. I
        promise :]
    </p>
    <h2>
        Which Properties Can You Animate?
    </h2>
    <p>
        Until now, you’ve only animated position and rotation for
        <code>
            View
        </code>
        , but
        <code>
            ValueAnimator
        </code>
        doesn’t care what you do with the value that it supplies.
    </p>
    <p>
        You can tell
        <code>
            ValueAnimator
        </code>
        to animate the value using any of the following types:
    </p>
    <ul>
        <li>
            <code>
                float
            </code>
            if you create
            <code>
                ValueAnimator
            </code>
            instance with
            <code>
                ofFloat
            </code>
        </li>
        <li>
            <code>
                int
            </code>
            if you do it with
            <code>
                ofInt
            </code>
        </li>
        <li>
            <code>
                ofObject
            </code>
            is for the cases when
            <code>
                float
            </code>
            or
            <code>
                int
            </code>
            is not enough — it’s often used to animate colors
        </li>
    </ul>
    <p>
        You can also animate any property of
        <code>
            View
        </code>
        . Some examples are:
    </p>
    <ul>
        <li>
            <code>
                scaleX
            </code>
            and
            <code>
                scaleY
            </code>
            – these allow you to scale the view by x-axis or y-axis independently,
            or you can call both with the same value to animate the view’s size.
        </li>
        <li>
            <code>
                translationX
            </code>
            and
            <code>
                translationY
            </code>
            – these allow you to change the view’s on-screen position.
        </li>
        <li>
            <code>
                alpha
            </code>
            – animate view’s transparency;
            <code>
                0
            </code>
            stands for completely transparent and
            <code>
                1
            </code>
            for completely opaque.
        </li>
        <li>
            <code>
                rotation
            </code>
            – rotates the view on screen; the argument is in degrees, so
            <code>
                360
            </code>
            means a full clockwise turn. You may specify negative values as well,
            for instance,
            <code>
                -90
            </code>
            means a counterclockwise quarter-turn.
        </li>
        <li>
            <code>
                rotationX
            </code>
            and
            <code>
                rotationY
            </code>
            – the same as
            <code>
                rotation
            </code>
            but along the x-axis and y-axis. These properties allow you to rotate
            in 3D.
        </li>
        <li>
            <code>
                backgroundColor
            </code>
            – lets you set a color. The integer argument must specify a color as Android
            constants
            <code>
                Color.YELLOW
            </code>
            ,
            <code>
                Color.BLUE
            </code>
            do.
        </li>
    </ul>
    <h3>
        ObjectAnimator
    </h3>
    <p>
        Meet
        <code>
            ObjectAnimator
        </code>
        , a subclass of
        <code>
            ValueAnimator
        </code>
        . If you only need to animate a single property of a single object,
        <code>
            ObjectAnimator
        </code>
        may just be your new best friend.
    </p>
    <p>
        Unlike
        <code>
            ValueAnimator
        </code>
        , where you must set a listener and do something with a value,
        <code>
            ObjectAnimator
        </code>
        can handle those bits for you almost automagically. :]
    </p>
    <p>
        Go to
        <em>
            LaunchRocketObjectAnimatorAnimationActivity.kt
        </em>
        class and enter the following code:
    </p>
    <pre lang="kotlin">
        // 1 val objectAnimator = ObjectAnimator.ofFloat(rocket, "translationY",
        0f, -screenHeight) // 2 objectAnimator.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
        objectAnimator.start()
    </pre>
    <p>
        Here’s what you’re doing:
    </p>
    <ol>
        <li>
            Creating an instance of
            <code>
                ObjectAnimator
            </code>
            (like you did with
            <code>
                ValueAnimator
            </code>
            ) except that the former takes two more parameters:
            <ul>
                <li>
                    <code>
                        rocket
                    </code>
                    is the object to animate
                </li>
                <li>
                    The object must have a property corresponding to the name of the property
                    you wish to change, which in this example is
                    <code>
                        “translationY”
                    </code>
                    . You’re able to do this because
                    <code>
                        rocket
                    </code>
                    is an object of class
                    <code>
                        View
                    </code>
                    , which, in its base Java class, has an accessible setter with
                    <code>
                        setTranslationY()
                    </code>
                    .
                </li>
            </ul>
        </li>
        <li>
            You set the duration for the animation and start it.
        </li>
    </ol>
    <p>
        Run your project. Select
        <em>
            Launch a rocket (ObjectAnimator)
        </em>
        in the list. Tap on the screen.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/linear-launch.gif"
        alt="linear-launch" width="272" height="484" class="aligncenter size-full wp-image-134552">
    </p>
    <p>
        The rocket behaves the same as it did with
        <code>
            ValueAnimator
        </code>
        , but with less code. :]
    </p>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : There’s a limitation to
            <code>
                ObjectAnimator
            </code>
            — it can’t animate two objects simultaneously. To work around it, you
            create two instances of
            <code>
                ObjectAnimator
            </code>
            .
        </p>
        <p>
            Consider your use cases and the amount of coding required when you decide
            to use
            <code>
                ObjectAnimator
            </code>
            or
            <code>
                ValueAnimator
            </code>
            .
        </p>
    </div>
    <h3>
        Animating Color
    </h3>
    <p>
        Speaking of use cases, there’s animating colors to consider. Neither
        <code>
            ofFloat()
        </code>
        nor
        <code>
            ofInt()
        </code>
        can construct your animator
        <i>
            and
        </i>
        get good results with colors. You’re better off using
        <code>
            ArgbEvaluator
        </code>
        .
    </p>
    <p>
        Open
        <em>
            ColorAnimationActivity.kt
        </em>
        and put this code into
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        //1 val objectAnimator = ObjectAnimator.ofObject( frameLayout, "backgroundColor",
        ArgbEvaluator(), ContextCompat.getColor(this, R.color.background_from),
        ContextCompat.getColor(this, R.color.background_to) ) // 2 objectAnimator.repeatCount
        = 1 objectAnimator.repeatMode = ValueAnimator.REVERSE // 3 objectAnimator.duration
        = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION objectAnimator.start()
    </pre>
    <p>
        In the code above, you:
    </p>
    <ol>
        <li>
            Call
            <code>
                ObjectAnimator.ofObject()
            </code>
            and give it the following arguments:
            <ul>
                <li>
                    <code>
                        frameLayout
                    </code>
                    — the object with the property to be animated
                </li>
                <li>
                    <code>
                        "backgroundColor"
                    </code>
                    — the property you want to animate
                </li>
                <li>
                    <code>
                        ArgbEvaluator()
                    </code>
                    — an additional argument that specifies how to interpolate between two
                    different
                    <em>
                        ARGB
                    </em>
                    (alpha, red, green, blue) color values
                </li>
                <li>
                    Start and end color values — here you make use of
                    <code>
                        ComtextCompat.getColor()
                    </code>
                    to get the color resource id of a custom color specified in your
                    <code>
                        colors.xml
                    </code>
                    .
                </li>
            </ul>
        </li>
        <li>
            Set the number of times the animation will repeat by setting the object’s
            <code>
                repeatCount
            </code>
            value. Then you set its
            <code>
                repeatMode
            </code>
            to define what the animation does when it reaches the end. More on this
            soon!
        </li>
        <li>
            Set duration and start the animation.
        </li>
    </ol>
    <p>
        Build and run. Pick the
        <em>
            Background color
        </em>
        item and tap on the screen.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/bg-color.gif"
        alt="bg-color" width="272" height="484" class="aligncenter size-full wp-image-134368">
    </p>
    <p>
        That’s amazing! Hey, you’re getting the hang of this pretty quickly. That’s
        a buttery-smooth background color change :]
    </p>
    <h2>
        Combining Animations
    </h2>
    <p>
        Animating a view is pretty awesome, but so far you’ve changed only one
        property and one object at a time. Animations need not be so restrictive.
    </p>
    <p>
        It’s time to send Doge to the moon! :]
    </p>
    <p>
        <code>
            AnimatorSet
        </code>
        allows you to play several animations together or in sequence. You pass
        your first animator to
        <code>
            play()
        </code>
        , which accepts an
        <code>
            Animator
        </code>
        object as an argument and returns a builder.
    </p>
    <p>
        Then you can call the following methods on that builder, all of which
        accept
        <code>
            Animator
        </code>
        as an argument:
    </p>
    <ul>
        <li>
            <code>
                with()
            </code>
            — to play the
            <code>
                Animator
            </code>
            passed as the argument simultaneously with the first one you specified
            in
            <code>
                play()
            </code>
        </li>
        <li>
            <code>
                before()
            </code>
            — to play it before
        </li>
        <li>
            <code>
                after()
            </code>
            — to play it after
        </li>
    </ul>
    <p>
        You can create chains of calls such as these.
    </p>
    <p>
        Open
        <em>
            LaunchAndSpinAnimatorSetAnimatorActivity.kt
        </em>
        in your editor, and put the following code into
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        // 1 val positionAnimator = ValueAnimator.ofFloat(0f, -screenHeight) //
        2 positionAnimator.addUpdateListener { val value = it.animatedValue as
        Float rocket.translationY = value } // 3 val rotationAnimator = ObjectAnimator.ofFloat(rocket,
        "rotation", 0f, 180f) // 4 val animatorSet = AnimatorSet() // 5 animatorSet.play(positionAnimator).with(rotationAnimator)
        // 6 animatorSet.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
        animatorSet.start()
    </pre>
    <p>
        Here’s what you’re doing in this block:
    </p>
    <ol>
        <li>
            Create a new
            <code>
                ValueAnimator
            </code>
            .
        </li>
        <li>
            Attach an
            <code>
                AnimatorUpdateListener
            </code>
            to the ValueAnimator that updates the rocket’s position.
        </li>
        <li>
            Create an
            <code>
                ObjectAnimator
            </code>
            , a second animator that updates the rocket’s rotation.
        </li>
        <li>
            Create a new instance of
            <code>
                AnimatorSet
            </code>
            .
        </li>
        <li>
            Specify that you’d like to execute
            <code>
                positionAnimator
            </code>
            together with
            <code>
                rotationAnimator
            </code>
            .
        </li>
        <li>
            Just as with a typical animator, you set a duration and call
            <code>
                start()
            </code>
            .
        </li>
    </ol>
    <p>
        Build and run again. Select the
        <em>
            Launch and spin (AnimatorSet)
        </em>
        . Tap the screen.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/launch-n-spin.gif"
        alt="launch-n-spin" width="272" height="484" class="aligncenter size-full wp-image-134377">
    </p>
    <p>
        Doge defies the laws of physics with this one.
    </p>
    <p>
        There’s a nifty tool to simplify animating several properties of the same
        object. The tool is called…
    </p>
    <h3>
        ViewPropertyAnimator
    </h3>
    <p>
        One of the greatest things about animation code that uses
        <code>
            ViewPropertyAnimator
        </code>
        is that it’s easy to write and read — you’ll see.
    </p>
    <p>
        Open
        <em>
            LaunchAndSpinViewPropertyAnimatorAnimationActivity.kt
        </em>
        and add the following call to
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        rocket.animate() .translationY(-screenHeight) .rotationBy(360f) .setDuration(BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION)
        .start()
    </pre>
    <p>
        In here,
        <code>
            animate()
        </code>
        returns an instance of
        <code>
            ViewPropertyAnimator
        </code>
        so you can chain the calls.
    </p>
    <p>
        Build and run, select
        <em>
            Launch and spin (ViewPropertyAnimator)
        </em>
        , and you’ll see the same animation as in the previous section.
    </p>
    <p>
        Compare your code for this section to the
        <code>
            AnimatorSet
        </code>
        code snippet that you implemented in the previous section:
    </p>
    <pre lang="kotlin">
        val positionAnimator = ValueAnimator.ofFloat(0f, -screenHeight) positionAnimator.addUpdateListener
        { val value = it.animatedValue as Float rocket?.translationY = value }
        val rotationAnimator = ObjectAnimator.ofFloat(rocket, "rotation", 0f, 180f)
        val animatorSet = AnimatorSet() animatorSet.play(positionAnimator).with(rotationAnimator)
        animatorSet.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
        animatorSet.start()
    </pre>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate.png"
        alt="" width="320" height="320" class="aligncenter size-medium wp-image-173339"
        srcset="https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate.png 500w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-250x250.png 250w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-320x320.png 320w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-32x32.png 32w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-50x50.png 50w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-64x64.png 64w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-96x96.png 96w, https://koenig-media.raywenderlich.com/uploads/2017/10/viewanimate-128x128.png 128w"
        sizes="(max-width: 320px) 100vw, 320px">
    </p>
    <p>
        <code>
            ViewPropertyAnimator
        </code>
        may provide better performance for multiple simultaneous animations. It
        optimizes invalidated calls, so they only take place once for several properties
        — in contrast to each animated property causing its own invalidation independently.
    </p>
    <h3>
        Animating the Same Property of Two Objects
    </h3>
    <p>
        A nice feature of
        <code>
            ValueAnimator
        </code>
        is that you can reuse its animated value and apply it to as many objects
        as you like.
    </p>
    <p>
        Test it out by opening
        <em>
            FlyWithDogeAnimationActivity.kt
        </em>
        and putting the following code in
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        //1 val positionAnimator = ValueAnimator.ofFloat(0f, -screenHeight) positionAnimator.addUpdateListener
        { val value = it.animatedValue as Float rocket.translationY = value doge.translationY
        = value } //2 val rotationAnimator = ValueAnimator.ofFloat(0f, 360f) rotationAnimator.addUpdateListener
        { val value = it.animatedValue as Float doge.rotation = value } //3 val
        animatorSet = AnimatorSet() animatorSet.play(positionAnimator).with(rotationAnimator)
        animatorSet.duration = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION
        animatorSet.start()
    </pre>
    <p>
        In the above code you just created three animators:
    </p>
    <ol>
        <li>
            <code>
                positionAnimator
            </code>
            — for changing positions of both
            <code>
                rocket
            </code>
            and
            <code>
                doge
            </code>
        </li>
        <li>
            <code>
                rotationAnimator
            </code>
            — for rotating Doge
        </li>
        <li>
            <code>
                animatorSet
            </code>
            — to combine the first two animators
        </li>
    </ol>
    <p>
        Notice that you set translation for
        <i>
            two
        </i>
        objects at once in the first animator.
    </p>
    <p>
        Run the app and select
        <em>
            Don’t leave Doge behind (Animating two objects)
        </em>
        . You know what to do now. To the moon!
    </p>
    <h2>
        Animation Listeners
    </h2>
    <p>
        Animation typically implies that a certain action has occurred or will
        take place. Typically, whatever happens usually comes at the end of your
        fancy animation.
    </p>
    <p>
        You don’t get to observe it, but know that the rocket stops and stays
        off screen when the animation ends. If you don’t plan to land it or finish
        the activity, you could remove this particular view to conserve resources.
    </p>
    <p>
        <code>
            AnimatorListener
        </code>
        — receives a notification from the animator when the following events
        occur:
    </p>
    <ul>
        <li>
            <code>
                onAnimationStart()
            </code>
            — called when the animation starts
        </li>
        <li>
            <code>
                onAnimationEnd()
            </code>
            — called when the animation ends
        </li>
        <li>
            <code>
                onAnimationRepeat()
            </code>
            — called if the animation repeats
        </li>
        <li>
            <code>
                onAnimationCancel()
            </code>
            — called if the animation is canceled
        </li>
    </ul>
    <p>
        Open
        <em>
            WithListenerAnimationActivity.kt
        </em>
        and add the following code to
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        //1 val animator = ValueAnimator.ofFloat(0f, -screenHeight) animator.addUpdateListener
        { val value = it.animatedValue as Float rocket.translationY = value doge.translationY
        = value } // 2 animator.addListener(object : Animator.AnimatorListener
        { override fun onAnimationStart(animation: Animator) { // 3 Toast.makeText(applicationContext,
        "Doge took off", Toast.LENGTH_SHORT) .show() } override fun onAnimationEnd(animation:
        Animator) { // 4 Toast.makeText(applicationContext, "Doge is on the moon",
        Toast.LENGTH_SHORT) .show() finish() } override fun onAnimationCancel(animation:
        Animator) {} override fun onAnimationRepeat(animation: Animator) {} })
        // 5 animator.duration = 5000L animator.start()
    </pre>
    <p>
        The structure of the code above, with the exception of the listener part,
        should look the same as the previous section. Here’s what you’re doing
        in there:
    </p>
    <ol>
        <li>
            Create and set up an animator. You use
            <code>
                ValueAnimator
            </code>
            to change the position of two objects simultaneously — you can’t do the
            same thing with a single
            <code>
                ObjectAnimator
            </code>
            .
        </li>
        <li>
            Add the
            <code>
                AnimatorListener
            </code>
            .
        </li>
        <li>
            Show a toast message when the animation starts
        </li>
        <li>
            And another toast when it ends
        </li>
        <li>
            Start the animation as usual
        </li>
    </ol>
    <p>
        Run the app. Select
        <em>
            Animation events
        </em>
        . Tap on the screen. Look at the messages!
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/events.gif"
        alt="events" width="272" height="484" class="aligncenter size-full wp-image-134384">
    </p>
    <div class="note">
        <em>
            Note
        </em>
        : You also can add a listener to
        <code>
            ViewPropertyAnimator
        </code>
        by adding a
        <code>
            setListener
        </code>
        to a call chain before calling
        <code>
            start()
        </code>
        :
        <p>
        </p>
        <pre lang="kotlin">
            rocket.animate().setListener(object : Animator.AnimatorListener { // Your
            action })
        </pre>
        <p>
            Alternatively, you can set start and end actions on your View by calling
            <code>
                withStartAction(Runnable)
            </code>
            and
            <code>
                withEndAction(Runnable)
            </code>
            after
            <code>
                animate()
            </code>
            . It’s the equivalent to an
            <code>
                AnimatorListener
            </code>
            with these actions.
        </p>
    </div>
    <h2>
        Animation Options
    </h2>
    <p>
        Animations are not one-trick ponies that simply stop and go. They can
        loop, reverse, run for a specific duration, etc.
    </p>
    <p>
        In Android, you can use the following methods to adjust an animation:
    </p>
    <ul>
        <li>
            <code>
                repeatCount
            </code>
            — specifies the number of times the animation should repeat
            <i>
                after
            </i>
            the initial run.
        </li>
        <li>
            <code>
                repeatMode
            </code>
            — defines what this animation should do when it reaches the end
        </li>
        <li>
            <code>
                duration
            </code>
            — specifies the animation’s total duration
        </li>
    </ul>
    <p>
        Open up
        <em>
            FlyThereAndBackAnimationActivity.kt
        </em>
        , and add the following to
        <code>
            onStartAnimation()
        </code>
        .
    </p>
    <pre lang="kotlin">
        // 1 val animator = ValueAnimator.ofFloat(0f, -screenHeight) animator.addUpdateListener
        { val value = it.animatedValue as Float rocket.translationY = value doge.translationY
        = value } // 2 animator.repeatMode = ValueAnimator.REVERSE // 3 animator.repeatCount
        = 3 // 4 animator.duration = 500L animator.start()
    </pre>
    <p>
        In here, you:
    </p>
    <ol>
        <li>
            Create an animator, as usual
        </li>
        <li>
            You can set the
            <code>
                repeatMode
            </code>
            to either of the following:
            <ul>
                <li>
                    <code>
                        RESTART
                    </code>
                    — restarts the animation from the beginning.
                </li>
                <li>
                    <code>
                        REVERSE
                    </code>
                    — reverses the animation’s direction with every iteration.
                </li>
            </ul>
            <p>
                In this case, you set it to
                <code>
                    REVERSE
                </code>
                because you want the rocket to take off and then go back to the same position
                where it started. Just like SpaceX! :]
            </p>
        </li>
        <li>
            …Except you’ll do it twice.
        </li>
        <li>
            Set a duration and start the animation, as usual.
        </li>
    </ol>
    <div class="note">
        <p>
            <em>
                Note
            </em>
            : So why does the third section specify the repeat count at three? Each
            up-and-down motion consumes two repetitions, so you need three to bring
            Doge back to earth twice: one to land the first time, and two to launch
            and land again. How many times would you like to see Doge bounce? Play
            around with it!
        </p>
    </div>
    <p>
        Run the app. Select
        <em>
            Fly there and back (Animation options)
        </em>
        in the list. A new screen is opened. Tap on the screen.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/there-and-back.gif"
        alt="there-and-back" width="272" height="484" class="aligncenter size-full wp-image-134385">
    </p>
    <p>
        You should see your rocket jumping like a grasshopper! Take that, Elon
        Musk. :]
    </p>
    <h2>
        Declaring Animations in XML
    </h2>
    <p>
        You’ve made it to the best part of this tutorial. In this final section,
        you’ll learn how to declare once and use everywhere — yes, that’s right,
        you’ll be able to reuse your animations with impunity.
    </p>
    <p>
        By defining animations in XML, you allow reuse of animations throughout
        your code base.
    </p>
    <p>
        Defining animations in XML bears some resemblance to composing view layouts.
    </p>
    <p>
        The starter project has an animation XML in
        <em>
            res/animator
        </em>
        named
        <em>
            jump_and_blink.xml
        </em>
        . Open the file in the editor, you should see this:
    </p>
    <pre lang="xml">
        &lt;?xml version="1.0" encoding="utf-8"?&gt; &lt;set xmlns:android="http://schemas.android.com/apk/res/android"
        android:ordering="together"&gt; &lt;/set&gt;
    </pre>
    <p>
        The following XML tags are available to you:
    </p>
    <ul>
        <li>
            <code>
                set
            </code>
            — the same as
            <code>
                AnimatorSet
            </code>
        </li>
        <li>
            <code>
                animator
            </code>
            — the same as
            <code>
                ValueAnimator
            </code>
        </li>
        <li>
            <code>
                objectAnimator
            </code>
            — you guessed correctly; it stands for
            <code>
                ObjectAnimator
            </code>
        </li>
    </ul>
    <p>
        When using an
        <code>
            AnimatorSet
        </code>
        in XML, you nest the
        <code>
            ValueAnimator
        </code>
        and
        <code>
            ObjectAnimator
        </code>
        objects inside it, similar to how you nest
        <code>
            View
        </code>
        objects inside
        <code>
            ViewGroup
        </code>
        objects (
        <code>
            RelativeLayout
        </code>
        ,
        <code>
            LinearLayout
        </code>
        , etc.) in layout XML files.
    </p>
    <p>
        Replace the contents of
        <em>
            jump_and_blink.xml
        </em>
        with the following code:
    </p>
    <pre lang="xml">
        &lt;?xml version="1.0" encoding="utf-8"?&gt; &lt;set xmlns:android="http://schemas.android.com/apk/res/android"
        android:ordering="together"&gt; &lt;objectAnimator android:propertyName="alpha"
        android:duration="1000" android:repeatCount="1" android:repeatMode="reverse"
        android:interpolator="@android:interpolator/linear" android:valueFrom="1.0"
        android:valueTo="0.0" android:valueType="floatType"/&gt; &lt;objectAnimator
        android:propertyName="translationY" android:duration="1000" android:repeatCount="1"
        android:repeatMode="reverse" android:interpolator="@android:interpolator/bounce"
        android:valueFrom="0" android:valueTo="-500" android:valueType="floatType"/&gt;
        &lt;/set&gt;
    </pre>
    <p>
        Here you declare a root element,
        <code>
            set
        </code>
        tag. Its
        <code>
            ordering
        </code>
        attribute can be either
        <code>
            together
        </code>
        or
        <code>
            sequential
        </code>
        . It’s
        <code>
            together
        </code>
        by default, but you may prefer to specify it for clarity. The
        <code>
            set
        </code>
        tag has two child XML tags, each of which is an
        <code>
            objectAnimator
        </code>
        .
    </p>
    <p>
        Take a look at the following attributes of
        <code>
            objectAnimator
        </code>
        :
    </p>
    <ul>
        <li>
            <code>
                android:valueFrom
            </code>
            and
            <code>
                android:valueTo
            </code>
            — specify start and end values like you did when you created an instance
            of
            <code>
                ObjectAnimator
            </code>
        </li>
        <li>
            <code>
                android:valueType
            </code>
            — value type; either
            <code>
                floatType
            </code>
            or
            <code>
                intType
            </code>
        </li>
        <li>
            <code>
                android:propertyName
            </code>
            — the property you want to animate without the
            <code>
                set
            </code>
            part
        </li>
        <li>
            <code>
                android:duration
            </code>
            — duration of the animation
        </li>
        <li>
            <code>
                android:repeatCount
            </code>
            — the same as with
            <code>
                setRepeatCount
            </code>
        </li>
        <li>
            <code>
                android:repeatMode
            </code>
            — the same as with
            <code>
                setRepeatMode
            </code>
        </li>
        <li>
            <code>
                android:interpolator
            </code>
            — specify interpolator; it usually starts with
            <code>
                @android:interpolator/
            </code>
            . Start typing this and Android Studio will show all available interpolators
            under autocomplete options
        </li>
        <li>
            You can’t specify your target object here, but you can do it later in
            Kotlin
        </li>
    </ul>
    <p>
        In the last block, you added two instances of
        <code>
            objectAnimator
        </code>
        to the
        <code>
            AnimatorSet
        </code>
        , and they will play together. Now, it’s time to use them.
    </p>
    <p>
        Go to
        <em>
            XmlAnimationActivity.kt
        </em>
        and add the following code to
        <code>
            onStartAnimation()
        </code>
        :
    </p>
    <pre lang="kotlin">
        // 1 val rocketAnimatorSet = AnimatorInflater.loadAnimator(this, R.animator.jump_and_blink)
        as AnimatorSet // 2 rocketAnimatorSet.setTarget(rocket) // 3 val dogeAnimatorSet
        = AnimatorInflater.loadAnimator(this, R.animator.jump_and_blink) as AnimatorSet
        // 4 dogeAnimatorSet.setTarget(doge) // 5 val bothAnimatorSet = AnimatorSet()
        bothAnimatorSet.playTogether(rocketAnimatorSet, dogeAnimatorSet) // 6 bothAnimatorSet.duration
        = BaseAnimationActivity.Companion.DEFAULT_ANIMATION_DURATION bothAnimatorSet.start()
    </pre>
    <p>
        In the above code, you’re doing a few things:
    </p>
    <ol>
        <li>
            First, you load
            <code>
                AnimatorSet
            </code>
            from
            <code>
                R.animator.jump_and_blink
            </code>
            file, just like you normally would to inflate a view layout
        </li>
        <li>
            Then you set
            <code>
                rocket
            </code>
            as the target for just-loaded animator
        </li>
        <li>
            Load the animator from the same file once again
        </li>
        <li>
            Rinse and repeat for
            <code>
                doge
            </code>
            object
        </li>
        <li>
            Now you create a third
            <code>
                AnimatorSet
            </code>
            and set it up to play the first two simultaneously
        </li>
        <li>
            Set the duration for the root animator and start
        </li>
        <li>
            Whew! Rest just a little bit :]
        </li>
    </ol>
    <p>
        Build and run. Select
        <em>
            Jump and blink (Animations in XML)
        </em>
        in the list. Tap to see your handiwork.
    </p>
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2016/05/jump-n-blink.gif"
        alt="jump-n-blink" width="272" height="484" class="aligncenter size-full wp-image-134382">
    </p>
    <p>
        You should see Doge jumping, disappearing and then returning back to the
        ground safely :]
    </p>
    <h2>
        Where To Go From Here
    </h2>
    <p>
        You can grab the final project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/10/rocket_launcher-final.zip">
            here
        </a>
        .
    </p>
    <p>
        During this tutorial you:
    </p>
    <ul>
        <li>
            Created and used property animations with
            <code>
                ValueAnimator
            </code>
            and
            <code>
                ObjectAnimator
            </code>
        </li>
        <li>
            Set up
            <em>
                time interpolator
            </em>
            of your choice for your animation
        </li>
        <li>
            Animated position, rotation and color for
            <code>
                View
            </code>
        </li>
        <li>
            Combined animations together
        </li>
        <li>
            Used the spectacular
            <code>
                ViewPropertyAnimator
            </code>
            with the help of
            <code>
                animate()
            </code>
        </li>
        <li>
            Repeated your animation
        </li>
        <li>
            Defined the animation in XML for reuse across the project
        </li>
    </ul>
    <p>
        Basically, you just gained Android animation super-powers.
    </p>
    <p>
        If you’re hungry for more, check out the available time interpolators
        in
        <a href="https://developer.android.com/reference/android/animation/TimeInterpolator.html"
        target="_blank">
            Android’s documentation
        </a>
        (see Known Indirect Subclasses). If you’re not happy with either of them,
        you can create your own. You can also set
        <code>
            Keyframe
        </code>
        s for your animation to make them very sophisticated.
    </p>
    <p>
        Android has other animations systems like
        <em>
            View animations
        </em>
        and
        <em>
            Drawable Animations
        </em>
        . You can also make use of
        <em>
            Canvas
        </em>
        and
        <em>
            OpenGL ES
        </em>
        APIs to create animations. Stay tuned :]
    </p>
</div>