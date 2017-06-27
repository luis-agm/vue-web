<template>
  <div id='header' class='header'>    
    <div id='parts'></div>
    <h1 class='header__main-banner'>Make <span class='great'>Great</span> Stuff</h1>
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
  background: radial-gradient(ellipse at 50% 60%, rgba(255, 255, 255, 0.3), rgba(0, 0, 0, 7)), url('../assets/moreSky.jpg');
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
    font-family: 'Raleway', sans-serif;
    font-size: 64px;
    font-weight: 900;
    z-index: 99;
    align-self: flex-start;
    color: #FFF;
    top: 50%;
    width: 20%;
  }

  .great {
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
