---
layout: post
title: ES6 Async Await
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-09-03
color: brown
---

According to the definition from <a target="_blank" href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function">MDN</a>: The async function declaration defines an asynchronous function, which returns an AsyncFunction object. An asynchronous function is a function which operates asynchronously via the event loop, using an implicit Promise to return its result. But the syntax and structure of your code using async functions is much more like using standard synchronous functions.

First of all, let me define a traditional Javascript function like below:

```javascript
function myFunc() {
  return "Hello";
}

console.log(myFunc());
```

This will simply outpub `Hello`. But if I add async before the myFunc, the output will be a Promise:

```bash
    Promise {<resolved>: "Hello"}
    __proto__: Promise
    [[PromiseStatus]]: "resolved"
    [[PromiseValue]]: "Hello"
```

> So notes that this is the key point. return a Promise

Secondly, I will do some changing in there:

```javascript
async function myFunc() {
  const promise = new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Hello");
    }, 3000);
  });

  const error = false; // if true will go wrong

  if (!error) {
    const res = await promise; // wait until promise is resolved
    return res;
  } else {
    await Promise.reject(new Error("Something went wrong"));
  }
}

myFunc()
  .then(res => console.log(res))
  .catch(err => console.log(err));
```

If run this code, the string 'Hello' will display after 3 seconds, because the await will wait resolve. beside the error is true, will catch the error.

There is one of the use case example:

```javascript
async function getUsers() {
  // await response of the fetch call
  const response = await fetch("https://api.github.com/users");

  // only proceed once its resolved
  const data = await response.json();

  // only proceed once second promise is resolved
  return data;
}

getUsers()
  .then(users => {
    console.log(users);
  })
  .catch(err => console.log(err));
```
