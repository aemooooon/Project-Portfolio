---
layout: post
title: Implements Privacy Policy with WebView
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-11-16
color: brown
---

About Privacy Policy, I have try to edit the content as a standard HTML and difines as JavaScript object to put inside the View by a third component which is called react-native-render-html. It is working, but realy ugly as well as not flexable. I've do some research found thera are a way could do better, but need a web page to support. So I just createa a GitHub repository pages just for this kind of job. [FitsGo Privacy Policy](https://aemooooon.github.io/FitsGoPrivacyPolicy/)

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/058.png?raw=true "compare to two ways")
![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/059.png?raw=true "compare to two ways")

```jsx
import { WebView } from 'react-native';
import HTML from 'react-native-render-html';

const htmlContent = `
<p>Otago Polytech 2019S2 Mobile Project Group Hua Wang&Panithan (Carthur) Pongpatimet built the FitsGo app as a Free app. This SERVICE is provided by Otago Polytech at no cost and is intended for use as is.</p>
<p>This page is used to inform visitors regarding our policies with the collection, use, and disclosure of Personal Information if anyone decided to use our Service.</p>
<p>If you choose to use our Service, then you agree to the collection and use of information in relation to this policy. The Personal Information that we collect is used for providing and improving the Service. We will not use or share your information with anyone except as described in this Privacy Policy.</p>
<p>The terms used in this Privacy Policy have the same meanings as in our Terms and Conditions, which is accessible at FitsGo unless otherwise defined in this Privacy Policy.</p>
<h3>Information Collection and Use</h3>
<p>For a better experience, while using our Service, we may require you to provide us with certain personally identifiable information, including but not limited to location,email,icon. The information that we request will be retained by us and used as described in this privacy policy.</p>
<p>The app does use third party services that may collect information used to identify you.</p>
<p>Link to privacy policy of third party service providers used by the app <a target='_blank' href='https://www.google.com/policies/privacy/'>Google Play Services</a></p>

<h3>Log Data</h3>
`
<>
    <Header
        leftComponent={<AntDesign name="arrowleft" onPress={() => this.props.navigation.goBack()} size={32} color="white" />}
        centerComponent={{ text: "Privacy Policy"}}
    />
    {/* <ScrollView style={[styles.container]}>
        <HTML html={htmlContent} imagesMaxWidth={Dimensions.get('window').width-50} />
    </ScrollView> */}
<WebView
    source={{ uri: 'https://aemooooon.github.io/FitsGoPrivacyPolicy/' }}
/>
</>
```