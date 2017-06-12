<template>
  <div id='header'>    
    <div id='parts'></div>
    <h1>{{ headerTitle }}</h1>
  </div>
</template>

<script>
import 'particles.js'
import partCfg from '@/assets/particles.config.json'

export default {
  name: 'MainHeader',
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

#header {
  background: url('../assets/roraima.jpg');
  position: absolute;
  top: 0;
  left: 0;
  display: flex;
  flex-flow: column;
  height: 800px;
  width: 100%;

  .toolbar {
    width: 100%;
  }

  h1 {
    font-family: 'Ubuntu', sans-serif;
    z-index: 99;
    align-self: flex-start;
    color: #FFF;
    top: 0;
    width: 20%;
  }

  canvas.particles-js-canvas-el {
    /* background-color: rgba(#4781FF,0.2); */
    background-color: rgba(255,255,255,0.6);
    position: absolute;
    top: 0;
    left: 0;
  }
}

</style>
