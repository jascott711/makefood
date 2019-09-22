<template>
  <div id="app">
    <Header></Header>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="makefood"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header'

export default {
  name: 'app',
  components: {
    HelloWorld,
    Header
  }
}
</script>

<style lang="scss">
  @import './scss/variables';

  body {
    margin: 0;
  }

  #app {
    font-family: $primary_font;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
  }
</style>