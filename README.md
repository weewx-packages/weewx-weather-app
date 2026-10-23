# WeeWX Weather App

An Android app by OdiousApps that displays weather data hosted by a WeeWX
station. It reads the Inigo plugin's settings and JSON outputs and offers
weather screens, forecasts and a home-screen widget. It does not collect
station hardware readings itself.

This repository mirrors
[evilbunny2008/WeeWXWeatherApp](https://github.com/evilbunny2008/WeeWXWeatherApp).
The current source declares app version 2.1.30, Android 11 or newer, and targets
Android API 37. It is an external Android project with no WeeWX extension
installer or catalog archive.

## Set up the app

Install the app through the upstream
[Google Play listing](https://play.google.com/store/apps/details?id=com.odiousapps.weewxweather),
or build an APK from this source as described below. Store availability and
published app versions are managed by upstream.

On the station, install and configure the separate
[Inigo plugin](https://github.com/evilbunny2008/InigoPlugin) using that project's
instructions. Serve its `inigo-settings.txt`, `inigo-data` JSON, `inigo-dicts`
JSON and `inigo-last` JSON from your own web server. This app expects Inigo's
format; an unrelated `weewx.json` report is not a substitute.

On first launch, enter your settings URL, for example
`https://weather.example.org/weewx/inigo-settings.txt`, then save it. The settings
file supplies the JSON addresses and station details. If those settings change,
use the app's settings pane to download them again. Swipe down on a weather
screen to refresh. Widget updates need background downloading enabled.

The [upstream setup wiki](https://github.com/evilbunny2008/WeeWXWeatherApp/wiki)
explains the settings format and app operation. Its server paths are examples;
use the web output directory configured for your station. The Android app
itself is installed on the phone, not with `weectl extension install`.

## Build from source

Use JDK 21 and an Android SDK containing API 37. The repository pins Gradle
9.8.1 and Android Gradle Plugin 9.4.1. Configure your own SDK location in
`local.properties`; the checked-in machine path is not portable.

```sh
./gradlew :app:assembleDebug
```

The debug APK is under `app/build/outputs/apk/debug`. Release builds require
your own signing configuration; see [`scripts/signing.conf.example`](scripts/signing.conf.example)
and [`scripts/build-signed.sh`](scripts/build-signed.sh). Do not reuse a developer's
SDK paths or signing files. The build downloads Gradle and Maven dependencies.
No Android build, device connection or live station was exercised for this
README update.

## Screenshots

Examples of earlier app screens are in [`screenshots`](screenshots).

## License

Source code is made available under the GPLv3 licence, in the hope the code might be useful to others. See [LICENCE](LICENSE) for details.

## Credits

Big thanks to the [WeeWX project](https://WeeWX.com), as this app wouldn't be possible otherwise.

Weather Icons from [FlatIcon](https://www.flaticon.com) and is licensed under [CC 3.0 BY](https://creativecommons.org/licenses/by/3.0/)

This app is by [OdiousApps](https://odiousapps.com).
