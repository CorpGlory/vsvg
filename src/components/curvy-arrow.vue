<template>
  <g>
    <defs>
      <marker
        id="carrow-end-r"
        markerWidth="20"
        markerHeight="20"
        refX="10"
        refY="4"
        orient="auto"
        markerUnits="strokeWidth"
      >
        <g transform="scale(-1,1) translate(-10,0)">
          <arrowEndPath />
        </g>
      </marker>

      <marker
        id="carrow-end-t"
        markerWidth="20"
        markerHeight="20"
        refX="10"
        refY="4"
        orient="auto"
        markerUnits="strokeWidth"
      >
        <g transform="translate(14,0) rotate(90)">
          <arrowEndPath />
        </g>
      </marker>

      <marker
        id="carrow-end-l"
        markerWidth="10"
        markerHeight="10"
        refX="0"
        refY="4"
        orient="auto"
        markerUnits="strokeWidth"
      >
      <!-- <g transform="translate(10,0) scale(-1,1)"> -->
        <arrowEndPath />
      <!-- </g> -->
      </marker>

    </defs>
    <path
      class="linePath"
      fill="none"
      :d="d"
      :stroke-width="strokeWidth"
      :marker-end="`url(#${marker})`"
      :stroke-dasharray="dashArray"
    />
  </g>
</template>

<script>
const markerLength = 19;
const d3 = require('d3');
export default {
  props: {
    x1: { type: Number, required: true },
    y1: { type: Number, required: true },
    x2: { type: Number, required: true },
    y2: { type: Number, required: true },
    isDashed: { type: Boolean, default: false },
    orientation: { type: String, default: 'rl' },
    strokeWidth: { type: Number, default: 2 },
    corner: { type: Boolean, default: false },
    l: { type: Number, default: -1 },
    l2: { type: Number, default: -1 },
    s: { type: Number, default: -1 }
  },
  computed: {
    d: function() {
      var mp = middleOrientationPoints.bind(this)();

      var toPoint = [this.x2, this.y2];

      var ml = 9 * this.strokeWidth;
      var ce = this.orientation[this.orientation.length-1];
      if(ce === 'l') {
        toPoint[0] -= ml;
        if(!this.corner) {
          mp[1][0] -= ml;
        }
      }
      if(ce === 'r') {
        toPoint[0] += ml;
        if(!this.corner) {
          mp[1][0] += ml;
        }
      }

      return d3.line()
        .curve(
          this.corner ?
            d3.curveLinear :
            d3.curveCatmullRom
        )
        .x(d => d[0])
        .y(d => d[1])([
          [this.x1, this.y1],
          mp[0],
          mp[1],
          toPoint
        ])
    },
    dashArray: function() {
      if(this.isDashed) {
        return '5, 5'
      } else {
        return '0'
      }
    },
    marker: function() {
      if(this.corner) {
        return 'carrow-end-l';
      }
      return 'carrow-end-' + this.orientation[this.orientation.length-1];
    }
  },
  components: {
    arrowEndPath: require('./arrow-end-path')
  }
}

function middleOrientationPoints() {

  var l = 12 * this.strokeWidth;

  if(this.l !== -1) {
    l = this.l;
  }

  var l1 = l;
  var l2 = l;

  if(this.l2 !== -1) {
    l2 = this.l2;
  }

  var s = 3 * this.strokeWidth;
  if(this.s !== -1) {
    s = this.s;
  }
  if(this.corner) {
    s = 0;
    //l /= 1.5;
  }
  var m = {
    'lr': [[-l1, s], [l2, -s]],
    'll': [[-l1, -s], [-l2, s]],
    'tr': [[-s, -l1], [l2, s]],
    'tl': [[s, -l1], [-l2, s]],
    'bt': [[-s, l1], [s, -l2]],
    'br': [[-s, l1], [l2, -s]],
    'rr': [[l1, -s], [l2, s]],
    'rl': [[l1, -s], [-l2, s]],
  }
  var sm = m[this.orientation];
  if(
    (this.orientation == 'rl' || this.orientation == 'lr') &&
    this.y1 < this.y2
  ) {
    sm[0][1] = s; sm[1][1] = -s;
  }

  if(
    (this.orientation == 'bt' || this.orientation == 'tb') &&
    this.x1 < this.x2
  ) {
    sm[0][0] = s; sm[1][0] = -s;
  }

  if(!sm) {
    throw new Error('Can`t find orientation')
  }
  return [
    [sm[0][0] + this.x1, sm[0][1] + this.y1],
    [sm[1][0] + this.x2, sm[1][1] + this.y2],
  ];
}

</script>

<style lang='scss' scoped>
.linePath {
  fill: none;

}
</style>
