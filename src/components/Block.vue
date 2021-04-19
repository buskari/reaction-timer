<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    CLICK ME
  </div>
</template>

<script>
export default {
  props: ['delay'],
  emits: ['end'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit('end', this.reactionTime);
    }
  }
}
</script>

<style>
  html {
    font-family: Arial, Helvetica, sans-serifs;
  }
  .block {
    box-sizing: border-box;
    width: 400px;
    border-radius: 20px;
    background: #014d13;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
    font-size: 1.5rem;
  }
</style>