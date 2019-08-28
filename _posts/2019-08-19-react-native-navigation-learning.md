---
layout: post
title: React Native navigation learning
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1]
date: 2019-08-19
color: brown
---

React Native Navigation use a sort of Stack to manages different screens. I need a main page to define a Stack which called StackNavigator, then put all other screens to here. Then I can via props to pass with different screen to navigate. To use this function, First need install 2 packages:

```javascript
npm install --save react-navigation
npm install --save react-native-gesture-handler
```

after that I have created a App main entrance which called App.js put in the root directory. When user open the App, will auto navigate to Home screen.
App.js context down below:
```javascript
import React from 'react';
import { createStackNavigator, createAppContainer } from 'react-navigation';
import HomeScreen from './screens/HomeScreen';
import SignInScreen from './screens/SignInScreen';
import SignUpScreen from './screens/SignUpScreen';
import ProfileScreen from './screens/ProfileScreen';

const navigator = createStackNavigator({
  Home: HomeScreen,
  SignIn: SignInScreen,
  SignUp: SignUpScreen,
  Profile: ProfileScreen,
}, {
    initialRouteName: 'Home',
    defaultNavigationOptions: {
      header: null,
    }
  });

const App = createAppContainer(navigator);

export default () => {
  return (<App />)
}
```

For each other screen has already get props property. So just use `this.props.navigation.navigate('the screen you want to go to')`


## Drawer Menu
When I first time to do Drawer menu, I can only test on Android platform, but Curthor has found some way can fit both platform. So this kind of both of us working, I list the code belw:

```javascript
    render() {
        var drawer = (
            <ScrollView contentContainerStyle={{ flex: 1, flexDirection: 'column', backgroundColor: '#1d1d26', justifyContent: 'space-between' }}>
                <SafeAreaView forceInset={{ top: 'always', horizontal: 'never' }}>
                    <View style={styles.userIconContainer}>
                        <Image
                            style={styles.userIconPlaceholder}
                            source={require('../assets/user-icon-image-placeholder.jpg')}
                        />
                        <Text style={{ marginVertical: 10, color: '#FFFFFF' }}>{this.state.user ? this.state.user.email : null}</Text>
                    </View>
                    <View>
                        <TouchableOpacity onPress={() => this.props.navigation.navigate('Home')}>
                            <View style={styles.item}>
                                <View style={styles.iconContainer}>
                                    <FontAwesome name="home" size={20} color="green" />
                                </View>
                                <Text style={styles.label}>Home</Text>
                            </View>
                        </TouchableOpacity>
                        <TouchableOpacity onPress={() => this.props.navigation.navigate('Profile')}>
                            <View style={styles.item}>
                                <View style={styles.iconContainer}>
                                    <AntDesign name="profile" size={18} color="pink" />
                                </View>
                                <Text style={styles.label}>Profile</Text>
                            </View>
                        </TouchableOpacity>
                        <TouchableOpacity onPress={() => this.props.navigation.navigate('MyRecords')}>
                            <View style={styles.item}>
                                <View style={styles.iconContainer}>
                                    <Ionicons name="ios-stats" size={20} color="yellow" />
                                </View>
                                <Text style={styles.label}>My Records</Text>
                            </View>
                        </TouchableOpacity>
                    </View>
                </SafeAreaView>
                <TouchableOpacity onPress={() => {
                    firebase.auth().signOut();
                    this.setState({ loggedIn: false });
                }}>
                    <View style={styles.item}>
                        <View style={styles.iconContainer}>
                            <AntDesign name="logout" size={20} color="red" />
                        </View>
                        <Text style={styles.label}>Logout</Text>
                    </View>
                </TouchableOpacity>
            </ScrollView>
        );
        return (
            <View style={styles.container}>
                <Drawer
                    ref={(ref) => this._drawer = ref}
                    content={drawer}
                    openDrawerOffset={(viewport) => viewport.width - 200}
                    tapToClose={true}
                    negotiatePan={false}>
                    <Header
                        leftComponent={<Icon name="menu" onPress={() => this._drawer.open()} />}
                        centerComponent={{ text: "MAP", style: { color: '#FFF', fontSize: 25 } }}
                        rightComponent={<Icon name="home" />} />
                    <Map />
                </Drawer>
            </View>
        )
    }


    const styles = StyleSheet.create({
    container: {
        flex: 1,
    },
    userIconContainer: {
        justifyContent: 'center',
        alignItems: 'center',
        paddingTop: 50,
        paddingBottom: 10,
        backgroundColor: '#191919'
    },
    userIconPlaceholder: {
        width: 80,
        height: 80,
        borderRadius: 80 / 2
    },
    item: {
        flexDirection: 'row',
        alignItems: 'center',
    },
    label: {
        margin: 10,
        fontWeight: 'bold',
        color: '#FFFFFF',
    },
    iconContainer: {
        marginHorizontal: 16,
        width: 24,
        alignItems: 'center',
    },
    icon: {
        width: 24,
        height: 24,
    }
});
```