---
layout: post
title: Development Enviroment Setup
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1]
date: 2019-08-01
color: brown
---

A good start is a general success. First, let me put the development environment up. About React Native development enviroment, there are two ways to implement it. Whatever IOS or Android. Expo CLI and React Native CLI.

## Expo CLI

Expo is really easy way to start. The prerequesite is Node 10+ installed. Then:

#### Server
```
npm install -g expo-cli # install expo-cli

expo init ProjectName # initialization a new project
cd ProjectName # enter into new project
npm start # or expo start # start the server
```
#### Client
1. Install app on my phone. (https://expo.io/)
2. Use app scan the QR code from my server terminal

Now, I can start to modify App.js to develop. Any changing will automatically reload. I have try it at my home, based on same WIFI at my home, it's working properly. But when I try this way in the Project room of the campus does not wroking properly. I think the reason is because the WIFI not in the same Lan.


## React Native CLI

#### prerequesite
1. Install Chocolatey with command `@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"`
2. `choco install -y nodejs.install python2 jdk8`
3. `npm install -g react-native-cli`
4. Install Android Studio and make sure below components to installed.
```
Android SDK
Android SDK Platform
Performance (Intel ® HAXM)
Android Virtual Device
```
5. configurate Android Studio SDK
```
Android SDK Platform 28
Intel x86 Atom_64 System Image or Google APIs Intel x86 Atom System Image
```
6. Add Anddroid/SDK and Android/SKD/platform-tools to System Environment Variables.
7. Create a new Project with `react-native init ProjectName`
8. `cd ProjectName && react-native run-android`

These are just the basic steps without any exceptions. But I have encounter a lot of different issues below:

## Exception Issues

#### emulator-5554 Device is UNAUTHORIZED

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/001.png?raw=true "emulator-5554 Device is UNAUTHORIZED")

For this kind of situation, I have try to some way from stackoverflow. use below command:
```
adb kill-server
adb start-server
```
and also I have delete my exists AVD, create a new one instead it. Does it working.

#### No online devices found

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/002.png?raw=true "No online devices found")

Just changed the AVD settings to enable "Use Host GPU"


#### Do not have Android SDK

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/003.png?raw=true "Do not have Android SDK")

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/004.png?raw=true "Do not have Android SDK")

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/005.png?raw=true "Do not have Android SDK")

This situation because I install the new latest version of Andriod Studio. And this kind of version don't include Andriod SKD more, it is seperated. So just follow the picture above could solved.


#### debug.keystore' not found 
```bash
D:\GoogleDrives\2019S2\Project1\excercise-app\ExcerciseApp>react-native run-android
info Running jetifier to migrate libraries to AndroidX. You can disable it using "--no-jetifier" flag.
Jetifier found 855 file(s) to forward-jetify. Using 12 workers...
info JS server already running.
info Installing the app...
> Task :app:validateSigningDebug FAILED

Deprecated Gradle features were used in this build, making it incompatible with Gradle 6.0.
Use '--warning-mode all' to show the individual deprecation warnings.
See https://docs.gradle.org/5.4.1/userguide/command_line_interface.html#sec:command_line_warnings
17 actionable tasks: 10 executed, 7 up-to-date

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:validateSigningDebug'.
> Keystore file 'D:\GoogleDrives\2019S2\Project1\excercise-app\ExcerciseApp\android\app\debug.keystore' not found for signing config 'debug'.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 13s

error Failed to install the app. Make sure you have the Android development environment set up: https://facebook.github.io/react-native/docs/getting-started.html#android-development-environment. Run CLI with --verbose flag for more details.Error: Command failed: gradlew.bat app:installDebug -PreactNativeDevServerPort=8081

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':app:validateSigningDebug'.
> Keystore file 'D:\GoogleDrives\2019S2\Project1\excercise-app\ExcerciseApp\android\app\debug.keystore' not found for signing config 'debug'.

* Try:
Run with --stacktrace option to get the stack trace. Run with --info or --debug option to get more log output. Run with --scan to get full insights.

* Get more help at https://help.gradle.org

BUILD FAILED in 13s

    at checkExecSyncError (child_process.js:621:11)
    at execFileSync (child_process.js:639:15)
    at runOnAllDevices (D:\GoogleDrives\2019S2\Project1\excercise-app\ExcerciseApp\node_modules\@react-native-community\cli-platform-android\build\commands\runAndroid\runOnAllDevices.js:75:39)
    at buildAndRun (D:\GoogleDrives\2019S2\Project1\excercise-app\ExcerciseApp\node_modules\@react-native-community\cli-platform-android\build\commands\runAndroid\index.js:169:41)
    at D:\GoogleDrives\2019S2\Project1\excercise-app\ExcerciseApp\node_modules\@react-native-community\cli-platform-android\build\commands\runAndroid\index.js:135:12
    at processTicksAndRejections (internal/process/task_queues.js:85:5)
    at async Command.handleAction (D:\GoogleDrives\2019S2\Project1\excercise-app\ExcerciseApp\node_modules\react-native\node_modules\@react-native-community\cli\build\cliEntry.js:160:7)
```
The solution is Just download the official template put into `/android/app/`
```html
https://raw.githubusercontent.com/facebook/react-native/master/template/android/app/debug.keystore
```

Pull remote branch to local if the branch on the remote without local
```
git fetch origin
git checkout --track origin/<remote_branch_name>
```
`git pull origin dev-env`
