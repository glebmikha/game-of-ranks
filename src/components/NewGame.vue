<template>
  <div class="row">
    <div class="col-sm-8 offset-sm-2 col-xs-12 col-md-6 offset-md-3 text-center">
      <button class="btn btn-success" @click="startNewGame">Start New Game</button>
    </div>
  </div>
</template>

<script>
const N_NUMBERS = 12;
const COEF = 120;

export default {
  data: function() {
    return {
      nNumbers: N_NUMBERS,
      coef: COEF
    };
  },
  methods: {
    startNewGame() {
      this.$emit("startNewGame", {
        nNumbers: this.nNumbers,
        coef: this.coef
      });
    }
  }
};
</script>