<template>
  <g :transform="translate">
    <g v-for="line in lines">
      <text
        :x="line.x"
        :y="line.y"
        class="monofont"
      >
        {{ line.text }}
      </text>
    </g>

  </g>

</template>


<script>

const _ = require('lodash');

export default {
  props: {
    x: { type: Number, default: 0 },
    y: { type: Number, default: 0 }
  },
  computed: {
    translate: function() {
      return `translate(${this.x}, ${this.y + 10})`
    },
    lines: function() {
      var res =
        _(this.$slots.default[0].text.split('\n'))
        .drop(1)
        .map((e, i) => {
          return {
            x: _.takeWhile(e, c => c == ' ').length * 9,
            y: i * 20,
            text: _.dropWhile(e, c => c == ' ').join('')
          }
        })
        .value();
      return res;
    }
  }
}

</script>
