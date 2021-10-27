<template>
  <section class="container__time">
    <article class="set__container">
      <div class="container__input">
        <input
          v-model="hours__model"
          class="input__set"
          type="text"
          placeholder="00"
        />
        <input
          v-model="minutes__model"
          class="input__set"
          type="text"
          placeholder="00"
        />
        <input
          v-model="seconds__model"
          class="input__set"
          type="text"
          placeholder="00"
        />
      </div>
    </article>

    <div  v-if="isRunningCounter" >
        <RunningComponent :hours__props="newCounter.getHours()"
        :minutes__props="newCounter.getMinutes()"
        :seconds__props="newCounter.getSeconds()"/>
    </div>
   
    
    <article class="buttoners">
      <md-button
       
        class="md-icon-button md-raised md-primary"
        v-if="isPaused"
        v-on:click="createCounter()"
      >
        <img src="../../assets/icons/play_arrow_white_24dp.svg" alt="icon" />
      </md-button>

      <md-button
        class="md-icon-button md-raised md"
        v:on-click="!isClose"
      >
        <img src="../../assets/icons/replay_black_24dp.svg" alt="icon" />
      </md-button>  

      <md-button class="md-icon-button md-raised md" v-if="!isPaused" v-on:click="pauseInterval()">
        <img src="../../assets/icons/pause_black_24dp.svg" alt="icon" />
      </md-button>  

      <md-button class="md-icon-button md-raised md-accent"
       v-if="!isStop"
       v-on:click="cleanInterval()">
       
        <img src="../../assets/icons/stop_white_24dp.svg" alt="icon" />
      </md-button>
    </article>
    <!-- {{ hours__model }} - {{ minutes__model }} - {{ seconds__model}} -->
    {{ times }}
    
  </section>
 
</template>

<script>
import Vue from "vue";
import { MdButton } from "vue-material/dist/components";
import "vue-material/dist/vue-material.min.css";
import "vue-material/dist/theme/default.css";
import RunningComponent from "../running/RunningComponent.vue";
Vue.use(MdButton);

export default {
  data() {
    return {
      hours__model: 0,
      minutes__model: 0,
      seconds__model: 0,
      times: "",
      isPaused: true,
      isRunningCounter:false,
      isStop: true,
      counterInterval: null,
      isClose:true,
      newCounter:null 
    };
  },
  components:{
      RunningComponent
  },
  methods: {
    pauseInterval(counterInterval) {
        this.isPaused=true;
        clearInterval(counterInterval);
        clearInterval(this.counterInterval);
        
    },
     

    cleanInterval(){
      this.isStop=false
        this.pauseInterval()
      
        this.newCounter.setHours(0)
        this.newCounter.setMinutes(0)
        this.newCounter.setSeconds(0)

        this.hours__model=0
        this.minutes__model=0
        this.seconds__model=0
        // this.isRunningCounter=false;
        
    },

    createCounter() {
      
      if(this.hours__model>=1 || this.minutes__model >=1 || this.seconds__model>=1){

         
        this.isPaused=false
        this.isRunningCounter=true;
      this.isStop=false
      
      this.counterInterval = setInterval(() => {

       this.newCounter = new Date();

       this.newCounter.setHours(
          this.hours__model,
          this.minutes__model,
          --this.seconds__model
        );
        this.times = `${this.newCounter.getHours()}  - ${this.newCounter.getMinutes()} - ${this.newCounter.getSeconds()}`;

        if (
          this.newCounter.getHours() == 0 &&
          this.newCounter.getMinutes() == 0 &&
          this.newCounter.getSeconds() == 0
        ) {
          this.cleanInterval()
          this.stopInterval(this.counterInterval);
         
        }

        


      }, 1000);
    }
    }
  },
};
</script>
    











<style>



.set__container {
  width: 250px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  height: 250px;
  background-color: rgb(99, 36, 136);
  border-radius: 50%;
  overflow:hidden;
}
.container__input {
  display: flex;
  justify-content: center;
  overflow:hidden;
  flex-wrap: wrap;
}
.container__time {
  padding-top: 50px;
  display: flex;
  justify-content: end;
  flex-wrap: wrap;
  align-items: center;
  flex-direction: column;
  
}

.buttoners {
  margin-top: 25px;
  display: flex;
  justify-content: center;
  background-color: #eee;
  border-radius: 10px;
  padding: 10px 20px;
  /* width: 290px; */
  flex-wrap: wrap;
}

.input__set {
  width: 55px !important;
  height: 55px;
  text-align: center;
  border-radius: 50%;
  border: 1px solid #eee;
  outline: none;
  margin: 0 2px;
  background-color: white;
  font-weight: 600;
  font-size: 17px;
  font-family: "ubuntu";
}
</style>