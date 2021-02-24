# Shared Prefrences


Following is sample byte code on how to write Data in Shared Preferences:

```
// Storing data into SharedPreferences
SharedPreferences sharedPreferences = getSharedPreferences("MySharedPref",MODE_PRIVATE);

// Creating an Editor object to edit(write to the file)
SharedPreferences.Editor myEdit = sharedPreferences.edit();

// Storing the key and its value as the data fetched from edittext
myEdit.putString("name", name.getText().toString());
myEdit.putInt("age", Integer.parseInt(age.getText().toString()));

// Once the changes have been made,
// we need to commit to apply those changes made,
// otherwise, it will throw an error
myEdit.commit();

```
Following is the sample byte code on how to read Data in Shared Preferences:
```
// Retrieving the value using its keys the file name
// must be same in both saving and retrieving the data
SharedPreferences sh = getSharedPreferences("MySharedPref", MODE_APPEND);

// The value will be default as empty string because for
// the very first time when the app is opened, there is nothing to show
String s1 = sh.getString("name", "");
int a = sh.getInt("age", 0);

// We can then use the data
name.setText(s1);
age.setText(String.valueOf(a));

```

### Example to Demonstrate the use of Shared Preferences in Android

Below is the small demo for Shared Preferences. In this particular demo, there are two EditTexts, which save and retain the data entered earlier in them. This type of feature can be seen in applications with forms. Using Shared Preferences, the user will not have to fill in details again and again. Invoke the following code inside the activity_main.xml file to implement the UI:

```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
	xmlns:android="http://schemas.android.com/apk/res/android"
	xmlns:tools="http://schemas.android.com/tools"
	android:layout_width="match_parent"
	android:layout_height="match_parent"
	tools:context=".MainActivity"
	tools:ignore="HardcodedText">

	<TextView
		android:id="@+id/textview"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:layout_centerHorizontal="true"
		android:layout_marginTop="32dp"
		android:text="Shared Preferences Demo"
		android:textColor="@android:color/black"
		android:textSize="24sp" />

	<!--EditText to take the data from the user 
		and save the data in SharedPreferences-->
	<EditText
		android:id="@+id/edit1"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:layout_below="@+id/textview"
		android:layout_marginStart="16dp"
		android:layout_marginTop="8dp"
		android:layout_marginEnd="16dp"
		android:hint="Enter your Name"
		android:padding="10dp" />

	<!--EditText to take the data from the user and
		save the data in SharedPreferences-->
	<EditText
		android:id="@+id/edit2"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:layout_below="@+id/edit1"
		android:layout_marginStart="16dp"
		android:layout_marginTop="8dp"
		android:layout_marginEnd="16dp"
		android:hint="Enter your Age"
		android:padding="10dp" />

</RelativeLayout>

```

Working with the MainActivity.java file to handle the two of the EditText to save the data entered by the user inside the SharedPreferences. Below is the code for the MainActivity.java file. Comments are added inside the code to understand the code in more detail.

```
import androidx.appcompat.app.AppCompatActivity;

import android.content.SharedPreferences;
import android.os.Bundle;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

	private EditText name, age;

	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		name = findViewById(R.id.edit1);
		age = findViewById(R.id.edit2);
	}

	// Fetch the stored data in onResume()
	// Because this is what will be called
	// when the app opens again
	@Override
	protected void onResume() {
		super.onResume();

		// Fetching the stored data
		// from the SharedPreference
		SharedPreferences sh = getSharedPreferences("MySharedPref", MODE_PRIVATE);

		String s1 = sh.getString("name", "");
		int a = sh.getInt("age", 0);

		// Setting the fetched data
		// in the EditTexts
		name.setText(s1);
		age.setText(String.valueOf(a));
	}

	// Store the data in the SharedPreference
	// in the onPause() method
	// When the user closes the application
	// onPause() will be called
	// and data will be stored
	@Override
	protected void onPause() {
		super.onPause();

		// Creating a shared pref object
		// with a file name "MySharedPref" 
		// in private mode
		SharedPreferences sharedPreferences = getSharedPreferences("MySharedPref", MODE_PRIVATE);
		SharedPreferences.Editor myEdit = sharedPreferences.edit();

		// write all the data entered by the user in SharedPreference and apply
		myEdit.putString("name", name.getText().toString());
		myEdit.putInt("age", Integer.parseInt(age.getText().toString()));
		myEdit.apply();
	}
}

```
