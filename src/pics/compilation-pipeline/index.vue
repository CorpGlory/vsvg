<template>
  <svg width="580" height="591">

    <fc name="first" x="0" y="0" />
    <fc name="second" x="390" y="0" />

    <block width="180" height="70" x="200" y="370" label="Linker" />
    <text
      text-anchor="middle"
      x="290" y="330"
    >
      libraries
    </text>
    <arrow x1="290" :y1="370-35" x2="290" y2="370" />

    <block width="180" height="70" x="200" y="520" label="Loader" />

    <labeledArrow x1="290" y1="440" x2="290" y2="520">
      <text>executable file</text>
    </labeledArrow>

    <arrow x1="90" y1="340" x2="200" y2="410" />
    <arrow x1="480" y1="340" x2="380" y2="410" />

  </svg>
</template>

<script>
export default {
  components: {
    fc: require('./file-compilation')
  },
  computed: {
  },
  methods: {
  }
}
</script>


<style lang='scss' scoped>

</style>
