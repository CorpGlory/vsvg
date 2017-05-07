<template>
  <g :transform="translate">
    <text> {{ name }} </text>
    <g transform="translate(0, 5)">
      <slot />
    </g>
  </g>
</template>


<script>

export default {
  props: {
    x: { type: Number, default: 0 },
    y: { type: Number, default: 0 },
    name: { type: String, required: true },
  },
  computed: {
    translate: function() {
      return `translate(${this.x}, ${this.y + 20})`
    },
  }
}

</script>
