# Chrome App Developer Tool for Mobile

The Chrome App Developer Tool for Mobile is a distribution of
[Apache Cordova App Harness](https://git-wip-us.apache.org/repos/asf/cordova-app-harness.git)
that can run Chrome Apps. It is based on the plugins from the
[cca](https://github.com/MobileChromeApps/mobile-chrome-apps) toolkit.

## Installation

### Using a Pre-Built Binary (Android only)

1. Enable USB debugging on your device (follow step 2 [here](http://developer.android.com/tools/device.html#setting-up)).
2. Download an APK from [here](https://github.com/MobileChromeApps/chrome-app-developer-tool/releases).
3. Run `adb install ChromeAppDeveloperTool-debug.apk` (of course, navigating to the appropriate directory first).
  * Alternatively, download the `.apk` using your device's browser.

### Building from Source (iOS or Android)

1. Clone this repository:

        git clone https://github.com/MobileChromeApps/chrome-app-developer-tool.git

2. Create a Chrome App Developer Tool project using `createproject.sh`.  For instance:

        ./createproject.sh ChromeAppDevTool

You can get more info using `./createproject.sh --help`.

## Using the Chrome App Developer Tool

1. Run the Chrome App Developer Tool on a device or simulator.
2. Navigate to your app directory and deploy using the `cca push --target=IP_ADDRESS` command.
    
    **Note:** You can find more on cca [here](https://github.com/MobileChromeApps/mobile-chrome-apps/blob/master/docs/Installation.md#install-the-cca-command-line-tool).
    
That's it—you're up and running!

### Tips and Tricks

* Use `cca push --watch` to automatically refresh the app when a file is updated.
* Minimize the app using a two-finger double-tap.
* Deploying via USB:
  * Android: Use `adb forward tcp:2424 tcp:2424`, and then run `cca push`
  * iOS: Use `python tcprelay.py 2424:2424` (available [here](https://github.com/chid/tcprelay)), and then run `cca push`

## Major Unimplemented Features

Suggestions are always welcome! :)

### General
* Applying app settings (DisallowOverscroll, etc)
* Applying app splashscreen
* Applying app's whitelist

### In-App Menu
* Inject a JSConsole script tag
* Initiate a weinre session
* Suggestions welcome! :)

# Release Notes

## v0.8.2 (August 28, 2014)
* Make createproject.sh delete output directory and rm andrew-create-project.sh
* Rename buildharness.sh -> build-android-release.sh
* Make createproject.sh work even when no dependencies are set up ahead of time
* createproject.sh: include ios by default when host=Darwin
* Remove xwalk as a package.json dep. Use the version within cca instead
* Update list of preloaded plugins
* Install plugins from registry when needed

## v0.8.1 (July 11, 2014)
* Fix exception on second launch and stop using plugin whitelist
* Fix wrong path in createproject.sh (failed every time)
* Add ArrayBuffer.slice polyfill for Android pre-KK (#22)
* Update link to Chrome Dev Editor
* Fix line-breaking CSS in About page

## v0.8.0 (June 25, 2014)
* Add chrome.alarms and org.apache.cordova.media plugins (mistakenly left out)
* Fix Android back button always quitting the app (now does what you'd expect)
* App now loads only the plugins that an app uses (instead of all installed plugins)
* Initial app push is now much faster for apps with lots of files
* First cut at "Details" and "About" pages
* Deleted notification bubble
* Fix apps not launching when you: push App A, then push App B, then push App A again

## v0.7.1 (June 17, 2014)
* Fix crash on launch-after-backbutton (#13)

## v0.7.0 (June 17, 2014)
* Speed improvements to initial app push (zippush endpoint)
* Implemented details & about page
* Minor UI tweaks

## v0.6.0 (June 17, 2014)
* New name: Chrome App Developer Tool for Mobile
* Default WebView for Chrome Apps is now using Crosswalk, currently based on Chrome/36.0.1985.18
* Changed the Android Launch Mode to singleTop so that clicking icon from launcher doesn't restart the app unnecessarily
* Few updates to the set of plugins we bundle by default
* Fix "failed to start server" when you close the app and start it again
* Displayed IP address now updates when your device's IP changes
* Some minor UI updates

## v0.5.1 (June 3, 2014)
* Now bundling all core Cordova plugins
* Use relative times for "last updated"
* Deleted in-app menu in favour of showing the main screen on double two-finger tap
* UI Overhaul

## v0.5.0 (May 27, 2014)
* Harness server now written in JS using chrome.socket
* Supports incremental updates to apps for faster pushes
* Server now works on iOS
* Use two-finger double-tap to summon menu instead of three-finger swipe

