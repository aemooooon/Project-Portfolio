---
layout: post
title: A bloody case caused by a character
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-11-18
color: brown
---

I felt bored last night just want to experience the latest Windows 10 terminal, and then updated the system by the way, and also updated the nodejs, and found that I could not start my project today. I really think that I am very bad, the last week of the semester, all the features are completed, just upload the project to the google play store, and this happened. 

It’s sad! 

The key is that I am constantly deleting, reinstalling, and updating can't solve the problem. It took me nearly three hours to finally find a solution. So I think that is valued to record here.

error output like:

```bash
wanghua@Aemon MINGW64 /d/GoogleDrives/2019S2/Project1/excercise-app/ExerciseApp (clean-up)    
$ expo start
Starting project at D:\GoogleDrives\2019S2\Project1\excercise-app\ExerciseApp
Expo DevTools is running at http://localhost:19002
Opening DevTools in the browser... (press shift-d to disable)
error Invalid regular expression: /(.*\\__fixtures__\\.*|node_modules[\\\]react[\\\]dist[\\\].*|website\\node_modules\\.*|heapCapture\\bundle\.js|.*\\__tests__\\.*)$/: Unterminated character class. Run CLI with --verbose flag for more details.

Metro Bundler process exited with code 1
Set EXPO_DEBUG=true in your env to view the stack trace.
```

solutions: update file locate at: ./node_modules/metro-config/src/defaults/blacklist.js

```jsx
var sharedBlacklist = [
  /node_modules[/\\]react[/\\]dist[/\\].*/,
  /website\/node_modules\/.*/,
  /heapCapture\/bundle\.js/,
  /.*\/__tests__\/.*/
];

// change to

var sharedBlacklist = [
  /node_modules[\/\\]react[\/\\]dist[\/\\].*/,
  /website\/node_modules\/.*/,
  /heapCapture\/bundle\.js/,
  /.*\/__tests__\/.*/
];
```