ProgressedView
==============

ProgressedView provides you to show progress to user, when clicks any view. After done your task at background reverse it back to view again. This view extends RelativeLayout, so it easily implement in xml or code. 

ProgressedView can host only one child. Becuase it adds another view, which contains progressbar and seekbar, just with exact layoutparams with source view. 

Implementation
--------------

```xml
<com.yayandroid.progressedview.ProgressedView
        android:id="@+id/progressed"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true"
        app:animationTime="1000"
        app:animationType="swipe_top_to_bottom"
        app:bringTargetFront="false"
        app:interpolation="bounce"
        app:defaultBackgroundColor="#0072C3"
        app:progressType="just_indeterminate"
        app:remainSteady="false"
        app:reversingAnimationType="swipe_top_to_bottom" >

        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_centerInParent="true"
            android:padding="10dp"
            android:text="@string/button_text" />
    </com.yayandroid.progressedview.ProgressedView>
```

You can specify almost everything in xml, and because it extends from RelativeLayout you can put your view inside it as easy as it is Relative. You don't have to give any of these specifications, but otherwise library will be using default variables. All variables have setter methods, so you can modify themn in code.

There are two important flags:

1- remainSteady, if you set this true then your source view will not move when progress view comes. This is pretty if you're using one of swipe animations, otherwise it doesn't even seem any different.

2- bringTargetFront, if this is set true that means whichever view will come, it will come to front. So if you set remainSteady flag true and check out one of swipe animation you will not be able to see reversing animation becuase progress view is top on your source view, setting this true solve that issue. 

Animation Types
---------------

```java
public enum AnimationType {
  	SWIPE_LEFT_TO_RIGHT, SWIPE_RIGHT_TO_LEFT, SWIPE_TOP_TO_BOTTOM, SWIPE_BOTTOM_TO_TOP, 
    SCALE_IN, SCALE_OUT, ALPHA
}
```

You can easily set animation types for changing view to progress, and reversing back to view. The animations don't have to be same, you can choose them seperately. And if you choose, only view to progress animation then library will decide what reversing animation should be.

Progress Style
--------------

And also possible to change progress style, which is more limited for now:

```java
public enum ProgressType {
  	JUST_INDETERMINATE, JUST_SEEK, SEEK_AND_INDETERMINATE
}
```

You can choose whether you need to display progress with seekbar or just with indeterminated progress bar. To display seek bar, you can check out examples.

Interpolations
--------------

You can also specify interpolations which they are defined as attributes so you can simply implement them from xml, or you can set them from code as well. Used interpolatins:

```java
AccelerateInterpolator, 
DecelerateInterpolator, 
AccelerateDecelerateInterpolator, 
AnticipateInterpolator, 
OvershootInterpolator, 
AnticipateOvershootInterpolator, 
BounceInterpolator, 
LinearInterpolator, // As default 
CycleInterpolator // Not so effective for this library
```

Customization
-------------

You can customize all parts of this view, and even just from xml. 

You can change background color of default progress view. Or background and progress colors of default seek bar. 

If you want to show a custom progressbar, or custom seekbar, or anything else. Just create a layout and point it to progressedView. It will switch your custom view with the animations you choose. 

```xml
app:progressLayout="@layout/custom_progress_layout"
```

Link
----
Demo is available on [GooglePlayStore] [GooglePlayStoreUrl]
[GooglePlayStoreUrl]: https://play.google.com/store/apps/details?id=com.yayandroid.progressedview

Inspired by [this project] [InspireUrl]
[InspireUrl]: http://lab.hakim.se/ladda/
