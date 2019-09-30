<template>
  <div id="app">
    <Header
      v-bind:areRecipesShowing="areRecipesShowing"
      v-bind:arePrefsShowing="arePrefsShowing"
      v-on:show-recipes="setRecipesShowing($event)"
      v-on:show-prefs="setPrefsShowing($event)"
    ></Header>
    <transition name="fade" id="content">
      <MyRecipes v-if="areRecipesShowing" v-on:get-recipe="setRecipe($event)"></MyRecipes>
      <Preferences v-if="arePrefsShowing"></Preferences>
    </transition>
    <RecipeView></RecipeView>
  </div>
</template>

<script>
  import recipes from './data/recipes';
  import Header from './components/Header'
  import MyRecipes from './components/MyRecipes'
  import Preferences from './components/Preferences'
  import RecipeView from './components/RecipeView'

  export default {
    name: 'app',
    components: {
      Header,
      MyRecipes,
      Preferences,
      RecipeView
    },
    props: [
      'getRecipes',
      'getPrefs'
    ],
    data() {
      return {
        recipes,
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
      },
      setRecipe: function(e){
        this.recipes = e;
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