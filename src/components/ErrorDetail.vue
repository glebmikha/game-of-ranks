<template>
  <div class="table-responsive">
    <table class="table table-sm">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Absolute Error</th>
          <th scope="col">Relative Error</th>
          <th scope="col">Expected Rank</th>
          <th scope="col">Expected Number</th>
          <th scope="col">Recieved Rank</th>
          <th scope="col">Recieved Element</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(error,index) in errorDetail" :key="index">
          <th scope="row">{{ index + 1}}</th>
          <td>{{error.absoluteError}}</td>
          <td>{{error.relativeError.toFixed(0)}}%</td>
          <td>{{error.qRank + 1}}</td>
          <td>{{error.qElement}}</td>
          <td>{{error.aRank + 1}}</td>
          <td>{{error.aElement}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: ["errorDetail"]
};
</script>

<style scoped>
span {
  color: red;
}
</style>