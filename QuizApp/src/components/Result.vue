<template>
  <div class="results">
    <p>Your Results...</p>
    <h1>
      {{numberOfCorrectAnswer}}/{{quizQuestionLength}}
    </h1>
    <RouterLink class="resul" to="/">Go Back</RouterLink>
  </div>
</template>

<script setup>
 import {defineProps} from "vue"
 import {RouterLink} from "vue-router";

 const {numberOfCorrectAnswer,quizQuestionLength} = defineProps(['numberOfCorrectAnswer','quizQuestionLength'])
</script>

<style scoped>
   .results {
     text-align: center;
     padding: 100px 0;
   }

   p {
     font-size: 25px;
   }

   h1 {
     font-size: 25px;
     margin-bottom: 10px;
   }
   .resul {
     color: white;
     text-decoration: none;
     font-size: 20px;
     border: 1px solid burlywood;
     border-radius: 15px;
     background-color: burlywood;
     box-shadow: 1px 3px 1px black;
     padding: 10px;
   }

</style>