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


