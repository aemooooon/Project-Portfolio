---
layout: post
title: Building a Standalone Apps
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-11-10
color: brown
---

Almost done this semester, also it is the project 1 done time. I need try to build our apps to binary file and publish to Andriod play store or Apple app store. Because we use the Expo CLI tools to develop this app, So there is some easy way to do that. And I just record this processes because this is not mormally using. 

###  Prerequsites:
1. I am working on Window 10, So need Windows Command Line with Adaministrotor permit.
2. Needing installs Expo cli tools
3. Needing a Expo account.

### Processes
1. configurates app.json, app name, version and android package...
```json
{
  "expo": {
    "name": "FitsGo",
    "slug": "ExerciseApp",
    "privacy": "public",
    "sdkVersion": "34.0.0",
    "platforms": [
      "ios",
      "android",
      "web"
    ],
    "version": "1.0.0",
    "orientation": "portrait",
    "icon": "./assets/icon.png",
    "splash": {
      "image": "./assets/splash.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    },
    "updates": {
      "fallbackToCacheTimeout": 0
    },
    "assetBundlePatterns": [
      "**/*"
    ],
    "ios": {
      "supportsTablet": true,
    },
    "android": {
      "package": "com.opbitproject.fitsgo"
    }
  }
}
```
2. running command with `expo build:android` to start building. During this need to login with expo account

```bash
An Expo user account is required to proceed.
? How would you like to authenticate? Log in with an existing Expo account
? Username/Email Address: aemooooon@gmail.com
? Password: [hidden]

Success. You are now logged in as aemooooon.
```
You may asked keystore, there are two ways that I just choose by handle from expo

```bash
? Would you like to upload a keystore or have us generate one for you?
If you do not know what this means, let us handle it! :)
 false
Publishing to channel default...
Building iOS bundle
connect ECONNREFUSED 127.0.0.1:19001
Set EXPO_DEBUG=true in your env to view the stack trace.
```
To sovle this error just run command with `Set EXPO_DEBUG=true` on the bash and restart it. In the same time, it needs start app use expo start which I use Visual studio code

3. wait to building...
```bash
Publishing to channel default...
Building iOS bundle
Building Android bundle
Analyzing assets
Uploading assets
No assets changed, skipped.
Processing asset bundle patterns:
- D:\GoogleDrives\2019S2\Project1\excercise-app\ExerciseApp\**\*
Uploading JavaScript bundles
Published
Your URL is

https://exp.host/@aemooooon/ExerciseApp

Checking if this build already exists...

Build started, it may take a few minutes to complete.
You can check the queue length at https://expo.io/turtle-status

You can make this faster. 🐢
Get priority builds at: https://expo.io/settings/billing

You can monitor the build at

 https://expo.io/builds/45e6f7a3-89c7-4994-b25f-e8e1e88488f0

Waiting for build to complete. You can press Ctrl+C to exit.
√ Build finished.
Successfully built standalone app: https://expo.io/artifacts/23369479-bbc6-4313-bef6-b418380a3f41
```

4. about Google Map API not found error make sure app.json added the api key in the section of Android or ios
```bash
"android": {
   "package": "com.codingmechanic.mapcuny",
   "config": {
      "googleMaps": { "apiKey": "<Your API Key>" }   
   }
}

"ios": {
  "bundleIdentifier": "com.codingmechanic.mapcuny",
  "config": {
    "googleMapsApiKey": "YOUR IOS API KEY HERE"
  }
},
```