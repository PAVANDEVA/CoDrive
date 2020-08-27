<template>
  <app-navigator></app-navigator>
</template>

<script>
import React from "react";
import {
  createAppContainer,
  createBottomTabNavigator,
  createMaterialBottomTabNavigator,
  createMaterialTopTabNavigator,
  createStackNavigator,
} from "vue-native-router";
import myrouteIcon from "../../../assets/images/myroute.png";
import AntDesignIcons from "react-native-vector-icons/AntDesign"
import MyRouteScreen from "../my-route.vue";
import NewRouteScreen from "../new-route.vue";
import SearchScreen from "../search.vue";
import {Image} from 'react-native';
import MaterialIcons from "react-native-vector-icons/MaterialIcons";
import Icon from 'react-native-vector-icons/Ionicons';  

const BottomTabNavigator = createMaterialBottomTabNavigator({
  MyRoute: {
    screen: MyRouteScreen,

    navigationOptions: ({ navigation }) => ({
      tabBarOptions: { showIcon: true, },
      labelStyle: {
    fontSize: 12,
  },
      title: "My Route",
      tabBarLabel: "My Route",
      tabBarIcon: ({ focused, tintColor }) => {
        return <AntDesignIcons name="user" size={22} color="#FFFFFF" />;
      },
      fontStyle: 40,
      fontWeight: "bold",
      activeColor: "#f6980c",
      inactiveColor: "#f65a22",
      barStyle: { backgroundColor: "#f6980c" },
    }),
  },
  NewRoute: {
    screen: NewRouteScreen,
    navigationOptions: ({ navigation }) => ({
      labelStyle: {
        fontSize: 12,
      },
      tabBarLabel: "New Route",
      tabBarOptions: { showIcon: true, },
      tabBarIcon: ({ focused, tintColor }) => {
        return <MaterialIcons name="add-location" size={22} color="#FFFFFF" />;
      },
      fontStyle: 30,
      fontWeight: "bold",
      activeColor: "#f6980c",
      inactiveColor: "#f65a22",
      barStyle: { backgroundColor: "#f6980c" },
    }),
  },
  Search: {
    screen: SearchScreen,
    navigationOptions: ({ navigation }) => ({
      tabBarLabel: "Search",
      labelStyle: {
    fontSize: 16,
    fontWeight:'bold',
  },
      tabBarOptions: { showIcon: true, },
      tabBarIcon: ({ focused, tintColor }) => {
        return <Icon name="search" size={22} color="#FFFFFF" />;
      },
      fontStyle: 30,
      fontWeight: "bold",
      activeColor: "#f6980c",
      inactiveColor: "#f65a22",
      barStyle: { backgroundColor: "#f6980c" },
    }),
  },
});

const StackNavigator = createStackNavigator(
  {
    MyRoute: MyRouteScreen,
    BottomTabNavigator,
  },
  {
    initialRouteName: "BottomTabNavigator",
    headerMode: "none",
  }
);

const AppNavigator = createAppContainer(StackNavigator);
export default {
  components: { AppNavigator, StackNavigator },
  // Declare `navigation` as a prop
  props: {
    navigation: {
      type: Object,
    },
  },
  created() {
    this.navigation.navigate("BottomTabNavigator");
  },
  methods: {
    goToNewRouteScreen() {
      this.navigation.navigate("MyRoute");
    },
    goToMyRideScreen() {
      this.navigation.navigate("NewRoute");
    },
  },
};
</script>
