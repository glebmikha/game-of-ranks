<template>
  <div class="container">
    <app-header :numberCount="7" :maxNumbers="12"></app-header>
    <question :qRank="3"></question>
    <number-grid :numbers="numbers"></number-grid>
    <average-error>14</average-error>
    <error-detail></error-detail>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import AverageError from "./components/AverageError.vue";
import NumberGrid from "./components/NumberGrid.vue";
import Question from "./components/Question.vue";
import ErrorDetail from "./components/ErrorDetail.vue";

export default {
  components: {
    appHeader: Header,
    appFooter: Footer,
    averageError: AverageError,
    numberGrid: NumberGrid,
    question: Question,
    errorDetail: ErrorDetail
  },
  data: function() {
    return {
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
    };
  }
};
</script>

<style>
</style>
