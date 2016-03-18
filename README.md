## Self-Service-Icon-Maker
A simple app that can extract bundle icons (icns files) and convert them to png's suitable for use with Casper Suite's Self Service application

###New version uploaded: 1.1  
**Changes:**  

- Upon first launch, the application will now prompt for a location to save the converted icons, allowing you to contain them all in one location (so you don't need to clutter up your Desktop).
- If you click Cancel during the initial selection, your Desktop will be chosen instead.
- Whichever location is set, it will be stored inside a local plist in `~/Library/Preferences/org.mm2270.SelfServiceIconMaker.plist` The entry is labeled `iconDir` and is a simple POSIX path string.
- Icon resolution can be set programmatically from Terminal with the following command:  
`defaults write org.mm2270.SelfServiceIconMaker iconRes 256`
-   The above would set the icon resolution during conversions to 256 x 256. The default is 128 x 128 if this value is not set in the plist.

**Note:** You should only set the resolution to a size that any .icns file would contain, such as 128, 256, 512, etc. Odd sizes like '200' may result in errors during conversion from .icns to .png format.

**Usage:**  

1. Drag an application bundle onto the app (currently it will only accept .app files)  
2. The application will launch and display a log window  
3. If the app you dropped on Self Service Icon Maker contains a valid CFBundleIconFile reference in its Info.plist, the script in the app will attempt to locate the actual icns file referenced by the CFBundleIconFile name (usually in the Resources directory)  
4. If successful, it will use sips (simple image processing system) to make a copy of the icns file into a png file in either the default 128 x 128 size, or whatever size is specified in the plist (see notes above), saved to your Desktop. The filename format will be: `<ApplicationName>_SelfServiceIcon_<resolution>x<resolution>.png`

That's it. Currently this is a 1.0 or more like a 0.1 release as it does only minor error checking, and if it isn't able to locate the bundled icns file for some reason, it will just report that and exit. ~~A future version may prompt you to locate the icon file for conversion. Or maybe allow you to set a location of where to save the resulting png.~~  It does this now.
