<template>
  <div id="app">
    <main-header></main-header>
    <router-view></router-view>
  </div>
</template>

<script>
import MainHeader from 'components/Header.vue'

export default {
  name: 'app',
  components: {MainHeader}
}
</script>

<style lang='scss'>

@import url('https://fonts.googleapis.com/css?family=Ubuntu');

body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
