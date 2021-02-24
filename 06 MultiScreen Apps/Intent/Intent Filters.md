# What are Intent Filters in Android?

An intent filter is an instance of the IntentFilter class. Intent filters are helpful while using implicit intents, It is not going to handle in java code, we have to set it up in AndroidManifest.xml. Android must know what kind of intent it is launching so intent filters give the information to android about intent and actions.

Before launching intent, android going to do action test, category test and data test. This example demonstrate about how to use intent filters in android.

**Step 1** − Create a new project in Android Studio,go to File ⇒ New Project and fill all required details to create a new project.

**Step 2** − Add the following code to res/layout/activity_main.xml.
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
   xmlns:app="http://schemas.android.com/apk/res-auto"
   xmlns:tools="http://schemas.android.com/tools"
   android:layout_width="match_parent"
   android:layout_height="match_parent"
   android:gravity="center"
   android:orientation="vertical"
   tools:context=".MainActivity">
   <Button
      android:id="@+id/buton"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:text="intent filter button" />
</LinearLayout>
```
In the above, we have given a button when you click on button it will show intent with action.

**Step 3** − Add the following code to src/MainActivity.java
```
package com.example.andy.myapplication;
import android.content.Intent;
import android.os.Bundle;
import android.support.v7.app.AppCompatActivity;
import android.view.View;
import android.widget.Button;
import android.widget.RadioButton;
public class MainActivity extends AppCompatActivity {
   RadioButton radioButton;
   @Override
   protected void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      setContentView(R.layout.activity_main);
      final Button button = findViewById(R.id.buton);
      button.setOnClickListener(new View.OnClickListener() {
         @Override
         public void onClick(View v) {
            Intent intent = new Intent(Intent.ACTION_SEND);
            intent.setType("message/rfc822");
            intent.putExtra(Intent.EXTRA_EMAIL, new String[]{"contact@tutorialspoint.com"});
            intent.putExtra(Intent.EXTRA_SUBJECT, "Welcome to tutorialspoint.com");
            startActivity(Intent.createChooser(intent, "Choose default Mail App"));
         }
      });
}
}
```
In the above when user click on button it will call intent using ACTION_SEND and will set type as message/rfc882. Now we passed out email id and subject message.

**Step 4** − Add the following code to manifest.xml
```
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
   package="com.example.andy.myapplication">
   <uses-permission android:name="android.permission.INTERNET" />
   <application
      android:allowBackup="true"
      android:icon="@mipmap/ic_launcher"
      android:label="@string/app_name"
      android:roundIcon="@mipmap/ic_launcher_round"
      android:supportsRtl="true"
      android:theme="@style/AppTheme">
      <activity android:name=".MainActivity">
         <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
            <action android:name="android.intent.action.SEND" />
            <category android:name="android.intent.category.DEFAULT" />
            <data android:mimeType="message/rfc822" />
         </intent-filter>
      </activity>
</application>
</manifest>
```
