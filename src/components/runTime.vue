<template>
<v-app>
<v-card
  class="flexcard"
  min-height="300px"
  elevation="19"
  outlined
  tile
  shaped color="light-green lighten-4"
>
<v-card-title>Display</v-card-title>
    <selectTime  v-on:aggFunction='FunctionDropdownShow'/>
    <aggFunction v-show="show"   v-on:timeFrameDisable="GroupingIntervalTimeFrmeShow"/>
    <timeFrame v-show="showTimeFrme" v-on:enableSlider="SliderShow" />
    <sliderRange v-show="showSlider"/>

  <div class="buttons">
      <v-btn 
        small
        class="mx-1"
        >Cancel</v-btn>
      <v-btn
        color="primary"
        class="mx-1"
        small
      >Update</v-btn>
  </div>
    
</v-card>

</v-app>
</template>

<script>
import selectTime from '../components/selectTime.vue';
import aggFunction from '../components/aggFunction.vue';
import timeFrame from '../components/timeFrame.vue';
import sliderRange from '../components/sliderRange.vue'
export default {
  name: 'runTime',

  components: {
      selectTime,
      aggFunction,
      timeFrame,
      sliderRange
    
  },
  data(){
    return {
        show:false,
        showTimeFrme:false,
        showSlider:false
    }
  },
  methods:{
    FunctionDropdownShow(arg){
      this.show=arg
    },
    GroupingIntervalTimeFrmeShow(arg1){
      this.showTimeFrme=arg1
    },
    SliderShow(arg){
      this.showSlider=arg
    }
  }
}
</script>

<style scoped>
.flexcard {
  width: 45%;
  display: flex;
  flex-direction: column;
  position: relative;
  left: 350px;
}
.buttons{
  padding-left: 500px;
  padding-bottom: 20px;
  padding-top: 20px; 
}
</style>
