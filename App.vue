<template>
  <div id="app">
    <question-component :question="currentQuestion" @answer-submitted="handleAnswer"></question-component>
    <feedback-component :feedback="feedback"></feedback-component>
  </div>
</template>

<script>
import QuestionComponent from './components/QuestionComponent.vue';
import FeedbackComponent from './components/FeedbackComponent.vue';

export default {
  components: {
    QuestionComponent,
    FeedbackComponent
  },
  data() {
    return {
      currentQuestion: {},
      feedback: {
        show: false,
        correct: false,
        solution: ''
      },
      questions: [],
      currentDifficulty: 5 // Initial difficulty
    }
  },
  created() {
    fetch('questions.json')
      .then(response => response.json())
      .then(data => {
        this.questions = data;
        this.currentQuestion = this.getNextQuestion();
      });
  },
  methods: {
    getNextQuestion() {
      // Implement adaptive algorithm here
      // ...
      return this.questions[0]; // Placeholder
    },
    handleAnswer(userAnswer) {
      // Check the answer and update feedback
      // Adjust difficulty based on performance
      this.currentQuestion = this.getNextQuestion();
    }
  }
}
</script>
