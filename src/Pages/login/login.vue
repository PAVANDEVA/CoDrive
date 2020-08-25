<template>
  <view class="container">
    <image :style="{marginLeft:70}" :source="require('/CoDrive/assets/images/logo.png')" />
    <image class="splash-logo" :source="require('/CoDrive/assets/images/splash-logo.png')" />
    <text class="content" :style="{color:'orange',fontSize: 25,marginRight: auto,marginTop:15}">Login</text>
    <text-input class="input-style" v-model="emailValue" placeholder="username" />
    <text-input
      class="input-style"
      v-model="password"
      placeholder="Enter password"
      secure-text-entry
    />
    <nb-list-item :onPress="consentChecked">
      <nb-checkbox :checked="consent" color="orange" borderRadius="0" :style="{marginLeft:5}" />
      <nb-body>
        <nb-text small>By using coDrive you agree to our</nb-text>
        <nb-button transparent small>
          <nb-text :style="{color:'orange',fontSize:13,letterSpacing:0}">Privacy Policy</nb-text>
        </nb-button>
      </nb-body>
    </nb-list-item>
    <button class="button-style" :on-press="onSubmit" title="Sign In" color="darkorange" />
    
    <status-bar background-color="rgba(255, 174, 0, 0.986)" bar-style="dark-content" />
  </view>
</template>

<script>
import { WebView } from "react-native-webview";
import { required, email } from "vuelidate/lib/validators";
import { Toast } from "native-base";
import logo from "../../../assets/images/logo.png";
import { StyleSheet } from "react-native";
import { NavigationActions } from 'vue-native-router';
export default {
  data() {
    return {
      emailValue: "",
      password: "",
      consent: false,
      response: [],
      cred: true,
      logo,
      data: [],
      status:false
    };
  },
  validations: {
    emailValue: {
      required,
    },
    password: {
      required,
    },
  },
  components: {
    "web-view": WebView,
  },
  // Declare `navigation` as a prop
  props: {
    navigation: {
      type: Object,
    },
  },

  methods: {
    onSubmit() { 
      alert(this.emailValue);
      alert(this.password);
      if(!this.emailValue ||!this.password|| !this.consent){
      if (!this.emailValue) {
        Toast.show({
          text: "Invalid email",
          buttonText: "Okay",
          duration: 1400,
        });
      } else if (!this.password) {
        Toast.show({
          text: "Please enter Password",
          buttonText: "Okay",
          duration: 1400,
        });
      } else  {
        Toast.show({
          text: "Please accept the privacy policy to proceed",
          buttonText: "Okay",
        });
      } }else {
       // Simple POST request with a JSON body using fetch
      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          username: this.emailValue,
          password: this.password,
        }),
      };
      fetch("http://3.7.237.213:8080/login", requestOptions)
        .then((response) => response.json())
        .then((data) => (this.data = data));
        status=JSON.stringify(this.data.status);
        if(status){
          alert(JSON.stringify(this.data));
          //this.navigation.navigate("dashboard")
        }else{
          alert("Invalid credentials");
        }
      }
    },
    goToHomeScreen() {
      this.navigation.navigate("dashboard");
    },
    consentChecked() {
      this.consent = !this.consent;
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
.content {
  margin-top: 30;
  margin-left: 20;
  letter-spacing: 0;
}
.button-style {
  margin-left: 40;
  margin-right: 40;
  align-self: center;
}
.input-style {
  height: 40;
  margin-top: 10;
  margin-left: 20;
  margin-right: 20;
  border-color: rgb(234, 240, 245);
  border-bottom-color: slategray;
  border-bottom-width: 1;
  border-radius: 5px;
}
.splash-logo {
  align-content: center;
  justify-content: center;
  margin-left: 30;
  margin-top:10;
}
</style>