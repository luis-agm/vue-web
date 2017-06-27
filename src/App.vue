<template>
  <div id="app">
    <toolbar/>
    <top-section class='topsection'></top-section>
    <router-view></router-view>
  </div>
</template>

<script>
import Toolbar from 'components/Toolbar.vue'
import TopSection from 'components/TopSection.vue'

export default {
  name: 'app',
  components: {TopSection, Toolbar}
}
</script>

<style lang='scss'>
@import './assets/styles/style.scss';
@import url('https://fonts.googleapis.com/css?family=Raleway:100,200,400,900');

body {
  margin: 0;
  background-color: $dark-gray;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
}

</style>
