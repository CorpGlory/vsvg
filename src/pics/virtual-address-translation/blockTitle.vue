<template>
  <g>
    <text
      v-for="line in lines"
      :x="x" :y="line.y"
      text-anchor="middle"
    >
      {{ line.text }}
    </text>
  </g>
</template>

<script>
export default {
  props: {
    x: {
      type:Number,
      required:true
    },
    y: {
      type:Number,
      required:true
    },
    text: {
      type:String,
      required:true
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
