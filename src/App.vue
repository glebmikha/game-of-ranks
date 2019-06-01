<template>
  <div class="container">
    <app-header :numberCount="7" :maxNumbers="12"></app-header>
    <average-error>14</average-error>
    <number-grid :numbers="numbers"></number-grid>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import AverageError from "./components/AverageError.vue";
import NumberGrid from "./components/NumberGrid.vue";
export default {
  components: {
    appHeader: Header,
    appFooter: Footer,
    averageError: AverageError,
    numberGrid: NumberGrid
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
