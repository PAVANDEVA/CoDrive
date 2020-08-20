
<template>
 <AppNavigator/> 
</template>

<script>
import {
createAppContainer,
createStackNavigator,
} from "vue-native-router";

import LoginScreen from "./src/Pages/login/login.vue";
import DashboardScreen from "./src/Pages/dashboard/dashboard.vue";
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
components: { LoginScreen,AppNavigator },
}
</script>