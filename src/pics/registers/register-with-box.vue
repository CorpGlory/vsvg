<template>
  <g>
    <r :x="x" :y="y"> {{ name }} </r>
    <g :transform="transform">
      <boxedText :value='value1'/>
      <boxedText :value='value2' y="29"/>
    </g>
  </g>
</template>

<script>
const _ = require('lodash');
export default {
  props: ['x', 'y', 'value'],
  components: {
    r: require('./register')
  },
  computed: {
    name: function() {
      return this.$slots.default[0].text;
    },
    transform: function() {
      return `translate(${this.x - 40} ${this.y + 5}) scale(0.5)`
    },
    value1: function() {
      return _.take(this.value, 8).join('')
    },
    value2: function() {
      return _.drop(this.value, 8).join('')
    },
    // dvalue: function() {
    //   return _.take(this.value, 2).join('') +
    //           '...' +
    //           _.drop(this.value, 5).join('');
    // }
  },
  data: function() {
    return {}
  }
}
</script>

<style lang='scss' scoped>
text {
  text-anchor: middle;
  font-size: 16px;
  font-weight: bold;
}
</style>
