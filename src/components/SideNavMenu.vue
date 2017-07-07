<template>     
  <v-list class="pt-0" dark>
    <v-list-tile>
      <v-list-tile-action>
        <v-icon>airplanemode_active</v-icon>
      </v-list-tile-action>
      <v-list-tile-content>
        <v-list-tile-title>Hola!</v-list-tile-title>
      </v-list-tile-content>
    </v-list-tile>
    <v-divider></v-divider>
    <v-list-tile>
      <v-list-tile-action>
        <v-icon>lock</v-icon>
      </v-list-tile-action>
      <v-list-tile-content>
        <v-list-tile-title>Hola2!</v-list-tile-title>
      </v-list-tile-content>
    </v-list-tile>
  </v-list>
</template>

<script>
export default {
  props: ['closeNav', 'visible'],
  beforeDestroy () {
    this.closeNav()
  },
  computed: {
    showSideNav () {
      return this.visible
    }
  }
}
</script>

<style>
</style>
