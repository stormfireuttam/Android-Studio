# Relative Layout

A Layout where the positions of the children can be described in relation to each other or to the parent.

Note that you cannot have a circular dependency between the size of the RelativeLayout and the position of its children. For example, you cannot have a RelativeLayout whose height is set to WRAP_CONTENT and a child set to ALIGN_PARENT_BOTTOM.

Note: In platform version 17 and lower, RelativeLayout was affected by a measurement bug that could cause child views to be measured with incorrect MeasureSpec values. (See MeasureSpec.makeMeasureSpec for more details).

This was triggered when a RelativeLayout container was placed in a scrolling container, such as a ScrollView or HorizontalScrollView. If a custom view not equipped to properly measure with the MeasureSpec mode UNSPECIFIED was placed in a RelativeLayout, this would silently work anyway as RelativeLayout would pass a very large AT_MOST MeasureSpec instead.

This behavior has been preserved for apps that set android:targetSdkVersion="17" or older in their manifest's uses-sdk tag for compatibility. Apps targeting SDK version 18 or newer will receive the correct behavior.

<img src="https://github.com/stormfireuttam/Android-Studio/blob/main/01%20Android%20Layouts/images/relativetoParent.jpg"/>

<img src="https://github.com/stormfireuttam/Android-Studio/blob/main/01%20Android%20Layouts/images/relativeToOther.jpg"/>
