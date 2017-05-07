<template>
  <g :transform="translate">
    <namedCode name=".text (main)"
      :x="0" :y="0"
      :height="65" :width="180"
      >
{{ cd }}
  call PLT[foo]
{{ cd }}
    </namedCode>

    <namedCode name=".text (lib)"
      :x="225" :y="0"
      :height="85" :width="180"
      >
{{ cd }}
foo:
  mov rax, rbx
{{ cd }}
    </namedCode>

    <namedCode name="PLT"
      :x="0" :y="110"
      :height="185" :width="180"
      >
{{ cd }}
PLT[0]:
  call resolve
{{ cd }}
PLT[foo]:
  jmp *GOT[foo]
  prepare resolving
  jmp PLT[0]
{{ cd }}
    </namedCode>

    <namedBlock
      name="GOT"
      :x="225" :y="125"
      :height="145"
    >
      <g>
      <tb
        :x="0" :y="0"
        :cols="15"
        :width="180"
        filled="2"
      />
      </g>
    </namedBlock>

  </g>
</template>

<script>
export default {
  props: {
    x: { type: Number, default: 0 },
    y: { type: Number, default: 0 },
  },
  components: {
    namedCode: require('./named-code'),
    namedBlock: require('./named-block'),
    tb: require('../virtual-address-translation/table')
  },
  computed: {
    translate: function() {
      return `translate(${this.x}, ${this.y + 20})`
    },
    cd: function() {
      return '       ...';
    }
  }
}
</script>
