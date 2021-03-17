<template lang="pug">
.background
  img.background__img(src="./images/childblue.jpg")
  .ball
    .extremely(@mouseover="changeLevelOne()" :class="{active: levelOne}")
      .ball__bg(v-for="(item, i) in levelTwo" @mouseover="changeLevelTwo(i)" :class="{active: levelOne === levelTwo[i]}" :key="i")
        .ball__bg(v-for="(item, i2) in levelThree[i]" @mouseover="changeLevelThree(i,i2)" :class="{active: !levelTwo[i] || levelThree[i][i2]}" :key="i2")
          .ball__bg(v-for="(item, i3) in levelFour[i][i2]" @mouseover="changeLevelFour(i,i2,i3)" :class="{active: !levelThree[i][i2] || levelFour[i][i2][i3]}" :key="i3")
            .ball__bg(v-for="(item, i4) in levelFive[i][i2][i3]" @mouseover="changeLevelFive(i,i2,i3,i4)" :class="{active: !levelFour[i][i2][i3] || levelFive[i][i2][i3][i4]}" :key="i4")
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
      levelFive: [
        [[[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]]],
        [[[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]]], 
        [[[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]]], 
        [[[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]], [[false, false, false, false], [false, false, false, false], [false, false, false, false], [false, false, false, false]]]
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
      this.levelFour[i][i2][i3] = true
    },
    changeLevelFive (i, i2, i3, i4) {
      this.levelFive[i][i2][i3][i4] = true
    },
  }
}
</script>
<style lang="scss" scoped>
  @import './style.scss';
</style>
