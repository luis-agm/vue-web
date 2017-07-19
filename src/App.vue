<template>
  <div id="app">
    <top-section class='topsection'></top-section>
    <div class='sidenav'>
    
    </div>
    <MainFooter class='wat' />
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

.sidenav {
  width: 75px;
  height: 100vh;
  position: absolute;
  right: 0;
  top: 0;
  z-index: 3;
  background-color: rgba(0, 0, 0, 0.3);
}

#app {
  display: flex;
  flex-flow: column;
  background: radial-gradient(ellipse at 50% 60%, rgba(255, 255, 255, 0.0), rgba(0, 0, 0, 5)), url('./assets/moreSky.jpg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  font-size: 14pt;
  -moz-osx-font-smoothing: grayscale;
  min-height: 100vh;  
}

</style>
