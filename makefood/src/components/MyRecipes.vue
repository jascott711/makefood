<template>
  <div id="display-recipes">
    <div id="recipe"
         v-for="recipe in recipes"
         :key="recipe.recipeID">
      <div class="container">
        <h3>{{recipe.recipeName}}</h3>
      </div>
    </div>
  </div>
</template>

<script>
  import recipes from '../data/recipes';

  export default {
    name: 'MyRecipes',
    props: [

    ],
    data: function() {
      return {
        recipes
      }
    }
  }
</script>

<style lang="scss">

</style>