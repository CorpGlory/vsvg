<template>
  <text
    font-weight="bold"
    :x="x"
    :y="y"
    text-anchor="middle"
  > ... </text>
</template>

<script>
export default {
  props: {
    x: {
      type: Number,
      required: true
    },
    y: {
      type: Number,
      required: true
    },
  }
}
</script>
