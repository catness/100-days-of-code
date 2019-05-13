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


### Day 5: 2019-05-05

* Refactored database exporting as an Async task.

* Added the Import option, which deletes the database and imports from a predefined .json file (previously exported and placed to the directory manually - there's really no way to make it both safe and user-friendly).

* Added bulk insert methods and synchronized methods to the data repository, to use with Import, which is an Async task anyway.

* Renamed debug preference section to development; added preferences to show/hide Export and Import in the main menu.

(Normally, export/import should be rarely used - e.g. only upon reinstalling the app on a new phone. Or if something gets screwed up... ;)

* Removed the export to internal memory option because it's useless; moved the export mode setting to the development settings.

* Replaced the graphics for level-up dialog with royalty free graphics. (Against all the design principles, I'm using an ornamental frame, like in old adventure games, because I like eye candy.)

Note: the [online 9-patch generator](http://romannurik.github.io/AndroidAssetStudio/nine-patches.html)is amazingly user-friendly!

### Day 6: 2019-05-06

* Added the dark mode! And the setting to toggle between dark and light mode in preferences, [according to this explanation](https://carthrottle.io/how-to-implement-flexible-night-mode-in-your-android-app-f00f0f83b70e). Still need to fix a few elements.

### Day 7: 2019-05-07

* Fixed the rest of the dark mode settings: the levelup message, calendar and preferences editText dialog. The latter took hours (here's one resource: [Customize Alert Dialog style](http://joerg-richter.fuyosoft.com/?p=181) ) but it still has a weird white frame around it, which I'm unable to eliminate no matter what. But for now, it's good enough.

Note: the 9-patch png images can be re-colored in the image editor, but the 1-pixel border around them has to stay black, otherwise the project doesn't even compile!

### Day 8: 2019-05-08

* Added an option of export to SD card if it exists (which is not the same as export to external memory...)

* Started to fix lint warnings. 

### Day 9: 2019-05-09

* Implemented swipe on report calendar day view, to go directly to the next/previous day.

* Fixed a few bugs (e.g. canceling "edit report" from the calendar was returning to the main activity, not to the calendar), and layout problems.

### Day 10: 2019-05-10

* Refactored both report list activities to eliminate duplicate code.

* Implemented swipe on the empty calendar days.

* Removed the Paged adapter on the main screen (it didn't work as expected, and there's no need for it as the Calendar page is more convenient), and added a setting for the max number of reports to show.

### Day 11: 2019-05-11

* Replaced the text "edit datetime" field for reports with date and time picker widgets.

* Removed the export database dependency on LiveData, made it fully asynchronous, cleaned up export/import code.

### Day 12: 2019-05-12

* Replaced the color picker with a better one which supports the dark mode.

* Fixed the init issues upon (re)installing the app.

* Fixed the drag&drop of subjects, though not completely.

* Fixed a few layout issues.

### Day 13: 2019-05-13

* Fixed the drag&drop of subjects for good!! It was damn tricky to get rid of the flicker while the data is updating.

* Fixed the issue with initial color of the new subject.
