<template>
  <namedBlock :x="x" :y="y" :name="name">
    <rect
      x="0" y="0"
      :width="width"
      :height="height"
      fill="none"
    />
    <monofontText :x="5" :y="5"><slot/></monofontText>
  </namedBlock>
</template>

<script>
export default {
  props: {
    x: { type: Number, default: 0 },
    y: { type: Number, default: 0 },
    width: { type: Number, default: 100 },
    height: { type: Number, default: 100 },
    name: { type: String, required: true },
  },
  components: {
    namedBlock: require('./named-block')
  }
}

</script>
