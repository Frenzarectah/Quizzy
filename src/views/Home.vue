<script setup>
import questions from '../data/data.json';
import { RouterLink } from 'vue-router';
import Card from '../components/Card.vue';
import { ref,watch } from "vue"

const quizzes = ref(questions);
const search = ref("")

watch(search, () =>{
 quizzes.value = questions.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})
</script>

<template>
<div class="container">
    <header>
      <h1>Quizzy</h1>
    <input  v-model.trim="search" type="text" placeholder="Search...">
    </header>
  <div class="options-container">
  <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz"/> -->
  </div>
  </div>
</template>
<style scoped>
  .container{
    max-width: 1000px;
    margin: 0 auto;
    
  }
  header{
    margin-bottom: 10px;
    margin-top: 30px;
    display: flex;
    align-items: center;
  }
  header h1{
    font-weight: bold;
    margin-right:30px;
  }
  header input{
    border: none;
    background-color: rgba(128,128,128,0.1);
    padding: 10px;
    border-radius: 5px;
  }
  .options-container{
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    margin-top: 40px;
  }

</style>