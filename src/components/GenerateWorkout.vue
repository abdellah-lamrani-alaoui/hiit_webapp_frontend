<template>
    <div id="app">
      <div>
      <p v-if="!image_url"> With WorkoutNow, you can generate a new workout designed by the best HIIT Coaches <a href="https://www.lasource-paris.com/" target="_blank">@LaSource :</a></p>
      <br>
      </div>
      <button @click="generate_workout">{{ button_caption }}</button>
      <div>
      <br>
      <img v-if="image_url" :src="image_url" height="400"><br>
      <p v-if="duration_minutes"><b>This is a {{ duration_minutes }} minutes workout !</b> &#128170; &#128170; &#128170;</p>
        <a v-if="timer_url" :href="timer_url" target="_blank"><button class="btn2">Get the Timer </button></a>
      </div>
      <br >
    </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "GenerateWorkout",
  data () {
  return {image_url : "", timer_url : "", duration_minutes : "", button_caption : "Generate Workout"}
  },
  methods: {
    generate_workout: function() {
      this.button_caption = "Change Workout";
      axios.get("https://workoutnowdev.herokuapp.com/workout").then(response => (this.image_url = response.data.image_url, this.timer_url = response.data.timer_url, this.duration_minutes = response.data.duration_minutes))
      }
    }
};
</script>

<style>
button {
  padding: 10px 20px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
  font-family: '微软雅黑',arail;
  cursor: pointer;
  background-color: #6495ED;
  color: #fff;
}
.btn2 {
  padding: 10px 20px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 10px;
  font-family: '微软雅黑',arail;
  cursor: pointer;
  background-color: #51678d;
  color: #fff;
}
</style>
