<template>
  <marker id="arrow-end" markerWidth="12" markerHeight="20" refX="0" refY="4" orient="auto-start-reverse" markerUnits="strokeWidth">
    <arrowEndPath />
  </marker>
</template>

<script>
export default {
  components: {
    arrowEndPath: require('./arrow-end-path')
  }
}
</script>
