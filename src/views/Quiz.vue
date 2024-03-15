<script setup>
import Question from "../components/Question.vue";
import QuizHeader from "../components/QuizHeader.vue";
import { useRoute } from "vue-router";
import { ref, computed } from "vue";
import quizes from "../data/data.json";
import Result from "@/components/Result.vue";
const currentQuestionIndex = ref(0);
const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizes.find((q) => q.id === quizId);
// const questionStatus = ref(
//   `${currentQuestionIndex.value}/${quiz.questions.length}`
// );
// watch(
//   () => currentQuestionIndex.value,
//   () => {
//     questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`;
//   }
// );
const questionStatus = computed(() => {
  return `${currentQuestionIndex.value}/${quiz.questions.length}`;
});
const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
);
const numberOfCorrectAnswer = ref(0);
const showResult = ref(false);
const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswer.value++;
  }
  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResult.value = true;
  }
  currentQuestionIndex.value++;
};
</script>

<template>
  <div class="template">
    <QuizHeader
      :questionStatus="questionStatus"
      :barPercentage="barPercentage"
    />
    <div>
      <Question
        v-if="!showResult"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
      <Result
        v-else
        :quizQuestionLength="quiz.questions.length"
        :numberOfCorrectAnswer="numberOfCorrectAnswer"
      />
    </div>
  </div>
</template>
<style scoped>
.template {
  width: 80%;
  margin: 100px auto;
  padding: 30px;
  border-radius: 10px;
  background-color: rgb(6, 21, 75);
}
button {
  margin-top: 30px;
  margin-left: 10px;
  padding: 10px;
  background-color: rgb(141, 224, 141);
  border-radius: 2px;
  border: none;
  cursor: pointer;
}
</style>
