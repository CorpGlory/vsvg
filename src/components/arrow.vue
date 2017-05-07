<template>
  <g>
    <defs>
      <arrowEnd />
    </defs>
    <line
      :x1="cx1"
      :y1="cy1"
      :x2="cx2"
      :y2="cy2"
      :stroke-width="strokeWidth"
      marker-end="url(#arrow-end)"
      markerUnits="10"
      :stroke-dasharray="dashArray"
    />
  </g>
</template>

<script>
const markerLength = 21;
export default {
  props: {
    x1: { type: Number, required: true },
    y1: { type: Number, required: true },
    x2: { type: Number, required: true },
    y2: { type: Number, required: true },
    isDashed: { type: Boolean, default: false },
    strokeWidth: { type: Number, default: 2 }
  },
  components: {
    arrowEnd: require('./arrow-end')
  },
  computed: {
    cx1: function() {
      return this.x1;
    },
    cy1: function() {
      return this.y1;
    },
    cx2: function() {
      return this.x2 - this.ev[0] * markerLength
    },
    cy2: function() {
      return this.y2 - this.ev[1] * markerLength;
    },
    ev: function () {
      var v = [this.x2 - this.x1, this.y2 - this.y1];
      var l = Math.sqrt(v[0] * v[0] + v[1] * v[1]);
      return [
        v[0] / l, v[1] / l
      ];
    },
    dashArray: function() {
      if(this.isDashed) {
        return '5, 5'
      } else {
        return '0'
      }
    },
  }
}
</script>
