<template>
  <div id="header">
    <h1>makefood</h1>
    <div id="navigation">
      <div class="nav-option no-my-recipes" id="my-recipes"
           @click="showRecipes($event)">
        <span>My Recipes</span>
        <span>{{areRecipesShowing}}</span>
      </div>
      <div class="nav-option no-my-preferences" id="my-preferences"
           @click="showPrefs($event)">
        <span>Preferences</span>
        <span>{{arePrefsShowing}}</span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Header',
    props: [
      'areRecipesShowing',
      'arePrefsShowing'
    ],
    methods: {
      showRecipes: function (e) {
        this.$emit('show-prefs', false);
        this.areRecipesShowing ? this.$emit('show-recipes', false) : this.$emit('show-recipes', true);
      },
      showPrefs: function (e) {
        this.$emit('show-recipes', false);
        this.arePrefsShowing ? this.$emit('show-prefs', false) : this.$emit('show-prefs', true);
      }
    }
  }
</script>

<style lang="scss">
  @import '../scss/variables';

  #header {
    background: $primary_color;
    color: $secondary_color;
    position: relative;
    padding: 10px;
    text-align: left;

    h1 {
      display: inline-block;
      color: #333;
      font-family: $secondary_font;
      font-size: 28px;
      margin: 0;
    }

    #navigation {
      display: block;
      text-align: left;
      margin: 10px 0;

      .nav-option {
        display: inline-block;
        font-size: 14px;
        padding: 0 20px 0 0;
      }
    }

    @media(min-width: 600px) {
      #navigation {
        display: block;
        background: transparent;
        position: absolute;
        top: 50%;
        left: 0;
        right: 0;
        transform: translate(0, -50%);
        text-align: center;
        margin: 0;

        .nav-option {
          display: inline-block;
          font-size: 14px;
          padding: 0 10px;
        }
      }
    }
  }
</style>