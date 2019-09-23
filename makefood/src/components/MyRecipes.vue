<template>
  <div id="display-recipes">
    <div class="recipe-list">
      <div class="recipe-list-item"
          v-for="recipe in recipes"
          :key="recipe.recipeID"
          @click="getCurrentRecipe($event, recipe)">
        <div class="recipe-title">{{recipe.recipeName}}</div>
      </div>
    </div>
    <div class="recipe-full">
      <div class="recipe-title">{{currentRecipe}}</div>
      <div class="recipe-ingredients"
          v-for="ingredient in currentIngredients">
        <div class="componentName">{{ingredient.ingredientComponentName}}</div>
        <div class="ingredients"
          v-for="ingredientList in ingredient.ingredients">
          {{ingredientList}}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import recipes from '../data/recipes';

  export default {
    name: 'MyRecipes',
    props: [
      'currentRecipe',
      'currentIngredients'
    ],
    data: function() {
      return {
        recipes
      }
    },
    methods: {
      getCurrentRecipe: function (e, recipe) {
        this.currentRecipe = recipe.recipeName;
        this.currentIngredients = recipe.recipeIngredients;


      }
    }
  }
</script>

<style lang="scss">
  @import '../scss/variables';

  #display-recipes {
    background: $grey1;
    padding: 20px 10px 10px;
    .recipe-list {
      text-align: left;
      .recipe-list-item {
        display: block;
        background: $grey2;
        -webkit-border-radius: 3px;
        -moz-border-radius: 3px;
        border-radius: 3px;
        padding: 10px;
        margin: 0 10px 10px;
        text-align: center;
        .recipe-title {
          font-size: 18px;
          font-weight: 700;
        }
      }
    }
    .recipe-full {
      .recipe-title {
        font-size: 24px;
        font-weight: 700;
      }
    }
  }

  @media(min-width: 768px) {
    #display-recipes {
      .recipe-list {
        display: inline-block;
        width: 350px;
      }
      .recipe-full {
        display: inline-block;
        width: calc(100% - 350px);
        vertical-align: top;
      }
    }
  }
</style>