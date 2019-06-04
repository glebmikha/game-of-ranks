<template>
  <div class="row">
    <div class="col-sm-8 offset-sm-2 col-xs-12 col-md-6 offset-md-3 text-center">
      <h3>
        Correct answers:
        <span>
          <slot></slot>
        </span>
      </h3>
    </div>
  </div>
</template>

<script>
</script>

<style scoped>
span {
  color: blue;
}
</style>