
<template>
<root>
<!-- <status-bar background-color="rgba(255, 174, 0, 0.986)" bar-style="dark-content" /> -->
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
import { Datetime } from 'vue-datetime';
import { VueNativeBase } from "native-base";
import Vuelidate from 'vuelidate';
import { Toast } from 'native-base';
import { Root } from "native-base";

Vue.use(Vuelidate)
Vue.use(VueNativeBase);
Vue.component('datetime', Datetime);
console.reportErrorsAsExceptions = false;
const StackNavigator = createStackNavigator(
{
login: LoginScreen,
dashboard: DashboardScreen,

},
{
initialRouteName: 'login',
 headerMode: "none"
}
);

const AppNavigator = createAppContainer(StackNavigator);

export default {
components: { LoginScreen,AppNavigator,Root},
}
</script>