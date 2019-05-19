# Android_Navigation_Drawer
This Android tutorial implements the navigation drawer (Side Menu).

First, create a project with empty activity.

To add navigation drawer in application, it requires to add following library to the  project. So, copy below line in your Project's ```Build.gradle (Module: App)``` file inside dependencies section.
```
implementation 'com.android.support:design:28.0.0'
```
Now, Change your the layout of ```acitivity_main.xml``` to the the drawer layout, and add the following lines of code to drawer layout.
```
android:id="@+id/drawer_layout"
android:fitsSystemWindows="true"
tools:openDrawer="start"
```
Using only drawer layout, we can get the Navigation Drawer in project.
The Activity with the drawer layout contains The Layout for Main Acitivty Content, the navigation view and toolbar. It is required to create the toolbar for the Navigation Drawer, because Default app toolbar does not support the Navigation Drawer.
Navigation Drawer is created using NavigationView.
So see the code of ```activity_main.xml``` copy it in your xml file.

Here in Navigation View we can add the content using menu and header layout. Using below code that I have added in my navigation View.
```
app:headerLayout="@layout/nav_header_main"
app:menu="@menu/activity_main_drawer"
```

To add the content to Navigation View, create menu file and put all the items you want. See the code of ```activity_main_drawer.xml```, I have created group of items so that user it stays only on item selected at a time.

To add the header layout create new layout file and place all the content you want to add in your drawer. I have created ```nav_header_main.xml``` file.

Now, we also need to remove the Default app toolbar from our activity so we need to change the Style of our Activity. So open the styles.xml from res>values>styles.xml folder. Keep the default style as it is and create new style for the activity just below the default acitivty add following code to your ```styles.xml```.
```
<style name="AppTheme.NoActionBar">
     <item name="windowActionBar">false</item>
     <item name="windowNoTitle">true</item>
 </style>
 ```
 
 For your application's version 21 or above we can put the status bar color transparent when the drawer is open. To do that create new styles.xml with version specified to 21.
 Add the following code to your ```styles.xnl(v21)``` file.
 ```
 <?xml version="1.0" encoding="utf-8"?>
<resources>
    <style name="AppTheme.NoActionBar">
        <item name="windowActionBar">false</item>
        <item name="windowNoTitle">true</item>
        <item name="android:statusBarColor">@android:color/transparent</item>
    </style>
</resources>
```
Now Add these style to your MainActivity through ```AndroidManifest.xml```. Add the following dode to your Activity tag.
```
<activity android:name=".MainActivity" android:theme="@style/AppTheme.NoActionBar">
```
Now, Move to the ```MainActivity.java``` code to add the navigation drawer to your app.
First, create the instance of drawer_layout, navigationView and tool bar. To create instance of Navigationiew class will implement the ```NavigationView.OnNavigationItemSelectedListener``` and override it's method. Here It has a method ```onNavigationItemSelected()```. Then we need to configure the AppBar using the ```ActionBarDrawerToggle```, add the following code to your ```onCreate()``` method.
```
drawerLayout = (DrawerLayout)findViewById(R.id.drawer_layout);
toolbar = (Toolbar)findViewById(R.id.toolbar);
setSupportActionBar(toolbar);
navigationView = (NavigationView)findViewById(R.id.nav_view);
navigationView.setNavigationItemSelectedListener(this);

ActionBarDrawerToggle toggle = new ActionBarDrawerToggle(
      this, drawerLayout, toolbar, R.string.navigation_drawer_open, R.string.navigation_drawer_close);
      drawerLayout.addDrawerListener(toggle);
toggle.syncState();
```

Then when your Navigation Drawer is open and back button is pressed the drawer should be closed inted of closing the activity.
For that override the ```OnBackPressed()``` method.
Add the following method. in your ```MainAcivity.java```
```
@Override
public void onBackPressed() {
    if (drawerLayout.isDrawerOpen(GravityCompat.START)) {
          drawerLayout.closeDrawer(GravityCompat.START);
    } 
    else {
          super.onBackPressed();
    }
}
```
Action's for the menu items will be created inside ```onNavigationItemSelected()``` method. whenever the any menu item is selected it will close the drawer the layout and perform the action.

Now run the project and you will see your drawer layout working.

Screen Preview:<br/>
<img src="https://github.com/Vijay-Tahelramani/Android_Navigation_Drawer/blob/master/Images/sidemenu.png" width="250" />
