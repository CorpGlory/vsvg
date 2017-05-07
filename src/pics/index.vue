<template>
<div>
  <picHolder picName="Von Neumann Architecture - 1"><p1/></picHolder>
  <picHolder picName="Von Neumann Architecture - 2"><p2/></picHolder>

  <table style="width:500px">
    <tr>
      <td>
        <picHolder picName="Registers - Version 1"><p3_1/></picHolder>
      </td>
      <td>
        <picHolder picName="Registers - Version 2"><p3_2/></picHolder>
      </td>
    </tr>
  </table>

  <picHolder picName="Stack register"><p4/></picHolder>
  <picHolder picName="Compilation pipeline"><p5/></picHolder>
  <picHolder picName="Forth machine"><p6/></picHolder>

  <picHolder picName="Virtual address translation"><p7/></picHolder>

  <picHolder picName="PLT Before resolving"><p8_1/></picHolder>

  <picHolder picName="PLT After resolving"><p8_2/></picHolder>

  <picHolder picName="Inderect threated code"><p9/></picHolder>

  <picHolder picName="GOT global variable"><p10/></picHolder>

  <div style="height: 400px"></div>

</div>
</template>

<script>

import Vue from 'vue';

Vue.component('cpuBase', require('./cpu-base'));

export default {
  components: {
    p1: require('./von-neuman-1'),
    p2: require('./von-neuman-2/index'),
    p3_1: require('./registers/v1'),
    p3_2: require('./registers/v2'),
    p4: require('./reg-stack/index'),
    p5: require('./compilation-pipeline/index'),
    p6: require('./forth-machine/index'),
    p7: require('./virtual-address-translation/index'),
    p8_1: require('./rip-data-section/before'),
    p8_2: require('./rip-data-section/after'),
    p9: require('./indirect-threaded-code/index'),
    p10: require('./got-global-variable/index'),
  }
}

</script>

<style lang='scss'>

$active-color: black;
$nonactive-color: gray;

.monofont {
  font-family:monospace;
  font-size: 15px;
}

table,
svg {
  margin: auto;
}

table {
  td {
    vertical-align: top
  }
}

@mixin elems-colors($color) {
  path,
  text {
    fill: $color;
  }
  line,
  path,
  rect {
    stroke: $color;
  }
}

@include elems-colors($active-color);

.nonactive {
  @include elems-colors($nonactive-color);
}

.active {
  @include elems-colors($active-color);
}

</style>
