---
layout: post
title: Passing props with Components
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1], technical proficiency
date: 2019-08-10
color: brown
---

There are two differents way to pass props from components call page to components detail page. If just put props as the parameter to component function, it will includes all props and all other objects. So in some aspect, maybe not good to enficiency. So I would like to pass each detailed props.

> The way I prefer below

```javascript
const ImageScreen = () => {
    return (
        <View>
            <ImageDetail title="Forest" imageSource={require('../../assets/forest.jpg')} score={9}></ImageDetail>
            <ImageDetail title="Beach" imageSource={require('../../assets/beach.jpg')} score={12}></ImageDetail>
            <ImageDetail title="Mountain" imageSource={require('../../assets/mountain.jpg')} score={25}></ImageDetail>
        </View>
    )
}

const ImageDetial=({imageSource,title,score})=>{
    return(
        <View>
            <Image source={imageSource}></Image>
            <Text>{title}</Text>
            <Text>Score: {score}</Text>
        </View>
        
    )
};
```

> other way


```javascript
const ImageScreen = () => {
    return (
        <View>
            <ImageDetail title="Forest" imageSource={require('../../assets/forest.jpg')} score={9}></ImageDetail>
            <ImageDetail title="Beach" imageSource={require('../../assets/beach.jpg')} score={12}></ImageDetail>
            <ImageDetail title="Mountain" imageSource={require('../../assets/mountain.jpg')} score={25}></ImageDetail>
        </View>
    )
}

const ImageDetial=(props)=>{
    return(
        <View>
            <Image source={props.imageSource}></Image>
            <Text>{props.title}</Text>
            <Text>Score: {props.score}</Text>
        </View>
        
    )
};
```

> props output

```bash
Finished building JavaScript bundle in 84ms.
Running application on EVR-AL00.
Object {
  "imageSource": 3,
  "score": 9,
  "title": "Forest",
}
Object {
  "imageSource": 3,
  "score": 9,
  "title": "Forest",
}
Object {
  "imageSource": 4,
  "score": 12,
  "title": "Beach",
}
Object {
  "imageSource": 4,
  "score": 12,
  "title": "Beach",
}
Object {
  "imageSource": 5,
  "score": 25,
  "title": "Mountain",
}
Object {
  "imageSource": 5,
  "score": 25,
  "title": "Mountain",
}
```