
<template>

<block width="270" height="190" :x="x" :y="y">
  <blockTitle> Memory </blockTitle>
  <g transform="translate(10, 35)">
    <mu y="0"   value="11011100" address="0000 0000" />
    <mu y="30"  value="10011110" address="0000 0001" />
    <mu y="60"  value="11111001" address="0000 0002" />
    <mu y="120" value="00110010" address="FFFF FFFF" />
  </g>

  <tdots :x="270 / 2" :y="140" />

</block>
</template>

<script>
export default {
  props: ['x', 'y'],
  components: {
    mu: require('./memory-unit')
  }
}
</script>
