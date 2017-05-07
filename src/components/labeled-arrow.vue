<template>
  <g>
    <arrow
      :x1="anchors[2].x" :y1="anchors[2].y"
      :x2="anchors[3].x" :y2="anchors[3].y"
    />

    <line
      :x1="anchors[0].x" :y1="anchors[0].y"
      :x2="anchors[1].x" :y2="anchors[1].y"
    />

    <g :transform="slotTransform">
      <slot />
    </g>
  </g>
</template>

<script>
const markerLength = 19;
const gapLength = 25;
export default {
  props: [
    // TODO: make it nums
    'x1', 'y1', 'x2', 'y2'
  ],
  data: function() {
    return {
      // it is not computed cuz
      // we need to know slot params later
      slotTransform: ''
    }
  },
  mounted: function() {
    var slot = this.$slots.default[0].elm;
    var sbb = slot.getBBox();
    var mx = this.mx;
    var my = this.my;
    mx -= sbb.x;
    mx -= sbb.width / 2;
    my -= sbb.y;
    my -= sbb.height / 2;
    this.slotTransform = `translate(${mx}, ${my})`;
  },
  computed: {
    mx: function() {
      return (+this.x1 + +this.x2) / 2;
    },
    my: function() {
      return (+this.y1 + +this.y2) / 2;
    },
    anchors: function() {
      return [
        {
          x: +this.x1,
          y: +this.y1
        },
        {
          x: +this.mx - this.ev.x * gapLength / 2,
          y: +this.my - this.ev.y * gapLength / 2
        },
        {
          x: this.mx + this.ev.x * gapLength / 2,
          y: this.my + this.ev.y * gapLength / 2
        },
        {
          x: +this.x2,
          y: +this.y2
        }
      ];
    },
    ev: function () {
      var v = [this.x2 - this.x1, this.y2 - this.y1];
      var l = Math.sqrt(v[0] * v[0] + v[1] * v[1]);
      return {
        x: v[0] / l,
        y: v[1] / l
      };
    }
  }
}
</script>

<style lang='scss' scoped>
line {
  stroke-width: 2;
}
</style>
