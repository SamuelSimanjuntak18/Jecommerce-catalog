<template> 
  <TvMaze msg="Helo"/>
</template>

<script>
import TvMaze from './components/TvMaze.vue'

export default {
  name: 'App',
  components: {
    TvMaze
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
