<template>
  <g>
    <defs>
      <arrowEnd />
    </defs>
    <line
      :x1="cx1"
      :y1="cy1 - 2"
      :x2="cx2"
      :y2="cy2 - 2"
      stroke-width="2"

    />

    <line
      :x1="cx1"
      :y1="cy1"
      :x2="cx2"
      :y2="cy2"
      stroke-width="2"
      marker-end="url(#arrow-end)"
      marker-start="url(#arrow-end)"
      style="stroke: none"
    />

    <line
      :x1="cx1"
      :y1="cy1 + 2"
      :x2="cx2"
      :y2="cy2 + 2"
      stroke-width="2"
    />
  </g>
</template>

<script>
const markerLength = 22;
export default {
  props: [
    'x1', 'y1', 'x2', 'y2'
  ],
  components: {
    arrowEnd: require('./arrow-end')
  },
  computed: {
    cx1: function() {
      return +this.x1 + this.ev[0] * markerLength;
    },
    cy1: function() {
      return +this.y1 + this.ev[1] * markerLength;
    },
    cx2: function() {
      return +this.x2 - this.ev[0] * markerLength
    },
    cy2: function() {
      return +this.y2 - this.ev[1] * markerLength;
    },
    ev: function () {
      var v = [this.x2 - this.x1, this.y2 - this.y1];
      var l = Math.sqrt(v[0] * v[0] + v[1] * v[1]);
      return [
        v[0] / l, v[1] / l
      ];
    }
  }
}
</script>

<style lang='scss' scoped>
.background {
  fill: none;
  stroke-width: 1;
}
</style>
