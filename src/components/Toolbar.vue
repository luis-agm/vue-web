<template>
  <v-toolbar class="main-toolbar elevation-0" v-bind:class='{ solid: solidHeader, "fixed-style": solidHeader }' light>
      <v-toolbar-title class="main-toolbar__title toolbar-text" v-bind:class='{ "fixed-style": solidHeader }'>Toolbar</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-toolbar-item class="main-toolbar__item toolbar-text" v-bind:class='{ "fixed-style": solidHeader }' v-for="item in navItems" :key="item">
          {{ item.title }}
        </v-toolbar-item>
      </v-toolbar-items>
    </v-toolbar>
</template>

<script>

import debounce from 'lodash/debounce'

export default {
  data () {
    return {
      pageTitle: 'DevDevDev',
      navItems: [
        {title: 'Projects', link: '#'},
        {title: 'Destruction', link: '#'}
      ],
      solidHeader: false
    }
  },
  methods: {
    positionCheck () {
      console.log('waat')
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

@import '../assets/styles/style.scss';

.main-toolbar {
  z-index: 1000;
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
