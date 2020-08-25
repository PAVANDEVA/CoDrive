
<template>
<root>
<script src="http://localhost:8098"></script>
 <AppNavigator/> 
</root>
</template>

<script>

import {
createAppContainer,
createStackNavigator,
} from "vue-native-router";
import Vue from "vue-native-core";
import LoginScreen from "./src/Pages/login/login.vue";
import DashboardScreen from "./src/Pages/dashboard/dashboard.vue";
import { VueNativeBase } from "native-base";
import Vuelidate from 'vuelidate';
import { Toast } from 'native-base';
import { Root } from "native-base";

Vue.use(Vuelidate)
Vue.use(VueNativeBase);

console.reportErrorsAsExceptions = false;
const StackNavigator = createStackNavigator(
{
login: LoginScreen,
dashboard: DashboardScreen
},
{
initialRouteName: 'login',
}
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
components: { LoginScreen,AppNavigator,Root},
}
</script>