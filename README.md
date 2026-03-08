Here is the **Markdown (.md) code** of the main content from your PDF so you can paste it directly into a `.md` file.

````md
# Android Practical Assignments

Source: Practical Details Explanation :contentReference[oaicite:0]{index=0}

---

# Assignment 1

## 1. Create Android Project
- Open **Android Studio**
- Click **New Project → Empty Activity**
- App Name: **StudentDetails**
- Language: **Java**
- Click **Finish**

---

## 2. Design Layout

**activity_main.xml**

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:orientation="vertical"
 android:padding="20dp">

 <TextView
 android:text="Student Details"
 android:textSize="20sp"
 android:textStyle="bold"
 android:layout_gravity="center"
 android:layout_marginBottom="20dp"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"/>

 <GridLayout
 android:layout_width="match_parent"
 android:layout_height="wrap_content"
 android:columnCount="2"
 android:rowCount="3"
 android:alignmentMode="alignMargins"
 android:useDefaultMargins="true">

 <TextView
 android:text="Student Name:"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"/>

 <EditText
 android:id="@+id/etName"
 android:hint="Enter Name"
 android:layout_width="200dp"
 android:layout_height="wrap_content"/>

 <TextView
 android:text="Class:"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"/>

 <EditText
 android:id="@+id/etClass"
 android:hint="Enter Class"
 android:layout_width="200dp"
 android:layout_height="wrap_content"/>

 <TextView
 android:text="Roll No:"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"/>

 <EditText
 android:id="@+id/etRoll"
 android:hint="Enter Roll No"
 android:inputType="number"
 android:layout_width="200dp"
 android:layout_height="wrap_content"/>

 </GridLayout>

</LinearLayout>
````

---

## 3. MainActivity.java

```java
package com.example.studentdetails;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {

 @Override
 protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
  setContentView(R.layout.activity_main);
 }

}
```

---

## 4. Execute Application

Steps:

1. Open **AVD Manager**
2. Click **Run ▶**
3. Select **Emulator**
4. Application launches

---

# Assignment 2

## Activity Life Cycle

Methods used:

* onCreate()
* onStart()
* onResume()
* onPause()
* onStop()
* onRestart()
* onDestroy()

---

## MainActivity.java

```java
package com.example.activitylifecycle;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.util.Log;

public class MainActivity extends AppCompatActivity {

 @Override
 protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
  setContentView(R.layout.activity_main);
  Log.d("MyActivity", "onCreate() method called");
 }

 @Override
 protected void onStart() {
  super.onStart();
  Log.d("MyActivity", "onStart() method called");
 }

 @Override
 protected void onResume() {
  super.onResume();
  Log.d("MyActivity", "onResume() method called");
 }

 @Override
 protected void onPause() {
  super.onPause();
  Log.d("MyActivity", "onPause() method called");
 }

 @Override
 protected void onStop() {
  super.onStop();
  Log.d("MyActivity", "onStop() method called");
 }

 @Override
 protected void onRestart() {
  super.onRestart();
  Log.d("MyActivity", "onRestart() method called");
 }

 @Override
 protected void onDestroy() {
  super.onDestroy();
  Log.d("MyActivity", "onDestroy() method called");
 }

}
```

---

# Hello Intent Example

## activity_main.xml

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 android:gravity="center"
 android:orientation="vertical">

 <Button
 android:id="@+id/btnNext"
 android:text="Next"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"/>

</LinearLayout>
```

---

## MainActivity.java

```java
package com.example.hellointentapp;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.content.Intent;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {

 Button btnNext;

 @Override
 protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
  setContentView(R.layout.activity_main);

  btnNext = findViewById(R.id.btnNext);

  btnNext.setOnClickListener(new View.OnClickListener() {
   @Override
   public void onClick(View view) {

    Intent intent = new Intent(MainActivity.this, SecondActivity.class);
    intent.putExtra("message","Hello from Main Activity.");
    startActivity(intent);

   }
  });

 }

}
```

---

## SecondActivity.java

```java
package com.example.hellointentapp;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.content.Intent;
import android.widget.TextView;

public class SecondActivity extends AppCompatActivity {

 TextView tvMessage;

 @Override
 protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
  setContentView(R.layout.activity_second);

  tvMessage = findViewById(R.id.tvMessage);

  Intent intent = getIntent();
  String msg = intent.getStringExtra("message");

  tvMessage.setText(msg);

 }

}
```

---

# Output

* First Screen → Button
* Click Button → Second Activity
* Message displayed

```

---

✅ If you want, I can also give you a **perfect GitHub-style README.md version (cleaner for exams or notes)** which will look **very professional**.
```
