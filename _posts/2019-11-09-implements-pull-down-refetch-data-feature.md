---
layout: post
title: Implements pull down refetch data feature
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, technical proficiency]
date: 2019-11-09
color: brown
---

When I every day using the apps from other developer that I normally pull down the screen to refresh and getting the latest data from the server. Today I was working on the Myrecords page which includes a lot of list data, so I just realize that is a good chance to implements this kind of feature on my own app. I have done some research from official document of the React Native, it is pretty simple. Therefore put the code here without explaination in order to some day to review again.

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/057.png?raw=true "The effects on ios")
The effects on ios

```jsx
import React, { Component } from 'react';
import { Text, StyleSheet, View, ScrollView, SafeAreaView, RefreshControl } from 'react-native';
import { Header } from 'react-native-elements';
import { AntDesign } from '@expo/vector-icons';
import firebase from 'firebase';
import { db } from '../components/common/config';

export default class MyRecordsScreen extends Component {
    constructor(props) {
        super(props);
    }

    state = {
        records: [],
        refreshing: false,
    };

    _onRefresh() {
        this.setState({ refreshing: true });
        this.fetchData().then(() => {
            this.setState({ refreshing: false });
        });
    }

    fetchData() {
        return new Promise((resolve, reject) => {
            db.ref('records/' + firebase.auth().currentUser.uid).on('value', (data) => {
                if (Object.values(data.val())) {
                    this.setState({
                        records: Object.values(data.val())
                    });
                }
            });
            const error = false;
            if (!error) {
                resolve();
            } else {
                reject('Something went wroing');
            }
        });
    }

    componentWillMount() {
        firebase.auth().onAuthStateChanged((user) => {
            if (user) {
                this.setState({ user: user });
            } else {
                this.props.navigation.navigate('SignIn');
            }
        });

        this.fetchData();
    }

    convertMode(directionMode) {
        let result = '';
        switch (directionMode) {
            case 'WALKING':
                result = 'Walk';
                break;
            case 'BICYCLING':
                result = 'Bike';
                break;
            case 'RUNNING':
                result = 'Run';
                break;
        }
        return result;
    }

    renderRecords() {
        return this.state.records.map((record, i) => {
            return (
                <View style={styles.table} key={i}>
                    <Text style={styles.rows}>{record.doneTime}</Text>
                    <Text style={styles.rows}>{this.convertMode(record.directionMode)}</Text>
                    <Text style={styles.rows}>{parseFloat(record.finalDistance).toFixed(3) < 1 ? parseFloat(record.finalDistance * 1000).toFixed(0) + 'm' : parseFloat(record.finalDistance).toFixed(2) + 'km'}</Text>
                    <Text style={styles.rows}>{parseInt(record.realDuration / 1000 / 60)}min</Text>
                    <Text style={styles.rows}>{record.calories}cal</Text>
                </View>
            )
        });
    }

    render() {
        return (
            <SafeAreaView>
                <Header
                    leftComponent={<AntDesign name='arrowleft' onPress={() => this.props.navigation.goBack()} size={32} color='white' />}
                    centerComponent={{ text: 'My Records' }} />
                <View style={styles.tableHead}>
                    <Text style={styles.headRows}>Date</Text>
                    <Text style={styles.headRows}>Mode</Text>
                    <Text style={styles.headRows}>Distance</Text>
                    <Text style={styles.headRows}>Duration</Text>
                    <Text style={styles.headRows}>Calory</Text>
                </View>
                <ScrollView refreshControl={
                    <RefreshControl
                        refreshing={this.state.refreshing}
                        onRefresh={this._onRefresh.bind(this)}
                    />
                }>
                    {this.state.records ? this.renderRecords() : 'Have not exercise yet...'}
                </ScrollView>
            </SafeAreaView>
        )
    }
}

const styles = StyleSheet.create({
    title: {
        fontSize: 20,
        fontWeight: 'bold',
        textAlign: 'center',
        marginVertical: 10,
        color: '#48cfad'
    },
    table: {
        textAlign: 'center',
        flexDirection: 'row',
        alignSelf: 'stretch',
    },
    tableHead: {
        textAlign: 'center',
        flexDirection: 'row',
        alignSelf: 'stretch',
    },
    rows: {
        fontSize: 12,
        backgroundColor: '#7adac4',
        textAlign: 'center',
        marginBottom: 1,
        alignSelf: 'stretch',
        flex: 1,
        height: 37,
        lineHeight: 37,
    },
    headRows: {
        fontSize: 15,
        backgroundColor: '#0ac092',
        textAlign: 'center',
        marginBottom: 1,
        alignSelf: 'stretch',
        flex: 1,
        height: 40,
        lineHeight: 40,
        fontWeight: 'bold',
    }
})
```

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/056.png?raw=true "The effects on Android")
The effects on Android



