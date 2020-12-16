# Symbolicate crashlog from tester's device

Created time: Dec 9, 2020 4:54 PM
Last edited time: Dec 16, 2020 9:28 AM
Tags: information

## Retrieve crashlog from device

- Steps
    1. Open Settings > Privacy > Analytics & Improvement > Analytics Data
    2. Scroll down to find the app name, eg. `Your_App_Name-2020-12-08-151545.ips`
    3. Rename the extension from .ips into `.crash` , eg. `Your_App_Name-2020-12-08-151545.crash`

## Get DSYM file

- Steps
    1. Open Xcode > Window > Organizer (opt + cmd + shift + O)
    2. Select `Archives` from the left tab
    3. Right click on a build and select `Show in Finder`
    4. Right click file with `.xcarchive` extension and select `Show Package Content`
    5. Open dSYMs folder and copy file with `.app.dSYM` extension to Desktop

## Symbolicating crashlog

- Preparing
    1. Create a folder on Desktop with any name, eg. `Your_App_Name` and add the `dSYM file` into the folder
    2. Add the `Your_App_Name-2020-12-08-151545.crash` file into the folder
    3. Open the folder and right click the `dSYM file` and select `Show Package Content`
    4. Open Contents > Resources > DWARF
    5. Copy the App named file and paste into the `Your_App_Name` folder
- Symbolicating
    1. Open the `.crash` file and copy the hex code under `Thread 0 Crashed` section, eg. 0x00000001a25f2d88 0x1a25cd000 (do not copy the string after + sign)
    2. Open terminal, and navigate to the folder, eg. cd Desktop/HPPregnancyLite
    3. Example hex 0x00000001a25f2d88 0x1a25cd000, replace $2 with 0x1a25cd000 and $1 with 0x00000001a25f2d88 and YourAppName.

    ```bash
    xcrun atos -o YourAppName -arch arm64 -l $2 $1
    ```

    4. The final command will be like this

    ```bash
    xcrun atos -o YourAppName -arch arm64 -l 0x1a25cd000 0x00000001a25f2d88
    ```
