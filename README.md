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
Developed by:ASHIKA TR
Registeration Number :212224220011
*/
```

## activity_main.xml

```
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp"
    android:gravity="center">

    <!-- Display -->
    <TextView
        android:id="@+id/tvResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="0"
        android:textSize="32sp"
        android:gravity="right"
        android:padding="10dp"
        android:background="#EEEEEE" />

    <!-- Buttons Grid -->
    <GridLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:rowCount="5"
        android:columnCount="5"
        android:layout_marginTop="20dp">

        <!-- Row 1 -->
        <Button android:id="@+id/btn7" android:text="7"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="0" android:layout_column="0"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btn8" android:text="8"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="0" android:layout_column="1"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btn9" android:text="9"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="0" android:layout_column="2"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btnDiv" android:text="/"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="0" android:layout_column="3"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>

        <!-- Row 2 -->
        <Button android:id="@+id/btn4" android:text="4"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="1" android:layout_column="0"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btn5" android:text="5"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="1" android:layout_column="1"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btn6" android:text="6"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="1" android:layout_column="2"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btnMul" android:text="*"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="1" android:layout_column="3"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>

        <!-- Row 3 -->
        <Button android:id="@+id/btn1" android:text="1"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="2" android:layout_column="0"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btn2" android:text="2"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="2" android:layout_column="1"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btn3" android:text="3"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="2" android:layout_column="2"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btnSub" android:text="-"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="2" android:layout_column="3"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>

        <!-- Row 4 -->
        <Button android:id="@+id/btn0" android:text="0"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="3" android:layout_column="0"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btnDot" android:text="."
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="3" android:layout_column="1"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btnEqual" android:text="="
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="3" android:layout_column="2"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
        <Button android:id="@+id/btnAdd" android:text="+"
            android:layout_width="0dp" android:layout_height="80dp" android:layout_row="3" android:layout_column="3"
            android:layout_columnWeight="1" android:layout_rowWeight="1"/>
    </GridLayout>

</LinearLayout>

```
## MAinActivity.java

```
package com.example.calculator;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    TextView tvResult;
    String currentInput = "";
    String operator = "";
    double firstNumber = 0;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        tvResult = findViewById(R.id.tvResult);

        // Number buttons
        int[] numberIDs = {R.id.btn0, R.id.btn1, R.id.btn2, R.id.btn3, R.id.btn4,
                R.id.btn5, R.id.btn6, R.id.btn7, R.id.btn8, R.id.btn9};

        View.OnClickListener numberListener = v -> {
            Button b = (Button) v;
            currentInput += b.getText().toString();
            tvResult.setText(currentInput);
        };

        for (int id : numberIDs) {
            findViewById(id).setOnClickListener(numberListener);
        }

        // Operators
        findViewById(R.id.btnAdd).setOnClickListener(v -> setOperator("+"));
        findViewById(R.id.btnSub).setOnClickListener(v -> setOperator("-"));
        findViewById(R.id.btnMul).setOnClickListener(v -> setOperator("*"));
        findViewById(R.id.btnDiv).setOnClickListener(v -> setOperator("/"));

        // Equal
        findViewById(R.id.btnEqual).setOnClickListener(v -> calculate());
    }

    private void setOperator(String op) {
        firstNumber = Double.parseDouble(currentInput);
        operator = op;
        currentInput = "";
    }

    private void calculate() {
        double secondNumber = Double.parseDouble(currentInput);
        double result = 0;

        switch (operator) {
            case "+": result = firstNumber + secondNumber; break;
            case "-": result = firstNumber - secondNumber; break;
            case "*": result = firstNumber * secondNumber; break;
            case "/":
                if (secondNumber != 0) {
                    result = firstNumber / secondNumber;
                } else {
                    tvResult.setText("Error");
                    return;
                }
                break;
        }

        tvResult.setText(String.valueOf(result));
        currentInput = String.valueOf(result);
    }
}

```

## OUTPUT

<img width="1867" height="1108" alt="image" src="https://github.com/user-attachments/assets/dc9a4d50-fe5c-4dfb-9818-951fc05b1a0b" />



## RESULT
Thus a Simple Android Application develop a program to create simple calculator in Android Studio is developed and executed successfully.
