<template>
  <div class="col col-sm-1 col-md-3 col-lg-1 col-xs-3" @click="hit=true">
    <div class="card card-default text-center" :class="{pushed:hit}">
      <div class="card-body number">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      hit: false
    };
  }
};
</script>

<style>
.number {
  cursor: pointer;
}

.number:hover {
  background-color: #d3e4ff;
}

.pushed {
  background-color: #e5e6e8;
}
</style>