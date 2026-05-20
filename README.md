# Ex.No:5 Develop a simple calculator using android studio.

## AIM:

To develop a program to develop a simple calculator in Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Min.required Artic Fox)

## ALGORITHM:

Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as calculator and click Next. 

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout using UI components in activity_main.xml.

Step 6: Display the calculator operation in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
```
/*
Program to print the text “calculator operation”.
Developed by: DINESHKARTHIK N
Registeration Number : 212223220021
*/
```

#### MainActivity.java
```
package com.example.ex5calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText etInput;
    String display = "";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        etInput = findViewById(R.id.etInput);

        int[] ids = {
                R.id.btn0,R.id.btn1,R.id.btn2,R.id.btn3,
                R.id.btn4,R.id.btn5,R.id.btn6,R.id.btn7,
                R.id.btn8,R.id.btn9,
                R.id.btnAdd,R.id.btnSub,
                R.id.btnMul,R.id.btnDiv
        };

        for (int id : ids) {
            findViewById(id).setOnClickListener(this::onButtonClick);
        }

        findViewById(R.id.btnEq).setOnClickListener(v -> calculate());

        findViewById(R.id.btnC).setOnClickListener(v -> {
            display = "";
            etInput.setText("");
        });
    }

    private void onButtonClick(View v) {
        Button btn = (Button) v;
        display += btn.getText().toString();
        etInput.setText(display);
    }

    private void calculate() {
        try {
            String result = String.valueOf(eval(display));
            etInput.setText(result);
            display = result;
        } catch (Exception e) {
            etInput.setText("Error");
        }
    }

    private double eval(String expression) {
        String[] parts;

        if (expression.contains("+")) {
            parts = expression.split("\\+");
            return Double.parseDouble(parts[0]) + Double.parseDouble(parts[1]);
        }
        else if (expression.contains("-")) {
            parts = expression.split("-");
            return Double.parseDouble(parts[0]) - Double.parseDouble(parts[1]);
        }
        else if (expression.contains("\\*")) {
            parts = expression.split("\\*");
            return Double.parseDouble(parts[0]) * Double.parseDouble(parts[1]);
        }
        else if (expression.contains("/")) {
            parts = expression.split("/");
            return Double.parseDouble(parts[0]) / Double.parseDouble(parts[1]);
        }

        return 0;
    }
}
```

#### activity_main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:background="#000000"
    android:padding="16dp">

    <EditText
        android:id="@+id/etInput"
        android:layout_width="match_parent"
        android:layout_height="60dp"
        android:hint="0"
        android:textSize="28sp"
        android:textColor="#FFFFFF"
        android:textColorHint="#AAAAAA"
        android:enabled="false"
        android:background="#222222"
        android:textAlignment="viewEnd"
        android:padding="10dp"
        android:layout_marginBottom="20dp"/>

    <!-- ROW 1 -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginBottom="10dp">

        <Button
            android:id="@+id/btn7"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="7"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btn8"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="8"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btn9"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="9"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btnDiv"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="/"
            android:textColor="#FFFFFF"
            android:backgroundTint="#B22222"/>
    </LinearLayout>

    <!-- ROW 2 -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginBottom="10dp">

        <Button
            android:id="@+id/btn4"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="4"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btn5"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="5"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btn6"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="6"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btnMul"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="*"
            android:textColor="#FFFFFF"
            android:backgroundTint="#B22222"/>
    </LinearLayout>

    <!-- ROW 3 -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginBottom="10dp">

        <Button
            android:id="@+id/btn1"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="1"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btn2"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="2"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btn3"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="3"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btnSub"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="-"
            android:textColor="#FFFFFF"
            android:backgroundTint="#B22222"/>
    </LinearLayout>

    <!-- ROW 4 -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btn0"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="0"
            android:textColor="#FFFFFF"
            android:backgroundTint="#DC143C"/>

        <Button
            android:id="@+id/btnC"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="C"
            android:textColor="#FFFFFF"
            android:backgroundTint="#8B0000"/>

        <Button
            android:id="@+id/btnEq"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="="
            android:textColor="#FFFFFF"
            android:backgroundTint="#8B0000"/>

        <Button
            android:id="@+id/btnAdd"
            android:layout_width="0dp"
            android:layout_height="60dp"
            android:layout_weight="1"
            android:text="+"
            android:textColor="#FFFFFF"
            android:backgroundTint="#B22222"/>
    </LinearLayout>

</LinearLayout>
```

## OUTPUT

<img width="397" height="733" alt="image" src="https://github.com/user-attachments/assets/04d36dc2-a353-401b-bdc7-9611ac8e93dc" />

<img width="382" height="740" alt="image" src="https://github.com/user-attachments/assets/ecb3db3d-c106-447b-87b7-e480f7baf1ee" />



## RESULT
Thus a Simple Android Application develop a program to create simple calculator in Android Studio is developed and executed successfully.
