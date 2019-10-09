---
layout: post
title: A little trick
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-08-11
color: brown
---


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