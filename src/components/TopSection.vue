<template>
  <div id='header' class='header'>    
    <div id='parts'></div>
    <div class='header__banner'>
      <h1 class='header__main-banner name'>Luis González ,</h1>
      <transition name='fade'>
        <span v-show="showTag === true" class='header__main-banner great'>{{currentTag}}</span>
      </transition>
      <h1 class='header__main-banner developer'> Developer</h1>
    </div>
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
    setInterval(() => { this.cycleTags() }, 1500)
    // Sphere({container: 'clouder', tags: [ ...this.tags ]})
  },
  data () {
    return {
      showTag: true,
      currentTag: 'Full-Stack',
      tagPos: 0,
      headerTitle: 'Make Great Stuff',
      tags: ['JavaScript', 'ES6', 'NodeJS', 'Stuff', 'More Stuff']
    }
  },
  methods: {
    cycleTags () {
      this.showTag = false
      setTimeout(() => {
        this.currentTag = this.tags[this.tagPos]
        this.tagPos === this.tags.length - 1 ? this.tagPos = 0 : this.tagPos += 1
        this.showTag = true
      }, 300)
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

  &__banner {
    width: 60%;
    display: flex;
    flex-flow: column;
  }

  &__main-banner {
    text-shadow: 2px 3px 10px black;
    transform: translateY(-15%);
    font-size: 64px;
    font-weight: 900;
    z-index: 99;
    color: #FFF;
    top: 50%;
    width: 60%;
    &.name {
      align-self: flex-start;
      width: auto;
    }
    &.great {
      text-align: center;
      align-self: center;
      width: 100%;
      transform: translateX(-50px);
      color: $primary;
      margin-bottom: 16px;
    }
    &.developer {
      align-self: flex-end;
      width: auto;
    }
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .3s
  }
  .fade-enter, .fade-leave-to {
    opacity: 0
  }

  canvas.particles-js-canvas-el {
    position: absolute;
    top: 0;
    left: 0;
  }
}

</style>
