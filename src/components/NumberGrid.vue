<template>
  <div class="row">
    <app-number
      v-for="(number, index) in numbers"
      :key="index"
      :numStyle="numStyles[index]"
      @click.native="clickNumber($event, index)"
    >{{ number }}</app-number>
  </div>
</template>

<script>
import Number from "./Number.vue";

export default {
  props: ["numbers", "numStyles"],
  components: {
    appNumber: Number
  },
  methods: {
    clickNumber($event, index) {
      this.$emit("numberClicked", index);
    }
  }
};
</script>

<style>
</style>