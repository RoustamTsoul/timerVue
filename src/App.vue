<template>
<div id="app" class="timer-container">
  <TimerComponent/>
</div>
</template>

<script>
import TimerComponent from './components/TimerComponent.vue'

export default {
  name: 'App',
  components: {
    TimerComponent 
  },

}
</script>

<style>
body{
  font-family:"Broadway";
  background-color: rgb(32, 144, 32);
}

.timer-container{
background-color: rgb(18, 106, 147);
border: 5px solid white;
border-radius: 6px;
margin-top: 20%;
}
</style>