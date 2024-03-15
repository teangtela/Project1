<script setup>
import { defineProps, defineEmits } from "vue";
const emit = defineEmits(["selectOption"]);
const { question } = defineProps(["question"]);
const emitSelectedOption = (isCorrect) => {
  emit("selectOption", isCorrect);
};
</script>
<template>
  <div class="question-container">
    <h1 class="question">
      {{ question.text }}
    </h1>
  </div>
  <div class="options-container">
    <div
      v-for="option in question.options"
      :key="option.id"
      class="option"
      @click="emitSelectedOption(option.isCorrect)"
    >
      <p class="option-label">
        {{ option.label }}
      </p>
      <div class="option-value">
        {{ option.text }}
      </div>
    </div>
  </div>
</template>
<style scoped>
.question {
  color: white;
  font-size: 25px;
  margin: 30px 20px;
}
.option {
  margin-top: 10px;
  margin-left: 10px;
  display: flex;
  gap: 10px;
  color: white;
  cursor: pointer;
  width: 35%;
  height: 40px;
  align-items: center;
  background-color: rgb(92, 186, 249);
  border-radius: 5px;
}

.option-label {
  height: 100%;
  background-color: white;
  padding: 0 10px;
  color: red;
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
  display: flex;
  align-items: center;
}
</style>
