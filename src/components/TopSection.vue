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
        <top-button v-for='button in buttons' :key='button' :icon='button.icon' :text='button.text' @click.native='goTo( button.link )'></top-button>
      </div>
    </div>
    <div id='parts'></div>
  </div>
</template>

<script>
import 'particles.js'
import partCfg from '@/assets/particles.config.json'
import TopButton from 'components/TopButton.vue'

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
      tags: ['JavaScript', 'Babel/ES6', 'NodeJS', 'Python', 'VueJS', 'React-Redux'],
      buttons: [
        { icon: 'fa-github', text: 'GitHub', link: 'http://github.com/luis-agm' },
        { icon: 'fa-linkedin', text: 'LinkedIn', link: 'http://linkedin.com/in/luis-agm-dev' },
        { icon: 'fa-envelope', text: 'Contact Me', link: 'contact' }
      ]
    }
  },
  methods: {
    goTo (link) {
      console.log('LINKED')
      if (link === 'contact') {

      } else {
        window.location = link
      }
    },
    cycleTags () {
      this.showTag = false
      setTimeout(() => {
        this.currentTag = this.tags[this.tagPos]
        this.tagPos === this.tags.length - 1 ? this.tagPos = 0 : this.tagPos += 1
        this.showTag = true
      }, 300)
    }
  },
  components: { TopButton }
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
  }

  &__banner {
    z-index: 2;
    display: flex;
    flex-flow: row;
    max-width: 1200px;
    justify-content: space-around;
  }

  &__title {
    display: flex;
    flex-flow: column;
  }

  &__main-banner {
    text-shadow: 2px 3px 10px black;
    font-size: responsive 50px 64px;
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
      font-size: responsive 55px 70px;
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
