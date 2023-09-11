# Content_Provider
## Ex.No:5 Create Your Own Content Providers to get Contacts details.
## AIM:
To create your own content providers to get contacts details using Android Studio.

## EQUIPMENTS REQUIRED:
Android Studio(Latest Version)

## ALGORITHM:
Step 1: Open Android Stdio and then click on File -> New -> New project.

Step 2: Then type the Application name as “contentprovider″ and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Get contacts details and Display details give in MainActivity file.

Step 7: Save and run the application.

## PROGRAM:
/*
Program to print the text create your own content providers to get contacts details.

Developed by: Kulaganachi

Registeration Number :212221040086
*/
## Activity_xml File:
~~~
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout             xmlns:android="http://schemas.android.com/apk/res/android"
 xmlns:app="http://schemas.android.com/apk/res-auto"
 xmlns:tools="http://schemas.android.com/tools"
 android:layout_width="match_parent"
 android:layout_height="match_parent"
 tools:context=".MainActivity">

<Button
 android:id="@+id/button"
 android:layout_width="wrap_content"
 android:layout_height="wrap_content"
 android:layout_marginStart="129dp"
 android:layout_marginTop="302dp"
 android:text="GET CONTACTS"
 android:onClick="btnGetContactPressed"
 app:layout_constraintStart_toStartOf="parent"
 app:layout_constraintTop_toTopOf="parent" />
</androidx.constraintlayout.widget.ConstraintLayout>
~~~
## MainActivity.java File:
~~~
 package com.example.contactsgetter;

import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;

import android.Manifest;
import android.annotation.SuppressLint;
import android.content.ContentResolver;
import android.content.pm.PackageManager;
import android.database.Cursor;
import android.net.Uri;
import android.os.Bundle;
import android.provider.ContactsContract;
import android.util.Log;
import android.view.View;


public class MainActivity extends AppCompatActivity {

@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);


  Button show = (Button) findViewById(R.id.button2);
 //        show.setOnClickListener(view->
 //        {
 //            getPhoneContacts();
 //        });

}
private void getPhoneContacts(){
  if(ContextCompat.checkSelfPermission(this, Manifest.permission.READ_CONTACTS) != PackageManager.PERMISSION_GRANTED) {
    ActivityCompat.requestPermissions(this,new String[] {Manifest.permission.READ_CONTACTS},0);

}
ContentResolver contentResolver = getContentResolver();
Uri uri = ContactsContract.CommonDataKinds.Phone.CONTENT_URI;
Cursor cursor = contentResolver.query(uri,null,null,null,null);
Log.i("CONTACT_PROVIDER_DEMO","TOTAL # COUNTS :::"+cursor.getCount());
if(cursor.getCount() > 0)
{
    while(cursor.moveToNext()){
        @SuppressLint("Range") String contactName = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME));
        @SuppressLint("Range") String contactNumber = cursor.getString(cursor.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER));
        Log.i("Content_provider_demo","Name: # "+contactName+"Number: # "+contactNumber);
    }

}
}

public void btnGetContactPressed(View view) {
getPhoneContacts();
 }
}
~~~
## OUTPUT

![image](https://github.com/Kulaganachi/Content_Provider/assets/133641126/568368d7-71db-4a1a-a99a-a558bb5b7bd9)

![image](https://github.com/Kulaganachi/Content_Provider/assets/133641126/1f88aeec-3491-49bc-9616-358cfb9eca99)

![image](https://github.com/Kulaganachi/Content_Provider/assets/133641126/b739468f-4ce5-4f8c-99f4-5a19e9e7431a)



## RESULT
Thus a Simple Android Application create your own content providers to get contacts details using Android Studio is developed and executed successfully.
