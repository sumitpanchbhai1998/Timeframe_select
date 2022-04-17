<template>

<div class="dropdown">
<template>
 <v-row align="center">
 <v-col cols="3">
 <v-text-field
 v-model="DayNumber"
 type="number"
 label="Day"   @change="method_1"
 ></v-text-field>
 </v-col>
 <v-col cols="3">
 <v-text-field
 v-model="HourNumber"
  type="number"
 label="Hours"  @change="method_1"
 ></v-text-field>
 </v-col>
<v-col cols="3">
 <v-text-field
 v-model="MinuteNumber"  
 type="number"
 label="Minutes"   @change="method_1"
></v-text-field>
 </v-col>
<v-col cols="3">
<v-text-field
v-model="secondNumber"
 type="number"
 label="Seconds"    @change="method_1"
 ></v-text-field>
</v-col>
</v-row>
 </template>
</div>

</template>

<script>
export default {
    name:'timeFrame',
    data(){
        return {
            timeframe:['30s','50s','70s'],
            timeframe_val:'',
            DayNumber:null,
            secondNumber:null,
            MinuteNumber:null,
            HourNumber:null


        }
    },
    methods:{
      method_1(){
        if (this.DayNumber !== null || this.secondNumber !== null || this.MinuteNumber !== null || this.HourNumber !== null){
            this.$emit('enableSlider',true)
        }
        console.log("Slider Enable");

    },
    }
  
}
</script>

<style scoped>
.dropdown{
    width:600px ;
    position: relative;
    left: 30px;
    right: 30px;
  } 
</style>