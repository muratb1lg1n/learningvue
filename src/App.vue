<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Countdown msg="Countdown"/>
  </div>
</template>

<script>
import Countdown from './components/Countdown.vue'

export default {
  name: 'App',
  components: {
    Countdown,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
