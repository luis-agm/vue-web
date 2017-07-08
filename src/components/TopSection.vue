<template>
  <div id='header' class='header'>
    <div class='header__banner medium-10 large-10 large-centered columns grid-x'>
      <div class='header__title small-10 small-centered medium-12 medium-centered large-6 columns'>
        <h1 class='header__main-banner name'>Luis González</h1>
        <transition name='fade'>
          <span v-show="showTag === true" class='header__main-banner great'>{{currentTag}}</span>
        </transition>
        <h1 class='header__main-banner developer'>Developer</h1>
      </div>
      <div class='header__buttons small-10 small-centered medium-12 medium-centered large-6 columns grid-x'>
        <button class='btn btn-1e small-12 large-7 rows'><span class='btn__text'><i class='fa fa-github fa-3'></i> GitHub</span></button>
        <button class='btn btn-1e small-12 large-7 rows'><span class='btn__text'><i class='fa fa-linkedin'></i> LinkedIn</span></button>
        <button class='btn btn-1e small-12 large-7 rows'><span class='btn__text'><i class='fa fa-envelope'></i> Contact Me</span></button>
      </div>
    </div>
    <div id='parts'></div>
  </div>
</template>

<script>
import 'particles.js'
import partCfg from '@/assets/particles.config.json'

export default {
  name: 'MainHeader',
  mounted () {
    window.particlesJS('parts', partCfg)
    setInterval(() => { this.cycleTags() }, 1500)
    // Sphere({container: 'clouder', tags: [ ...this.tags ]})
  },
  data () {
    return {
      showTag: true,
      currentTag: 'Full-Stack',
      tagPos: 0,
      headerTitle: 'Make Great Stuff',
      tags: ['JavaScript', 'Babel/ES6', 'NodeJS', 'Python', 'VueJS', 'React-Redux']
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

.header {
  font-family: 'Raleway', Helvetica, Arial, sans-serif;
  background: radial-gradient(ellipse at 50% 60%, rgba(255, 255, 255, 0.0), rgba(0, 0, 0, 5)), url('../assets/moreSky.jpg');
  background-size: cover;
  background-attachment: fixed;
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: center;
  height: 100vh;
  padding: 40px;

  &__buttons {
    display: flex;
    justify-content: center;
    min-height: 220px;
    .btn {
      border: none;
      font-family: inherit;
      font-size: inherit;
      color: $white;
      background: rgba(0, 0, 0, 0.3);
      cursor: pointer;
      padding: 25px 80px;
      display: inline-block;
      margin: 15px 30px;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: 700;
      outline: none;
      position: relative;
      transition: all 0.3s;
      box-shadow: 3px 4px 10px black;

      &.btn-1e {
        overflow: hidden;
        border: 2px solid $primary;
      }

      &.btn-1e:after {
        width: 100%;
        height: 0;
        top: 50%;
        left: 50%;
        background: $primary;
        opacity: 0;
        transform: translateX(-50%) translateY(-50%) rotate(45deg);
      }

      &.btn-1e:hover,
      &.btn-1e:active {
        color: $black;
        border-color: #16863B;
        box-shadow: 0px 0px 15px black;
      }

      &.btn-1e:hover:after {
        height: 260%;
        opacity: 1;
      }

      &.btn-1e:active:after {
        height: 400%;
        opacity: 1;
      }
    }
    .btn:after {
      content: '';
      position: absolute;
      z-index: -1;
      transition: all 0.3s;
    }
  }

  &__banner {
    z-index: 2;
    display: flex;
    flex-flow: row;
    max-width: 1200px;
  }

  &__title {
    display: flex;
    flex-flow: column;
  }

  &__main-banner {
    text-shadow: 2px 3px 10px black;
    transform: translateY(-15%);
    font-size: 64px;
    font-weight: 900;    
    color: #FFF;
    top: 50%;
    width: 60%;
    &.name {
      align-self: flex-start;
      width: auto;
      margin-top: 0.3em;
      margin-bottom: 0.3em;
    }
    &.great {
      align-self: flex-start;
      font-size: 72px;
      width: auto;
      color: $primary;
    }
    &.developer {
      align-self: flex-start;
      width: auto;
      margin-top: 0.3em;
      margin-bottom: 0.3em;
    }
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .3s
  }
  .fade-enter, .fade-leave-to {
    opacity: 0
  }

  canvas.particles-js-canvas-el {
    z-index: 1;
    position: absolute;
    top: 0;
    left: 0;
  }
}

</style>
