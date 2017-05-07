<template>
  <svg width="460" height="400">
    <g id="before" transform="translate(10,0)" >
      <ripBase :x="10" :y="1" />
      <g transform="translate(20, 0)" class="nonactive">
        <curvyArrow
          :x1="399"
          :y1="198"
          :x2="354"
          :y2="97"
          :strokeWidth="1"
          orientation="rr"
          :isDashed="true"
          :corner="true"
          :l="25"
          :l2="70"
          class="active"
        />

        <curvyArrow
          :x1="102"
          :x2="213"
          :y1="257"
          :y2="193"
          :s="5"
          :l2="30"
          :strokeWidth="1"
          orientation="tl"
          :isDashed="false"
        />

        <curvyArrow
          :x1="135"
          :x2="135"
          :y1="78"
          :y2="267"
          :l="15"
          :strokeWidth="1"
          :corner="true"
          orientation="rr"
          :isDashed="false"
        />
      </g>

      <curvyArrow
        class="nonactive"
        :x1="25"
        :x2="25"
        :y1="308"
        :y2="208"
        :l="30"
        :strokeWidth="1"
        :corner="true"
        orientation="ll"
        :isDashed="false"
      />

    </g>
  </svg>
</template>

<script>
export default {
  components: {
    ripBase: require('./rip-base')
  }
}
</script>


<style lang='scss' scoped>

</style>
