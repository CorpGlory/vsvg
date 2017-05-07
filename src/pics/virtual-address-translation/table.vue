<template>
  <g :transform="`translate(${x}, ${y})`">

    <line
      v-for="col in ccols"
      x1="0" :x2="width"
      :y1="col.y" :y2="col.y"
    />

    <eti
      v-for="hole in holes"
      :width="width"
      :x="0.5" :y="hole"
    />

    <curvyArrow
      v-if="shift"
      :x1="width + 2"
      :x2="width + 2"
      :y1="0"
      :y2="shiftY2"
      :strokeWidth="0.9"
      :corner="true"
      orientation="rr"
    />

    <rect
      x="0" y="0"
      :width="width"
      :height="height"
      fill="none"
    />

  </g>

</template>

<script>

const _ = require('lodash');

const LINE_H = 10;

export default {
  props: {
    cols: { type: Number, required: true },
    x: { type: Number, required: true },
    y: { type: Number, required: true },
    shift: { type: Number, default: 0 },
    width: { type: Number, default: 100 },
    filled: { type: [String, Array], default: '' }
  },
  components: {
    eti: require('./emptyTableItem')
  },
  computed: {
    height: function() {
      return this.cols * LINE_H;
    },
    ccols: function() {
      var filled = this.filled;
      return _.map(Array(this.cols - 1), (e,i) => ({
        y: (i + 1) * LINE_H,
        hole: !~filled.indexOf(i + '')
      }));
    },
    holes: function() {
      var fls = typeof this.filled === 'string' ?
        this.filled.split('').map(e=>+e) :
        this.filled
      return _(_.range(this.cols))
        .difference(fls)
        .map(e => e * LINE_H)
        .value()
    },
    shiftY2: function() {
      return this.shift * LINE_H;
    }
  },
  methods: { }
}
</script>


<style lang='scss' scoped>

</style>
