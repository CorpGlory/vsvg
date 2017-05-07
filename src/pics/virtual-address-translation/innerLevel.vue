<template>
  <g :transform="`translate(${x}, 0)`">
    <sep :x="0" />
    <bt :text="name" :x="80" :y="35" />

    <g transform="translate(0, 50) scale(0.8)">
      <g v-for="block in blocks">
        <tb v-if="block.type == 'b'"
          :x="50" :y="block.y" :cols="10"
          :filled="block.filled"
          class="nonactive"
        />
        <tb v-if="block.type == 's'"
          :x="50" :y="block.y" :cols="10"
          :filled="block.filled"
          :shift='block.shift'
        />
        <tdots v-if="block.type == '.'"
          :x="100"
          :y="block.y"
        />
      </g>
    </g>

  </g>
</template>

<script>

export default {
 props: {
   name: {
     type: String,
     required: true
   },
   x: {
     type: Number,
     required: true
   },
   items: {
     type: String,
     required: true
   },
   filled: {
     type: [Array, String],
     default: function() {
       return [];
     }
   }
 },
 components: {
   'tb': require('./table'),
   'sep': require('./separator'),
   'bt': require('./blockTitle'),
 },
 computed: {
   blocks: function() {
     var y = 0;
     var res = [];
     var fldIndex = 0;
     for(var i = 0; i < this.items.length; i++) {
       var c = this.items[i];
       var r = {
         type: c
       }
       r.y = y;
       if(c == 'b' || c == 's') {
         y += 120;
         r.filled = this.filled[fldIndex];
         fldIndex++;
       }
       if(c == '.') {
         y += 15;
       }
       if(c == 's') {
         r.shift = +this.items[i + 1];
         i++;
       }
       res.push(r);
     }
     return res;
   }
 }
}

</script>


<style lang='scss' scoped>

</style>
