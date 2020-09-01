<template>
  <app-navigator></app-navigator>
</template>

<script>
import {
  createAppContainer,
  createStackNavigator,
} from "vue-native-router";
import Vue from "vue-native-core";
import NewRouteScreen from "./src/Pages/newRoute/newRoute.vue";
import { Datetime } from 'vue-datetime';
import { VueNativeBase } from "native-base";
import Vuelidate from 'vuelidate';
import { Toast } from 'native-base';
import { Root } from "native-base";

const StackNavigator = createStackNavigator(
  {
    Main: NewRouteScreen,
  },
  {
    initialRouteName: 'Main',
  }
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
  components: { NewRouteScreen,AppNavigator },
}
</script>