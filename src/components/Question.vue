<template>
  <div class="row">
    <div class="col-sm-8 offset-sm-2 col-xs-12 col-md-6 offset-md-3 text-center">
      <h1>
        Find element with rank
        <span>{{ qRank }}</span>
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  props: ["qRank"]
};
</script>

<style scoped>
span {
  color: green;
}
</style>