<template>
  <div class="col-2 col-lg-1 p-1 p-xl-1 m-0 spacer">
    <div class="card number" :class="{ dimmed: clicked }">
      <div class="card-body text-center text-xs-left p-1">
        <p class="card-text">
          <slot></slot>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["clicked"]
};
</script>

<style scoped>
.number {
  cursor: pointer;
}

.spacer {
  margin-top: 1rem;
}

.number:hover {
  background-color: #d3e4ff;
}

.dimmed {
  background-color: #e5e6e8;
}

.card-text {
  font-size: 100%;
  white-space: nowrap;
}
</style>