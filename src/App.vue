<template>
  <div id="app">
    <v-navigation-drawer v-model='sidenav' class='side-nav' persistent temporary enable-resize-watcher light>      
      <main-menu></main-menu>
    </v-navigation-drawer>  
    <toolbar :toggle-nav="toggleSideNav"></toolbar>
    <top-section class='topsection'></top-section>
    <main-footer></main-footer>
    <router-view v-if='nav'></router-view>
  </div>
</template>

<script>
import Toolbar from 'components/Toolbar.vue'
import TopSection from 'components/TopSection.vue'
import MainFooter from 'components/Footer.vue'
import MainMenu from 'components/MainMenu.vue'

export default {
  data () {
    return {
      nav: false,
      sidenav: false
    }
  },
  methods: {
    toggleSideNav () {
      this.sidenav = !this.sidenav
    },
    closeSideNav () {
      this.sidenav = false
    }
  },
  name: 'app',
  components: {TopSection, Toolbar, MainFooter, MainMenu}
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
