# DeretBilanganFibonacii
### Nama           :  Nadiatul umah ###
### NIM            : 312210500 ###
### Kelas          : TI.22.A5 ### 
### Dosen Pengampu : Donny Maulana S.Kom., M.M.S.I

# ProjectFibonacci

# Tugas Pertemuan 6

![gambar tugas](https://github.com/nadyakhorun/ProjectFibonacci/assets/115801823/49aaf952-758f-404e-a68e-7da72c9b66b1)

# Langkah-Langkah

1. Hal yang pertama kita harus lakukan adalan membuat project barunya terlebih dahulu dengan nama project "tugasenam"

2. Kemudian pada layout activity_main kita tambahkan 3 "button" dan 1 "textview" seperti berikut



3. Pada button yang pertama itu berfungsi sebagai tombol "Toast" yang nantinya ketika kita tekan akan muncul sebuah toast message yaitu "Bilangan Fibonacci". Dan button yang kedua, berfungsi sebagai tombol “count” yang nantinya ketika tombol ditekan akan menghitung bilangan fibonaccinya. lalu kemudian yang terakhir Textview, yang berfungsi untuk menampilkan angka atau bilangan fibonaccinya yang tepat berada di tengah.

4. langkah yang perlu kita lakukan selajutnya adalah masukkan codingan didalam activity_fibonacci seperti berikut

 * activity_fibonacci.xml
  ```
    <?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <Button
        android:id="@+id/button_limit"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_marginEnd="8dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:background="@color/colorPrimary"
        android:onClick="setLimit"
        android:textColor="@android:color/white"
        android:text="@string/enter_fibonacci_limit"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize"/>


    <Button
        android:id="@+id/button_count"
        android:layout_width="190dp"
        android:layout_height="48dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="@color/colorPrimary"
        android:onClick="countUp"
        android:text="@string/button_label_count"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml,VisualLintButtonSize" />

    <Button
        android:id="@+id/button_finish"
        android:layout_width="190dp"
        android:layout_height="48dp"
        android:layout_marginStart="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="@color/colorPrimary"
        android:onClick="back1"
        android:text="@string/button_label_finish"
        android:textColor="@android:color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="1.0"
        app:layout_constraintStart_toStartOf="parent"
        tools:ignore="UsingOnClickInXml" />

    <TextView
        android:id="@+id/show_count"
        android:layout_width="0dp"
        android:layout_height="0dp"
        android:layout_marginStart="8dp"
        android:layout_marginTop="8dp"
        android:layout_marginEnd="8dp"
        android:layout_marginBottom="8dp"
        android:background="#FFFF00"
        android:gravity="center_vertical"
        android:text="@string/count_initial_value"
        android:textAlignment="center"
        android:textColor="@color/colorPrimary"
        android:textSize="160sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@id/button_count"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@id/button_limit"
        tools:ignore="RtlCompat" />

</androidx.constraintlayout.widget.ConstraintLayout>
```
  * strings.xml
``` 
 <resources>
    <string name="app_name">Tugasenam</string>
    <string name="button_label_count">Count</string>
    <string name="count_initial_value"> </string>
    <string name="button_label_finish">Reset</string>
    <string name="enter_fibonacci_limit">Masukan Limit Angka</string>
</resources>
 ```   
* colors.xml
```
  <resources>
    <color name="black">#FF000000</color>
    <color name="white">#FFFFFFFF</color>
    <color name="colorPrimary">#3F5185</color>
    <color name="colorPrimaryDark">#303F9F</color>
    <color name="colorAccent">#FF4081</color>
    <color name="color1">#FF0000</color>
    <color name="color2">#00FF00</color>
    <color name="color3">#0000FF</color>
</resources>
```

  # Tampilan Design

  ![tampilan design](https://github.com/nadyakhorun/ProjectFibonacci/assets/115801823/ec02ff54-1c1c-4d25-b477-be9a82311e10)

  # MainActivity.java

  Dalam MainActivity.java ini berisi semua codingan untuk fungsi-fungsinya. Seperti, fungsi untuk 
  tombol-tombol dan rumus bilangan fibonaccinya.

```
package com.example.tugas_enam_fibonacci;

import android.app.AlertDialog;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {
    private TextView showCount;
    private int count = 1;
    private long fibNMinus1 = 1;
    private long fibNMinus2 = 0;
    private int limit = -1; // Inisialisasi limit dengan nilai default

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        showCount = findViewById(R.id.show_count);
    }

    public void countUp(View view) {
        if (count == 0) {
            showCount.setText("0");
        } else if (count == 1) {
            showCount.setText("1");
        } else {
            if (limit != -1 && count > limit) {
                // Jika count melebihi limibonacciit, atur ulang perhitungan
                count = 0;
                fibNMinus1 = 1;
                fibNMinus2 = 0;
                showCount.setText(getString(R.string.count_initial_value));
            } else {
                long fibCurrent = fibNMinus1 + fibNMinus2;
                fibNMinus2 = fibNMinus1;
                fibNMinus1 = fibCurrent;

                // Mengatur warna teks berdasarkan angka Fibonacci
                int colorResId = R.color.color1; // Warna default
                switch (count % 3) {
                    case 1:
                        colorResId = R.color.color1; // Warna merah
                        break;
                    case 2:
                        colorResId = R.color.color2; // Warna hijau
                        break;
                    case 0:
                        colorResId = R.color.color3; // Warna biru
                        break;
                }
                showCount.setTextColor(getResources().getColor(colorResId));
                showCount.setText(String.valueOf(fibCurrent));
            }
        }

        count++;
    }

    public void back1(View view) {
        count = 1;
        fibNMinus1 = 1;
        fibNMinus2 = 0;
        limit = -1;
        showCount.setText(getString(R.string.count_initial_value));
    }

    public void setLimit(View view) {
        AlertDialog.Builder builder = new AlertDialog.Builder(this);
        builder.setTitle("Set limit bilangan yang ditampilkan :");

        final EditText input = new EditText(this);
        input.setInputType(android.text.InputType.TYPE_CLASS_NUMBER);
        builder.setView(input);

        builder.setPositiveButton("OK", (dialog, which) -> {
            String limitStr = input.getText().toString();
            limit = Integer.parseInt(limitStr);
        });

        builder.setNegativeButton("Cancel", (dialog, which) -> dialog.cancel());

        builder.show();
    }
}
```
# Hasil Run

Untuk run app ini saya menggunakan hp android . Berikut ini adalah tampilan dari aplikasi yang telah saya buat :

* Tombol Toast ditekan, maka akan muncul message "Bilangan Fibonacci" seperti berikut
![WhatsApp Image 2023-11-02 at 20 05 54](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/747b20a2-38aa-4dbe-a39b-234b61e02ca6)
![WhatsApp Image 2023-11-02 at 20 05 55](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/19a52e7e-3798-4a2f-bc71-29210053562d)
![WhatsApp Image 2023-11-02 at 20 05 56](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/cf07d42f-ad03-4164-ba49-325cfc720e43)
![WhatsApp Image 2023-11-02 at 20 05 56 (1)](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/58c86803-2b4e-4681-9b1b-a88e4b7e3c71)
![WhatsApp Image 2023-11-02 at 20 05 56 (2)](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/6fec538c-407a-431c-9408-a8873a2094ac)
![WhatsApp Image 2023-11-02 at 20 05 57](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/a0c6e289-c61a-40c1-9ceb-d0299b3dfcd3)
![WhatsApp Image 2023-11-02 at 20 05 57 (1)](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/b492d6dc-0641-4883-b0f0-250652a4c770)
![WhatsApp Image 2023-11-02 at 20 05 57 (2)](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/5ebea146-514b-4ff1-9386-29e7d9666738)
![WhatsApp Image 2023-11-02 at 20 05 58](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/597968a9-597a-449e-81ce-f0f89449d0f4)
![WhatsApp Image 2023-11-02 at 20 05 58 (1)](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/9cd63301-c74c-4022-8400-b742ccfa7074)
![WhatsApp Image 2023-11-02 at 20 05 58 (2)](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/38ebd791-55f6-4506-a354-3ac5a7bfb8a0)
![WhatsApp Image 2023-11-02 at 20 05 58 (3)](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/ecbc331f-4525-4ca0-92ca-312670fdb81b)
![WhatsApp Image 2023-11-02 at 20 05 59](https://github.com/Nadiatulumah2/DeretBilanganFibonacii/assets/129835302/e8cd6b7e-5d97-4ffa-9dad-b08e43b94b9e)





 



