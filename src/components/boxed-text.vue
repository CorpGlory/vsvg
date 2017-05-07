<template>
  <g :transform='translate'>
    <rect
      class='background'
      width="160"
      height="25"
      rx="1"
      ry="1"
    ></rect>
    <g v-for="letter in letters">
      <text
        :x="letter.x + 10"
        y="18"
        class="monofont"
      >
        {{ letter.value }}
      </text>
      <line v-if="letter.i != 0"
        y1="0" y2="25"
        :x1="letter.x"
        :x2="letter.x"
        :class="(letter.i % 4 == 0) ? 'bigSeparator': 'separator'"
      />
    </g>

  </g>
</template>

<script>
export default {
  props: {
    x: { type: Number, default: 0 },
    y: { type: Number, default: 0 },
    value: { type: String }
  },
  computed: {
    translate: function() {
      return `translate(${this.x}, ${this.y})`
    },
    letters: function() {
      return this.value.split('').map((d, i) => ({
        value: d,
        i: i,
        x: i * 20
      }));
    }
  }

}
</script>

<style lang='scss' scoped>
text {
  font-size: 18px;
  text-anchor: middle;
}
.separator {
  stroke-width: 0.5;
}
.bigSeparator {
  stroke-width: 1;
}
.background {
  fill: none;
  stroke-width:1;
}
</style>
