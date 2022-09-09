<template>
  <div id="App">
    <LearnApp />
  </div>
</template>

<script>
import LearnApp from './components/LearnApp.vue'

export default {
  name: 'App',
  components: {
    LearnApp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin: 60px 40px;
}
</style>
