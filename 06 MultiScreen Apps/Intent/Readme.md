# Intent in Android

An intent is to perform an action on the screen. It is mostly used to start activity, send broadcast receiver,start services and send message between two activities. There are two intents available in android as Implicit Intents and Explicit Intents. Here is a sample example to start new activity with old activity.

Step 1 − Create a new project in Android Studio,go to File ⇒ New Project and fill all required details to create a new project.

Step 2 − Add the following code to res/layout/activity_main.xml. (First Activity layout)
```
<?xml version = "1.0" encoding = "utf-8"?>
<android.support.constraint.ConstraintLayout
xmlns:android = "http://schemas.android.com/apk/res/android" xmlns:tools = "http://schemas.android.com/tools" android:layout_width = "match_parent"
   android:layout_height = "match_parent">
<LinearLayout
   android:layout_width = "match_parent"
   android:layout_height = "match_parent"
   android:gravity = "center"
   android:orientation = "vertical">
   <Button
      android:layout_width = "wrap_content"
      android:layout_height = "wrap_content"
      android:text = "Send to another activitys"
      android:id = "@+id/send"/>
</LinearLayout>
</android.support.constraint.ConstraintLayout>
```
Step 3 − Create a new layout in res/layout/ folder and add the following code to res/layout/activity_main.xml. (Second Activity layout )
```
<?xml version = "1.0" encoding = "utf-8"?>
<android.support.constraint.ConstraintLayout xmlns:android = "http://schemas.android.com/apk/res/android"
   xmlns:app = "http://schemas.android.com/apk/res-auto"
   xmlns:tools = "http://schemas.android.com/tools"
   android:layout_width = "match_parent"
   android:layout_height = "match_parent"
   android:layout_centerInParent = "true"
   android:layout_centerHorizontal = "true"
   tools:context = ".SecondActivity">
   <TextView
      android:id = "@+id/data"
      android:textSize = "20sp"
      android:layout_width = "wrap_content"
      android:layout_height = "wrap_content" />
</android.support.constraint.ConstraintLayout>
```
Step 4 − Add the following code to src/MainActivity.java (First activity)
```
import android.content.Intent;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.View;
import android.widget.Button;
public class MainActivity extends AppCompatActivity {
   @Override
   protected void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      setContentView(R.layout.activity_main);
      Button send = findViewById(R.id.send);
      send.setOnClickListener(new View.OnClickListener() {
         @Override
         public void onClick(View v) {
            Intent send = new Intent(MainActivity.this, SecondActivity.class);
            startActivity(send);
         }
      });
   }
}
```
In the above activity we are starting new activity using startActivity(). To start activity, we need to create new intent and we have to pass current activity and new activity as shown below.
```
Intent send = new Intent(MainActivity.this, SecondActivity.class);
startActivity(send);
```
Step 4 − Create a new activity and add the following code to src/SecondActivity.java (Second Activity)
```
package com.example.andy.myapplication;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.TextView;
public class SecondActivity extends AppCompatActivity {
   @Override
   protected void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      setContentView(R.layout.activity_second);
      TextView data=findViewById(R.id.data);
      data.setText("This is second activity");
   }
}
```
Step5 − Add the following code to AndroidManifest.xml.
```
<?xml version = "1.0" encoding = "utf-8"?>
<manifest xmlns:android = "http://schemas.android.com/apk/res/android"
   package = "com.example.andy.myapplication">
   <application
      android:allowBackup = "true"
      android:icon = "@mipmap/ic_launcher"
      android:label = "@string/app_name"
      android:roundIcon = "@mipmap/ic_launcher_round"
      android:supportsRtl = "true"
      android:theme = "@style/AppTheme">
      <activity android:name = ".MainActivity">
         <intent-filter>
            <action android:name = "android.intent.action.MAIN" />
            <category android:name = "android.intent.category.LAUNCHER" />
         </intent-filter>
      </activity>
      <activity android:name = ".SecondActivity"></activity>
   </application>
</manifest>
```
In the above code, we have declare MainActivity and SecondActivity as shown below.
```
<activity android:name = ".SecondActivity"></activity>
<activity android:name = ".MainActivity""></activity>
```
