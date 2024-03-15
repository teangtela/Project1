<script setup>
import { defineProps } from "vue";
const { questionStatus, barPercentage } = defineProps([
  "questionStatus",
  "barPercentage",
]);
</script>

<template>
  <header>
    <h4>Question {{ questionStatus }}</h4>
    <div class="bar">
      <div class="completion" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>
<style scoped>
header {
  text-align: center;
  color: white;
}
.bar {
  width: 300px;
  height: 30px;
  border: 1px solid greenyellow;
  margin: 10px auto;
}
.completion {
  height: 100%;
  width: 0%;
  background-color: greenyellow;
}
</style>
