<template>
  <div id="app">

   
      <NavbarComponent />
    <TimeComponent  />
   
  </div>
</template>

<script>
 import NavbarComponent from "./components/navbar/NavbarComponent.vue";
import TimeComponent from './components/time/TimeComponent.vue';

export default {
  name: 'App',
  components: {
    NavbarComponent,
    TimeComponent
  }
}
</script>


<style>
 
   
</style>
 