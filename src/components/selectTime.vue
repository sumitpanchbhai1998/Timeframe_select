<template>
    <div>
  <template>
  <v-container fluid>
  <v-col cols="12">
    <v-radio-group
      v-model="radios"
      mandatory
    >
      <v-radio
        label="Last" @click="method_1" 
        value="radio-1"
      ></v-radio>

      <div v-show="show_last" class="dropdownTime">
      <template>
        <v-row align="center">
        <v-col cols="12">
        <v-select
          :items="items"
          label="Last"
          v-model="select_last"
                                @change="method_5"
        ></v-select>
        </v-col>
        </v-row>
      </template>
      </div>


      <v-radio
        label="Interval" @click="method_2"
        value="radio-2"
      ></v-radio>


      <div v-show="show_custome" class="dropdownTime">
      <template>
        <v-row align="center">
        <v-col cols="12">
        <v-select
          :items="interval"
          label="Intrval"
          v-model="select_last"
                                @change="method_5"
        ></v-select>
        </v-col>
        </v-row>
      </template>
      </div>

      <v-radio
        label="Custome" @click="method_4"
        value="radio-3"
      ></v-radio>

    <div v-show="show_custome_1">
    <v-row>
    <v-col
      cols="5"
    >
      <v-dialog
        ref="dialog"
        v-model="modal"
        :return-value.sync="time"
        persistent
        width="290px"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            v-model="time"
            label="Start Date"
            prepend-icon="mdi-clock-time-four-outline"
            readonly
            v-bind="attrs"   @change="checking"
            v-on="on"                
          ></v-text-field>
        </template>
        <v-time-picker
          v-if="modal"
          v-model="time"
          full-width         @change="checking"
        >
          <v-spacer></v-spacer>
          <v-btn
            text
            color="primary"
            @click="modal = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            color="primary"
            @click="$refs.dialog.save(time)"
          >
            OK
          </v-btn>
        </v-time-picker>
          </v-dialog>
        </v-col>

      <v-col
      cols="5"
      >
      <v-menu
        v-model="menu2"
        :close-on-content-click="false"
        :nudge-right="40"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            v-model="date"
            label="Start Time"
            prepend-icon="mdi-calendar"
            readonly
            v-bind="attrs"
            v-on="on"           
          ></v-text-field>
        </template>
        <v-date-picker
          v-model="date"
          @input="menu2 = false"
        ></v-date-picker>
        </v-menu>
        </v-col>
        </v-row>

    <v-row>
    <v-col
      cols="5"
    >
      <v-dialog
        ref="dialog1"
        v-model="modal_1"
        :return-value.sync="time_1"
        persistent
        width="290px"
      >
            <template v-slot:activator="{ on, attrs }">
            <v-text-field
            v-model="time_1"
            label="End Date"
            prepend-icon="mdi-clock-time-four-outline"
            readonly
            v-bind="attrs"
            v-on="on"             
            ></v-text-field>
            </template>
            <v-time-picker
            v-if="modal_1"
            v-model="time_1"
            full-width                  @change="checking"
            >
            <v-spacer></v-spacer>
            <v-btn
            text
            color="primary"
            @click="modal_1 = false"
            >
            Cancel
            </v-btn>
            <v-btn
            text
            color="primary"
            @click="$refs.dialog1.save(time_1)"
            >
            OK
            </v-btn>
            </v-time-picker>
            </v-dialog>
            </v-col> 

            <v-col
            cols="5"
            >
            <v-menu
            v-model="menu3"
            :close-on-content-click="false"
            :nudge-right="40"
            transition="scale-transition"
            offset-y
            min-width="auto"
            >
            <template v-slot:activator="{ on, attrs }">
            <v-text-field
            v-model="date_1"
            label="End Time"
            prepend-icon="mdi-calendar"
            readonly
            v-bind="attrs"
            v-on="on"                      
            ></v-text-field>
            </template>
            <v-date-picker
            v-model="date_1"
            @input="menu3 = false"
            ></v-date-picker>
            </v-menu>
            </v-col>
            </v-row>
            </div>
            </v-radio-group>
            </v-col>
    </v-container>
    </template>
    </div>


</template>

<script>
export default {
    name:'selectTime',
    data(){
        return {
        radios: null,
        items:['1 Hour', '2 Hour', '3 Hour', '5 Hour','10 Hour'],
        show_custome:false,
        show_custome_1:false,
        show_last:false,
        interval:['Current Hour','Current Day','1-Week(Sun-Sat)','1-Week(Mon-Sun)'],
        select_last:'',
        time: null,
        modal:false,
        menu2: false,
        date: null,
        modal_1:false,
        time_1:null,
        menu3:false,
        date_1:null,
        }
    },
    methods:{
    method_1(){
       this.show_last=!this.show_last;
       this.show_custome=false;
       this.show_custome_1=false;

    },
    method_2(){
      this.show_custome=!this.show_custome;
      this.show_last=false;
      this.show_custome_1=false;
    },
    method_4(){
      this.show_custome_1=!this.show_custome_1;
      this.show_custome=false;
      this.show_last=false;
    },
    checking(){
      console.log(this.time_1)
      console.log(this.date_1)
      console.log(this.date)
      console.log(this.time)
      if (  (this.select_last != '' || ((this.date != null && this.time != null) && (this.date_1!=null && this.time_1!=null)) )){
        console.log("working");
      }
    },
    method_5(){
        if (this.select_last != '' || ((this.date != null && this.time != null) && (this.date_1!=null && this.time_1!=null)) ){
        console.log("method 5 running")
        this.$emit('aggFunction',true);
        console.log("enable the agg function")
      }
    }
    },
    // created(){
    //   if (this.select_last != '' || ((this.date != null && this.time != null) && (this.date_1!=null && this.time_1!=null)) ){
    //     this.$emit('timeFrame',true);
    //   }
    // }

}
</script>

<style scoped>
.dropdownTime{
    width: 600px;
  }
</style>