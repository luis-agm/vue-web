<template>
  <div id="app">
    <div id='particles'>
      <h1>Hello!</h1>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import 'particles.js'
import partCfg from '@/assets/particles.config.json'

export default {
  name: 'app',
  mounted () {
    console.log(partCfg)
    window.particlesJS('particles', partCfg)
  }
}
</script>

<style lang='scss'>
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#particles {
  height: 800px;
  width: 100%;
  background-color: black;
}

h1 {
  color: #FFF;
  font-family: sans-serif;
  top: 0;
  width: 20%;
}
</style>
