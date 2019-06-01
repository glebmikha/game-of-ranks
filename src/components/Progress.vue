<template>
  <div class="row">
    <div class="col-sm-12">
      <!-- <h3>Game Of Ranks</h3> -->
      <div class="progress">
        <div
          class="progress-bar"
          role="progressbar"
          :style="{width: (numberCount / maxNumbers) * 100 + '%'}"
          aria-valuenow="25"
          aria-valuemin="0"
          aria-valuemax="100"
        >{{ numberCount }} / {{ maxNumbers}}</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ["numberCount", "maxNumbers"]
};
</script>