## Self Service Icon Maker
A simple app that can extract bundle icons (icns files) and convert them to png's suitable for use with Casper Suite's Self Service application

### Current release: 1.3.1  
**Changes:**  

- Changed default output icon dimensions to 512 x 512 for better compatiblity with Jamf Pro 10.

### Version 1.3 Change log
**Changes:**  

- Self Service Icon Maker can now accept mutliple applications at once! This means you can select as many applications you want in a single directory, drag them all on top of **Self Service Icon Maker** and the app will locate and convert every application icon it can find for each application in one shot.  
- Because it can now handle many applications at once, an additional "Summary" section is provided at the end of the run in the log window. It will show how many applications were dropped on the app or window, how many it could successfully generate a Self Service icon for, and how many it failed to generate an icon from (if any) The log window still displays the conversion process for each application as it loops over them.  
- If the chosen directory for saving the icons to somehow goes missing, the app will re-prompt you for a save destination the next time it runs or applications are dropped on it.  
- Some small bug fixes and better error handling was incorporated in this version, preventing failures in cases where an icns file was located in more than one location within the `/Contents/Resources/` path.  

### Version 1.1 Change log
**Changes:**  

- Upon first launch, the application will now prompt for a location to save the converted icons, allowing you to contain them all in one location (so you don't need to clutter up your Desktop).
- If you click Cancel during the initial selection, your Desktop will be chosen instead.
- Whichever location is set, it will be stored inside a local plist in `~/Library/Preferences/org.mm2270.SelfServiceIconMaker.plist` The entry is labeled `iconDir` and is a simple POSIX path string.
- Icon resolution can be set programmatically from Terminal with the following command:  
`defaults write org.mm2270.SelfServiceIconMaker iconRes 256`
-   The above would set the icon resolution during conversions to 256 x 256. The default is 128 x 128 if this value is not set in the plist.

**Note:** You should only set the resolution to a size that any .icns file would contain, such as 128, 256, 512, etc. Odd sizes like '200' may result in errors during conversion from .icns to .png format.

### Version 1.0 (Initial Release)  

**Usage:**  

1. Drag an application bundle onto the app (currently it will only accept .app files)  
2. The application will launch and display a log window  
3. If the app you dropped on Self Service Icon Maker contains a valid CFBundleIconFile reference in its Info.plist, the script in the app will attempt to locate the actual icns file referenced by the CFBundleIconFile name (usually in the Resources directory)  
4. If successful, it will use sips (simple image processing system) to make a copy of the icns file into a png file in either the default 128 x 128 size, or whatever size is specified in the plist (see notes above), saved to your Desktop. The filename format will be: `<ApplicationName>_SelfServiceIcon_<resolution>x<resolution>.png`

That's it. Currently this is a 1.0 or more like a 0.1 release as it does only minor error checking, and if it isn't able to locate the bundled icns file for some reason, it will just report that and exit. A future version may prompt you to locate the icon file for conversion. ~~Or maybe allow you to set a location of where to save the resulting png.~~  It does this now.
