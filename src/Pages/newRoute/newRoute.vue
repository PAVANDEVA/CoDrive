<template>
  <view class="container" :style="{backgroundColor: 'white',flex: 1}">
        
    <view class="navbar">
       <image class="avatar" :style="{marginRight: 'auto'}"
       :source="require('/CoDrive/assets/images/person-m.png')"
       />
       <text class="page" :style="{marginRight: 'auto'}">NEW ROUTE</text>
       <touchable-opacity :on-press="onPressButton">
       <image class="logout" :style="{marginLeft: 'auto'}"
        :source="require('/CoDrive/assets/images/person-m.png')"
       />
       </touchable-opacity>
    </view>

    <view class="newRouteForm">

      <view class="routeDetails">
        <text-input class="setup" placeholder="Origin" v-model="startLocation"/>
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
        <text-input class="setup" placeholder="Pick-up Point" v-model="pickupLocation"/>
        <image class="addPoint" :style="{marginTop: 15}"
         :source="require('/CoDrive/assets/images/addpoint.png')"
        />
        <touchable-opacity :on-press="newTodo">
        <image class="addPoint" :style="{marginTop: 15,marginLeft: 10}"
         :source="require('/CoDrive/assets/images/add.png')"
        />
        </touchable-opacity>
      </view>

      <!-- <view class="todo" v-for="todo in todos" :key="todo.id">
        <text v-if="todo.done">{{todo.title}}</text>
        <text v-else>{{todo.title}}</text>
        <touchable-opacity :on-press="() => removeTodo(todo.id)">
          <text>Remove</text>
        </touchable-opacity>
      </view> -->

      <view class="routeDetails" :style="{paddingTop: 15}">
        <text class="page">Seats</text>
        <touchable-opacity class="buttonStyling"
         :style="{borderColor: 'red'}" >
         <text :style="{color: 'red',paddingBottom: 12}">_</text>
        </touchable-opacity>
        <text class="page" :style="{marginLeft: 5,marginRight: 5}">{{count}}</text>
        <touchable-opacity class="buttonStyling"
         :style="{borderColor: 'green',marginLeft: 0,marginRight: 20,paddingBottom: 2}">
         <text :style="{color: 'green'}">+</text>
        </touchable-opacity>
        <text class="page" :style="{marginLeft: 10}">Time</text>
        <touchable-opacity>
         <text class="page" :style="{marginLeft: 20}">09:00</text>
        </touchable-opacity>
      </view>

      <view class="routeDetails">
        <image class="addPoint" :style="{marginTop: 0}"
         :source="require('/CoDrive/assets/images/calendar.png')"
       />
        <text-input class="setup" placeholder="From" :style="{width: '50%',height: 25,paddingBottom:1}"/>
        <image class="addPoint" :style="{marginTop: 0}"
         :source="require('/CoDrive/assets/images/calendar.png')"
       />
        <text-input class="setup" placeholder="To" :style="{width: '50%',height: 25,paddingBottom:1}"/>
      </view>
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

      <view class="navbar" :style="{marginTop: 'auto',height: 60}">
        <view class="navbar" :style="{height : 60,width: '33%',flexDirection: 'column'}">
          <image :style="{height: 25,width: 25}"
           :source="require('/CoDrive/assets/images/myroute.png')"
           />
          <text class="page">My Ride</text>
        </view>
        <view class="navbar" :style="{height : 60,width: '33%',flexDirection: 'column',borderColor: 'brown',borderTopWidth: 3}">
          <image :style="{height: 25,width: 25}"
           :source="require('/CoDrive/assets/images/newroute.png')"
           />
          <text class="page">New Route</text>
        </view>
        <view class="navbar" :style="{height : 60,width: '33%',flexDirection: 'column'}">
          <image :style="{height: 25,width: 25}"
           :source="require('/CoDrive/assets/images/find.png')"
           />
          <text class="page">Find Ride</text>
        </view>
      </view>
  </view>

</template>

<script>
import { Alert } from 'react-native';
    export default {
        
        data(){
            return {
                count: 1,
                startLocation: "",
                dropLocation: "",
                pickupLocation: '',
                todos: [
                  {
                    id: 0,
                    title: 'jntu',
                    done: false,
                  }
                ]
            };
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
          },
          newTodo(){
            this.todos.push({
              id: this.todos.length + 1,
              title: this.pickupLocation,
              done: false
            });

            this.pickupLocation = '';
          },
          removeTodo(id){
            this.todos = this.todos.filter(todo => todo.id !== id);
          },
       }
      }
</script>

<style>

.navbar {
  flex-direction: row;
  background-color:orange;
  height: 50px;
  justify-content: center;
  align-items: center;
}

.avatar{
  margin-left: 15;
  height: 25;
  width: 25;
}

.page{
  color: black;
  font-size: 15;
  font-weight: 400;
}

.logout{
  margin-right: 15;
  height: 25;
  width: 25;
}

.newRouteForm {
  margin-top: 20;
  margin-left: 50;
  margin-right: 100;
}

.setup{
  width: 100%;
  border-color: slategray;
  border-bottom-width: 1;
  border-radius: 5px;
}

.routeDetails{
  flex-direction: row;
  height: 50;
  margin-top:20;
}

.addPoint{
  margin-top: 15;
  height: 25;
  width: 25;
}

.buttonStyling{ 
  justify-content: center;
  align-items: center;
  height: 15;
  width: 15;
  background-color: white;
  border-width: 1;
  border-radius: 15;
  margin-left: 50;
  margin-top:3;
}
.weekDays{
  background-color:white;
  margin: auto;
  height: 80;
  width:90%;
  align-self: center;
  border-radius: 20;
  elevation: 5;
  flex-direction: row;
}
.days{
  height: 65;
  width: 14.5%;
  align-self: center;
  flex-direction: column;
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

/* .todo{
  background-color: whitesmoke;
  flex-direction: row;
  height: 30;
  width: 100%;
  justify-content: center;
  align-items: center;
  align-self: center;
  
} */


</style>