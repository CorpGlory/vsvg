<template>
  <svg width="566" height="352">

    <block width="180" height="70" x="5" y="1" label="Data Stack" />
    <block width="180" height="70" x="5" y="121" label="CPU" />
    <block width="180" height="70" x="5" y="241" label="Return Stack" />

    <memory x="295" :y="62" />

    <dearrow x1="90" y1="71" x2="90" y2="121" />
    <dearrow x1="90" y1="191" x2="90" y2="241" />

    <dearrow x1="185" y1="156" x2="295" y2="156" />

  </svg>
</template>

<script>
export default {
  components: {
    memory: require('../memory/index')
  },
  computed: {
  },
  methods: {
  }
}
</script>


<style lang='scss' scoped>

</style>
