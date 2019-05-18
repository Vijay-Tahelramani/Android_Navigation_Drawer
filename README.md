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
The Activity with the drawer layout contains The Layout for Main Content and the Navigation View. It is required to create the toolbar for the Navigation Drawer, because Default app bar does not support the Navigation Drawer.
Navigation Drawer is created using NavigationView.
So see the code of ```activity_main.xml``` copy it in your xml file.

To add the content to Navigation View, create menu file and put all the items you want.
