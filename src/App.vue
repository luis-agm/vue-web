<template>
  <div id="app">
    <div id='header'>
      <h1>{{ headerTitle }}</h1>
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
    window.particlesJS('header', partCfg)
  },
  data () {
    return {
      headerTitle: 'Awesome Header'
    }
  }
}
</script>

<style lang='scss'>

@import url('https://fonts.googleapis.com/css?family=Ubuntu');

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

#header {
  background: url('assets/roraima.jpg');
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  height: 800px;
  width: 100%;

  h1 {
    font-family: 'Ubuntu', sans-serif;
    z-index: 99;
    align-self: center;
    color: #FFF;
    top: 0;
    width: 20%;
  }

  canvas {
    background-color: rgba(#4781FF,0.5);
    position: absolute;
    top: 0;
    left: 0;
  }
}

/* flexbox mebby? */


</style>
