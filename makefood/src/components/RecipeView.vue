<template>
  <div class="recipe-view">
    <transition >
      <div class="recipe"
           v-if="currentRecipe"
           :class="'recipe-'+currentRecipe.replace(/ /g,'-').toLowerCase()">
        <div class="recipe-title">{{currentRecipe}}</div>
        <div class="recipe-section recipe-section-ingredients">
          <div class="recipe-section-heading">Ingredients</div>
          <div class="recipe-item recipe-ingredient"
               v-for="ingredient in currentIngredients">
            <span v-html="ingredient"></span>
          </div>
        </div>
        <div class="recipe-section recipe-section-utensils">
          <div class="recipe-section-heading">Utensils</div>
          <div class="recipe-item recipe-utensil"
               v-for="utensil in currentUtensils">
            <span v-html="utensil"></span>
          </div>
        </div>
        <div class="recipe-section recipe-section-directions">
          <div class="recipe-section-heading">Directions</div>
          <div class="recipe-item recipe-direction"
               v-for="direction in currentDirections">
            <span v-html="direction"></span>
          </div>
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
  export default {
    name: 'MyRecipes',
    props: [
      'currentRecipe',
      'currentIngredients',
      'currentUtensils',
      'currentDirections'
    ],
    data: function() {
      return {
        recipe
      }
    },
    computed: {
      getCurrentRecipe: function (e, recipe) {
        this.currentRecipe = recipe.recipeName;
        this.currentIngredients = recipe.recipeIngredients;
        this.currentUtensils = recipe.recipeUtensils;
        this.currentDirections = recipe.recipeDirections;
      }
    }
  }
</script>

<style lang="scss">
  @import '../scss/variables';

  #display-recipes {
    background: $grey1;
    padding: 20px 10px 10px;
    margin: 115px 0 0;
    .recipe-list {
      text-align: left;
      .recipe-list-item {
        display: block;
        background: $grey2;
        -webkit-border-radius: 3px;
        -moz-border-radius: 3px;
        border-radius: 3px;
        box-shadow: 0px 1px 7px -3px rgba(0,0,0,0.8);
        padding: 10px;
        margin: 0 10px 10px 0;
        text-align: center;
        cursor: pointer;
        transition: all 0.3s;
        &:hover {
          transform: translate(0px, -3px);
          box-shadow: 0px 2px 7px -3px rgba(0,0,0,0.8);
        }
        &.active {
          transform: translate(10px, 0);
          box-shadow: 0px 2px 7px -3px rgba(0,0,0,0.8);
        }
        .recipe-title {
          font-size: 14px;
          font-weight: 700;
        }
      }
    }
    .recipe-view {
      .recipe {
        transition: all 0.5s;

        .recipe-title {
          font-size: 24px;
          font-weight: 700;
        }

        .recipe-section {
          margin: 0 0 20px;

          .recipe-section-heading {
            border-bottom: 1px solid #41b883;
            font-size: 18px;
            font-weight: 700;
            padding: 10px 0;
            margin: 0 0 10px;
          }

          .recipe-item {
            font-family: $secondary_font;
            font-size: 16px;
            font-weight: 400;

            strong {
              display: block;
              margin: 10px 0 0;
            }
          }
        }
      }
    }
  }

  @media(min-width: 600px) {
    #display-recipes {
      margin: 73px 0 0;
    }
  }

  @media(min-width: 768px) {
    #display-recipes {
      .recipe-list {
        display: inline-block;
        width: 330px;
        padding: 10px;
      }
      .recipe-view {
        display: inline-block;
        width: calc(100% - 350px);
        vertical-align: top;
      }
    }
  }
</style>