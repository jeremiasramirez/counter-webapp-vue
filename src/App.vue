<template>
  <div id="app">

      <SplashsCreen   v-if="!isCharged"/>

      <section v-if="isCharged">
        <NavbarComponent />
        <TimeComponent  />
      </section>

      {{charged()}}
  </div>
</template>

<script>
import SplashsCreen from "./components/splash/SplashScreen.vue";
import NavbarComponent from "./components/navbar/NavbarComponent.vue";
import TimeComponent from './components/time/TimeComponent.vue';

export default {
  name: 'App',
  components: {
    NavbarComponent,
    TimeComponent,
    SplashsCreen
  },
  data() {
    return {
      isCharged:false
    }
  },
  methods :{
      
      charged(){
        setTimeout(()=>{
          this.isCharged=true;
        },2000)
          
      }
 
  }
}
</script>


<style>
 
   
</style>
 