<template>
  <svg width="592" height="352">
    <g transform="translate(1,1)" class="nonactive">
      <cpuBase :height="350" />
    </g>
    <block width="180" :height="160" x="5" y="181">
      <blockTitle>Registers</blockTitle>
      <g class="nonactive">
      <r :x="leftX" :y="line(1)">rax</r>
      <r :x="leftX" :y="line(2)">rbx</r>
      <r :x="leftX" :y="line(3)">rcx</r>
      <r :x="leftX" :y="line(4)">rdx</r>
      <r :x="leftX" :y="line(6)">rip</r>

      <r :x="rightX" :y="line(1)">rsi</r>
      <r :x="rightX" :y="line(2)">rdi</r>
      <g class="active">
        <rb :x="rightX" :y="line(3.2)" value="00000000E2809473">rsp</rb>
      </g>
      <r :x="leftX" :y="line(5)">rbp</r>
      <r :x="rightX" :y="line(6)">rflags</r>
      </g>
    </block>

    <block width="270" height="250" x="300" :y="(352 - 250)/2" class="nonactive">
      <blockTitle> Memory </blockTitle>
      <g transform="translate(10, 35)">
        <mu y="0"   value="11011100" address="0000 0000" />
        <mu y="30"  value="10011110" address="0000 0001" />
        <mu y="60"  value="11111001" address="0000 0002" />

        <g class="active">
          <mu y="120" value="00010110" address="E280 9473" />
        </g>

        <mu y="180" value="00110010" address="FFFF FFFF" />
      </g>

      <tdots :x="270 / 2" :y="140" />
      <tdots :x="270 / 2" :y="200" />

    </block>

    <g class="nonactive">
      <dearrow x1="190" y1="100" x2="300" y2="100" />
    </g>
    <curvyArrow
      :x1="178" :y1="288"
      :x2="304" :y2="218.5"
      :isDashed="true"
    />
  </svg>
</template>

<script>
export default {
  components: {
    r: require('../registers/register'),
    rb: require('../registers/register-with-box'),
    mu: require('../memory/memory-unit')
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


<style lang='scss' scoped>

</style>
