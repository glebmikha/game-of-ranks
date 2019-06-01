<template>
  <div class="container">
    <app-header :numberCount="7" :maxNumbers="12"></app-header>
    <average-error></average-error>
    <app-footer></app-footer>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Footer from "./components/Footer.vue";
import AverageError from "./components/AverageError.vue";
export default {
  components: {
    appHeader: Header,
    appFooter: Footer,
    averageError: AverageError
  }
};
</script>

<style>
</style>
