<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <GenerateWorkout></GenerateWorkout>
</template>

<script>
import GenerateWorkout from './components/GenerateWorkout.vue'

export default {
  name: 'App',
  components: {
    GenerateWorkout
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
