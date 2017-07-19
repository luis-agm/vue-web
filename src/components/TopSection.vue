<template>
  <div id='top-section' class='top-section'>
    <div class='top-section__container medium-12 large-10 large-centered columns grid-x'>
      <div class='top-section__banner medium-12 large-12 large-centered columns grid-x'>
        <div class='top-section__title small-12 small-centered medium-8 medium-centered large-6 columns'>
          <h1 class='top-section__main-banner name'>Luis González</h1>
          <transition name='fade'>
            <span v-show="showTag === true" class='top-section__main-banner great'>{{currentTag}}</span>
          </transition>
          <h1 class='top-section__main-banner developer'>Developer</h1>
        </div>
        <div class='top-section__buttons small-12 small-centered medium-8 medium-centered large-6 columns grid-x'>
          <TopButton v-for='button in buttons' :key='button' :icon='button.icon' :text='button.text' @click.native='goTo( button.link )'></TopButton>
        </div>
      </div>
    </div>
    <ModalForm v-if='showForm' @close='closeForm()'></ModalForm>
    <div id='parts'></div>
  </div>
</template>

<script>
import 'particles.js'
import partCfg from '@/assets/particles.config.json'
import TopButton from 'components/TopButton.vue'
import ModalForm from 'components/ModalForm.vue'
import MainFooter from 'components/Footer.vue'

export default {
  name: 'TopSection',
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
      tags: ['JavaScript', 'ES2017', 'NodeJS', 'Python', 'VueJS', 'React', 'Angular', 'Full-Stack'],
      buttons: [
        { icon: 'fa-github', text: 'GitHub', link: 'https://github.com/luis-agm' },
        { icon: 'fa-linkedin', text: 'LinkedIn', link: 'https://linkedin.com/in/luis-agm-dev' },
        { icon: 'fa-codepen', text: 'CodePen', link: 'https://codepen.io/luis-agm/' },
        { icon: 'fa-envelope', text: 'Contact Me', link: 'contact' }
      ],
      showForm: false
    }
  },
  methods: {
    closeForm () {
      this.showForm = false
    },
    goTo (link) {
      if (link === 'contact') {
        this.showForm = true
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
  components: { TopButton, ModalForm, MainFooter }
}
</script>

<style lang='scss'>

.top-section {
  font-family: 'Raleway', Helvetica, Arial, sans-serif;
  display: flex;
  flex-flow: column;
  flex: 20 0 auto;
  align-items: center;
  justify-content: center;
  overflow:visible;
  padding: 0px 40px;

  &__buttons {
    display: flex;
    justify-content: center;
    min-height: 220px;    
  }

  &__container {
    display: flex;
  }

  &__banner {
    z-index: 2;
    display: flex;
    flex-flow: row;
    max-width: 1200px;
    justify-content: space-around;
    align-self: center;
  }

  &__title {
    display: flex;
    flex-flow: column;
    justify-content: center;
  }

  &__main-banner {
    text-shadow: 2px 3px 10px black;
    font-size: responsive 45px 64px;
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
      font-size: responsive 50px 70px;
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
