# 入门ARCore - Kotlin
---
#### [原文地址](https://www.raywenderlich.com/170520/getting-started-arcore-kotlin) 翻译：[DeveloperLx](http://weibo.com/DeveloperLx)

<div class="content-wrapper">
    <p>
        <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/ARCore-feature.png"
        alt="Getting Started with ARCore with Kotlin" width="250" height="250"
        class="alignright size-thumbnail bordered">
    </p>
    <p>
        Did Vikings have cannons in reality? I’m not entirely sure, but there’s
        no reason Vikings can’t have cannons in Augmented Reality! :]
    </p>
    <p>
        At WWDC 2017, Apple announced
        <em>
            ARKit
        </em>
        , its foray into the world of AR development. Not to be outdone, just
        last week Google
        <a href="https://www.blog.google/products/google-vr/arcore-augmented-reality-android-scale/"
        target="_blank">
            announced
        </a>
        <em>
            ARCore
        </em>
        , extracted from the
        <a href="https://get.google.com/tango/" target="_blank">
            Tango
        </a>
        indoor mapping project. Tango requires using particular devices that have
        a depth sensor, whereas ARCore will (eventually) be available on most Android
        devices.
    </p>
    <p>
        The race to explore this new domain is on, with demo projects coming fast
        and furious. You can check out some of the ARCore demos at the
        <a href="https://experiments.withgoogle.com/ar" target="_blank">
            AR Experiments
        </a>
        site.
    </p>
    <p>
        ARCore apps can be built using
        <em>
            OpenGL
        </em>
        ,
        <em>
            Unity
        </em>
        , and
        <em>
            Unreal
        </em>
        . In this tutorial, you’ll get started by building on top of a modified
        version of the OpenGL sample app provided by Google, working entirely in
        <em>
            Kotlin
        </em>
        ! And all within the comfort of Android Studio! :]
    </p>
    <p>
        If you’re just getting started with Kotlin, please check out
        <a href="https://www.raywenderlich.com/132381/kotlin-for-android-an-introduction"
        target="_blank">
            Kotlin For Android: An Introduction
        </a>
        .
    </p>
    <p>
        ARCore does not work with the Android Emulator. As of this writing, you’ll
        need a
        <em>
            Samsung Galaxy S8
        </em>
        or
        <em>
            Google Pixel/Pixel XL
        </em>
        to fully follow along, ideally running Android Nougat (7.0) or later.
        If you don’t have either of those devices, hopefully you’ll still get a
        feel for working with the ARCore SDK.
    </p>
    <p>
        Ready to explore this brave new (augmented) world? Let’s go!
    </p>
    <h2>
        Getting Started
    </h2>
    <p>
        Begin by downloading the starter project
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/targetpractice-starter-2.zip">
            here
        </a>
        . Open up the starter project in Android Studio 3.0 Beta 5 or later.
    </p>
    <p>
        You may also have luck if you’re using Android Studio 2.3.3 with the Kotlin
        plugin. :]
    </p>
    <p>
        Next, make sure to
        <a href="https://developer.android.com/studio/debug/dev-options.html#enable"
        target="_blank">
            enable developer options
        </a>
        on your device, and
        <a href="https://developer.android.com/studio/debug/dev-options.html#debugging"
        target="_blank">
            enable USB debugging
        </a>
        . Before running the starter project, you’ll also need to download and
        install the
        <a href="https://github.com/google-ar/arcore-android-sdk/releases/download/sdk-preview/arcore-preview.apk">
            ARCore Service
        </a>
        provided by Google.
    </p>
    <p>
        The ARCore Service can be installed using the following
        <em>
            adb
        </em>
        command:
    </p>
    <pre lang="bash">
        $ adb install -r -d arcore-preview.apk
    </pre>
    <p>
        Check out the adb
        <a href="https://developer.android.com/studio/command-line/adb.html">
            documentation
        </a>
        if you need more info.
    </p>
    <p>
        Now you can hit
        <em>
            Run/Run ‘app’
        </em>
        or hit Ctrl-R, and the starter up should be up and running.
    </p>
    <p>
        You’ll first get prompted to provide camera permissions, and on approving,
        you’ll see a radio group at the top, which you’ll use later to select the
        type of object to insert into the scene.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-170527"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-121813.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        You’ll see a snackbar at the bottom indicating “Searching for surfaces…”.
        You may also see a few points highlighted, which are points being tracked.
    </p>
    <p>
        Aiming the device at a flat surface, a plane will be detected:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206-281x500.png"
            alt="" width="281" height="500" class="aligncenter size-large wp-image-170528"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206-281x500.png 281w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206-180x320.png 180w, https://koenig-media.raywenderlich.com/uploads/2017/09/device-2017-09-05-122206.png 1080w"
            sizes="(max-width: 281px) 100vw, 281px">
        </a>
    </p>
    <p>
        Once the first plane is detected, the snackbar disappears and the plane
        is highlighted on the screen. Note that light-colored planes may have trouble
        being detected.
    </p>
    <p>
        At this point, the starter app doesn’t do a whole lot, but time to check
        out some it’s code to get your bearings! Especially before you setup a
        viking with a cannon!
    </p>
    <h2>
        The ARCode SDK
    </h2>
    <p>
        The starter app has the 3D models we’ll be using in the
        <em>
            main/assets
        </em>
        folder in the
        <em>
            Project
        </em>
        view of Android Studio. There are models for a viking, a cannon, and a
        target. The 3D model files were created in
        <em>
            Blender
        </em>
        using the instructions in
        <a href="https://www.raywenderlich.com/48293/how-to-export-blender-models-to-opengl-es-part-1"
        target="_blank">
            How To Export Blender Models to OpenGL ES: Part 1/3
        </a>
        .
    </p>
    <p>
        Inside of
        <em>
            res/raw
        </em>
        , there are OpenGL shaders, all from the Google ARCore sample app.
    </p>
    <p>
        You’ll see a package in the starter app named
        <em>
            rendering
        </em>
        , which contains some OpenGL renderers and utilities from the Google ARCore
        sample app. There’s also a class named
        <em>
            PlaneAttachment
        </em>
        that has been converted to Kotlin and that uses the ARCore SDK.
    </p>
    <h3>
        Planes, Anchors, and Poses
    </h3>
    <p>
        The
        <em>
            PlaneAttachment
        </em>
        class is constructed using a
        <em>
            Plane
        </em>
        and an
        <em>
            Anchor
        </em>
        , and can be used to construct a
        <em>
            Pose
        </em>
        . All three are from the ARCore SDK.
    </p>
    <p>
        A
        <em>
            Plane
        </em>
        describes a real-world planar surface. An
        <em>
            Anchor
        </em>
        descibes a fixed location and orientation in space. A
        <em>
            Pose
        </em>
        describes a coordinate transformation from one system to another, from
        an object’s local frame to the
        <em>
            world coordinate frame
        </em>
        .
    </p>
    <p>
        You can read more about each in the official
        <a href="https://developers.google.com/ar/reference/java/com/google/ar/core/package-summary"
        target="_blank">
            documentation
        </a>
        .
    </p>
    <p>
        So,
        <em>
            PlaneAttachment
        </em>
        let’s you attach an anchor to a plane, and retrieve the corresponding
        pose, which is used by ARCore as you move about the anchor point.
    </p>
    <h3>
        ARCore Session
    </h3>
    <p>
        The starter app includes an ARCore
        <em>
            Session
        </em>
        object in
        <em>
            MainActivity
        </em>
        . The session describes the entire AR state, and you’ll use it to attach
        anchors to planes when the user taps the screen.
    </p>
    <p>
        In
        <code>
            setupSession()
        </code>
        , called from
        <code>
            onCreate(...)
        </code>
        , the starter app checks that the device supports ARCore. If not, a
        <em>
            Toast
        </em>
        is displayed and the activity finishes.
    </p>
    <p>
        Assuming you have a supported device, it’s time to setup some objects
        to render in the scene!
    </p>
    <h2>
        Adding Objects
    </h2>
    <p>
        Open up
        <em>
            MainActivity
        </em>
        , and add the following properties
    </p>
    <pre lang="kotlin">
        private val vikingObject = ObjectRenderer() private val cannonObject =
        ObjectRenderer() private val targetObject = ObjectRenderer()
    </pre>
    <p>
        Each is defined as an
        <em>
            ObjectRenderer
        </em>
        from the ARCore sample app.
    </p>
    <p>
        Also, add three
        <em>
            PlaneAttachment
        </em>
        properties just below the objects:
    </p>
    <pre lang="kotlin">
        private var vikingAttachment: PlaneAttachment? = null private var cannonAttachment:
        PlaneAttachment? = null private var targetAttachment: PlaneAttachment?
        = null
    </pre>
    <p>
        These are Kotlin
        <em>
            nullables
        </em>
        initialized as null, and will be created later when the user taps the
        screen.
    </p>
    <p>
        You need to setup the objects, which you’ll do in
        <code>
            onSurfaceCreated(...)
        </code>
        . Find the existing
        <code>
            try-catch
        </code>
        block in that function add the following
        <code>
            try-catch
        </code>
        above it:
    </p>
    <pre lang="kotlin">
        // Prepare the other rendering objects. try { vikingObject.createOnGlThread(this,
        "viking.obj", "viking.png") vikingObject.setMaterialProperties(0.0f, 3.5f,
        1.0f, 6.0f) cannonObject.createOnGlThread(this, "cannon.obj", "cannon.png")
        cannonObject.setMaterialProperties(0.0f, 3.5f, 1.0f, 6.0f) targetObject.createOnGlThread(this,
        "target.obj", "target.png") targetObject.setMaterialProperties(0.0f, 3.5f,
        1.0f, 6.0f) } catch (e: IOException) { Log.e(TAG, "Failed to read obj file")
        }
    </pre>
    <p>
        You’re using the 3D model files provided in the starter app to setup each
        of the three objects, as well as setting some material properties on each.
    </p>
    <h2>
        Attaching Anchors to the Session
    </h2>
    <p>
        Find
        <code>
            handleTaps(...)
        </code>
        in
        <em>
            MainActivity
        </em>
        . Add the following inside the innermost
        <code>
            if
        </code>
        statement, just above the comment before the
        <code>
            break
        </code>
        statement:
    </p>
    <pre lang="kotlin">
        when (mode) { Mode.VIKING -&gt; vikingAttachment = addSessionAnchorFromAttachment(vikingAttachment,
        hit) Mode.CANNON -&gt; cannonAttachment = addSessionAnchorFromAttachment(cannonAttachment,
        hit) Mode.TARGET -&gt; targetAttachment = addSessionAnchorFromAttachment(targetAttachment,
        hit) }
    </pre>
    <p>
        The value of
        <code>
            mode
        </code>
        is controlled by the radio buttons at the top of the screen.
        <code>
            Mode
        </code>
        is a Kotlin
        <em>
            enum class
        </em>
        that also includes a scale factor float value for each mode. The scale
        factor is used to tune the size of the corresponding 3D model in the scene.
    </p>
    <p>
        In the
        <code>
            when
        </code>
        statement, for each mode, you’re setting a new value for the corresponding
        <em>
            PlaneAttachment
        </em>
        , using the old attachment and the hit value for the tap, which is an
        ARCore
        <em>
            PlaneHitResult
        </em>
        defining the intersection of the 3D ray for the tap and a plane.
    </p>
    <p>
        You now need to add
        <code>
            addSessionAnchorFromAttachment(...)
        </code>
        :
    </p>
    <pre lang="kotlin">
        private fun addSessionAnchorFromAttachment( previousAttachment: PlaneAttachment?,
        hit: PlaneHitResult): PlaneAttachment { previousAttachment?.let { session.removeAnchors(Arrays.asList(previousAttachment.anchor))
        } return PlaneAttachment(hit.plane, session.addAnchor(hit.hitPose)) }
    </pre>
    <p>
        If the
        <code>
            previousAttachment
        </code>
        is not null, you’re first removing its anchor from the session, then adding
        in the new anchor to the session and returning a new value for the
        <em>
            PlaneAttachment
        </em>
        , based on the PlaneHitResult plane and an anchor from the PlaneHitResult
        pose.
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/vikingcannons.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/vikingcannons.png"
            alt="" width="372" height="281" class="aligncenter size-full wp-image-170603">
        </a>
    </p>
    <p>
        You’re almost ready to see your viking do some target practice! :]
    </p>
    <h2>
        Drawing the Objects
    </h2>
    <p>
        The last step you need to do is draw the objects on the screen. You’re
        creating plane attachments when the user taps, but now you need to draw
        the objects as part of the screen rendering.
    </p>
    <p>
        Look for the
        <code>
            onDrawFrame(...)
        </code>
        function. Add the following calls to the bottom of the
        <code>
            try
        </code>
        block:
    </p>
    <pre lang="kotlin">
        drawObject(vikingObject, vikingAttachment, Mode.VIKING.scaleFactor, projectionMatrix,
        viewMatrix, lightIntensity) drawObject(cannonObject, cannonAttachment,
        Mode.CANNON.scaleFactor, projectionMatrix, viewMatrix, lightIntensity)
        drawObject(targetObject, targetAttachment, Mode.TARGET.scaleFactor, projectionMatrix,
        viewMatrix, lightIntensity)
    </pre>
    <p>
        You’re calling the pre-existing
        <code>
            drawObject(...)
        </code>
        helper function, which takes the object, its corresponding attachment,
        its corresponding scale factor, as well as matrices and values needed for
        OpenGL to draw the object that are computed using these starter app helpers:
    </p>
    <pre lang="kotlin">
        private fun computeProjectionMatrix(): FloatArray { val projectionMatrix
        = FloatArray(16) session.getProjectionMatrix(projectionMatrix, 0, 0.1f,
        100.0f) return projectionMatrix } private fun computeViewMatrix(frame:
        Frame): FloatArray { val viewMatrix = FloatArray(16) frame.getViewMatrix(viewMatrix,
        0) return viewMatrix } private fun computeLightIntensity(frame: Frame)
        = frame.lightEstimate.pixelIntensity
    </pre>
    <p>
        The
        <code>
            projectionMatrix
        </code>
        is calculated from the ARCore Session. The
        <code>
            viewMatrix
        </code>
        is calculated from the ARCore
        <em>
            Frame
        </em>
        , which describes the AR state at a particular point in time. The
        <code>
            lightIntensity
        </code>
        is also determined from the frame.
    </p>
    <p>
        Go ahead and run the app. Select a radio button at the top to select an
        object mode. Then find a plane with your camera and tap to place an object.
        Once you’ve placed all of the objects, if you rotate your phone, you’ll
        see a scene like this:
    </p>
    <p>
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115.png">
            <img src="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-650x366.png"
            alt="" width="650" height="366" class="aligncenter size-large wp-image-170529"
            srcset="https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-650x366.png 650w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-480x270.png 480w, https://koenig-media.raywenderlich.com/uploads/2017/09/Screenshot_20170905-134115-266x151.png 266w"
            sizes="(max-width: 650px) 100vw, 650px">
        </a>
    </p>
    <p>
        You can move around the scene and watch as your Viking prepares to fire.
        There’s no stopping your Viking now! :]
    </p>
    <h2>
        Where to go from here?
    </h2>
    <p>
        You’ve just scratched the surface of using ARCore with OpenGL in Android
        Studio. For more information, check out the
        <a href="https://developers.google.com/ar/reference/java" target="_blank">
            ARCore API
        </a>
        page and the
        <a href="https://developers.google.com/ar/discover/" target="_blank">
            ARCore Overview
        </a>
        .
    </p>
    <p>
        The final app for this tutorial can be downloaded
        <a href="https://koenig-media.raywenderlich.com/uploads/2017/09/targetpractice-final-2.zip">
            here
        </a>
        .
    </p>
    <p>
        You can also use
        <a href="https://developers.google.com/ar/develop/unity/getting-started"
        target="_blank">
            ARCore with Unity
        </a>
        and
        <a href="https://developers.google.com/ar/develop/unreal/getting-started"
        target="_blank">
            ARCore with Unreal
        </a>
        . Since a good portion of the development with ARCore will likely rely
        on Unity, I highly recommended you also take a look at our
        <a href="https://www.raywenderlich.com/category/unity" target="_blank">
            Unity content
        </a>
        .
    </p>
    <p>
        In addition to Android, ARCore targets the web, and you can find more
        info
        <a href="https://developers.google.com/ar/develop/web/getting-started"
        target="_blank">
            here
        </a>
        . Finally, some cool demos made with ARCore (primarily with Unity) can
        be found at the
        <a href="https://experiments.withgoogle.com/ar" target="_blank">
            Google experiments site
        </a>
        .
    </p>
</div>