<template lang="pug">
.background
  img.background__img(src="./images/childblue.jpg")
  .ball
    .level__one(@mouseover="changeLevelOne()" :class="{active: levelOne}")
    .level__two__group
      .level__two(v-for="(item, i) in levelTwo" @mouseover="changeLevelTwo(i)" :class="{active: levelOne === levelTwo[i]}" :key="i")
    .level__three__group
      .three(v-for="(node, i) in levelThree" :class="{active: !levelOne || !levelTwo[i]}")
        .level__three(v-for="(item, i2) in node" @mouseover="changeLevelThree(i,i2)" :class="{active: levelThree[i][i2]}" :key="i2")
</template>
<script>
export default {
  name: 'imgball',

  data() {
    return {
      levelOne: false,
      levelTwo: [false, false, false, false],
      levelThree: [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]],
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
    changeLevelThree (i, i2) {
      console.log('levelThree')
      console.log(i)
      console.log(i2)
      this.levelThree[i][i2] = true
    },
  }
}
</script>
<style lang="scss" scoped>
  @import './style.scss';
</style>
