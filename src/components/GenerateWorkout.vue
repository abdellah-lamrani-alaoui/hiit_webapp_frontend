<template>
    <div id="app">
      <div>
      <p v-if="!image_url"> With WorkoutNow, you can generate a new workout designed by the best HIIT Coaches</p>
      <br>
      </div>
      <button @click="generate_workout">{{ button_caption }}</button>
      <div>
      <br>
      <div v-if="workout_type === 'image'">
          <img v-if="url" :src="url" height="400">
      </div>
      <div v-else>
        <iframe v-if="url" :src="url" width="420" height="315" allowFullScreen></iframe>
      </div>
      <br>
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
  return {url : "", timer_url : "", duration_minutes : "", button_caption : "Generate Workout", workout_type: ""}
  },
  methods: {
    generate_workout: function() {
      this.button_caption = "Change Workout";
      axios.get("https://workoutnowdev.herokuapp.com/workout").then(response => (this.url = response.data.url,
      this.timer_url = response.data.timer_url, this.duration_minutes = response.data.duration_minutes,
      this.workout_type = response.data.workout_type))
      }
    }
};
</script>

<style>
button {
  padding: 10px 20px;
  border: 2px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
  font-family: '微软雅黑',arail;
  cursor: pointer;
  background-color: #4c76c4;
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
