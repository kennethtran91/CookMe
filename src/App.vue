<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import Homepage from '@/components/Homepage'
import Content from '@/components/Content'

export default {
  name: 'App',
  components: {
    Homepage, 
    
    }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: #F3F5F7;
  padding-top: 10%;
  padding-bottom: 50%;
}
</style>
