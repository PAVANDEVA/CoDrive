  <template>
  <view>
    <view class="header">
      <image
        :style="{marginTop:9,marginBottom:5}"
        :source="require('/CoDrive/assets/images/Avtar.png')"
      />
      <text
        :style="{fontSize:14,fontWeight:bold,color:'black',letterSpacing:0,marginLeft:120,paddingTop:10}"
      >NEW ROUTE</text>
    </view>
    
    <view class="container">
      <view class="content">
        <text-input class="input-style" v-model="origin" placeholder="Origin" />

        <image class="img-style" :source="require('/CoDrive/assets/images/addpoint.png')" />
      </view>
      <view class="content">
        <text-input class="input-style" v-model="destination" placeholder="Destination" />
        <image class="img-style" :source="require('/CoDrive/assets/images/addpoint.png')" />
      </view>
      <view class="content">
        <text-input class="input-style" v-model="destination" placeholder="pick-up Point" />
        <image class="img-style" :source="require('/CoDrive/assets/images/addpoint.png')" />
        <image class="img-style" :source="require('/CoDrive/assets/images/add.png')" />
      </view>
      <view :style="{marginLeft:20}" class="content">
        <image
          :style="{marginTop:9,marginBottom:5}"
          :source="require('/CoDrive/assets/images/calendar.png')"
        />
        <nb-date-picker
          :modalTransparent="false"
          animationType="fade"
          androidMode="spinner"
          placeHolderText="From"
          :textStyle="{ color: 'black' }"
          :placeHolderTextStyle="{ color: '#726E6D' }"
          :onDateChange="setDate"
          :borderRadius="5"
        />
        <image
          :style="{marginLeft:20,marginTop:9,marginBottom:5}"
          :source="require('/CoDrive/assets/images/calendar.png')"
        />
        <nb-date-picker
          :modalTransparent="false"
          animationType="fade"
          androidMode="spinner"
          placeHolderText="To"
          :textStyle="{ color: 'black' }"
          :placeHolderTextStyle="{ color: '#726E6D' }"
          :onDateChange="setDate"
          :borderRadius="5"
        />
      </view>
      <view class="button-style">
        <button title="OK" :on-press="search" color="darkorange" capitalize />
      </view>
      <!-- <status-bar background-color="rgba(255, 174, 0, 0.986)" bar-style="dark-content" /> -->
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      origin: "",
      destination: "",
    };
  },
   methods:{
    setDate: function(newDate) {
      this.chosenDate = newDate;
    }
  },

  props: {
    navigation: { type: Object },
  },
};
</script>

<style>
.container {
  margin-top: 20;
  margin-left: 25;
  margin-right: 10;
}
.button-style {
  margin-top: 10;
  margin-left: 85;
  margin-right: 105;
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
</style>