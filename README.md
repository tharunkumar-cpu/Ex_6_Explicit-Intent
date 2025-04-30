# Ex.No:6 Implement an application that uses Explicit Intent using Android


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1:
Open Android Studio and create a new project with a Basic Activity.

Step 2:
In activity_main.xml, create a TextField (EditText) to input a number and a Button labeled "Explicit Intent".

Step 3:
In MainActivity.java, get the value from the TextField and set up an Explicit Intent to pass the value to the second screen (SecondActivity).

Step 4:
Create SecondActivity.java and receive the number passed from MainActivity using getIntent().

Step 5:
In SecondActivity, calculate the factorial of the received number and display the result in a TextView.

Step 6:
Save and run the app. On clicking the "Explicit Intent" button, it will navigate to the second screen displaying the factorial.




## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: THARUN K
Registeration Number : 212222040172
*/
```
## Main activity.java
```
package com.example.explicitintentapp;

import android.content.Intent;
import android.os.Bundle;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText inputNumber;
    Button btnExplicitIntent;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        inputNumber = findViewById(R.id.inputNumber);
        btnExplicitIntent = findViewById(R.id.btnExplicitIntent);

        btnExplicitIntent.setOnClickListener(view -> {
            String numberStr = inputNumber.getText().toString();
            if (!numberStr.isEmpty()) {
                int number = Integer.parseInt(numberStr);
                Intent intent = new Intent(MainActivity.this, SecondActivity.class);
                intent.putExtra("number", number);
                startActivity(intent); 
            }
        });
    }
}

```
## Second activity.java
```
package com.example.explicitintentapp;

import android.annotation.SuppressLint;
import android.os.Bundle;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class SecondActivity extends AppCompatActivity {

    TextView factorialResult;

    @SuppressLint("MissingInflatedId")
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        factorialResult = findViewById(R.id.factorialResult);

        int number = getIntent().getIntExtra("number", 0);
        long result = factorial(number);

        factorialResult.setText("Factorial of " + number + " is: " + result);
    }

    private long factorial(int n) {
        if (n < 0) return 0;
        long fact = 1;
        for (int i = 1; i <= n; i++) {
            fact *= i;
        }
        return fact;
    }
}

```
## Activity main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp"
    android:background="@color/backgroundColor">

    <EditText
        android:id="@+id/inputNumber"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter a number"
        android:inputType="number"
        android:minHeight="48dp"
        android:textColor="@color/textColor" />

    <Button
        android:id="@+id/btnExplicitIntent"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:text="Explicit Intent"
        android:backgroundTint="@color/textColor" />
</LinearLayout>

```
## Second activity.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="24dp">

    <TextView
        android:id="@+id/factorialResult"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Result will appear here"
        android:textSize="22sp"
        />
</LinearLayout>

```
## OUTPUT
![Screenshot 2025-04-14 191458](https://github.com/user-attachments/assets/7c339201-c362-4b67-9353-42b18f0e2f44)

![Screenshot 2025-04-14 191031](https://github.com/user-attachments/assets/d25ff236-e9a9-41d2-afa3-870e9fe1f992)

![Screenshot 2025-04-14 191042](https://github.com/user-attachments/assets/8b10cddc-537a-4b6f-9fc9-f6bef893089d)


## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
