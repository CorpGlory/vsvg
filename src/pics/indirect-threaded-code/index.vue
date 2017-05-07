<template>
  <svg width="600" height="372">
    <g transform="translate(1,41)">
      <text x="300" y="195"> Dictionary Entry </text>
      <text x="0" y="95"> Dictionary entry </text>
      <boxedWords
        :x="205" :y="0"
        :words="prog"
      />

      <boxedWords
        :x="0" :y="100"
        :words="squareDict"
      />

      <boxedWords
        :x="300" :y="200"
        :words="dupDict"
      />

      <arrow
        :x1="300" :y1="28"
        :x2="300" :y2="110"
        :strokeWidth="1"
        :isDashed="true"
      />

      <curvyArrow
        :x1="305" :y1="128"
        :x2="490" :y2="193"
        orientation="bt"
        :strokeWidth="1"
        :isDashed="true"
      />

      <curvyArrow
        :x1="295" :y1="128"
        :x2="115" :y2="211"
        orientation="br"
        :l2="20"
        :strokeWidth="1"
      />

      <curvyArrow
        :x1="490" :y1="228"
        :x2="390" :y2="271"
        :l2="20"
        orientation="br"
        :strokeWidth="1"
      />


      <namedCode
        :x="50"
        :y="175"
        :width="172"
        :height="125"
      >
docol:
  sub rstack, 8
  mov [rstack], pc
  add w, 8
  mov pс, w
  jmp next
      </namedCode>

      <namedCode
        :x="300"
        :y="235"
        :width="172"
        :height="65"
      >
dup_impl:
  push qword[rsp]
  jmp next
      </namedCode>


    </g>

  </svg>
</template>

<script>

export default {
  components: {
    namedCode: require('../rip-data-section/named-code')
  },
  computed: {
    prog: function() {
      return [
        { text: '...',  width: 40 },
        { text: 'xt_square', style:'mono' },
        { text: '...', width: 40 },
      ];
    },
    squareDict: function() {
      return [
        { text: 'link', width: 60, bold: true },
        { text: 's', style:'mono' },
        { text: 'q', style:'mono' },
        { text: 'u', style:'mono' },
        { text: 'a', style:'mono' },
        { text: 'r', style:'mono' },
        { text: 'e', style:'mono' },
        { text: '0', style:'mono', bold: true },
        { text: 'flags', width: 60, bold: true },
        { text: 'docol', style:'mono' },
        { text: 'xt_dup', style:'mono' },
        { text: 'xt_mul', style:'mono'},
        { text: 'xt_exit', style:'mono' },
      ];
    },
    dupDict: function() {
      return [
        { text: 'link', width: 60, bold: true },
        { text: 'd', style:'mono' },
        { text: 'u', style:'mono' },
        { text: 'p', style:'mono' },
        { text: '0', style:'mono', bold: true },
        { text: 'dup_impl', style:'mono' },
      ];
    }
  }
}
</script>


<style lang='scss' scoped>
</style>
