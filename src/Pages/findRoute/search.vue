<template>
<view class="container" :style="{backgroundColor: 'white',flex: 1}">
  <view class="navbar">
    <image class="icon" :style="{marginRight: 'auto',marginLeft: 15}"
    :source="require('/CoDrive/assets/images/person-m.png')"
    />
    <text class="page">SEARCH</text>
    <touchable-opacity :on-press="onPressButton" :style="{marginLeft: 'auto',marginRight: 15}">
      <image class="icon"
      :source="require('/CoDrive/assets/images/person-m.png')"
      />
    </touchable-opacity>
  </view>

  <view class="routeForm">
    <view class="routeDetails">
      <text-input class="setup" placeholder="Origin" v-model="stratLocation"/>
      <image class="addPoint" :style="{marginTop: 15}"
       :source="require('/CoDrive/assets/images/addpoint.png')"
      />
    </view>

     <view class="routeDetails">
      <text-input class="setup" placeholder="Destination" v-model="dropLocation"/>
      <image class="addPoint" :style="{marginTop: 15}"
       :source="require('/CoDrive/assets/images/addpoint.png')"
      />      
    </view>

    <view class="routeDetails">
      <image class="addPoint" :style="{marginLeft: 35}"
         :source="require('/CoDrive/assets/images/calendar.png')"
       />
        <text-input class="setup" placeholder="From" :style="{width: '35%',height:35,paddingBottom:1,marginLeft:0}"/>
        <image class="addPoint" :style="{marginLeft: 10}"
         :source="require('/CoDrive/assets/images/calendar.png')"
       />
        <text-input class="setup" placeholder="To" :style="{width: '35%',height:36,paddingBottom:1,marginLeft:0}"/>
    </view>

    <view class="routeDetails">
      <text class="page" :style="{marginLeft: 'auto',marginRight:40}">Time</text>
      <touchable-opacity :style="{marginRight: 'auto',marginLeft:10}">
        <text class="page">9:00</text>
      </touchable-opacity>
    </view>

    <view class="weekDays">
        <view class="days">
          <text>S U</text>
          <CheckBox/>
        </view>
        <view class="days">
          <text>M</text>
          <CheckBox/>
        </view>
        <view class="days">
          <text>T</text>
          <CheckBox/>
        </view>
        <view class="days">
          <text>W</text>
          <CheckBox/>
        </view>
        <view class="days">
          <text>T H</text>
          <CheckBox/>
        </view>
        <view class="days">
          <text>F</text>
          <CheckBox/>
        </view>
        <view class="days" :style="{borderColor: 'white'}">
          <text>S</text>
          <CheckBox/>
        </view>
     </view>

     <view class="submit">
        <touchable-opacity
            :style="{backgroundColor: 'orange',padding: 10,borderRadius: 20,alignItems:'center'}">
            <text :style="{color: 'white'}">OK</text>
        </touchable-opacity>
      </view>
  </view>

      <view class="navbar" :style="{marginTop: 'auto',height: 60}">
        <view class="navbar" :style="{height : 60,width: '33%',flexDirection: 'column'}">
          <image :style="{height: 25,width: 25}"
           :source="require('/CoDrive/assets/images/myroute.png')"
           />
          <text class="page">My Ride</text>
        </view>
        <view class="navbar" :style="{height : 60,width: '33%',flexDirection: 'column'}">
          <image :style="{height: 25,width: 25}"
           :source="require('/CoDrive/assets/images/newroute.png')"
           />
          <text class="page">New Route</text>
        </view>
        <view class="navbar" :style="{height : 60,width: '33%',flexDirection: 'column',borderColor: 'brown',borderTopWidth: 3}">
          <image :style="{height: 25,width: 25}"
           :source="require('/CoDrive/assets/images/find.png')"
           />
          <text class="page">Find Ride</text>
        </view>
      </view>
      
</view>

</template>

<script>
export default {
  data(){
    return{
      stratLocation: '',
      dropLocation: ''
    }
  },
  methods: {
    onPressButton: function() {
            Alert.alert(
                'Alert',
                'Are you sure you want to log out?',
                [
                    {text: 'Cancel', onPress: () => console.log('Cancel Pressed'), style: 'cancel'},
                    {text: 'OK', onPress: () => console.log('OK Pressed')},
                ],
                { cancelable: false }
            )
          }
  }
}
</script>

<style>

.navbar{
  flex-direction: row;
  background-color:orange;
  height: 50px;
  justify-content: center;
  align-items: center;
}

.icon{
  height: 25;
  width: 25;
}

.page{
  color: black;
  font-size: 15;
  font-weight: 400;
}

.routeForm{
  width: 90%;
  align-self: center;
}

.routeDetails{
  flex-direction: row;
  margin-top: 20;
}

.setup{
  width: 70%;
  border-color: slategray;
  border-bottom-width: 1;
  border-radius: 5;
  margin-left: 40;
}

.addPoint{
  margin-top: 15;
  height: 20;
  width: 20;
}

.page{
  color: black;
  font-size: 15;
  font-weight: 400;
}

.weekDays{
  background-color:white;
  margin-top: 20;
  height: 80;
  border-radius: 20;
  elevation: 5;
  flex-direction: row;
}

.days{
  height: 65;
  width: 14.5%;
  align-self: center;
  justify-content: center;
  align-items: center;
  border-color: gray;
  border-right-width: 1;
}

.submit{
  width: 50%;
  margin-top: 15;
  align-self: center;
}

</style>