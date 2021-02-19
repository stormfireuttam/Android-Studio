# Linear Layout

<img src="https://github.com/stormfireuttam/Android-Studio/blob/main/01%20Android%20Layouts/images/ViewGroup.jpg"/>
A layout that arranges other views either horizontally in a single column or vertically in a single row.

The following snippet shows how to include a linear layout in your layout XML file:

```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
   android:layout_width="match_parent"
   android:layout_height="match_parent"
   android:paddingLeft="16dp"
   android:paddingRight="16dp"
   android:orientation="horizontal"
   android:gravity="center">

   <!-- Include other widget or layout tags here. These are considered
           "child views" or "children" of the linear layout -->

 </LinearLayout>
```
Set ***android:orientation*** to specify whether child views are displayed in a row or column.

To control how linear layout aligns all the views it contains, set a value for android:gravity. For example, the snippet above sets android:gravity to "center". The value you set affects both horizontal and vertical alignment of all child views within the single row or column.

You can set android:layout_weight on individual child views to specify how linear layout divides remaining space amongst the views it contains. See the Linear Layout guide for an example.

<img src="https://github.com/stormfireuttam/Android-Studio/blob/main/01%20Android%20Layouts/images/LayoutWeight.jpg"/>
