<template>
  <div id="app">
    <PerfectNav/>
  </div>
</template>

<script>
import PerfectNav from './components/PerfectNav.vue'

export default {
  name: 'app',
  components: {
    PerfectNav
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
