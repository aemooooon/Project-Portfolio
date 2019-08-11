---
layout: post
title: React Native learning
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1]
date: 2019-07-27
color: brown
---

This is just I read the React Native official Docs and write a very basic crash content here. A sample flow lead me know how to start a React Native project.

## Basic skeleton

App.js

```javascript
import React, { Component } from "react";
import { Text, View } from "react-native";
import HelloWorld from "./components/HelloWorld";

export default class HelloWorldApp extends Component {
  render() {
    return (
      <View style={{ flex: 1, justifyContent: "center", alignItems: "center" }}>
        <Text>Hello, world!</Text>
      </View>
    );
  }
}
```

./components/HelloWorld.js

```javascript
import React, { Component } from "react";
import { StyleSheet, Text, View } from "react-native";

class HelloWorld extends Component {
  render() {
    return (
      <View style={styles.view}>
        <Text style={styles.test}>Hello World!</Text>
        <View style={{ flex: 1, backgroundColor: "powderblue" }} />
        <View style={{ flex: 2, backgroundColor: "skyblue" }} />
        <View style={{ flex: 3, backgroundColor: "steelblue" }} />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  test: {
    color: "skyblue",
    fontWeight: "bold",
    fontSize: 30
  },

  view: {
    flex: 1,
    alignItems: "center"
  }
});

export default HelloWorld;
```

## Component Property and State

```javascript
import React, { Component } from "react";
import { AppRegistry, Text, View } from "react-native";

class Greeting extends Component {
  render() {
    return (
      <View style={{ alignItems: "center" }}>
        <Text>Hello {this.props.name}!</Text>
      </View>
    );
  }
}

export default class LotsOfGreetings extends Component {
  constructor(props) {
    super(props);

    this.state = {
      firstInput: "",
      secondInput: "",
      isValidated: false
    };
  }

  _displayResult() {
    if (this.state.firstInput !== "" && this.state.secondInput !== "") {
      this.setState({ isValidated: true });
    } else {
      this.setState({ isValidated: false });
    }
  }

  render() {
    return (
      <View style={{ alignItems: "center", top: 50 }}>
        <Greeting name="Rexxar" />
        <Greeting name="Jaina" />
        <Greeting name="Valeera" />
        <Text>{this.state.firstInput}</Text>
      </View>
    );
  }
}
```

## Style

```javascript
import React, { Component } from 'react';
import { StyleSheet, Text, View } from 'react-native';

const styles = StyleSheet.create({
  bigBlue: {
    color: 'blue',
    fontWeight: 'bold',
    fontSize: 30,
  },
  red: {
    color: 'red',
  },
});

export default class LotsOfStyles extends Component {
  render() {
    return (
      <View>
        <Text style={styles.red}>just red</Text>
        <Text style={styles.bigBlue}>just bigBlue</Text>
        <Text style={[styles.bigBlue, styles.red]}>bigBlue, then red</Text>
        <Text style={[styles.red, styles.bigBlue]}>red, then bigBlue</Text>
      </View>
    );
  }
}
```

## Flex
```javascript
      <View style={{flex: 1}}>
        <View style={{flex: 1, backgroundColor: 'powderblue'}} />
        <View style={{flex: 2, backgroundColor: 'skyblue'}} />
        <View style={{flex: 3, backgroundColor: 'steelblue'}} />
      </View>
```

All dimensions such as width, height in React Native are unitless, and represent density-independent pixels.



npm install react-navigation
npx expo-cli install react-native-gesture-handler react-native-reanimated
