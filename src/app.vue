<template>
  <div id="app">
    <h1> Low level pics </h1>
    <pics />
  </div>
</template>

<script>
export default {
  name: 'app',
  components: {
    pics: require('./pics/index')
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 30px;
}
a {
  color: black;
  text-decoration: none;
}

</style>
