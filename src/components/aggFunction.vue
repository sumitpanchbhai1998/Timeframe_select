<template>
<div class="dropdown">
  <template>
  <v-row >
    <v-col cols="12">
      <v-select
        :items="items_func"
        :menu-props="{ top: true, offsetY: true }"
        label="Function"
        v-model="Function_val" @change="method_1"
      ></v-select>
    </v-col>
  </v-row>
  </template>
</div>
</template>

<script>
export default {
    name:'aggFunction',
    data(){
        return {
            items_func:['AVG', 'MAX', 'MIN', 'SUM'],
            Function_val:'',

        }
    },
    methods:{
    method_1(){
    if (this.Function_val != ''){
      this.$emit('timeFrameDisable',true);
      console.log("Enable the timeframe")
    }
  }

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