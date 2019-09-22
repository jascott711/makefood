<template>
  <div id="navigation">
      <div class="nav-option no-my-recipes" id="my-recipes">My Recipes</div>
      <div class="nav-option no-my-preferences" id="my-preferences">Preferences</div>
  </div>
</template>

<script>

</script>

<style lang="scss">
  @import '../scss/variables';

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
</style>