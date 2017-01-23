# Validating and Rebuilding ROMs

In order to verify or rebuild a set, you need its corresponding DAT file and a software tool to process the DAT. DATs describe the ROM contents including filenames, file sizes, and checksums to verify contents are not incorrect or corrupt. The wiki pages for [MAME](https://github.com/RetroPie/RetroPie-Setup/wiki/MAME), [FB Alpha](https://github.com/RetroPie/RetroPie-Setup/wiki/FinalBurn-Alpha), and [Neo Geo](https://github.com/RetroPie/RetroPie-Setup/wiki/Neo-Geo) include DATs and detailed information about the ROM sets needed for the various arcade emulators.

Popular ROM verification tools include:

* [clrmamepro](http://mamedev.emulab.it/clrmamepro/) (Windows)
* [clrmamepro](http://www.emulab.it) (OSX)
* [romcenter](http://romcenter.com/) (Windows)
* [Romulus](http://romulus.net63.net/) (Windows)
* [RomVault](http://www.romvault.com/) (Windows)

All of the Windows tools can be run on Linux (x86) using [Wine](https://www.winehq.org/). **The remainder of this section will focus on clrmamepro for Windows, one of the most popular tools.**

## Video Tutorial

* [Easy ClrMamePro Tutorial](https://www.youtube.com/watch?v=_lssz2pAba8)

### Step 1 - Back up your ROMs
It is possible with clrmamepro to change one or two options and when it runs it will delete all your existing ROMs. OK, not really - using the default options it will make backups of any files it removes, but it is still possible to mess up their ROMs beyond repair when getting started with clrmamepro.

### Step 2 - Download [clrmamepro](http://mamedev.emulab.it/clrmamepro/#downloads)

### Step 3 - Acquire DAT files
You can download all .DAT files for all arcade emulators [**HERE**](https://github.com/HerbFargus/retropie-dat/archive/master.zip)
* For this tutorial, extract the zip file into `C:\` (but you can put it anywhere you want)
* Open retropie-dat-master and you should see a list of folders. Each folder contains the .DAT files for the respective emulator. We will only be using `C:\retropie-dat-master\mame4all\MAME 0.37b5.dat` in this tutorial.
* Create a subdirectory `C:\retropie-dat-master\mame4allroms` (this will be used in the next step)
* Create a subdirectory `C:\retropie-dat-master\pifbaroms`

### Step 4 - Run clrmamepro for the first time
* Run `C:\clrmamepro\cmpro64.exe`.  The welcome screen explains that common first steps are to 1) Create a Profile, 2) Set up your paths and 3) Scan your ROMs. We will be doing things slightly differently, in order to leave your source ROMs intact.  
* Click OK to the Welcome screen
* Click **"Add DatFile..."** and open the MAME4ALL DAT file at `C:\retropie-dat-master\mame4all\MAME 0.37b5.dat`
* Accept the default profile location of [PROFILES], click **"OK"**
* Select **"[NEW DATFILES]"** in the left-hand pane and select **"MAME 0.37b5"** in the right-hand pane
* Click **"Load / Update"**
* Clrmamepro will ask you how to generate the settings for this datfile, click **"Default"** (it is possible it will throw a warning but just select **"ok to all"** and continue on)
* You are now at the main window for clrmamepro.  We still need to set our paths, so click **"Settings"**
* Verify **"ROM-Paths"** is the selected option in the upper-left corner drop down menu
* Click the **"Add..."** button
* Select the folder you created in the last step called `C:\retropie-dat-master\mame4allroms` and click **"OK"**
* Close the settings window with the **"X"** button in the upper right

At this point, you could scan the ROMs folder you just selected, but we just created this folder and it is empty.  Instead, we will rebuild into this folder.

### Step 5- Rebuild a ROM set

* In the main clrmamepro window, select **"Rebuilder"**
* The destination should already be filled in for you - it is the same as the ROM path you defined above in the settings window: `C:\retropie-dat-master\mame4allroms`
* Use the browse button **"..."** to select your source path.  For example you might have a full set of MAME v0.156 ROMs - point clrmamepro to that directory as your source.
* When rebuilding there are three options: **Non-Merged, Merged, and Split**. (**NOTE**: Using Non-Merged ROMs is the most straightforward way to copy individual games to a RetroPie system.)

***
* **Non-merged**: All ROMs can be used standalone because each zip contains all the files needed to run that game, including any files from 'parent ROMs'. This is the recommended format for RetroPie arcade emulators.
* **Split**: Some ROMS that are considered clones, translations, or bootlegs also require a "parent ROM" to run. The parent ROM is often the first or most common variant of a game. In some cases the parent is not the most popular or best working version of the game, however. For example, in a Split set pacman.zip (a clone), will not work without puckman.zip (its parent).
* **Merged**: Clones are merged into the parent ROM zip, meaning that more than one game is stored per file. Merged ROM sets are not recommended.

***

* Click **"Rebuild..."**.  Depending on the size of the directory you chose as a source, this could take some time
* When clrmamepro is finished rebuilding, you will see a window with statistics showing how many matching files were found, how many files were created and how many were skipped.  Click "OK" 
* Repeat for any other source paths you might have.  You can rebuild from multiple sources, but leave the Destination path the same
* When finished, close the Rebuilder with the **"X"** in the upper right corner of the window

Time to find out how well your source ROMs matched up...

### Step 6 - Scan a ROM set
* In the main clrmamepro window, select **"Scanner"**
* Leave all settings at default and click **"New Scan..."**
* When clrmamepro finishes scanning, you will see a "Statistics" window with high level information and a "Scan Results" window with detailed information about your missing ROMs

### Repeat Steps 4 through 6 for the FBA ROM set#
* From clrmamepro "Profiler" window load the DAT file for PiFBA `C:\retropie-dat-master\pifba\fba_029671_od_release_10_working_roms.dat`
* From clrmamepro "Settings" windows set the ROM path to `C:\retropie-dat-master\pifbaroms`
* Use clrmamepro's "Rebuilder" to rebuild your existing ROMs to a new ROM set
* Scan the rebuilt ROMs using the "Scanner"

## Notes

That's the basics of using clrmamepro.  Some additional notes:

* Be careful with the "Fix" settings in the Scanner window and the "Remove Matched Sourcefiles" setting in the Rebuilder window. These settings will remove and rename your ROMs.
* If clrmamepro does delete any ROMs (because you told it to), you should be able to find backups in C:\clrmamepro\backup as long as you didn't change the default settings.
* clrmamepro is very stable.  It has been around for a long time, it is regularly updated and it is widely used.  If it reports problems reading your ROMs, you most likely have corrupt ROM archives (zip files) or a failing hard drive.

* If you feel the need to reset clrmamepro's settings, just delete your existing profile(s) and reload your DAT file, selecting **"Default"** settings for the new profile.  Almost all of clrmamepro's settings are per-profile.

# Filtering ROMs

To be written