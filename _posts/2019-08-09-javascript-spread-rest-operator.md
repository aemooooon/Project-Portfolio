---
layout: post
title: About Javascript Spread or Rest Operator
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-08-09
color: brown
---

recently, I read a lot of React-Native code from other place. I found a very intertising thing which is ... operator wherever in styles, views or any JSX. So I just do some research to understand what the ... are. Basicaly there are two aims to use this, one calls spread and other calls rest.


```javascript
import React, { useState } from 'react';
import { View, Text, Image, Button, StyleSheet } from 'react-native';

const ColorScreen = () => {
    const [colors, setColors] = useState([]);
    console.log(colors);

    return (
        <View>
            <Button title="Add a Color"
                onPress={() => {
                    setColors([...colors, randomRgb()]);
                }}
            ></Button>
            <View
                style={{ height: 100, width: 100, backgroundColor: randomRgb() }}
            ></View>
        </View>
    )
};

const randomRgb = () => {
    const red = Math.floor(Math.random() * 256);
    const green = Math.floor(Math.random() * 256);
    const blue = Math.floor(Math.random() * 256);

    return `rgb(${red},${green},${blue})`;
};

const styles = StyleSheet.create({

});

export default ColorScreen;
```

> output with ...

```bash
Array [
  "rgb(31,238,53)",
  "rgb(12,227,17)",
  "rgb(111,59,44)",
  "rgb(135,232,220)",
  "rgb(249,37,171)",
]
```

> output without ...

```bash
Finished building JavaScript bundle in 110ms.
Running application on EVR-AL00.
Array []
Array [
  Array [],
  "rgb(86,217,130)",
]
Array [
  Array [
    Array [],
    "rgb(86,217,130)",
  ],
  "rgb(139,35,6)",
]
Array [
  Array [
    Array [
      Array [],
      "rgb(86,217,130)",
    ],
    "rgb(139,35,6)",
  ],
  "rgb(112,5,99)",
]
Array [
  Array [
    Array [
      Array [
        Array [],
        "rgb(86,217,130)",
      ],
      "rgb(139,35,6)",
    ],
    "rgb(112,5,99)",
  ],
  "rgb(49,97,33)",
]
```

As we can see there are two pieces of code shot. If we use ... operator, the setState of useState will put the reulst which is from the function randomRgb to one Array which is we define the variable colors. otherwise, it will put the new result and append old one togethoer to new Array. So the code shot just like a recursion.

 Why like this?  what is going on under the hook? Because the ... operator use to spread colors array.