# Android integration

## Building the server

The integration has been done with maven and aar-plugin.
You can build it with three simple steps

1. locate your OS in <profiles> and set the correct path to the SDK
2. open a shell with maven and Java (I used 8 here) in $PATH or %PATH% - depending on your OS
3. build via `mvn clean install -DskpTests=true -p <the profile of your OS> -f pom-aar`

## Integrate in your Android App
### Gradle Dependencies
This build is currently not published to maven central. However, using Android Studio, one
simple can reference the local build artifacts.

Simply add this line to your build.gradle, section dependencies

`implementation 'org.nanohttpd:nanohttpd:<version>'`

If you are using Android studio, you will be asked to resync the project

### Permissions in android-manifest.xml

####for the webserver

`<uses-permission android:name="android.permission.INTERNET" />`
`<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />`

####for Wifi (I used this to obtain local IP)

`<uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />`

####to serve files from external SD

`<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>`

## Finally

That's it. Now you can derive NanoHTTPD and start implementing
