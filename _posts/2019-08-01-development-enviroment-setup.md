---
layout: post
title: Development Enviroment Setup
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1]
date: 2019-08-01
color: brown
---

About development enviroment, there are two ways to implement it. Whatever IOS or Android. Expo CLI and React Native CLI.

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
The solution is Just download the official template put into `/android/app/`
```html
https://raw.githubusercontent.com/facebook/react-native/master/template/android/app/debug.keystore
```