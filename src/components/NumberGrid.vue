<template>
  <div class="row">
    <app-number
      v-for="(number, index) in numbers"
      :key="index"
      :clicked="clicked[index]"
      @click.native="clickNumber($event, index)"
    >{{ number }}</app-number>
  </div>
</template>

<script>
import Number from "./Number.vue";

export default {
  props: ["numbers", "clicked"],
  components: {
    appNumber: Number
  },
  methods: {
    clickNumber($event, index) {
      this.$set(this.clicked, index, true);
      this.$emit("numberDeleted", index);
    }
  }
};
</script>

<style>
</style>