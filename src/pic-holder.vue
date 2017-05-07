<template>
  <div>
    <h3 v-if="picName">{{picName}}</h3>
    <slot/>
  </div>
</template>

<script>

export default {
  props: [ 'picName' ]
}

</script>

<style lang='scss'>
.block {
  fill: none;
  stroke-width: 1;
  stroke: black;
}
</style>
