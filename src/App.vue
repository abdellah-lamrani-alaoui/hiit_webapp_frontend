<template>
  <img alt="Vue logo" src="./assets/smaller_logo_vectorized.png">
  <GenerateWorkout></GenerateWorkout>
  <br>
  <br>
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
