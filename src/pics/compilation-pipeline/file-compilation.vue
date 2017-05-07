<template>
  <g :transform="`translate(${x}, ${y})`">
    <text
      text-anchor="middle"
      class="monofont"
      x="90" y="20"
    >
      {{ name }}.asm
    </text>
    <arrow x1="90" y1="25" x2="90" y2="60" />
    <g transform="translate(0,61)">
      <block width="180" height="70" x="5" y="0" label="Preprocessor" />
      <block width="180" height="70" x="5" y="150" label="Compiler" />
      <labeledArrow x1="90" y1="70" x2="90" y2="150">
        <text>code with substitutions</text>
      </labeledArrow>
    </g>

    <g transform="translate(0,281)">
      <arrow x1="90" y1="0" x2="90" y2="35" />
      <text
        text-anchor="middle"
        class="monofont"
        x="90" y="50"
      >
        {{ name }}.o
      </text>
    </g>
  </g>

</template>

<script>
export default {
  props: ['name', 'x', 'y'],
  components: {
  },
  computed: {
  },
  methods: {
  }
}
</script>


<style lang='scss' scoped>

</style>
