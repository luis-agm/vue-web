<template>
  <div></div>
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
