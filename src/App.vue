<template>
  <div id="app">
    <div v-if='!ready' style='width: 100%; height: 100vh; background-color:seagreen; z-index: 9999;'></div>
    <top-section class='topsection'></top-section>
    <!--<router-view v-if='nav'></router-view>-->
  </div>
</template>

<script>
import Toolbar from 'components/Toolbar.vue'
import TopSection from 'components/TopSection.vue'
import MainFooter from 'components/Footer.vue'
import SideNavMenu from 'components/SideNavMenu.vue'

export default {
  data () {
    return {
      nav: false,
      sidenav: false,
      ready: false
    }
  },
  mounted () {
    this.ready = true
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
  components: {TopSection, Toolbar, MainFooter, SideNavMenu}
}
</script>

<style lang='scss'>

body {
  margin: 0;
  background-color: $dark-gray;
}

a {
  color: #1976d2;
  background-color: transparent;
}

#app {
  display: flex;
  flex-flow: column;
  font-size: 14pt;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;  
}

</style>
