<template>
  <div class="col-2 col-lg-1 p-1 p-xl-1 m-0 spacer">
    <div class="card number">
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
  data: function() {
    return {
      hit: false
    };
  }
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

.pushed {
  background-color: #e5e6e8;
}

.card-text {
  font-size: 100%;
  white-space: nowrap;
}
</style>