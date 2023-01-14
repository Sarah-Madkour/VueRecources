<template>
  <div>
    <the-resources></the-resources>
  </div>
</template>

<script>
import TheResources from './components/Resourses/TheResources.vue'

export default {
  name: 'App',
  components: {
    TheResources
  },
  
  
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
</style>
