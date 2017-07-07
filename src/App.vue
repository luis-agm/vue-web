<template>
  <div id="app">
    <top-section class='topsection grid-x'></top-section>
    <main-footer></main-footer>
    <router-view v-if='nav'></router-view>
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
  height: 100vh;  
}

</style>
