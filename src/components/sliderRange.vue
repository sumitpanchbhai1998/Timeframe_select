<template>

<div class="slider">
  <template>
    <v-subheader>Select range</v-subheader>
      <v-row>
        <v-col class="pr-4" cols="12" >
          <v-slider
            v-model="slider"
            :max="max"
            :min="min"
            hide-details
          >
            <template v-slot:append>
              <v-text-field
                v-model="slider"
                class="mt-0 pt-0"
                hide-details
                single-line
                type="number"
                style="width: 60px" 
              ></v-text-field>
            </template>
          </v-slider>
        </v-col>
      </v-row>
    </template>
  </div>
    
</template>

<script>
export default {
    name:'sliderRange',
    data(){
        return {
            min: 0,
            max: 500,
            slider: null,
        }
    },
  methods:{
    
  }
}
</script>

<style scoped>
.slider{
    padding-left: 20px;
    padding-right:50px ;
  }

</style>