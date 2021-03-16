<template lang="pug">
.background
  img.background__img(src="./images/childblue.jpg")
  .ball
    .level__one(@mouseover="changeLevelOne()" :class="{active: levelOne}")
      .level__two(v-for="(item, i) in levelTwo" @mouseover="changeLevelTwo(i)" :class="{active: levelOne === levelTwo[i]}" :key="i")
        .level__three(v-for="(item, i2) in levelThree[i]" @mouseover="changeLevelThree(i,i2)" :class="{active: !levelTwo[i] || levelThree[i][i2]}" :key="i2")
          .level__four(v-for="(item, i3) in levelFour[i][i2]" @mouseover="changeLevelFour(i,i2,i3)" :class="{active: !levelThree[i][i2] || levelFour[i][i2][i3]}" :key="i3")
</template>
<script>
export default {
  name: 'imgball',

  data() {
    return {
      levelOne: false,
      levelTwo: [false, false, false, false],
      levelThree: [
        [false, false, false, false],
        [false, false, false, false], 
        [false, false, false, false], 
        [false, false, false, false]
      ],
      levelFour: [
        [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]],
        [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], 
        [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], 
        [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]]
      ],
    }
  },

  mounted () {
    document.body.style.margin = 0
  },

  methods: {
    changeLevelOne () {
      this.levelOne = true
    },
    changeLevelTwo (i) {
      this.levelTwo[i] = true
    },
    changeLevelThree (i, i2) {
      this.levelThree[i][i2] = true
    },
    changeLevelFour (i, i2, i3) {
      console.log(i, i2, i3)
      this.levelFour[i][i2][i3] = true
    },
  }
}
</script>
<style lang="scss" scoped>
  @import './style.scss';
</style>
