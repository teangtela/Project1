<script setup>
import { defineProps } from "vue";
import { useRouter } from "vue-router";
const { lomhat } = defineProps(["lomhat"]);
const router = useRouter();
const navigateToQuiz = () => {
  router.push(`/quiz/${lomhat.id}`);
};
</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="lomhat.img" alt="" />
    <div class="card-text">
      <h2>{{ lomhat.name }}</h2>
      <p>{{ lomhat.questions.length }} questions</p>
    </div>
  </div>
</template>
<style scoped>
.card {
  width: 100%;
  color: black;
  cursor: pointer;
  border-radius: 5px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
.card img {
  width: 100%;
  border-radius: 5px;
  height: 150px;
}
.card-text {
  padding: 5px;
  font-size: 15px;
}
</style>
