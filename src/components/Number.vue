<template>
  <div class="col-2 col-lg-1 p-1 p-xl-1 m-0 spacer">
    <div
      class="card"
      :class="{ error: numStyle === 'ERROR', success: numStyle === 'OK', number: numStyle === 'UNCLICKED' }"
    >
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
  props: ["numStyle"]
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

.card-text {
  font-size: 100%;
  white-space: nowrap;
}

.error {
  background-color: lightcoral;
}

.success {
  background-color: lightgreen;
}

.error:hover {
  cursor: default;
}

.success:hover {
  cursor: default;
}
</style>