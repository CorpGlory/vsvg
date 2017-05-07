<template>
  <svg width="192" height="482">
    <g transform="translate(1,1)" class="nonactive">
      <cpuBase :height="480" />
    </g>
    <block width="180" :height="287" x="5" y="181">
      <blockTitle>Registers</blockTitle>
      <rb :x="leftX" :y="line(1)"   value="D64905E5E92004D3">rax</rb>
      <rb :x="leftX" :y="line(2)"   value="68D1071186DB5372">rbx</rb>
      <rb :x="leftX" :y="line(3)"   value="686DB5C539637133">rcx</rb>
      <rb :x="leftX" :y="line(4)"   value="735437D42396E5A1">rdx</rb>
      <rb :x="leftX" :y="line(5.2)" value="72396437DD396E33">rip</rb>

      <rb :x="rightX" :y="line(1)"   value="E280947337D42391">rsi</rb>
      <rb :x="rightX" :y="line(2)"   value="534C972C3AD1248F">rdi</rb>
      <rb :x="rightX" :y="line(3)"   value="B3AD80ABD802E112">rsp</rb>
      <rb :x="rightX" :y="line(4)"   value="75732E3E8B7D4211">rbp</rb>
      <rb :x="rightX" :y="line(5.2)" value="FF8B2489118BD2B5">rflags</rb>
    </block>
  </svg>
</template>

<script>

export default {
  components: {
    rb: require('./register-with-box')
  },
  computed: {
    leftX: function functionName() {
      return 46.5;
    },
    rightX: function functionName() {
      return 133.5;
    },
  },
  methods: {
    line: function(l) {
      return l * 49 - 10;
    }
  }
}
</script>

<style lang='scss'>

</style>
