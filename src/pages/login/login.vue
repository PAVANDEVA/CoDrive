<template>
  <view class="container">
    <text>Login</text>
    <button title="Go to Dashboard" @press="goToHomeScreen"></button>
  </view>
</template>

<script>
export default {
  // Declare `navigation` as a prop
  props: {
    navigation: {
      type: Object
    }
  },
  methods: {
    goToHomeScreen() {
      this.navigation.navigate("dashboard");
    }
  }
}
</script>