<template>
  <text class="monofont" :x="x" :y="y" >
    <slot />
  </text>

</template>

<script>
export default {
  props: ['x', 'y']
}
</script>

<style lang='scss' scoped>
text {
  text-anchor: middle;
  font-size: 16px;
  font-weight: bold;
}
</style>
