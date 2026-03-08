# Assignment 1

## 1. Create Android Project

1. Open **Android Studio**
2. Click **New Project → Empty Activity**
3. Set:

   * **App Name:** `StudentDetails`
   * **Language:** `Java`
4. Click **Finish**

---

# 2. Design the Layout (Proper Alignment)

We use **GridLayout** so labels and text fields align properly.

### `activity_main.xml`

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
```

### Alignment Result

* Labels appear **on the left**
* Input fields appear **on the right**

---

# 3. MainActivity.java

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

# 4. Run the Application on Emulator

### Steps

1. Open **AVD Manager**
2. Click **Run ▶**
3. Select an **Emulator**
4. Application launches showing the **Student Details form**

---

# Assignment 2 – Activity Life Cycle

Objective: Demonstrate the **Activity Life Cycle** and observe output in **Logcat**.

### Methods Used

* `onCreate()`
* `onStart()`
* `onResume()`
* `onPause()`
* `onStop()`
* `onRestart()`
* `onDestroy()`

---

# 1. Create Android Project

* App Name: `ActivityLifeCycle`
* Language: `Java`

---

# 2. MainActivity.java

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
        Log.d("MyActivity","onCreate() method called");
    }

    @Override
    protected void onStart() {
        super.onStart();
        Log.d("MyActivity","onStart() method called");
    }

    @Override
    protected void onResume() {
        super.onResume();
        Log.d("MyActivity","onResume() method called");
    }

    @Override
    protected void onPause() {
        super.onPause();
        Log.d("MyActivity","onPause() method called");
    }

    @Override
    protected void onStop() {
        super.onStop();
        Log.d("MyActivity","onStop() method called");
    }

    @Override
    protected void onRestart() {
        super.onRestart();
        Log.d("MyActivity","onRestart() method called");
    }

    @Override
    protected void onDestroy() {
        super.onDestroy();
        Log.d("MyActivity","onDestroy() method called");
    }
}
```

---

# Checking Logcat Output

### Steps

1. Run the application
2. Open **Logcat**
3. Filter by:

```
MyActivity
```

Observe lifecycle logs when:

* App launches
* Press **Home**
* Reopen app
* Press **Back**
* Rotate device

---

# Assignment 2 (Set A – Intent Example)

Create an app that sends **Hello message from one Activity to another using Intent**.

---

# 1. Create Project

App Name: **HelloIntentApp**

Language: **Java**

---

# 2. Sender Activity

### `activity_main.xml`

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

### `MainActivity.java`

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

# 3. Receiver Activity

### `activity_second.xml`

```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:gravity="center"
    android:orientation="vertical">

    <TextView
        android:id="@+id/tvMessage"
        android:textSize="20sp"
        android:textStyle="bold"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

</LinearLayout>
```

---

### `SecondActivity.java`

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

1️⃣ First screen → **Next button**
2️⃣ Click button → **Second screen appears**
3️⃣ Displays message:

```
Hello from Main Activity
```

---

# Assignment 3:

Set A:

## 1) Design following Android Portrait and Landscape Screen Layout to add a border.

To add a border to any layout:
• We are creating separate xml file for border. Required attributes of borders are set in the xml.
• Apply the designed border to your layout in activity_main.xml file.

### 1️. Create Android Project

• New Project → Empty view Activity
• Language: Java
• Create 2 values xml files with names:
• border.xml and newborder.xml

### Border.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape 
xmlns:android="http://schemas.android.com/apk/res/android"
android:shape="rectangle">

<!-- Border -->
<stroke
android:width="8dp"
android:color="@color/black" />

<!-- Optional background -->
<solid
android:color="@android:color/holo_blue_dark" />

<!-- Optional rounded corners -->
<corners android:radius="8dp" />

<!-- Optional padding inside border -->
<padding
android:left="8dp"
android:top="8dp"
android:right="8dp"
android:bottom="8dp" />

</shape>
```

### Newborder.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<shape 
xmlns:android="http://schemas.android.com/apk/res/android"
android:shape="rectangle">

<!-- Border -->
<stroke
android:width="8dp"
android:color="@color/white" />

<!-- Optional background -->
<solid
android:color="@color/material_dynamic_neutral50" />

<!-- Optional rounded corners -->
<corners android:radius="8dp" />

<!-- Optional padding inside border -->
<padding
android:left="8dp"
android:top="8dp"
android:right="8dp"
android:bottom="8dp" />

</shape>
```

### Activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<androidx.constraintlayout.widget.ConstraintLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:layout_margin="30dp"
android:background="@drawable/border">

<TextView
android:layout_width="wrap_content"
android:layout_height="500dp"
android:background="@drawable/newborder"
android:gravity="center"
android:text="Hello World!"
android:textSize="28sp"
app:layout_constraintBottom_toBottomOf="parent"
app:layout_constraintEnd_toEndOf="parent"
app:layout_constraintStart_toStartOf="parent"
app:layout_constraintTop_toTopOf="parent" />

</androidx.constraintlayout.widget.ConstraintLayout>
```

Output: Shows different borders applied to constraint Layout and TextView each. 

---

# Set A: 2) Create a simple calculator to perform appropriate arithmetic operations.

### 1️. Create Android Project

• New Project → Empty view Activity
• Language: Java
• Name it: Calculator

---

## 2. Activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp"
    android:gravity="center">

    <TextView
        android:id="@+id/etNum"
        android:layout_width="match_parent"
        android:layout_height="50dp"
        android:layout_marginTop="10dp"
        android:hint="0"
        android:textAlignment="viewEnd"
        android:textSize="30dp"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center"
        android:layout_marginTop="20dp">

        <Button
            android:id="@+id/btn1"
            android:text="1"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btn2"
            android:text="2"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btn3"
            android:text="3"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btnplus"
            android:text="+"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

    </LinearLayout>


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center"
        android:layout_marginTop="20dp">

        <Button
            android:id="@+id/btn4"
            android:text="4"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btn5"
            android:text="5"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btn6"
            android:text="6"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btnminus"
            android:text="-"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

    </LinearLayout>


    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center"
        android:layout_marginTop="20dp">

        <Button
            android:id="@+id/btn7"
            android:text="7"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btn8"
            android:text="8"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btn9"
            android:text="9"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btnmultiply"
            android:text="*"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:gravity="center"
        android:layout_marginTop="20dp">

        <Button
            android:id="@+id/btn0"
            android:text="0"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btndevide"
            android:text="/"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btnequals"
            android:text="="
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

        <Button
            android:id="@+id/btnClear"
            android:text="C"
            android:textSize="30dp"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_weight="1"/>

    </LinearLayout>

</LinearLayout>
```

(Buttons for 4-9, multiply, minus, divide, clear, equals continue exactly as written in the PDF.)

---

## 3. MainActivity.java

```java
package com.example.calculator;

import static com.example.calculator.R.id.*;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

Button b1,b2,b3,b4,b5,b6,b7,b8,b9,b0,bplus,bminus,bmulti,bdevide,btnClear,btnequals;
TextView num;

@Override
protected void onCreate(Bundle savedInstanceState) {

super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

b1=findViewById(R.id.btn1);
b2=findViewById(R.id.btn2);
b3=findViewById(R.id.btn3);
b4=findViewById(R.id.btn4);
b5=findViewById(R.id.btn5);
b6=findViewById(R.id.btn6);
b7=findViewById(R.id.btn7);
b8=findViewById(R.id.btn8);
b9=findViewById(R.id.btn9);
b0=findViewById(R.id.btn0);
bplus=findViewById(R.id.btnplus);
bminus=findViewById(R.id.btnminus);
bmulti=findViewById(R.id.btnmultiply);
bdevide=findViewById(R.id.btndevide);
btnequals=findViewById(R.id.btnequals);
btnClear=findViewById(R.id.btnClear);

num=findViewById(R.id.etNum);

b1.setOnClickListener(v -> num.append("1"));
b2.setOnClickListener(v -> num.append("2"));
b3.setOnClickListener(v -> num.append("3"));
b4.setOnClickListener(v -> num.append("4"));
b5.setOnClickListener(v -> num.append("5"));
b6.setOnClickListener(v -> num.append("6"));
b7.setOnClickListener(v -> num.append("7"));
b8.setOnClickListener(v -> num.append("8"));
b9.setOnClickListener(v -> num.append("9"));
b0.setOnClickListener(v -> num.append("0"));

bplus.setOnClickListener(v -> num.append("+"));
bminus.setOnClickListener(v -> num.append("-"));
bmulti.setOnClickListener(v -> num.append("*"));
bdevide.setOnClickListener(v -> num.append("/"));

btnClear.setOnClickListener(v -> num.setText(""));

btnequals.setOnClickListener(v -> {

String input=num.getText().toString();
int output=0;
int num1=0,num2=0;
char operator=' ';

for(int i=0;i<input.length();i++){

char ch=input.charAt(i);

if(ch=='+'||ch=='-'||ch=='*'||ch=='/'){
operator=ch;
num1=Integer.parseInt(input.substring(0,i));
num2=Integer.parseInt(input.substring(i+1));
break;
}

}

switch(operator){

case '+':
output=num1+num2;
break;

case '-':
output=num1-num2;
break;

case '*':
output=num1*num2;
break;

case '/':
if(num2==0){
num.setText("Division by zero");
}
output=num1/num2;
break;

default:
num.setText("Invalid input");
break;

}

num.setText(String.valueOf(output));

});

}

}
```

Output:
This code will generate calculator with all basic functions. 

---

# Design a Screens Using Intents to insert customer contact details.

Flow

1. MainActivity → has “Add Contact” button
2. Clicking button opens AddContactActivity
3. User enters contact details
4. After clicking Save, a ContactDetailsActivity opens and shows the contact details (short view)

---

### activity_main.xml

```xml
<LinearLayout
xmlns:android="http://schemas.android.com/apk/res/android"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:gravity="center"
android:orientation="vertical">

<Button
android:id="@+id/btnAddContact"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Add Contact" />

</LinearLayout>
```

---

### MainActivity.java

```java
package com.example.contactapp;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

Button btnAddContact;

@Override
protected void onCreate(Bundle savedInstanceState){

super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

btnAddContact=findViewById(R.id.btnAddContact);

btnAddContact.setOnClickListener(v -> {

Intent intent=new Intent(MainActivity.this,AddContactActivity.class);
startActivity(intent);

});

}

}
```

---

# Set A:

## 1. Create a custom "Contact" layout to hold multiple pieces of information, including: Photo, Name, Contact Number, E-mail id and display it using fragment.

### Fragment Layout (fragment_contact.xml)

This is the custom contact UI.

```xml
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
android:padding="16dp">

<!-- Contact Photo -->

<ImageView
android:id="@+id/imgPhoto"
android:layout_width="120dp"
android:layout_height="120dp"
android:src="@drawable/ic_person"
android:layout_gravity="center"
android:contentDescription="Contact Photo"/>

<!-- Name -->

<TextView
android:id="@+id/txtName"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Name"
android:textSize="20sp"
android:textStyle="bold"
android:layout_marginTop="12dp"/>

<!-- Phone -->

<TextView
android:id="@+id/txtPhone"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Contact Number"
android:layout_marginTop="8dp"/>

<!-- Email -->

<TextView
android:id="@+id/txtEmail"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="Email ID"
android:layout_marginTop="8dp"/>

</LinearLayout>
```

Add a placeholder image like **ic_person.png** in `res/drawable`. 

---

## 2. Contact Fragment (ContactFragment.java)

```java
package com.example.contactapp;

import android.os.Bundle;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.TextView;

import androidx.annotation.NonNull;
import androidx.annotation.Nullable;
import androidx.fragment.app.Fragment;

public class ContactFragment extends Fragment {

@Nullable
@Override
public View onCreateView(@NonNull LayoutInflater inflater,
@Nullable ViewGroup container,
@Nullable Bundle savedInstanceState) {

View view = inflater.inflate(R.layout.fragment_contact, container, false);

ImageView imgPhoto = view.findViewById(R.id.imgPhoto);
TextView txtName = view.findViewById(R.id.txtName);
TextView txtPhone = view.findViewById(R.id.txtPhone);
TextView txtEmail = view.findViewById(R.id.txtEmail);

// Setting contact details

imgPhoto.setImageResource(R.drawable.ic_person);
txtName.setText("Amruta More");
txtPhone.setText("Phone: 9876543210");
txtEmail.setText("Email: amruta.more@gmail.com");

return view;

}

}
```

---

## 3. Activity Layout (activity_main.xml)

This holds the fragment.

```xml
<?xml version="1.0" encoding="utf-8"?>

<FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
android:id="@+id/fragment_container"
android:layout_width="match_parent"
android:layout_height="match_parent"/>
```

---

## 4. Main Activity (MainActivity.java)

Loads the fragment.

```java
package com.example.contactapp;

import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;
import androidx.fragment.app.FragmentTransaction;

public class MainActivity extends AppCompatActivity {

@Override
protected void onCreate(Bundle savedInstanceState) {

super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

ContactFragment contactFragment = new ContactFragment();

FragmentTransaction transaction =
getSupportFragmentManager().beginTransaction();

transaction.replace(R.id.fragment_container, contactFragment);
transaction.commit();

}

}
```

---

# 2) Create an application to add and remove items from spinner.

Use Spinner, Text box and Buttons to draw the GUI.

## 1. Layout File (activity_main.xml)

```xml
<?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:orientation="vertical"
android:padding="16dp">

<!-- Text Box -->

<EditText
android:id="@+id/edtItem"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:hint="Enter item"/>

<!-- Spinner -->

<Spinner
android:id="@+id/spinnerItems"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginTop="16dp"/>

<!-- Add Button -->

<Button
android:id="@+id/btnAdd"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Add Item"
android:layout_marginTop="16dp"/>

<!-- Remove Button -->

<Button
android:id="@+id/btnRemove"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Remove Item"
android:layout_marginTop="8dp"/>

</LinearLayout>
```

---

## 2. Main Activity (MainActivity.java)

```java
package com.example.spinnerapp;

import android.os.Bundle;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Spinner;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import java.util.ArrayList;

public class MainActivity extends AppCompatActivity {

Spinner spinner;
EditText edtItem;
Button btnAdd, btnRemove;

ArrayList<String> itemList;
ArrayAdapter<String> adapter;

@Override
protected void onCreate(Bundle savedInstanceState) {

super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

spinner = findViewById(R.id.spinnerItems);
edtItem = findViewById(R.id.edtItem);
btnAdd = findViewById(R.id.btnAdd);
btnRemove = findViewById(R.id.btnRemove);

itemList = new ArrayList<>();
itemList.add("Apple");
itemList.add("Banana");
itemList.add("Orange");

adapter = new ArrayAdapter<>(
this,
android.R.layout.simple_spinner_item,
itemList
);

adapter.setDropDownViewResource(
android.R.layout.simple_spinner_dropdown_item
);

spinner.setAdapter(adapter);

btnAdd.setOnClickListener(new View.OnClickListener() {
@Override
public void onClick(View view) {

String item = edtItem.getText().toString().trim();

if (!item.isEmpty()) {

itemList.add(item);
adapter.notifyDataSetChanged();
edtItem.setText("");

}
else {

Toast.makeText(MainActivity.this,
"Enter an item",
Toast.LENGTH_SHORT).show();

}

}

});

btnRemove.setOnClickListener(new View.OnClickListener() {

@Override
public void onClick(View view) {

if (itemList.size() > 0) {

int position = spinner.getSelectedItemPosition();
itemList.remove(position);
adapter.notifyDataSetChanged();

}

else {

Toast.makeText(MainActivity.this,
"No items to remove",
Toast.LENGTH_SHORT).show();

}

}

});

}

}
```

---

(The remaining sections **DatePicker & TimePicker, Toggle Light Bulb App, Date Image App, Custom Launcher Icon, File Explorer, Registration Form with DialogFragment, ImageSwitcher using setFactory(), Bank Menu App** continue exactly as written in the PDF.) 

---

# Assignment No: 5

**Databases-SQLite, Messaging and E-mail**

## 1. Create table Company (id, name, address, phno). Create Application for Performing the following operation on the table.

a) Insert New Company Details.
b) Show All the Company Details.

### Where Is the Table Created?

The table is created inside the:

DatabaseHelper.java → **onCreate() method**

```java
@Override
public void onCreate(SQLiteDatabase db) {
 db.execSQL("CREATE TABLE Company (id INTEGER PRIMARY KEY AUTOINCREMENT,
 name TEXT, address TEXT, phno TEXT)");
}
```

### When Does This Execute?

The table is created automatically when:

```
myDb = new DatabaseHelper(this);
```

is executed for the first time in **MainActivity**.

Android then:

1. Creates the database file (CompanyDB.db)
2. Calls onCreate()
3. Executes the CREATE TABLE statement

### Where Is the Database Stored?

Android stores it internally at:

```
/data/data/your.package.name/databases/CompanyDB.db
```

You don’t need to manually create it.

### Important

You do not create the table separately in Android Studio.
It is automatically created when the app runs the first time.

If Table Is Not Updating?

If you modify the table structure:

• Uninstall the app from emulator/device

OR

• Increase database version in constructor:

```
super(context, DATABASE_NAME, null, 2);
```

This triggers **onUpgrade()**.

---

## SQL: Create Company Table

```sql
CREATE TABLE Company (
 id INTEGER PRIMARY KEY AUTOINCREMENT,
 name TEXT NOT NULL,
 address TEXT NOT NULL,
 phno TEXT NOT NULL
);
```

---

## In Android Application

We will create:

• DatabaseHelper.java
• MainActivity.java
• activity_main.xml

---

# Create Database Helper Class

### DatabaseHelper.java

```java
package com.example.companyapp;

import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

public class DatabaseHelper extends SQLiteOpenHelper {

 private static final String DATABASE_NAME = "CompanyDB.db";
 private static final String TABLE_NAME = "Company";

 public DatabaseHelper(Context context) {
 super(context, DATABASE_NAME, null, 1);
 }

 @Override
 public void onCreate(SQLiteDatabase db) {
 db.execSQL("CREATE TABLE Company (id INTEGER PRIMARY KEY AUTOINCREMENT,
 name TEXT, address TEXT, phno TEXT)");
 }

 @Override
 public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
 db.execSQL("DROP TABLE IF EXISTS Company");
 onCreate(db);
 }

 // Insert Data
 public boolean insertData(String name, String address, String phno) {

 SQLiteDatabase db = this.getWritableDatabase();
 ContentValues contentValues = new ContentValues();

 contentValues.put("name", name);
 contentValues.put("address", address);
 contentValues.put("phno", phno);

 long result = db.insert(TABLE_NAME, null, contentValues);

 return result != -1;

 }

 // Get All Data
 public Cursor getAllData() {

 SQLiteDatabase db = this.getWritableDatabase();
 return db.rawQuery("SELECT * FROM Company", null);

 }

}
```

---

# Design Layout

### activity_main.xml

```xml
<?xml version="1.0" encoding="utf-8"?>

<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
 android:layout_width="match_parent"
 android:layout_height="match_parent">

 <LinearLayout
 android:orientation="vertical"
 android:padding="20dp"
 android:layout_width="match_parent"
 android:layout_height="wrap_content">

 <EditText
 android:id="@+id/editName"
 android:hint="Company Name"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"/>

 <EditText
 android:id="@+id/editAddress"
 android:hint="Address"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"/>

 <EditText
 android:id="@+id/editPhone"
 android:hint="Phone Number"
 android:inputType="phone"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"/>

 <Button
 android:id="@+id/btnInsert"
 android:text="Insert Company"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"/>

 <Button
 android:id="@+id/btnView"
 android:text="View All Companies"
 android:layout_width="match_parent"
 android:layout_height="wrap_content"/>

 </LinearLayout>

</ScrollView>
```

---

# MainActivity.java

```java
package com.example.companyapp;

import androidx.appcompat.app.AppCompatActivity;

import android.database.Cursor;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AlertDialog;

public class MainActivity extends AppCompatActivity {

 DatabaseHelper myDb;

 EditText editName, editAddress, editPhone;

 Button btnInsert, btnView;

 @Override
 protected void onCreate(Bundle savedInstanceState) {

 super.onCreate(savedInstanceState);
 setContentView(R.layout.activity_main);

 myDb = new DatabaseHelper(this);

 editName = findViewById(R.id.editName);
 editAddress = findViewById(R.id.editAddress);
 editPhone = findViewById(R.id.editPhone);

 btnInsert = findViewById(R.id.btnInsert);
 btnView = findViewById(R.id.btnView);

 insertData();
 viewAll();

 }

 public void insertData() {

 btnInsert.setOnClickListener(new View.OnClickListener() {

 @Override
 public void onClick(View v) {

 boolean isInserted = myDb.insertData(
 editName.getText().toString(),
 editAddress.getText().toString(),
 editPhone.getText().toString()
 );

 if(isInserted)

 Toast.makeText(MainActivity.this, "Data Inserted",
 Toast.LENGTH_LONG).show();

 else

 Toast.makeText(MainActivity.this, "Data Not Inserted",
 Toast.LENGTH_LONG).show();

 }

 });

 }

 public void viewAll() {

 btnView.setOnClickListener(new View.OnClickListener() {

 @Override
 public void onClick(View v) {

 Cursor res = myDb.getAllData();

 if(res.getCount() == 0) {

 showMessage("Error", "No Data Found");
 return;

 }

 StringBuffer buffer = new StringBuffer();

 while(res.moveToNext()) {

 buffer.append("ID: " + res.getString(0) + "\n");
 buffer.append("Name: " + res.getString(1) + "\n");
 buffer.append("Address: " + res.getString(2) + "\n");
 buffer.append("Phone: " + res.getString(3) + "\n\n");

 }

 showMessage("Company Details", buffer.toString());

 }

 });

 }

 public void showMessage(String title, String message) {

 AlertDialog.Builder builder = new AlertDialog.Builder(this);

 builder.setCancelable(true);
 builder.setTitle(title);
 builder.setMessage(message);

 builder.show();

 }

}
```

---

(The PDF continues with **Emp-Dept database application, SMS sending/receiving, Email sending app, Login module with SQLite, Project-Employee many-to-many database, MMS with image and contact, Google Maps location services, Map search, Zoom/Satellite/Terrain view, Distance between two locations, and Directions API route drawing** exactly as written in the document.) 

