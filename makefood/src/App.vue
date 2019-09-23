<template>
  <div id="app">
    <Header
      v-bind:areRecipesShowing="areRecipesShowing"
      v-bind:arePrefsShowing="arePrefsShowing"
      v-on:show-recipes="setRecipesShowing($event)"
      v-on:show-prefs="setPrefsShowing($event)"
    ></Header>
    <transition name="fade" id="content">
      <MyRecipes v-if="areRecipesShowing"></MyRecipes>
      <Preferences v-if="arePrefsShowing"></Preferences>
    </transition>
  </div>
</template>

<script>
  import Header from './components/Header'
  import MyRecipes from './components/MyRecipes'
  import Preferences from './components/Preferences'

  export default {
    name: 'app',
    components: {
      Header,
      MyRecipes,
      Preferences
    },
    props: [
      'getRecipes',
      'getPrefs'
    ],
    data() {
      return {
        areRecipesShowing: true,
        arePrefsShowing: false
      }
    },
    methods: {
      setRecipesShowing: function(showing){
        this.areRecipesShowing = showing;
      },
      setPrefsShowing: function(showing){
        this.arePrefsShowing = showing;
      }
    },
    watch: {
      getRecipes: function(showing){
        this.areRecipesShowing = showing;
      },
      getPrefs: function(showing){
        this.arePrefsShowing = showing;
      }
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