# 100 Days Of Code - Log

## Project : Classroom points app

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

### Day 14: 2019-05-14

* Improved the display of current day's points. 

* Added numeric types to EditText whenever necessary. 

* Started refactoring and cleanup of the code. (We're on the home stretch!)

(Note: besides ./gradlew lint, there's an Android Studio tool : right-click -> Analyze -> Inspect code)

### Day 15: 2019-05-15

* Fixed the points display bug caused by SimpleDateFormat being not thread safe (!!!) by replacing it with DateTimeFormatter. 

* Fixed potential layout overlaps.

* Refactored the code into different directories/packages.

* Continuing with the code & resources cleanup.

### Day 16: 2019-05-16

* Fixed the calendar/daily reports so they return to the correct month

* Fixed the "static leak" warnings in Async tasks by using the weak references

* Moved export & import tasks to their own files

* Finished refactoring & cleanup for now


## New project : the Unicode glyphs game app

### Day 17: 2019-05-17

* Set up the initial app

* Tried out custom ttf fonts and gradient color (it works)

* Still experimenting with the layout for the main screen. Grid layout causes problems when adding views dynamically. (And I thought that Android layouts would be easier than LibGDX scene2d...)

### Day 18: 2019-05-18

* After a lot of struggle, created a reasonable layout (with dynamically added views) for the main screen, using the functions to get the current screen size, toolbar size etc to calculate the dimensions. So far it's not any easier than with LibGDX.

* Started with the BoardItem class.

### Day 19: 2019-05-19

* Added BoardPanel and InputPanel (partially) with the appropriate item classes.

* Started implementing the interaction.

### Day 20: 2019-05-20

* Added the animated timer bar and connected it to the character input

* Made the characters selectable in any order

* Added more symbols from the font

* Started working on the status panel

* Added debugging options for the board.

### Day 21: 2019-05-21

* Rescalling the characters to fit the board

* The score panel, updating the score

* Fade in/out for the board characters

* "Game over" message; restarting after game over

### Day 22: 2019-05-22

* Refactored the code, moving all the gameplay logics from the MainActivity into appropriate classes

* Created a separate class for the progressbar workaround

* Got rid of hardcoded strings and colors

### Day 23: 2019-05-23

* Added the settings menu, with the options to select font, set debug on/off, and change text colors (the last one not implemented yet)

* Refactored the font definitions, moved them to a separate class.

* Implemented font selection from the preferences. 

* Found why it doesn't work with some fonts (1 character is a string.substring of length 2, not 1), didn't fix yet.


### Day 24: 2019-05-24

* Fixed the rendering of wide-character fonts

* Implemented changing the text color from the settings (and fixed updating of the preview thumbnail by a workaround)

* Made the character cell fixed size (still not 100%)

* Added the hint option for debugging

Note: [The preferences color picker](https://github.com/martin-stone/hsv-alpha-color-picker-android)

### Day 25: 2019-05-25

* Started with the Powerup widgets - a complicated layout with a circular progress bar around a symbol. They look ok now, but I still have no idea why they refuse to be resized, why there's extra padding which doesn't go away, and why the only way to fix it seems to be rescaling the layout.

Note: [A great example of circular progress bar](https://demonuts.com/circular-progress-bar)

### Day 26: 2019-05-26

* Implemented all the (currently planned) powerups! Enhanced their layout and appearance; organized them into separate classes.

* Added more fonts, enhanced the appearance of some icons.

* Fixed the bug with "tall" characters.

### Day 27: 2019-05-27

* Refactored glyphs setup, changed the settings menu to load the list dynamically

* Added several parameters to control the fonts dynamically

* Changed the score number to progress bar, added the bonuses indicator 

* Enhanced the hint appearance

* Added more fonts

### Day 28: 2019-05-28

* Revamped the main layout, extending the powerups panel to the bottom

* Implemented speeding up the timer

* Fixed the timer bar (properly instead of the workaround)

* Added the sample text to test the colors in the settings menu

* Added more fonts

### Day 29: 2019-05-29

* Added the SQL database! (Room/LiveData) 

* Now the powerups are stored in / retrieved from the database.

* Added a nice launcher icon.

### Day 30: 2019-05-30

* Added the dex activity with the grid view 

* Implemented displaying the font (both UTF-8 and UTF-16) (without the database yet) according to the preferences

* Added opening the browser to show extended info for the selected character

Notes:
- https://www.raywenderlich.com/995-android-gridview-tutorial
- https://stackoverflow.com/questions/14171755/custom-scrollbar-android (though doesn't work with the fastscroll)
- https://hajsoftutorial.com/java-supplementary-characters-utf-16-encoding
- https://graphemica.com


### Day 31: 2019-05-31

* Created the database interface for the characters

* Added all the fonts except for utf16 for now

* Added the list of selected characters sorted by count after each gameover

* Saving several random characters to the database upon gameover (except for utf16)

### Day 32: 2019-06-01

* Connected the dex activity to the database

* Updated the algorithm of picking the characters to save to the db

* Located the problem with characters missing from the font

* Added pause/resume option for debugging

### Day 33: 2019-06-02

* Added all the handling for utf-16 fonts

* Fixed pageback for debugging

* Revamped the dex layout, added stars

* Cleaned up the nonexistent characters

* Added debugging option in the settings to add/remove characters manually


### Day 34: 2019-06-03

* Added several levels of stars and bonuses, with different colors

* Changed the score calculation to take the bonuses into account

* Updated the way of picking the characters for the dex


### Day 35: 2019-06-04

* Added the gameover popup message - with a nice frame, different text for different levels, and the list of rewards

* Added a color "animation" in case of winning

* Updated the score bonuses 


### Day 36: 2019-06-05

* Added the (sort-of animated) loading screen to wait until the database is initialized

* Added the sound effects and on/off setting

* Fixed the dex layout centering


### Day 37: 2019-06-06

* Added the settings menu to the dex, implemented all the relevant optoins

* Refactored the levels-colors correspondence 

* Added some fonts

* Fixed the pause option to properly resume

* Fixed closing the gameover message


### Day 38: 2019-06-07

* Changed the temporary pause option into a proper powerup

* Split the source files into several packages

* Fixed part of the "code inspect" warnings


### Day 39: 2019-06-08

* Added color animation on the loading screen

* Continuing with the code cleanup / refactoring


### Day 40: 2019-06-09

* Added one more level

* Updated the gameover popup

* Added a "quick win" debugging option

* Fixed all the code inspect warnings


### Day 41: 2019-06-10

* Replaced some fonts with Google Noto

* Added more fonts

* Fixed most of the lint warnings

* More code cleanup (hardcoded strings, unnecessary logging, code duplication)

And that's all for the time being!

## Project : Classroom points app again

### Day 42: 2019-06-11

* Added the Theme database object and implemented the interface

* Added the Theme select/new/edit activities (without the actual levels yet)

### Day 43: 2019-06-12

* Added the Theme Levels database object and partially the interface

* Added all the Theme related activities to prototype the workflow

### Day 44: 2019-06-13

* Implemented all the Theme Levels workflow (except for the images)

* Realized that the app is becoming too bloated! It has to support level packs, but the level editor should be a separate application (preferably desktop or web-based). 

### Day 45:  2019-06-14

* Deleted the bloated theme packs code and updated it for the new format

* Implemented uploading and unzipping a zip file with the .json theme file and the images

* Implemented creating a new theme from the zip file (so far without the error checking etc)

### Day 46:  2019-06-15

* Implemented the rest of the theme management: activate & use (show the theme images and titles), switch between themes, delete the theme with all the files

* Checking for existing themes while uploading; rename the image directory if necessary

* Changed the reset option to reset only the level


### Day 47: 2019-06-16

* Fixed the theme interface in the dark mode

* Fixed unzipping the theme with a big json file

* Added a theme comment field

* Added checking for missing image files (save the message in comment)

* Fixed the initial points display while the db is not loaded

* Fixed the display of levels with missing images


### Day 48: 2019-06-17

* Added the setting to show/hide themes in the main menu

* Fixed the db migration

* Wrote a Python script to create a theme from a directory of images 

* Wrote a Python script to create the country flags theme sorted by approx. population, using the population dataset


## Project : desktop game development in C++/SDL

### Day 49: 2019-06-18

* Created the initial setup for the project, reworking some old code

### Day 50: 2019-06-19

* Added the camera, scrolling and scaling the background

### Day 51: 2019-06-20

* Added background layers and parallax scrolling

* Changed the world dimensions to be set up dynamically per scene

* Cleared the confusion between the viewport and the screen

### Day 52: 2019-06-21

* Implemented objects in the scene (static images so far), with clickable hotspots

### Day 53: 2019-06-22

* Implemented sprites: animated objects (non-moving), and objects with several states.

* Started implementing the object actions (on click).

### Day 54: 2019-06-23

* Added the avatar - an animated sprite controlled by arrows, simple movement so far.

* Implemented the scene scrolling automatically when the avatar approaches the edge. 2 kinds: incremental (bit by bit while it's in the center) and immediate (like a page turn when it's at the edge).
 
### Day 55: 2019-06-24

* Fixed the scrolling to make it smooth, and with the same speed as the avatar.

* Added collision detection with the room walking area and with the objects.

### Day 56: 2019-06-25

* Wrote a Python script to create an atlas (with SDL map) for a spritesheet

* Added a platformer-type avatar (only the movement so far, no collision detection)

### Day 57: 2019-06-26

* Added collision detection with the room background (partially).

* Fixed the mirrored spritesheet.

* Fixed handling the scene edges, the scrolling, and the flying animation.

### Day 58: 2019-06-27

* Improved the collision detection.

* Fixed some more animation bugs.

* Separated the code for adventure and platformer avatars, and added the compiler directive for easy switching.

### Day 59: 2019-06-28

* Started to create the inventory system.

* Added a "pickable" flag to pick an object on collision.

### Day 60: 2019-06-29

* Improved avatar/object collision in platformer mode.

* Implemented adding objects to inventory, including the possibility of multiple copies of the same item. (But it's still more of a proof of concept, needs some serious reworking.)

### Day 61: 2019-06-30

* Added the inventory screen overlay to display the items. (Very basic so far)

### Day 62: 2019-07-01

* Optimized the inventory to preload all the items in the scene, instead of creating on the fly.

* Added transparency and frame to the inventory overlay.  

### Day 63: 2019-07-02

* Started with the YAML parser to create the game definition file in a convenient format.

### Day 64: 2019-07-03

* Implemented the YAML parser for creating rooms and static (so far) objects / inventory items. 

### Day 65: 2019-07-04

* Continuing with the YAML parser: added the handling of multiple copies of the same object, and the sprites.
 
### Day 66: 2019-07-05

 * Yaml parser: added object/sprite action scripts, both embedded and as external files.

### Day 67: 2019-07-06

* Added the avatar to Yaml parser (2 types: platformer and adventure).

* Fixed Makefile dependencies, switched to using the include file generated by the Yaml parser.


### Day 68: 2019-07-07

* Added the messagebox overlay for simple messages.

* Displaying a message box with object description upon right-clicking.

### Day 69: 2019-07-08

* Fixed the messagebox position to stay near the clicked hotspot, and within the boundaries of the screen.

* Fixed calling the messagebox from object action scripts.

### Day 70: 2019-07-09

* Started handling room exits: loading another scene when the avatar triggers the hotspots. 

### Day 71: 2019-07-10

* Added unlocking a locked exit upon picking an item

* Added picking items on click (for adventure mode)

* Started adding global settings (so far pick on click / pick on collision)


### Day 72: 2019-07-11

* Select/deselect an inventory object, and drag the currently selected object around the screen.

### Day 73: 2019-07-12

* Using an inventory object on a scene object (via the object action script)

* Fixed the draggable inventory image dimensions 


### Day 74: 2019-07-13

* Added item counter to the inventory window

* Started implementing using inventory items on other items

### Day 75: 2019-07-14

* Implemented the mechanism of using inventory items on other items

* Added the inventory item-on-item action scripts to the yaml parser

* Fixed the message position for inventory actions


### Day 76: 2019-07-15

* Added the close-up item view for inventory screen

* Fixed the distinction between the item icon and close-up image 

* Fixed the multi-line item description in closeups


### Day 77: 2019-07-16

* Experimented with connecting the pathfinder algorithm for the avatar to follow the mouse clicks. So far it's too slow.

### Day 78: 2019-07-17

* Fixed the pathfinder's performance and implemented the walking

* Fixed the avatar's facing direction while walking the path

Notes: 
  * [The pathfinder algorithm I used](https://github.com/ActiveState/code/blob/master/recipes/C%2B%2B/577457_Astar_Shortest_Path_Algorithm/recipe-577457.cpp)
  * [Bresenham line algorithm](https://stackoverflow.com/a/32252934) which I use to find a reachable target when the original target is in the unreachable zone

### Day 79: 2019-07-18

* Fixed the pathfinder to take into account the objects in the room (besides the walkable areas).

* Added auto-scrolling and exiting to other rooms when following the path from the pathfinder.
 
### Day 80: 2019-07-19

* Started to add the option of trajectories for NPCs to follow.


### Day 81: 2019-07-20

* Implemented the NPC trajectories (loop and back&forth modes)

* Added trajectory handling to YAML parser

* Wrote a Python script to generate a simple line trajectory for testing

* Fixed the atlas-creating script to work with the older version of PIL

* Added the "hidden" property to objects


