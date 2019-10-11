---
layout: post
title: A little trick
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-08-11
color: brown
---

There are many werid circumstances when I develop that code, it is not about official documents or principles could handle it, just some way to solve the problems and comes from the experience. So this post just use to record these thing I called that litte trick.

### update sub component value when parent component changing
1. declare ref in parent component
```jsx
this.workout = React.createRef(); // inside of constructor
```

2. set up ref value when call sub component inside of parent component
```jsx
<Workout ref={this.workout} />

3. call sub componet function inside of parent component when needed
```jsx
this.workout.current.subComponentFunction(parameter);
```

4. declare function inside of sub coponent
```jsx
subComponentFunction=(parameter)=>{
    this.setState({
        valueWeWantToUpdated: parameter
    });
}
```

### defautl placeholder tag in JSX
```jsx
    return (
        // <View style={{ flex: 1 }}>
        <>
            <SearchBar
                term={term}
                onTermChange={newTerm => setTerm(newTerm)}
                onTermSubmit={() => searchApi(term)}>
            </SearchBar>
            {errorMessage ? <Text>{errorMessage}</Text> : null}
            <Text>We have found {results.length} results.</Text>
            <ScrollView>
                <ResultsList results={filterResultsByPrice('$')} title="Cost Effective"></ResultsList>
                <ResultsList results={filterResultsByPrice('$$')} title="Bit Pricier"></ResultsList>
                <ResultsList results={filterResultsByPrice('$$$')} title="Big Spender"></ResultsList>
            </ScrollView>
        </>
        // </View>
    );
```

### Height attribute in Android and ios
```jsx
import {Platform, StyleSheet} from 'react-native';

const styles = StyleSheet.create({
  height: Platform.OS === 'ios' ? 200 : 100,
});
```
Some time the view if set up the height will going to be display different between ios and android. If so need set up height to 100 on ios if the doesnot set up on the android. for example in our project workout.js screen_pause and screen_run function, the first view inside 0.00 km.