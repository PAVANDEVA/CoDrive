<template>
  <view>
    <view class="header">
      <image
        :style="{marginTop:9,marginBottom:5}"
        :source="require('/CoDrive/assets/images/Avtar.png')"
      />
      <text
        :style="{fontSize:14,fontWeight:bold,color:'black',letterSpacing:0,marginLeft:120,paddingTop:10}"
      >MY RIDE</text>
    </view>
    <view class="segment-style">
      <button
        :style="{marginRight:120}"
        title="UPCOMING"
        :on-press="search"
        color="#rgba(255, 174, 0, 0.986)"
        expand="block"
      />
      <button
        :style="{marginLeft:auto}"
        title="COMPLETED"
        :on-press="search"
        color="#rgba(255, 174, 0, 0.986)"
        expand="block"
      />
    </view>
    <!-- <status-bar background-color="rgba(255, 174, 0, 0.986)" bar-style="dark-content" /> -->
  </view>
</template>

<script>
import React from "react";
import { Text } from "react-native";

export default {
  props: {
    navigation: { type: Object },
  },
  methods: {
    gototabnav() {
      this.navigation.navigate("BottomTabNavigator");
    },
  },
};
</script>

<style>
.container {
  margin-top: 20;
  margin-left: 25;
  margin-right: 25;
}

.button-style {
  margin-top: 10;
  margin-left: 85;
  margin-right: 85;
}
.input-style {
  height: 40;
  width: 260;
  margin-top: 10;
  margin-bottom: 5;
  margin-left: 30;
  border-color: rgb(234, 240, 245);
  border-bottom-color: slategray;
  border-bottom-width: 1;
  border-radius: 5px;
}
.img-style {
  margin-top: 25;
}
.header {
  /* margin-top: 0;
  margin-bottom: 150; */
  background-color: "#rgba(255, 174, 0, 0.986)";
  flex-direction: row;
}
.content {
  flex-direction: row;
  flex-wrap: wrap;
}
.segment-style {
  background-color: "#rgba(255, 174, 0, 0.986)";
  margin-top: 3;
  margin-bottom: 70;
  flex-direction: row; 
  flex-wrap: nowrap;
}
</style>

