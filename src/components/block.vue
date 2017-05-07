<template>

  <g :transform='translate'>
    <rect
      class='background'
      :width="width"
      :height="height"
      rx="10"
      ry="10"
    ></rect>
    <text
      v-if="label" class="label"
      text-anchor="middle"
      :x="width / 2"
      :y="height / 2 + 5"
    > {{label}} </text>
    <slot />
  </g>

</template>

<script>
export default {
  props: [
    'width', 'height', 'x', 'y', 'label'
  ],
  computed: {
    translate: function() {
      return `translate(${this.x}, ${this.y})`
    }
  }
}
</script>

<style lang='scss' scoped>
.background {
  fill: none;
  stroke-width:1
}
</style>
