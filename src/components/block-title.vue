<template>
  <text :x="x" y="20" text-anchor="middle">
    <slot />
  </text>
</template>

<script>
export default {
  data: function() {
    return {
      x: 0
    }
  },
  mounted: function() {
    var bbox = this.$parent.$el.getBBox();
    this.x = (bbox.width + bbox.x) / 2;
  }
}
</script>
