<template>
  <v-toolbar class="main-toolbar elevation-0" v-bind:class='{ solid: solidHeader, "fixed-style": solidHeader }' light>
      <v-toolbar-side-icon @click.native.stop="sideNav()" light></v-toolbar-side-icon>
      <v-toolbar-title class="main-toolbar__title toolbar-text" v-bind:class='{ "fixed-style": solidHeader }'>Developer</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn class="main-toolbar__item toolbar-text" v-bind:class='{ "fixed-style": solidHeader }' v-for="item in navItems" :key="item" ripple>
          {{ item.title }}
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
</template>

<script>

import debounce from 'lodash/debounce'

export default {
  props: ['toggleNav'],
  data () {
    return {
      pageTitle: 'DevDevDev',
      navItems: [
        {title: 'Home', link: '#'},
        {title: 'About Me', link: '#'},
        {title: 'Projects', link: '#'}
      ],
      solidHeader: false
    }
  },
  methods: {
    sideNav () {
      this.toggleNav()
    },
    positionCheck () {
      if (window.scrollY >= 56) this.solidHeader = true
      if (window.scrollY < 56) this.solidHeader = false
    }
  },
  mounted () {
    window.addEventListener('scroll', debounce(this.positionCheck, 70))
  },
  destroyed () {
    window.removeEventListener('scroll', debounce(this.positionCheck, 70))
  }
}
</script>

<style lang='scss'>

.main-toolbar {
  z-index: 1;
  width: 100%;
  position:fixed;
  transition: background 0.4s;
  background: transparent;
  color: $white;

  &.solid {
    background: $primary;
    box-shadow: 1px 1px 7px #000000 !important;
  }

  .fixed-style {
    color: $black; 
  }

  &.toolbar--light .toolbar__item:hover {
    background-color: rgba(255,255,255,0.1);
  }

  &__title, &__item {    
    .toolbar-text {
      color: $white;
      font-weight: 400;
    }
    .fixed-style {      
      color: $black; 
    } 
  }

}
</style>
