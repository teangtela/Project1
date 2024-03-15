<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";
const { quizQuestionLength, numberOfCorrectAnswer } = defineProps([
  "quizQuestionLength",
  "numberOfCorrectAnswer",
]);
</script>
<template>
  <div class="results">
    <p>Your Result ...</p>
    <h1>{{ numberOfCorrectAnswer }} / {{ quizQuestionLength }}</h1>
  </div>
  <div class="btn">
    <button><RouterLink to="/">Back</RouterLink></button>
  </div>
</template>
<style scoped>
.results {
  text-align: center;
  padding: 50px 0;
  width: 50%;
  background-color: rgb(63, 85, 63);
  margin: 50px auto;
  color: white;
  border-radius: 20px;
}
.btn {
  width: 20%;
  margin: 0 auto;
  text-align: center;
}
button {
  padding: 10px 20px;
  cursor: pointer;
  background-color: red;
  border: none;
  border-radius: 5px;
  text-decoration: none;
}
p {
  font-size: 40px;
  font-family: sans-serif;
}
h1 {
  font-size: 90px;
}
</style>
