We recommend setting up your environment to upload dSYMs automatically from Xcode, [here's how](/04_iOS_SDK/About_dSYMs.html).
But if you already did this and you are seeing a message in TestFairy about missing dSYMs, this section is here to help.

### Locating dSYMs on your hard-drive


If your build is missing dSYMs, you can find them and upload them manually to TestFairy.

1. Login to TestFairy and go to the App overview page by clicking the name of your app.
2. Click on the name of your app build to reach the build overview page.
3. Click on 'Settings' from the Build menu, then select the 'Symbolication' section.
4. This section lists several required UUIDs (representing binary app builds for different device architecture or binary builds for frameworks you're using). To see crash reports with your classes and method names, you'll need to upload dSYMs for each UUID that is specified as required.
5. Open a command line terminal and run the following command to locate the DSYMs folder name for one of the listed required UUIDs (replace '<UUID>' with the actual UUID string):
    ```sh
    mdfind "com_apple_xcode_dsym_uuids == <UUID>" | grep dSYM
    ```
6. Create a zip file with the content of the DSYM directory (you can call the zip file any name you like)
	```
	zip -r /tmp/symbols.zip <YOUR_DSYM_LOCATION>/*
	 ```
7. Proceed to upload the zip as described [here](upload).

If you can't locate your dSYMS using mfind, follow these instructions:

1. In Xcode, open the organizer window.
2. Control-Click the relevant build, and select "Show in Finder".
3. In Finder, Control-Click the archive and select "Show Package Contents".
4. The archive will contain a folder called dSYM.
5. Create a zip with the contents of the folder and proceed to upload the zip to TestFairy as explained [here].

### Locating dSYMs for Bitcode builds.

If you enabled Bitcode for your build and released it to the store or submitted to TestFlight, take note that Apple will generate new dSYMs for your app and you'll need to download the new dSYMs from Xcode, and then upload them to TestFairy.

1. In Xcode, open the organizer window.
2. Click on the relevant build.
3. From the right side menu, click "download dSYMs".
4. Manually upload the dSYMs to TestFairy, [as described here](upload)

### <a name="upload">Manually upload dSYMs to TestFairy</a>

1. Login to TestFairy and go to the "App Overview" page by clicking the name of your app.
2. Click on the name of your app build to reach the build overview page.
3. Click on 'Build-Settings' from the top menu, then select the 'Symbolication' section.
4. Select the zip files with the dSYM you just created and click "Upload".
