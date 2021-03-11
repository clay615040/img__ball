<template lang="pug">
.background
  img.background__img(src="./images/childblue.jpg")
  .ball
    .level__one(@mouseover="changeLevelOne()" :class="{active: levelOne}")
    .level__two__group
      .level__two(v-for="(item, i) in levelTwo" @mouseover="changeLevelTwo(i)" :class="{active: levelOne === levelTwo[i]}" :key="i")
    //- .level__three(v-for="(item, i) in 4" @mouseover="changeLevelThree()" :key="i")
      //- .level__four(v-for="(item, i) in 4" @mouseover="changeLevelFour()" :key="i")
</template>
<script>
export default {
  name: 'imgball',

  data() {
    return {
      levelOne: false,
      levelTwo: [false, false, false, false],
      // levelThree: [[0, 0, 0, 0],[0, 0, 0, 0],[0, 0, 0, 0],[0, 0, 0, 0]],
    }
  },

  mounted () {
    document.body.style.margin = 0
  },

  methods: {
    changeLevelOne () {
      console.log('levelOne')
      this.levelOne = true
    },
    changeLevelTwo (i) {
      console.log('levelTwo')
      console.log(i)
      this.levelTwo[i] = true
    },
  }
}
</script>
<style lang="scss" scoped>
  @import './style.scss';
</style>
