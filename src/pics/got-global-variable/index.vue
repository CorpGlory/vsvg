<template>
  <svg width="300" height="700">
    <block width="245" :height="560" x="1" y="1">
      <blockTitle> Virtual Memory </blockTitle>
      <block width="235" height="270" x="5" y="30">
        <blockTitle> Lib </blockTitle>
        <g class="nonactive">
          <namedCode
            :x="5"
            :y="20"
            :width="225"
            :height="65"
            name=".text"
          >
fun:
   mov rdx, rcx
{{ dt }}
          </namedCode>

        </g>

        <namedCode
          :x="5"
          :y="110"
          :width="225"
          :height="65"
          name=".data"
        >
{{ dt }}
           x
{{ dt }}
        </namedCode>

        <g class="nonactive">
          <namedCode
            :x="5"
            :y="200"
            :width="225"
            :height="30"
            name="GOT"
          >
{{ dt }}
          </namedCode>
      </g>

      </block>
      <block width="235" height="240" x="5" y="305">
        <blockTitle> Main </blockTitle>

        <namedCode
          :x="5"
          :y="20"
          :width="225"
          :height="65"
          name="GOT"
        >
{{ dt }}
address of x
{{ dt }}
        </namedCode>

        <namedCode
          :x="5"
          :y="110"
          :width="225"
          :height="90"
          name=".text"
        >
main:
  ...
  mov rax, [x wrt ..got]
  mov rax, [rax]
        </namedCode>
      </block>


      <curvyArrow
        :x1="160" :y1="380"
        :x2="160" :y2="196"
        :strokeWidth="1"
        orientation="rr"
        :corner="true"
        :isDashed="true"
        :l="20"
      />

      <curvyArrow
        :x1="240" :y1="490"
        :x2="200" :y2="380"
        :l2="60"
        :strokeWidth="1"
        orientation="rr"
        :corner="true"
        :isDashed="true"
        :l="20"
      />
    </block>
  </svg>
</template>

<script>
export default {
  components: {
    namedCode: require('../rip-data-section/named-code')
  },
  computed: {
    dt: function() {
      return '          ...';
    }
  }
}
</script>
