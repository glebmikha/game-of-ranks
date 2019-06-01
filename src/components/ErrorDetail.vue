<template>
  <table class="table">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">Delta</th>
        <th scope="col">Error</th>
        <th scope="col">Expected Rank</th>
        <th scope="col">Expected Number</th>
        <th scope="col">Recieved Rank</th>
        <th scope="col">Recieved Element</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(error,index) in errorDetail" :key="index">
        <th scope="row">{{ index + 1}}</th>
        <td>{{error.delta}}</td>
        <td>{{error.error}}%</td>
        <td>{{error.qRank + 1}}</td>
        <td>{{error.qElement}}</td>
        <td>{{error.aRank + 1}}</td>
        <td>{{error.aElement}}</td>
      </tr>
    </tbody>
  </table>
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