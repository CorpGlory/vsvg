<template>
  <curvyArrow
    :x1="x1"
    :x2="x2"
    :y1="y1"
    :y2="y2"
    :strokeWidth="1"
    orientation="rl"
    :isDashed="!isPath"
    :class="isPath?'':'nonactive'"
  />
</template>

<script>
export default {
  props: {
    x1: {
      type:Number,
      required:true
    },
    y1: {
      type:Number,
      required:true
    },
    x2: {
      type:Number,
      required:true
    },
    y2: {
      type:Number,
      required:true
    },
    isPath: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    lines: function() {
      var h = 20;
      var ls = this.text.split(',')
      var yy = this.y - ls.length * h / 2
      return ls.map((e,i) => ({
        text: e,
        y: i * h + yy
      }))

    }
  }
}
</script>
