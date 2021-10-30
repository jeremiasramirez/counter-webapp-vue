<template>
 
  

  <section>
    <!-- menu "-->
     <article class="menu animate" v-if="hide==true">

      <nav class="menu__nav">
          <p class="bounceLeft menu__nav__title">History</p>
      </nav>


    </article>



  <!-- close menu -->
    <div class="closeMenu">
        <md-button v-on:click="createMenu()" v-if="hide==false">
         <img class="zoomIn" src="../../assets/icons/menu.svg" alt="icon" />
        </md-button>

        <md-button  v-if="hide==true" v-on:click="createMenu()">
         <img class="zoomIn" src="../../assets/icons/close.svg" alt="icon" />
        </md-button>
    </div>
  

    <section class="container__time">
    

    <article class="set__container animate" v-if="!isClose">
      <div class="container__input">
        <input
          v-model="hours__model"
          class="input__set "
          type="text"
          placeholder="00"
        /> <p class="separate">:</p>
        <input
          v-model="minutes__model"
          class="input__set "
          type="text"
          placeholder="00"
        /><p class="separate">:</p>
        <input
          v-model="seconds__model"
          class="input__set "
          type="text"
          placeholder="00"
        />
      </div>
    </article>

    <div  v-if="isClose" >
        <RunningComponent :hours__props="newCounter.getHours()"
        :minutes__props="newCounter.getMinutes()"
        :seconds__props="newCounter.getSeconds()"/>
    </div>
   
    
    <article class="buttoners animate">
      <md-button
       
        class="md-icon-button md-raised md-primary "
        v-if="isPaused"
        v-on:click="createCounter()"
      >
        <img class="zoomIn" src="../../assets/icons/play_arrow_white_24dp.svg" alt="icon" />
      </md-button>



      <md-button class="md-icon-button md-raised md" v-if="!isPaused" v-on:click="pauseInterval()">
        <img class="zoomIn" src="../../assets/icons/pause_black_24dp.svg" alt="icon" />
      </md-button>  

      <md-button class="md-icon-button md-raised md-accent"
       v-if="isRunningCounter && !isStop"
       v-on:click="cleanInterval()">
       
        <img class="zoomIn" src="../../assets/icons/stop_white_24dp.svg" alt="icon" />
      </md-button>


        <md-button
       
        class="md-icon-button md-raised md"
        v-if="isClose"
        v-on:click="closeRunning()"
      >
        <img class="zoomIn" src="../../assets/icons/close_black_24dp.svg" alt="icon" />
      </md-button>
    </article>
  
    
  </section>
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
      seconds__model: 1,
      times: "",
      isPaused: true,
      isRunningCounter:false,
      isStop: true,
      counterInterval: null,
      isClose:false,
    
      ishide:false,
      hide:false,
      newCounter:null 
    };
  },
  components:{
      RunningComponent
  },
  methods: {


    createMenu(){
 
      if(!this.hide==true) this.hide=true;
      else this.hide=false;

    },


    closeRunning(){
      this.isClose=false
       this.isRunningCounter=false
      this.cleanInterval()
      
    },

    pauseInterval(counterInterval) {
        this.isPaused=true;
        clearInterval(counterInterval);
        clearInterval(this.counterInterval);
    },
     

    cleanInterval(){
  
        this.pauseInterval()
      
        this.newCounter.setHours(0)
        this.newCounter.setMinutes(0)
        this.newCounter.setSeconds(0)

        this.hours__model=0
        this.minutes__model=0
        this.seconds__model=0
        this.isRunningCounter=false
          this.isStop=false
          
    },

    createCounter() {
      
      if(this.hours__model>=1 || this.minutes__model >=1 || this.seconds__model>=1){

        this.isClose=true
        this.isPaused=false
        this.isRunningCounter=true;
      this.isStop=false
      
      this.counterInterval = setInterval(() => {

       this.newCounter = new Date();

       this.newCounter.setHours(
          this.hours__model,
          this.minutes__model,
          --this.seconds__model+1
        );
        this.times = `${this.newCounter.getHours()}  - ${this.newCounter.getMinutes()} - ${this.newCounter.getSeconds()}`;

        if (
          this.newCounter.getHours() == 0 &&
          this.newCounter.getMinutes() == 0 &&
          this.newCounter.getSeconds() == 0
        ) {
          this.cleanInterval()
          this.pauseInterval(this.counterInterval);
         
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
  border: 10px solid rgba(58, 67, 189, 0.26);
  border-radius: 50%;
  overflow:hidden;
}

.separate{
  color:blue;
  font-weight: 600;
  font-size:18px;
 
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
  position:absolute;
  top:52%;
  margin-top: 40px;
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
  border-radius: 10%;
  color: blue;
  border: 1px solid #eee;
  outline: none;
  margin: 0 2px;
  background-color: #eee;
  font-weight: 600;
  font-size: 17px;
  font-family: "ubuntu";
}


.closeMenu{
  position:absolute;

  top:0px;
  left:-20px;
  height:100px !important;
}

.closeMenu *{
 
  margin:-1px 0 0 0 !important;
  height: 51px !important;
  background-color:rgb(30, 59, 185) !important;
}
.closeMenu img{
  margin-left:15px !important;
  margin-top:7px !important;
   height: 37px !important;
   
}
.hide{
  opacity:0;
}

.menu{
  position:absolute;
  width:20%;
  background-color: rgb(250, 245, 245);
  height:100%;
  border-right:2px solid rgb(230, 226, 226);
}

.menu__nav{
  border-bottom:1px solid #eee;
  /* margin-top: -16px; */
  height:30px;
}

.menu__nav__title{
  font-size:16px;
  text-align:center;
  font-family: "ubuntu";
  font-weight:500;
}
</style>