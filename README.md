# ANDROID PROGRAMMING PRACTICALS
# Practical: 1


## Aim
Aim: Introduction to Android, introduction to Android Studio IDE, Application 
Fundamentals: Creating a project, android components, activities, services, 
content providers, broadcast receivers, interface overview, creating android 
virtual device, USB debugging mode, Android Application overview. Simple  
“Hello World” program. Input:  

## Input
```
activity_main.xml:   
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout     
xmlns:android="http://schemas.android.com/apk/res/android"     
android:id="@+id/main"     
android:layout_width="match_parent"     
android:layout_height="match_parent"     
android:gravity="center">  
  
    <TextView         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:text="Hello World!"         
android:textSize="30sp"         
android:textColor="@color/black"/>  
  
</LinearLayout>  
```


# Practical: 2

## Aim
Programming resources, Android resources, color, theme, strain, Drawable, 
Dimension, Image.

## Input
```
string.xml: 
<resources>  
    <string name="app_title">Resource Demo App</string>  
    <string name="welcome_msg">Hello, Welcome to Resource Practical!</string> 
</resources>  
  
colors.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<resources>  
    <color name="myPurple">#6200EE</color>  
    <color name="myGreen">#4CAF50</color>  
</resources>  
  
dimensions.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<resources>  
    <dimen name="text_large">24sp</dimen>  
    <dimen name="padding_big">16dp</dimen>  
</resources>  
  
round_button.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<shape 
xmlns:android="http://schemas.android.com/apk/res/android"     
android:shape="rectangle">     <corners android:radius="12dp"/>  
    <solid android:color="@color/myPurple"/>  
    <padding 

     android:left="12dp"         
android:right="12dp"         
android:top="8dp"         
android:bottom="8dp"/>  
</shape>  
  
activity_main.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout 
xmlns:android="http://schemas.android.com/apk/res/android"     
android:layout_width="match_parent"     
android:layout_height="match_parent"      
android:orientation="vertical">  
  
  
    <TextView         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:text="@string/welcome_msg"         
android:textColor="@color/myGreen"         
android:textSize="@dimen/text_large"         
android:padding="@dimen/padding_big" />  
  
    <ImageView         
android:layout_width="200dp"         
android:layout_height="200dp"         
android:layout_marginTop="16dp"         
android:src="@drawable/cat"         
android:adjustViewBounds="true" /> 

 <Button         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:text="Click Me"         
android:layout_marginTop="24dp"         
android:background="@drawable/round_button" 
/>  
</LinearLayout>
```

## Output
(Refer practical output screenshot in PDF)

---

# Practical: 3

## Aim
Programming Activities and Fragments: Activity Life Cycle, Activity 
Methods, Multiple Activities, Life Cycle of Fragments and Multiple Fragments.

## Input
```
MainActivity.java  
Package  
com.example.activityfragementdemo ; 
import android.content.Intent;  
import android.os.Bundle;  
importAandroidx.appcompat.app.AppCompatActivity;  
import android.util.Log;  
import android.widget.Button; 
import android.widget.Toast;  
  
public class MainActivity extends AppCompatActivity{   
String TAG = "ActivityLifeCycle";  
@Override protected void onCreate(Bundle 
savedInstanceState) {  
super.onCreate(savedInstanceState);  
setContentView(R.layout.activity_main);  
Toast.makeText(this,  "onCreate  called", 
 Toast.LENGTH_SHORT).show(); Log.d(TAG, "onCreate called");  
  
Button  btnSecond  =  findViewById(R.id.btnOpenSecond); 
btnSecond.setOnClickListener(v -> {  
Intent  i  =  new  Intent(MainActivity.this,  SecondActivity.class); 
startActivity(i);  
});  
Button btnFrag1 = findViewById(R.id.btnFrag1); 
Button btnFrag2 = findViewById(R.id.btnFrag2);  
btnFrag1.setOnClickListener(v  ->  { 
getSupportFragmentManager().beginTransaction().replace(R.id.fragmentConta
i ner,  
new FirstFragment()).commit();  
  
});  
btnFrag2.setOnClickListener(v  ->  { 
getSupportFragmentManager().beginTransaction().replace(R.id.fragmentConta
i ner,  
new SecondFragment()).commit();  
});  
}  
@Override  
protected void onStart() {  
super.onStart();  
Toast.makeText(this,  "onStart  called", 
 Toast.LENGTH_SHORT).show(); Log.d(TAG, "onStart called");  
}  
@Override protected void 
onResume() {  
super.onResume();  
Toast.makeText(this, "onResume called", Toast.LENGTH_SHORT).show(); 
Log.d(TAG, "onResume called");  
}  
@Override  
protected void onPause(){  
super.onPause();  
Toast.makeText(this, "onPause called", Toast.LENGTH_SHORT).show(); 
Log.d(TAG, "onPause called"); 
}  
@Override protected 
void onStop(){  
super.onStop();  
Toast.makeText(this,  "onStop  called", 
 Toast.LENGTH_SHORT).show(); Log.d(TAG, "onStop called");  
}  
@Override  
Protected void onRestart(){  
super.onRestart();  
Toast.makeText(this, "onRestart called", Toast.LENGTH_SHORT).show(); 
Log.d(TAG, "onRestart called");  
}  
@Override  
protected void onDestroy(){  
super.onDestroy();  
Toast.makeText(this, "onDestroy called", Toast.LENGTH_SHORT).show();  
Log.d(TAG, "onDestroy called");  
}  
  
activity_main.xml  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout 
xmlns:android="http://schemas.android.com/apk/res/android
" android:layout_width="match_parent" 
android:layout_height="match_parent" 
android:orientation="vertical" android:padding="20dp">  
<Button 
android:id="@+id/btnOpenSecond" 
android:layout_width="match_parent"
android:layout_height="wrap_content" 
android:text="Open Second Activity" 
android:layout_marginTop="10dp"/>  
<Button android:id="@+id/btnFrag1" 
android:layout_width="match_parent
" 
android:layout_height="wrap_content
" android:text="Load Fragment 1" 
android:layout_marginTop="10dp"/>  
<Button android:id="@+id/btnFrag2" 
android:layout_width="match_parent
" 
android:layout_height="wrap_content
" android:text="Load Fragment 2" 
android:layout_marginTop="10dp"/>  
<FrameLayout 
android:id="@+id/fragmentContainer" 
android:layout_width="match_parent" 
android:layout_height="0dp" 
android:layout_weight="1" 
android:background="#E0E0E0" 
android:layout_marginTop="20dp"/>  
</LinearLayout> 
activity_second.xml  
<?xml version="1.0" encoding="utf-8"?>  
<RelativeLayout 
xmlns:android="http://schemas.android.com/apk/res/android" 
android:layout_width="match_parent" 
android:layout_height="match_parent" 
android:padding="20dp"> 
<TextView 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="This is Second Activity" 
android:textSize="22sp" 
android:layout_centerInParent="true"/>  
</RelativeLayout> 
fragment_first.xml  
<?xml version="1.0" encoding="utf-8"?>  
<FrameLayout 
xmlns:android="http://schemas.android.com/apk/res/android" 
android:layout_width="match_parent" 
android:layout_height="match_parent" 
android:background="#FFA726">  
  
<TextView 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="First Fragment" 
android:textSize="22sp" 
android:layout_gravity="center"/>  
</FrameLayout>  
  
FirstFragment.java  
package 
com.example.activityfragementdemo;  
import android.content.Context;  
import android.os.Bundle;  
import androidx.fragment.app.Fragment; 
import android.util.Log;  
import android.view.LayoutInflater;  
import android.view.View;  
import android.view.ViewGroup;  
public class FirstFragment extends Fragment{  
String TAG = "FRAGMENT1"  
@Override public void onAttach(Context 
context) { super.onAttach(context); 
Log.d(TAG, "onAttach");  
}  
@Override public void onCreate(Bundle 
savedInstanceState) { 
super.onCreate(savedInstanceState); Log.d(TAG, 
"onCreate");  
}  
@Override public View onCreateView(LayoutInflater inflater, ViewGroup container, 
Bundle savedInstanceState) {  
Log.d(TAG, "onCreateView");  
return inflater.inflate(R.layout.fragment_first, container, false);  
}  
@Override public 
void onStart() { 
super.onStart();  
Log.d(TAG, "onStart");  
}  
@Override public void 
onResume() {  
super.onResume(); Log.d(TAG, 
"onResume");  
}  
@Override  
public void onPause() {  
super.onPause(); Log.d(TAG, 
"onPause");  
}  
@Override public 
void onStop() {  
super.onStop(); Log.d(TAG, 
"onStop");  
}  
@Override public void 
onDestroyView() { 
super.onDestroyView();  
Log.d(TAG, "onDestroyView");  
}  
@Override public void 
onDestroy() {  
super.onDestroy(); 
Log.d(TAG, "onDestroy");  
}  
@Override public void 
onDetach() {  
super.onDetach(); Log.d(TAG, 
"onDetach");  
}  
fragment_second.xml  
<?xml version="1.0" encoding="utf-8"?>  
<FrameLayout 
xmlns:android="http://schemas.android.com/apk/res/android" 
android:layout_width="match_parent"
android:layout_height="match_parent" 
android:background="#FFA726">  
<TextView 
android:layout_width="wrap_content" 
android:layout_height="wrap_content" 
android:text="Second Fragment" 
android:textSize="22sp" 
android:layout_gravity="center"/>  
</FrameLayout>  
  
SecondFragment.java  
package com.example.activityfragementdemo; 
import android.content.Context;  
import android.os.Bundle;  
import androidx.fragment.app.Fragment;  
import android.util.Log;  
import android.view.LayoutInflater;  
import android.view.View;  
import android.view.ViewGroup;  
 
public class SecondFragment extends Fragment{  
String TAG = "FRAGMENT2"  
@Override public void onAttach(Context 
context) { super.onAttach(context); 
Log.d(TAG, "onAttach");  
}  
@Override public void onCreate(Bundle 
savedInstanceState) {  
super.onCreate(savedInstanceState);  
Log.d(TAG, "onCreate"); 
}  
@Override public View onCreateView(LayoutInflater inflater, ViewGroup container, 
Bundle savedInstanceState) {  
Log.d(TAG, "onCreateView");  
return inflater.inflate(R.layout.fragment_second, container, false);  
}  
@Override public 
void onStart() { 
super.onStart();  
Log.d(TAG, "onStart");  
}  
@Override public void 
onResume() {  
super.onResume(); Log.d(TAG, 
"onResume");  
}  
@Override public void 
onPause() {  
super.onPause(); Log.d(TAG, 
"onPause");  
}  
@Override public 
void onStop() {  
super.onStop(); Log.d(TAG, 
"onStop");  
}  
@Override public void 
onDestroyView() { 
super.onDestroyView();  
Log.d(TAG, "onDestroyView");  
} 
@Override public void 
onDestroy() {  
super.onDestroy(); 
Log.d(TAG, "onDestroy");  
}  
@Override public void 
onDetach() {  
super.onDetach(); Log.d(TAG, 
"onDetach");} 

```

## Output
(Refer practical output screenshot in PDF)

---

# Practical: 4
 
 ## Aim
 Aim: Programs related to different layouts: Coordinator, linear, relative, table, 
absolute, frame, listview, gridview.

## Input

```
<?xml version="1.0" encoding="utf-8"?>  
<androidx.coordinatorlayout.widget.CoordinatorLayout     
xmlns:android="http://schemas.android.com/apk/res/android"     
android:layout_width="match_parent"     
android:layout_height="match_parent"     
xmlns:app="http://schemas.android.com/apk/res-auto">     
<com.google.android.material.appbar.AppBarLayout         
android:layout_width="match_parent"         
android:layout_height="match_parent">  
        <com.google.android.material.appbar.MaterialToolbar             
android:layout_width="match_parent"             
android:layout_height="match_parent"             
app:title="Coordinator Layout"/>  
    </com.google.android.material.appbar.AppBarLayout>  
</androidx.coordinatorlayout.widget.CoordinatorLayout>  
  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout     
xmlns:android="http://schemas.android.com/apk/res/android"     
android:layout_width="match_parent"     
android:layout_height="match_parent"     
android:orientation="vertical"      
android:gravity="center"    
 android:padding="20dp"> 
    <TextView         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:text="linear layout Example"         
android:textSize="20sp"/>  
    <Button         
android:layout_width="match_parent"         
android:layout_height="wrap_content"         
android:text="Click Me"/>  
</LinearLayout>  
<?xml version="1.0" encoding="utf-8"?>  
<RelativeLayout     
xmlns:android="http://schemas.android.com/apk/res/android"     
android:layout_width="match_parent"     
android:layout_height="match_parent"     
android:gravity="center">  
    <TextView         android:id="@+id/title"         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:text="Relative layout Example"         
android:layout_centerHorizontal="true"         
android:textSize="20sp"/>  
    <Button         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:layout_centerInParent="true"         
android:layout_below="@+id/title"         
android:text="Click Me"/>  
</RelativeLayout> 
<?xml version="1.0" encoding="utf-8"?>  
<TableLayout     
xmlns:android="http://schemas.android.com/apk/res/android"     
android:layout_width="match_parent"     
android:layout_height="wrap_content"     
 android:stretchColumns="1"     
 android:padding="10dp">  
<TableRow>      
<TextView          
android:text="Name"         
android:background="@drawable/border"         
android:padding="10dp"         
android:textSize="18sp"/>  
    <TextView          
android:text="Designation"         
android:background="@drawable/border"         
android:padding="10dp"         
android:textSize="18sp"/>  
</TableRow>  
    <TableRow>     <TextView         
android:text="Course"         
android:background="@drawable/border"         
android:padding="10dp"  />  
    <TextView          
android:text="Age"         
android:background="@drawable/border"         
android:padding="10dp"/>  
   </TableRow> 
</TableLayout> 
boarder.xml  
<?xml version="1.0" encoding="utf-8"?>  
<shape xmlns:android="http://schemas.android.com/apk/res/android">  
<stroke  
    android:color="#000000"     
android:width="1dp"/>  
    <padding         
android:left="4dp"         
android:right="4dp"         
android:top="4dp"         
android:bottom="4dp"/>  
</shape>  
<?xml version="1.0" encoding="utf-8"?>  
<ListView     
xmlns:android="http://schemas.android.com/apk/res/android"     
android:id="@+id/listView"     
android:layout_width="match_parent"     
android:layout_height="match_parent">  
</ListView>  
 
MainActivity.java  
package com.example.layoutdemo; 
import android.os.Bundle;  
import android.widget.ArrayAdapter;  
import android.widget.ListView;  
import androidx.appcompat.app.AppCompatActivity; 
 
 public class MainActivity extends AppCompatActivity 
{  
    ListView listView;  
    String items[]={"mango","apple","banana","strawberry","kiwi"};  
    @Override     protected void onCreate(Bundle 
savedInstanceState) {         
super.onCreate(savedInstanceState);         
setContentView(R.layout.activity_main);         listView 
= findViewById(R.id.listView);  
        ArrayAdapter adapter = new ArrayAdapter(this, 
android.R.layout.simple_list_item_1, items);  
        listView.setAdapter(adapter);  
}  
}  
 
<?xml version="1.0" encoding="utf-8"?>  
<GridView     
xmlns:android="http://schemas.android.com/apk/res/android"     
android:id="@+id/gridView"     
android:layout_width="match_parent"     
android:layout_height="match_parent"     
android:numColumns="2"     
android:horizontalSpacing="10dp"     
android:verticalSpacing="10dp">  
</GridView> 
 
 MainActivity.java:  
package com.example.layoutdemo;  
import android.os.Bundle;  
import android.widget.ArrayAdapter;  
import android.widget.GridView;  
import android.widget.ListView;  
import androidx.appcompat.app.AppCompatActivity; 
public class MainActivity extends AppCompatActivity 
{ 
      GridView gridView;  
    String items[]={"mango","apple","banana","strawberry","kiwi"};  
    @Override     protected void onCreate(Bundle 
savedInstanceState) {         
super.onCreate(savedInstanceState);         
setContentView(R.layout.activity_main);         gridView 
= findViewById(R.id.gridView);  
        ArrayAdapter adapter = new ArrayAdapter(this, 
android.R.layout.simple_list_item_1, items);         gridView.setAdapter(adapter);  
    }  
    }  
```

## Output
(Refer practical output screenshot in PDF)

---

# Practical: 5

## Aim
Programming UI element-Appbar,Fragment,UI Component.

## Input
```
activity_main.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"     
xmlns:app="http://schemas.android.com/apk/res-auto"     
android:id="@+id/main"      
android:layout_width="match_parent"     
android:layout_height="match_parent"     
android:orientation="vertical">      
<androidx.appcompat.widget.Toolbar         
android:layout_width="match_parent"         
android:layout_height="wrap_content"          
android:id="@+id/toolbar"          
android:background="@color/purple_500"          
app:title="My AppBar"          
android:titleTextColor="android:color/white"/>  
    <FrameLayout         
android:layout_width="match_parent"         
android:layout_height="match_parent"         
android:id="@+id/fragment_container"/>  
</LinearLayout>  
 
colors.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<resources>  
    <color name="purple_500">#6200EE</color>  
    <color name="purple_700">#3700B3</color>  
    <color name="teal_200">#03DAC5</color>  
</resources>  
  
fragment_home.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"     
xmlns:tools="http://schemas.android.com/tools"     
android:layout_width="match_parent"      
android:layout_height="match_parent"      
android:layout_gravity="center"      
android:orientation="vertical">  
    <TextView         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:id="@+id/textViewHome"         
android:text="This Home Fragment"         
android:textSize="22sp"/>  
    <Button         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:id="@+id/btnGo"          
android:text="Go to second Fragment"         
android:layout_marginTop="20dp"/>  
</LinearLayout>  
  
fragment_second.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"     
xmlns:tools="http://schemas.android.com/tools"     
android:layout_width="match_parent"     
android:layout_height="match_parent"     
android:gravity="center"      
android:orientation="vertical">  
    <!-- TODO: Update blank fragment layout -->  
    <TextView  
        android:layout_width="wrap_content"            
android:layout_height="wrap_content"          
android:text="this is Second fragment"         
android:textSize="22sp"/>  
</LinearLayout> 

SecondFragment.java:  
package com.example.pr4;  
import android.os.Bundle;  
import androidx.fragment.app.Fragment;  
import android.view.LayoutInflater;  
import android.view.View;  
import android.view.ViewGroup;  
public class SecondFragment extends Fragment {  
    @Override     public  View  onCreateView(LayoutInflater 
 inflater,ViewGroup  container,Bundle savedInstanceState)  
    {  
        return inflater.inflate(R.layout.fragment_second, container, false);  
    }  
}  
  
HomeFragment.java:  
package com.example.pr4;  
import android.os.Bundle;  
import androidx.fragment.app.Fragment; 
import android.view.LayoutInflater; 
import android.view.View;  
import android.view.ViewGroup;  
import android.widget.Button;  
import androidx.fragment.app.FragmentTransaction;  
public class HomeFragment extends Fragment {  
   @Override     public  View  onCreateView(LayoutInflater 
 inflater,ViewGroup  container,Bundle savedInstanceState)  
   {  
       View View=inflater.inflate(R.layout.fragment_home, container, false);        
Button btn= getView().findViewById(R.id.btnGo);        
btn.setOnClickListener(v->{FragmentTransaction  transaction= 
getParentFragmentManager().beginTransaction();        
  
  
transaction.replace(R.id.fragment_container,new SecondFragment());        
transaction.commit();  
       });        
return View;  
   }  
}  
MainActivity.java:  
package com.example.pr4;  
import android.os.Bundle;  
import androidx.activity.EdgeToEdge;  
import androidx.appcompat.app.AppCompatActivity; 
import androidx.core.graphics.Insets;  
import androidx.core.view.ViewCompat;  
import androidx.core.view.WindowInsetsCompat; 
import androidx.fragment.app.Fragment;  
public class MainActivity extends AppCompatActivity {  
    @Override     protected void onCreate(Bundle 
savedInstanceState) {         
super.onCreate(savedInstanceState);         
setContentView(R.layout.activity_main);         
loadFragment(new HomeFragment());  
    }  
    private void loadFragment(Fragment fragment)  
    {  
getSupportFragmentManager().beginTransaction().replace(R.id.fragment_container,fragment 
).commit();  
    }  
}  
activity_main.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"     
xmlns:app="http://schemas.android.com/apk/res-auto"      
android:id="@+id/main"  
  
  
    android:layout_width="match_parent"     
android:layout_height="match_parent"    
android:orientation="vertical">     
<androidx.appcompat.widget.Toolbar         
android:layout_width="match_parent"         
android:layout_height="wrap_content"         
android:id="@+id/toolbar"         
android:background="@color/purple_500"          
app:title="My AppBar"         
android:titleTextColor="@android:color/white"/>  
    <FrameLayout         
android:layout_width="match_parent"         
android:layout_height="match_parent"         
android:id="@+id/fragment_container"/>  
</LinearLayout> 
```

## Output
(Refer practical output screenshot in PDF)

---

# Practical: 6

## Aim
Programming menus,dialog,dialog fragment.

## Input
```
package com.example.mydialoguefragment;  
import android.os.Bundle;  
import android.view.Menu;  
import android.view.MenuItem;  
import android.widget.Toast;  
import androidx.activity.EdgeToEdge;  
import androidx.appcompat.app.AlertDialog;  
import androidx.appcompat.app.AppCompatActivity; 
import androidx.core.graphics.Insets;  
import androidx.core.view.ViewCompat;  
import androidx.core.view.WindowInsetsCompat; 
public class MainActivity extends AppCompatActivity  
{     @Override     protected void onCreate(Bundle 
savedInstanceState)  
    {  
        super.onCreate(savedInstanceState);         
setContentView(R.layout.activity_main);  
    }  
    @Override  
    public boolean onCreateOptionsMenu(Menu menu)  
    {  
        getMenuInflater().inflate(R.menu.main_menu,menu);         
return true;     }  
    @Override     public boolean 
onOptionsItemSelected(MenuItem item)  
    {  
        if (item.getItemId()==R.id.simple_dialog)  
        {  
ANDROID PROGRAMMING
 
  
           showSimpleDialog();             
return true;  
        }  
        if(item.getItemId()==R.id.dialog_fragment)  
        {  
            MyDialogFragment dialog=new MyDialogFragment();             
dialog.show(getSupportFragmentManager(),  
                    "MyDialog");             
return true;  
        }  
        return super.onOptionsItemSelected(item);  
    }  
    private void showSimpleDialog()  
    {  
        AlertDialog.Builder builder=new AlertDialog.Builder(this);         
builder.setTitle("simple  dialog");         builder.setMessage("this 
is simple dialog");         
builder.setPositiveButton("OK",(dialog,which)->  
                Toast.makeText(this,"Ok Clicked",Toast.LENGTH_SHORT).show());         
builder.show();  
    }  
}  
activity_main.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout  
    xmlns:android="http://schemas.android.com/apk/res/android"     
android:layout_width="match_parent"     
android:layout_height="match_parent"   
android:orientation="vertical"      
android:gravity="center">  
    <TextView         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
 
  
android:text="this is menu box"         
android:textSize="20sp" />  
</LinearLayout>  
 
main_menu.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<menu xmlns:android="http://schemas.android.com/apk/res/android">  
    <item         
android:id="@+id/simple_dialog"         
android:title="Simple Dialog"/>  
    <item         
android:id="@+id/dialog_fragment"         
android:title="Dialog fragment"/>  
</menu>  
 
MyDialogFragment.java:  
package com.example.mydialoguefragment;  
import android.app.Dialog;  
import android.os.Bundle;  
import androidx.annotation.NonNull;  
import androidx.appcompat.app.AlertDialog;  
import androidx.fragment.app.DialogFragment;     
public class MyDialogFragment extends DialogFragment{  
        @NonNull         
@Override  
        public Dialog onCreateDialog(Bundle savedInstanceState) {             
AlertDialog.Builder builder=new AlertDialog.Builder(getActivity());             
builder.setTitle("dialog Fragment");             builder.setMessage("this is 
dialog fragment");             builder.setPositiveButton("OK",(dialog,which)->                    
dismiss());             return builder.create();  
        }  
    }  
```

## Output
(Refer practical output screenshot in PDF)

---

# practical 7

## AIM
Aim:Programs on Intents,Event,Listeners and Adapters The Android Intent 
class,using Events and event listeners. 
## Input


```
MainActivity.java:  
package com.example.p7;  
import android.content.Intent;  
import android.net.Uri;  
import android.os.Bundle;  
import android.widget.ArrayAdapter;  
import android.widget.Button;  
import android.widget.ListView;  
import android.widget.Toast;  
import androidx.activity.EdgeToEdge;  
import androidx.appcompat.app.AppCompatActivity; 
import androidx.core.graphics.Insets;  
import androidx.core.view.ViewCompat;  
import androidx.core.view.WindowInsetsCompat;  
public class MainActivity extends AppCompatActivity {  
    Button btnExplicit,btnImplicit,btnClick;  
    ListView listView;  
    String fruits[]={"Apple","Banana","Mango","Orange"};  
    @Override     protected void onCreate(Bundle 
savedInstanceState) {         
super.onCreate(savedInstanceState);         
setContentView(R.layout.activity_main);         
btnExplicit=findViewById(R.id.btnExplicit);         
btnImplicit=findViewById(R.id.btnImplicit);         
btnClick=findViewById(R.id.btnClick);         
listView=findViewById(R.id.listView);         
btnExplicit.setOnClickListener(v->{  
            Intent i=new Intent(MainActivity.this,SecondActivity.class);             
startActivity(i);  
 
  
        });  
        btnImplicit.setOnClickListener(v->{  
            Intent i=new Intent(Intent.ACTION_VIEW, Uri.parse("https://google.com"));             
startActivity(i);  
        });  
        btnClick.setOnClickListener(v->{  
            Toast.makeText(MainActivity.this,"button  
Clicked!",Toast.LENGTH_SHORT).show();  
        });  
        ArrayAdapter<String>adapter=new   
ArrayAdapter<>(this, android.R.layout.simple_list_item_1,fruits);         
listView.setAdapter(adapter);  
        listView.setOnItemClickListener( (parent,view,position,id)->                 
Toast.makeText(MainActivity.this,"You 
selected:"+fruits[position],Toast.LENGTH_SHORT).show());  
    }  
}  
 
activity_main.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"     
android:id="@+id/main"      
android:layout_width="match_parent"     
android:layout_height="match_parent"     
 android:gravity="center"     
 android:orientation="vertical"     
 android:padding="20dp">  
    <Button         
android:layout_width="match_parent"         
android:layout_height="wrap_content"         
android:text="Open Second Activity"         
android:id="@+id/btnExplicit" >  
    </Button>  
      
 
  
<Button         
android:layout_width="match_parent"         
android:layout_height="wrap_content"         
android:text="Open Google"         
android:id="@+id/btnImplicit">  
</Button> 
     
 <Button         
android:layout_width="match_parent"         
android:layout_height="wrap_content"         
android:text="Click Event"         
android:id="@+id/btnClick">  
    </Button>     <ListView         
android:id="@+id/listView"         
android:layout_width="match_parent"         
android:layout_height="match_parent"/>  
</LinearLayout>  
  
activity_second.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"     
android:id="@+id/main"      
android:layout_width="match_parent"     
android:layout_height="match_parent"     
 android:gravity="center"     
 android:orientation="vertical">  
    <TextView         
android:layout_width="wrap_content"         
android:layout_height="wrap_content"         
android:text="This is second activity"         
android:textSize="22sp"/>  
</LinearLayout>  
```

## Output
(Refer practical output screenshot in PDF)

---

## practical 8
## Aim
Aim: Program on Services, Notification and Broadcast Receiver.
## Input 

```
Broadcast Receiver
1.activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="BROADCAST RECEIVER"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.556"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.084" />

</androidx.constraintlayout.widget.ConstraintLayout>

2. AirplaneMode.java
package com.example.broadcast;

import android.content.BroadcastReceiver;
import android.content.Context;
import android.content.Intent;
import android.provider.Settings;
import android.widget.Toast;

public class AirplaneMode extends BroadcastReceiver {
    @Override
    public void onReceive(Context context, Intent intent) {
        if (isAirplaneModeOn(context.getApplicationContext())){
            Toast.makeText(context, "Airplane Mode On", Toast.LENGTH_SHORT).show();
        }else{
            Toast.makeText(context, "Airplane Mode Off", Toast.LENGTH_SHORT).show();
        }
    }

    private static boolean isAirplaneModeOn(Context context) {
        return Settings.System.getInt(context.getContentResolver(), Settings.Global.AIRPLANE_MODE_ON, 0) != 0;
    }

}

3. MainActivity.java
package com.example.broadcast;

import android.content.Intent;
import android.content.IntentFilter;
import android.os.Bundle;

import androidx.activity.EdgeToEdge;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.graphics.Insets;
import androidx.core.view.ViewCompat;
import androidx.core.view.WindowInsetsCompat;

public class MainActivity extends AppCompatActivity {
    AirplaneMode airplaneMode = new AirplaneMode();

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        EdgeToEdge.enable(this);
        setContentView(R.layout.activity_main);
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main), (v, insets) -> {
            Insets systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars());
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom);
            return insets;
        });
    }

    @Override
    protected void onStart() {
        super.onStart();
        IntentFilter intentfilter = new IntentFilter(Intent.ACTION_AIRPLANE_MODE_CHANGED);
        registerReceiver(airplaneMode, intentfilter);

    }

    @Override
    protected void onStop() {
        super.onStop();
        unregisterReceiver(airplaneMode);
    }
}
```

## Output
(Refer practical output screenshot in PDF)

---

# practical 9

## Aim
Database Programming with SQLite.

## Input
```
activity_main.xml:  
<?xml version="1.0" encoding="utf-8"?>  
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"     
android:layout_width="match_parent"     
android:layout_height="match_parent" >  
    <LinearLayout         
android:layout_width="match_parent"         
android:layout_height="wrap_content"         
android:orientation="vertical"         
android:padding="20dp">  
        <EditText             
android:layout_width="match_parent"             
android:layout_height="wrap_content"             
android:id="@+id/etName"             
android:hint="Enter Name(Insert)" />  
        <Button             
android:layout_width="wrap_content"             
android:layout_height="wrap_content"             
android:id="@+id/btnAdd"             
android:text="Save"             
android:layout_marginTop="10dp"/>  
        <EditText  
            android:layout_width="match_parent"             
android:layout_height="wrap_content"             
android:id="@+id/etUpdateId"              
android:hint="Enter ID to Update"             
android:layout_marginTop="25dp"/>  
        <EditText             
android:layout_width="match_parent"             
android:layout_height="wrap_content"             
 
  
android:id="@+id/etUpdateName"             
android:hint="New Name"/>  
        <Button             
android:layout_width="wrap_content"             
android:layout_height="wrap_content"             
android:id="@+id/btnUpdate"             
android:text="Update"             
android:layout_marginTop="10dp"/>  
        <EditText             
android:layout_width="match_parent"             
android:layout_height="wrap_content"             
android:id="@+id/etDeleteId"             
android:hint="Enter ID to Delete"             
android:layout_marginTop="25dp"/>  
        <Button             
android:layout_width="wrap_content"             
android:layout_height="wrap_content"             
android:id="@+id/btnDelete"             
android:text="Delete" />  
        <Button             
android:layout_width="wrap_content"             
android:layout_height="wrap_content"             
android:id="@+id/btnShow"             
android:text="Show All"             
android:layout_marginTop="25dp"/>  
        <TextView             
android:layout_width="match_parent"             
android:layout_height="wrap_content"             
android:id="@+id/tvResult"             
android:textSize="18sp"             
android:layout_marginTop="20dp"/>  
    </LinearLayout>  
</ScrollView>  
  
 
  
MainActivity.java:  
package com.example.p9;  
import androidx.appcompat.app.AppCompatActivity; 
import android.os.Bundle;  
import android.widget.*;  
public class MainActivity extends AppCompatActivity {     
EditText etName, etUpdateId, etUpdateName, etDeleteId;  
    Button btnAdd, btnShow, btnUpdate, btnDelete;  
    TextView tvResult;  
    DBHelper db;      
@Override     protected void onCreate(Bundle 
savedInstanceState) {         
super.onCreate(savedInstanceState);         
setContentView(R.layout.activity_main);          
etName = findViewById(R.id.etName);          
etUpdateId = findViewById(R.id.etUpdateId);         
etUpdateName = findViewById(R.id.etUpdateName);         
etDeleteId = findViewById(R.id.etDeleteId);          
btnAdd = findViewById(R.id.btnAdd);          
btnShow = findViewById(R.id.btnShow);          
btnUpdate = findViewById(R.id.btnUpdate);         
btnDelete = findViewById(R.id.btnDelete);          
tvResult = findViewById(R.id.tvResult);          
db = new DBHelper(this);         
btnAdd.setOnClickListener(v -> {  
            String name = etName.getText().toString();             
if (db.insertName(name)) {  
                Toast.makeText(this, "Inserted!", Toast.LENGTH_SHORT).show();                 
etName.setText("");  
            } else {  
                Toast.makeText(this, "Error inserting!", Toast.LENGTH_SHORT).show();  
            }  
        });  
  
 
  
        btnUpdate.setOnClickListener(v -> {  
            int id = Integer.parseInt(etUpdateId.getText().toString());             
String newName = etUpdateName.getText().toString();             if 
(db.updateName(id, newName)) {  
                Toast.makeText(this, "Updated!", Toast.LENGTH_SHORT).show();  
            } else {  
                Toast.makeText(this, "ID not found!", Toast.LENGTH_SHORT).show();  
            }  
        });  
        btnDelete.setOnClickListener(v -> {             int id = 
Integer.parseInt(etDeleteId.getText().toString());             if 
(db.deleteName(id)) {  
                Toast.makeText(this, "Deleted!", Toast.LENGTH_SHORT).show();  
            } else {  
                Toast.makeText(this, "ID not found!", Toast.LENGTH_SHORT).show();  
            }  
        });  
        btnShow.setOnClickListener(v -> {             
String data = db.getAllNames();             
tvResult.setText(data);  
        });  
    }  
}  
  
DBHelper.java:  
package com.example.p9;  
import android.content.ContentValues;  
import android.content.Context;  
import android.database.Cursor;  
import android.database.sqlite.SQLiteDatabase;  
import android.database.sqlite.SQLiteOpenHelper;  
 
public class DBHelper extends SQLiteOpenHelper {     
public static final String DB_NAME = "StudentDB";     
  
  
public static final String TABLE_NAME = "students";     
public DBHelper(Context context) {         
super(context, DB_NAME, null, 1);  
    }  
    @Override     public void 
onCreate(SQLiteDatabase db) {  
        db.execSQL("CREATE TABLE " + TABLE_NAME + "(id INTEGER PRIMARY  
KEY AUTOINCREMENT, name TEXT)");  
    }  
    @Override     public void onUpgrade(SQLiteDatabase db, int oldVersion, int 
newVersion) {         db.execSQL("DROP TABLE IF EXISTS " + 
TABLE_NAME);         onCreate(db);  
    }  
    public boolean insertName(String name) {         
SQLiteDatabase db = this.getWritableDatabase();         
ContentValues cv = new ContentValues();         
cv.put("name", name);         long result = 
db.insert(TABLE_NAME, null, cv);         return result 
!= -1;  
    }  
    public boolean updateName(int id, String newName) {  
        SQLiteDatabase db = this.getWritableDatabase();         
ContentValues cv = new ContentValues();         cv.put("name", 
newName);  
        int result = db.update(TABLE_NAME, cv, "id=?", new String[]{String.valueOf(id)});         
return result > 0;  
    }  
    public boolean deleteName(int id) {  
        SQLiteDatabase db = this.getWritableDatabase();          
int result = db.delete(TABLE_NAME, "id=?", new String[]{String.valueOf(id)});         
return result > 0;  
    }  
    public String getAllNames() {  
        SQLiteDatabase db = this.getReadableDatabase();  
 
  
        Cursor cursor = db.rawQuery("SELECT * FROM " + TABLE_NAME, null);         
StringBuilder sb = new StringBuilder();         while (cursor.moveToNext()) {             
sb.append(cursor.getInt(0))  
                    .append(" - ")  
                    .append(cursor.getString(1))  
                    .append("\n");  
        }         
cursor.close();         
return sb.toString();  
    }  
} 
```

## Output
(Refer practical output screenshot in PDF)

---

