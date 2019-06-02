<template>
  <div class="container">
    <app-header class="spacer"></app-header>
    <new-game class="spacer"></new-game>
    <app-progress :numberCount="7" :maxNumbers="12" class="spacer"></app-progress>
    <question :qRank="3" class="spacer"></question>
    <number-grid :numbers="numbers" class="spacer"></number-grid>
    <average-error class="spacer">14</average-error>
    <error-detail class="spacer"></error-detail>
    <app-footer class="spacer"></app-footer>
  </div>
</template>

<script>
import Footer from "./components/Footer.vue";
import AverageError from "./components/AverageError.vue";
import NumberGrid from "./components/NumberGrid.vue";
import Question from "./components/Question.vue";
import ErrorDetail from "./components/ErrorDetail.vue";
import Progress from "./components/Progress.vue";
import NewGame from "./components/NewGame.vue";
import Header from "./components/Header.vue";

export default {
  components: {
    appProgress: Progress,
    appFooter: Footer,
    averageError: AverageError,
    numberGrid: NumberGrid,
    question: Question,
    errorDetail: ErrorDetail,
    newGame: NewGame,
    appHeader: Header
  },
  data: function() {
    return {
      numbers: [
        1,
        2,
        3,
        4,
        5,
        6,
        7,
        8,
        123,
        1100,
        11,
        12,
        1,
        2,
        9999,
        4,
        97087,
        6,
        7,
        8,
        123,
        1100,
        11,
        12
      ]
    };
  }
};
</script>

<style>
.spacer {
  margin-top: 1rem;
}
</style>
