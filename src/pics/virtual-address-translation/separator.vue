<template>

<line
  :x1="x" :x2="x"
  y1='50' y2='550'
/>

</template>

<script>
export default {
  props: {
    x: {
      type: Number,
      required: true
    }
  }
}

</script>

<style scoped>
line {
  stroke: gray;
  stroke-width: 0;
}
</style>
