# 100 Days Of Code - Log

### Day 1: 2019-05-01

* Added the Settings menu with one setting so far, to turn the sound off/on. 

I created the Android Studio "Settings Activity" to ensure that I'm not using any deprecated code from the online tutorials, and then deleted all the unnecessary stuff from it (but it's good to know that there is sample code for all kinds of settings), and customized the rest, using mostly [this guide](https://medium.com/@bhavyankaria/step-by-step-guide-to-create-app-settings-using-preferences-in-android-part-1-fa470305b530) as a reference. For me, the Settings/Preferences is still a black box with goodies, but as long as I can manipulate it to serve my purposes, it's all fine.

* Added the date title separator between the reports on the main page. 

This one I did from scratch without any copy/paste, by adding a TextView for the date to the report list item, and hiding it in the adapter for all the items except those where the date changes.



### Day 2: 2019-05-02

* Added the Debug section to settings, with the option to show/hide the Reset item in the main menu. (An additional protection from deleting stuff by mistake.) Here's the [resource for icons](https://material.io/tools/icons/).

* Added the header with today's date and points on the main reports page. Adjusted the colors.

* Changed the Floating Action Button to be movable (from [this Stack Overflow example](https://stackoverflow.com/questions/46370836/android-movable-draggable-floating-action-button-fab)  )

* Tried to fix the reordering of subjects; replaced 2 async tasks (updating each subject's position independently) with 1 task (swap positions). The dragging still stops after the first swap. Apparently every change in LiveData causes the adapter to reload all the data, and resets the ItemTouchHelper state of dragging. I don't know how to deal with it yet.


### Day 3: 2019-05-03

* Added database export to json, using [Jackson Object Mapper](https://www.codexpedia.com/java/jackson-parser-example-in-android/), and saving it to a [file on external storage](https://developer.android.com/training/data-storage/files).

(Pleasantly surprised how easy it is with the Room database. I didn't have to do anything with SQLite at all, just converted the objects from the view models.)

* Added sending the file as an attachment by email. [Here's how to make the application files accessible.](https://stackoverflow.com/questions/48117511/exposed-beyond-app-through-clipdata-item-geturi) 

(Actually, it should not be necessary to read the file, but sending the json string directly as an attachment didn't work. But it's nice to know how to send files anyway.)

Note: the easiest way to pretty-print a json file on command line:

`python3 -m json.tool < FILENAME`

### Day 4: 2019-05-04

* Added the setting to export database either to external or internal storage or to email (in that case, saving to the cache, and deleting the file afterwards). 

Note: the files can be accessed through Device Explorer in Android Studio; external storage also through Android apps (I use Ghost Commander).

* Added the setting to change the toolbar title throughout all the activities.

(So the user can call it Hogwarts, or Unseen University, or Starfleet Academy, or whatever, according to their theme; without the developer running into any copyright problems.)
