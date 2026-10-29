# 6. Develop an Android Application Using Adapters to Populate Spinner or ListView Dynamically

[← Back to Index](README.md)

## Project Name
`AdapterDemo`

## Aim
To develop an Android application using `ArrayAdapter` to populate a `Spinner` and a `ListView` dynamically and handle item selection and click events.

## Introduction

An Android **Spinner** is a view similar to a dropdown list that allows users to select one option from a list of options. When the user clicks the Spinner, it displays a dropdown list of available values.

A **ListView** displays a scrollable list of items. An **Adapter** connects the data source to a view and provides the items that should be displayed.

In this application, `ArrayAdapter` is used to populate both the Spinner and the ListView with a list of cities.

## 1. File Name: `activity_main.xml`

**File Path:** `app/src/main/res/layout/activity_main.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="20dp">

    <Spinner
        android:id="@+id/spinner"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" />

    <ListView
        android:id="@+id/listView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp" />

</LinearLayout>
```

## 2. File Name: `MainActivity.java`

**File Path:** `app/src/main/java/com/example/adapterdemo/MainActivity.java`

```java
package com.example.adapterdemo;

import android.os.Bundle;
import android.view.View;
import android.widget.AdapterView;
import android.widget.ArrayAdapter;
import android.widget.ListView;
import android.widget.Spinner;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    Spinner spinner;
    ListView listView;

    String[] cities = {
            "Mumbai",
            "Pune",
            "Delhi",
            "Chennai",
            "Hyderabad"
    };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        spinner = findViewById(R.id.spinner);
        listView = findViewById(R.id.listView);

        // Spinner Adapter
        ArrayAdapter<String> spinnerAdapter = new ArrayAdapter<>(
                this,
                android.R.layout.simple_spinner_item,
                cities
        );

        spinnerAdapter.setDropDownViewResource(
                android.R.layout.simple_spinner_dropdown_item
        );

        spinner.setAdapter(spinnerAdapter);

        // ListView Adapter
        ArrayAdapter<String> listAdapter = new ArrayAdapter<>(
                this,
                android.R.layout.simple_list_item_1,
                cities
        );

        listView.setAdapter(listAdapter);

        // Spinner Item Selection
        spinner.setOnItemSelectedListener(
                new AdapterView.OnItemSelectedListener() {

                    @Override
                    public void onItemSelected(
                            AdapterView<?> parent,
                            View view,
                            int position,
                            long id) {

                        Toast.makeText(
                                MainActivity.this,
                                "Selected: " + cities[position],
                                Toast.LENGTH_SHORT
                        ).show();
                    }

                    @Override
                    public void onNothingSelected(
                            AdapterView<?> parent) {
                    }
                }
        );

        // ListView Item Click
        listView.setOnItemClickListener(
                (parent, view, position, id) -> {

                    Toast.makeText(
                            MainActivity.this,
                            "Clicked: " + cities[position],
                            Toast.LENGTH_SHORT
                    ).show();
                }
        );
    }
}
```

**Important:** Ensure that the package name `com.example.adapterdemo` matches your Android Studio project's package name.

## 3. Explanation

### Spinner Adapter

- The Spinner displays a dropdown list of cities.
- `ArrayAdapter<String>` connects the `cities` array to the Spinner.
- `setDropDownViewResource()` specifies the layout used for dropdown items.
- `setAdapter()` attaches the adapter to the Spinner.
- When an item is selected, a Toast message displays the selected city.

### ListView Adapter

- The ListView displays all cities as a vertical list.
- `android.R.layout.simple_list_item_1` provides a standard layout for each row.
- `setAdapter()` connects the ListView to its adapter.
- When a city is clicked, a Toast message displays the clicked city.

### ArrayAdapter

`ArrayAdapter` is an Android adapter that connects an array or list of data to a view such as a Spinner or ListView.

In this application, the same `cities` array is used to populate both views.

## 4. Expected Output

1. The application displays a Spinner and a ListView.
2. The Spinner contains Mumbai, Pune, Delhi, Chennai, and Hyderabad.
3. Selecting a city from the Spinner displays a Toast message, such as `Selected: Mumbai`.
4. The ListView displays all five cities.
5. Clicking a city in the ListView displays a Toast message, such as `Clicked: Pune`.

**Note:** Android may automatically trigger the Spinner's selection listener for its initial selection when the screen loads.

## 5. Result

Thus, an Android application using `ArrayAdapter` to populate a Spinner and a ListView dynamically was developed successfully.

## 6. Upload the Project to GitHub

1. Open your Android Studio project folder.
2. Create or update the `README.md` file with this content.
3. Save the file.
4. Open your GitHub repository.
5. Commit and push your changes.

### Git Commands

```bash
git add README.md
git commit -m "Add Spinner and ListView Adapter practical"
git push
```
