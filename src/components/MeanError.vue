<template>
  <div class="row">
    <div class="col-sm-8 offset-sm-2 col-xs-12 col-md-6 offset-md-3 text-center">
      <h1>
        Your mean error is
        <span>
          <slot></slot>%
        </span>
      </h1>
    </div>
  </div>
</template>

<script>
</script>

<style scoped>
span {
  color: red;
}
</style>