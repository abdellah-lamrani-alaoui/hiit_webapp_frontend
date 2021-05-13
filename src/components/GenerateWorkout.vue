<template>
    <div id="app">
      <div>
      <p v-if="!image_url"> With WorkoutNow, you can generate a new workout designed by the best HIIT Coaches</p>
      <br>
      <!-- TODO : make more dynamic -->
      <b>Workout duration  </b>
      <select v-model="selected">
        <option disabled value="">Choose a duration</option>
        <option>10 min</option>
        <option>15 min</option>
        <option>20 min</option>
        <option>25 min</option>
        <option>30 min</option>
        <option>40 min</option>
        <option>50 min</option>
        <option>60 min</option>
      </select>
      </div>
      <br>
      <button @click="generate_workout">{{ button_caption }}</button>
      <div>
      <br>
      <div v-if="workout_type === 'image'">
          <img v-if="url" :src="url" height="400">
      </div>
      <div v-else>
        <iframe v-if="url" :src="url" width="420" height="315" allowFullScreen></iframe>
      </div>
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
      axios.get("https://workoutnowdev.herokuapp.com/workout", { params: { duration_filter: this.selected }}).then(response => (this.url = response.data.url,
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
