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
