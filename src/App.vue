<template>
  <div class="container">
    <app-header class="spacer"></app-header>
    <new-game class="spacer" @startNewGame="newGame"></new-game>
    <app-progress :numberCount="clickedIndexes.length" :maxNumbers="numbers.length" class="spacer"></app-progress>
    <question :qRank="qRank + 1" class="spacer" v-if="remainingSortedNumbers.length > 0"></question>
    <number-grid
      :numbers="numbers"
      :clicked="clickedStatuses"
      @numberClicked="clickNumber"
      class="spacer"
    ></number-grid>
    <mean-error class="spacer">{{curMeanRelativeError}}</mean-error>
    <error-detail class="spacer" :errorDetail="errorLog" :nClicked="clickedIndexes.length"></error-detail>
    <app-footer class="spacer"></app-footer>
  </div>
</template>

<script>
import Footer from "./components/Footer.vue";
import MeanError from "./components/MeanError.vue";
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
    meanError: MeanError,
    numberGrid: NumberGrid,
    question: Question,
    errorDetail: ErrorDetail,
    newGame: NewGame,
    appHeader: Header
  },
  data: function() {
    return {
      numbersParams: "",
      numbers: [],
      sortedNumbers: "",
      remainingSortedNumbers: [],
      clickedStatuses: "",
      clickedIndexes: [],
      qElement: "",
      qRank: "",
      aElement: "",
      aRank: "",
      errorLog: [],
      curMeanRelativeError: 0,
      curRelativeError: 0
    };
  },
  methods: {
    newGame(numbersParams) {
      this.numbersParams = numbersParams;
      this.clickedIndexes = [];
      this.errorLog = [];
      this.generateNumbers();
      this.createSortedNumbers();
      this.nextQuestion();
    },
    generateNumbers() {
      this.numbers = [];
      while (this.numbers.length < this.numbersParams.nNumbers) {
        var r = Math.floor(Math.random() * this.numbersParams.coef) + 1;
        // take only unique
        if (this.numbers.indexOf(r) === -1) this.numbers.push(r);
      }
      this.clickedStatuses = Array(this.numbersParams.nNumbers).fill(false);
    },
    clickNumber(index) {
      if (!this.clickedIndexes.includes(index)) {
        // get user answer
        this.aElement = this.numbers[index];
        this.aRank = this.sortedNumbers.indexOf(this.aElement);

        this.clickedIndexes.push(index);

        // calculate errors

        this.curRelativeError =
          (Math.abs(this.qRank - this.aRank) * 100) / this.sortedNumbers.length;

        let logLine = {
          absoluteError: this.qRank - this.aRank,
          relativeError: this.curRelativeError,
          qRank: this.qRank,
          qElement: this.qElement,
          aRank: this.aRank,
          aElement: this.aElement
        };

        this.errorLog.unshift(logLine);

        // get current mean relative error
        let errors = this.errorLog.map(a => a.relativeError);
        const average = arr => arr.reduce((p, c) => p + c, 0) / arr.length;
        this.curMeanRelativeError = average(errors).toFixed(0);

        // delete element from sorted numbers
        var i = this.remainingSortedNumbers.indexOf(this.aElement);
        if (i !== -1) this.remainingSortedNumbers.splice(i, 1);

        this.nextQuestion();
      }
    },
    createSortedNumbers() {
      this.sortedNumbers = [...this.numbers];
      this.sortedNumbers.sort((a, b) => a - b);
      this.remainingSortedNumbers = [...this.sortedNumbers];
    },
    nextQuestion() {
      this.qElement = this.remainingSortedNumbers[
        Math.floor(Math.random() * this.remainingSortedNumbers.length)
      ];

      this.qRank = this.sortedNumbers.indexOf(this.qElement);
    }
  }
};
</script>

<style>
.spacer {
  margin-top: 1rem;
}
</style>
