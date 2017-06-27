<template>
  <div id='header' class='header'>    
    <div id='parts'></div>
    <h1 class='header__main-banner'>Luis <span class='great'>Full-Stack</span> Developer</h1>
  </div>
</template>

<script>
import 'particles.js'
import partCfg from '@/assets/particles.config.json'
// import Sphere from '@/scripts/clouder.js'

export default {
  name: 'MainHeader',
  mounted () {
    console.log(partCfg)
    window.particlesJS('header', partCfg)
    // Sphere({container: 'clouder', tags: [ ...this.tags ]})
  },
  data () {
    return {
      headerTitle: 'Make Great Stuff',
      tags: ['JavaScript', 'ES6', 'NodeJS', 'Stuff', 'More Stuff']
    }
  }
}
</script>

<style lang='scss'>

@import '../assets/styles/style.scss';


.header {
  background: radial-gradient(ellipse at 50% 60%, rgba(255, 255, 255, 0.0), rgba(0, 0, 0, 5)), url('../assets/moreSky.jpg');
  background-size: cover;
  background-attachment: fixed;
  position: absolute;
  left: 0;
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100%;
  padding: 40px;

  #clouder {
    height: 300px;
    width: 300px;
  }

  &__main-banner {
    text-shadow: 2px 3px 10px black;
    transform: translateY(-15%);
    font-family: 'Raleway', sans-serif;
    font-size: 64px;
    font-weight: 900;
    z-index: 99;
    align-self: center;
    color: #FFF;
    top: 50%;
    width: 60%;
  }

  .great {
      text-overflow: nowrap;
      font-size:100%;
      color: $primary;
    }

  canvas.particles-js-canvas-el {
    /* background-color: rgba(#4781FF,0.2); */
    // background-color: rgba(0,0,0,0.6);
    position: absolute;
    top: 0;
    left: 0;
  }
}

</style>
