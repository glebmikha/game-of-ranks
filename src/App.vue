<template>
  <div class="container">
    <app-header class="spacer"></app-header>
    <new-game class="spacer" @startNewGame="newGame"></new-game>
    <app-progress :numberCount="7" :maxNumbers="12" class="spacer"></app-progress>
    <question :qRank="3" class="spacer"></question>
    <number-grid
      :numbers="numbers"
      :clicked="clicked_status"
      @numberClicked="clickNumber"
      class="spacer"
    ></number-grid>
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
      numbers: "",
      clicked_status: "",
      numbers_param: "",
      clicked_index: [],
      clicked_element: [],
      error_log: [],
      sortedNumbers: "",
      remainingSorterNumber: ""
    };
  },
  methods: {
    newGame(numbers_param) {
      this.numbers_param = numbers_param;
      this.generateNumbers();
      this.createSortedNumbers();
    },
    generateNumbers() {
      this.numbers = Array.from({ length: this.numbers_param.n_numbers }, () =>
        Math.floor(Math.random() * this.numbers_param.coef)
      );
      this.clicked_status = Array(this.numbers_param.n_numbers).fill(false);
    },
    clickNumber(index) {
      if (!this.clicked_index.includes(index)) {
        this.clicked_index.push(index);
        this.clicked_element.push(this.numbers[index]);
      }
    },
    createSortedNumbers() {
      this.sortedNumbers = [...this.numbers];
      this.sortedNumbers.sort((a, b) => a - b);
      this.remainingSorterNumber = [...this.sortedNumbers];
    }
  }
};
</script>

<style>
.spacer {
  margin-top: 1rem;
}
</style>
