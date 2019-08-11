---
layout: post
title: A little trick
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1]
date: 2019-08-12
color: brown
---


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