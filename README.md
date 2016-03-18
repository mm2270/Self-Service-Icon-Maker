## Self-Service-Icon-Maker
A simple app that can extract bundle icons (icns files) and convert them to png's suitable for use with Casper Suite's Self Service application

**Usage:**  

1. Drag an application bundle onto the app (currently it will only accept .app files)  
2. The application will launch and display a log window  
3. If the app you dropped on Self Service Icon Maker contains a valid CFBundleIconFile reference in its Info.plist, the script in the app will attempt to locate the actual icns file referenced by the CFBundleIconFile name (usually in the Resources directory)  
4. If successful, it will use sips (simple image processing system) to make a copy of the icns file into a 128 x 128 pixel png file, saved to your Desktop The filename format will be: `ApplicationName_SelfServiceIcon_128x128.png`

That's it. Currently this is a 1.0 or more like a 0.1 release as it does only minor error checking, and if it isn't able to locate the bundled icns file for some reason, it will just report that and exit. A future version may prompt you to locate the icon file for conversion. Or maybe allow you to set a location of where to save the resulting png.
