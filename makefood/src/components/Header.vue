<template>
  <div id="header">
    <h1>makefood</h1>
    <div id="navigation">
      <div class="nav-option no-my-recipes" id="my-recipes"
           @click="showRecipes($event)"
           :class="areRecipesShowing ? 'active' : ''">
        <span>My Recipes</span>
      </div>
      <div class="nav-option no-my-preferences" id="my-preferences"
           @click="showPrefs($event)"
           :class="arePrefsShowing ? 'active' : ''">
        <span>Preferences</span>
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
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    padding: 20px;
    text-align: left;

    h1 {
      display: inline-block;
      color: $grey3;
      font-family: $logo_font;
      font-size: 28px;
      margin: 0;
    }

    #navigation {
      display: block;
      text-align: left;
      margin: 10px 0;

      .nav-option {
        position: relative;
        display: inline-block;
        color: $grey3;
        font-family: $logo_font;
        font-size: 14px;
        font-weight: 700;
        text-transform: lowercase;
        padding: 0 20px 0 0;
        &.active {
          &:after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            right: 0;
            width: 20%;
            height: 3px;
            background: #343434;
            margin: 0 auto;
          }
        }
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
          cursor: pointer;
        }
      }
    }
  }

  .fade-enter-active {
    -webkit-animation: fadeInDown .5s;
    animation: fadeInDown .5s;
  }
  .fade-leave-active {
    -webkit-animation: fadeInUp .5s;
    animation: fadeInUp .5s;
  }

  @-webkit-keyframes fadeInDown {
    from {
      opacity: 0;
      -webkit-transform: translate3d(0, -100%, 0);
      transform: translate3d(0, -100%, 0);
    }

    to {
      opacity: 1;
      -webkit-transform: translate3d(0, 0, 0);
      transform: translate3d(0, 0, 0);
    }
  }

  @keyframes fadeInDown {
    from {
      opacity: 0;
      -webkit-transform: translate3d(0, -100%, 0);
      transform: translate3d(0, -100%, 0);
    }

    to {
      opacity: 1;
      -webkit-transform: translate3d(0, 0, 0);
      transform: translate3d(0, 0, 0);
    }
  }

  .fadeInDown {
    -webkit-animation-name: fadeInDown;
    animation-name: fadeInDown;
  }

  @-webkit-keyframes fadeInUp {
    from {
      opacity: 1;
      -webkit-transform: translate3d(0, 0, 0);
      transform: translate3d(0, 0, 0);
    }

    to {
      opacity: 0;
      -webkit-transform: translate3d(0, -100%, 0);
      transform: translate3d(0, -100%, 0);
    }
  }

  @keyframes fadeInUp {
    from {
      -webkit-transform: translate3d(0, 0, 0);
      transform: translate3d(0, 0, 0);
    }

    to {
      opacity: 0;
      -webkit-transform: translate3d(0, -100%, 0);
      transform: translate3d(0, -100%, 0);
    }
  }

  .fadeInUp {
    -webkit-animation-name: fadeInUp;
    animation-name: fadeInUp;
  }

</style>