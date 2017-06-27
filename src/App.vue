<template>
  <div id="app">
    <toolbar></toolbar>
    <top-section class='topsection'></top-section>
    <main-footer></main-footer>
    <router-view v-if='nav'></router-view>
  </div>
</template>

<script>
import Toolbar from 'components/Toolbar.vue'
import TopSection from 'components/TopSection.vue'
import MainFooter from 'components/Footer.vue'

export default {
  data () {
    return {
      nav: false
    }
  },
  name: 'app',
  components: {TopSection, Toolbar, MainFooter}
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
  display: flex;
  flex-flow: column;
  font-family: 'Raleway', Helvetica, Arial, sans-serif;
  font-size: 14pt;
  -moz-osx-font-smoothing: grayscale;
  height: 100vh;
}

</style>
