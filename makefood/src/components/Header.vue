<template>
  <div id="header">
    <h1>makefood</h1>
    <Navigation></Navigation>
  </div>
</template>

<script>
  import Navigation from './Navigation'

  export default {
    name: 'header',
    components: {
      Navigation
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
  }
</style>