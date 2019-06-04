<template>
  <div class="row">
    <div class="col-sm-8 offset-sm-2 col-xs-12 col-md-6 offset-md-3 text-center">
      <button class="btn btn-success" @click="startNewGame">Start New Game</button>
    </div>

    <div class="col-sm-8 offset-sm-2 col-xs-12 col-md-6 offset-md-3 text-center mt-3">
      <label for="male">
        <input type="radio" id="easy" value="12" v-model="difficulty"> Easy
      </label>
      <label for="female">
        <input type="radio" id="medium" value="24" v-model="difficulty"> Medium
      </label>
      <label for="female">
        <input type="radio" id="hard" value="36" v-model="difficulty"> Hard
      </label>
    </div>
  </div>
</template>

<script>
const COEF = 120;

export default {
  data: function() {
    return {
      coef: COEF,
      difficulty: 12
    };
  },
  methods: {
    startNewGame() {
      this.$emit("startNewGame", {
        nNumbers: this.difficulty,
        coef: this.coef
      });
    }
  }
};
</script>
<style>
label {
  margin-right: 1rem;
}
</style>