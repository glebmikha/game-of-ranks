<template>
  <div class="row">
    <app-number
      v-for="(number, index) in numbers"
      :key="index"
      @click.native="deleteNumber($event, index)"
    >{{ number }}</app-number>
  </div>
</template>

<script>
import Number from "./Number.vue";

export default {
  props: ["numbers"],
  components: {
    appNumber: Number
  },
  methods: {
    deleteNumber($event, index) {
      this.$emit("numberDeleted", index);
    }
  }
};
</script>

<style>
</style>