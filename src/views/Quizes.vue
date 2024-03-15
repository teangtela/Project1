<script setup>
import q from "../data/data.json";
import { ref, watch } from "vue";
import Card from "../components/card.vue";
const quizes = ref(q);
const search = ref("");
watch(search, () => {
  quizes.value = q.filter((quiz) =>
    quiz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>
<template>
  <div>
    <header>
      <h1>Subject</h1>

      <input v-model.trim="search" type="text" placeholder="search ..." />
    </header>
    <div class="option-container">
      <Card v-for="quiz in quizes" :key="quiz.id" :lomhat="quiz" />
      <!-- :lomhat="quiz" jg ban ney tha yg jg ban data bos quiz tv brer 
      nv knong components card so jing define data dal mean nv knong quiz tv knong lomhat-->

      <!-- <div v-for="quiz in quizes" :key="quiz.id" class="card">
        <img :src="quiz.img" alt="" />
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} questions</p>
        </div>
      </div> -->
    </div>
  </div>
</template>

<style scoped>
header {
  margin-top: 10px;
  margin-bottom: 30px;
  display: flex;
  align-items: center;
}
header h1 {
  font-weight: bold;
  margin-right: 30px;
  color: black;
  font-size: 40px;
}
header input {
  border: none;
  background-color: rgb(147, 145, 145);
  padding: 10px;
  border-radius: 4px;
  width: 200px;
  outline: none;
}
::placeholder {
  color: white;
}
.option-container {
  margin-top: 50px;
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}
</style>
