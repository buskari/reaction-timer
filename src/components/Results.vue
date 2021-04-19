<template>
  <p>Reaction Time: {{ score }} ms</p>
  <p class="rank"> {{ rank }} </p>
</template>

<script>
export default {
  props: ['showResults', 'score'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if (this.score < 300) {
      this.rank = 'WOW! That was realy fast!'
    } else if (this.score <= 330) {
      this.rank = 'Its fast!'
    } else if (this.score <= 400) {
      this.rank = 'Normal speed!'
    } else if (this.score <= 450) {
      this.rank = 'You can do better!'
    } else {
      this.rank = 'WTF! Are you drunk??'
    }
  }
}
</script>

<style>
  .rank { 
    font-size: 1.4rem;
    color: #014d13;
    font-weight: bold;
  }
</style>