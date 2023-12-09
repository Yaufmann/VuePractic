<template>
  <div>
    <quiz-header
        :questionStatus="questionStatus"
        :barPercentage="barPercentage"
    />
    <div>
      <Question
          v-if="!showResults"
          :question="quiz.questions[currentQuestionIndex]"
          @selectOption="onOptionSelected"
      />
      <Result
          v-else
          :quizQuestionLength="quiz.questions.length"
          :numberOfCorrectAnswer="numberOfCorrectAnswer"
      />
    </div>
<!--    {{numberOfCorrectAnswer}}-->
<!--    <button @click="currentQuestionIndex++">Next Question</button>-->
  </div>
</template>

<script setup>
  import Question from "@/components/Question.vue";
  import QuizHeader from "@/components/QuizHeader.vue";
  import {useRoute} from "vue-router";
  import { ref, watch , computed } from "vue";
  import quizes from "../data/quizes.json";
  import Result from "@/components/Result.vue";

  const route = useRoute();
  const quizId = parseInt(route.params.id);
  const quiz = quizes.find(q => q.id === quizId);
  const currentQuestionIndex = ref(0);
  const numberOfCorrectAnswer = ref(0);
  const showResults = ref(false)

  const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
  const barPercentage = computed(() => `${currentQuestionIndex.value/quiz.questions.length * 100}%`)
  const onOptionSelected = (isCorrect) => {
    if(isCorrect) {
      numberOfCorrectAnswer.value++;
    }
    if(quiz.questions.length -1 === currentQuestionIndex.value) {
      showResults.value = true
    }
    currentQuestionIndex.value++
  }
</script>


