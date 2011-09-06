SFACT
=
is a more prectical and easier to tune derivative of Skeinforge.  

# Features

## General

* Will not mess up your old Skeinforge settings as it will use its own settings, located in the **sfact_profiles** directory, inside its own folder.

* Deleted unused plugins and unused settings.

* Namings changed to be more understandable.

* Important settings moved to top of Plugin Tab.

* Default values give good prints rightaway.

* Internally used Gcode files use extension .gmc now.

* Most Feedrates are now entered as values (mm/s) and their respective flowrates are 1 so you dont have to enter everything twice.

## Specific
### CARVE

* Extrusion width is now entered in mm insteda of a ratio to layer height.

### CHAMBER

* Moved Turn Extruder off at shutdown to Chamber.

* Added Turn PrintBed off at shutdown.

### CLIP 

* Clip over Perimeter width is now calculated automatically.  The default is 1 and can be tuned from there.

### DIMENSION

* Added feature for calibration.

* Retract can be set conditionally depending on extrusion amount before retract and the travel move in retracted state (SF Beanshell).  Also retract can be forced to happen if moving over loops.

### EXPORT

* Replaced existing Export plugin with [Gary Hodgson's Export plugin](https://github.com/garyhodgson/skeinforge/blob/master/skeinforge_application/skeinforge_plugins/craft_plugins/export.py).
Gary discusses the features of the plugin [here](http://garyhodgson.com/reprap/2011/06/hacking-skeinforge-export-module/).  

* Option to export settings as Zip file or a single CSV file for sharing.

* Option to individually name the exported gcode files with description, timestamp and profile used.

### FILL

* Infill width over layerthickness setting is replaced by Extrusion Lines Extra spacing.

* Extrusion Lines Extra spacing is calculated automatically and defaults to 1 for tuning.

* Infill Overlap over Perimeter is also calculated internally and defaults to 1 so it can be easily tweaked.

### INSET

* The inset value is now Overlap Removal and is also calculated internally with default 1 for tweaking.

### PREFACE

* Added the option to send Extruder reset (G92 E0) command before print so that the extruder does not spool back after priming - even without start.gmc file.

### RAFT

* Ordering, grouping and namings changed to reflect the use of interface settings for the support structures.

* Support feedrate and support flowrate can be set seperately.

* Support extension(s) are now more understandable.

* First Layer feedrates are given in mm/s instead of a ratio to the main feedrate.

### SPEED

* Feedrates are entered as values with respective flowrates as 1, instead of entering same value again - except for Bridge Feedrate.

* Nozzle Lift setting has been changed to Extra nozzle Lift over object and defaults to 0.

* Wipe is on by default and is around the 0 point.


# Getting SFACT

The latest working version is available here:
http://www.reprapfordummies.net/downloads/SFACT.rar

The latest development version is here:
https://github.com/ahmetcemturan/SFACT


# Using SFACT

You need to have Python installed. If you had Skeinforge running before, your Python installation is sufficient. If you don't yet have Python installed, kliment's Printrun [readme](https://github.com/kliment/Printrun/blob/master/README.md) covers installing the required Python core and modules on various platforms.

**NOTE:** If you intend using SFACT with Pronterface, the section [Using SFACT with Pronterface](#uswp), (below) details the required directory structure.

1. Extract the contents of the downloaded SFACT compressed file to a folder of your choice.

2. Go to the **skeinforge_application** folder and run *skeinforge.py*

3. Go to the **DIMENSION** tab and enter your "measured" filament diameter.

4. In the **CARVE** tab enter reasonable Layer height and Extrusion width values. (Try to have layer height slightly less than nozzle diameter and Extrusion width slightly more than nozzle diameter.)

5. Click **Skeinforge** in the bottom left corner and choose the STL file to slice.

6. Generated Gcode will be saved to the same folder as the STL file.

7. *Enjoy good Prints!*

## Calibration

If you need to calibrate:

1. Print a file from the folder **single_wall_calibration_parts**, (or a [Single walled test piece](http://www.thingiverse.com/thing:1637) which also available in this [Calibration set](http://www.thingiverse.com/thing:2064)).

2. Measure the width of the wall.

3. Go to **DIMENSION** and check the Calibration Checkbox.

4. Enter the Measured value.

5. Re-Skein and print the object. During the Skein the command window will display a packing ratio.  Note it somewhere - the first four digits are enough.

6. If satisfied with the print, go to **DIMENSION** tab uncheck the calibration checkbox and enter that value into the packing density Box.

7. You are done.  Repeat when needed.  Changing extrusion values should not necessarily require the need for recalibration.

## Using SFACT with Pronterface

Copy all the SFACT files and sub-folders into a folder called **skeinforge** within the **Pronterface** folder.  Then, copy (or move) the **sfact_profiles** folder from the SFACT root folder into the **Pronterface** folder. Without doing so, SFACT won't see the default profiles shipped with it.

**Pronterface directory structure - pre SFACT:**

    C:\
    ___path_to_Pronterface
    ______Pronterface
    _________locale

**Pronterface + SFACT directory structure:**

    C:\
    ___path_to_Pronterface
    ______Pronterface
    _________locale
    _________sfact_profiles
    _________skeinforge
    ____________[SFACT files and folders go here]


# Bugs

No known bugs.

If you find a bug, please raise an issue here:
https://github.com/ahmetcemturan/SFACT/issues

And/or fork this project, correct the problem and submit a pull request.

# Licence

License is same as Skeinforge (GNU Affero General Public License).