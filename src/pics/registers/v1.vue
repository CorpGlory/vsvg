<template>
  <svg width="192" height="352">
    <g transform="translate(1,1)" class="nonactive">
      <cpuBase :height="350" />
    </g>
    <block width="180" :height="160" x="5" y="181">
      <blockTitle>Registers</blockTitle>
      <r :x="leftX" :y="line(1)">rax</r>
      <r :x="leftX" :y="line(2)">rbx</r>
      <r :x="leftX" :y="line(3)">rcx</r>
      <r :x="leftX" :y="line(4)">rdx</r>
      <r :x="leftX" :y="line(6)">rip</r>

      <r :x="rightX" :y="line(1)">rsi</r>
      <r :x="rightX" :y="line(2)">rdi</r>
      <r :x="rightX" :y="line(3)">rsp</r>
      <r :x="rightX" :y="line(4)">rbp</r>
      <r :x="rightX" :y="line(6)">rflags</r>

    </block>
  </svg>
</template>

<script>

export default {
  components: {
    r: require('./register')
  },
  computed: {
    leftX: function functionName() {
      return 50;
    },
    rightX: function functionName() {
      return 130;
    },
  },
  methods: {
    line: function(l) {
      return l * 20 + 25;
    }
  }
}
</script>

<style lang='scss'>

</style>
